---
title: Security.txt
description: Découvrez comment fournir des informations pour aider les chercheurs en sécurité à signaler les vulnérabilités.
contributor_name: Kalpesh Mehta from Corra
contributor_link: https://partners.magento.com/portal/details/partner/id/70/
source-git-commit: 27c3914540a0574fa4ff58df50d5cd2c71fb6670
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%

---


# Fichier TXT de sécurité

Lorsque des chercheurs découvrent des vulnérabilités de la sécurité, des canaux de reporting appropriés sont souvent manquants. Par conséquent, certaines vulnérabilités ne sont pas signalées. L’objet de la variable `security.txt` [format de fichier](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-09) est destiné à fournir aux chercheurs en sécurité les informations qu’ils peuvent utiliser pour rapporter leurs résultats.

Les vendeurs peuvent saisir leurs coordonnées pour [rapport sur les problèmes de sécurité](https://docs.magento.com/user-guide/stores/security-issue-reporting.html) de Commerce _Administration_. Pour les développeurs, la variable `Magento_Securitytxt` fournit les fonctionnalités suivantes :

- Permet d’enregistrer les configurations de sécurité à partir du _Administration_.
- Contient un routeur qui correspond à la classe d’action de l’application pour les requêtes envoyées à l’événement `.well-known/security.txt` et `.well-known/security.txt.sig` fichiers .
- Diffuse le contenu de la `.well-known/security.txt` et `.well-known/security.txt.sig` fichiers .

Un valide `security.txt` peut se présenter comme suit :

```text
Contact: mailto:security@example.com
Contact: tel:+1-201-555-0123
Encryption: https://example.com/pgp.asc
Acknowledgement: https://example.com/security/hall-of-fame
Policy: https://example.com/security-policy.html
Signature: https://example.com/.well-known/security.txt.sig
```

Pour créer la variable `security.txt` signature (`security.txt.sig`) :

```bash
gpg -u KEYID --output security.txt.sig --armor --detach-sig security.txt
```

Pour vérifier la signature :

```bash
gpg --verify security.txt.sig security.txt
```
