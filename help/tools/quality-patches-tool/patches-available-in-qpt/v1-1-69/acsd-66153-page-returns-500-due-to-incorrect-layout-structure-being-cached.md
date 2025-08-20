---
title: 'ACSD-66153 : la page renvoie une erreur 500 en raison d’une structure de disposition incorrecte mise en cache'
description: Appliquez le correctif ACSD-66153 pour résoudre le problème d’Adobe Commerce où une page renvoie un code d’erreur 500 en raison d’une structure de mise en page incorrecte mise en cache.
feature: Catalog Management
role: Admin, Developer
type: Troubleshooting
source-git-commit: 70c7255e369ef366407d539488f0d815eb93f48a
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# ACSD-66153 : la page renvoie une erreur 500 en raison d’une structure de disposition incorrecte mise en cache

Le correctif ACSD-66153 corrige le problème où une page renvoie un code d’erreur 500 en raison d’une structure de mise en page incorrecte mise en cache. Ce correctif est disponible lorsque la version 1.1.69 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-66153. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p10

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une page renvoie une erreur 500 en raison d’une structure de disposition incorrecte mise en cache.

<u>Procédure à suivre </u> :

1. Installez `2.4-develop`.
1. Créez et installez un module personnalisé :
1.1 Ajoutez un bloc personnalisé à la disposition `catalog_category_view`.
1.1 Injecter `Magento\Framework\View\Result\Layout` dans le bloc personnalisé via son constructeur.
1. Créez le **[!UICONTROL shop]** de catégorie.
1. Ouvrez **[!UICONTROL two terminal windows]** :
   1. **Terminal 1** : nettoyez en permanence le cache de disposition :

      ```
      for i in {1..200}; do
        bin/magento cache:clean layout
      done
      ```

   1. **Terminal 2** : simule des requêtes simultanées sur la page de catégorie :

      ```
      for i in {1..200}; do
        curl -s -o /dev/null -w "Request $i: HTTP %{http_code}\n""http://your_magento_base_url/shop.html?req=$i"
      done
      ```

1. Certaines requêtes échouent de manière aléatoire avec un code d’état 500 et le `var/log/support_report.log` affiche l’erreur suivante :

   ```
   report.CRITICAL: The element with the "root" ID wasn't found. Verify the ID and try again. [] []
   ```

<u>Résultats attendus</u> :

Toutes les requêtes renvoient 200 OK.

<u>Résultats réels</u> :

Certaines requêtes renvoient par intermittence une erreur de serveur interne 500.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
