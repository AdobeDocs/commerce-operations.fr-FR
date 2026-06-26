---
title: Présentation de  [!DNL Quality Patches Tool] (QPT) v1.1.80
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans  [!DNL Quality Patches Tool] (QPT) v1.1.80.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
autotag-review: '2026-06-11T01:10:37.916Z'
TQID: 'https://experienceleague.adobe.com/q2sNWUJQCm4eRUP8RusytBAqQoscU4F9qDtDIeNmm6E'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: c1256247-af4b-46d8-9dca-0c654ecfa157
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 9c0c1b7124793e2f8b9b9e4296ba42315557ac61
workflow-type: tm+mt
source-wordcount: 541
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.80

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.80.

QPT v1.1.80 comprend les correctifs suivants :

1. **ACP2E-4239** : correction d’un problème en raison duquel les filtres de grille d’administration utilisant des attributs de date renvoyaient des résultats incorrects en raison de différences de fuseau horaire entre la date sélectionnée, les valeurs UTC stockées et le fuseau horaire du magasin configuré.
1. **[ACP2E-4472](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4472.md)** : corrige le problème où un enregistrement de guillemet nul est créé dans la table de base de données `quote` pendant le flux de **[!UICONTROL Login as Customer]**.
1. **ACP2E-4481** : correction d’un problème en raison duquel la vendabilité du bundle du produit n’est pas recalculée correctement après l’annulation d’une commande.
1. **[ACP2E-4488](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4488.md)** : correction d’un problème en raison duquel l’enregistrement ou la modification des produits dans Admin était lent pour les produits dotés de jeux d’attributs volumineux.
1. **ACP2E-4493** : correction du problème en raison duquel la grille d&#39;archivage des commandes client affiche un statut de commande incorrect lorsque l&#39;indexation asynchrone est activée.
1. **ACP2E-4496** : corrige le problème en raison duquel la tâche Analytics cron entraîne une dégradation des performances pendant l’exécution, ce qui entraîne une amélioration des performances globales du système.
1. **ACP2E-4533** : correction du problème en raison duquel les images d’espace réservé ne se chargent pas sur le storefront lorsqu’un code de magasin est inclus dans l’URL.
1. **[ACP2E-4552](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4552.md)** : corrige le problème en raison duquel le statut de la société n’est pas renvoyé dans la réponse GraphQL.
1. **[ACP2E-4496](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4496.md)** : corrige le problème en raison duquel la tâche Analytics cron entraîne une dégradation des performances pendant l’exécution, ce qui entraîne une amélioration des performances globales du système.
1. **[ACP2E-4533](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4533.md)** : correction du problème en raison duquel les images d’espace réservé ne se chargent pas sur le storefront lorsqu’un code de magasin est inclus dans l’URL.
1. **ACP2E-4610** : corrige le problème en raison duquel la tâche cron `sales_clean_quotes` présente des problèmes de performances.
1. **ACP2E-4615** : corrige le problème d&#39;échec des remboursements des commandes en ligne avec une erreur PayPal indiquant *la passerelle PayPal rejette la demande. Erreur interne.*.
1. **[ACP2E-4626](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4626.md)** : correction d&#39;un problème en raison duquel certains fichiers de JavaScript Storefront étaient demandés et exécutés deux fois, provoquant des chargements en double intermittents et un comportement instable.
1. **ACP2E-4653** : correction d’un problème en raison duquel la portée de l’attribut de condition **[!UICONTROL Cart Price Rule]** pour **[!UICONTROL Category (Parent Only)]** et **[!UICONTROL Category (Children Only)]** n’est pas exposée lors de la récupération ou de la mise à jour de règles via l’API REST.
1. **ACP2E-4808** : correction du problème en raison duquel l’attribut Poids de la page produit du storefront n’affiche qu’une valeur numérique brute dans la section **[!UICONTROL Additional Information]** ou **[!UICONTROL More Information]** sans l’unité de mesure configurée (lb ou kg).
1. **ACP2E-4626** : correction d&#39;un problème en raison duquel certains fichiers de JavaScript Storefront étaient demandés et exécutés deux fois, provoquant des chargements en double intermittents et un comportement instable.
1. **[ACP2E-4653](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4653.md)** : correction d’un problème en raison duquel la portée de l’attribut de condition de règle de prix de panier pour **[!UICONTROL Category (Parent Only)]** et **[!UICONTROL Category (Children Only)]** n’est pas exposée lors de la récupération ou de la mise à jour de règles via l’API [!DNL REST].
1. **[ACP2E-4808](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4808.md)** : correction du problème en raison duquel l’attribut Poids de la page produit du storefront n’affiche qu’une valeur numérique brute dans la section **[!UICONTROL Additional Information]** ou **[!UICONTROL More Information]** sans l’unité de mesure configurée (lb ou kg).
1. **[ACP2E-4156](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4156.md)** : correction d’un problème en raison duquel la validation de l’adresse d’expédition dans l’API [!DNL REST] n’adhère pas à la configuration d’attribut définie dans Admin.
1. **ACP2E-4813** : corrige le problème en raison duquel les méthodes d&#39;expédition USPS ne sont pas disponibles au moment du passage en caisse et les estimations d&#39;expédition sont incorrectes pour certains produits, y compris les commandes fractionnées en plusieurs packages.
1. **ACSD-53502** : corrige le problème d’échec intermittent du **[!UICONTROL Add to Cart]** sur le storefront dans iOS [!DNL Safari] en raison d’appels récursifs au script de surveillance New Relic, ce qui entraîne des rechargements de page.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
