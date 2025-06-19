---
title: 'Les taux spécifiques ACSD-61622: [!DNL FedEx] account sont manquants dans la réponse de l’API REST'
description: Appliquez le correctif ACSD-61622 pour résoudre le problème d’Adobe Commerce où les taux spécifiques  [!DNL FedEx]  compte sont absents de la réponse de l’API REST.
feature: Shipping/Delivery
role: Admin, Developer
exl-id: 59e33dc4-3f9b-4590-95b6-e98c77e750ee
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-61622 : les taux spécifiques au compte [!DNL FedEx] sont manquants dans la réponse de l’API REST

Le correctif ACSD-61622 résout le problème où les taux spécifiques [!DNL FedEx's] compte sont absents de la réponse de l’API REST. Il ajoute le type de requête de taux de `ACCOUNT` à la requête de l’API REST envoyée par Adobe Commerce à [!DNL FedEx], qui renvoie une réponse similaire à la réponse de l’API SOAP. Ce correctif est disponible lorsque la version 1.1.57 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-61622. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p1 - 2.4.6-p8

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les taux spécifiques au compte [!DNL FedEx's] sont absents de la réponse de l’API REST.

<u>Procédure à suivre </u> :

1. Installez une instance Adobe Commerce propre.
1. Créez un produit simple d&#39;un poids de 5 livres.
1. Configurez [!DNL FedEx] pour l’API REST.
1. Activez [!DNL FedEx] méthode d’expédition et effacez le cache.
1. Commencez à observer le fichier journal : `var/log/shipping.log`
1. Ajoutez un produit simple au panier et accédez à la page d’expédition lors du passage en caisse. Exemple de données client :

   * Code postal : 58601
   * Noms : John Doe
   * Adresse : 196 Eulalia Burg
   * Pays : US
   * État : Dakota du Nord
   * Numéro de téléphone : 187-563-3627

<u>Résultats attendus</u> :

Les taux d’`PAYOR_ACCOUNT_PACKAGE` sont disponibles dans la réponse de l’API REST, comme dans les réponses de l’API SOAP.

<u>Résultats réels</u> :

Seuls les taux de `PAYOR_LIST_PACKAGE` sont disponibles dans la réponse, ce qui signifie qu’il n’existe aucun taux (de compte) négocié de [!DNL FedEx].

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
