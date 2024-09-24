---
title: 'MDVA-41164 : impossible d’enregistrer ou de modifier la société avec des attributs de client personnalisés'
description: Le correctif MDVA-41164 résout le problème où l’utilisateur administrateur ne peut pas enregistrer ou modifier une entreprise avec des attributs client personnalisés de fichiers ou d’images de n’importe quel type. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.5 est installé. L’ID de correctif est MDVA-41164. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
feature: Admin Workspace, Attributes, B2B, Companies
role: Developer
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# MDVA-41164 : impossible d’enregistrer ou de modifier la société avec des attributs de client personnalisés

Le correctif MDVA-41164 résout le problème où l’utilisateur administrateur ne peut pas enregistrer ou modifier une entreprise avec des attributs client personnalisés de fichiers ou d’images de n’importe quel type. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.5 est installé. L’ID de correctif est MDVA-41164. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’utilisateur administrateur ne peut pas enregistrer ni modifier une société avec des attributs client personnalisés de fichiers ou d’images de n’importe quel type.

<u>Conditions préalables</u> :

Le module B2B est installé.

<u>Étapes à reproduire</u> :

1. Activez Entreprise dans **Magasins** > **Config** > **Fonctionnalités B2B**.
1. Créez un attribut du client dans **Magasins** > **Attributs** > **Clients** > **Ajouter un nouvel attribut** :
   * Type d’entrée : Fichier (pièce jointe)
   * Afficher sur Storefront : Oui
   * Ordre de tri : Tout
   * Forms à utiliser dans : sélectionnez toutes les
1. Créez une nouvelle société dans **Customers** > **Entreprises** > **Ajouter une nouvelle société** et téléchargez un fichier pour le nouvel attribut créé ci-dessus.

<u>Résultats attendus</u> :

L’utilisateur peut terminer la création de la société et la pièce jointe est téléchargée sans erreur.

<u>Résultats réels</u> :

* Vous recevez un message d&#39;erreur : *Quelque chose s&#39;est mal passé lors de l&#39;enregistrement du fichier.*
* Le journal des exceptions contient un enregistrement comme celui-ci :

  ```php
  report.CRITICAL: Notice: Undefined index: customer in
  ../app/code/Magento/Customer/Controller/Adminhtml/File/Customer/Upload.php on line 69
  ```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) .
