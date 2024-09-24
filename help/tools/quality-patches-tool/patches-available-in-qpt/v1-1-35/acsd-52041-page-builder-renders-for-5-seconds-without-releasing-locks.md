---
title: "ACSD-52041 : le rendu du générateur de pages ne libère pas les verrous"
description: Appliquez le correctif ACSD-52041 pour résoudre le problème Adobe Commerce en raison duquel le générateur de pages s’affiche pendant cinq secondes sans déclencher de verrous.
feature: Page Builder
role: Admin, Developer
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# ACSD-52041 : Le rendu du générateur de pages ne libère pas les verrous

Le correctif ACSD-52041 corrige le problème de rendu de Page Builder pendant cinq secondes sans relâcher de verrous. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.48 est installé. L’ID de correctif est ACSD-52041-v2. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.4-p5, 2.4.5 - 2.4.5-p4 et 2.4.6 - 2.4.6-p2.



>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.


## Problème

Le **[!DNL Page Builder]** effectue le rendu pendant *5* secondes sans relâcher les verrous.

<u>Étapes à reproduire</u> :

1. Modifiez une page CMS, une page de produit ou tout autre élément qui comporte **[!DNL Page Builder]**.
1. Enregistrez les modifications.
1. Remarquez le temps d’économie de la page.

<u>Résultats attendus</u>

Le contenu est enregistré. Aucune erreur n’est trouvée dans le journal du navigateur.

<u>Résultats réels</u>

L’enregistrement prend plus de temps que la durée habituelle.
Erreur dans la console : ``Page Builder was rendering for 5 seconds without releasing locks``

## Appliquer le correctif

Pour appliquer des correctifs individuels pour les versions **2.4.4 - 2.4.4-p5, 2.4.5 - 2.4.5-p4 et 2.4.6 - 2.4.6-p2**, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) dans le guide [!DNL Quality Patches Tool].
