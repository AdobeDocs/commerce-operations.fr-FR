---
title: 'ACSD-65684 : la mise à niveau de Magento_Company dans B2B 1.5.2 est lente avec plus de 100 000 enregistrements dans company_structure'
description: Appliquez le correctif ACSD-65684 pour résoudre le problème d’Adobe Commerce où la mise à niveau du module Magento_Company dans B2B 1.5.2 prend trop de temps en raison du traitement d’un grand nombre d’enregistrements (~100 000+) dans la table company_structure.
feature: B2B
role: Admin, Developer
type: Troubleshooting
exl-id: 1b45ebe4-4fb4-4fb5-b107-a2d44ec784e0
source-git-commit: b1912bbc5aabd36067563326ee5c6bb84e14441d
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-65684 : la mise à niveau de `Magento_Company` dans [!DNL B2B] 1.5.2 est lente avec plus de 100 000 enregistrements dans `company_structure`

Le correctif ACSD-65684 corrige un problème de performances en raison duquel la mise à niveau du module `Magento_Company` dans la [!DNL B2B] 1.5.2 prend trop de temps lors du traitement de plus de 100 000 enregistrements dans la table `company_structure`. Ce correctif est disponible lorsque la version 1.1.64 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-65684. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce B2B (toutes les méthodes de déploiement) 1.5.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce B2B (toutes les méthodes de déploiement) 1.5.2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Problème de performance en raison duquel la mise à niveau du module `Magento_Company` dans la [!DNL B2B] 1.5.2 prend trop de temps lors du traitement de plus de 100 000 enregistrements dans la table `company_structure`.

<u>Procédure à suivre </u> :

1. Installez Adobe Commerce 2.4.7-p4 avec [!DNL B2B].
1. Ajoutez 100 000 enregistrements à `company_structure` table.
1. Mise à niveau vers Adobe Commerce 2.4.7-p5 et le dernier module [!DNL B2B] (1.5.2).
1. Appliquez le correctif ACSD-65540.
1. Exécuter :

```
bin/magento setup:upgrade
```

<u>Résultats attendus</u> :

`setup:upgrade` termine dans un délai raisonnable.

<u>Résultats réels</u> :

`setup:upgrade` prend beaucoup trop de temps.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
