---
title: 'ACSD-63572 : les tables temporaires de l’indexeur « catalogrule » ne sont pas nettoyées si le processus de l’indexeur est terminé'
description: Appliquez le correctif ACSD-63572 pour résoudre le problème d’Adobe Commerce où les tables de l’indexeur ne sont pas nettoyées lorsque le processus a été arrêté en raison d’une mise à niveau du système ou d’un arrêt du [!UICONTROL CLI].
feature: System
Role: Admin, Developers
exl-id: 1cab7058-ca20-4d43-bfca-9b0e3ad35f42
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# ACSD-63572 : les tables temporaires de l’indexeur `catalogrule` ne sont pas nettoyées si le processus de l’indexeur est arrêté

Le correctif ACSD-63572 corrige le problème où les tables temporaires de l’indexeur ne sont pas nettoyées lorsque le processus a été arrêté en raison d’une mise à niveau du système ou d’un arrêt du [!UICONTROL CLI]. Ce correctif est disponible lorsque la version 1.1.58 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-63572. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p8

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les tables temporaires de l&#39;indexeur ne sont pas nettoyées lorsque le processus a été arrêté en raison d&#39;une mise à niveau du système ou d&#39;un arrêt dans [!UICONTROL CLI].

<u>Procédure à suivre </u> :

1. Ouvrez [!UICONTROL CLI].
1. Exécutez la commande : `bin/magento indexer:reindex catalogrule_rule`.
1. Annuler le processus avant la fin en utilisant : `^C`.
1. Réinitialiser les indexeurs en utilisant : `bin/magento indexer:reset catalogrule_rule catalogrule_product`.
1. Répétez plusieurs fois les étapes précédentes.
1. Recherchez les tables temporaires suivantes qui ont été créées dans la base de données :

   ```
   catalogrule_product__temp*
   catalogrule_product_price__temp*
   ```

<u>Résultats attendus</u> :

Les anciennes tables temporaires sont supprimées lorsqu&#39;elles ne sont pas nécessaires.

<u>Résultats réels</u> :

Les anciennes tables temporaires ne sont pas supprimées.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
