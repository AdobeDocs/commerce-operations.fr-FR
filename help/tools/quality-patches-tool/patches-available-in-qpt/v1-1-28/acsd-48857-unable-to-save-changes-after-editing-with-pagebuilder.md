---
title: 'ACSD-48857 : impossible d’enregistrer les modifications après modification avec  [!DNL Page Builder]'
description: Appliquez le correctif ACSD-48857 pour résoudre le problème d’Adobe Commerce en raison duquel l’utilisateur ne peut pas enregistrer les modifications après les avoir modifiées avec  [!DNL Page Builder].
feature: Admin Workspace, CMS, Page Builder
role: Admin
exl-id: b03cd597-8fef-4528-9699-793dc61d34da
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-48857 : impossible d’enregistrer les modifications après modification avec [!DNL Page Builder]

Le correctif ACSD-48857 corrige le problème en raison duquel l’utilisateur ne peut pas enregistrer les modifications après les avoir modifiées avec [!DNL Page Builder]. Ce correctif est disponible lorsque la version 1.1.28 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-48857. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’utilisateur ne peut pas enregistrer les modifications après les avoir modifiées avec [!DNL Page Builder].

<u>Procédure à suivre</u>

1. Connectez-vous au site Web de l’administrateur.
1. Accédez à **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** pour créer une page CMS vide.
1. Exécutez ce script SQL pour définir la valeur du champ **[!UICONTROL Content]** suivante :

   ```SQL
   update cms_page set content = '<div data-content-type="text" data-appearance="default" data-element="main"><h4 style="text-align: center;" contenteditable="true" data-placeholder="Edit Heading Text" data-content-type="heading" data-appearance="default" data-element="main">THE RULES</h4></div>' where page_id=8;
   ```

1. Revenez à **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** dans Admin.
1. Modifiez votre page.
1. Accédez à l’onglet **[!UICONTROL Content]** .
1. Cliquez sur **[!UICONTROL Save]**.

<u>Résultats attendus</u>

L’assainissement du contenu HTML est mis en œuvre. Cela supprime [!DNL Page Builder] attributs HTML réservés dans le contenu généré par l’éditeur de texte.

<u>Résultats réels</u>

La page n’est pas enregistrée et le chargeur continue de tourner. Dans la console, l’erreur suivante est générée :

```
[ERROR] Page Builder was rendering for 5 seconds without releasing locks.
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
