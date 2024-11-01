---
title: Configuration du stockage distant
description: Découvrez comment configurer le module de stockage distant pour l’application Commerce sur site.
feature: Configuration, Storage
exl-id: 0428f889-46b0-44c9-8bd9-98c1be797011
source-git-commit: 4fce6763ec619b0b5069e71cced9ebeb81505304
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---

# Configuration du stockage distant

Le module Stockage distant offre la possibilité de stocker des fichiers multimédias et de planifier les imports et exports dans un conteneur de stockage distant persistant à l’aide d’un service de stockage, tel qu’AWS S3.

Par défaut, l’application Adobe Commerce stocke les fichiers multimédias dans le même système de fichiers que celui qui contient l’application. Cela n’est pas efficace pour les configurations multi-serveurs complexes et peut entraîner une dégradation des performances lors du partage des ressources. Avec le module de stockage distant, vous pouvez stocker des fichiers multimédias dans le répertoire `pub/media` et importer/exporter des fichiers dans le répertoire `var` du stockage d’objets distants afin de tirer parti du redimensionnement d’image côté serveur.

>[!BEGINSHADEBOX]

Le stockage à distance _et le stockage de base de données_ ne peuvent pas être activés en même temps. Vous devez désactiver le stockage de la base de données avant d’activer le stockage à distance.

```bash
bin/magento config:set system/media_storage_configuration/media_database 0
```

L’activation du stockage à distance peut affecter votre expérience de développement établie. Par exemple, certaines fonctions de fichier PHP peuvent ne pas fonctionner comme prévu. L’utilisation de Commerce Framework pour les opérations de fichier doit être appliquée. La liste des fonctions natives PHP interdites est disponible dans le référentiel [magento-coding-standard](https://github.com/magento/magento-coding-standard/blob/develop/Magento2/Sniffs/Functions/DiscouragedFunctionSniff.php) .

>[!ENDSHADEBOX]

>[!INFO]
>
>- Le stockage à distance n’est disponible que pour Commerce version 2.4.2 et ultérieure. Voir les [notes de mise à jour 2.4.2](https://devdocs.magento.com/guides/v2.4/release-notes/open-source-2-4-2.html).
>
>- Le module de stockage à distance prend _en charge limitée_ dans Adobe Commerce sur l’infrastructure cloud. Adobe ne peut pas résoudre entièrement les problèmes liés au service d’adaptateur de stockage tiers. Voir [Configuration de l’espace de stockage distant pour Commerce sur l’infrastructure cloud](cloud-support.md) pour obtenir des conseils sur l’implémentation de l’espace de stockage distant pour les projets cloud.

![image de schéma](../../assets/configuration/remote-storage-schema.png)

## Options de stockage distant

Vous pouvez configurer le stockage à distance à l’aide de l’option `remote-storage` avec la commande [`setup` CLI](../../installation/tutorials/deployment.md). L’option `remote-storage` utilise la syntaxe suivante :

```text
--remote-storage-<parameter-name>="<parameter-value>"
```

`parameter-name` fait référence au nom du paramètre de stockage distant spécifique. Le tableau suivant répertorie les paramètres disponibles pour la configuration du stockage à distance :

| Paramètre de ligne de commande | Nom du paramètre | Description | Valeur par défaut |
|--- |--- |--- |--- |
| `remote-storage-driver` | conducteur | Nom de l’adaptateur<br>Valeurs possibles :<br>**file** : désactive le stockage distant et utilise le système de fichiers local <br>**aws-s3** : utilisez le [service de stockage simple Amazon (Amazon S3)](remote-storage-aws-s3.md) | none |
| `remote-storage-bucket` | compartiment | Stockage d’objet ou nom du conteneur | none |
| `remote-storage-prefix` | préfixe | Préfixe facultatif (emplacement dans le stockage d’objets) | empty |
| `remote-storage-region` | region | Nom de la région | none |
| `remote-storage-key` | clé d&#39;accès | Clé d’accès facultative | empty |
| `remote-storage-secret` | clé secrète | Clé secrète facultative | empty |

### Adaptateurs de stockage

L’emplacement de stockage par défaut se trouve dans le système de fichiers local. Un _adaptateur de stockage_ vous permet de vous connecter à un service de stockage et de stocker vos fichiers où que vous soyez. [!DNL Commerce] prend en charge la configuration des services de stockage suivants :

- [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md)

## Activer le stockage à distance

Vous pouvez installer un stockage distant lors d’une installation Adobe Commerce ou ajouter un stockage distant à une instance Commerce existante. Les exemples suivants montrent chaque méthode utilisant un ensemble de paramètres `remote-storage` avec des commandes d’interface de ligne de commande Commerce `setup`. Au minimum, vous devez fournir le stockage `driver`, `bucket` et `region`.

- Exemple : installation de Commerce avec stockage à distance

  ```bash
  bin/magento setup:install --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
  ```

- Exemple : activer le stockage à distance sur Commerce existant

  ```bash
  bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
  ```

>[!TIP]
>
>Pour Adobe Commerce sur l’infrastructure cloud, voir [Configuration de l’espace de stockage distant pour Commerce sur l’infrastructure cloud](cloud-support.md).

## Migration de contenu

Après avoir activé le stockage à distance pour un adaptateur spécifique, vous pouvez utiliser l’interface de ligne de commande pour migrer les fichiers _media_ existants vers le stockage à distance.

```bash
./magento2ce/bin/magento remote-storage:sync
```

>[!INFO]
>
>La commande sync migre uniquement les fichiers du répertoire `pub/media`, _et non_ les fichiers d&#39;import/export dans le répertoire `var`. Voir [Import/Export planifié](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-scheduled-import-export.html) dans le _Guide de l’utilisateur de Commerce 2.4_.

<!-- link definitions -->

[import-export]: https://docs.magento.com/user-guide/system/data-scheduled-import-export.html
