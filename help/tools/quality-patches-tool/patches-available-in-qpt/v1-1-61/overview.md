---
title: Présentation de  [!DNL Quality Patches Tool] (QPT) v1.1.61
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans  [!DNL Quality Patches Tool] (QPT) v1.1.61.
feature: Tools and External Services
role: Admin, Developer
exl-id: 065235fb-12e3-448b-bc37-51efdf95393a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.61

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.61.

QPT v1.1.61 comprend les correctifs suivants :

1. **ACP2E-3689** : corrige plusieurs problèmes d’affichage de l’arborescence des catégories à des niveaux plus profonds et en reflétant les relations ancre/non-ancre.
1. **ACP2E-3705** : correction d’un problème en raison duquel l’exécution du cron `indexer_update_all_views` échoue lorsque la `MAGE_INDEXER_THREADS_COUNT` est définie.
1. **ACSD-63883** : corrige le problème en raison duquel le [!UICONTROL Requisition List] renvoie un `items_count` incorrect dans la réponse [!DNL GraphQL].
1. **ACSD-63974** : corrige le problème en raison duquel le chargement de la page [!UICONTROL Requisition List] prend trop de temps lorsqu’il y a trop d’éléments, en ajoutant une fonctionnalité de pagination à la grille de [!UICONTROL Requisition List] du storefront, qui affiche uniquement des parties d’enregistrements limités au nombre d’enregistrements par page, au lieu de tous les enregistrements en même temps.
1. **ACSD-64178** : correction du problème en raison duquel la page de modification du [!UICONTROL Attribute Set] se charge lentement s’il existe des milliers d’attributs de produit.
1. **ACSD-64209** : correction du problème en raison duquel le planificateur cron récupère toutes les guillemets négociables sans exclure ceux dont le statut est **[!UICONTROL ordered]**, provoquant le déclenchement d’un e-mail ou d’e-mails.
1. **ACSD-64431** : la mutation `placeOrder` qui contient les informations sur le code de coupon dans la requête ne renvoie plus d’erreur interne, mais indique que la commande a été passée avec succès.
1. **ACSD-64467** : corrige le problème en raison duquel l’éditeur WYSIWYG apparaît vide après l’enregistrement d’une description de catégorie au niveau de l’affichage du magasin.
1. **ACSD-64546** : corrige le problème où un message d’erreur générique se produit dans l’interface utilisateur et où une exception *Conversion de tableau en chaîne* est stockée dans les journaux lors de la création de l’étiquette d’expédition de l’onduleur, en veillant à ce que l’erreur réelle s’affiche dans l’interface utilisateur et que le message d’erreur correct soit stocké dans les journaux.
1. **ACSD-64684** : corrige le problème d’erreur de validation lors de l’édition et de l’enregistrement d’une carte cadeau d’une valeur supérieure à *999* en raison de la virgule (séparateur des milliers) dans le nombre *mille (1 000)*.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
