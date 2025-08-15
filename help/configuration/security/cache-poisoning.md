---
title: Prévenir l’empoisonnement du cache
description: Découvrez comment empêcher l’empoisonnement du cache de page pour votre storefront Commerce.
feature: Configuration, Cache, Security
exl-id: 947024dd-d59d-480d-bb6c-8e0065054bb6
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Prévenir l’empoisonnement du cache

Cette rubrique explique comment éviter l&#39;empoisonnement du cache si vous utilisez le serveur Web Microsoft Internet Information Server (IIS). L’_empoisonnement du cache_ est une méthode permettant de modifier le contenu du cache afin d’inclure différentes pages du même site. Par exemple, il est possible d’injecter une page d’erreur HTTP 404 (Introuvable) à la place d’une page bénigne (par exemple, la page d’accueil du storefront), ce qui peut entraîner un déni de service potentiel. Les URL des pages malveillantes sont mises en cache par Varnish ou Redis, d’où le nom _empoisonnement du cache de page_.

Ces types d’attaques peuvent être difficiles à détecter, car ils n’entraînent pas d’erreurs dans les journaux du serveur web.

Cette solution s’applique aux versions de Commerce suivantes :

- 2.0.10 et versions ultérieures
- 2.1.2 et versions ultérieures

>[!INFO]
>
>Cette rubrique est destinée aux administrateurs IIS expérimentés.

## Description

Le problème se produit si les réécritures d’URL sont activées sur le serveur IIS et que l’un des en-têtes HTTP suivants est modifié avant que la requête n’atteigne le service de mise en cache de Vernis ou de Redis :

- `X-Rewrite-Url`
- `X-Original-Url`
- `IIS-wasurlrewritten`
- `Unencoded-URL`
- `Orig-path-info`

Si ces en-têtes sont modifiés, l’URL et le contenu qui en résultent sont mis en cache, ce qui entraîne des vulnérabilités potentielles.

## Solution

Nous proposons la possibilité de supprimer les valeurs de tous les en-têtes précédents en fonction du paramètre du serveur IIS pour `Enable_IIS_Rewrites`.

- Si `Enable_IIS_Rewrites` est défini sur `0`, les valeurs des en-têtes sont supprimées.
- Si `Enable_IIS_Rewrites` est défini sur `1`, les valeurs des en-têtes restent intactes.

>[!WARNING]
>
>Si vous définissez `Enable_IIS_Rewrites` sur `1`, vous ne devez pas autoriser la modification des valeurs des en-têtes précédents avant que la requête n&#39;atteigne le serveur Web IIS.
