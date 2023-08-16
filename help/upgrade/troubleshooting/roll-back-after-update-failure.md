---
title: Restauration après échec de la mise à jour du module
description: Dépannez votre mise à niveau Adobe Commerce ou Magento Open Source après avoir rencontré une erreur de mise à jour de module.
exl-id: 1537a6b1-b450-4f90-bffb-73359fa71598
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---

# Restauration après échec de la mise à jour du module

Si la mise à jour de votre module échoue, des messages similaires à ceux-ci s’affichent dans le journal de la console :

```terminal
[2015-08-14 12:12:02 CDT] Job "update {"components":[{"name":"example/module","version":"1.1.0"}]}" has been started
[2015-08-14 12:12:02 CDT] Starting composer update...
[2015-08-14 12:12:02 CDT] An error occurred while executing job "update {"components":
[{"name":"example/module","version":"1.1.0"}]}": Could not complete update {"components":
[{"name":"example/module","version":"1.1.0"}]} successfully: Cannot find component to update
```

Dans l’exemple précédent, il n’existe aucune version de composant à restaurer. Contactez le fournisseur du composant ou essayez de résoudre le problème vous-même.

En attendant, vous pouvez restaurer une version précédente en cliquant sur **Retour arrière**, qui récupère vos données même si vous ne les avez pas sauvegardées précédemment.
