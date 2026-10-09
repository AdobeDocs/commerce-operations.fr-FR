---
title: 'MDVA-39384 : impossible d’enregistrer l’attribut du client personnalisé pour l’utilisateur de la société'
description: Le correctif MDVA-39384 résout le problème où l’attribut client personnalisé pour un utilisateur d’entreprise n’est pas enregistré. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 est installé. L’ID du correctif est MDVA-39384. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.
feature: Attributes, B2B, Companies
role: Developer
exl-id: 0ccaa4c5-ca43-4b25-963b-b9a547ecc71f
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%
---
# MDVA-39384 : impossible d’enregistrer l’attribut du client personnalisé pour l’utilisateur de la société

Le correctif MDVA-39384 résout le problème où l’attribut client personnalisé pour un utilisateur d’entreprise n’est pas enregistré. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.2 est installé. L’ID du correctif est MDVA-39384. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.1 - 2.3.6, 2.4.1 - 2.4.3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’attribut client personnalisé d’un utilisateur d’entreprise n’est pas enregistré.

<u>Conditions préalables</u> :

Les modules B2B sont installés.

<u>Procédure à suivre </u> :

1. Accédez à **Magasins** > Paramètres > **Configuration** > **Fonctionnalités B2B** et définissez **Activer l’entreprise** sur Oui.
1. Créez un attribut client personnalisé :
   * Valeurs requises : Oui (facultatif, activez-la afin que l’erreur de validation s’affiche).
   * Afficher sur Storefront : Oui.
   * Forms à utiliser dans : tous les éléments disponibles dans la liste.
1. Créez une entreprise et connectez-vous en tant qu’administrateur d’entreprise.
1. Accédez à Structure de l’entreprise dans votre compte .
1. Cliquez sur le lien **Ajouter un utilisateur**.
1. Remplissez le formulaire en incluant l’attribut personnalisé.
1. Cliquez sur **Enregistrer**.

<u>Résultats attendus</u> :

Les valeurs d’attribut personnalisé sont enregistrées avec le nouvel utilisateur de la société.

<u>Résultats réels</u> :

Les valeurs d’attribut personnalisé NE sont PAS enregistrées avec le nouvel utilisateur de la société.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
