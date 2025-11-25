---
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 1%

---
# Paramètres de configuration de MariaDB

La réindexation sur MariaDB 10.4 et 10.6 prend plus de temps que les versions précédentes de MariaDB ou MySQL. Pour accélérer la réindexation, nous vous recommandons de définir les paramètres de configuration MariaDB suivants :

* [`optimizer_switch='rowid_filter=off'`](https://mariadb.com/kb/en/optimizer-switch/)
* [`optimizer_use_condition_selectivity = 1`](https://mariadb.com/docs/server/server-management/variables-and-modes/server-system-variables#optimizer_use_condition_selectivity)

Si vous constatez une dégradation des performances non liée à l’indexation après la mise à niveau vers MariaDB 10.6, envisagez d’activer le paramètre [`--query-cache-type`](https://mariadb.com/kb/en/server-system-variables/#query_cache_type) . Par exemple, `--query-cache-type=ON`.

Avant de mettre à niveau Adobe Commerce sur des projets d’infrastructure cloud, vous devrez peut-être également mettre à niveau MariaDB ([voir Bonnes pratiques de mise à niveau de MariaDB](../implementation-playbook/best-practices/maintenance/mariadb-upgrade.md)).

Par exemple :

* Adobe Commerce 2.4.6 avec MariaDB version 10.5.1 ou ultérieure
* Adobe Commerce 2.3.5 avec MariaDB version 10.3 ou antérieure

Outre ces recommandations, contactez l’administrateur de votre base de données pour configurer les paramètres suivants :

>[!NOTE]
>
>Ces paramètres sont disponibles pour les déploiements sur site uniquement. Les clients Adobe Commerce sur les infrastructures cloud n’ont pas accès à ces paramètres.

* [`--query-cache-limit`](https://mariadb.com/kb/en/server-system-variables/#query_cache_limit)
* [`--query-cache-size`](https://mariadb.com/kb/en/server-system-variables/#query_cache_size)
* [`--join-buffer-size`](https://mariadb.com/kb/en/server-system-variables/#join_buffer_size)
* [`--innodb-buffer-pool-size`](https://mariadb.com/kb/en/innodb-buffer-pool/#innodb_buffer_pool_size)
