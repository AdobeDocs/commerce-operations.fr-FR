---
title: Bonnes pratiques relatives au redimensionnement des images de catalogue
description: Découvrez comment éviter la dégradation des performances avant le lancement en production de votre site Adobe Commerce.
feature: Best Practices
role: Developer
exl-id: 591b1a62-bdba-4301-858a-77620ee657a9
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# Bonnes pratiques relatives au redimensionnement des images de catalogue

Toutes les images de catalogue doivent être redimensionnées avant le début de la production d’un magasin. Si vous ne redimensionnez pas les images avant la mise en production, le redimensionnement de l’image est forcé pendant le chargement de la page, ce qui réduit considérablement la vitesse du site et augmente la charge du serveur au cours des premiers jours ou semaines suivant le lancement.

## La voie lente

Utilisez la commande CLI par défaut pour redimensionner toutes les images :

```bash
bin/magento catalog:images:resize
```

Les inconvénients de cette approche sont les suivants :

- Le processus est à thread unique
- Le processus redimensionne les images qui ont déjà été redimensionnées
- Le processus ne peut pas être interrompu, ce qui peut prendre plusieurs jours

## La voie rapide

Le redimensionnement asynchrone des images a été introduit dans Adobe Commerce 2.4 et peut redimensionner les images plus rapidement.

1. Sur chaque serveur web, démarrez temporairement certains gestionnaires de file d’attente supplémentaires (deux fois le nombre de processeurs physiques par serveur) :

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

Il existe une autre façon de redimensionner les images à l’aide du front-end.

Les avantages de cette approche sont les suivants :

- Le processus est multithread
- Le processus est multi-serveur (si vous avez plusieurs nœuds web, une répartition de charge et un espace disque partagé pour le répertoire `media/`)
- Le processus ignore les images qui ont déjà été redimensionnées

Cette approche redimensionne 100 000 images en moins de 8 heures, tandis que la commande d’interface de ligne de commande prend 6 jours.

1. Connectez-vous au serveur .
1. Accédez à `pub/media/catalog/product` et notez l’un des hachages (par exemple, 0047d83143a5a3a4683afdf1116df680).
1. Dans les exemples suivants, remplacez `www.example.com` par le domaine de votre boutique et remplacez le hachage par celui que vous avez noté.

>[!BEGINTABS]

>[!TAB SED]

```bash
cd pub/
find ./media/catalog/product -path ./media/catalog/product/cache -prune -o -type f -print | sed 's~./media/catalog/product/~https://www.example.com/media/catalog/product/cache/0047d83143a5a3a4683afdf1116df680/~g' > images.txt
```

>[!TAB  siège ]

L’inconvénient de `siege` est qu’il visite toutes les URL dans les 10 fois si la simultanéité est définie sur 10.

```bash
siege --file=./images.txt --user-agent="image-resizer" --no-follow --no-parser --concurrent=10 --reps=once
```

>[!TAB curl]

```bash
xargs -0 -n 1 -P 10 curl -X HEAD -s -w "%{http_code} %{time_starttransfer} %{url_effective}\n" < <(tr \\n \\0 <images.txt)
```

L’argument `-P` détermine le nombre de threads.

>[!TAB une seule ligne de bash]

Le texte en une seule ligne pour l’exemple `find/curl`, au cas où vous pouvez exécuter `curl` à partir de la même machine sur laquelle se trouvent les images :

```bash
find ./media/catalog/product -path ./media/catalog/product/cache -prune -o -type f -print | sed 's~./media/catalog/product/~https://www.example.com/media/catalog/product/cache/0047d83143a5a3a4683afdf1116df680/~g' | xargs -n 1 -P 10 curl -X HEAD -s -w "%{http_code} %{time_starttransfer} %{url_effective}\n"
```

Une fois de plus, remplacez `www.example.com` par le domaine de votre site web et définissez `-P` nombre de threads que votre serveur peut gérer sans se bloquer.

>[!ENDTABS]

La sortie renvoie une liste de toutes les images de produit du magasin. Vous pouvez analyser les images (avec `siege` ou tout autre robot d’exploration) à l’aide de tous les serveurs et cœurs de processeur disponibles et générer le cache de redimensionnement à une vitesse considérablement plus rapide que les autres approches.

La visite d’une URL de cache d’image génère toutes les tailles d’image en arrière-plan si elles n’existent pas encore. En outre, il ignore les fichiers qui ont déjà été redimensionnés.

>[!NOTE]
>
>- Adobe Commerce sur les projets d’infrastructure cloud peut décharger le redimensionnement des images de produit sur le service Fastly . Voir [Optimisation profonde des images](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization.html?lang=fr#deep-image-optimization) dans le _Guide du cloud_.
>- Si vous utilisez le module de stockage distant, vous pouvez également essayer de décharger le redimensionnement de l’image sur nginx. Voir [Configurer le redimensionnement des images pour le stockage distant](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/storage/remote-storage/remote-storage-image-resize.html?lang=fr) dans le _Guide de configuration_.
