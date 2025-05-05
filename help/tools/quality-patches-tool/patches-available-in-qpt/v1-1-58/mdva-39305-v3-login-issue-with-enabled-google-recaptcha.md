---
title: 'MDVA-39305-V3 : problème de connexion avec activé [!DNL Google reCAPTCHA]'
description: Appliquez le correctif MDVA-39305-V3 pour résoudre le problème d’Adobe Commerce en raison duquel les clients enregistrés ne peuvent pas se connecter lorsque  [!DNL Google reCAPTCHA]  est activé. Ce correctif corrige également le problème en raison duquel un formulaire peut être envoyé avant  [!DNL Google reCAPTCHA]  chargement complet. En outre, il corrige l’erreur *L’appel à une fonction membre isDisabled() sur null* lorsque des blocs sont utilisés à des emplacements autres que ceux par défaut sur une page CMS.
feature: Console
role: Admin
source-git-commit: 7846079987d2b7c0e9fdd0485bb3aae4f09cd6f9
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-39305-V3 : problème de connexion avec le [!DNL Google reCAPTCHA] activé

>[!NOTE]
>
>Ce correctif est une mise à jour du correctif [MDVA-39305](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-1/mdva-39305-login-issues-with-enabled-google-recaptcha.md).

Le correctif MDVA-39305-V3 corrige le problème en raison duquel les clients enregistrés ne peuvent pas se connecter lorsque [!DNL Google reCAPTCHA] est activé. Ce correctif corrige également le problème où un formulaire peut être envoyé avant le chargement complet de l’[!DNL Google reCAPTCHA]. En outre, il corrige l’erreur *Appel à une fonction membre isDisabled() sur null* lorsque des blocs sont utilisés à des emplacements autres que ceux par défaut sur une page CMS.

Ce correctif a été ajouté dans l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) version 1.1.48. Elle a été mise à jour dans la version QPT 1.1.58 afin d’inclure les nouvelles versions Adobe Commerce 2.4.7 à 2.4.7-p4. L’ID du correctif est MDVA-39305-V3. Notez que le problème a été corrigé dans les versions 2.4.4, 2.4.5-p2 et 2.4.7 d’Adobe Commerce.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4, 2.4.5-p2, 2.4.7

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p1 - 2.4.7-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Événements

### Cas I

1. Les clients enregistrés ne peuvent pas se connecter à l’aide du [!DNL Google reCAPTCHA] activé.
1. Un formulaire peut être envoyé avant le chargement complet de [!DNL Google reCAPTCHA].

<u>Procédure à suivre </u> :

1. Accédez à **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Security]** > **[!DNL Google reCAPTCHA Storefront]** et activez ***[!DNL Google reCAPTCHA]***.
1. Accédez au front-end.
1. Ouvrez **[!UICONTROL Developer Tool Console]** dans le navigateur.

<u>Résultats attendus</u> :

Aucun avertissement de CSP dans la console.

<u>Résultats réels</u> :

Avertissements de la CSP dans la console.

### Cas II

Une erreur indiquant *L’appel à une fonction membre estDisabled() sur null* est générée lorsque des blocs sont utilisés à des emplacements autres que ceux par défaut sur une page CMS.

<u>Procédure à suivre </u> :

1. Créez un bloc statique avec le contenu suivant :

   ```
   {{block class="Magento\Newsletter\Block\Subscribe" name="home.form.subscribe"
   template="Magento_Newsletter::subscribe.phtml"}}
   ```

1. Ajoutez un bloc statique dans une page CMS à partir de **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]** > **[!UICONTROL Add/Edit CMS page]** > **[!UICONTROL Content]**.
1. Enregistrez la page.

<u>Résultats attendus</u> :

La page se charge sans erreur.

<u>Résultats réels</u> :

Une erreur 500 se produit sur la page du storefront.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .


