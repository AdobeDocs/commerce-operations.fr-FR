---
title: 'ACSD-51120 : le cache de demandes du GET GraphQL n’est pas effacé pour les pages CMS qui contiennent des blocs CMS'
description: Appliquez le correctif ACSD-51120 pour résoudre le problème d’Adobe Commerce où le cache de requête GraphQL GET n’est pas effacé pour les pages CMS qui contiennent des blocs CMS.
exl-id: e1b84db0-2441-4729-aeeb-8486a623aebf
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-51120 : le cache de demandes du GET GraphQL n’est pas effacé pour les pages CMS qui contiennent des blocs CMS

Le correctif ACSD-51120 corrige le problème en raison duquel le cache de requête GraphQL GET n’est pas effacé pour les pages CMS qui contiennent des blocs CMS mis à jour par le biais d’une mise à jour d’évaluation. Ce correctif est disponible lorsque la version 1.1.33 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-51120. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le cache de requêtes de GET GraphQL n’est pas effacé pour les pages CMS qui contiennent des blocs CMS mis à jour par le biais d’une mise à jour d’évaluation.

<u>Procédure à suivre </u> :

1. Créez un bloc CMS.
1. Incluez le bloc CMS dans une page CMS à l’aide de l’[!DNL Page Builder] .
1. Récupérez la page CMS à l’aide de la requête GraphQL donnée à l’aide d’une requête GET :

   ```GraphQL
   {
   cmsPage( identifier: "<CMS PAGE IDENTIFIER>") {
       content
       content_heading
       identifier
       meta_description
       meta_keywords
       meta_title
       page_layout
       title
       url_key
   }
   }
   ```

1. Assurez-vous que la réponse de GraphQL est mise en cache dans [!DNL Varnish].
1. Créez une mise à jour planifiée pour le bloc.
1. Attendez que la mise à jour planifiée s’applique et exécutez la tâche cron pour appliquer la mise à jour planifiée.
1. Récupérez à nouveau la page CMS à l’aide de la requête GraphQL donnée à l’aide d’une requête GET.

<u>Résultats attendus</u> :

La réponse affiche le contenu mis à jour.

<u>Résultats réels</u> :

La réponse affiche toujours l’ancien contenu.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
