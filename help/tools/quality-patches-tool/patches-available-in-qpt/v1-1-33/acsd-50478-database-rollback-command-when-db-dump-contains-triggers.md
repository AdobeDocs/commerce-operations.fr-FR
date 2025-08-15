---
title: 'ACSD-50478 : problème JS de l’action de restauration dans la grille des sauvegardes et la commande de restauration de la base de données'
description: Appliquez le correctif ACSD-50478 pour résoudre le problème JS de l’action de restauration dans la grille des sauvegardes et la commande de restauration de la base de données dans le cas où l’image mémoire de la base de données contient des déclencheurs et une commande SQL de *délimiteur*.
exl-id: 2f47fbf6-44fc-487c-91fe-6e2e52fcdb2b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-50478 : problème JS de l’action de restauration dans la grille des sauvegardes et la commande de restauration de la base de données

Le correctif ACSD-50478 corrige le problème JS de l’action de restauration dans la grille des sauvegardes et la commande de restauration de la base de données dans le cas où l’image mémoire de la base de données contient des déclencheurs et une commande SQL *délimiteur*. Ce correctif est disponible lorsque la version 1.1.33 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-50478. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.4-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Problème JS de l’action de restauration dans la grille Sauvegardes et la commande de restauration de la base de données pour un cas où l’image mémoire de la base de données contient des déclencheurs et une commande SQL *délimiteur*.

<u>Procédure à suivre </u> :

1. Définissez les indexeurs en mode [!UICONTROL Update on Schedule] afin que les déclencheurs soient créés dans la base de données.
1. Activez la fonctionnalité de sauvegarde à partir de la ligne de commande :

   `bin/magento config:set system/backup/functionality_enabled 1`

1. Accédez à **Système** > **Outils** > **Sauvegardes** et générez une sauvegarde de base de données.
1. Ouvrez la console du navigateur ; l’erreur suivante s’affiche :

   ```
   Uncaught SyntaxError: Unexpected token '&' (at (index):606:32)
   
   function eventListener8jtGaqtgG2 () {
   
           return backup.rollback(&#039;db&#039;, &#039;1678391644&#039;);
   ```

1. Essayez d&#39;importer la base de données à partir de la ligne de commande :

   `bin/magento setup:rollback --db-file="<filename>"`

1. L’erreur suivante s’affiche :

   ```
   Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'delimiter' at line 1, query was: delimiter ;;
   ```

<u>Résultats attendus</u> :

La restauration de la base de données s’effectue correctement à partir de l’Administration et de la ligne de commande.

<u>Résultats réels</u> :

Vous avez observé les erreurs mentionnées aux étapes 4 et 6.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
