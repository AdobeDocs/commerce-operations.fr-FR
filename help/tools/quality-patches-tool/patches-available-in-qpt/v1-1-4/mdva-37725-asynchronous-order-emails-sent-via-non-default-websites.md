---
title: 'MDVA-37725 : les e-mails envoyés via des sites non par défaut contiennent les URL de logo du site par défaut'
description: Le correctif MDVA-37725 corrige le problème d’envoi des e-mails de commande asynchrones via des sites web autres que ceux par défaut contenant des URL de logo à partir du site web par défaut.
feature: Communications, Orders
role: Admin
exl-id: 6e72897c-7652-4b5a-8575-090e94188daf
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-37725 : les e-mails envoyés via des sites non par défaut contiennent les URL de logo du site par défaut

>[!WARNING]
>
> Le correctif MDVA-37725 est obsolète.

Le correctif MDVA-37725 corrige le problème d’envoi des e-mails de commande asynchrones via des sites web autres que ceux par défaut contenant des URL de logo à partir du site web par défaut. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4 est installé. L’ID du correctif est MDVA-37725. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les e-mails de commande asynchrones sont envoyés via des sites web autres que ceux par défaut contenant les URL de logo du site web par défaut.

<u>Conditions préalables</u> :

1. Le deuxième site web/magasin/affichage de magasin doit avoir été créé.
1. La configuration **Envoi asynchrone** doit être activée à partir de **Magasins** > **Paramètres** > **Configuration** > **Ventes** > **Ventes Email** > **Paramètres généraux**.
1. **Ajouter le code de magasin aux URL** la configuration est activée pour faciliter l’accès au site web secondaire à partir de **Magasins** > **Paramètres** > **Configuration** > **Options d’URL**.

<u>Procédure à suivre </u> :

1. Passez des commandes à partir du premier et du deuxième magasin.
1. Exécutez cron pour envoyer les e-mails de vente.
1. Vérifiez l’e-mail du deuxième site web.

<u>Résultats attendus</u> :

L’URL du logo de l’e-mail contient l’URL du deuxième site web.

<u>Résultats réels</u> :

L’URL du logo de l’e-mail contient l’URL du site web par défaut.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr).
