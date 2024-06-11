---
title: Notes de mise à jour du correctif de sécurité Adobe Commerce 2.4.7
description: Découvrez les correctifs de sécurité, les améliorations de sécurité et d’autres mises à jour relatives à la sécurité inclus dans les versions des correctifs de sécurité pour Adobe Commerce version 2.4.7.
source-git-commit: 7705e750a466ab134ae2616a40a32880ee0c45de
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%

---


# Notes de mise à jour des correctifs de sécurité d’Adobe Commerce 2.4.7

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.7-p1

La version de sécurité Adobe Commerce 2.4.7-p1 fournit des correctifs de bogues de sécurité pour les vulnérabilités identifiées dans les versions précédentes de la version 2.4.7.

Pour obtenir les informations les plus récentes sur les correctifs de bogues de sécurité, voir [Bulletin de sécurité Adobe APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

## Mise en évidence de la sécurité

Cette version comprend une mise à jour des [paramètres de mot de passe unique (OTP)](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) pour l’authentificateur Google afin de résoudre une erreur introduite par un [modification rétrocompatible](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) dans 2.4.7. La description de la variable **[!UICONTROL OTP Window]** fournit désormais une explication exacte du paramètre et la valeur par défaut a été modifiée à partir de `1` to `29`.
