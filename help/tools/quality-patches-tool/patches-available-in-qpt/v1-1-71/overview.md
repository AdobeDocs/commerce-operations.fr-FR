---
title: Présentation de  [!DNL Quality Patches Tool] (QPT) v1.1.71
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans  [!DNL Quality Patches Tool] (QPT) v1.1.71.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: 57fea42c0c893166c3489f6b95e09ccba787b9f1
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.71

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.71.

QPT v1.1.71 comprend les correctifs suivants :


* **ACSD-60624** : **[!UICONTROL Upload Image]** ne fonctionne pas pour le contenu vide dans les sections [!UICONTROL Image], [!UICONTROL Banner] et [!UICONTROL Slider] dans [!DNL Page Builder].
* **ACSD-67089** : problème de pagination dans l’API `inventory/export-stock-salable-qty`, qui limite incorrectement la `total_count` à la taille de la page.
* **ACSD-67093** : la récupération des commandes via [!DNL GraphQL] à l’aide du filtre de période renvoie des résultats incorrects.
* **ACSD-67459** : impossible d&#39;importer les produits dont la description dépasse 65 536 caractères.
* **ACSD-67603** : temps de traitement long de la génération du plan de site pour les produits avec l’inclusion d’images activée
* **ACSD-67643** : des entrées en double sont créées lors des mises à jour planifiées dans les environnements comportant un grand nombre de catégories imbriquées.
* **ACSD-67652** : le statut du bundle du produit est renvoyé comme étant en rupture de stock dans les appels de [!DNL GraphQL], même avec des produits enfants et parents en stock.
* **ACSD-67904** : impossible de passer des commandes si le nom de la ville contient des chiffres (0-9), une esperluette (&amp;), un point (.) ou des parenthèses ().

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
