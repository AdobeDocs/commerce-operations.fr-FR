---
title: Stockage à distance pour Commerce sur l’infrastructure cloud
description: Consultez des conseils sur la configuration du stockage à distance pour Adobe Commerce sur l’infrastructure cloud.
source-git-commit: 8102c083bb0216bbdcad2882f39f7711b9cee52b
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---


# Configuration du stockage à distance pour l’infrastructure Commerce on Cloud

Si vous choisissez d’utiliser la solution de stockage à distance avec un projet d’infrastructure cloud Adobe Commerce, utilisez la variable [Amazon S3](https://docs.fastly.com/en/guides/amazon-s3) dans la section _Fastly_ documentation pour vous assurer qu’Optimisation rapide des images fonctionne avec AWS S3.

Préparez-vous à [Informations d’identification rapides](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#get-fastly-credentials). Sur les projets Pro, utilisez SSH pour vous connecter à votre serveur et obtenir les informations d’identification Fastly de la `/mnt/shared/fastly_tokens.txt` fichier . Les environnements d’évaluation et de production disposent d’informations d’identification uniques. Vous devez obtenir les informations d’identification pour chaque environnement.

Continuez à configurer l’espace de stockage distant pour les projets cloud avec les tâches suivantes :

1. Configurez une [Intégration rapide du serveur principal](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md).

1. Création d’une logique VCL pour [Authentification AWS S3](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket).

1. Création d’une logique VCL pour [Requêtes du serveur principal vers le compartiment AWS S3](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/).
