---
title: Prévenir l’empoisonnement du cache
description: Découvrez comment empêcher l’empoisonnement du cache de page pour votre storefront Commerce.
feature: Configuration, Cache, Security
exl-id: 947024dd-d59d-480d-bb6c-8e0065054bb6
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
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
