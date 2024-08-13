---
title: Notes de mise à jour du correctif de sécurité Adobe Commerce 2.4.7
description: Découvrez les correctifs de sécurité, les améliorations de sécurité et d’autres mises à jour relatives à la sécurité inclus dans les versions des correctifs de sécurité pour Adobe Commerce version 2.4.7.
exl-id: 38e5632b-c795-47d8-89dd-26bbaeb34e67
source-git-commit: 3a2d104f0a689ac3715af302d470a1660857543c
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# Notes de mise à jour des correctifs de sécurité d’Adobe Commerce 2.4.7

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## 2.4.7-p2

La version de sécurité Adobe Commerce 2.4.7-p2 fournit des correctifs de bogues de sécurité pour les vulnérabilités identifiées dans les versions précédentes de la version 2.4.7.

Pour obtenir les informations les plus récentes sur les correctifs de bogues de sécurité, reportez-vous à la section [Bulletin de sécurité Adobe APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html).

### Tons clairs

{{$include /help/_includes/release-notes/2024-08/security.md}}

### Correctifs inclus dans cette version

{{$include /help/_includes/release-notes/2024-08/hotfixes-included.md}}

## 2.4.7-p1

La version de sécurité Adobe Commerce 2.4.7-p1 fournit des correctifs de bogues de sécurité pour les vulnérabilités identifiées dans les versions précédentes de la version 2.4.7.

Pour obtenir les informations les plus récentes sur les correctifs de bogues de sécurité, reportez-vous à la section [Bulletin de sécurité Adobe APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Correctif pour CVE-2024-34102

{{$include /help/_includes/release-notes/2024-06/hotfixes-not-included.md}}

### Tons clairs

Cette version comprend les points forts suivants :

* **Mise à jour [des paramètres de mot de passe unique (OTP)](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) pour l’authentificateur Google** - Cette mise à jour est nécessaire pour résoudre une erreur qui a été introduite par une [modification rétrocompatible](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) dans la version 2.4.7. La description du champ **[!UICONTROL OTP Window]** fournit désormais une explication exacte du paramètre et la valeur par défaut a été changée de `1` à `29`.

* **Compatibilité de version B2B** : pour la compatibilité avec Commerce version 2.4.7-p1, les marchands qui ont l’extension Adobe Commerce B2B doivent effectuer la mise à niveau vers [B2B version 1.4.2-p1](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1).

### Correctifs inclus dans cette version

Adobe Commerce 2.4.7-p1 résout un problème introduit dans la portée de la migration de l’intégration UPS de SOAP à l’API REST. Ce problème affectait les clients qui expédient en dehors des États-Unis et les empêchait d’utiliser les mesures du système de mesure/SI des kilogrammes et des centimètres pour les colis afin de créer des envois avec UPS. Pour plus d’informations, consultez l’article [Migration de l’intégration de la méthode d’expédition UPS de SOAP à l’API RESTful](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api) .
