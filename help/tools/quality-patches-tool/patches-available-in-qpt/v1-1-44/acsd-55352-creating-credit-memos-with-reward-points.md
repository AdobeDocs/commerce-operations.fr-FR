---
title: 'ACSD-55352 : Création d''avoirs avec des points de récompense'
description: Appliquez le correctif ACSD-55352 pour résoudre le problème d’Adobe Commerce où, après la création d’un avoir partiel avec des points de récompense client, le statut de la commande passe à *fermé* et les options d’avoir disparaissent de la page de commande de l’administrateur.
feature: Checkout, Orders
role: Admin, Developer
exl-id: bee0c4be-11ec-4dcb-9b3c-7af26676cee9
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-55352 : Création d&#39;avoirs avec des points de récompense

Le correctif ACSD-55352 corrige le problème suivant : après la création d&#39;un avoir partiel avec des points de récompense client, le statut de la commande passe à *fermé* et les options d&#39;avoir disparaissent de la page de commande de l&#39;administrateur. Ce correctif est disponible lorsque la version 1.1.44 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-55352. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Après avoir créé un avoir partiel avec des points de récompense client, le statut de la commande passe à *fermé* et les options d&#39;avoir disparaissent de la page de commande de l&#39;administrateur.

<u>Procédure à suivre </u> :

1. Connectez-vous à l’administration Adobe Commerce.
2. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Other Setting]** > **[!UICONTROL Reward Exchange Rates]** > **[!UICONTROL Add New Rate]**.
3. Ajoutez deux taux :
   * *[!UICONTROL First]* :
      * *[!UICONTROL Direction]* = *Points dans la devise*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
   * *[!UICONTROL Second]* :
      * *[!UICONTROL Direction]* = *Devise en points*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
4. Créez un produit simple au prix de *$100* et avec *Qté* : *100*.
5. Créez un client à partir du storefront.
6. Revenez sur le serveur principal : **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** > **[!UICONTROL Edit]** > **[!UICONTROL Reward Points]** > **[!UICONTROL Update Points]** > Ajouter *100* et enregistrez le client.
7. Accédez au storefront et connectez-vous en tant que client créé précédemment.
8. Ajoutez le produit au panier avec *Qté* : *10*.
9. Accédez à **[!UICONTROL Checkout]** et utilisez les points de récompense *100* disponibles lorsque vous y êtes invité et passez la commande.
10. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice]** et expédiez cette commande.
11. Accédez à [!UICONTROL Credit Memo] et mettez à jour la *Qté à rembourser* sur *8*.
12. Cochez la case **[!UICONTROL Refund Reward Points]** et cliquez sur **[!UICONTROL Refund offline]**.
13. Essayez de rembourser les deux autres produits restants de la commande, en utilisant le [!UICONTROL Credit Memo].

<u>Résultats attendus</u> :

* L’administrateur crée des [!UICONTROL Credit Memo] pour renvoyer les deux produits restants.
* Le statut de la commande est *Terminé*.

<u>Résultats réels</u> :

* Impossible de créer d&#39;autres [!UICONTROL Credit Memo].
* Le statut de la commande est *Fermé*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
