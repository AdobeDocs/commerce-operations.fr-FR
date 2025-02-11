---
title: Notes De Mise À Jour Du Correctif De Sécurité D’Adobe Commerce 2.4.7
description: Découvrez les correctifs de sécurité, les améliorations de sécurité et les autres mises à jour liées à la sécurité inclus dans les versions des correctifs de sécurité pour Adobe Commerce version 2.4.7.
exl-id: 38e5632b-c795-47d8-89dd-26bbaeb34e67
source-git-commit: 9397740c608e4f0521018d6f6c918ca267197c6c
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Notes de mise à jour des correctifs de sécurité d’Adobe Commerce 2.4.7

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.7-p4

La version de sécurité 2.4.7-p4 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités identifiées dans les versions précédentes de 2.4.7.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB25-08](https://helpx.adobe.com/security/products/magento/apsb25-08.html).

{{b2b-patches}}

### Faits saillants

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.7-p3

La version de sécurité 2.4.7-p3 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités identifiées dans les versions précédentes de 2.4.7.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html).

{{b2b-patches}}

### Faits saillants

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### Correctifs inclus dans cette version

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2.4.7-p2

La version de sécurité 2.4.7-p2 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités identifiées dans les versions précédentes de 2.4.7.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html).

### Faits saillants

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### Correctifs inclus dans cette version

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.7-p1

La version de sécurité 2.4.7-p1 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités qui ont été identifiées dans les versions précédentes de 2.4.7.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Appliquer un correctif pour CVE-2024-34102

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### Faits saillants

Les points forts de cette version sont les suivants :

* **Mise à jour [paramètres de mot de passe à usage unique (OTP)](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) pour l’authentificateur Google**-Cette mise à jour est nécessaire pour résoudre une erreur introduite par une [modification rétrocompatible](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) dans la version 2.4.7. La description du champ **[!UICONTROL OTP Window]** fournit désormais une explication précise du paramètre et la valeur par défaut a été modifiée de `1` en `29`.

* **Compatibilité des versions B2B** : pour des raisons de compatibilité avec la version 2.4.7-p1 de Commerce, les commerçants qui disposent de l’extension Adobe Commerce B2B doivent effectuer la mise à niveau vers la version 1.4.2-p1 de [B2B](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1).

### Correctifs inclus dans cette version

Adobe Commerce 2.4.7-p1 résout un problème introduit dans le cadre de la migration de l’intégration UPS de SOAP vers l’API REST. Ce problème affectait les clients qui expédiaient à l&#39;extérieur des États-Unis et les empêchait d&#39;utiliser les mesures du système métrique/SI de kilogrammes et de centimètres pour les colis afin de créer des expéditions avec UPS. Consultez l’article de la base de connaissances [ Migration de l’intégration de la méthode d’expédition UPS de l’API SOAP vers l’API RESTful ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api) pour plus d’informations.
