---
title: Security.txt
description: Découvrez comment fournir des informations pour aider les chercheurs en sécurité à signaler les vulnérabilités.
feature: Configuration, Security
badge: label="Contribution de Kalpesh Mehta de Corra" type="Informative" url="https://solutionpartners.adobe.com/s/directory/detail/corra" tooltip="Kalpesh Mehta"
exl-id: ddafd03c-77b2-42e8-b593-7d655d08e9c3
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%
---
# Fichier TXT de sécurité

Lorsque des vulnérabilités de sécurité sont découvertes par les chercheurs, les canaux de création de rapports appropriés font souvent défaut. Par conséquent, certaines vulnérabilités ne sont pas signalées. Le but du fichier `security.txt` [format](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-09) est de fournir aux chercheurs en sécurité les informations qu&#39;ils peuvent utiliser pour rapporter leurs résultats.

Les commerçants peuvent saisir leurs coordonnées pour [signalement des problèmes de sécurité](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-issue-reporting) à partir de Commerce _Admin_. Pour les développeurs, le module `Magento_Securitytxt` fournit les fonctionnalités suivantes :

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

```shell
gpg -u KEYID --output security.txt.sig --armor --detach-sig security.txt
```

Pour vérifier la signature :

```shell
gpg --verify security.txt.sig security.txt
```
