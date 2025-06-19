---
title: 'ACSD-57086 : les commandes provenant de sites Web autres que ceux par défaut dont les conditions générales sont activées sont traitées de manière incorrecte'
description: Appliquez le correctif ACSD-57086 pour résoudre le problème d’Adobe Commerce en raison duquel les commandes passées à partir de sites web autres que ceux par défaut dont les conditions générales sont activées ne sont pas traitées correctement.
feature: Orders
role: Admin, Developer
exl-id: d9f2ef50-12c4-4a2d-b140-dfd0e8948fd3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# ACSD-57086 : les commandes provenant de sites Web autres que ceux par défaut dont les conditions générales sont activées sont traitées de manière incorrecte

Le correctif ACSD-57086 corrige le problème en raison duquel les commandes passées à partir de sites Web autres que ceux par défaut dont les conditions générales sont activées ne sont pas traitées correctement. Ce correctif est disponible lorsque la version 1.1.49 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-57086. Ce problème a été résolu dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lors de l’utilisation d’une configuration multi-magasin avec traitement AsyncOrder, les commandes passées sur des sites web/magasins autres que le site web principal sont rejetées en raison de problèmes de gestion de l’étendue dans le code de client de la file d’attente.

<u>Procédure à suivre </u> :

1. Installez [!DNL RabbitMQ] et exécutez `bin/magento setup:upgrade` pour créer les files d’attente pour les [!DNL RabbitMQ].
1. Configurez le traitement AsyncOrder avec :

   ```bash
   bin/magento setup:config:set --checkout-async 1
   ```

1. Créez un site web secondaire, un magasin et une vue de magasin.
1. Créez un produit partagé entre les deux sites web.
1. Activer les termes et conditions :
   1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]**.
   1. Définissez *[!UICONTROL Enable Terms And Conditions]* sur *Oui*.
1. Configurez les conditions générales des deux sites web :
   1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Terms And Conditions]** > **[!UICONTROL Add New Condition]**.
   1. Utilisez les paramètres suivants :
      * *[!UICONTROL Condition Name]* : *N&#39;importe quoi*
      * *[!UICONTROL Status]* : *[!UICONTROL Enabled]*
      * *[!UICONTROL Applied]* : *[!UICONTROL Manually]*
      * *[!UICONTROL Store View]* : *[!UICONTROL Default Store View]*
   1. Créez une autre condition pour la deuxième vue de site web/magasin.
1. Modifiez le site web par défaut en accédant à **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**. Cliquez sur le deuxième site web, vérifiez *[!UICONTROL Set as Default]* et enregistrez.
1. Effacez le cache avec :

   ```bash
   bin/magento cache:clear
   ```

1. Accédez à la vitrine et ajoutez un produit au panier. Passer en caisse et passer une commande (vous devriez voir une case à cocher à l&#39;étape du mode de paiement pour accepter les conditions générales).
1. Revenez à Admin après avoir passé la commande, puis redéfinissez le site web par défaut sur le site web principal d’origine et enregistrez.
1. Effacez le cache :

   ```bash
   bin/magento cache:clear
   ```

1. Exécutez la commande suivante pour démarrer le client de file d’attente :

   ```bash
   bin/magento queue:cons:start placeOrderProcessor
   ```

<u>Résultats attendus</u> :

La commande est exécutée ; elle n’est pas automatiquement rejetée.

<u>Résultats réels</u> :

Le statut de la commande est *rejeté* avec le commentaire suivant :

*La commande n&#39;a pas été passée. Tout d&#39;abord, acceptez les termes et conditions, puis essayez de passer à nouveau votre commande.*

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
