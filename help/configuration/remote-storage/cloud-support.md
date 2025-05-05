---
title: Stockage à distance pour Commerce sur l’infrastructure cloud
description: Consultez des conseils sur la configuration du stockage à distance pour Adobe Commerce sur l’infrastructure cloud.
feature: Configuration, Cloud, Storage
exl-id: da352466-13f2-42e4-a589-3b0a89728467
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# Configuration du stockage à distance pour Commerce sur l’infrastructure cloud

À partir du package `ece-tools` 2002.1.5, vous pouvez utiliser une variable d’environnement pour activer le module de stockage distant. Cependant, le module de stockage distant a une prise en charge _limitée_ sur Adobe Commerce sur l’infrastructure cloud. Adobe ne peut pas résoudre entièrement les problèmes liés au service d’adaptateur de stockage tiers.

## Variable d’environnement

La variable `REMOTE_STORAGE` est utilisée pendant la [phase de déploiement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html?lang=fr) d’un projet d’infrastructure cloud.

### `REMOTE_STORAGE`

- **Par défaut**—_Non défini_
- **Version**—Commerce 2.4.2 et versions ultérieures

Configurez un _adaptateur de stockage_ pour stocker les fichiers multimédia dans un conteneur de stockage distant persistant à l’aide d’un service de stockage, tel qu’AWS S3. Activez le module Stockage distant afin d’améliorer les performances sur les projets Cloud avec des configurations multi-serveurs complexes qui doivent partager des ressources. Voici un exemple de configuration de stockage à distance à l’aide du fichier `.magento.env.yaml` :

```yaml
stage:
  deploy:
    REMOTE_STORAGE:
      driver: aws-s3 # Required
      prefix: cloud # Optional
      config:
        bucket: my-bucket # Required
        region: my-region # Required
        key: my-key # Optional
        secret: my-secret-key # Optional
```

### Définition de la variable avec l’interface de ligne de commande de Cloud

Définissez la variable `REMOTE_STORAGE` en tant que [ variable de niveau environnement ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html?lang=fr) de sorte que les fichiers ne soient pas partagés entre les environnements de production, d’évaluation et d’intégration. La définition des variables au niveau de l’environnement offre la possibilité de n’utiliser que le stockage à distance dans certains environnements, comme exclure l’utilisation de l’environnement d’intégration du stockage à distance.

**Pour ajouter la variable de stockage distant à l’aide de l’interface de ligne de commande de Cloud** :

```bash
magento-cloud variable:create --level environment --name REMOTE_STORAGE --json true --inheritable false --value '{"driver":"aws-s3","prefix":"uat","config":{"bucket":"aws-bucket-id","region":"eu-west-1","key":"optional-key","secret":"optional-secret"}}'
```

Cela crée une variable `REMOTE_STORAGE` avec la configuration JSON spécifiée. La variable `REMOTE_STORAGE` utilise une chaîne JSON pour configurer le stockage à distance. Voici un exemple de configuration JSON :

```json
{
  "driver": "aws-s3",
  "prefix": "uat",
  "config": {
    "bucket": "aws-bucket-id",
    "region": "aws-region-id",
    "key": "optional-key",
    "secret": "optional-secret"
  }
}
```

Une fois la configuration et le déploiement créés, les journaux de déploiement doivent inclure des informations sur la configuration du stockage distant, par exemple `INFO: Remote storage driver set to: "aws-s3"`.

### Définir la variable avec l’interface web du projet

Vous pouvez également utiliser l’interface web du projet pour ajouter la variable à l’environnement approprié.

**Pour ajouter la variable de stockage distant à l’aide de l’interface web du projet** :

1. Dans l’ _interface web du projet_, sélectionnez l’environnement dans la partie gauche.

1. Cliquez sur l&#39;icône **Configurer l&#39;environnement** .

1. Dans la vue _Configurer l’environnement_, cliquez sur l’onglet **Variables** .

1. Cliquez sur **Ajouter la variable**.

1. Dans le champ _Name_ , saisissez `REMOTE_STORAGE`

1. Dans le champ _Value_ , ajoutez la configuration JSON.

1. Sélectionnez **Valeur JSON** et **Sensitive** ; désélectionnez **Héritable par les environnements enfants**.

1. Cliquez sur **Ajouter la variable**.

### Utilisation de l’authentification facultative

`key` et `secret` sont facultatifs. Lorsque vous créez la variable, vous pouvez masquer les `key` et `secret` en sélectionnant l’option `sensitive` . Avec ce paramètre, les valeurs ne sont pas visibles dans l’interface web. Voir [Visibilité des variables](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html?lang=fr#visibility) dans le _guide Commerce on Cloud Infrastructure_.

Si vous souhaitez utiliser une autre méthode d’authentification, omettez les `key` et `secret` de la configuration JSON. Configurez la méthode d’authentification alternative et vérifiez que le serveur est autorisé à utiliser le compartiment S3.

### Synchronisation de l’espace de stockage distant

Après avoir activé le module de stockage distant, synchronisez les fichiers multimédias actuels avec l’emplacement de magasin distant.

**Pour démarrer la synchronisation** :

1. Utilisez SSH pour vous connecter à l’environnement distant avec le stockage à distance configuré.

1. Lancez la synchronisation.

```bash
bin/magento remote-storage:sync 
```

## Configuration rapide

Si vous choisissez d’utiliser la solution de stockage distant avec un projet d’infrastructure cloud Adobe Commerce, utilisez les instructions [Amazon S3](https://docs.fastly.com/en/guides/amazon-s3) de la documentation _Fastly_ afin de vous assurer que l’optimisation des images Fastly fonctionne avec AWS S3.

Préparez-vous à utiliser vos [informations d’identification Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=fr#get-fastly-credentials). Sur les projets Pro, utilisez SSH pour vous connecter à votre serveur et obtenir les informations d’identification rapides à partir du fichier `/mnt/shared/fastly_tokens.txt`. Les environnements d’évaluation et de production disposent d’informations d’identification uniques. Vous devez obtenir les informations d’identification pour chaque environnement.

Continuez à configurer l’espace de stockage distant pour les projets cloud avec les tâches suivantes :

1. Configurez une [intégration d’arrière-plan Fastly](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md).

1. Créez une logique VCL pour l’ [authentification AWS S3](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket).

1. Créez une logique VCL pour les [requêtes du serveur principal vers le compartiment AWS S3](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/).
