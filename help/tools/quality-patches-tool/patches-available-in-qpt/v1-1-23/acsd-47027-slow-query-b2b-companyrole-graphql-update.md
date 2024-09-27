---
title: 'ACSD-47027 : requête lente B2B [!UICONTROL CompanyRole] [!DNL GraphQL] update'
description: Appliquez le correctif ACSD-47027 pour résoudre le problème Adobe Commerce en cas de mise à jour lente de la requête B2B [!UICONTROL CompanyRole] [!DNL GraphQL] .
feature: B2B, Companies, GraphQL, Roles/Permissions
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-47027 : mise à jour de la requête lente B2B [!UICONTROL CompanyRole] [!DNL GraphQL]

Le correctif ACSD-47027 résout le problème où la mise à jour de la requête lente B2B [!UICONTROL CompanyRole] [!DNL GraphQL] ne fonctionne pas comme prévu. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.23 est installé. L’ID de correctif est ACSD-47027. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La mise à jour de la requête lente B2B [!UICONTROL CompanyRole] [!DNL GraphQL] ne fonctionne pas comme prévu.

<u>Conditions préalables</u> :

Installez le module B2B.

<u>Étapes à reproduire</u> :

1. Dans l’administrateur Adobe Commerce, accédez à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configurations]** > **[!UICONTROL B2B Features]** et définissez **[!UICONTROL Enable Company]** sur _Oui_.
1. Positionnez-vous au front-end et créez une société.
1. Une fois connecté en tant qu’utilisateur de la société, accédez à **[!UICONTROL My Account]** > **[!UICONTROL Roles and Permissions]** et ajoutez un nouveau rôle.
1. Activez le journal de requête [!UICONTROL dev] à l’aide de `bin/magento dev:que:enab`.
1. Maintenant, envoyez la demande [!DNL GraphQL] ci-dessous (id est l&#39;ID de rôle encodé [!UICONTROL base64]) :

   <pre><code>
   mutation {
   updateCompanyRole(
      input: {
         id: "Mg=="
         permissions: [
         "Magento_Company::view"
         "Magento_Company::view_account"
         "Magento_Company::user_management"
         "Magento_Company::roles_view"
        ]
      }
    ) {
      role {
         id

         name

         permissions {
         id

         text

         children {
            id

            text

            children {
               id

               text
             }
           }
         }
       }
     }
   }
   </code></pre>

1. Vérifiez le journal des requêtes.
1. Vous pouvez constater que la requête ci-dessus est exécutée. Cette requête est exécutée dans `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources`.

<u>Résultats attendus</u> :

`app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources` doit être optimisé pour éviter de charger toutes les données disponibles dans la table **[!UICONTROL company_permissions]** DB.

<u>Résultats réels</u> :

Adobe Commerce exécute une requête sans aucun filtre. Lorsqu’il y a un grand nombre d’enregistrements, la préparation de la collecte de données par Adobe Commerce prend beaucoup de temps.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure. 

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
