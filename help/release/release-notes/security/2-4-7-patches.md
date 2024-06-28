---
title: Notes de mise à jour du correctif de sécurité Adobe Commerce 2.4.7
description: Découvrez les correctifs de sécurité, les améliorations de sécurité et d’autres mises à jour relatives à la sécurité inclus dans les versions des correctifs de sécurité pour Adobe Commerce version 2.4.7.
exl-id: 38e5632b-c795-47d8-89dd-26bbaeb34e67
source-git-commit: e5f659cc3bee2d116222c15549fb3d6094644531
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# Notes de mise à jour des correctifs de sécurité d’Adobe Commerce 2.4.7

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.7-p1

La version de sécurité Adobe Commerce 2.4.7-p1 fournit des correctifs de bogues de sécurité pour les vulnérabilités identifiées dans les versions précédentes de la version 2.4.7.

Pour obtenir les informations les plus récentes sur les correctifs de bogues de sécurité, voir [Bulletin de sécurité Adobe APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Mise en évidence de la sécurité

* **Mettre à jour [paramètres de mot de passe unique (OTP)](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) pour l’authentificateur Google**- Cette mise à jour est nécessaire pour résoudre une erreur qui a été introduite par une [modification rétrocompatible](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) dans 2.4.7. La description de la variable **[!UICONTROL OTP Window]** fournit désormais une explication exacte du paramètre et la valeur par défaut a été modifiée à partir de `1` to `29`.

* **Compatibilité des versions B2B**—Pour des raisons de compatibilité avec Commerce version 2.4.7-p1, les commerçants qui disposent de l’extension Adobe Commerce B2B doivent effectuer la mise à niveau vers [B2B version 1.4.2-p1](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes#b2b-v142p1.html).

### Correctifs inclus dans cette version

Adobe Commerce 2.4.7-p1 résout un problème introduit dans la portée de la migration de l’intégration UPS de SOAP à l’API REST. Ce problème affectait les clients qui expédient en dehors des États-Unis et les empêchait d’utiliser les mesures du système de mesure/SI des kilogrammes et des centimètres pour les colis afin de créer des envois avec UPS. Voir [Migration de l’intégration de la méthode d’expédition UPS de SOAP vers l’API RESTful](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api) article de la base de connaissances pour plus de détails.
