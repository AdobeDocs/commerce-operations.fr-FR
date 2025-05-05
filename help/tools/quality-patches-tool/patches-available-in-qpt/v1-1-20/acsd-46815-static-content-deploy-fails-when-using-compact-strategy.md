---
title: 'ACSD-46815 : le déploiement de contenu statique échoue à l’aide d’une stratégie compacte'
description: Appliquez le correctif ACSD-46815 pour résoudre le problème d’Adobe Commerce en raison duquel le déploiement de contenu statique échoue lors de l’utilisation d’une stratégie compacte.
feature: Deploy, Page Content, SCD
role: Admin
exl-id: 66941a83-daf8-4bb2-a575-b615e1c5dc7c
source-git-commit: 94fba368c799f4584e27331e852c0f8abeeabbd6
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# ACSD-46815 : le déploiement de contenu statique échoue lors de l’utilisation d’une stratégie compacte

Le correctif ACSD-46815 corrige le problème d’échec du déploiement du contenu statique lors de l’utilisation de la stratégie compacte. Ce correctif est disponible lorsque la version 1.1.20 de [[!DNL Quality Patches Tool (QPT)]](https://support.magento.com/hc/en-us/articles/360047139492) est installée. L’ID du correctif est ACSD-46815. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le déploiement de contenu statique échoue lors d’un déploiement avec une stratégie compacte.

<u>Procédure à suivre </u> :

1. Déployez le contenu statique avec une stratégie compacte en exécutant la commande suivante :

```bash
bin/magento setup:static-content:deploy -f -s compact
```

<u>Résultats attendus</u> :

Le déploiement du contenu statique s’est terminé sans erreur.

<u>Résultats réels</u> :

Le déploiement de contenu statique échoue avec une stratégie compacte. L’erreur suivante se produit lors du processus de déploiement : *Le contenu de /app/pub/static/adminhtml/Magento/base/default/.Impossible de lire le fichier /node_modules/@spectrum-css/vars/dist/spectrum-global.css.*

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans notre documentation destinée aux développeurs et développeuses.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
