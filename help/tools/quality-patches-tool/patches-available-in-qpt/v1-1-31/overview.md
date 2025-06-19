---
title: Présentation de  [!DNL Quality Patches Tool] (QPT) v1.1.31
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans  [!DNL Quality Patches Tool] (QPT) v1.1.31.
feature: Tools and External Services
role: Admin
exl-id: d37c7f05-1bf5-495b-9b9e-ac9dd117a3ab
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.31

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.31.

QPT v1.1.31 comprend les correctifs suivants :

1. **ACSD-50817** : optimise l’exécution plus rapide des `sales_clean_quotes` de tâche cron en ajoutant un index composite sur les colonnes `store_id` et `updated_at` de la table des guillemets.
1. **ACSD-50345** : corrige le problème suivant : [!DNL Google reCAPTCHA v2] ne recharge pas après l’envoi d’un paiement ayant échoué, [!DNL Google reCAPTCHA v3 Invisible] ne fonctionne pas lors du passage en caisse et la commande ne peut pas être passée, et [!UICONTROL PlaceOrder]’événement n’a pas été déclenché.
1. **ACSD-49392** : correction d’un problème en raison duquel le statut de la commande passe à Fermé après un remboursement partiel pour un produit groupé.
1. **ACSD-51036** : corrige le problème où les conditions de concurrence lors d’appels simultanés d’API REST entraînent un remplacement des informations de statut d’expédition dans la table [!UICONTROL Items Ordered] .
1. **ACSD-50858** : correction d’un problème en raison duquel un coupon est incorrectement marqué comme utilisé après un échec de paiement par carte.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
