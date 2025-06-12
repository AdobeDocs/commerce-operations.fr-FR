---
title: 'ACSD-49013 : confirmation d’e-mail non traduite en paramètres régionaux du site web'
description: Appliquez le correctif ACSD-49013 pour résoudre le problème d’Adobe Commerce en raison duquel la confirmation par e-mail n’est pas traduite en paramètres régionaux du site web lors de la création de clients à l’aide de l’API en bloc.
feature: Admin Workspace, Communications
role: Admin
exl-id: 1b0dc6aa-d5ee-4adf-882d-88f29a7eab34
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-49013 : confirmation d’e-mail non traduite en paramètres régionaux du site web

Le correctif ACSD-49013 corrige le problème où la confirmation par e-mail n’est pas traduite en paramètres régionaux du site web lors de la création de clients à l’aide de l’API en bloc. Ce correctif est disponible lorsque la version 1.1.27 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-49013. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les e-mails de confirmation ne sont pas traduits en paramètres régionaux du site web lors de la création de clients utilisant l’API en bloc.

<u>Procédure à suivre </u> :

1. Installez un autre paramètre régional comme `de_DE`.
1. Configurez *RabbitMQ*.
1. Exécutez `bin/magento setup:upgrade` pour installer les files d’attente dans RabbitMQ et configurer le module linguistique.
1. Créez un site web supplémentaire dans [!UICONTROL Admin] > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**.
1. Définissez le paramètre régional de ce nouveau site web sur `de_DE` dans [!UICONTROL Admin] > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Locale Options]**.
1. Exécutez un appel API pour créer un compte client à l’aide de l’API en bloc. Utilisez la `website_id` correspondante.

   `Endpoint: /rest/async/bulk/V1/customers`

   ```
   [{
       "customer": {
       "email": "test@example.com",
       "firstname": "test",
       "lastname": "test",
       "website_id": 2
       },
       "password": "Passw0rd!"
   }]
   ```

1. Exécutez `bin/magento queue:consumers:start async.operations.all --single-thread --max-messages=10`.
1. Vous pouvez constater que le compte client est correctement créé sur le site web spécifié.
1. Vérifiez l’e-mail reçu pour l’enregistrement du client.

<u>Résultats attendus</u> :

Puisque le client est créé sur un site web spécifié, l’e-mail d’enregistrement est envoyé à l’aide des paramètres régionaux de ce site web.

<u>Résultats réels</u> :

Le client est créé correctement sur le site web spécifié, mais l’e-mail d’enregistrement est envoyé à l’aide du paramètre régional par défaut lorsque l’API en bloc est utilisée.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
