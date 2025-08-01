---
title: 'MDVA-41164 : impossible d’enregistrer ou de modifier la société avec des attributs de client personnalisés'
description: Le correctif MDVA-41164 résout le problème où l’utilisateur administrateur n’est pas en mesure d’enregistrer ou de modifier une société avec des attributs client personnalisés de fichiers ou d’images de n’importe quel type. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 est installé. L’ID du correctif est MDVA-41164. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.
feature: Admin Workspace, Attributes, B2B, Companies
role: Developer
exl-id: 9d1792e0-ba7b-444b-b1b1-771fd0e328eb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# MDVA-41164 : impossible d’enregistrer ou de modifier la société avec des attributs de client personnalisés

Le correctif MDVA-41164 résout le problème où l’utilisateur administrateur n’est pas en mesure d’enregistrer ou de modifier une société avec des attributs client personnalisés de fichiers ou d’images de n’importe quel type. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 est installé. L’ID du correctif est MDVA-41164. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’utilisateur administrateur ne peut pas enregistrer ni modifier une société avec des attributs client personnalisés de fichiers ou d’images de n’importe quel type.

<u>Conditions préalables</u> :

Module B2B installé.

<u>Procédure à suivre </u> :

1. Activez la société dans **Magasins** > **Configuration** > **Fonctionnalités B2B**.
1. Créez un attribut client dans **Magasins** > **Attributs** > **Clients** > **Ajouter un nouvel attribut** :
   * Type d’entrée : Fichier (pièce jointe)
   * Afficher sur Storefront : Oui
   * Ordre de tri : Tous
   * Forms à utiliser dans : tout sélectionner
1. Créez une nouvelle société dans **Clients** > **Sociétés** > **Ajouter une nouvelle société** et téléchargez un fichier pour le nouvel attribut créé ci-dessus.

<u>Résultats attendus</u> :

L’utilisateur peut terminer la création de la société et la pièce jointe est téléchargée sans erreur.

<u>Résultats réels</u> :

* Un message d’erreur s’affiche : *Un problème est survenu lors de l’enregistrement du fichier.*
* Le journal des exceptions contient un enregistrement tel que celui-ci :

  ```php
  report.CRITICAL: Notice: Undefined index: customer in
  ../app/code/Magento/Customer/Controller/Adminhtml/File/Customer/Upload.php on line 69
  ```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
