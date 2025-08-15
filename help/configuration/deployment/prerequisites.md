---
title: Conditions préalables au déploiement
description: Consultez la liste des conditions préalables au déploiement de Commerce dans un système de développement, de version ou de production.
feature: Configuration, Deploy
exl-id: 9ea0eeff-e0f8-4532-887c-5d7f07d89ddd
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '161'
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
