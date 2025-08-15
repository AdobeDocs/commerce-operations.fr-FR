---
title: 'ACSD-47027 : mise à jour B2B de requête lente [!UICONTROL CompanyRole] [!DNL GraphQL] update)'
description: Appliquez le correctif ACSD-47027 pour résoudre le problème d’Adobe Commerce lié à une mise à jour B2B [!UICONTROL CompanyRole] [!DNL GraphQL] requête lente).
feature: B2B, Companies, GraphQL, Roles/Permissions
role: Admin
exl-id: 91eb0297-1ba8-47b7-9581-29bee835843c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-47027 : mise à jour de [!UICONTROL CompanyRole] B2B à requête lente [!DNL GraphQL]

Le correctif ACSD-47027 résout le problème en raison duquel la mise à jour [!UICONTROL CompanyRole] de la [!DNL GraphQL] B2B de requête lente ne fonctionne pas comme prévu. Ce correctif est disponible lorsque la version 1.1.23 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-47027. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La mise à jour du [!UICONTROL CompanyRole] de [!DNL GraphQL] B2B de requête lente ne fonctionne pas comme prévu.

<u>Conditions préalables</u> :

Installez le module B2B .

<u>Procédure à suivre </u> :

1. Dans Adobe Commerce Admin, accédez à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configurations]** > **[!UICONTROL B2B Features]** et définissez **[!UICONTROL Enable Company]** sur _Oui_.
1. Accédez au serveur frontal et créez une entreprise.
1. Après vous être connecté en tant qu’utilisateur d’entreprise, accédez à **[!UICONTROL My Account]** > **[!UICONTROL Roles and Permissions]** et ajoutez un nouveau rôle.
1. Activez [!UICONTROL dev] journal des requêtes à l’aide de `bin/magento dev:que:enab`.
1. Envoyez maintenant la requête de [!DNL GraphQL] ci-dessous (l’identifiant est l’identifiant de rôle codé en [!UICONTROL base64]) :

   <pre><code>
   mutation &lbrace;
   updateCompanyRole(
      input: &lbrace;
         id: "Mg=="
         permissions: &lbrack;
         "Magento_Company::view"
         "Magento_Company::view_account"
         "Magento_Company::user_management"
         "Magento_Company::roles_view"
        &rbrack;
      &rbrace;
    ) &lbrace;
      role &lbrace;
         id

         name

         permissions &lbrace;
         id

         text

         children &lbrace;
            id

            text

            children &lbrace;
               id

               text
             &rbrace;
           &rbrace;
         &rbrace;
       &rbrace;
     &rbrace;
   &rbrace;
   </code></pre>

1. Vérifiez le journal des requêtes.
1. Vous pouvez constater que la requête ci-dessus est exécutée. Cette requête est exécutée en `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources`.

<u>Résultats attendus</u> :

Le `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources` doit être optimisé pour éviter de charger toutes les données disponibles dans la table de base de données **[!UICONTROL company_permissions]**.

<u>Résultats réels</u> :

Adobe Commerce exécute une requête sans aucun filtre. Lorsqu’il y a un grand nombre d’enregistrements, la préparation de la collecte de données par Adobe Commerce prend beaucoup de temps.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud . 

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
