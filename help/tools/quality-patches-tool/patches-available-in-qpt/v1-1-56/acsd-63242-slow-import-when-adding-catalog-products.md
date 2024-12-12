---
title: 'ACSD-63242 : importation lente lors de l’ajout de plus de 10 000 produits de catalogue'
description: Appliquez le correctif ACSD-63242 pour résoudre le problème Adobe Commerce des importations lentes lorsque des produits de catalogue comportant plus de 10 000 entrées sont ajoutés.
feature: Data Import/Export
role: Admin, Developer
source-git-commit: 5fe00c9341414a0a2ba6b535d992d6c64e1c3b3a
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# ACSD-63242 : importation lente lors de l’ajout de plus de 10 000 produits de catalogue

Le correctif ACSD-63242 corrige le problème des importations lentes lorsque des produits du catalogue comportant plus de 10 000 entrées sont ajoutés. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 est installé. L’ID de correctif est ACSD-63242. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p8

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p8 et 2.4.7-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’importation des produits est lente lorsque des produits de catalogue comportant plus de 10 000 entrées sont ajoutés.

<u>Étapes à reproduire</u> :

1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Import]** > **[!UICONTROL Products]** > **[!UICONTROL Add/Update]**.
1. Importez un fichier avec plus de 10 000 entrées.

<u>Résultats attendus</u> :

L’importation des produits du catalogue est exécutée dans le délai prévu.

<u>Résultats réels</u> :

L’importation des produits est lente. Le `var/log/exception.log` contient :

```PHP
Exception: Warning: DOMXPath::query(): Recursion limit exceeded in /var/www/html/lib/internal/Magento/Framework/Validator/HTML/ConfigurableWYSIWYGValidator.php on line 114 in /var/www/html/lib/internal/Magento/Framework/App/ErrorHandler.php:62
```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] : outil en libre-service pour les correctifs de qualité ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils.
