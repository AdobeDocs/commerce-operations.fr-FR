---
title: 'ACSD-63870 : le client ne s''est pas déconnecté correctement lors du changement de statut de la société'
description: Appliquez le correctif ACSD-63870 pour résoudre le problème d’Adobe Commerce en raison duquel un client d’une société n’est pas correctement déconnecté lorsque le statut de la société change au cours d’une session client active.
feature: Customers, B2B, Companies
role: Admin, Developer
exl-id: 4488f3cb-bb34-491e-8821-c2e98ff69429
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-63870 : le client ne s&#39;est pas déconnecté correctement lors du changement de statut de la société

Le correctif ACSD-63870 résout le problème où un client d&#39;une entreprise n&#39;est pas correctement déconnecté lorsque le statut de l&#39;entreprise change pendant une session client active. Ce correctif est disponible lorsque la version 1.1.59 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-63870. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.4-p10

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Échec de déconnexion du client lorsque le statut de l’entreprise est modifié au cours d’une session client active.

<u>Procédure à suivre </u> :

1. Activez la fonctionnalité B2B.
1. Créez un produit simple.
1. Créez une nouvelle entreprise et marquez-la comme *Active*.
1. Connectez-vous en tant qu’utilisateur de l’entreprise et ajoutez un produit au panier.
1. Procédez au passage en caisse jusqu’à l’étape [!UICONTROL Shipping Address]. Ne saisissez pas l’adresse.
1. Accédez à Admin et modifiez le statut de la société en *Approbation en attente*.
1. Revenez au serveur frontal et renseignez l’adresse de livraison.

<u>Résultats attendus</u> :

Le client a été déconnecté.

<u>Résultats réels</u> :

* Les utilisateurs reçoivent l’erreur *Un problème est survenu*.
* `var/log/exception.log` contient :

  ```
  report.CRITICAL: InvalidArgumentException: Incorrect theme identification key in /home/lib/internal/Magento/Framework/View/Design/Theme/FlyweightFactory.php:60
  ```


## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Étapes supplémentaires requises après l’installation du correctif

(Cette section est facultative ; certaines étapes peuvent être nécessaires après l’application du correctif pour résoudre le problème.) 

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
