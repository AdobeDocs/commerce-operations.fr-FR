---
title: 'ACSD-62951 : corrige les éléments et les totaux manquants dans les e-mails [!UICONTROL Credit Memo] envoyés via l’API REST'
description: Appliquez le correctif ACSD-62951 pour résoudre le problème d’Adobe Commerce en raison duquel l’e-mail [!UICONTROL Credit Memo] est envoyé sans inclure les éléments de commande et les totaux.
feature: REST
role: Admin, Developer
source-git-commit: bfefe2bbe2046bda967b0a14f238919452935400
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-62951 : corrige les éléments et les totaux manquants dans les e-mails *[!UICONTROL Credit Memo]* envoyés via l’API REST

Le correctif ACSD-62951 corrige le problème d’envoi de l[!UICONTROL Credit Memo]e-mail sans inclure les éléments de commande et les totaux. Ce correctif est disponible lorsque la version 1.1.57 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-62951. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p10

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’e-mail de *[!UICONTROL Credit Memo]* envoyé lorsqu’un avoir est créé via l’API REST `POST V1/order/:orderId/refund` n’inclut pas les éléments de commande et les totaux.

<u>Procédure à suivre </u> :

1. Créez une commande avec n’importe quel produit.
1. Expédiez et facturez la commande. Assurez-vous que l’e-mail de facture est envoyé et qu’il inclut les détails du produit.
1. Générez un jeton d’administration à l’aide du client API.
1. Utilisez le jeton pour créer un avoir via l’API REST.
   1. Point d’entrée : `POST V1/order/:orderId/refund`
   1. Payload de requête :

      ```
      {  
          "notify": true,  
          "items": [  
              {  
                  "order_item_id": 1,  
                  "qty": 1  
              }  
          ]  
      }  
      ```

<u>Résultats attendus</u> :

L’e-mail de *[!UICONTROL Credit Memo]* doit inclure les éléments et totaux remboursés

<u>Résultats réels</u> :

L’e-mail *[!UICONTROL Credit Memo]* ne contient aucun élément ou total, ce qui entraîne des informations incomplètes.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-Premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
