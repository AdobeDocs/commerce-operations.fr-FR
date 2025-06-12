---
title: 'MDVA-38626 : l''utilisateur administrateur ne peut pas passer de commandes avec PayPal Payflow Pro'
description: Le correctif MDVA-38626 résout le problème où l'utilisateur administrateur ne peut pas passer de commande sur le serveur principal à l'aide de la méthode de paiement PayPal Payflow Pro. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9 est installé. L’ID du correctif est MDVA-38626. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: Admin Workspace, Orders, Payments
role: Admin
exl-id: 32d2e5dd-7081-42f2-a074-71e21c870dc2
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# MDVA-38626 : l&#39;utilisateur administrateur ne peut pas passer de commandes avec PayPal Payflow Pro

Le correctif MDVA-38626 résout le problème où l&#39;utilisateur administrateur ne peut pas passer de commande sur le serveur principal à l&#39;aide de la méthode de paiement PayPal Payflow Pro. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9 est installé. L’ID du correctif est MDVA-38626. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.3 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L&#39;utilisateur administrateur ne peut pas passer de commandes sur le serveur principal à l&#39;aide de la méthode de paiement PayPal Payflow Pro.

<u>Procédure à suivre </u> :

1. Configurez le mode de paiement PayPal Payflow Pro.
1. Accédez à **Clients** > **Tous les clients** et créez un compte client.
1. Cliquez sur **Créer une commande**.
1. Ajoutez n’importe quel article au panier.
1. Essayez de passer la commande en utilisant Payflow Pro.

<u>Résultats attendus</u> :

La commande est passée.

<u>Résultats réels</u> :

Erreur 500. Le journal de rapport contient :

```
{"0":"No such entity with cartId = 0","1":"#1 Magento\\Quote\\Model\\QuoteRepository->loadQuote() called at [app\/code\/Magento\/Quote\/Model\/QuoteRepository.php:136]\n#2 Magento\\Quote\\Model\\QuoteRepository->get() called at [lib\/internal\/Magento\/Framework\/Interception\/Interceptor.php:58]\n#3 Mag
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
