---
title: Hachage de mot de passe
description: Découvrez les stratégies de hachage de mot de passe et leur mise en oeuvre.
source-git-commit: 5c0d285717a79d654af769cb734ec385d2d4046f
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---


# Hachage de mot de passe

Actuellement, Commerce utilise sa propre stratégie de hachage de mot de passe, en fonction de différents algorithmes de hachage PHP natifs. Commerce prend en charge plusieurs algorithmes tels que `MD5`, `SHA256`ou `Argon 2ID13`. Si l&#39;extension Sodium est installée (installée par défaut en PHP 7.3), `Argon 2ID13` est choisi comme algorithme de hachage par défaut. Sinon, `SHA256` est la valeur par défaut. Commerce peut utiliser le PHP natif `password_hash` avec la prise en charge de l’algorithme Argon 2i.

Pour éviter de compromettre des mots de passe plus anciens qui ont été hachés avec des algorithmes obsolètes comme `MD5`, la mise en oeuvre actuelle fournit une méthode pour mettre à niveau le hachage sans modifier le mot de passe d’origine. En règle générale, le hachage du mot de passe présente le format suivant :

```text
password_hash:salt:version<n>:version<n>
```

Où `version<n>`...`version<n>` représente toutes les versions des algorithmes de hachage utilisées sur le mot de passe. De plus, le sel est toujours stocké avec le hachage du mot de passe, afin que nous puissions restaurer la chaîne entière des algorithmes. Voici un exemple :

```text
a853b06f077b686f8a3af80c98acfca763cf10c0e03597c67e756f1c782d1ab0:8qnyO4H1OYIfGCUb:1:2
```

La première partie représente le hachage du mot de passe. La seconde, `8qnyO4H1OYIfGCUb` est le sel. Les deux derniers sont les différents algorithmes de hachage : 1 est `SHA256` et 2 correspond à `Argon 2ID13`. Cela signifie que le mot de passe du client a été haché à l’origine avec `SHA256` et après cela, l’algorithme a été mis à jour avec `Argon 2ID13` et le hachage a été haché avec Argon.

## Stratégie de hachage de mise à niveau

Examinez à quoi ressemble le mécanisme de mise à niveau de hachage. Supposons qu’à l’origine, un mot de passe ait été haché avec `MD5` puis l’algorithme a été mis à jour plusieurs fois avec Argon 2ID13. Le diagramme suivant illustre le flux de mise à niveau de hachage.

![Workflow de mise à niveau des hachages](../../assets/configuration/hash-upgrade-algorithm.png)

Chaque algorithme de hachage utilise le hachage précédent du mot de passe pour générer un nouveau hachage. Commerce ne stocke pas le mot de passe d’origine brut.

![Stratégie de mise à niveau des hachages](../../assets/configuration/hash-upgrade-strategy.png)

Comme mentionné ci-dessus, plusieurs versions de hachage du mot de passe peuvent être appliquées au mot de passe d’origine.
Voici comment fonctionne le mécanisme de vérification du mot de passe lors de l’authentification d’un client.

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

Comme Commerce stocke toutes les versions de hachage de mot de passe utilisées avec le hachage de mot de passe, nous pouvons restaurer la chaîne de hachage entière pendant la vérification du mot de passe. Le mécanisme de vérification de hachage est similaire à la stratégie de mise à niveau de hachage : en fonction des versions stockées avec le hachage du mot de passe, l’algorithme génère des hachages à partir du mot de passe fourni et renvoie le résultat de comparaison entre le mot de passe haché et le hachage stocké dans la base de données.

## Implémentation

Le `\Magento\Framework\Encryption\Encryptor` est responsable de la génération et de la vérification du hachage du mot de passe. Le [`bin/magento customer:hash:upgrade`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#customerhashupgrade) met à niveau le hachage d’un mot de passe client vers le dernier algorithme de hachage.
