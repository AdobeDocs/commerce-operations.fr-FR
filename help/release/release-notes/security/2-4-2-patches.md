---
title: Notes de mise à jour du correctif de sécurité Adobe Commerce 2.4.2
description: Découvrez les correctifs de sécurité, les améliorations de sécurité et d’autres mises à jour relatives à la sécurité inclus dans les versions des correctifs de sécurité pour Adobe Commerce version 2.4.2.
exl-id: e6058e96-b810-4a78-8804-15783afef951
source-git-commit: d532402e2d65a1f34558fc3c283d4291be5b006b
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---


# Notes de mise à jour des correctifs de sécurité d’Adobe Commerce 2.4.2

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.2-p2

La version de sécurité Adobe Commerce 2.4.2-p2 fournit des correctifs de bogues de sécurité pour les vulnérabilités identifiées dans les versions précédentes de la version 2.4.2.

Pour obtenir les informations les plus récentes sur les correctifs de bogues de sécurité, reportez-vous à la section [Bulletin de sécurité Adobe APSB21-64](https://helpx.adobe.com/security/products/magento/apsb21-64.html).

## Appliquez `AC-3022.patch` pour continuer à proposer DHL comme opérateur de transport

DHL a introduit la version 6.2 du schéma et va abandonner la version 6.0 dans un avenir proche. Adobe Commerce 2.4.4 et les versions antérieures qui prennent en charge l’intégration DHL ne prennent en charge que la version 6.0. Les commerçants qui déploient ces versions doivent appliquer `AC-3022.patch` dès que possible pour continuer à proposer DHL en tant qu&#39;opérateur de transport. Pour plus d’informations sur le téléchargement et l’installation du correctif, reportez-vous à l’article [Appliquer un correctif pour continuer à proposer DHL comme opérateur de transport](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) de la base de connaissances.
