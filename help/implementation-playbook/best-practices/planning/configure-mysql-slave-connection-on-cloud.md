---
title: Bonne pratique pour configurer la connexion au Secondaire MySQL
description: Découvrez comment configurer la connexion au Secondaire MySQL pour les sites Adobe Commerce déployés sur l’infrastructure cloud.
role: Developer
feature: Best Practices
exl-id: d65bc80a-c4ec-4ea4-aff1-110592838201
source-git-commit: 3532480e2172c39ceb4ec55c9819d5271fd1fcdb
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# Bonne pratique pour configurer la connexion au Secondaire MySQL

>[!NOTE]
>
>Cet article contient des termes logiciels standard que certains peuvent trouver racistes, sexistes ou oppressifs et qui peuvent faire que le lecteur se sent blessé, traumatisé ou mal accueilli. Adobe s’efforce de supprimer ces termes du code, de la documentation et des expériences utilisateur.

Adobe Commerce peut lire plusieurs bases de données de manière asynchrone. Si vous attendez une charge élevée pour la base de données MySQL d’un site Commerce déployé sur l’architecture de Cloud Infrastructure Pro, Adobe recommande d’activer la connexion au Secondaire MYSQL.

Lorsque vous activez la connexion au Secondaire MYSQL, Adobe Commerce utilise une connexion en lecture seule à la base de données pour recevoir le trafic en lecture seule sur un noeud non maître. Les performances s’améliorent grâce à l’équilibrage de charge lorsqu’un seul noeud gère le trafic lecture-écriture.

## Versions affectées

Adobe Commerce sur l’infrastructure cloud, architecture Pro uniquement

## Configuration de la connexion au Secondaire MySQL

Dans Adobe Commerce sur l’infrastructure cloud, vous pouvez remplacer la configuration par défaut de la connexion au Secondaire MYSQL en définissant la variable [MYSQL_USE_SECONDAIRE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) Variable . Définissez cette variable sur `true` pour utiliser automatiquement une connexion en lecture seule à la base.

**Pour activer la connexion au Secondaire MySQL**:

1. Sur votre poste de travail local, modifiez le répertoire de votre projet.

1. Dans le `.magento.env.yaml` , définissez `MYSQL_USE_SLAVE_CONNECTION` sur true.

   ```
   stage:
     deploy:
       MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. Validez la variable `.magento.env.yaml` change de fichier et envoie une notification push vers l’environnement distant.

   Une fois le déploiement terminé, la connexion au Secondaire MySQL est activée pour l’environnement cloud.

## Informations supplémentaires

En savoir plus sur la personnalisation de l’environnement cloud en remplaçant votre configuration Commerce existante par [Variables d’environnement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html#environment-variables) dans le _Guide sur l’infrastructure cloud d’Adobe Commerce_.

Voir [Goulot d’étranglement de charge élevée MySQL dans Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.html) dans l’ _Base de connaissances d’assistance_.
