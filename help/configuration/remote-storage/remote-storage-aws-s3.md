---
title: Configuration du compartiment AWS S3 pour le stockage à distance
description: Configurez votre projet Commerce pour utiliser le service de stockage AWS S3 pour le stockage à distance.
feature: Configuration, Storage
exl-id: e8aeade8-2ec4-4844-bd6c-ab9489d10436
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Configuration du compartiment AWS S3 pour le stockage à distance

Le [ service de stockage simple Amazon (Amazon S3)][AWS S3] est un service de stockage d’objets qui offre une évolutivité, une disponibilité des données, une sécurité et des performances de pointe. Le service AWS S3 utilise des compartiments, ou conteneurs, pour le stockage des données. Cette configuration nécessite la création d&#39;un compartiment _private_. Pour Adobe Commerce sur l’infrastructure cloud, voir [Configuration de l’espace de stockage distant pour Commerce sur l’infrastructure cloud](cloud-support.md).

>[!WARNING]
>
>L&#39;Adobe décourage fortement l&#39;utilisation de compartiments publics car elle présente un risque grave pour la sécurité.

**Pour activer le stockage à distance avec l’adaptateur AWS S3** :

1. Connectez-vous à votre tableau de bord Amazon S3 et créez un compartiment _private_.

1. Configurez les rôles [AWS IAM]. Vous pouvez également générer des clés d’accès et secrètes.

1. Désactivez le stockage de la base par défaut.

   ```bash
   bin/magento config:set system/media_storage_configuration/media_database 0
   ```

1. Configurez Commerce pour utiliser le compartiment privé. Voir [Options de stockage à distance](remote-storage.md#remote-storage-options) pour obtenir la liste complète des paramètres.

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="<bucket-name>" --remote-storage-region="<region-name>" --remote-storage-prefix="<optional-prefix>" --remote-storage-key=<optional-access-key> --remote-storage-secret=<optional-secret-key> -n
   ```

1. Synchronisez les fichiers multimédias avec l’enregistrement à distance.

   ```bash
   bin/magento remote-storage:sync
   ```

## Configuration de Nginx

Nginx nécessite une configuration supplémentaire pour effectuer l&#39;authentification avec la directive `proxy_pass`. Ajoutez les informations de proxy suivantes au fichier `nginx.conf` :

>nginx.conf

```conf
location ~* \.(ico|jpg|jpeg|png|gif|svg|js|css|swf|eot|ttf|otf|woff|woff2)$ {
    # Proxying to AWS S3 storage.
    resolver 8.8.8.8;
    set $bucket "<s3-bucket-name>";
    proxy_pass https://s3.amazonaws.com/$bucket$uri;
    proxy_pass_request_body off;
    proxy_pass_request_headers off;
    proxy_intercept_errors on;
    proxy_hide_header "x-amz-id-2";
    proxy_hide_header "x-amz-request-id";
    proxy_hide_header "x-amz-storage-class";
    proxy_hide_header "Set-Cookie";
    proxy_ignore_headers "Set-Cookie";
}
```

### Authentification

Si vous utilisez des clés d’accès et secrètes au lieu des rôles [AWS IAM], vous devez inclure le module [`ngx_aws_auth` Nginx][ngx repo].

### Autorisations

L’intégration S3 repose sur la possibilité de générer et de stocker des images mises en cache sur le système de fichiers local. Par conséquent, les autorisations de dossier pour `pub/media` et les répertoires similaires sont identiques pour S3 à l’utilisation du stockage local.

### Opérations de fichier

Il est vivement recommandé d’utiliser les méthodes d’adaptateur de fichier [!DNL Commerce] dans votre développement de codage ou d’extension, quel que soit le type de stockage de fichier. Lors de l’utilisation de S3 pour le stockage, n’utilisez pas d’opérations d’E/S de fichier PHP natif, telles que `copy`, `rename` ou `file_put_contents`, car les fichiers S3 ne se trouvent pas dans le système de fichiers. Voir [DriverInterface.php](https://github.com/magento/magento2/blob/2.4-develop/lib/internal/Magento/Framework/Filesystem/DriverInterface.php#L18) pour consulter des exemples de code.

<!-- link definitions -->

[AWS S3]: https://aws.amazon.com/s3
[AWS IAM]: https://aws.amazon.com/iam/
[ngx repo]: https://github.com/anomalizer/ngx_aws_auth
