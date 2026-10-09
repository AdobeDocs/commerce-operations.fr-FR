---
title: 'ACSD-49877 : la lecture automatique de la vidéo ne fonctionne pas sur les [!DNL Safari] mobiles'
description: Appliquez le correctif ACSD-49877 pour résoudre le problème d’Adobe Commerce en raison duquel l’option de lecture automatique de la vidéo ne fonctionne pas sur les [!DNL Safari] mobiles lorsque la vidéo est directement liée à un fichier vidéo distant.
feature: CMS
role: Admin
exl-id: aa2557e2-4bed-4004-b9bc-36c59f1e9cdc
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: ddbd0f6e-b569-5a04-8a70-55058777c373
    internal-label: CMS
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%
---
# ACSD-49877 : la lecture automatique de la vidéo ne fonctionne pas sur les [!DNL Safari] mobiles

L’ACSD-49877 corrige le problème en raison duquel l’option de lecture automatique sur les [!DNL Safari] mobiles ne fonctionne pas lorsque la vidéo est directement liée à un fichier vidéo distant. Ce correctif est disponible lorsque la version 1.1.30 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-49877. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package [!magento/quality-patches] vers la dernière version et vérifiez la compatibilité sur le [[!DNL Quality Patches Tool] : Rechercher des correctifs]. Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La lecture automatique de la vidéo ne fonctionne pas sur les [!DNL Safari] mobiles lorsque la vidéo est directement liée à un fichier vidéo distant et non à un service de diffusion en continu.

<u>Conditions préalables</u> :
Les modules [!DNL Page Builder] sont installés.

<u>Procédure à suivre </u> :

1. Créez une page CMS et modifiez la **[!UICONTROL Content Value]** avec [!DNL Page Builder].
1. Ajoutez un élément *Tab* au contenu et ajoutez un élément *Video* dans l’*Tab*.
1. Cliquez maintenant sur le bouton d’engrenage pour modifier l’*Élément vidéo*.
1. Ajoutez un lien vers un fichier vidéo mp4 au champ [!UICONTROL Video URL] .
1. Marquez le champ **[!UICONTROL Autoplay]** comme *Oui*.
1. Cliquez sur **[!UICONTROL Save]**.
1. Ouvrez la page récemment créée sur [!DNL Safari] à l’aide d’une iPhone.

<u>Résultats attendus</u>

L’option de lecture automatique fonctionne sur les [!DNL Safari] à l’aide d’une iPhone.

<u>Résultats réels</u>

L’option de lecture automatique ne fonctionne pas sur les [!DNL Safari] utilisant un iPhone.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
