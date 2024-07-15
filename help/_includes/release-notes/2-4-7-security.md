---
source-git-commit: 4ed23e2a8319ff97f8206f752cf1cbe2e73ea5c5
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---
# Améliorations de la sécurité 2.4.7

* **Ajout de la prise en charge de l’intégrité des sous-ressources** pour se conformer aux exigences PCI 4.0 de vérification de l’intégrité des scripts sur les pages de paiement. La prise en charge de l’intégrité des sous-ressources (SRI) fournit des hachages d’intégrité pour toutes les ressources JavaScript résidant dans le système de fichiers local. La fonctionnalité de SRI par défaut est implémentée uniquement sur les pages de paiement pour les zones d’administration et de storefront. Cependant, les marchands peuvent étendre la configuration par défaut à d’autres pages. Voir [Intégrité des sous-ressources](https://developer.adobe.com/commerce/php/development/security/subresource-integrity/) dans le _Guide du développeur PHP de Commerce_.<!--AC-1153-->

* **Modifications de la stratégie de sécurité du contenu (CSP)** : mise à jour et améliorations de la configuration des stratégies de sécurité du contenu (CSP) Adobe Commerce pour se conformer aux exigences PCI 4.0. Pour plus d&#39;informations, reportez-vous à la section [Stratégies de sécurité du contenu](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) du _Guide du développeur PHP de Commerce_. <!--AC-11513-->

   * La configuration par défaut de la CSP pour les pages de paiement pour l’administrateur Commerce et les zones de storefront est désormais le mode `restrict`. Pour toutes les autres pages, la configuration par défaut est le mode `report-only`.  Dans les versions antérieures à la version 2.4.7, la CSP était configurée en mode `report-only` pour toutes les pages.

   * Ajout d’un fournisseur à usage unique pour permettre l’exécution de scripts intégrés dans une CSP. Le fournisseur de valeur à usage unique facilite la génération de chaînes de valeur à usage unique pour chaque requête. Les chaînes sont ensuite jointes à l’en-tête CSP.

   * Ajout d’options pour configurer des URI personnalisés afin de signaler les violations CSP pour la page Créer une commande dans l’Admin et la page Passage en caisse dans le storefront. Vous pouvez ajouter la configuration à partir de l’administrateur ou en ajoutant l’URI au fichier `config.xml`.

     >[!NOTE]
     >
     >La mise à jour de la configuration CSP vers le mode `restrict` peut bloquer les scripts intégrés existants sur les pages de paiement dans l’Admin et le storefront, ce qui entraîne l’erreur de navigateur suivante lors du chargement d’une page : `Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`. Corrigez ces erreurs en mettant à jour la configuration de la liste blanche pour autoriser les scripts requis. Voir [Dépannage](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#troubleshooting) dans le _Guide du développeur PHP de Commerce_.
