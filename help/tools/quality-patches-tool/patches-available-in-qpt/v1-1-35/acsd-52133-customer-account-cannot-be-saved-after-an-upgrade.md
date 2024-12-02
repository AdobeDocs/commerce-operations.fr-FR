---
title: 'ACSD-52133 : le compte client ne peut pas être enregistré après une mise à niveau'
description: Appliquez le correctif ACSD-52133 pour résoudre le problème Adobe Commerce en raison duquel un compte client ne peut pas être enregistré après une mise à niveau.
feature: Customers, Upgrade
role: Admin
exl-id: 4a0e6ed8-3e35-40ce-bb49-8ccfcde437a0
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-52133 : le compte client ne peut pas être enregistré après une mise à niveau

Le correctif ACSD-52133 corrige le problème lorsqu’un compte client ne peut pas être enregistré après une mise à niveau. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.35 est installé. L’ID de correctif est ACSD-52133. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le compte client ne peut pas être enregistré après une mise à niveau.

<u>Étapes à reproduire</u> :

1. Installez Adobe Commerce version 2.4.4.
1. Créez un client.
1. Mettez à niveau Adobe Commerce vers la version 2.4.6 à partir de la version précédente de 2.4.4 où un client a déjà été créé.
1. Définissez la clé de chiffrement comme ci-dessous dans `env.php` :

   `d337b914e91ff703b1e94ba4156aadf0`

1. Définissez les valeurs ci-dessous dans la base de données pour tout client sous la table `customer_entity` :

   ```
   -> rp_token as incr4869
   -> rp_token_created_at as "2021-04-29 20:06:14"
   ```

1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Modifiez le client pour lequel les valeurs ci-dessus ont été mises à jour.
1. Cliquez sur **[!UICONTROL Save Customer]** ou **[!UICONTROL Save and Continue Edit]**

<u>Résultats attendus</u> :

Le client est enregistré avec succès sans erreur.

<u>Résultats réels</u> :

* L’enregistrement du client n’est pas enregistré.
* L&#39;administrateur voit le message d&#39;erreur suivant : *Une erreur s&#39;est produite lors de l&#39;enregistrement du client.*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool]
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide d’infrastructure Commerce on Cloud

## Lecture connexe

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].
* [ Bonnes pratiques pour la modification des tables de base de données](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel de mise en oeuvre de Commerce

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
