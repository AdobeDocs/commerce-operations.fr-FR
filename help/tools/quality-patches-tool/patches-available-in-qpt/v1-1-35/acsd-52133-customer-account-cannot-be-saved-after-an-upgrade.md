---
title: 'ACSD-52133 : impossible d’enregistrer le compte client après une mise à niveau'
description: Appliquez le correctif ACSD-52133 pour résoudre le problème d’Adobe Commerce en raison duquel un compte client ne peut pas être enregistré après une mise à niveau.
feature: Customers, Upgrade
role: Admin
exl-id: 4a0e6ed8-3e35-40ce-bb49-8ccfcde437a0
source-git-commit: 82667023bbaa9d725eb52dacb8bd47042bdfe028
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-52133 : impossible d’enregistrer le compte client après une mise à niveau

>[!NOTE]
>
>Ce correctif a été abandonné en raison d’un conflit avec le correctif de sécurité [APSB25-08](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-08).

Le correctif ACSD-52133 corrige le problème en raison duquel un compte client ne peut pas être enregistré après une mise à niveau. Ce correctif est disponible lorsque la version 1.1.35 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-52133. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le compte client ne peut pas être enregistré après une mise à niveau.

<u>Procédure à suivre </u> :

1. Installez Adobe Commerce version 2.4.4.
1. Créez un client.
1. Mettez à niveau Adobe Commerce vers la version 2.4.6 à partir de la version antérieure 2.4.4 où un client était déjà créé.
1. Définissez la clé de chiffrement comme indiqué ci-dessous dans `env.php` :

   `d337b914e91ff703b1e94ba4156aadf0`

1. Définissez les valeurs ci-dessous dans la base de données pour tout client sous le tableau `customer_entity` :

   ```
   -> rp_token as incr4869
   -> rp_token_created_at as "2021-04-29 20:06:14"
   ```

1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Modifiez le client pour lequel les valeurs ci-dessus ont été mises à jour.
1. Cliquez sur **[!UICONTROL Save Customer]** ou **[!UICONTROL Save and Continue Edit]**

<u>Résultats attendus</u> :

Le client est enregistré sans erreur.

<u>Résultats réels</u> :

* L’enregistrement du client n’est pas enregistré.
* Le message d’erreur suivant apparaît : *Un problème est survenu lors de l’enregistrement du client.*

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool]
* Adobe Commerce sur les infrastructures cloud : [ Mises à niveau et correctifs > Appliquer des correctifs ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances du support
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool]
* [Recommandations relatives à la modification des tables de base de données](https://experienceleague.adobe.com/fr/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel Commerce Implementation Playbook

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
