---
title: Onglet [!UICONTROL Security]
description: Découvrez l’onglet [!UICONTROL Security] de [!DNL Observation for Adobe Commerce].
exl-id: b567e4a4-534e-4151-b6f6-bf59b1bd4028
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# Onglet [!UICONTROL Security]

L’onglet **[!UICONTROL Security]** explique les problèmes de sécurité et isole leurs causes potentielles. De plus, les cadres de l’onglet sont décrits.

## [!UICONTROL API calls by IP, details by URL]

L’image **[!UICONTROL API calls by IP, details by URL]** présente un certain nombre d’appels API par IP sur une période sélectionnée. Ce cadre affiche l’adresse IP et l’URL de l’API auxquelles cette adresse IP a accédé.

![Appels API par IP](../../assets/tools/observation-for-adobe-commerce/calls-by-ip.jpg)

## [!UICONTROL Forgot Password]

Le cadre d’accès **[!UICONTROL Forgot Password]** indique le nombre de tentatives de mot de passe oubliées au cours d’une période sélectionnée. Une activité élevée contre une adresse IP peut être une attaque sur le site.

![Mot de passe oublié](../../assets/tools/observation-for-adobe-commerce/forgot-password.jpg)

## [!UICONTROL Create Account access]

L’image **[!UICONTROL Create Account access]** indique le nombre de nouvelles activités de compte au cours d’une période sélectionnée. Une activité élevée provenant d’une seule adresse IP peut indiquer une attaque.

![create-account-access](../../assets/tools/observation-for-adobe-commerce/create-account-access.png)

## [!UICONTROL POST activities]

L’image **[!UICONTROL POST activities]** montre les activités `POST` du site, facettées sur `client_ip` à partir des journaux [!DNL Fastly]. Il indique également l’URL à laquelle l’adresse IP a accès.

![POST-activities](../../assets/tools/observation-for-adobe-commerce/POST-activities.jpg)

## [!UICONTROL POST activities summary table]

L’image **[!UICONTROL POST activities summary table]** montre les activités `POST` résumées pour le site, facettées sur `client_ip` à partir des journaux [!DNL Fastly]. Il indique également le nombre d’adresses URL auxquelles l’adresse IP accède. Le décompte correspond à la période sélectionnée.

![POST-activities-summary](../../assets/tools/observation-for-adobe-commerce/POST-activities-summary.jpg)

## [!UICONTROL POST activities details table]

L’image **[!UICONTROL POST activities details table]** montre les activités `POST` du site à partir des journaux [!DNL Fastly]. Il affiche également tous les détails du journal [!DNL Fastly] de ces requêtes. Elle est limitée aux 2000 dernières demandes.
![POST-activities-details](../../assets/tools/observation-for-adobe-commerce/POST-activities-details.jpg)

## [!UICONTROL Guest Carts activities]

L’image **[!UICONTROL Guest Carts activities]** indique le nombre d’activités du panier d’invités au cours d’une période sélectionnée, facettée par l’adresse IP et l’URL consultée. Les paniers d’invités peuvent être utilisés dans le cadre d’une attaque de carte. Ce cadre affiche le nombre total de demandes pour lesquelles les URL des paniers d’invités sont accessibles.

![guest-carts-activities](../../assets/tools/observation-for-adobe-commerce/guest-carts-activities.jpg)

## [!UICONTROL API – forgot password, create account by Countries]

L’image **[!UICONTROL API – forgot password, create account by Countries]** indique le nombre de comptes créés et de demandes de réinitialisation d’un mot de passe oublié au cours d’une période sélectionnée. Il est également mis en page pour indiquer le pays d’origine de la demande. Ce cadre est axé sur le pays d’origine de la demande.

![api-oublié-countries](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries.jpg)

## [!UICONTROL API - forgot password, create account by Countries and IP address]

L’image **[!UICONTROL API - forgot password, create account by Countries and IP address]** indique le nombre de comptes créés et de demandes de réinitialisation d’un mot de passe oublié au cours d’une période sélectionnée. Il est facetté pour afficher également l’adresse IP, l’URL consultée et le pays d’origine de la demande. Ce cadre est axé sur le nombre d’adresses IP.

![api-oublié-countries-ip](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries-ip.png)

## [!UICONTROL Guest cart activities by IP]

L’image **[!UICONTROL Guest cart activities by IP]** affiche les activités de panier d’invités par IP sur une période sélectionnée.

![guest-cart-ip](../../assets/tools/observation-for-adobe-commerce/guest-cart-ip.png)

## [!UICONTROL Guest cart activities by Countries]

L’image **[!UICONTROL Guest cart activities by Countries]** présente les activités de panier d’invités par pays sur une période sélectionnée.

![guest-cart-country](../../assets/tools/observation-for-adobe-commerce/guest-cart-country.png)
