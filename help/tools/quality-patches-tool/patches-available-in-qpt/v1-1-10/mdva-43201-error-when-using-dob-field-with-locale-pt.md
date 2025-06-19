---
title: 'MDVA-43201 : erreur lors de l’utilisation du champ DOB avec le paramètre régional PT'
description: Le correctif MDVA-43201 résout le problème où une erreur se produit lors de l’utilisation de l’attribut client DOB dans le formulaire d’enregistrement du client pour les paramètres régionaux portugais. Ce correctif est disponible lorsque l’[Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 est installé. L’ID du correctif est MDVA-43201. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.
feature: B2B, Cache
role: Admin
exl-id: be087420-1ee3-40cc-8ff7-62c5641609cc
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-43201 : erreur lors de l’utilisation du champ DOB avec le paramètre régional PT

Le correctif MDVA-43201 résout le problème où une erreur se produit lors de l’utilisation de l’attribut client DOB dans le formulaire d’enregistrement du client pour les paramètres régionaux portugais. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 est installé. L’ID du correctif est MDVA-43201. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsque l&#39;attribut du client DOB est ajouté au formulaire d&#39;enregistrement du client pour les paramètres régionaux portugais, le formulaire donne l&#39;erreur *l&#39;argument 1 transmis à iterator_to_array() doit implémenter l&#39;interface travesable, null donné*.

<u>Conditions préalables</u> :

Les modules B2B sont installés.

<u>Procédure à suivre </u> :

1. Accédez à Admin > **Magasins** > **Configuration** > **Général** > **Options de paramètres régionaux**, définissez Paramètres régionaux sur **Portugais (Portugal)** puis cliquez sur **Enregistrer**.
1. Réindexez et effacez le cache.
1. Accédez à **Magasins** > **Attribut** > **Client**.
1. Ouvrez l’attribut du client DOB et définissez **Afficher sur Storefront** sur **Oui**.
1. Sélectionnez tout dans **Formulaire à utiliser dans**.
1. Enregistrez l’attribut.
1. Accédez à la page Créer un compte sur le serveur frontal.

<u>Résultats attendus</u> :

Le formulaire d’enregistrement du client pour la boutique en portugais ne renvoie aucune erreur lors de l’ajout de l’attribut DOB.

<u>Résultats réels</u> :

Le formulaire d’enregistrement du client pour la boutique en portugais renvoie une erreur lors de l’ajout de l’attribut DOB.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
