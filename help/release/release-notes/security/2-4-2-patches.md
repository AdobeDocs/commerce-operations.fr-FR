---
title: Notes De Mise À Jour Du Correctif De Sécurité D’Adobe Commerce 2.4.2
description: Découvrez les correctifs de sécurité, les améliorations de sécurité et les autres mises à jour liées à la sécurité inclus dans les versions des correctifs de sécurité pour Adobe Commerce version 2.4.2.
exl-id: e6058e96-b810-4a78-8804-15783afef951
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---


# Notes de mise à jour des correctifs de sécurité d’Adobe Commerce 2.4.2

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## Adobe Commerce 2.4.2-p2

La version de sécurité 2.4.2-p2 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités qui ont été identifiées dans les versions précédentes de 2.4.2.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB21-64](https://helpx.adobe.com/security/products/magento/apsb21-64.html).

## Appliquez `AC-3022.patch` pour continuer à proposer DHL comme transporteur

DHL a introduit la version 6.2 du schéma et abandonnera la version 6.0 dans un avenir proche. Adobe Commerce 2.4.4 et les versions antérieures qui prennent en charge l’intégration DHL ne prennent en charge que la version 6.0. Les commerçants qui déploient ces mainlevées devraient appliquer `AC-3022.patch` dès que possible pour continuer à offrir DHL en tant que transporteur. Consultez l’article de la base de connaissances [Appliquer un correctif pour continuer à proposer DHL en tant que transporteur](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) pour plus d’informations sur le téléchargement et l’installation du correctif.
