---
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---
# 2.4.7 améliorations de la sécurité

* **Ajout de la prise en charge de l’intégrité des sous-ressources (SRI)** pour se conformer aux exigences PCI 4.0 pour la vérification de l’intégrité des scripts sur les pages de paiement. La prise en charge de l’intégrité des sous-ressources (SRI) fournit des hachages d’intégrité pour toutes les ressources JavaScript résidant dans le système de fichiers local. La fonction SRI par défaut est implémentée uniquement sur les pages de paiement pour les zones Admin et Storefront. Cependant, les commerçants peuvent étendre la configuration par défaut à d’autres pages. Voir [Intégrité des sous-ressources](https://developer.adobe.com/commerce/php/development/security/subresource-integrity/) dans le _Guide du développeur de Commerce PHP_.<!--AC-1153-->

* **Modifications apportées à la politique de sécurité du contenu (CSP)** : mises à jour et améliorations de la configuration des politiques de sécurité du contenu (CSP) d’Adobe Commerce pour se conformer aux exigences PCI 4.0. Pour plus de détails, consultez [Politiques de sécurité du contenu](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) dans le _Guide du développeur de Commerce PHP_. <!--AC-11513-->

   * La configuration CSP par défaut pour les pages de paiement des zones Commerce Admin et Storefront est désormais en mode `restrict`. Pour toutes les autres pages, la configuration par défaut est le mode `report-only`.  Dans les versions antérieures à la version 2.4.7, CSP était configuré en mode `report-only` pour toutes les pages.

   * Ajout d’un fournisseur à usage unique pour permettre l’exécution de scripts intégrés dans une CSP. Le fournisseur de valeur à usage unique facilite la génération de chaînes à usage unique pour chaque requête. Les chaînes sont ensuite associées à l’en-tête CSP.

   * Ajout d’options permettant de configurer des URI personnalisés pour signaler des violations de CSP pour la page Créer une commande dans l’administration et la page Passage en caisse dans le storefront. Vous pouvez ajouter la configuration à partir de l’administration ou en ajoutant l’URI au fichier `config.xml`.

     >[!NOTE]
     >
     >La mise à jour de la configuration du CSP en mode `restrict` peut bloquer les scripts intégrés existants sur les pages de paiement dans Admin et Storefront, ce qui entraîne l’erreur de navigateur suivante lorsqu’une page se charge : `Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`. Corrigez ces erreurs en mettant à jour la configuration de la liste autorisée pour autoriser les scripts requis. Voir [Dépannage](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#troubleshooting) dans le _Guide du développeur de Commerce PHP_.
