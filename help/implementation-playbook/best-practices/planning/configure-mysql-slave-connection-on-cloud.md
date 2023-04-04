---
title: Bonne pratique pour configurer la connexion au Secondaire MySQL
description: Découvrez comment configurer la connexion au Secondaire MySQL pour les sites Adobe Commerce déployés sur l’infrastructure cloud.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: cb86772e9ceabc580ec32ad6ae1206a71ea03946
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Bonne pratique pour configurer la connexion au Secondaire MySQL

>[!NOTE]
>
>Cet article contient des termes logiciels standard que certains peuvent trouver racistes, sexistes ou oppressifs et qui peuvent faire que le lecteur se sent blessé, traumatisé ou mal accueilli. Adobe s’efforce de supprimer ces termes de notre code, de notre documentation et de nos expériences utilisateur.

Pour les sites Adobe Commerce déployés sur l’infrastructure cloud Pro, Adobe recommande d’activer par défaut la connexion au Secondaire MYSQL pour la base de données.

Adobe Commerce peut lire plusieurs bases de données de manière asynchrone. Lorsque vous activez la connexion au Secondaire MYSQL, Adobe Commerce utilise une connexion en lecture seule à la base de données pour recevoir le trafic en lecture seule sur un noeud non maître. Les performances s’améliorent grâce à l’équilibrage de charge lorsqu’un seul noeud gère le trafic lecture-écriture.

## Versions affectées

Adobe Commerce sur l’infrastructure cloud, architecture Pro

## Configuration de la connexion au Secondaire MySQL

Dans Adobe Commerce sur l’infrastructure cloud, vous pouvez remplacer la configuration par défaut de la connexion au Secondaire MYSQL en définissant la variable [MYSQL_USE_SECONDAIRE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) . Définissez cette variable sur true pour utiliser automatiquement une connexion en lecture seule à la base de données.

**Pour activer la connexion au Secondaire MySQL**:

1. Sur votre poste de travail local, modifiez le répertoire de votre projet.

1. Dans le `.magento.env.yaml` , définissez la variable `MYSQL_USE_SLAVE_CONNECTION` sur true.

   ```
   stage:
     deploy:
       MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. Validez la variable `.magento.env.yaml` change de fichier et envoie une notification push vers l’environnement distant.

   Une fois le déploiement terminé, la connexion au Secondaire MySQL est activée pour l’environnement cloud.

En savoir plus sur la personnalisation de l’environnement cloud en remplaçant votre configuration Commerce existante par [Variables d’environnement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html#environment-variables) dans le _Guide sur l’infrastructure cloud d’Adobe Commerce_.

## Informations supplémentaires

- [Goulot d’étranglement de charge élevée MySQL dans Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.html?lang=en)
- [Bonnes pratiques relatives aux bases de données pour Adobe Commerce sur l’infrastructure cloud](database-on-cloud.md)
