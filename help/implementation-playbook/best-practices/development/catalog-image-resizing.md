---
title: Bonnes pratiques relatives au redimensionnement des images du catalogue
description: Découvrez comment empêcher la dégradation des performances avant le lancement en production de votre site Adobe Commerce.
feature: Best Practices
role: Developer
source-git-commit: 94d37b6a95cae93f465daf8eb96363a198833e27
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---


# Bonnes pratiques relatives au redimensionnement des images du catalogue

Toutes les images du catalogue doivent être redimensionnées avant qu’un magasin ne soit en production. L’échec du redimensionnement des images avant production force le redimensionnement des images au chargement de la page, ce qui réduit considérablement la vitesse du site et augmente la charge du serveur dans les premiers jours à quelques semaines après le lancement.

## La lenteur

Utilisez la commande d’interface de ligne de commande par défaut pour redimensionner toutes les images :

```bash
bin/magento catalog:images:resize
```

Cette approche présente les inconvénients suivants :

- Le processus est à thread unique.
- Le processus redimensionne les images qui ont déjà été redimensionnées
- Le processus ne peut pas être interrompu, ce qui peut prendre des jours.

## La méthode rapide

Le redimensionnement asynchrone des images a été introduit dans Adobe Commerce 2.4 et peut redimensionner les images plus rapidement.

1. Sur chaque serveur web, démarrez temporairement des gestionnaires de file d’attente supplémentaires (deux fois le nombre de processeurs physiques par serveur) :

   ```bsh
   for i in {1.."$((2 * `nproc --all`))"};do bin/magento queue:consumers:start media.storage.catalog.image.resize &;done;
   ```

1. Vérifiez que les gestionnaires de file d’attente sont en cours d’exécution :

   ```bash
   pgrep -fl media.storage.catalog.image.resize
   ```

1. Remplissez la file d’attente avec toutes les demandes de redimensionnement d’image :

   ```bash
   bin/magento catalog:images:resize --async
   ```

1. Une fois toutes les images redimensionnées, arrêtez le processus :

   ```bash
   pkill -f media.storage.catalog.image.resize
   ```

## La voie rapide

Il existe une autre manière de redimensionner les images à l’aide du front-end.

Cette approche présente les avantages suivants :

- Le processus est multithread
- Le processus est multi-serveur (si vous avez plusieurs noeuds web, un équilibreur de charge et un espace disque partagé pour la `media/` directory)
- Le processus ignore les images qui ont déjà été redimensionnées

Cette approche redimensionne 100 000 images en moins de 8 heures, tandis que la commande de l’interface de ligne de commande prend 6 jours.

1. Connectez-vous au serveur .
1. Accédez à `pub/media/catalog/product` et notez l’un des hachages (par exemple, 0047d83143a5a3a4683afdf116df680).
1. Dans les exemples suivants, remplacez `www.example.com` avec le domaine de votre boutique et remplacez le hachage par celui que vous avez noté.

>[!BEGINTABS]

>[!TAB sed]

```bash
cd pub/
find ./media/catalog/product -path ./media/catalog/product/cache -prune -o -type f -print | sed 's~./media/catalog/product/~https://www.example.com/media/catalog/product/cache/0047d83143a5a3a4683afdf1116df680/~g' > images.txt
```

>[!TAB siège]

L’inconvénient de `siege` est qu’il consulte toutes les URL dans les 10 fois si la simultanéité est définie sur 10.

```bash
siege --file=./images.txt --user-agent="image-resizer" --no-follow --no-parser --concurrent=10 --reps=once
```

>[!TAB curl]

```bash
xargs -0 -n 1 -P 10 curl -X HEAD -s -w "%{http_code} %{time_starttransfer} %{url_effective}\n" < <(tr \\n \\0 <images.txt)
```

La variable `-P` détermine le nombre de threads.

>[!TAB une ligne de base]

La ligne unique pour la variable `find/curl` par exemple, au cas où vous pourriez exécuter `curl` sur le même ordinateur que les images :

```bash
find ./media/catalog/product -path ./media/catalog/product/cache -prune -o -type f -print | sed 's~./media/catalog/product/~https://www.example.com/media/catalog/product/cache/0047d83143a5a3a4683afdf1116df680/~g' | xargs -n 1 -P 10 curl -X HEAD -s -w "%{http_code} %{time_starttransfer} %{url_effective}\n"
```

Une fois de plus, remplacez `www.example.com` avec le domaine de votre site web et défini `-P` au nombre de threads que votre serveur peut gérer sans se bloquer.

>[!ENDTABS]

La sortie renvoie une liste de toutes les images de produits dans le magasin. Vous pouvez analyser les images (avec `siege` ou tout autre moteur de recherche) qui utilise tous les serveurs et coeurs de processeur à votre disposition et qui génèrent le cache de redimensionnement à une vitesse nettement supérieure à celle des autres approches.

La consultation d’une URL de cache d’image génère toutes les tailles d’image en arrière-plan si elles n’existent pas encore. En outre, il ignore les fichiers qui ont déjà été redimensionnés.

>[!NOTE]
>
>- Adobe Commerce sur les projets d’infrastructure cloud peut décharger le redimensionnement des images du produit vers le service Fastly. Voir [Optimisation des images profondes](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization.html?lang=en#deep-image-optimization) dans le _Guide de Cloud_.
>- Si vous utilisez le module de stockage à distance, vous pouvez également essayer de décharger le redimensionnement de l’image sur nginx. Voir [Configuration du redimensionnement des images pour le stockage à distance](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/storage/remote-storage/remote-storage-image-resize.html) dans le _Guide de configuration_.
