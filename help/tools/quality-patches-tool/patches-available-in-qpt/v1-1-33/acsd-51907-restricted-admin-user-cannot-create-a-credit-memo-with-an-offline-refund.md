---
title: 'ACSD-51907 : l''utilisateur administrateur restreint ne peut pas créer d''avoir pour le remboursement hors ligne'
description: Appliquez le correctif ACSD-51907 pour résoudre le problème d’Adobe Commerce en raison duquel l’utilisateur administrateur restreint ne peut pas créer d’avoir avec remboursement hors ligne.
exl-id: 1c44d99b-7633-4768-b7e7-332f3666a5d9
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# ACSD-51907 : l&#39;utilisateur administrateur restreint ne peut pas créer d&#39;avoir pour le remboursement hors ligne

Le correctif ACSD-51907 corrige le problème de performances en raison duquel l’utilisateur administrateur restreint ne peut pas créer d’avoir avec remboursement hors ligne. Ce correctif est disponible lorsque la version 1.1.33 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-51907. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 &lt; 2.4.3-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L&#39;utilisateur administrateur restreint ne peut pas créer un avoir avec un remboursement hors ligne.

<u>Procédure à suivre </u> :

1. Créez un **client** sur le site web par défaut.
1. Créez **nouveau site web** avec les *magasin* et *vue de magasin* associés.
1. Définissez le site web par défaut sur le nouveau site web. Effacez les caches.
1. Modifiez la configuration client : **Admin** > **Store** > **Configuration** > **Customers** > **Configuration client** > **Partager les comptes client = Global**.
1. Créez un rôle d’utilisateur administrateur avec la portée du rôle définie sur la nouvelle *de site web créée (accès aux données de vente uniquement)* dans **Admin** > **Système** > **Autorisations**.
1. Créez un compte administrateur avec ce rôle.
1. Créez une nouvelle commande à l&#39;aide du mode de paiement en ligne *(par ex. Auth.net ou PayPal)*.
1. Connectez-vous en tant qu’utilisateur administrateur restreint.
1. Accédez à **Ventes** > **Commandes** > puis **page d’affichage des commandes**.
1. Créez une facture.
1. Accédez à l’onglet Factures .
1. Cliquez sur **Facture**.
1. Cliquez sur **[!UICONTROL Credit Memo]**.
1. Cochez la case **[!UICONTROL Refund to Store Credit]** , définissez le champ de texte près de lui sur la valeur *1*.
1. Cliquez sur le bouton **[!UICONTROL Refund Offline]**.

<u>Résultats attendus</u> :

L&#39;avoir est créé et *1 $* est remboursé au crédit du magasin.

<u>Résultats réels</u> :

Le message d’erreur *Des autorisations supplémentaires sont nécessaires pour afficher cet élément* s’affiche.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
