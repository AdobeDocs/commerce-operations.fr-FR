---
title: Notes de mise à jour du correctif de sécurité Adobe Commerce 2.4.2
description: Découvrez les correctifs de sécurité, les améliorations de sécurité et d’autres mises à jour relatives à la sécurité inclus dans les versions des correctifs de sécurité pour Adobe Commerce version 2.4.2.
exl-id: e6058e96-b810-4a78-8804-15783afef951
source-git-commit: 1eaf2329c16e6dbe3e93cb7fff3a6920b4b8379d
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---

# Notes de mise à jour des correctifs de sécurité Adobe Commerce 2.4.2

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.2-p2

La version de sécurité Adobe Commerce 2.4.2-p2 fournit des correctifs de bogues de sécurité pour les vulnérabilités identifiées dans la version trimestrielle précédente, Adobe Commerce 2.4.2 et Magento Open Source 2.4.2.

Pour obtenir les informations les plus récentes sur les correctifs de bogues de sécurité, voir [Bulletin de sécurité Adobe APSB21-64](https://helpx.adobe.com/security/products/magento/apsb21-64.html).

## Appliquer `AC-3022.patch` continuer à proposer DHL comme opérateur de transport

DHL a introduit la version 6.2 du schéma et va abandonner la version 6.0 dans un avenir proche. Adobe Commerce 2.4.4 et les versions antérieures qui prennent en charge l’intégration DHL ne prennent en charge que la version 6.0. Les commerçants qui déploient ces versions doivent s’appliquer `AC-3022.patch` dès leur première convenance de continuer à proposer DHL comme transporteur. Voir [Appliquez un correctif pour continuer à proposer DHL comme opérateur de transport](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) Article de la base de connaissances pour plus d’informations sur le téléchargement et l’installation du correctif.

