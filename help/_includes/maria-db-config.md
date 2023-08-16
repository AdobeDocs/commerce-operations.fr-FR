---
source-git-commit: 631735eceb3609edd743c682291f373f6b01b399
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 1%

---
# Paramètres de configuration MariaDB

La réindexation sur MariaDB 10.4 et 10.6 prend plus de temps que les versions précédentes de MariaDB ou de MySQL. Pour accélérer la réindexation, nous vous recommandons de définir les paramètres de configuration MariaDB suivants :

* [`optimizer_switch='rowid_filter=off'`](https://mariadb.com/kb/en/optimizer-switch/)
* [`optimizer_use_condition_selectivity = 1`](https://mariadb.com/products/skysql/docs/reference/es/system-variables/optimizer_use_condition_selectivity/)

Si vous constatez une dégradation des performances non liée à l’indexation après la mise à niveau vers MariaDB 10.6, envisagez d’activer la variable [`--query-cache-type`](https://mariadb.com/kb/en/server-system-variables/#query_cache_type) . Par exemple, `--query-cache-type=ON`.

Outre ces recommandations, consultez l’administrateur de la base de données pour configurer les paramètres suivants :

>[!NOTE]
>
>Ces paramètres sont disponibles uniquement pour les déploiements sur site. Les clients d’Adobe Commerce sur l’infrastructure cloud n’ont pas accès à ces paramètres.

* [`--query-cache-limit`](https://mariadb.com/kb/en/server-system-variables/#query_cache_limit)
* [`--query-cache-size`](https://mariadb.com/kb/en/server-system-variables/#query_cache_size)
* [`--join-buffer-size`](https://mariadb.com/kb/en/server-system-variables/#join_buffer_size)
* [`--innodb-buffer-pool-size`](https://mariadb.com/kb/en/innodb-buffer-pool/#innodb_buffer_pool_size)
