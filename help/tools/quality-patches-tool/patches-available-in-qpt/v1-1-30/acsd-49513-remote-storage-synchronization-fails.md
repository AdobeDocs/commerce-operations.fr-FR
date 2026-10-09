---
title: 'ACSD-49513 : la synchronisation du stockage distant échoue'
description: Appliquez le correctif ACSD-49513 pour résoudre le problème d’Adobe Commerce en raison duquel la synchronisation du stockage distant échoue en raison de fichiers de 0 octet.
feature: Iaas, Storage
role: Admin
exl-id: 94dacfc4-d2d6-47b9-be0a-5bb55225af9a
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: aa037b12-c774-5642-a947-459024feb1a2
    internal-label: Storage
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
    internal-label: Architecture
subfeature_v2:
  - id: df5e974b-6742-4873-a687-a6bedaafdaa2
    internal-label: IaaS
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%
---
# ACSD-49513 : la synchronisation du stockage distant échoue en raison de fichiers de 0 octet

Le correctif ACSD-49513 corrige le problème d’échec de la synchronisation du stockage distant en raison de fichiers de 0 octet. Ce correctif est disponible lorsque la version 1.1.30 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-49513. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.4-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La synchronisation du stockage distant échoue en raison de fichiers de 0 octet.

<u>Procédure à suivre </u> :

1. Configurez AWS S3 comme stockage distant.
1. Exécutez `[bin/magento remote-storage:sync]` pour vous assurer que la synchronisation fonctionne correctement au début.
1. Créez un fichier de 0 octet dans le `[pub/media]`.
1. Exécutez à nouveau `[bin/magento remote-storage:sync]`.

<u>Résultats attendus</u> :

Comme AWS S3 accepte les fichiers de 0 octet sur la notification push directe S3, il n’y a aucune erreur.

<u>Résultats réels</u> :

L’erreur suivante se produit :

```PHP
Uploading media files to remote storage.
In File.php line 387:
  The file or directory "pub/media/xxxx.file" cannot be copied to "*.amazonaws.com/media/xxxx.file"
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Étapes supplémentaires requises après l’installation du correctif

(Cette section est facultative ; certaines étapes peuvent être nécessaires après l’application du correctif pour résoudre le problème.) 

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
