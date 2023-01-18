---
title: Bonne pratique pour configurer la connexion au Secondaire MySQL
description: Découvrez comment configurer la connexion au Secondaire MySQL pour les sites Adobe Commerce déployés sur l’infrastructure cloud.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: a5a6e25e3fd303e07a07110b85aa1d460f53cd54
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---


# Bonne pratique pour configurer la connexion au Secondaire MySQL

>[!NOTE]
>
>Nous sommes conscients que cet article contient toujours des termes logiciels standard que certains peuvent trouver racistes, sexistes ou oppressifs et qui peuvent faire que le lecteur se sent blessé, traumatisé ou mal accueilli. Adobe s’efforce de supprimer ces termes de notre code, de notre documentation et de nos expériences utilisateur.

Pour les sites Adobe Commerce déployés sur l’infrastructure cloud Pro, Adobe recommande d’activer par défaut la connexion au Secondaire MYSQL pour la base de données.

Adobe Commerce peut lire plusieurs bases de données de manière asynchrone.  Lorsque vous activez la connexion au Secondaire MYSQL, Adobe Commerce utilise une connexion en lecture seule à la base de données pour recevoir le trafic en lecture seule sur un noeud non maître. Cela améliore les performances grâce à l’équilibrage de charge, car un seul noeud doit gérer le trafic lecture-écriture.

## Versions affectées

Adobe Commerce sur l’infrastructure cloud, architecture Pro

## Configuration de la connexion au Secondaire MySQL

La configuration de la connexion au Secondaire MYSQL est définie par la variable [MYSQL_USE_SECONDAIRE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) déployer la variable dans Adobe Commerce sur le fichier de configuration de l’environnement de l’infrastructure cloud, `.magento.env.yaml`. Définissez cette variable sur `true` pour activer la connexion.

Pour activer la connexion au Secondaire MySQL :

1. Modifiez votre `.magento.env.yaml` et vérifiez que `MYSQL_USE_SLAVE_CONNECTION` est activée.

   ```
   stage:
      deploy:
      MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. Validez les modifications, puis poussez-les vers la branche d’environnement pour déployer la mise à jour.

   Une fois le déploiement terminé, la connexion au Secondaire MySQL est activée sur votre infrastructure cloud.

## Informations supplémentaires

- [Variables d’environnement](https://devdocs.magento.com/cloud/env/variables-intro.html)
- [Goulot d’étranglement de charge élevée MySQL dans Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.html?lang=en)
- [Bonnes pratiques relatives aux bases de données pour Adobe Commerce sur l’infrastructure cloud](database-on-cloud.md)
