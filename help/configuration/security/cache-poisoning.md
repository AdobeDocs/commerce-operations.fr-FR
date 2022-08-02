---
title: Empoisonnement du cache
description: Découvrez comment empêcher l’empoisonnement du cache de page pour votre vitrine Commerce.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---


# Empoisonnement du cache

Cette rubrique explique comment empêcher [cache](https://glossary.magento.com/cache) empoisonnement si vous utilisez le serveur web Microsoft Internet Information Server (IIS). _Empoisonnement du cache_ est une méthode permettant de modifier le contenu du cache afin d’inclure différentes pages du même site. Par exemple, il est possible d’injecter une page d’erreur HTTP 404 (Introuvable) à la place d’une page bénigne (par exemple, la variable [storefront](https://glossary.magento.com/storefront) page d’accueil), qui peut entraîner un déni de service (DoS) potentiel. Les URL de page malveillantes sont mises en cache par Varnish ou Redis, d’où le nom _empoisonnement du cache de page_.

Ces types d’attaques peuvent être difficiles à détecter, car ils ne génèrent pas d’erreurs dans les journaux du serveur web.

Cette solution s’applique aux versions commerciales suivantes :

- 2.0.10 et versions ultérieures
- 2.1.2 et versions ultérieures

>[!INFO]
>
>Cette rubrique est destinée aux administrateurs IIS expérimentés.

## Description

Le problème se produit si les réécritures d’URL sont activées sur le serveur IIS, et que l’un des en-têtes HTTP suivants est modifié avant que la requête n’atteigne le service de mise en cache de vernis ou de redis :

- `X-Rewrite-Url`
- `X-Original-Url`
- `IIS-wasurlrewritten`
- `Unencoded-URL`
- `Orig-path-info`

Si ces en-têtes sont modifiés, l’URL et le contenu qui en résultent sont mis en cache, ce qui entraîne des vulnérabilités potentielles.

## Solution

Nous fournissons la possibilité de supprimer les valeurs de tous les en-têtes précédents en fonction du paramètre du serveur IIS pour `Enable_IIS_Rewrites`.

- If `Enable_IIS_Rewrites` est défini sur `0`, les valeurs des en-têtes sont supprimées.
- If `Enable_IIS_Rewrites` est défini sur `1`, les valeurs des en-têtes sont conservées intactes.

>[!WARNING]
>
>Si vous définissez `Enable_IIS_Rewrites` to `1`, vous ne devez pas autoriser la modification des valeurs des en-têtes précédents avant que la requête n’atteigne le serveur web IIS.
