---
title: "ACSD-51120 : cache de requête de GET GraphQL non effacé pour les pages CMS qui contiennent des blocs CMS"
description: Appliquez le correctif ACSD-51120 pour résoudre le problème Adobe Commerce en raison duquel le cache de demande de GET GraphQL n’est pas effacé pour les pages CMS qui contiennent des blocs CMS.
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-51120 : cache de requête de GET GraphQL non effacé pour les pages CMS contenant des blocs CMS

Le correctif ACSD-51120 corrige le problème en raison duquel le cache de demande de GET GraphQL n’est pas effacé pour les pages CMS qui contiennent des blocs CMS mis à jour par le biais d’une mise à jour intermédiaire. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.33 est installé. L’ID de correctif est ACSD-51120. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le cache de requête de GET GraphQL n’est pas effacé pour les pages CMS qui contiennent des blocs CMS mis à jour par le biais d’une mise à jour intermédiaire.

<u>Étapes à reproduire</u> :

1. Créez un bloc CMS.
1. Insérez le bloc CMS dans une page CMS à l’aide de [!DNL Page Builder].
1. Récupérez la page CMS à l’aide de la requête GraphQL donnée à l’aide d’une demande de GET :

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

1. Assurez-vous que la réponse GraphQL est mise en cache dans [!DNL Varnish].
1. Créez une mise à jour planifiée pour le bloc.
1. Attendez que la mise à jour planifiée s’applique et exécute la tâche cron pour appliquer la mise à jour planifiée.
1. Récupérez à nouveau la page CMS à l’aide de la requête GraphQL donnée à l’aide d’une requête GET.

<u>Résultats attendus</u> :

La réponse affiche le contenu mis à jour.

<u>Résultats réels</u> :

La réponse affiche toujours l’ancien contenu.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
