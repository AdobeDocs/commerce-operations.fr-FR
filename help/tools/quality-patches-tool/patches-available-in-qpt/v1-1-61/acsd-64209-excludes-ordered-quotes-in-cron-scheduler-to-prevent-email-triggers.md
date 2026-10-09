---
title: 'ACSD-64209 : le planificateur Cron récupère les devis négociables sans exclure les devis [!UICONTROL Ordered]'
description: Appliquez le correctif ACSD-64209 pour résoudre le problème d’Adobe Commerce où le planificateur cron récupère toutes les guillemets négociables sans exclure ceux dont le statut est [!UICONTROL Ordered], ce qui entraîne le déclenchement d’un e-mail ou d’e-mails.
feature: B2B, Communications
role: Admin, Developer
exl-id: 51ba0edc-ad0c-4e32-acd7-2337a62bff53
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bb03f6c4-cab9-560e-9d02-5816e1808d17
    internal-label: Communications
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 4a03af2383a03584c88feb83e7ad726a42cab2d6
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%
---
# ACSD-64209 : le planificateur Cron récupère les devis négociables sans exclure les devis [!UICONTROL Ordered]

Le correctif ACSD-64209 corrige le problème en raison duquel le planificateur cron récupère tous les devis négociables sans exclure ceux dont le statut est **[!UICONTROL Ordered]**, ce qui entraîne le déclenchement d’un e-mail ou d’e-mails. Ce correctif est disponible lorsque la version 1.1.61 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-64209. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le planificateur cron récupère tous les devis négociables sans exclure ceux qui ont le statut **[!UICONTROL Ordered]**, ce qui déclenche l’envoi d’un e-mail ou d’e-mails.

<u>Procédure à suivre </u> :


1. Sur la barre latérale *Admin*, accédez à **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL B2B Features]** et activez les devis d’entreprise et B2B.
1. Définissez **[!UICONTROL Default Expiration Period]** sur *1* dans *Admin* > **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** > **[!UICONTROL General]**.
1. Créez une société, activez-la et connectez-vous en tant qu’administrateur de société.
1. Ajoutez un produit au panier.
1. Demandez un devis.
1. Dans la barre latérale *Admin*, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.
1. Sélectionnez le devis créé, puis cliquez sur **[!UICONTROL Send]** pour renvoyer le devis à l&#39;acheteur.
1. Connectez-vous en tant qu’administrateur d’entreprise sur le storefront.
1. Sélectionnez le devis et cliquez sur **[!UICONTROL Proceed to checkout]** pour terminer l&#39;achat.
1. Vérifiez que le statut du devis est **[!UICONTROL Ordered]** et qu&#39;aucune autre action n&#39;est possible sur le storefront.
1. Déclenchez la tâche cron `negotiable_quote_send_emails`.


<u>Résultats attendus</u> :

Étant donné que le devis a été commandé et qu’aucune autre action ne peut être entreprise, aucun e-mail concernant l’expiration du devis ne doit être envoyé.

<u>Résultats réels</u> :

Un e-mail *Le devis expire bientôt* est envoyé.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
