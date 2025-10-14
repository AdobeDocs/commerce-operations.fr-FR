---
title: Configurer le compartiment AWS S3 pour le stockage distant
description: Configurez votre projet Commerce pour utiliser le service de stockage AWS S3 pour le stockage distant.
feature: Configuration, Storage
exl-id: e8aeade8-2ec4-4844-bd6c-ab9489d10436
source-git-commit: 3690043019d70ad15332f757158937a7d5305043
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# Configurer le compartiment AWS S3 pour le stockage distant

Le [service Amazon Simple Storage Service (Amazon S3)][AWS S3] est un service de stockage d’objets qui offre une évolutivité, une disponibilité des données, une sécurité et des performances de pointe. Le service AWS S3 utilise des compartiments, ou conteneurs, pour le stockage des données. Cette configuration nécessite la création d’un compartiment _privé_. Pour Adobe Commerce sur l’infrastructure cloud, consultez [Configuration du stockage distant pour Commerce sur l’infrastructure cloud](cloud-support.md).

>[!WARNING]
>
>Adobe décourage fortement l’utilisation des compartiments publics, car ils posent un risque de sécurité grave.
>
>Lors de l’utilisation d’un compartiment S3 fourni par le client pour le stockage de ressources ou de médias, Adobe n’est pas responsable des problèmes, des pertes de données ou des pannes liés à la configuration, à la gestion ou au fonctionnement du compartiment S3, et ne fournit pas de prise en charge pour ces problèmes. Le dépannage et la maintenance du compartiment S3 relèvent de la seule responsabilité du client.

**Pour activer le stockage distant avec l&#39;adaptateur AWS S3** :

1. Connectez-vous à votre tableau de bord Amazon S3 et créez un compartiment _privé_.

1. Configurez [les rôles AWS IAM]. Vous pouvez également générer des clés d’accès et secrètes.

1. Désactivez le stockage de base de données par défaut.

   ```bash
   bin/magento config:set system/media_storage_configuration/media_database 0
   ```

1. Configurez Commerce pour utiliser le compartiment privé. Pour obtenir une liste complète des paramètres[&#x200B; consultez la section &#x200B;](remote-storage.md#remote-storage-options) Options de stockage distant .

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="<bucket-name>" --remote-storage-region="<region-name>" --remote-storage-prefix="<optional-prefix>" --remote-storage-key=<optional-access-key> --remote-storage-secret=<optional-secret-key> -n
   ```

1. Synchronisez les fichiers multimédias avec le stockage distant.

   ```bash
   bin/magento remote-storage:sync
   ```

## Configurer Nginx

>[!NOTE]
>
>Cette approche ne s’applique pas à Adobe Commerce sur les projets d’infrastructure cloud. Nginx ne peut pas être configuré sur Adobe Commerce sur une infrastructure cloud. Pour plus d’informations, consultez la [documentation spécifique au cloud](cloud-support.md).

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

L’intégration S3 repose sur la possibilité de générer et de stocker des images mises en cache sur le système de fichiers local. Par conséquent, les autorisations de dossier pour les répertoires `pub/media` et similaires sont les mêmes pour S3 que lors de l’utilisation du stockage local.

### Opérations sur les fichiers

Il est vivement recommandé d’utiliser des méthodes d’adaptateur de fichiers [!DNL Commerce] dans votre développement de codage ou d’extension, quel que soit le type de stockage de fichiers. Lorsque vous utilisez S3 pour le stockage, n&#39;utilisez pas les opérations d&#39;E/S de fichiers PHP natives, telles que `copy`, `rename` ou `file_put_contents`, car les fichiers S3 ne se trouvent pas dans le système de fichiers. Voir [DriverInterface.php](https://github.com/magento/magento2/blob/2.4-develop/lib/internal/Magento/Framework/Filesystem/DriverInterface.php#L18) pour des exemples de code.

<!-- link definitions -->

[AWS S3]: https://aws.amazon.com/s3
[AWS IAM]: https://aws.amazon.com/iam/
[ngx repo]: https://github.com/anomalizer/ngx_aws_auth
