---
title: 'ACSD-51892 : problème de performances lorsque les fichiers de configuration se chargent plusieurs fois'
description: Appliquez le correctif ACSD-51892 pour résoudre le problème de performances d’Adobe Commerce où les fichiers de configuration se chargent plusieurs fois pendant le déploiement.
feature: Observability
role: Admin
exl-id: ef3d3b85-b6a0-4037-95c0-e84125fa9088
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4239b8a6-e74f-567d-a7a5-b98b9ead0ea4
    internal-label: Observability
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%
---
# ACSD-51892 : problème de performances lorsque les fichiers de configuration se chargent plusieurs fois

Le correctif ACSD-51892 corrige le problème de performances qui résulte du chargement des fichiers `app/etc/env.php` et `app/etc/config.php` chaque fois que les valeurs de configuration de déploiement sont accessibles dans une seule requête. La lecture excessive des fichiers met le système à rude épreuve, ce qui entraîne une dégradation des performances globales. Ce correctif est disponible lorsque la version 1.1.33 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-51892. Notez que le problème a été résolu dans Adobe Commerce 2.4.6-p2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Il existe un problème de performances en raison duquel les fichiers de configuration se chargent plusieurs fois.

<u>Procédure à suivre </u> :

1. Effectuez le déploiement ou la mise à niveau vers Adobe Commerce 2.4.6 ou une version ultérieure.
1. Vérifiez les journaux du système de fichiers pour accéder aux fichiers `app/etc/env.php` et `app/etc/config.php` pendant l’exécution du déploiement.

<u>Résultats attendus</u> :

Le déploiement a réussi dans les délais impartis.

<u>Résultats réels</u> :

* Les serveurs ont du mal à répondre aux commandes que vous saisissez. Cela entraîne l’*erreur 503 du délai d’expiration du premier octet* lors de l’accès au site web.
* Les fichiers journaux contiennent plusieurs entrées ayant accès aux fichiers `app/etc/env.php` et `app/etc/config.php`.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
