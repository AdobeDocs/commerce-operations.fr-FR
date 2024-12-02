---
title: 'ACSD-49513 : Échec de la synchronisation du stockage distant'
description: Appliquez le correctif ACSD-49513 pour résoudre le problème Adobe Commerce où la synchronisation du stockage distant échoue en raison de fichiers de 0 octet.
feature: Iaas, Storage
role: Admin
exl-id: 94dacfc4-d2d6-47b9-be0a-5bb55225af9a
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-49513 : la synchronisation du stockage distant échoue en raison de fichiers de 0 octet

Le correctif ACSD-49513 corrige le problème d’échec de la synchronisation du stockage distant en raison de fichiers de 0 octet. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.30 est installé. L’ID de correctif est ACSD-49513. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.4-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La synchronisation du stockage distant échoue en raison de fichiers de 0 octet.

<u>Étapes à reproduire</u> :

1. Configurez AWS S3 en tant que stockage distant.
1. Exécutez `[bin/magento remote-storage:sync]` pour vous assurer que la synchronisation fonctionne correctement au début.
1. Créez un fichier de 0 octet dans le `[pub/media]`.
1. Exécutez à nouveau `[bin/magento remote-storage:sync]`.

<u>Résultats attendus</u> :

Comme AWS S3 accepte les fichiers de 0 octet sur la notification push directe S3, aucune erreur n’est générée.

<u>Résultats réels</u> :

L’erreur suivante se produit :

```PHP
Uploading media files to remote storage.
In File.php line 387:
  The file or directory "pub/media/xxxx.file" cannot be copied to "*.amazonaws.com/media/xxxx.file"
```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Autres étapes requises après l’installation du correctif

(Cette section est facultative ; certaines étapes peuvent être requises après l’application du correctif pour résoudre le problème.) 

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
