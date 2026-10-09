---
title: Conditions préalables au déploiement
description: Consultez la liste des conditions préalables au déploiement de Commerce dans un système de développement, de version ou de production.
feature: Configuration, Deploy
exl-id: 9ea0eeff-e0f8-4532-887c-5d7f07d89ddd
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
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
source-wordcount: '162'
ht-degree: 0%
---
# Conditions préalables au développement, à la création et aux systèmes de production

Les autorisations et la propriété des fichiers doivent être cohérentes sur l’ensemble des systèmes de développement, de création et de production. Pour que cela fonctionne, vous devez effectuer l’une des opérations suivantes :

- Tous les éléments suivants :

  - Configurer le même nom d&#39;utilisateur propriétaire de système de fichiers sur tous les systèmes
  - Vérifiez que le serveur Web s&#39;exécute comme le même utilisateur sur tous les systèmes
  - Vérifiez que le propriétaire du système de fichiers se trouve dans le groupe de serveurs Web sur tous les systèmes

- Modifiez les autorisations et la propriété du système de fichiers Commerce sur chaque système si nécessaire en suivant les instructions suivantes :

  - Développement et génération : [définir la propriété et les autorisations de préinstallation (deux utilisateurs)](file-system-permissions.md#set-up-two-owners-for-default-or-developer-mode)
  - Production : [propriété et autorisations Commerce en développement et production](file-system-permissions.md)

>[!INFO]
>
>Si vous optez pour cette approche, vous devez définir les autorisations et la propriété du système de fichiers chaque fois que vous extrayez du code de votre système de génération (si le propriétaire du système de fichiers ou l’utilisateur du serveur web sont différents sur votre système de génération).
