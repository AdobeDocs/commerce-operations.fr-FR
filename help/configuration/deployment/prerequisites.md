---
title: Conditions préalables au déploiement
description: Consultez la liste des conditions préalables au déploiement de Commerce dans un système de développement, de création ou de production.
feature: Configuration, Deploy
exl-id: 9ea0eeff-e0f8-4532-887c-5d7f07d89ddd
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# Conditions préalables pour les systèmes de développement, de génération et de production

Les autorisations et la propriété des fichiers doivent être cohérentes entre les systèmes de développement, de génération et de production. Pour que cela fonctionne, vous devez :

- Tous les éléments suivants :

   - Configuration du même nom d’utilisateur du propriétaire du système de fichiers sur tous les systèmes
   - Assurez-vous que le serveur web s’exécute comme le même utilisateur sur tous les systèmes.
   - Assurez-vous que le propriétaire du système de fichiers se trouve dans le groupe de serveurs Web sur tous les systèmes.

- Modifiez les droits d’accès et de propriété du système de fichiers Commerce sur chaque système selon les besoins en suivant les instructions suivantes :

   - Développement et création : [Définir la propriété et les autorisations de pré-installation (deux utilisateurs)](file-system-permissions.md#set-up-two-owners-for-default-or-developer-mode)
   - Production : [Propriété commerciale et autorisations dans le développement et la production](file-system-permissions.md)

>[!INFO]
>
>Si vous choisissez cette approche, vous devez définir les droits d’accès et de propriété du système de fichiers chaque fois que vous extrayez du code de votre système de génération (si le propriétaire du système de fichiers ou l’utilisateur du serveur Web diffèrent sur votre système de génération).
