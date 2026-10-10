---
title: Notes De Mise À Jour Du Correctif De Sécurité D’Adobe Commerce 2.4.2
description: Découvrez les correctifs de sécurité, les améliorations de sécurité et les autres mises à jour liées à la sécurité inclus dans les versions des correctifs de sécurité pour Adobe Commerce version 2.4.2.
exl-id: e6058e96-b810-4a78-8804-15783afef951
last-update: 2026-08-19
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: a3c0eba7bdcd8017e88bdb4df1f45d77fe4bb351
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%
---

# Notes de mise à jour des correctifs de sécurité d’Adobe Commerce 2.4.2

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## Adobe Commerce 2.4.2-p2

La version de sécurité 2.4.2-p2 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités qui ont été identifiées dans les versions précédentes de 2.4.2.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB21-64](https://helpx.adobe.com/fr/security/products/magento/apsb21-64.html).

## Appliquer AC-3022.patch pour continuer à offrir DHL comme transporteur

DHL a introduit la version 6.2 du schéma et abandonnera la version 6.0 dans un avenir proche. Adobe Commerce 2.4.4 et les versions antérieures qui prennent en charge l’intégration DHL ne prennent en charge que la version 6.0. Les commerçants qui déploient ces mainlevées devraient appliquer `AC-3022.patch` dès que possible pour continuer à offrir DHL en tant que transporteur. Consultez l’article de la base de connaissances [Appliquer un correctif pour continuer à proposer DHL en tant que transporteur](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) pour plus d’informations sur le téléchargement et l’installation du correctif.

<!-- Last updated from includes: 2026-08-19 13:31:55 -->
