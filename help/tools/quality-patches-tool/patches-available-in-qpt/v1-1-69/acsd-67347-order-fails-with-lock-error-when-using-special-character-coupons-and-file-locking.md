---
title: 'ACSD-67347 : la commande échoue avec l’erreur « Impossible d’acquérir un verrou » lors de l’utilisation de codes de coupon'
description: Appliquez le correctif ACSD-67347 au problème Adobe Commerce où les commandes échouent avec une erreur « Impossible d’acquérir un verrou » lorsque les codes coupon contiennent des caractères spéciaux (par exemple, BIT/123456) et que le verrouillage des fichiers est activé.
feature: Checkout, Shopping Cart
role: Admin, Developer
type: Troubleshooting
source-git-commit: 1a48428efbb022b53320370f68691eaed44809b3
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---


# ACSD-67347 : la commande échoue avec l’erreur *Impossible d’acquérir un verrou* lors de l’utilisation de codes de coupon

Le correctif ACSD-67347 corrige le problème d’échec des commandes avec une erreur *Impossible d’acquérir un verrou* lorsque les codes coupon contiennent des caractères spéciaux (par exemple, BIT/123456) et que le verrouillage des fichiers est activé. Ce correctif est disponible lorsque la version 1.1.69 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-67347. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p12

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p11 - 2.4.5-p13

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les commandes échouent avec l’erreur *Impossible d’acquérir un verrou* lorsque des coupons avec des caractères spéciaux sont utilisés et que le verrouillage de fichier est activé.

<u>Procédure à suivre </u> :

1. Installez 2.4-development.
1. Définissez la configuration du verrouillage de fichier dans le fichier `env.php` :

   ```
   'lock' => [
           'provider' => 'file',
           'config' => [
               'path' => '/Users/awijesooriya/sites/acsd15194dev/locks'
           ]
       ],
   ```

1. Créez une règle de panier avec un coupon à l’aide du format de code de coupon : *BIT/123456*.
1. Créez un produit simple.
1. Ajoutez le produit au panier et appliquez le code de coupon.
1. Passez à la caisse et passez la commande.

<u>Résultats attendus</u> :

Les commandes sont passées avec succès car il n&#39;y a aucune restriction sur la création de codes coupon.

<u>Résultats réels</u> :

La commande ne peut pas être passée. L’erreur suivante s’affiche : *Impossible d’acquérir lock.*

```
File "/Users/test/sites/test/locks/coupon_code_123/abc" cannot be opened Warning!fopen(/Users/test/sites/test/locks/coupon_code_123/abc): Failed to open stream: No such file or directory
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
