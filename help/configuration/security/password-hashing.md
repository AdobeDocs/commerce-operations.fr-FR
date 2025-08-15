---
title: Hachage du mot de passe
description: Découvrez les stratégies de hachage de mot de passe et leur implémentation.
feature: Configuration, Security
exl-id: 2865d041-950a-4d96-869c-b4b35f5c4120
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Hachage du mot de passe

Actuellement, Commerce utilise sa propre stratégie de hachage de mot de passe, basée sur différents algorithmes de hachage PHP natifs. Commerce prend en charge plusieurs algorithmes tels que `MD5`, `SHA256` ou `Argon 2ID13`. Si l&#39;extension Sodium est installée (installée par défaut en PHP 7.3), alors `Argon 2ID13` est choisi comme algorithme de hachage par défaut. Dans le cas contraire, `SHA256` est la valeur par défaut. Commerce peut utiliser la fonction native PHP `password_hash` avec la prise en charge de l&#39;algorithme Argon 2i.

Pour éviter de compromettre des mots de passe plus anciens qui ont été hachés avec des algorithmes obsolètes tels que `MD5`, l’implémentation actuelle fournit une méthode pour mettre à niveau le hachage sans modifier le mot de passe d’origine. En règle générale, le hachage du mot de passe présente le format suivant :

```text
password_hash:salt:version<n>:version<n>
```

Où `version<n>`...`version<n>` représente toutes les versions d’algorithmes de hachage utilisées sur le mot de passe. En outre, le sel est toujours stocké avec le hachage du mot de passe, de sorte que nous pouvons restaurer toute la chaîne d&#39;algorithmes. Voici un exemple :

```text
a853b06f077b686f8a3af80c98acfca763cf10c0e03597c67e756f1c782d1ab0:8qnyO4H1OYIfGCUb:1:2
```

La première partie représente le hachage du mot de passe. Le deuxième, `8qnyO4H1OYIfGCUb`, c&#39;est le sel. Les deux derniers sont les différents algorithmes de hachage : 1 est `SHA256` et 2 est `Argon 2ID13`. Cela signifie que le mot de passe du client a d’abord été haché avec `SHA256`, puis que l’algorithme a été mis à jour avec `Argon 2ID13` et que le hachage a été rehaché avec Argon.

## Mettre à niveau la stratégie de hachage

Examinez à quoi ressemble le mécanisme de mise à niveau du hachage. Supposons qu’à l’origine, un mot de passe ait été haché avec `MD5`, puis que l’algorithme ait été mis à jour plusieurs fois avec Argon 2ID13. Le diagramme suivant illustre le flux de mise à niveau du hachage.

![Workflow de mise à niveau du hachage](../../assets/configuration/hash-upgrade-algorithm.png)

Chaque algorithme de hachage utilise le hachage du mot de passe précédent pour générer un nouveau hachage. Commerce ne stocke pas le mot de passe brut d’origine.

![Stratégie de mise à niveau de hachage](../../assets/configuration/hash-upgrade-strategy.png)

Comme nous l’avons vu plus haut, le hachage du mot de passe peut comporter plusieurs versions de hachage appliquées au mot de passe d’origine.
Voici comment fonctionne le mécanisme de vérification des mots de passe lors d’une authentification du client.

```php
def verify(password, hash):
    restored = password

    hash_map = extract(hash)
    # iterate through all versions specified in the received hash [md5, sha256, argon2id13]
    for version in hash_map.get_versions():
        # generate new hash based on password/previous hash, salt and version
        restored = hash_func(salt . restored, version)

    # extract only password hash from the hash:salt:version chain
    hash = hash_map.get_hash()

    return compare(restored, hash)
```

Comme Commerce stocke toutes les versions de hachage de mot de passe utilisées ainsi que le hachage du mot de passe, nous pouvons restaurer l’ensemble de la chaîne de hachage pendant la vérification du mot de passe. Le mécanisme de vérification du hachage est similaire à la stratégie de mise à niveau du hachage : en fonction des versions stockées avec le hachage du mot de passe, l’algorithme génère des hachages à partir du mot de passe fourni et renvoie le résultat de la comparaison entre le mot de passe haché et le hachage stocké dans la base de données.

## Mise en œuvre

La classe `\Magento\Framework\Encryption\Encryptor` est responsable de la génération et de la vérification du hachage du mot de passe. La commande [`bin/magento customer:hash:upgrade`](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/cli-reference/commerce-on-premises#customerhashupgrade) met à niveau un hachage de mot de passe client vers le dernier algorithme de hachage.
