---
source-git-commit: 10a6329502bc63ec06bac0652301770bd8e2935a
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 0%

---
# Améliorations de la sécurité 2.4.7

Aucune attaque confirmée liée à ces problèmes n&#39;a été survenue à ce jour. Cependant, certaines vulnérabilités peuvent être exploitées pour accéder aux informations sur les clients ou prendre le contrôle des sessions d’administrateur. La plupart de ces problèmes nécessitent qu’un attaquant obtienne d’abord l’accès à l’administrateur. Par conséquent, nous vous rappelons de prendre toutes les mesures nécessaires pour protéger votre administrateur, y compris, mais sans s’y limiter, les actions suivantes :

* PLACE SUR LA LISTE AUTORISÉE IP
* [Authentification à deux facteurs](https://developer.adobe.com/commerce/testing/functional-testing-framework/two-factor-authentication/)
* Utilisation d&#39;un VPN
* Utilisation d’un emplacement unique plutôt que `/admin`
* Bonne hygiène des mots de passe

Les améliorations de sécurité de cette version améliorent la conformité aux dernières bonnes pratiques en matière de sécurité.

* **Modifications du comportement des clés de cache non générées**:

   * Les clés de cache non générées pour les blocs incluent désormais des préfixes différents des préfixes pour les clés générées automatiquement. (Les clés de cache non générées sont des clés définies par le biais de la syntaxe de directive de modèle ou de la fonction `setCacheKey` ou `setData` méthodes.)
   * Les clés de cache non générées pour les blocs ne doivent désormais contenir que des lettres, des chiffres, des tirets (-) et des traits de soulignement (_).  <!-- AC-9831 -->

* **Limites du nombre de codes de bon générés automatiquement**. Commerce limite désormais le nombre de codes de bon générés automatiquement. La valeur par défaut maximale est de 250 000. Les vendeurs peuvent utiliser la nouvelle **[!UICONTROL Code Quantity Limit]** option de configuration (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) pour éviter toute surcharge potentielle du système avec de nombreux coupons. <!-- AC-8753 -->

* **Optimisation du processus de génération d’URL d’administration par défaut**. La génération de l’URL d’administration par défaut est optimisée pour une répartition aléatoire accrue, ce qui rend les URL générées moins prévisibles. <!-- AC-9028 -->

* **Ajout de la prise en charge de l’intégrité des sous-ressources (SRI)** pour se conformer aux exigences PCI 4.0 de vérification de l’intégrité du script sur les pages de paiement. La prise en charge de l’intégrité des sous-ressources (SRI) fournit des hachages d’intégrité pour toutes les ressources JavaScript résidant dans le système de fichiers local. La fonctionnalité de SRI par défaut est implémentée uniquement sur les pages de paiement pour les zones d’administration et de storefront. Cependant, les marchands peuvent étendre la configuration par défaut à d’autres pages. Voir [Intégrité des sous-ressources](https://developer.adobe.com/commerce/php/development/security/subresource-integrity/) dans le _Guide du développeur PHP de Commerce_.<!--AC-1153-->

* **Modifications apportées à la stratégie de sécurité du contenu (CSP)**: mises à jour et améliorations de la configuration des stratégies de sécurité du contenu (CSP) Adobe Commerce pour se conformer aux exigences PCI 4.0. Pour plus d’informations, voir [Stratégies de sécurité du contenu](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) dans le _Guide du développeur PHP de Commerce_. <!--AC-11513-->

   * La configuration par défaut de la CSP pour les pages de paiement pour l’administrateur Commerce et les zones de storefront est désormais `restrict` mode . Pour toutes les autres pages, la configuration par défaut est `report-only` mode .  Dans les versions antérieures à la version 2.4.7, la stratégie de sécurité du contenu a été configurée dans `report-only` pour toutes les pages.

   * Ajout d’un fournisseur à usage unique pour permettre l’exécution de scripts intégrés dans une CSP. Le fournisseur de valeur à usage unique facilite la génération de chaînes de valeur à usage unique pour chaque requête. Les chaînes sont ensuite jointes à l’en-tête CSP.

   * Ajout d’options pour configurer des URI personnalisés afin de signaler les violations CSP pour la page Créer une commande dans l’Admin et la page Passage en caisse dans le storefront. Vous pouvez ajouter la configuration à partir de l’administrateur ou en ajoutant l’URI au `config.xml` fichier .

     >[!NOTE]
     >
     >Mise à jour de la configuration CSP vers `restrict` Le mode peut bloquer les scripts intégrés existants sur les pages de paiement dans l’Admin et le storefront, ce qui entraîne l’erreur de navigateur suivante lors du chargement d’une page : `Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`. Corrigez ces erreurs en mettant à jour la configuration de la liste blanche pour autoriser les scripts requis. Voir [Dépannage](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#troubleshooting) dans le _Guide du développeur PHP de Commerce_.

* Un nouveau paramètre de configuration du cache de la page entière peut aider à atténuer les risques associés au HTTP `{BASE-URL}/page_cache/block/esi` point de terminaison . Ce point de terminaison prend en charge les fragments de contenu sans restriction et chargés dynamiquement à partir des poignées de disposition Commerce et des structures de bloc. La nouvelle **[!UICONTROL Handles params size]** paramètre de configuration définit la valeur de ce point de terminaison. `handles` qui détermine le nombre maximal autorisé de gestionnaires par API. La valeur par défaut de cette propriété est 100. Les vendeurs peuvent modifier cette valeur à partir de l’option Admin (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles params size]**). Voir [Configuration de l’application Commerce pour l’utilisation du vernis](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/configure-varnish-commerce.html). <!-- AC-9113 -->

* **Limitation du taux natif pour les informations de paiement transmises par les API REST et GraphQL**. Les vendeurs peuvent désormais [configurer la limitation de débit](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/sales#rate-limiting) pour les informations de paiement transmises par REST et GraphQL. Cette couche de protection supplémentaire prend en charge la prévention des attaques par carte et peut éventuellement réduire le volume des attaques par carte qui testent de nombreux numéros de carte de crédit en même temps. Il s’agit d’une modification du comportement par défaut d’un point de terminaison REST existant. Voir [Limite de débit](https://developer.adobe.com/commerce/webapi/get-started/rate-limiting/).

* Le comportement par défaut de la variable [isEmailAvailable](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) Requête GraphQL et ([V1/customers/isEmailAvailable](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) Le point de terminaison REST a changé. Par défaut, les API renvoient désormais toujours `true`. Les vendeurs peuvent activer le comportement d’origine en définissant la variable *[Activation de la connexion à l’extraction des invités](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/checkout)* dans l’option Admin to `yes`, mais cela peut exposer les informations client à des utilisateurs non authentifiés.
