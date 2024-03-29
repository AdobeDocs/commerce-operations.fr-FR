---
title: La variable [!UICONTROL Security] tab
description: En savoir plus sur les [!UICONTROL Security] de [!DNL Observation for Adobe Commerce].
exl-id: b567e4a4-534e-4151-b6f6-bf59b1bd4028
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# La variable [!UICONTROL Security] tab

La variable **[!UICONTROL Security]** explique les problèmes de sécurité et isole leurs causes potentielles. De plus, les cadres de l’onglet sont décrits.

## [!UICONTROL API calls by IP, details by URL]

La variable **[!UICONTROL API calls by IP, details by URL]** cadre affiche un certain nombre d’appels API par IP au cours d’une période sélectionnée. Ce cadre affiche l’adresse IP et l’URL de l’API auxquelles cette adresse IP a accédé.

![Appels API par IP](../../assets/tools/observation-for-adobe-commerce/calls-by-ip.jpg)

## [!UICONTROL Forgot Password]

La variable **[!UICONTROL Forgot Password]** Le cadre d’accès indique le nombre de tentatives de mot de passe oubliées au cours d’une période sélectionnée. Une activité élevée contre une adresse IP peut être une attaque sur le site.

![Mot de passe oublié](../../assets/tools/observation-for-adobe-commerce/forgot-password.jpg)

## [!UICONTROL Create Account access]

La variable **[!UICONTROL Create Account access]** Le cadre indique le nombre de nouvelles activités de compte au cours d’une période sélectionnée. Une activité élevée provenant d’une seule adresse IP peut indiquer une attaque.

![create-account-access](../../assets/tools/observation-for-adobe-commerce/create-account-access.png)

## [!UICONTROL POST activities]

La variable **[!UICONTROL POST activities]** Le cadre affiche la `POST` activités du site, facettées sur `client_ip` de la [!DNL Fastly] journaux. Il indique également l’URL à laquelle l’adresse IP a accès.

![POST-activities](../../assets/tools/observation-for-adobe-commerce/POST-activities.jpg)

## [!UICONTROL POST activities summary table]

La variable **[!UICONTROL POST activities summary table]** Le cadre affiche le résumé `POST` activités du site, facettées sur `client_ip` de la [!DNL Fastly] journaux. Il indique également le nombre d’adresses URL auxquelles l’adresse IP accède. Le décompte correspond à la période sélectionnée.

![POST-activities-summary](../../assets/tools/observation-for-adobe-commerce/POST-activities-summary.jpg)

## [!UICONTROL POST activities details table]

La variable **[!UICONTROL POST activities details table]** Le cadre affiche la `POST` activités pour le site à partir de la fonction [!DNL Fastly] journaux. Il affiche également tous les détails de la variable [!DNL Fastly] journal de ces requêtes. Elle est limitée aux 2000 dernières demandes.
![POST-activities-details](../../assets/tools/observation-for-adobe-commerce/POST-activities-details.jpg)

## [!UICONTROL Guest Carts activities]

La variable **[!UICONTROL Guest Carts activities]** cadre affiche le nombre d’activités du panier d’invités au cours d’une période sélectionnée, facettée par l’adresse IP et l’URL consultée. Les paniers d’invités peuvent être utilisés dans le cadre d’une attaque de carte. Ce cadre affiche le nombre total de demandes pour lesquelles les URL des paniers d’invités sont accessibles.

![guest-carts-activities](../../assets/tools/observation-for-adobe-commerce/guest-carts-activities.jpg)

## [!UICONTROL API – forgot password, create account by Countries]

La variable **[!UICONTROL API – forgot password, create account by Countries]** Le cadre indique le nombre de comptes créés et de demandes de réinitialisation d’un mot de passe oublié au cours d’une période sélectionnée. Il est également mis en page pour indiquer le pays d’origine de la demande. Ce cadre est axé sur le pays d’origine de la demande.

![api-oubli-countries](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries.jpg)

## [!UICONTROL API - forgot password, create account by Countries and IP address]

La variable **[!UICONTROL API - forgot password, create account by Countries and IP address]** Le cadre indique le nombre de comptes créés et de demandes de réinitialisation d’un mot de passe oublié au cours d’une période sélectionnée. Il est facetté pour afficher également l’adresse IP, l’URL consultée et le pays d’origine de la demande. Ce cadre est axé sur le nombre d’adresses IP.

![api-oublié-countries-ip](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries-ip.png)

## [!UICONTROL Guest cart activities by IP]

La variable **[!UICONTROL Guest cart activities by IP]** cadre affiche les activités du panier d’invités par IP sur une période sélectionnée.

![guest-cart-ip](../../assets/tools/observation-for-adobe-commerce/guest-cart-ip.png)

## [!UICONTROL Guest cart activities by Countries]

La variable **[!UICONTROL Guest cart activities by Countries]** cadre affiche les activités de panier d’invités par pays sur une période sélectionnée.

![guest-cart-country](../../assets/tools/observation-for-adobe-commerce/guest-cart-country.png)
