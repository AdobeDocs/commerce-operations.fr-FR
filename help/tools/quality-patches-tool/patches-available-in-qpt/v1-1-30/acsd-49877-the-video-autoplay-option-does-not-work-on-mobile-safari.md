---
title: 'ACSD-49877 : la lecture automatique de la vidéo ne fonctionne pas sur mobile [!DNL Safari]'
description: Appliquez le correctif ACSD-49877 pour résoudre le problème Adobe Commerce en raison duquel l’option de lecture automatique de la vidéo ne fonctionne pas sur mobile [!DNL Safari]  lorsque la vidéo est directement liée à un fichier vidéo distant.
feature: CMS
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-49877 : La lecture automatique de la vidéo ne fonctionne pas sur le périphérique mobile [!DNL Safari]

L’ACSD-49877 corrige le problème en raison duquel l’option de lecture automatique sur le mobile [!DNL Safari] ne fonctionne pas lorsque la vidéo est directement liée à un fichier vidéo distant. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.30 est installé. L’ID de correctif est ACSD-49877. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package [!magento/quality-Correctifs] vers la dernière version et vérifiez la compatibilité sur le [[!DNL Quality Patches Tool] : recherchez des correctifs]. Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La lecture automatique de la vidéo ne fonctionne pas sur le mobile [!DNL Safari] lorsque la vidéo est directement liée à un fichier vidéo distant et non à un service de diffusion en continu.

<u>Conditions préalables</u> :
Les modules [!DNL Page Builder] sont installés.

<u>Étapes à reproduire</u> :

1. Créez une page CMS et modifiez la **[!UICONTROL Content Value]** avec [!DNL Page Builder].
1. Ajoutez un élément *Tab* au contenu, puis un *élément vidéo* dans l’onglet *Tab*.
1. Cliquez maintenant sur le bouton d’engrenage pour modifier l’ *élément vidéo*.
1. Ajoutez un lien vers un fichier vidéo mp4 au champ [!UICONTROL Video URL].
1. Marquez le champ **[!UICONTROL Autoplay]** comme *Oui*.
1. Cliquez sur **[!UICONTROL Save]**.
1. Ouvrez la page récemment créée sur [!DNL Safari] à l’aide d’une iPhone.

<u>Résultats attendus</u>

L’option de lecture automatique fonctionne sur [!DNL Safari] à l’aide d’un iPhone.

<u>Résultats réels</u>

L’option de lecture automatique ne fonctionne pas sur [!DNL Safari] à l’aide d’un iPhone.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
