---
title: 'ACSD-66149 : le gestionnaire IPN renvoie *500* pour les types non pris en charge'
description: Appliquez le correctif ACSD-66149 pour résoudre le problème Adobe Commerce où le gestionnaire d’IPN n’ignore pas les types d’IPN non pris en charge ou inconnus, ce qui entraîne la non-journalisation du problème, l’interruption du processus et le renvoi d’une erreur 500.
feature: Payments
role: Admin, Developer
type: Troubleshooting
exl-id: d4794e24-1b6b-4bb5-b54c-9a248fa5f3bd
source-git-commit: cf0f5992c7b2a51b270a4a1a81fd50305a92759c
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-66149 : le gestionnaire IPN renvoie *500* pour les types non pris en charge

Le correctif ACSD-66149 corrige le problème en raison duquel le gestionnaire IPN (Instant Payment Notification) renvoie une erreur 500 pour les types IPN non pris en charge ou inconnus. Ce correctif est disponible lorsque la version 1.1.69 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-66149. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le problème est que le gestionnaire IPN renvoie une erreur *500* pour les types IPN non pris en charge ou inconnus. Cela se produit lorsque Paypal envoie un code PIN avec des champs manquants.

<u>Procédure à suivre </u> :

1. Créez un module personnalisé qui émule tous les types d&#39;adresses IP inconnus de PayPal.
1. Créez au moins un produit.
1. Configurez PayPal Express avec vos propres identifiants.
1. Passez une commande avec Paypal Express.
1. Exécutez l&#39;émulateur PayPal.

<u>Résultats attendus</u> :

Le gestionnaire d&#39;adresses IP d&#39;application ignore les types d&#39;adresses IP incorrects et ne génère pas d&#39;erreurs *500* :

```Order 000000001: Status processing — HTTP 500```

<u>Résultats réels</u> :

L&#39;application génère de nombreuses erreurs *500* lors du traitement d&#39;adresses IP incorrectes et ne traite pas sporadiquement certaines commandes si les champs attendus sont absents.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool]
* Adobe Commerce sur les infrastructures cloud : [ Mises à niveau et correctifs > Appliquer des correctifs ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
