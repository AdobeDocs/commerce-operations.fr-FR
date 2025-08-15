---
title: Security.txt
description: Découvrez comment fournir des informations pour aider les chercheurs en sécurité à signaler les vulnérabilités.
feature: Configuration, Security
badge: label="Contribution de Kalpesh Mehta de Corra" type="Informative" url="https://solutionpartners.adobe.com/s/directory/detail/corra" tooltip="Kalpesh Mehta"
exl-id: ddafd03c-77b2-42e8-b593-7d655d08e9c3
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# Fichier TXT de sécurité

Lorsque des vulnérabilités de sécurité sont découvertes par les chercheurs, les canaux de création de rapports appropriés font souvent défaut. Par conséquent, certaines vulnérabilités ne sont pas signalées. Le but du fichier `security.txt` [format](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-09) est de fournir aux chercheurs en sécurité les informations qu&#39;ils peuvent utiliser pour rapporter leurs résultats.

Les commerçants peuvent saisir leurs coordonnées pour [signalement des problèmes de sécurité](https://experienceleague.adobe.com/fr/docs/commerce-admin/systems/security/security-issue-reporting) à partir de Commerce _Admin_. Pour les développeurs, le module `Magento_Securitytxt` fournit les fonctionnalités suivantes :

- Permet l’enregistrement des configurations de sécurité depuis l’_Admin_.
- Contient un routeur pour faire correspondre la classe d&#39;action de l&#39;application pour les requêtes aux fichiers `.well-known/security.txt` et `.well-known/security.txt.sig`.
- Diffuse le contenu des fichiers `.well-known/security.txt` et `.well-known/security.txt.sig`.

Un fichier `security.txt` valide peut se présenter comme suit :

```text
Contact: mailto:security@example.com
Contact: tel:+1-201-555-0123
Encryption: https://example.com/pgp.asc
Acknowledgement: https://example.com/security/hall-of-fame
Policy: https://example.com/security-policy.html
Signature: https://example.com/.well-known/security.txt.sig
```

Pour créer le fichier de signature `security.txt` (`security.txt.sig`) :

```bash
gpg -u KEYID --output security.txt.sig --armor --detach-sig security.txt
```

Pour vérifier la signature :

```bash
gpg --verify security.txt.sig security.txt
```
