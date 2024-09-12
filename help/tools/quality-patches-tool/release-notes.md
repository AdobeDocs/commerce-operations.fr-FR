---
title: Notes de mise à jour
description: Découvrez les correctifs disponibles pour Adobe Commerce et les problèmes qu’ils résolvent.
exl-id: 22262555-f5ea-49ad-98ad-ea8428ef66d5
source-git-commit: b1b7152caa8a9f04ee779e4483c6b82d2002fcc7
workflow-type: tm+mt
source-wordcount: '21646'
ht-degree: 0%

---

# Notes de mise à jour

[[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) fournit des correctifs individuels développés par Adobe et par la communauté du Magento Open Source. Il vous permet d’appliquer, de rétablir et d’afficher des informations générales sur tous les correctifs individuels disponibles pour la version installée d’Adobe Commerce. Vous pouvez appliquer des correctifs aux projets Adobe Commerce et Magento Open Source, quel que soit le développeur du correctif. Par exemple, vous pouvez appliquer un correctif développé par la communauté aux projets Adobe Commerce.

>[!INFO]
>
>Voir [Application de correctifs](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches) pour obtenir des instructions sur l’application de correctifs à vos projets Adobe Commerce. Voir [[!DNL Quality Patches Tool] : Recherchez des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le Guide de mise à jour des logiciels pour consulter la liste complète des correctifs publiés.

>[!INFO]
>
>Pour plus d’informations sur [!DNL quality patches] créé par la communauté pour Magento Open Source, consultez les [notes de mise à jour](https://github.com/magento/quality-patches/blob/master/community-release-notes.md).

## v1.1.51 {#v1-1-51}

* **ACSD-59786** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.8) - Correction du problème en raison duquel GraphQL renvoie une erreur de serveur interne lors de l’obtention d’un ID de devis expiré.
* **ACSD-60234** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Correction du problème qui entraînait l’affichage d’un montant incorrect sur [!DNL PayPal] lorsque la remise était appliquée par le mode de paiement.
* **ACSD-59967** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7-p2) - Correction du problème où une erreur JavaScript empêchait [!DNL Google Maps] d’effectuer correctement le rendu.
* **ACSD-60326** (pour Adobe Commerce >=2.4.4 &lt;2.4.8) - Correction du problème qui se produit lorsqu’une erreur se produit sur la requête GraphQL pour l’état de retour du client.
* **ACSD-60538** (pour Adobe Commerce >=2.4.7 &lt;2.4.8) - Correction du problème en raison duquel si un produit est désactivé dans *[!UICONTROL All Store Views]* et activé uniquement dans des portées d’affichage de magasin spécifiques, les attributs de produit ne s’affichent pas correctement dans la réponse GraphQL, ce qui entraîne un affichage incorrect du produit.
* **ACSD-60631** (pour Adobe Commerce et Magento Open Source >=2.4.7 &lt;2.4.8) - Correction du problème où GraphQL renvoie une erreur lorsque le même produit simple est affecté à plusieurs produits configurables.
* **ACSD-60632** (pour Adobe Commerce et Magento Open Source >=2.4.5-p8 &lt;2.4.8) - Correction du problème qui entraînait l’enregistrement d’une nouvelle adresse à chaque tentative de placement de commande, que la commande ait été créée ou non.
* **ACSD-60816** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel les scripts [!DNL New Relic Browser Monitoring] injectés par l’agent APM ne sont pas conformes à la CSP (Content Security Policy), empêchant leur exécution.
* **ACSD-61195** (pour Adobe Commerce et Magento Open Source >=2.4.7 &lt;2.4.8) - Correction du problème en raison duquel aucun élément de panier n’était renvoyé sur la dernière page pour la demande GraphQL de panier.
* Correctifs mis à jour : ACSD-59378

## v1.1.50 {#v1-1-50}

* **ACSD-59280** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.5) - Correction de l’erreur *Appel à la méthode non définie ReflectionUnionType::getName()* qui se produit lors de l’installation des versions 2.4.4-pX.
* **ACSD-45049** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.4-p8) || >=2.4.5 &lt;2.4.6) - Correction du problème en raison duquel un paramètre d’attribut customer *[!UICONTROL Is required]* ne fonctionne pas correctement selon la portée du site web dans Admin.
* **ACSD-46938** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème lié aux performances des déclencheurs DB recréés pendant `setup:upgrade`.
* **ACSD-48210** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel la mise à jour d’un attribut *[!UICONTROL Website Scope]* dans une vue de magasin spécifique remplace les valeurs d’attribut dans la portée globale.
* **ACSD-54887** (pour Adobe Commerce et Magento Open Source >=2.4.4-p4 &lt;2.4.4-p9 || >=2.4.5-p3 &lt;2.4.5-p8 || >=2.4.6-p1 &lt;2.4.6-p6) - Correction du problème en raison duquel le panier du client était effacé une fois la session du client expirée avec [!UICONTROL Persistent Shopping Cart] activé.
* **ACSD-58141** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Correction du problème en raison duquel PHPSESSID régénère les demandes de POST sur la zone de storefront pour un client connecté si [!DNL L2 Redis cache] est activé et que le client est mis à jour à partir de l’administrateur.
* **ACSD-58352** (pour Adobe Commerce >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel les libellés d’attribut de retour pour la vue de magasin par défaut sont renvoyés via l’API GraphQL lorsqu’une vue de magasin autre que la vue par défaut est spécifiée dans l’en-tête de la requête.
* **ACSD-58442** (pour Adobe Commerce >=2.4.4 &lt;2.4.7-p1) - Correction du problème en raison duquel les appareils d’une largeur de 768 px sont traités comme mobiles, ce qui entraînait le chargement du menu et de l’en-tête dans une vue mobile plutôt que sur ordinateur de bureau.
* **ACSD-58790** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Correction de la fonctionnalité de pincement pour zoomer sur les images de page des détails du produit dans la vue mobile sur [!DNL Chrome].
* **ACSD-59036** (pour Adobe Commerce et Magento Open Source >=2.4.7 &lt;2.4.8) - Correction d’une exception qui se produit lors du chargement des prix des produits avec des limites inférieure et supérieure égales à 0 $.
* **ACSD-59229** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel les informations relatives aux groupes de clients étaient enregistrées dans le mauvais segment en raison de l’ancienne valeur de X-Magento-Vary dans la demande.
* **ACSD-59378** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction du problème de mise à jour incorrecte des réécritures d’URL au niveau du magasin lors de l’importation.
* **ACSD-59514** (pour Adobe Commerce >=2.4.4 &lt;2.4.7-p2) - Correction du problème en raison duquel les formulaires dans la zone d’administration avec [!DNL Page Builder] généraient l’erreur *[!DNL Page Builder]pendant 5 secondes sans déclencher de verrous.* dans la console du navigateur après l’envoi du formulaire et les modifications ne peuvent pas être enregistrées.
* **ACSD-60303** (pour Adobe Commerce >=2.4.4-p9 &lt;2.4.5 || >=2.4.5-p8 &lt;2.4.6 || >=2.4.6-p6 &lt;2.4.8) - Correction du problème qui empêchait de placer une commande provenant d’Admin si la minimisation des HTMLS était activée.
* **ACSD-60441** (pour Adobe Commerce et Magento Open Source 2.4.4-p9) || 2.4.5-p8 || 2.4.6-p6 || 2.4.7-p1) - Correction du problème lié à la mise à jour des clients via le point de terminaison `V1/customers` [!DNL REST API] lors de l’utilisation du jeton d’accès d’intégration généré à partir du serveur principal.
* Correctifs mis à jour : ACSD-57003

## v1.1.49 {#v1-1-49}

* **ACSD-56979** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème de suppression des images de produit après suppression d’une mise à jour intermédiaire.
* **ACSD-57086** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème qui empêchait le traitement correct des commandes passées à partir de sites web autres que les termes et conditions activés.
* **ACSD-57588** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel la livraison d’une commande à plusieurs adresses déclenche une erreur lors du traitement de l’ID de région.
* **ACSD-57643** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème qui entraînait l’ajout incorrect de produits avec des options personnalisées au panier via GraphQL.
* **ACSD-57846** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel la recherche de produits GraphQL avec un filtre de prix zéro ne renvoyait aucun résultat en raison d’une exception.
* **ACSD-57941** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel les options de produit étaient incorrectement affectées à la boutique d’administration au lieu de leurs magasins respectifs.
* **ACSD-58375** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel une mauvaise configuration *[!DNL YouTube API Key]* provoquait une erreur lors de l’ajout d’une vidéo [!DNL YouTube] au niveau de la vue du magasin.
* **ACSD-58739** (pour Adobe Commerce et Magento Open Source >=2.4.7 &lt;2.4.8) - Correction du problème où la réindexation partielle renvoie une erreur.
* **ACSD-58446** (pour Adobe Commerce >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel, lors de la suppression d’une équipe avec des utilisateurs enfants ou des équipes quel que soit leur état (inactif), le système fournit un message d’erreur non informatif qui n’est pas cohérent avec l’interface utilisateur.
* **ACSD-58054** (pour Adobe Commerce >=2.4.4 &lt;2.4.6) - Correction du problème où il est possible de générer des jetons client pour les clients inactifs via l’API.
* **ACSD-58163** (pour Adobe Commerce >=2.4.3 &lt;2.4.7) - Correction du problème où un *[!UICONTROL Cart Price Rule]* n’applique pas de réduction pour un client invité du panier *[!UICONTROL Customer Segment]* correspondant sans code de coupon.
* **ACSD-57045** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction du problème où les réécritures d’URL provoquent une boucle infinie de page après que *[!UICONTROL Website Root]* n’a pas été coché à partir de *[!UICONTROL Hierarchy]*.
* Correctifs mis à jour : ACSD-46815, ACSD-47027, ACSD-51683, ACSD-55031, ACSD-51819, ACSD-54965-v2

## v1.1.48 {#v1-1-48}

* **ACSD-55566** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème d’échec de la mutation `mergeCart` avec une &quot;*Erreur interne du serveur*&quot; dans la réponse [!DNL GraphQL] lors de la fusion des paniers source et de destination ayant les mêmes éléments de lot.
* **ACSD-56546** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel les produits configurables et groupés s’affichaient comme **Out of Stock** sur le storefront lorsque l’ **affichage hors configuration de produit** était *Désactivé*}.
* **ACSD-56635** (pour Adobe Commerce >=2.4.6 &lt;2.4.7) - Correction du problème de duplication du client importé avec la même adresse électronique, lorsqu’un import est utilisé avec le **partage de compte** défini sur *Global*.
* **ACSD-56741** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du message d’erreur &quot;*Tentative d’accès au décalage de tableau sur la valeur de type null*&quot; qui s’affiche pendant `setup:upgrade` lorsque la base de données contient un déclencheur [!DNL MySQL] personnalisé non lié au mécanisme d’indexation et [!DNL MView].
* **ACSD-57315** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème lorsqu’une nouvelle transaction est créée dans [!DNL PayPal Payflow Pro] chaque fois que l’utilisateur clique sur le bouton [!UICONTROL Fetch] de l’écran **[!UICONTROL View transaction]** de l’administrateur.
* **ACSD-57337** (pour Adobe Commerce >=2.4.4 &lt;2.4.6) - Correction du problème en raison duquel un utilisateur administrateur avec des restrictions d’accès à des sites web spécifiques pouvait voir des entreprises de tous les sites web dans la grille **[!UICONTROL Companies]**.
* **ACSD-57394** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème de tri incorrect des produits selon plusieurs champs de tri dans [!DNL GraphQL].
* **ACSD-57565** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel le tableau de bord **[!UICONTROL Order]** affichait des informations de commande incorrectes jusqu’à la mise à jour de la période. Le tableau de bord affiche désormais les statistiques de commande correctes au premier chargement.
* **ACSD-57854** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème lorsque les demandes de produit [!DNL GraphQL] renvoyaient des catégories désactivées dans les agrégations de catégories.
* **ACSD-58008** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel la mise à jour d’une mise à jour planifiée supprimait la version précédente d’un élément intermédiaire, si aucune date de fin n’était spécifiée.
* Correctifs mis à jour : MDVA-39305-V2, ACSD-48627, ACSD-54965

## v1.1.47 {#v1-1-47}

* **ACSD-55241** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel les attributs *[!UICONTROL Used]* et *[!UICONTROL Times Used]* affichaient des valeurs incorrectes pour les bons générés lors de l’extraction avec plusieurs adresses.
* **ACSD-56760** (pour Adobe Commerce >=2.4.6 &lt;2.4.7) - Correction du problème qui empêchait un utilisateur administrateur limité à un site web spécifique de trier ou d’ajouter de nouveaux produits dans une catégorie au cas où le magasin web avait sa propre catégorie racine.
* **ACSD-56858** (pour Adobe Commerce >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel les autorisations de rôle d’entreprise B2B s’affichaient incorrectement pour un administrateur d’entreprise restreint.
* **ACSD-57074** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel l’attribut personnalisé *Oui/Non* avec `attrbute_code` commençant par `price_` ne fonctionne pas correctement avec l’indexation et les produits avec de tels attributs ne sont pas disponibles sur le front-end.
* Correctifs mis à jour : ACSD-53378, ACSD-51819

## v1.1.46 {#v1-1-46}

* **ACSD-46767** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème en raison duquel la page de catégories caches invalidée lorsque la quantité de stock change, même si le produit est toujours en stock.
* **ACSD-54656** (pour Adobe Commerce >=2.4.5 &lt;2.4.6) - Correction du problème d’échec de la récupération invisible lors de l’extraction, empêchant le placement d’une commande.
* **ACSD-55100** (pour Adobe Commerce >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel GraphQL ne renvoie pas plus de 10 000 produits dans les résultats de recherche.
* **ACSD-56621** (pour Adobe Commerce >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel le prénom et le nom mis à jour ne sont pas reflétés dans la section d’en-tête des salutations pour l’utilisateur administrateur de la société.
* **ACSD-56842** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème de l’absence des proxies différées et des usines de proxy différées après l’exécution de `setup:di:compile`.
* **ACSD-57003** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel l’état de la commande était remplacé par *[!UICONTROL Complete]* au lieu d’être remplacé par *[!UICONTROL Processing]* lorsqu’une commande est partiellement remboursée et partiellement expédiée.
* Correctifs mis à jour : ACSD-50260-v2, ACSD-54966

## v1.1.45 {#v1-1-45}

* **ACSD-56886** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème où un produit configurable est en rupture de stock lorsqu’un des deux produits enfants est désactivé par une mise à jour planifiée.
* **ACSD-56616** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction du problème où les produits regroupés s’affichent en stock sur le storefront lorsque leurs produits simples sont en rupture de stock.
* **ACSD-56515** (pour Adobe Commerce >=2.4.2 &lt;2.4.7) - Correction du problème qui empêchait l’administrateur disposant d’autorisations au niveau du site web d’ajouter ou de modifier un bloc dynamique.
* **ACSD-56447** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel l’ajout du même produit au panier via des demandes d’API Web REST parallèles générait deux éléments distincts dans le panier.
* **ACSD-56415** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème de ralentissement des performances de l’indexation de prix partielle en raison d’une requête `DELETE` lorsque la base de données contient un grand nombre de données de prix partiel à indexer.
* **ACSD-54965** (pour Adobe Commerce >=2.4.5 &lt;2.4.6) - Correction du problème en raison duquel la grille de marchandisage visuel n’affichait pas le stock correct lorsqu’un produit était affecté à un stock personnalisé uniquement.
* **ACSD-52824** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction du problème d’affichage des boutons PayPal Express, Google Pay et Apple Pay pour les clients de l’entreprise lorsque ces méthodes de paiement sont désactivées dans les paramètres de l’entreprise.
* Correctifs mis à jour : ACSD-56193

## v1.1.44 {#v1-1-44}

* **ACSD-56790** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème où un utilisateur est redirigé vers le tableau de bord Admin lors du tri des produits de catégorie à l’aide de l’option **Déplacer hors stock vers le bas** et l’erreur `Invalid security or form key. Please refresh the page` s’affiche en haut de l’écran.
* **ACSD-56280** (pour Adobe Commerce >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel la commande d’éléments à partir d’un registre de cadeaux entraînait une exception.
* **ACSD-56246** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel les données sont supprimées de l’attribut de sélection multiple personnalisé lorsqu’une mise à jour planifiée d’un produit devient active.
* **ACSD-56193** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4) - Correction du problème en raison duquel le cache de vernis/Fastly n’est pas mis à jour lorsqu’un bloc planifié est utilisé dans la description de catégorie à l’aide du générateur de pages.
* **ACSD-56158** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel la requête &quot;panier&quot; renvoyait la valeur de taxe totale pour chaque règle de taxe.
* **ACSD-56023** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel le contenu du widget n’était pas mis à jour sur la page CMS lorsque le cache était activé.
* **ACSD-55427** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction du problème qui empêchait l’utilisateur administrateur d’annuler l’affectation d’un produit d’un catalogue partagé à partir de la page de produit dans l’administrateur.
* **ACSD-55352** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel, après la création d’une note de crédit partielle avec des points de récompense client, l’état de la commande passe à Fermé et les options de note de crédit disparaissent de la page de commande Admin.
* **ACSD-55231** (pour Adobe Commerce >=2.4.2 &lt;2.4.7) - Correction du problème qui empêchait d’ajouter des produits à un panier à l’aide de la fonctionnalité de commande rapide.
* **ACSD-54283** (pour Adobe Commerce >=2.4.3 &lt;2.4.4) - Correction du problème en raison duquel les produits/catégories non affectés au catalogue partagé par défaut (groupe général) étaient toujours inclus dans le plan de site XML.
* Correctifs mis à jour : ACSD-52041, ACSD-54040, ACSD-51819

## v1.1.43 {#v1-1-43}

* **ACSD-54972** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel l’URL de catégorie canonique n’était pas mise à jour après modification de l’URL de catégorie.
* **ACSD-53636** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.5) - Correction du problème en raison duquel le prix normal ne s’affichait pas sur les pages de liste de produits pour les produits configurables ayant des produits enfants avec des prix spéciaux.
* **ACSD-54885** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème lié au passage en caisse de plusieurs adresses lorsque l’utilisateur administrateur utilise la fonctionnalité *Se connecter en tant que client* .
* **ACSD-55610** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel une commande partiellement annulée avait un montant de remise incorrect.
* **ACSD-55334** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction des traductions des libellés par le biais des dictionnaires de traduction dans la réponse GraphQL.
* **ACSD-54739** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel la condition d’état du stock de produit n’était pas appliquée pour les règles de produit associées.
* **ACSD-53925** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème qui empêchait l’administrateur d’enregistrer le bloc CMS avec le carrousel de produit lorsque `catalog_product_price` dimensions-mode était défini sur *site web*.
* **ACSD-52714** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel le filtre de date ne fonctionnait pas dans la grille d’administration lorsque le format de date était défini sur *Y-m-d*.
* **ACSD-55055** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Améliore les performances de chargement des attributs de produit dans les règles de prix du panier dans le panier.
* **ACSD-53790** (pour Adobe Commerce >=2.4.6 &lt;2.4.7) - Correction du problème de création de plusieurs RMA pour un seul produit via l’API REST.
* **ACSD-56090** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.5) - Correction du problème en raison duquel la demande GraphQL répondait avec toutes les données des magasins plutôt que avec les données de magasin demandées spécifiquement.
* **ACSD-54983** (pour Adobe Commerce >=2.4.2 &lt;2.4.7) - Correction du problème qui empêchait d’obtenir l’utilisateur de l’entreprise UID avec la demande GraphQL lorsque l’état de l’utilisateur était défini sur *[!UICONTROL Inactive]*.
* **ACSD-53309** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel la taxe n’est pas entièrement appliquée dans l’étiquette *[!UICONTROL Regular Price]* lorsque l’option personnalisable est sélectionnée.
* **ACSD-55305** (pour Adobe Commerce >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel la fenêtre contextuelle *[!UICONTROL Edit Company User]* de la page **[!UICONTROL myAccount]** > **[!UICONTROL Company Structure]** se bloque avec un chargeur à l’écran.
* Correctifs mis à jour : ACSD-49013

## v1.1.42 {#v1-1-42}

* **ACSD-53658** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel les données de produit *[!UICONTROL Recently Viewed]* n’étaient pas correctement mises à jour dans la vue de magasin.
* **ACSD-54626** (pour Adobe Commerce >=2.4.6 &lt;2.4.7) - Correction du problème qui empêchait de créer une nouvelle règle de bon de commande (`createPurchaseOrderApprovalRule`) avec l’attribut `NUMBER_OF_SKUS` via [!DNL GraphQL].
* **ACSD-53845** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction du problème de délai de connexion [!DNL MySQL] lorsque `consumer max_messages` = 0.
* **ACSD-54890** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction du problème où `aggregate_sales_report_bestsellers_data` provoquait des erreurs [!DNL MySQL] en raison d’un manque d’espace disque `/tmp`.
* **ACSD-55112** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction du problème en raison duquel il était possible de cliquer plusieurs fois sur le bouton *[!UICONTROL Submit review]* sans validation [!DNL Google reCAPTCHA v3].
* **ACSD-54264** (pour Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.7) - Correction du problème en raison duquel le message d’erreur *&quot;Vous ne pouvez pas mettre à jour l’attribut demandé. ID de ligne : store_id&quot;* s’affiche lorsqu’un client tente d’extraire avec un guillemet négociable provenant d’une autre vue de magasin.
* **ACSD-54418** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction du problème où un montant fixe de remise est incorrectement appliqué à chaque produit enfant du lot à prix dynamique.
* **ACSD-55238** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correctifs de l’enregistrement du produit vide *[!UICONTROL Meta Description]*.
* **ACSD-54966** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel un code de bon avec une utilisation limitée par client ne peut pas être réutilisé en cas d’échec de la commande précédente.
* **ACSD-54060** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème où un administrateur restreint ne peut pas enregistrer un produit s’il est un enfant d’un autre produit affecté à une autre portée.
* **ACSD-48910** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction du problème en raison duquel un produit en lot affecté à plusieurs sources est en rupture de stock après la facturation et l’expédition d’une commande, même s’il a toujours une quantité non nulle.
* **ACSD-55381** (pour Adobe Commerce >=2.4.2 &lt;2.4.7) - Correction d’une erreur de serveur interne lors de l’interrogation des champs `configurable_product_option_uid` et `configurable_product_option_value_uid` d’un [!DNL B2B] *[!UICONTROL Requisition list]* via [!DNL GraphQL].
* **ACSD-55628** (pour Adobe Commerce >=2.4.4-p2 &lt; 2.4.5 || >=2.4.5-p1 &lt; 2.4.6) - Correction du téléchargement d’un fichier sur le formulaire d’enregistrement de la société et du remplacement d’un fichier pour un attribut du client sur le storefront.
* Correctifs mis à jour : ACSD-51240, ACSD-51890, ACSD-53098

## v1.1.41 {#v1-1-41}

* **ACSD-54376** (pour Adobe Commerce >=2.4.2 &lt;2.4.7) - Correction du problème qui se produit dans le panier lorsqu’un produit est supprimé du catalogue partagé après avoir été ajouté au panier.
* **ACSD-53722** (pour Adobe Commerce >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel le prix des options de produit regroupées passe à 0 $ lorsque des mises à jour planifiées pour différentes portées deviennent actives.
* **ACSD-53643** (pour Adobe Commerce >=2.4.3 &lt;2.4.7) - Correction du problème où le total de la commande est incorrect lors du placement d’une commande avec des produits désactivés ou en rupture de stock. Elle est corrigée en masquant le bouton *[!UICONTROL Place Order]* pour ces commandes.
* **ACSD-54067** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction du problème de lecture d’une vidéo de produit sur un appareil mobile.
* **ACSD-55414** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Améliore les performances lorsque la MariaDB tente de convertir l’entity_id du fichier EAV de chaîne en entier.
* **ACSD-51819** (pour Adobe Commerce >=2.4.4 &lt;2.4.4-p4) - Correction du problème en raison duquel plusieurs commandes peuvent être placées avec le même ID de guillemet.
* **ACSD-53118** (pour Adobe Commerce >=2.4.0 &lt;2.4.7) - Correction du problème qui entraînait l’application de *[!UICONTROL Cart Price Rule]* à l’aide du code de bon alors que le produit avait un attribut vide.
* **ACSD-54324** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel la demande de GraphQL request_lists ne prend pas en compte les paramètres de pagination et renvoie tous les résultats.
* Correctifs mis à jour : MDVA-42855-v2

## v1.1.40 {#v1-1-40}

* **ACSD-54680** (pour Adobe Commerce >=2.4.0 &lt;2.4.6) - Résout le problème où il n’est pas possible de traiter une citation B2B envoyée pour un produit avec plusieurs sources affectées.
* **ACSD-54040** (pour Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2.4.5-p4 &lt;2.4.6) - Correction du problème en raison duquel le champ *[!UICONTROL Created]* était vide dans les détails de l’ordre lorsque les modules B2B étaient activés.
* **ACSD-54319** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6) - Correction du problème en raison duquel le prix du produit affichait zéro dans le rapport *[!UICONTROL Product in Cart]*.
* **ACSD-53378** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Améliore le temps de chargement de la page de passage en caisse pour les clients qui disposent de carnets d’adresses volumineux.
* **ACSD-52657** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel le minicart n’est pas mis à jour dans l’aperçu de magasin secondaire, qui utilise un sous-domaine.
* **ACSD-53414** (pour Adobe Commerce >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel un utilisateur administrateur restreint pouvait voir des pages CMS en dehors de leur portée d’autorisation.
* **ACSD-54472** (pour Adobe Commerce >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel les clients d’une société rejetée peuvent toujours s’authentifier, et les clients d’une société bloquée et rejetée peuvent toujours passer des commandes. Le correctif ajoute une validation supplémentaire pour les points de terminaison GraphQL.
* **ACSD-52801** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Ajoute l’option permettant d’effectuer une correspondance partielle lors de la recherche de produits dans GraphQL.
* **ACSD-55004** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel le programme de validation se bloque lors du téléchargement d’un fichier d’importation supérieur à la valeur configurée dans `php.ini`.
* **ACSD-54989** (pour Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.7) - Correction du problème qui empêchait l’administrateur d’une société de passer une commande lorsque *[!UICONTROL Enable Purchase Orders]* est défini sur *[!UICONTROL Yes]* et *[!UICONTROL Purchase Order]* sur *[!UICONTROL No]*.
* **ACSD-54007** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction de l’erreur *&quot;Clé de tableau non définie &quot;_scope&quot;* lors de l’importation de données client.
* **ACSD-55031** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction de l’erreur *Type &quot;mixte&quot; ne peut pas être nul* lors de la compilation.
* **ACSD-54961** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction du problème où un utilisateur administrateur restreint ne peut pas mettre à jour en masse l’état *Product Review*.
* **ACSD-55256** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel seule la première image s’affichait correctement dans le curseur de l’image.
* Correctifs mis à jour : ACSD-52041, ACSD-54106

## v1.1.39 {#v1-1-39}

* **ACSD-53704** (pour Adobe Commerce >=2.4.0 &lt;2.4.7) - Correction du problème en raison duquel l’historique d’équilibrage des points de récompense est mal calculé après l’expiration des points de récompense.
* **ACSD-53583** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Améliore les performances de réindexation partielle pour les indexeurs *Category Products* et *Product Categories*.
* **ACSD-54026** (pour Adobe Commerce >=2.4.6 &lt;2.4.7) - Correction d’un message d’erreur incorrect pour une requête GraphQL `updateCompanyRole` pour un utilisateur non autorisé.
* **ACSD-54106** (pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.5) - Correction du problème en raison duquel le tri des produits de catégorie par nom pour les caractères accentués turcs était incorrect.
* **ACSD-52219** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel les filtres enregistrés des grilles d’administration ne fonctionnaient pas comme prévu lors du basculement fréquent entre les vues de signet.
* **ACSD-54342** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction d’un message d’erreur incorrect *Erreur dans la structure des données : les valeurs sont mélangées* lors de l’importation d’un fichier CSV sans données valides.
* **ACSD-54660** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Ajout d’un nouvel attribut d’entrée *sort* pour trier les commandes client dans GraphQL par `sort_field` et `sort_direction`.
* **ACSD-54776** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel les valeurs de champs de produit non cochées *[!UICONTROL Use Default Value]* et non cochées par défaut ne sont pas enregistrées pour la deuxième vue de site Web, de magasin et de magasin.
* **ACSD-53998** (pour Adobe Commerce et Magento Open Source >=2.4.4-p2 &lt;2.4.5 || >=2.4.5-p1 &lt;2.4.7) - Correction du problème en raison duquel un **[!UICONTROL Dynamic Block]** basé sur un **[!UICONTROL Customer Segment]** ne fonctionnait pas correctement après déconnexion d’un compte client.
* **ACSD-53204** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correctifs *Le produit ne peut pas être enregistré.* lors de demandes simultanées d’ajout d’images à la galerie de produits à l’aide du point de terminaison `rest/V1/products/<sku>/media`.
* **ACSD-47657** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Ajout d’un mécanisme de mise en cache pour les informations d’identification AWS. Un fournisseur d’informations d’identification utilise désormais le cache du Magento pour mettre en cache les informations d’identification extraites d’AWS pour la configuration EC2.
* Mise à jour des correctifs : ACSD-51984, ACSD-51574.

## v1.1.38 {#v1-1-38}

* **ACSD-53098** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4) - Correction du problème en raison duquel les produits affectés à un catalogue partagé n’apparaissent pas sur le storefront lorsqu’un index partiel est exécuté.
* **ACSD-54018** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.6) - Correction des problèmes de performances avec le widget [!UICONTROL Product List] qui utilise un attribut non global dans la condition du widget.
* **ACSD-5411** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6) - Correction du problème en raison duquel les images miniatures du produit ne s’affichent pas sur le storefront lorsque les proportions de l’image de filigrane ne correspondent pas à l’image du produit.
* **ACSD-47669** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6) - Correction d’une *violation de contrainte d’intégrité : 1452 Impossible d’ajouter ou de mettre à jour une ligne enfant : une contrainte de clé étrangère échoue* lors de l’importation de produits CSV.
* **ACSD-53347** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème où l’indexeur de prix prend trop de temps à s’exécuter.
* **ACSD-52287** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction du problème avec un état d’ordre incorrect dans la grille d’ordre archivée lorsque l’indexation de grille asynchrone est activée.
* **ACSD-52929** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème lié aux demandes redondantes de réindexation des éléments source par défaut lorsque l’indexeur d’inventaire est configuré en mode asynchrone.
* **ACSD-53824** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel `UpdateMultiselectAttributesBackendTypes` le correctif de données de migration dépasse la limite de taille de transaction de la base de données pendant `setup:upgrade`.

## v1.1.37 {#v1-1-37}

* **ACSD-52613** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème d’actualisation des caches et des index même lorsqu’aucune mise à jour n’est apportée aux éléments `Inventory_source` par l’API REST.
* **ACSD-51884** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel le chemin du cache de l’image du produit était incorrect après l’exécution de la commande de redimensionnement.
* **ACSD-53628** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel le rapport de commande client CSV affichait des caractères spéciaux incorrects.
* **ACSD-53148** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel deux demandes parallèles dans GraphQL pour l’ajout du même produit configurable au panier généraient deux articles distincts sur le panier avec le même SKU de produit.
* **ACSD-52606** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction du problème qui entraînait l’affichage du message d’erreur *Votre commande n’est pas prête pour la récupération* lorsque l’utilisateur clique sur **[!UICONTROL Notify Order is Ready for Pickup]**.
* **ACSD-51574** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel l’image n’est pas mise à jour sur le front-end après son remplacement par une autre image portant le même nom.
* **ACSD-53728** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel l’indexeur EAV du produit prend plus de temps à se terminer.
* **ACSD-53979** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème JS qui se produit sur la page d’accueil si le message de bienvenue contient un guillemet simple.
* **ACSD-52085** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel un produit configurable avec un prix spécial n’est pas visible dans le carrousel du produit.
* **ACSD-53795** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème lié à un type de données non valide dans la tâche cron `indexer_update_all_views`.
* **ACSD-52143** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème de suppression des options personnalisées après l’importation du produit.
* **ACSD-53750** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction de l’erreur *pipe endommagée ou connexion fermée* lors de la réindexation `catalog_product_price` multithread.
* **ACSD-49843** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.0 || >=2.4.1 &lt;2.4.7) - Correction du problème en raison duquel le lien sur le téléchargement de produit n’est pas disponible une fois que l’article commandé est automatiquement facturé par le mode de paiement en ligne avec le paramètre **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]** activé.
* **ACSD-47054** (pour Adobe Commerce >=2.4.2 &lt;2.4.6) - Correction du problème en raison duquel la réindexation de l’aperçu s’exécute pour tous les magasins, ce qui entraîne une lenteur.
* Ajout de nouvelles versions pour ACSD-46541, ACSD-47079.
* ACSD-49970-v3 remplacé par ACSD-54095.

## v1.1.36 {#v1-1-36}

* **ACSD-53239** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt; 2.4.6) - Correction du problème en raison duquel l’indexeur d’inventaire nettoie tous les caches en mode Mise à jour en programmation.
* **ACSD-5087** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction du problème en raison duquel la propriété d’attribut de produit *[!UICONTROL Use in Search Results Layered Navigation]* peut être définie sur *Oui* sans l’option *[!UICONTROL Use in search]* définie sur *Oui*.
* **ACSD-51846** (pour Adobe Commerce et Magento Open Source >=2.4.3-p2 &lt;2.4.6) - Correction du problème *Erreur interne* qui se produit car tous les niveaux de charge utile de l’API REST ne sont pas validés.
* **ACSD-52906** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction du problème de définition incorrecte du cookie X-Magento-Vary pour les clients connectés qui appartiennent au même segment de client, ce qui entraîne une mise en cache incorrecte de certaines pages.
* **ACSD-52736** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.6) - Correction du problème en raison duquel une *règle de prix du panier* qui inclut des exigences de quantité configurable de produits ne fonctionne pas comme prévu.
* **ACSD-47875** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème qui empêchait les utilisateurs administrateurs d’ajouter un produit au panier d’un client à partir de l’administrateur pour une portée de vue de magasin particulière avec gestion de l’inventaire.
* **ACSD-53176** (pour Adobe Commerce >=2.3.7 &lt;2.4.5) - Correction du problème en raison duquel *Règle de produit connexe* avec *est une condition de* ne correspond pas aux produits.
* **ACSD-51666** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction de l’erreur *La session a expiré, veuillez vous reconnecter.* qui se produit lorsqu’un client tente de se connecter.
* Ajout de nouvelles versions pour MDVA-39305-v2.
* Mise à jour des exigences pour ACSD-19640.

## v1.1.35 {#v1-1-35}

* **ACSD-51899** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction du problème en raison duquel l’adresse de livraison par défaut à l’étape de livraison du passage en caisse était automatiquement renseignée avec une adresse de récupération en magasin précédemment sélectionnée.
* **ACSD-52041** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel le message d’erreur : *[ERROR] [!DNL Page Builder] était affiché pendant 5 secondes sans déclencher de verrouillage.* apparaît dans le navigateur Chrome lors de l’enregistrement du contenu modifié avec [!DNL Page Builder].
* **ACSD-52095** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.6) - Correction du problème en raison duquel la valeur `manage_stock` était incorrectement définie sur 0 dans le fichier CSV après l’exportation du produit.
* **ACSD-51358** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel la suppression d’une mise à jour planifiée sans date de fin entraîne la suppression d’autres mises à jour planifiées pour la même entité.
* **ACSD-48070** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel la modification d’une mise à jour planifiée déclenche une exception.
* **ACSD-51890** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction du problème en raison duquel il était possible de cliquer plusieurs fois sur le bouton [!UICONTROL Submit review] sans validation [!DNL Google reCAPTCHA] v3.
* **ACSD-51984** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel les valeurs *[!UICONTROL Use Default Value]* et *[!UICONTROL non-default product field]* non cochées ne sont pas enregistrées pour la deuxième vue de site Web, de magasin et de magasin.
* **ACSD-52398** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction de l’erreur *La quantité demandée n’est pas disponible* qui se produit lors de la tentative de mise à jour de la quantité d’un produit fourni dans le panier sur le storefront.
* **ACSD-52786** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction du problème où une condition de règle de catalogue *SKU is* s’applique à tous les produits commençant par le SKU donné.
* **ACSD-52921** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème qui se produit lorsqu’une erreur interne se produit lors de la demande de détails de panier auprès de GraphQL lorsqu’un produit configurable en rupture de stock se trouve dans le panier.
* **ACSD-51683** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel une option personnalisable ne pouvait pas être ajoutée au panier à l’aide de GraphQL.
* **ACSD-52133** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème qui empêchait l’enregistrement d’un compte client après une mise à niveau.
* **ACSD-52202** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème en raison duquel la quantité vendable du stock par défaut passe incorrectement à 0 lorsqu’un stock autre que le stock par défaut est remplacé par 0 qté lors de l’exécution de la commande.
* **ACSD-51265** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème lié aux performances de réindexation de `catalog_product_price` lorsqu’il y a trop de produits regroupés dans le système.
* **ACSD-52831** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction du problème qui empêchait les clients d’envoyer des commandes de devis négociables lorsque [!DNL Google reCAPTCHA v3 Invisible] était activé.
* **ACSD-51845** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel les produits suivants avec des prix de niveau et différents ensembles d’attributs ne pouvaient pas être mis à jour via l’API REST en bloc asynchrone.
* **ACSD-52815** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel l’entrée du champ de quantité d’une source autre que par défaut ne prend en charge que 6 chiffres au maximum, contrairement à 8 pour un stock par défaut.
* **ACSD-51149** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel ImportExport planifié avec les autorisations de catalogue activées invalide les indexeurs, puis vident le cache par cron.
* **ACSD-50815** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction du problème en raison duquel la quantité décimale pour un produit simple ne peut pas être utilisée pour une nouvelle option Produit groupé .
* Mise à jour des versions pour ACSD-47803.
* Titre mis à jour pour ACSD-51892.
* Mise à jour de ACSD-51379.
* Mise à jour de ACSD-49970-v2.

## v1.1.34 {#v1-1-34}

* **ACSD-52277** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction du problème en raison duquel un utilisateur administrateur n’est pas redirigé correctement après avoir sélectionné une vue de magasin lors de la création d’une commande dans Admin.
* **ACSD-50813** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel l’administrateur n’était pas en mesure d’ajouter des produits regroupés contenant une barre oblique dans le SKU avec la fonctionnalité [!UICONTROL Add Products by SKU] dans l’ordre d’administration.
* **ACSD-51630** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème en raison duquel un grand nombre de messages système ralentissait le téléchargement des pages d’administration.
* **ACSD-51853** (pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.7) - Correction du problème en raison duquel les styles de texte copiés ne sont pas appliqués lors de l’utilisation de [!UICONTROL Page Builder].
* **ACSD-52160** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel le résultat de la validation du produit par rapport à la règle du prix du panier n’était pas correctement évalué en fonction de la condition de la règle &quot;Si un article est TROUVÉ/INTROUVABLE dans le panier avec toutes/n’importe laquelle de ces conditions vraies&quot;.
* **ACSD-51636** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel l’administrateur de l’entreprise ne pouvait pas ajouter de nouveaux utilisateurs à partir de la section du compte client malgré tous les rôles et autorisations nécessaires.
* **ACSD-51739** (pour Adobe Commerce >=2.4.6 &lt;2.4.7) - Correction du problème où une erreur est renvoyée lorsqu’un `structure_id` est demandé dans une requête GraphQL CompanyTeam.
* **ACSD-51857** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction du problème de lenteur des performances du rapport `aggregate_sales_report_bestsellers_data` cron sur les tables de base de données de commande de ventes volumineuses et `sales_order_item` en raison de la manière dont la requête de données principale était écrite.
* **ACSD-48448** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction d’un problème de condition de concurrence survenant lors des annulations de commande, qui entraîne une entrée dupliquée dans la table `inventory_reservation`.
* **ACSD-52689** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.6) - Correction du problème qui empêchait le téléchargement des images vers le stockage Amazon S3 à l’aide de l’API REST.
* **B2B-2674** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Ajoutez la fonctionnalité de mise en cache à la requête GraphQL 1customAttributeMetadata1.
* Ajout de nouvelles versions pour ACSD-44938.
* Ajout des exigences pour ACSD-46988.

## v1.1.33 {#v1-1-33}

* **ACSD-50478** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.5) - Correction de la commande de restauration de la base de données pour un cas où le fichier de sauvegarde DB contient des déclencheurs et une commande SQL *délimiteur*.
* **ACSD-50512** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction de l’erreur *Le lien téléchargeable n’est pas lié au produit. Vérifiez le lien et réessayez.* erreur qui se produit lors de la mise à jour de la date de début d’une mise à jour intermédiaire de produit téléchargeable.
* **ACSD-50949** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel le filtre de prix dans la recherche avancée ne renvoyait pas de résultats appropriés lorsqu’il était utilisé avec le filtre SKU.
* **ACSD-51645** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction de l’erreur générée lors de l’enregistrement d’une nouvelle règle de prix du panier si l’extension `Magento_OfflineShipping` est désactivée.
* **ACSD-50895** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel [!DNL Google Analytics] 3 balises GTM ne sont pas déclenchées si [!DNL Google Analytics] 4 GTM n’est pas configuré.
* **ACSD-51102** (pour Adobe Commerce >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel une règle de catalogue appliquée à un grand nombre de produits n’est pas correctement indexée lorsque la règle est activée par une mise à jour planifiée.
* **ACSD-50368** (pour Adobe Commerce et Magento Open Source >= 2.4.3 &lt;2.4.5) - Correction du problème en raison duquel les `group_id` du client sont ignorés lorsqu’un client est créé via l’API REST asynchrone ou l’API REST asynchrone en bloc.
* **ACSD-51497** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7) - Correction du problème qui empêchait un client de trier une page de catalogue par attribut personnalisé du type de liste déroulante.
* **ACSD-51408** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt; 2.4.7) - Correction du problème en raison duquel l’état de l’élément de commande était incorrectement défini sur *[!UICONTROL Backordered]*.
* **ACSD-51735** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.5) - Correction du problème en raison duquel l’état de l’élément de commande était incorrectement défini sur *[!UICONTROL Ordered]* lorsque le stock de produit était *0*.
* **ACSD-51792** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction du problème où une page ne comporte pas l’événement d’impression lorsque [!DNL Google Tag Manager] 4 est activé.
* **ACSD-51471** (pour Adobe Commerce >=2.4.3 &lt;2.4.7) - Correction du problème qui empêchait un utilisateur administrateur d’enregistrer une mise à jour planifiée pour un produit fourni qui utilise un produit simple dont la mise à jour est planifiée.
* **ACSD-51700** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction de l’erreur qui se produit lors du changement d’affichage de magasin sur une page de modification de produit téléchargeable dans l’administrateur.
* **ACSD-51120** (pour Adobe Commerce >=2.3.7 &lt;2.4.3) - Correction du problème en raison duquel le cache des demandes de GET GraphQL n’est pas effacé pour les pages CMS qui contiennent des blocs CMS mis à jour par le biais d’une mise à jour intermédiaire.
* **ACSD-51240** (pour Adobe Commerce >=2.4.4 &lt;2.4.6) - Correction du problème d’absence du fichier téléchargé si l’enregistrement est effectué via le formulaire d’enregistrement de l’entreprise.
* **ACSD-51907** (pour Adobe Commerce >=2.4.2 &lt;2.4.3) - Correction du problème qui empêchait un utilisateur administrateur restreint de créer une note de crédit avec un remboursement hors ligne.
* **ACSD-52148** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.4) - Correction du problème d’échec occasionnel de la connexion de l’administrateur [!DNL Google V3 reCAPTCHA].
* **ACSD-51431** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème où un état d’indexeur est *fonctionnel* même s’il n’y a aucune nouvelle entrée dans le fichier de modification.
* **ACSD-51892** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème de performances où les fichiers de configuration se chargent plusieurs fois.
* ACSD-51114 obsolète.

## v1.1.32 {#v1-1-32}

* **ACSD-49628** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème où les erreurs [!UICONTROL Page Builder's] multiples empêchent l’administrateur d’enregistrer un produit sans autorisations de contenu.
* **ACSD-51305** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel les produits enfants configurables en rupture de stock ne sont pas disponibles dans la réponse GraphQL.
* **ACSD-50621** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel [!UICONTROL Tier Prices] pour les différents sites web du catalogue partagé ne sont pas visibles lors de la tentative de modification dans un environnement multisite.
* **ACSD-51041** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.0 || >=2.4.1 &lt;2.4.6) - Améliore les performances de l’indexeur de prix.
* **ACSD-51379** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel les modifications apportées au contenu du texte de la page via [!UICONTROL Page Builder] ne sont pas enregistrées.
* **ACSD-49480** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème en raison duquel une seule règle de prix de panier était appliquée au panier.
* **ACSD-51230** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction du problème de suppression du compte de carte-cadeau lorsqu’un remboursement partiel d’un produit simple est traité à partir d’une commande.
* **ACSD-51238** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel la source de stock était supprimée lors de la mise à jour des produits configurables et de la modification du prix.
* **ACSD-50794** (pour Adobe Commerce >=2.4.1 &lt;2.4.7) - Correction du problème en raison duquel les détails du message cadeau ou de l’emballage de cadeau ne sont pas mis à jour dans la base de données lors de sa suppression via GraphQL.
* **ACSD-51528** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel la colonne *x_uplo_for* avait des valeurs null dans la table *sales_order*.
* **ACSD-50849** (pour Adobe Commerce >=2.4.4 &lt;2.4.6) - Correction du problème en raison duquel l’ajout d’un nouveau produit à la catégorie après avoir effacé le cache entraînait une incohérence des positions et des sélections des produits existants.
* **ACSD-51294** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel le prix, la quantité, la taxe, l’expédition et le revenu GTM/GA sont envoyés sous forme de chaîne à [!DNL Google Analytics] et GTM.
* **ACSD-51204** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème en raison duquel un produit entièrement vendu ne revenait pas en stock après la création d’une note de crédit.
* **ACSD-51291** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.4-p4 || >=2.4.5 &lt;2.4.5-p3) : correction du problème en raison duquel un administrateur restreint ayant accès à un site web pouvait ajouter des images/vidéos au produit affecté à plusieurs sites web.
* Ajout de nouvelles versions pour ACSD-50336.
* Correctifs remplacés ACSD-49970.

## v1.1.31 {#v1-1-31}

* **ACSD-50345** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4 || >=2.4.4-p1 &lt;2.4.6) - Correction du problème en raison duquel Recaptcha v2 ne se rechargeait pas après l’envoi d’un paiement en échec.
* **ACSD-50817** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Optimise la tâche Cron `sales_clean_quotes` pour une exécution plus rapide.
* **ACSD-49392** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7) - Correction du problème en raison duquel l’état de la commande se fermait après un remboursement partiel pour un produit fourni.
* **ACSD-51036** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.5) - Correction du problème en raison duquel les conditions de concurrence lors d’appels API REST simultanés entraînent le remplacement des informations d’état de livraison dans le tableau [!UICONTROL Items Ordered].
* **ACSD-50858** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Améliore les performances de chargement du contenu des bannières.
* Ajout de nouvelles versions pour MDVA-39305-v2, ACSD-45169.
* Mise à jour des correctifs ACSD-50260-v2.

## v1.1.30 {#v1-1-30}

* **ACSD-50336** (pour Adobe Commerce et Magento Open Source >=2.4.4-p1 &lt;2.4.4-p3) - Correction du problème en raison duquel les e-mails d’alerte de produit ne sont pas envoyés lorsqu’un produit est de nouveau en stock ou que le prix est modifié.
* **ACSD-50367** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel l’exportation de l’adresse du client ne fonctionne pas lors de la création d’un attribut d’adresse du client à sélection multiple sans valeurs.
* **ACSD-49877** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel la lecture automatique de la vidéo ne fonctionne pas sur le mobile [!DNL Safari] lorsque la vidéo est directement liée à un fichier vidéo distant et non à un service de diffusion en continu.
* **ACSD-50165** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction de l’erreur *Le fichier ne peut pas être supprimé. Warning!unlink : aucun fichier ou répertoire de ce type n’est défini lors de la purge du cache JS/CSS de l’administrateur.*
* **ACSD-49737** (pour Adobe Commerce et Magento Open Source >=2.4.1-p1 &lt;2.4.7) - Correction du problème en raison duquel un coupon est incorrectement marqué comme utilisé après l’échec du paiement de la carte.
* **ACSD-50814** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème qui empêchait un utilisateur administrateur de créer une note de crédit.
* **ACSD-50116** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème qui empêchait un utilisateur administrateur de créer une réécriture d’URL pour les sous-catégories de niveau 3 ou inférieur.
* **ACSD-49513** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.5) - Correction du problème d’échec de la synchronisation du stockage distant en raison de fichiers de 0 octet.
* **ACSD-46683** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel le prix de livraison affichait *Pas encore calculé*.
* **ACSD-49129** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6) - Correction du problème en raison duquel l’attribut *[!UICONTROL content]* (code image base64) n’est pas renvoyé dans les réponses de l’API de média de produit `rest/V1/products/sku/media`.
* **ACSD-50276** (pour Adobe Commerce >=2.4.0 &lt;2.4.7) - Correction du problème en raison duquel le formulaire d’enregistrement du client ne fonctionne pas sur le storefront si un attribut de client à sélection multiple est créé.
* **ACSD-50527** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction de l’erreur qui se produit lors de l’enregistrement d’une page avec un bloc dynamique vide.
* **ACSD-49973** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.5) - Améliore les performances de récupération des produits regroupés via GraphQL.
* **ACSD-5114** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème en raison duquel un produit aléatoire disparaissait des catalogues volumineux lorsque l’indexation asynchrone était activée. Améliore les performances de la réindexation asynchrone pour les catalogues volumineux.
* **B2B-2598** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Ajoutez la fonctionnalité de mise en cache aux requêtes GraphQL [!UICONTROL availableStores], [!UICONTROL countries], [!UICONTROL country], [!UICONTROL currency] et [!UICONTROL storeConfig].
* Ajout de nouvelles versions pour MDVA-42806, ACSD-48627, ACSD-46815.
* Mise à jour des métadonnées de correctifs pour ACSD-49773, ACSD-47179, ACSD-48300.

## v1.1.29 {#v1-1-29}

* **ACSD-49389** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction du problème qui entraînait l’envoi par l’API d’un courrier électronique prêt à l’emploi lorsque la commande n’était pas prête pour la récupération.
* **ACSD-49822** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel les mises à jour de la page [!UICONTROL Requisition List] ne sont pas répercutées sur [!UICONTROL Print Requisition List].
* **ACSD-48771** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème lié à la mise à niveau du type de contenu de bloc de colonne à partir d’anciennes versions [!DNL Page Builder].
* **ACSD-49464** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel les factures, les envois et les notes de crédit ne sont pas renvoyés de l’archive lorsque orderId est différent.
* **ACSD-49773** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6) - Correction du problème d’échec de l’exportation de produits lorsque AWS S3 est utilisé comme stockage distant.
* **ACSD-49748** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction du problème qui empêchait l’envoi des invitations.
* **ACSD-49502** (pour Adobe Commerce >=2.4.3 &lt;2.4.7) - Correction du problème en raison duquel le lien téléchargeable n’est pas correctement mis à jour après l’application d’une mise à jour intermédiaire au produit téléchargeable.
* **ACSD-49527** (pour Adobe Commerce >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel les rôles de l’entreprise GraphQL n’affichent pas correctement la pagination.
* **ACSD-49706** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème d’enregistrement de la valeur par défaut pour un attribut d’échantillon visuel lorsqu’aucune valeur n’est sélectionnée.
* **ACSD-49835** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel la valeur de la case à cocher Utiliser par défaut n’est pas enregistrée correctement au niveau du magasin pour un attribut à sélection multiple.
* **ACSD-49898** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème où la grille de produits renvoie une exception lorsqu’un produit regroupé a un prix spécial qui dépasse 1 000.
* **ACSD-50234** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.5) - Correction du problème avec un nom de client incorrect dans l’e-mail de confirmation lors du placement d’une commande avec [!DNL PayPal].
* **ACSD-49960** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel le filtrage par date ne fonctionne pas pour la grille de commande du client.
* **ACSD-49849** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.6) - Correction du problème en raison duquel le courrier électronique du client était remplacé par le message [!DNL PayPal] lors du placement d’une commande avec [!DNL PayPal Express] via GraphQL.
* **ACSD-49839** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel la structure et les tarifs du catalogue partagé généraient une erreur dans Admin lorsque les produits contenaient des guillemets simples ou doubles dans le SKU.
* **ACSD-49970** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction d’une gestion incorrecte des erreurs GraphQL lorsque la création de rapports [!DNL New Relic] est activée.
* **ACSD-50260** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel les résultats de la recherche de produits GraphQL étaient limités à 10 000 résultats uniquement.
* **ACSD-48813** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème en raison duquel la recherche n’affichait pas de résultats pertinents en fonction du poids de la recherche des attributs.

## v1.1.28 {#v1-1-28}

* **ACSD-48204** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.3) - Correction du problème en raison duquel une règle de prix de catalogue créée à partir de l’attribut Oui/Non ne prend pas en compte la portée sélectionnée.
* **ACSD-47704** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel le produit regroupé affichait le prix de dans les produits en stock uniquement.
* **ACSD-49370** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel l’attribut de produit *Date Time*} avait un type *FilterMatchTypeInput* dans le schéma GraphQL.
* **ACSD-48807** (pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.7) - Correction du problème en raison duquel les révisions des produits du client ne sont pas filtrées par l’aperçu de magasin via GraphQL.
* **ACSD-49433** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème en raison duquel le montant par défaut s’affichait comme sous-total dans le panier pour la carte-cadeau avec un montant ouvert.
* **ACSD-48866** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème qui se produit lorsqu’une erreur se produit lors de la demande de flux RSS pour les catégories.
* **ACSD-48784** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel les prix des segments de clients sont incorrectement mis en cache entre les groupes de clients.
* **ACSD-48857** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème qui empêchait un utilisateur d’enregistrer les modifications après les avoir modifiées avec Page Builder.
* **ACSD-49065** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel les éléments de guillemet ne sont pas visibles dans l’administrateur s’ils sont uniquement affectés au stock personnalisé.
* **ACSD-49179** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel le rapport Commandes affichait des montants incorrects en cas de devises différentes pour différents magasins.
* **ACSD-49286** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème en raison duquel un produit est ajouté deux fois à un panier lorsque plusieurs widgets de produit sont présents sur la page.
* **ACSD-49574** (pour Adobe Commerce >=2.4.4 &lt;2.4.7) - Ajoute une fonctionnalité pour prendre en charge les mises à jour de produit Carte cadeau dans un panier via GraphQL.
* Mise à jour du correctif : ACSD-48694.

## v1.1.27 {#v1-1-27}

* **ACSD-48362** (pour Adobe Commerce >=2.4.1 &lt;2.4.7) - Correction du problème en raison duquel l’adresse de livraison par défaut était utilisée à la place d’une nouvelle adresse lors du placement d’une commande à l’aide d’un guillemet négociable.
* **ACSD-48059** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel les commerçants ne pouvaient pas enregistrer &quot;[!UICONTROL Match product by rule]&quot; dans la catégorie.
* **ACSD-48216** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7) - Correction du problème d’augmentation de [!UICONTROL AUTO_INCREMENT] de la table [!UICONTROL inventory_source_item] sur l’opération [!UICONTROL UPDATE].
* **ACSD-47908** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7) : corrige l’erreur &quot;Une valeur inférieure ou égale à 0 est attendue&quot; lors de la sélection de la source et de la quantité à l’étape d’expédition lors du passage en caisse.
* **ACSD-49497** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.6) - Correction du problème lorsqu’une commande reste en état de traitement après l’expédition et qu’un remboursement partiel est appliqué.
* **ACSD-48694** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.1 &lt;2.4.7) - Correction du problème en raison duquel l’erreur &quot;Changement d’état non valide demandé&quot; empêchait un client de passer une commande.
* **ACSD-49013** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème en raison duquel la confirmation des emails n’est pas traduite dans les paramètres régionaux du site web lors de la création de clients à l’aide de l’API en bloc.
* **ACSD-48164** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème qui empêchait un administrateur restreint d’enregistrer une valeur au niveau du site web.
* **ACSD-48404** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.4) - Correction du problème où &quot;Mémoriser la pagination des catégories = Oui&quot; provoquait une erreur lors de l’activation du bouton Précédent du navigateur.
* **ACSD-48634** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction des erreurs JS sur une page de mise à jour intermédiaire lorsque &quot;[!UICONTROL Google Analytics Content Experiments]&quot; est activé.
* **ACSD-49042** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.5) - Correction du problème qui empêchait la commande d’un produit avec un ordre infini en arrière-plan à partir de Storefront.
* Mise à jour des correctifs : ACSD-48366, ACSD-48661.

## v1.1.26 {#v1-1-26}

* **ACSD-47937** (pour Adobe Commerce et Magento Open Source 2.4.4) || >=2.4.5 &lt;2.4.6) - Correction du problème en raison duquel les notifications de baisse de prix ne sont pas toujours envoyées en raison de la mise en cache au niveau de l’application.
* **ACSD-48661** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel, si la limite de crédit de l’entreprise est supérieure à 999, le séparateur de virgule empêche l’enregistrement de l’entreprise en raison d’une erreur de validation.
* **ACSD-48773** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel le modèle d’email des points de récompense provient d’un mauvais magasin.
* **ACSD-48587** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème qui empêchait l’affichage des produits correspondants des caractères spéciaux d’HTML dans les règles de correspondance du widget de produits.
* **ACSD-48212** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.6) - Correction du problème en raison duquel l’importation de produit attribue le produit à la mauvaise source.
* **ACSD-47988** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.6) - Correction du problème en raison duquel l’exportation de produits supprimait les balises d’HTML de la description du produit du créateur de pages.
* **ACSD-48366** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème en raison duquel l’image du produit ne s’affichait pas dans le modèle de courrier électronique Retour au stock.
* **ACSD-48417** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème d’apparition d’une erreur SQL après la création d’une modification de planification pour un produit et l’enregistrement d’un autre produit.

## v1.1.25 {#v1-1-25}

* **ACSD-48058** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction du problème en raison duquel la réindexation des prix du produit ne fonctionne pas si le produit du lot n’est affecté à aucun site web.
* **ACSD-48262** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction du problème en raison duquel les produits ne sont pas visibles sur l’interface lorsque le paramètre &quot;Autoriser tous les produits par page&quot; est défini sur Oui.
* **ACSD-48293** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4) - Correction du problème en raison duquel les produits composites étaient en rupture de stock lorsque les produits enfants qui avaient été vendus étaient revendus en stock.
* **ACSD-47520** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème où les clients perdent des points de récompense lorsqu’une note de crédit est créée.
* **ACSD-48044** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.4) - Correction du problème en raison duquel l’application de plusieurs cartes-cadeaux à une seule commande avec livraison multiple empêchait le placement des commandes.
* **ACSD-48300** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème où un retour ne peut pas être créé si le produit configurable est supprimé.
* **ACSD-47910** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème des commandes, factures, envois et notes de crédit manquants dans les grilles d’entités respectives.
* **ACSD-47292** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème en raison duquel les produits en rupture de stock ne sont pas disponibles dans la réponse GraphQL si la valeur &quot;Afficher les produits en rupture de stock&quot; est définie sur Oui.
* **ACSD-48234** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction du problème en raison duquel le résultat de la recherche catalogue affichait un nombre d’éléments de catégorie incorrect lorsque l’option &quot;Afficher en rupture de stock&quot; était activée.
* **ACSD-48313** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.5) - Correction du problème en raison duquel la colonne &quot;configurable_variations&quot; n’est pas analysée si la valeur de l’attribut contient une virgule. Le même algorithme d’analyse est utilisé pour &quot;additional_attributes&quot;.
* **ACSD-48627** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction du problème en raison duquel le produit configurable en rupture de stock provoquait une erreur lors de l’envoi d’une demande GraphQL pour obtenir les détails du panier.
* Mise à jour du correctif : MDVA-39384.

## v1.1.24 {#v1-1-24}

* **ACSD-45168** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6) - Correction du problème en raison duquel les URL compatibles avec l’optimisation pour les moteurs de recherche ne sont pas générées pour les produits dont les attributs *url_key* ont été remplacés au niveau de l’affichage de magasin.
* **ACSD-46865** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème en raison duquel la grille Expédition et Mémo de crédit n’est pas renseignée lorsque l’indexation asynchrone est activée.
* **ACSD-47004** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6) - Correction du problème où la TVA n’est pas appliquée à une adresse de facturation sans identifiant de TVA.
* **ACSD-47803** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème où les échantillons de produits configurables en rupture de stock s’affichent comme disponibles.
* **ACSD-47137** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Améliore la vitesse de chargement de la galerie d’images lorsque le dossier pub/média est très volumineux.
* **ACSD-46770** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème d’envoi des emails des commandes d’administration même lorsque la *confirmation de commande email* est décochée.
* **ACSD-47955** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème en raison duquel GraphQL n’affiche pas correctement la remise au panier.
* **ACSD-46617** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel le bouton *Continuer vers le passage en caisse* est grisé même si le sous-total est supérieur au *Montant minimum de la commande* configuré.
* **ACSD-47079** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.5) - Correction du problème en raison duquel l’état du stock des produits composites (regroupés, configurables) n’était pas mis à jour lorsque l’état du stock des sous-produits changeait via le POST API REST /rest/V1/inventory/source-items.
* **ACSD-47336** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correctifs *Un problème s’est produit.* erreur lors de l’affichage des notifications dans l’administrateur Commerce.
* **ACSD-47559** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel la zone Prévisualiser le modèle de courrier électronique n’est pas entièrement visible.
* **ACSD-47920** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel les commandes peuvent être placées via l’API REST en tant qu’utilisateur invité même lorsque l’option *Autoriser le passage en caisse* est désactivée.
* Correctifs remplacés : MDVA-39305, MDVA-42855.

## v1.1.23 {#v1-1-23}

* **ACSD-47179** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème qui empêchait un administrateur ayant un accès limité à une portée spécifique de supprimer des révisions de produit.
* **ACSD-47107** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.5) - Correction du problème en raison duquel la remise de la règle de prix du catalogue était appliquée aux options de produit personnalisées.
* **ACSD-47232** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème qui empêchait l’application des bons avec des conditions de poids total dans l’administrateur.
* **ACSD-46519** (pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.6) - Correction du problème en raison duquel la requête categoryList de GraphQL renvoie un product_count incorrect pour une catégorie d’ancrage.
* **ACSD-47027** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6) - Correction d’une demande GraphQL updateCompanyRole lente.
* **ACSD-4766** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel la fonction de filtre ne fonctionne pas dans la grille Admin > Système > Autorisations > Rôles utilisateur > un rôle > Utilisateurs de rôle .
* **ACSD-47497** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel l’onglet Services n’était pas visible dans la configuration sous l’administrateur.
* Mise à jour du correctif : ACSD-47743.
* Correctifs remplacés : MDVA-42807.

## v1.1.22 {#v1-1-22}

* **ACSD-4744** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.3) - Correction de l’erreur _Tentative d’accès au décalage de tableau sur la valeur de type bool_ lors de l’accès à certains chemins de catégorie non existants pour les produits connus sur PHP 7.4.
* **ACSD-47332** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème d’échec de cron avec une erreur qui n’est signalée que lors de l’exécution entre 00:00 et 00:59 UTC.
* **ACSD-47280** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel la désactivation de la fonctionnalité de catalogue partagé sur une plage spécifique ne fonctionne pas correctement.
* **ACSD-47106** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème qui empêchait l’enregistrement d’une valeur dans un nouvel attribut personnalisé sur la page de création d’une entreprise.
* Mise à jour du correctif : ACSD-45143.

## v1.1.21 {#v1-1-21}

* **ACSD-46809** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6) - Correction du problème où un utilisateur obtenait une erreur lors de l’attribution d’un grand nombre de sources de produits.
* **ACSD-46856** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Améliore les prix des niveaux de mise à jour des performances via Système > Configuration > Importer > Tarifs avancés.
* **ACSD-46541** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.4) - Correction du problème qui empêchait un utilisateur administrateur de créer une note de crédit si un article de commande était supprimé.
* **ACSD-46581** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel le total de la taxe estimé n’est pas mis à jour après la sélection d’un pays dans le panier.
* **ACSD-46618** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel le widget de liste de produits affichait des prix en cache incorrects pour un client connecté.
* **ACSD-46674** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel les options personnalisées d’un type d’image s’affichent comme HTML dans les courriers électroniques du client.
* **ACSD-46988** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème en raison duquel la requête d’API &quot;devise&quot; de GraphQL renvoyait des valeurs NULL pour une devise personnalisée.
* **ACSD-47076** (pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.5) - Correction du problème qui empêchait la lecture des vidéos Vimeo sur le storefront.
* **ACSD-45071** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4) - Correction du problème en raison duquel la source par défaut était ajoutée au produit lors de l’importation.
* **AC-3023** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Mettre à jour le schéma DHL vers la dernière version 10.0.
* Mise à jour des correctifs : MDVA-42584.
* Correctifs remplacés : MDVA-36572, ACSD-45241.

## v1.1.20 {#v1-1-20}

* **ACSD-46520** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.5*) - Correction du problème en raison duquel un utilisateur obtient un état de commande incorrect lorsqu’il est remboursé à l’aide du crédit de magasin.
* **ACSD-46703** (*pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6*) - Correction du problème qui empêchait de faire glisser des options personnalisées sur une page de modification de produit.
* **ACSD-44851** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6*) - Correction du problème qui empêchait l’ouverture ou le développement d’une catégorie avec des sous-catégories.
* **ACSD-46815** (*pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6*) - Correction du problème en raison duquel la requête d’arborescence de catégories était limitée à 20 catégories.
* **ACSD-45675** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6*) - Correction du problème en raison duquel l’exportation de produits utilisait des noms de catégorie de la portée *Vue de magasin par défaut*.
* **ACSD-46869** (*pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6*) - Correction du problème en raison duquel un produit configurable dans un panier n’était pas mis à jour via une requête *API REST PUT* sans modifier la quantité du produit.
* **MDVA-42768-V2** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.3*) - Correction du problème en raison duquel le prix normal du produit configurable était *0* lorsque l’option *Afficher en rupture de stock* était *Oui*}.
* Mise à jour des correctifs : MDVA-44562, ACSD-46213, MDVA-41305, MDVA-38346, MDVA-13203.
* Correctif obsolète : MDVA-42768.

## v1.1.19 {#v1-1-19}

* **ACSD-46213** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.3*) - Correction du problème en raison duquel la requête d’arborescence de catégories était limitée à 20 catégories.
* **ACSD-45781** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.2*) - Correction du problème en raison duquel le champ de recherche frontale du magasin n’était pas affiché sur mobile.
* **ACSD-46192** (*pour Adobe Commerce et Magento Open Source >=2.3.6 &lt;2.4.5*) - Correction du problème lié à l’utilisation du point de terminaison `async/bulk/V1/configurable-products/bySku/options`.
* **ACSD-46404** (*pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.5*) - Correction du problème qui empêchait un utilisateur administrateur de se connecter après la mise à niveau vers la version 2.4.4.
* Mise à jour des correctifs : MDVA-41305, MDVA-38626, MDVA-38728, MDVA-41061-V4, MDVA-42269, MDVA-39305.

## v1.1.18 {#v1-1-18}

* **ACSD-45817** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Correction du problème en raison duquel une mutation de produit GraphQL pour un magasin spécifique renvoie toutes les variantes configurables, y compris celles qui ne sont pas affectées au magasin demandé.
* **ACSD-46146** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.6*) - Correction du problème d’envoi de deux emails de confirmation de commande après avoir passé une commande de l’administrateur.
* **ACSD-45255** (*pour Adobe Commerce >=2.4.3 &lt;2.4.6*) - Correction d’une exception sur la page Rapport Faible Stock pour un utilisateur administrateur restreint.
* **ACSD-45488** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6*) - Correction du problème en raison duquel un produit configurable avec plusieurs sources n’est pas automatiquement renvoyé à En stock.
* **ACSD-45754** (*pour Adobe Commerce et Magento Open Source >=2.3.1 &lt;2.4.6*) - Correction du problème en raison duquel les points de récompense ne sont pas ajoutés après l’application d’un coupon au panier.
* **ACSD-45849** (*pour Adobe Commerce >=2.4.3 &lt;2.4.4*) - Correction du problème de perte des métadonnées vidéo après l’application d’une mise à jour intermédiaire.
* **ACSD-45257** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;2.4.4*) - Correction du problème en raison duquel GraphQL n’affiche pas correctement une remise de panier.
* **ACSD-44938** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.4*) - Correction du problème en raison duquel `VAT_ID` ne peut pas être appliqué dans une requête GraphQL pour un utilisateur invité.
* Mise à jour des correctifs : MDVA-43417.

## v1.1.17 {#v1-1-17}

* **ACSD-45241** (*pour Adobe Commerce et Magento Open Source >=2.3.5 &lt;2.4.4*) - Correction du problème de calcul erroné de la quantité de stock d’un produit virtuel après la création d’une note de crédit.
* **ACSD-43887** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.5*) - Correction du problème en raison duquel des détails incorrects s’affichaient sur la page de paiement du passage en caisse lorsque les commandes pour les entreprises étaient activées.
* **ACSD-45143** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.5*) - Correction du problème en raison duquel la mutation `setShippingAddressesOnCart` ne permet pas de définir le code de région numérique sur *région*.
* **ACSD-44591** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.6*) - Correction de l’erreur qui se produit lorsqu’une commande est passée sans confirmation CAPTCHA.
* **ACSD-45520** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.6*) - Correction du problème en raison duquel les options d’échantillon ne sont pas présélectionnées sur la page des détails du produit lorsqu’un utilisateur modifie des produits configurables à partir du panier.
* **ACSD-45169** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.6*) - Correction du problème en raison duquel [!DNL Visual Merchandiser] n’affiche pas le stock et le prix corrects d’un produit configurable après l’application d’une mise à jour intermédiaire.
* **ACSD-45424** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;2.4.6*) - Correction du problème de création d’une compensation de réservation incorrecte après un remboursement partiel (note de crédit).
* **MDVA-42807** (*pour Adobe Commerce et Magento Open Source >=2.3.1 &lt;2.4.6*) - Correction du problème en raison duquel le symbole de devise personnalisé ne s’affichait pas sur le devant de la boutique.
* Mise à jour des correctifs : MDVA-42689, AC-3022.

## v1.1.16 {#v1-1-16}

* **MDVA-44703** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4*) - Correction du problème en raison duquel les totaux des commandes dans le rapport Commandes sont mal calculés pour l’utilisateur administrateur restreint.
* **MDVA-44940** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4*) - Correction de l’erreur SQL qui se produit lors de l’enregistrement de la catégorie depuis l’administrateur.
* **MDVA-44562** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.2-p2*) - Correction du problème en raison duquel l’ID de magasin autre que l’ID de guillemet par défaut est remplacé par l’ID de magasin par défaut, en dépit de la demande GraphQL provenant de la vue de magasin autre que celle par défaut.
* **MDVA-43167** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Correction du problème en raison duquel l’action en masse de la grille de commande d’administrateur ne s’applique pas pour les pages multiples lorsque l’utilisateur administrateur sélectionne toutes les commandes.
* **MDVA-44044** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.2-p2*) - Correction du problème en raison duquel un produit ne s’affiche pas sur la page de catégorie après avoir été affecté à un nouveau site web.
* **MDVA-42509** (*pour Adobe Commerce et Magento Open Source >=2.3.3 &lt;2.4.4*) - Correction du problème qui empêchait le téléchargement d’un fichier CSV pour un ordre rapide, ce qui entraînait une erreur *Impossible d’envoyer le cookie*.
* Mise à jour des correctifs : MDVA-41061, MDVA-42584.
* Le préfixe des nouveaux [!DNL Quality Patches Tool] correctifs sera remplacé de *MDVA* par *ACSD* en raison de changements de processus interne.

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4*) - Correction du problème en raison duquel un article supplémentaire ne peut pas être ajouté au panier alors que la quantité minimale de l’article est déjà dans le panier.
* **MDVA-44887** (*pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.5*) - Correction de l’erreur *Uncaught SyntaxError: Uncaught token ’const’* dans le panneau d’administration.
* **MDVA-43718** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correctifs *Le consommateur n’est pas autorisé à accéder à %resources.* erreur qui s’affiche lors de l’accès à un catalogue partagé à partir d’une intégration personnalisée.
* **MDVA-44660** (*pour Adobe Commerce et Magento Open Source >=2.4.2-p1 &lt;2.4.5*) - Correction du problème en raison duquel le caractère d’accent grave ``` ` ``` ne pouvait pas être utilisé pour le prénom et le nom d’un client.
* **MDVA-40896** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4*) - Correction de l’erreur *Error: TypeError: Argument 3 transmis à Magento* dans l’API asynchrone product en bloc.
* **MDVA-38559** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.3*) - Correction de l’erreur */V1/customers/search API* pour les clients ayant plusieurs abonnements.
* **MDVA-44533** (*pour Adobe Commerce et Magento Open Source >=2.3.1 &lt;2.4.4*) - Correction du problème en raison duquel la remise est incorrectement appliquée à un produit enfant groupé.
* Mise à jour des correctifs : MDVA-41061, MDVA-42269.

## v1.1.14 {#v1-1-14}

* **MDVA-43983** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.5*) - Correction du problème en raison duquel les produits *Non visibles individuellement* apparaissent toujours dans les résultats de recherche avancée du catalogue.
* **MDVA-44100** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.5*) - Correction du problème en raison duquel tous les FPT sont affectés au dernier produit dans le panier et réinitialisés pour d’autres produits.
* **MDVA-43605** (*pour Adobe Commerce et Magento Open Source >=2.3.1 &lt;2.4.5*) - Correction du problème en raison duquel les données de commande renvoyaient des valeurs négatives pour les totaux de lignes lors de l’utilisation de l’API REST.
* **MDVA-43102** (*pour Adobe Commerce et Magento Open Source >=2.3.1 &lt;2.4.5*) - Correction du problème en raison duquel la quantité vendable n’est pas correctement mise à jour lorsqu’un remboursement est effectué via l’API REST.
* **MDVA-43178** (*pour Adobe Commerce et Magento Open Source >=2.4.3-p2 &lt;2.4.5*) - Correction du problème qui empêchait la récupération d’un jeton client pour un magasin personnalisé dans GraphQL.
* **MDVA-43859** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.5*) - Correction du problème en raison duquel l’erreur *Aucune entité avec customerId =* n’est consignée lorsqu’un client supprimé tente de se connecter.
* **MDVA-44147** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.5*) - Correction du problème en raison duquel une requête GraphQL ne renvoyait pas de listes de demandes d’acquisition.
* **MDVA-44505** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.3*) - Correction des problèmes en raison desquels l’application de points de récompense à GraphQL ne met pas à jour le total général et où le crédit de magasin est appliqué plusieurs fois lors de l’emplacement de la commande.
* Mise à jour des correctifs : MDVA-29148, MDVA-36464-V5, MDVA-42584, MDVA-39993-V2.

## v1.1.13 {#v1-1-13}

* **MDVA-42969** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.3*) - Correction du problème en raison duquel la règle de produit associée ne fonctionne que lorsque le segment client est défini sur *Tous*.
* **MDVA-39605** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;2.4.5*) - Correction du problème en raison duquel Redis cache TTL (date d’expiration) a une valeur incorrecte.
* **MDVA-43862** (*pour Adobe Commerce et Magento Open Source >=2.3.3 &lt;2.4.5*) - Correction du problème en raison duquel le client ne peut pas mettre à jour les éléments de panier en raison d’une erreur GraphQL *UpdateCartItems mutation*.
* **MDVA-43824** (*pour Adobe Commerce et Magento Open Source >=2.3.6 &lt;=2.3.7-p3) || >=2.4.1 &lt;2.4.5*) - Correction du problème d’apparition d’une erreur lors de l’annulation de commandes avec une remise.
* **MDVA-43451** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.5*) - Correction du problème en raison duquel l’erreur *Le magasin demandé était introuvable. Vérifiez le magasin, puis réessayez.* s’affiche lors de la configuration d’un catalogue partagé pour un site web spécifique.
* **MDVA-43491** (*pour Adobe Commerce et Magento Open Source >=2.3.5 &lt;2.4.5*) - Correction du problème en raison duquel l’étiquette de l’image de base n’était pas mise à jour lors de l’importation de produits pour un site web multi-magasin.
* **MDVA-43601** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction du problème lié aux déclencheurs manquants après la réindexation complète.
* **MDVA-42046** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;=2.3.5-p2) || >=2.4.0 &lt;2.4.5*) - Correction du problème d’attribution d’une valeur incorrecte à un attribut de produit avec un champ de saisie de date lors de la mise à jour d’un produit.
* **MDVA-43935** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.5*) - Correction du problème en raison duquel le produit Upsell s’affichait deux fois.
* **MDVA-44188** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.5*) - Correction du problème en raison duquel les emails émis par le système avec `.-` dans les adresses ne sont pas envoyés.
* **MDVA-42283** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction du problème en raison duquel le format de date-heure dans la grille d’ordre d’administration des paramètres régionaux français n’est pas valide.
* Mise à jour des correctifs : MDVA-41061-V2, MDVA-36309, MDVA-30862, MDVA-39713.
* Ajout de métadonnées de correctifs pour le [!DNL Site-Wide Analysis Tool].

## v1.1.12 {#v1-1-12}

* **MDVA-39713** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.3.6*) - Correction du problème en raison duquel l’utilisateur peut modifier l’heure de début d’une mise à jour planifiée active.
* **MDVA-42410** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction du problème en raison duquel les rapports de coupon n’affichaient que la devise de base par défaut.
* **MDVA-41136** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction du problème en raison duquel la date d’expiration de `mage-cache-sessid` n’est pas étendue, ce qui entraîne un nettoyage des données client.
* **MDVA-3993** (*pour Adobe Commerce et Magento Open Source >=2.3.5 &lt;=2.3.7-p2) || >=2.4.0 &lt;2.4.4*) - Correction du problème en raison duquel les modifications d’inventaire effectuées par le biais de l’API ne se répercutent pas sur la page du produit sur le front-end.
* **MDVA-42855** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.5*) - Correction du problème en raison duquel une nouvelle adresse du client n’est pas enregistrée dans le carnet d’adresses lors de l’extraction.
* **MDVA-42645** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.5*) - Correction du problème en raison duquel l’administrateur ne pouvait pas rembourser les points si la fonctionnalité de crédit de magasin était désactivée.
* **MDVA-43414** (*pour Adobe Commerce et Magento Open Source >=2.3.6 &lt;=2.3.7-p2*) - Correction de l’erreur fatale PHP qui se produit lors de l’exécution du consommateur de file d’attente `inventory.reservations.updateSalabilityStatus` sur des SKU numériques.
* **MDVA-41628** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.5*) - Correction du problème en raison duquel les utilisateurs administrateurs limités existants avaient accès aux nouvelles ressources lors de l’ajout de nouveaux modules.
* **MDVA-43348** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.5*) - Correction du problème en raison duquel la demande de carte-cadeau GraphQL affichait une erreur si `gift_card_options` contenait *uid*.
* **MDVA-39546** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction du problème en raison duquel la date de début de la mise à jour de l’évaluation pouvait être définie sur une date antérieure à la date actuelle lors de la modification.
* **MDVA-42950** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction du problème de lecture des vidéos sur la page du produit.
* **MDVA-42689** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction du problème où Adobe Commerce renvoie une erreur *Violation de contrainte d’intégrité* lors de la mise à jour des catégories de produits lors de l’importation.
* **MDVA-41229** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction du problème en raison duquel les images disponibles sur le serveur principal ne s’affichent pas sur le serveur frontal après l’importation de produits configurables.
* **MDVA-43731** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4*) - Correction du problème en raison duquel les *Synonymes de recherche* ne fonctionnent plus lorsque la valeur est ajoutée dans *Termes minimum à correspondre*.
* **MDVA-43232** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;2.4.5*) - Correction du problème en raison duquel le tri des produits dans [!DNL Visual Merchandiser] par un prix spécial au bas/haut provoque une erreur lors de l’enregistrement de la catégorie.
* **MDVA-43726** (*pour Adobe Commerce et Magento Open Source >=2.3.3 &lt;2.4.3*) - Correction du problème en raison duquel la règle de prix du catalogue basée sur la correspondance des attributs de niveau magasin ne s’appliquait pas après la réindexation partielle.
* Mise à jour des correctifs : MDVA-36464, MDVA-37478, MDVA-38608.
* Ajout de métadonnées de correctifs pour le [!DNL Site-Wide Analysis Tool].

## v1.1.11 {#v1-1-11}

* **MDVA-42790** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.5*) - Correction du problème en raison duquel les attributs de prix du produit ne peuvent pas être mis à jour pour un site web spécifique via l’API REST.
* **MDVA-41350** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction du problème qui renvoie une exception lorsqu’un utilisateur administrateur avec accès restreint ajoute un produit en dehors de sa portée par SKU dans une commande.
* **MDVA-42269** (*pour Adobe Commerce et Magento Open Source >=2.4.3-p1 &lt;2.4.5*) - Correction du problème en raison duquel un utilisateur administrateur ne pouvait pas se connecter à l’administrateur en raison de l’erreur *TypeError: strtotime() s’attendait à ce que le paramètre 1 soit une chaîne, null en raison d’erreur*.
* **MDVA-40830** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction du problème en raison duquel le crédit de magasin est appliqué plusieurs fois lors du placement de la commande.
* **MDVA-42237** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.5*) - Correction du problème en raison duquel un prix spécial de produit configurable n’était pas mis à jour après modification du prix de son sous-produit.
* **MDVA-42520** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4*) - Correction du problème où le taux de taxe est appliqué deux fois si *Activer le commerce transfrontalier* est utilisé.
* Mise à jour des correctifs : MDVA-27239, MDVA-39305, MDVA-41236, MDVA-36832.
* Correctif obsolète : MDVA-37725.

## v1.1.10 {#v1-1-10}

* **MDVA-38728** (*pour Adobe Commerce et Magento Open Source >=2.3.2 &lt;2.4.5*) - Correction du problème en raison duquel la mise à jour des attributs de masse crée une réécriture des URL pour le magasin par défaut uniquement après avoir modifié la *visibilité du produit*.
* **MDVA-43091** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4*) - Correction du problème en raison duquel la commande d’un produit en bundle auprès de l’administrateur dans le serveur principal générait l’erreur *Vous ne pouvez pas utiliser de quantité décimale pour ce produit*.
* **MDVA-40816** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction du problème en raison duquel les règles de produit associées affichent des produits de catégories non définies dans les conditions de règle.
* **MDVA-41305** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.5*) - Correction du problème en raison duquel la mutation GraphQL ne renvoie pas d’options de produit configurables après l’avoir ajouté à la liste des souhaits.
* **MDVA-39181** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.5*) - Correction du problème en raison duquel les règles de produit associées affichent des produits de catégories non définies dans les conditions de règle.
* **MDVA-42584** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.3*) - Correction du problème en raison duquel l’état du stock configurable dans le serveur principal n’est pas mis à jour après la modification de l’état du stock et de la quantité via l’importation ou l’API.
* **MDVA-40175** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.3*) - Correction du problème en raison duquel *Cliquer pour modifier la méthode d’expédition* n’affichait pas de boutons radio pour sélectionner les méthodes d’expédition dans l’administrateur lors du réorganisation.
* **MDVA-42768** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;2.4.5*) - Correction du problème en raison duquel le produit configurable affiche un prix normal de 0 lorsque la valeur de *Display Out-of-Stock* est Oui.
* **MDVA-43201** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Correction du problème d’erreur lors de la connexion du client lors de l’utilisation de l’attribut DOB avec certains paramètres régionaux.
* Mise à jour des correctifs : MDVA-35092, MDVA-33970.

## v1.1.9 {#v1-1-9}

* **MDVA-38346** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction du problème en raison duquel les filtres de dates ne fonctionnent pas correctement lorsque le fuseau horaire Adobe Commerce est différent du fuseau horaire de l’environnement local.
* **MDVA-42657** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.5*) - Correction du problème qui empêchait l’utilisateur administrateur de sélectionner des catégories dans les conditions de segment du client.
* **MDVA-42806** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Correction du problème d’envoi d’un *nouvel enregistrement de société* par e-mail chaque fois qu’une société existante est mise à jour via l’API REST.
* **MDVA-37984** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.5*) - Correction du problème en raison duquel la fonctionnalité [!DNL Visual Merchandiser] *Faire correspondre le produit par règle* ne filtre pas correctement les produits avec des mises à jour intermédiaires.
* **MDVA-40488** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Correction du problème en raison duquel les produits configurables avec des produits enfants en rupture de stock ne s’affichaient pas dans la plage de prix correcte.
* **MDVA-42507** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.5*) - Correction du problème de nettoyage du cache de la page entière après l’application de la mise à jour intermédiaire pour la règle de panier.
* **MDVA-39163** (*pour Adobe Commerce et Magento Open Source >=2.3.5 &lt;2.4.5*) - Correction du problème en raison duquel les méthodes d’expédition ne sont pas disponibles lorsqu’un nouvel utilisateur est enregistré et que les produits du panier proviennent de la session d’invité.
* **MDVA-38626** (*pour Adobe Commerce et Magento Open Source >=2.3.3 &lt;2.4.5*) - Correction du problème en raison duquel l’utilisateur administrateur ne peut pas passer de commande sur le serveur principal à l’aide du paiement [!DNL PayPal Payflow Pro].
* **MDVA-38666** (*pour Adobe Commerce et Magento Open Source >=2.3.2 &lt;2.3.6*) - Correction du problème en raison duquel l’utilisateur administrateur ne peut pas modifier les options de produit configurables dans le panier du client.
* **MDVA-38526** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.4*) - Correction du problème qui empêchait l’utilisateur administrateur d’accéder à [!DNL Site-Wide Analysis tool].
* Mise à jour des correctifs : MDVA-40101.

## v1.1.8 {#v1-1-8}

* **MDVA-41215** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction du problème en raison duquel les utilisateurs obtenaient l’erreur 500 après avoir défini le cookie *mage-messages* s’il existe déjà, mais qu’il n’existe aucun nouveau message.
* **MDVA-41139** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4*) - Correction du problème en raison duquel les produits configurables deviennent hors stock après l’importation du produit lorsqu’un produit simple est qty=0 pour l’une de ses sources.
* **MDVA-42326** (*pour Adobe Commerce et Magento Open Source >=2.3.6 &lt;=2.3.7-p2) || >=2.4.1 &lt;2.4.4*) - Correction du problème qui entraînait l’affichage d’une erreur lors du passage en caisse après un délai d’expiration de session, même si le panier persistant était activé.
* **MDVA-42341** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Correction du problème en raison duquel la requête GraphQL `categoryList` ne filtre pas les résultats si une requête contient l’en-tête Magasin.
* **MDVA-38393** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction du problème en raison duquel les règles du catalogue ne fonctionnent plus pour un produit configurable si son produit simple est renommé.
* **MDVA-39153** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Correction du problème en raison duquel un montant de remise n’est pas correctement calculé lors d’une réorganisation dans l’administrateur.
* Mise à jour des correctifs : MDVA-28993, MDVA-41061, MDVA-35984.

## v1.1.7 {#v1-1-7}

* **MDVA-39711** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.3*) - Correction du problème en raison duquel les utilisateurs administrateurs ne pouvaient pas accéder à la grille du client après avoir supprimé le site web.
* **MDVA-40311** (*pour Adobe Commerce et Magento Open Source >=2.4.2-p2 &lt;2.4.4*) - Correction du problème en raison duquel les utilisateurs administrateurs recevaient le message d’erreur *Sécurité non valide ou clé de formulaire. Actualisez la page* après la connexion à l’administrateur si le chemin d’accès d’administrateur personnalisé est configuré et si la clé secrète est activée.
* **MDVA-41631** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.4*) - Correction du problème en raison duquel les utilisateurs obtenaient une erreur lorsqu’ils tentaient de récupérer des informations de commande sans valeur facultative *telephone* via GraphQL.
* **MDVA-27239** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.3.6*) - Correction du problème d’affichage des produits de vente croisée.
* Mise à jour des correctifs : MDVA-37068, MDVA-35254, MDVA-41164, MDVA-37916, MDVA-37478, MDVA-34551, MDVA-317799 .

## v1.1.6 {#v1-1-6}

* **MDVA-40550** (*pour Adobe Commerce et Magento Open Source >=2.3.5 &lt;2.4.4*) - Correction du problème lié aux produits manquants sur le front-end lors de la réindexation.
* **MDVA-40120** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.4*) - Correction du problème en raison duquel le tri GraphQL par DESC/ASC ne fonctionne pas avec des produits ayant la même pertinence ou le même prix.
* **MDVA-41399** (*pour Adobe Commerce et Magento Open Source >=2.3.3 &lt;2.4.2*) - Correction du problème en raison duquel les utilisateurs administrateurs ne peuvent pas accéder à la page *Gérer le panier d’achat* si un client ajoute un produit à la liste de souhaits.
* **MDVA-40609** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.3*) - Correction du problème en raison duquel les données de produits désactivés étaient absentes dans la table d’index `cataloginventory_stock_status`, affichant des quantités de produits désactivées incorrectes.
* **MDVA-39031** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.4*) - Correction du problème en raison duquel l’ajout d’un produit au panier via GraphQL est possible même s’il n’est pas affecté au site web cible.
* **MDVA-41597** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Correction du problème qui entraînait une erreur des utilisateurs lors de l’ajout de plusieurs produits configurables au panier à l’aide de GraphQL.
* **MDVA-27456** (*pour Adobe Commerce et Magento Open Source >=2.3.5 &lt;2.3.7*) - Correction du problème qui entraînait une erreur des utilisateurs lorsqu’ils tentaient de charger [!DNL Swagger].
* **MDVA-32776** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.2*) - Correction du problème en raison duquel l’état du stock n’est pas mis à jour lorsqu’une commande est passée mais pas expédiée.
* **MDVA-30862** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;2.4.0*) - Correction du problème lié à une date de commande incorrecte sur la facture de PDF imprimée.
* Amélioration de la page d’index pour le [!DNL Quality Patch Tool]. Ajout d’une recherche et d’un filtrage pratiques pour [!DNL quality patches] à la dernière version de l’outil.
* Mise à jour des correctifs : MDVA-33382, MDVA-39482.

## v1.1.5 {#v1-1-5}

* **MDVA-41236** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction du problème qui empêche la création ou la modification d’une mise à jour planifiée existante pour un produit si la Date de fin a été supprimée précédemment.
* **MDVA-41046** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction du problème en raison duquel des produits simples avec des options personnalisées sont disponibles pour l’affectation à des produits configurables/regroupés.
* **MDVA-40545** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction du problème en raison duquel seul le premier noeud d’une page était récupéré même s’il existait plusieurs noeuds pour la même page.
* **MDVA-41164** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.3-p1*) - Correction du problème qui empêchait un utilisateur administrateur d’enregistrer ou de modifier une société avec un attribut client personnalisé de type fichier ou image.
* **MDVA-39229** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction du problème qui entraîne l’affichage de l’erreur suivante après la mise à jour de l’heure de début de mise à jour de la règle de catalogue : *Cron Job staging_synchronize_entities_period a une erreur : la mise à jour active ne peut pas être supprimée*.
* **MDVA-40619** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction du problème en raison duquel les modifications apportées à la hiérarchie des pages CMS provoquaient une erreur 500 lors de la tentative de modification en ligne sur une page CMS.
* **MDVA-41061** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.3*) - Correction du problème en raison duquel l’état du stock était réinitialisé sur vendable lorsqu’un produit est enregistré depuis l’administrateur.
* **MDVA-31763** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction du problème en raison duquel les règles de prix du catalogue sont restaurées (ou non appliquées) jusqu’à la réindexation manuelle.
* **MDVA-37748** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.3*) - Correction du problème en raison duquel une requête GraphQL renvoyait des produits non attribués à un catalogue partagé.

## v1.1.4 {#v1-1-4}

* **MDVA-40399** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Correction du problème en raison duquel les factures partielles pour la même commande ne peuvent pas être créées simultanément via l’API REST.
* **MDVA-40101** (*pour Adobe Commerce et Magento Open Source >=2.3.2 &lt;2.4.0*) - Correction du problème en raison duquel les articles ne sont pas supprimés du mini panier après un placement de commande réussi à l’aide de [!DNL PayPal Express] Checkout (Passage en caisse).
* **MDVA-40401** (*pour Adobe Commerce et Magento Open Source >=2.3.6 &lt;=2.3.7-p2) || >=2.4.1 &lt;2.4.4*) - Correction du problème en raison duquel la valeur d’utilisation des coupons changeait même si le placement d’une commande échouait.
* **MDVA-40537** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;=2.4.0-p1*) - Correction du problème en raison duquel les utilisateurs obtenaient une erreur lors de la création d’une vue de magasin s’il existait plusieurs pages CMS avec la même clé d’URL.
* **MDVA-37725** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;=2.4.3-p1*) - Correction du problème en raison duquel les courriers électroniques de commande asynchrones envoyés à partir de sites web non par défaut contenaient des URL de logo du site web par défaut.
* **MDVA-39482** (*pour Adobe Commerce et Magento Open Source >=2.3.6 &lt;=2.3.7-p2) || >=2.4.1 &lt;2.4.4*) - Correction du problème d’épuisement d’un produit importé avec une quantité &quot;0&quot; lorsque les commandes en arrière-plan sont activées.
* **MDVA-40435** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;2.4.4*) - Correction du problème d’une remise incorrecte sur les produits de lot avec des prix dynamiques lorsqu’ils sont appliqués via GraphQL.
* **MC-42528** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;=2.4.3-p1*) - Correction du problème en raison duquel la requête GraphQL `categoryList` renvoie les catégories affectées et non affectées.
* **MDVA-29400** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;=2.3.7-p1) || >=2.4.0 &lt;=2.4.0-p1*) - Correction du problème lié aux commandes dupliquées placées avec [!DNL PayPal Express Checkout].
* **MDVA-26005** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;=2.3.5-p2*) - Correction du problème qui empêche de sélectionner une catégorie dans une arborescence de catégories pour les conditions des règles de prix du panier.
* **MDVA-25631** (*pour Adobe Commerce et Magento Open Source >=2.3.3 &lt;=2.3.5-p2*) - Améliore les performances de modification et d’enregistrement des segments de clients qui contiennent un grand nombre de clients.

## v1.1.3 {#v1-1-3}

* **MDVA-40262** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Correction du problème en raison duquel les requêtes de recherche GraphQL ne s’affichaient pas dans les termes de recherche courants dans l’administrateur.
* **MDVA-40601** (*pour Adobe Commerce et Magento Open Source >=2.3.1 &lt;=2.4.2-p2*) - Correction du problème qui entraînait une erreur des utilisateurs lorsqu’ils tentaient d’obtenir des informations sur la catégorie modifiée par une mise à jour planifiée via GraphQL.
* **MDVA-37234** (*pour Adobe Commerce et Magento Open Source >=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*) - Correction du problème en raison duquel l’ajout d’un élément au panier plusieurs fois (requête parallèle) pour le même SKU créait une ligne en double pour le même ID de panier.
* **MDVA-33606** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;=2.4.2-p2*) - Correction du problème en raison duquel les utilisateurs obtenaient une erreur *Violation de contrainte unique* lors de l’enregistrement d’une page CMS affectée à une hiérarchie.
* **MDVA-31590** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;=2.4.1-p1*) - Correction du problème en raison duquel les utilisateurs ne peuvent pas mettre à jour les attributs en masse à l’aide des files d’attente asynchrones MySQL.
* **MDVA-36309** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Correction du problème de lenteur de la recherche de produits par attributs dans les grilles d’administration.

## v1.1.2 {#v1-1-2}

* **MDVA-38929** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction du problème en raison duquel la facture avec FPT affichait un total général incorrect lorsque la commande était payée à partir du crédit de la boutique.
* **MDVA-37364** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;=2.4.3*) - Correction du problème en raison duquel l’attribut client personnalisé de type date rompt l’interface utilisateur de grille du client.
* **MDVA-39195** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Correction du problème en raison duquel le bouton *Ajouter au panier* était inactif sur la page de catégorie lors de la redirection vers le panier activée.
* **MDVA-37115** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Correction du problème qui entraînait l’affichage d’un avis inutile de *Il ne reste que 0} sur la page du produit configurable.*
* **MDVA-39521** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.4*) - Correction du problème en raison duquel l’utilisateur ne peut pas définir d’adresses de livraison sur le panier avec un numéro de téléphone vide via GraphQL.
* **MDVA-39384** (*pour Adobe Commerce et Magento Open Source >=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*) - Correction du problème en raison duquel l’attribut client personnalisé pour un utilisateur de la société n’était pas enregistré.
* **MDVA-39043** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;=2.4.3*) - Correction du problème en raison duquel l’utilisateur administrateur avec accès limité obtient une erreur lorsqu’il tente d’ajouter le widget *Products* à la page CMS.
* **MDVA-39966** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;=2.3.5-p2) || >=2.4.0 &lt;=2.4.0-p1*) - Correction du problème lié au déploiement de paramètres régionaux incorrects.
* **MDVA-38852** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;=2.3.5-p2*) - Correction du problème en raison duquel l’inventaire des catalogues par conception verrouille les tables pour les mises à jour qui diminuent considérablement les performances dans les cas de plusieurs commandes parallèles.
* **MDVA-39986** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.3*) - Correction du problème qui empêchait l’utilisateur de passer une commande dans Admin on MacOS à l’aide du navigateur Safari.
* **MDVA-38447** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Correction de deux problèmes : où les produits enfants configurables *Non visibles individuellement* sont renvoyés dans la réponse GraphQL et optimisent la requête MySQL pour les produits GraphQL avec filtre de catégorie.
* **MDVA-40134** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.3*) - Correction du problème en raison duquel GraphQL ne renvoie pas de produits associés lorsque le catalogue partagé est activé.
* **MDVA-39935** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.4*) - Correction du problème en raison duquel GraphQL renvoie des produits enfants configurables désactivés au niveau du site web.

## v1.1.1 {#v1-1-1}

* **MDVA-36021** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.4*) - Correction du problème en raison duquel l’erreur *Appel à une fonction membre getId()* s’affichait sur la page des détails de la commande dans l’administrateur.
* **MDVA-34948** (*pour Adobe Commerce et Magento Open Source >=2.3.6 &lt;=2.3.6-p1) || >=2.4.0 &lt;=2.4.0-p1*) - Correction du problème lié aux requêtes longues, telles que `GET_LOCK`.
* **MDVA-39305** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;=2.4.2-p1*) - Correction du problème en raison duquel les clients enregistrés ne pouvaient pas se connecter avec Google ReCaptcha activé.
* **MDVA-37897** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction du problème d’une redirection incorrecte lorsqu’un client tente d’ajouter des produits avec des options du widget Récemment consultés.

## v1.1.0 {#v1-1-0}

* Des catégories de correctifs ont été introduites afin d’améliorer l’expérience utilisateur et de faciliter la recherche des correctifs requis pour les clients.
* Le fichier `patches.json` a été renommé `support-patches.json`.
* **MDVA-38799** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Correction du problème en raison duquel les produits téléchargeables n’étaient pas enregistrés après la création d’une mise à jour intermédiaire.
* **MDVA-37592** (*pour Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - Correction du problème lorsque le tri par prix ne fonctionne pas correctement pour les produits dont le prix zéro est affecté au catalogue partagé.
* **MDVA-38827** (*pour Adobe Commerce >=2.3.3-p1 &lt;2.4.4*) - Correction du problème en raison duquel les clients reçoivent un courrier électronique d’expédition de commande contenant un message d’erreur.

## v1.0.26 {#v1-0-26}

* **MDVA-38468** (*pour Adobe Commerce >=2.3.2 &lt;=2.3.5-p2*) - Correction de l’erreur lors de l’enregistrement des pages CMS : *L’élément avec le même ID PAGE_ID existe déjà*.
* **MDVA-34680** (*pour Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;2.4.3*) - Correction du problème en raison duquel l’heure de création du compte client n’était pas correctement filtrée dans la grille des clients.
* **MDVA-37068** (*pour Adobe Commerce >=2.3.1 &lt;2.4.4*) - Correction du problème en raison duquel le taux d’imposition incorrect s’affiche lorsque le panier ne contient que des produits virtuels.
* **MDVA-38608** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Correction du problème en raison duquel les tables temporaires ne sont pas supprimées lorsque la réindexation n’est pas terminée correctement.
* **MDVA-38308** (*pour Adobe Commerce >=2.3.5 &lt;=2.3.6-p1) || >=2.4.0 &lt;=2.4.1-p1 || >=2.4.2 &lt;2.4.4*) - Correction des problèmes liés à l’ajout de vidéos [!DNL Vimeo] aux produits.

## v1.0.25 {#v1-0-25}

* **MDVA-37916** (*pour Adobe Commerce >=2.3.6 &lt;2.4.3*) - Correction du problème en raison duquel le client n’était pas amené sur la page de confirmation du paiement lors de l’utilisation de la méthode [!DNL Paypal Payment Advanced].
* **MDVA-37082** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Correction du problème lors de l’enregistrement du stock personnalisé de produits groupés qui entraîne l’affichage du produit en rupture de stock dans l’interface.
* **MDVA-36572** (*pour Adobe Commerce >=2.3.5 &lt;2.4.3*) - Correction du problème lorsque les mises à jour de la note de crédit ne provoquent plus de mises à jour de réservation de produits en double dans la base de données.
* **MDVA-38132** (*pour Adobe Commerce >=2.3.3 &lt;2.4.3*) - Correction du problème lorsque le panneau d’administration n’est pas accessible en raison d’une erreur *trop de redirections*.
* **MDVA-38270** (*pour Adobe Commerce >=2.4.1 &lt;2.4.3*) - Correction du problème lié aux informations de carte cadeau manquantes dans le total de la commande dans GraphQL.

## v1.0.24 {#v1-0-24}

* **MDVA-3779** (*pour Adobe Commerce >=2.4.2 &lt;=2.4.4*) - Correction du problème lié à l’ajout d’un produit configurable au panier via GraphQL lorsque l’ID de site web ne correspond pas à l’ID de magasin.
* **MDVA-36832** (*pour Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - Correction du problème de duplication des images sur les pages lorsque la largeur de l’affichage est de 768 px.
* **MDVA-37874** (*pour Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;=2.4.2-p1*) - Correction du problème en raison duquel le *montant de remise fixe pour le panier entier* est incorrectement appliqué à un produit en regroupement contenant plusieurs options.
* **MDVA-37913** (*pour Adobe Commerce >=2.3.0 &lt;=2.4.0-p1*) - Correction du problème de disparition des liens téléchargeables si le produit téléchargeable est mis à jour via l’API.
* **MDVA-34330** (*pour Adobe Commerce >=2.3.1 &lt;=2.4.2-p1*) - Correction du problème en raison duquel les commandes de la grille Commandes ne sont pas filtrées selon le fuseau horaire Admin.

## v1.0.23 {#v1-0-23}

* **MDVA-37478** (*pour Adobe Commerce >=2.3.0 &lt;=2.3.7*) - Correction du problème en raison duquel Adobe Commerce renvoie une erreur lors de la création d’une facture partielle pour les commandes passées avec le mode de paiement *Paiement sur compte* via l’API REST.
* **MDVA-37362** (*pour Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - Correction du problème en raison duquel les valeurs des options de produit configurables et les valeurs d’attribut de variante étaient vides dans la réponse GraphQL.
* **MDVA-37288** (*pour Adobe Commerce 2.4.2*) - Correction du problème en raison duquel des prix de niveau incorrects étaient renvoyés après la demande GraphQL.
* **MDVA-37225** (*pour Adobe Commerce >=2.4.1 &lt;=2.4.2-p1*) - Correction du problème de blocage du processus de chargement lors de la création d’un ordre rapide lorsqu’il existe une valeur entière dans les SKU importés.
* **MDVA-37224** (*pour Adobe Commerce >=2.3.3 &lt;=2.4.2-p1*) - Correction du problème en raison duquel les clients ne peuvent pas payer pour un devis négociable avec [!DNL PayFlow Pro] avec un autre produit dans le panier.
* **MDVA-36286** (*pour Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - Correction du problème d’interruption de l’aperçu du widget des produits Page Builder si le même SKU a une position différente dans les sous-catégories.
* **MDVA-30186** (*pour Adobe Commerce >=2.3.4 &lt;=2.3.5-p2, >=2.4.0 &lt;=2.4.0-p1, >=2.4.2 &lt;=2.4.2-p1*) - Correction du problème où les options d’attribut sont triées par valeur d’option nombre d’éléments dans la réponse GraphQL.

## v1.0.22 {#v1-0-22}

* **MDVA-36718** (*pour Adobe Commerce >=2.3.0 &lt;=2.4.2*) - Correction du problème en raison duquel les anciennes options personnalisées restent après avoir été modifiées via l’API.
* **MDVA-35773** (*pour Adobe Commerce >=2.3.6 &lt;=2.3.6-p1) || >=2.4.1 &lt;=2.4.2*) : correction du problème en raison duquel le total général n’était pas affiché comme zéro sur la facture pour les commandes avec une remise de 100 %.
* **MDVA-36833** (*pour Adobe Commerce 2.4.2*) - Correction du problème lié aux résultats de recherche qui affichaient un nombre aléatoire de produits par page après l’exclusion de certains produits du catalogue partagé.
* **MDVA-37182** (*pour Adobe Commerce >=2.4.1 &lt;=2.4.2*) - Correction du problème lié à l’obtention de résultats de recherche incorrects dans [!DNL Elasticsearch] version 6 et version 7.
* **MDVA-36253** (*pour Adobe Commerce >=2.4.0 &lt;=2.4.1-p1*) - Correction du problème en raison duquel un sous-total incorrect s’affichait dans le mini-panier après suppression de l’élément.
* **MDVA-36853** (*pour Adobe Commerce 2.4.2*) - Correction du problème en raison duquel aucune image n’apparaissait lors du chargement de galeries multimédia volumineuses.

## v1.0.21 {#v1-0-21}

* **MDVA-34665** (*pour Adobe Commerce >=2.3.4 &lt;=2.3.4-p2*) - Correction du problème lié aux produits regroupés manquants sur les pages de catégorie.
* **MDVA-36615** (*pour Adobe Commerce 2.4.2*) - Correction du problème lié à un nombre de produits incorrect dans la grille de produits Admin.
* **MDVA-36464** (*pour Adobe Commerce >=2.4.0 &lt;=2.4.2*) - Correction du problème de dysfonctionnement de la configuration des notifications électroniques au niveau de l’affichage en magasin.
* **MDVA-36138** (*pour Adobe Commerce ^2.3.2*) - Correction du problème en raison duquel le prix de livraison n’est pas ajusté et le prix de livraison complet est affiché aux clients si tous les articles du panier ne remplissent pas les critères de la règle du panier d’expédition gratuit.
* **MDVA-36424** (*pour Adobe Commerce >=2.3.0 &lt;=2.3.3-p1) || >=2.0.0 &lt;2.2.0*) - Correction du problème de disparition des images multimédias associées aux éléments du créateur de pages lorsque le contenu est modifié à plusieurs reprises si l’URL de base du serveur principal est différente de l’URL de base du storefront.
* **MDVA-35984** (*pour Adobe Commerce ^2.4.0*) - Correction du problème lié à une quantité de produits incorrecte et à une quantité vendable après la création de plusieurs envois simultanés pour le même produit.

## v1.0.20 {#v1-0-20}

* **MDVA-36170** (*pour Adobe Commerce >=2.3.4 &lt;2.4.2*) - Ceci corrige le problème en raison duquel la requête GraphQL n’est pas mise en cache à l’aide de la balise de cache de catégorie.
* **MDVA-33168** (*pour Adobe Commerce >=2.3.3 &lt;2.4.2*) - Correction du problème lors de la mise à jour d’un attribut de produit via l’API, tous les autres attributs passant à une valeur vide.
* **MDVA-19640** (*pour Adobe Commerce >=2.3.0*) - Correction du problème en raison duquel [!DNL Advanced Reporting] n’affiche aucune donnée.
* **MDVA-11189** (*pour Adobe Commerce >=2.3.0 &lt;2.3.5*) - Correction du problème lors de l’importation d’un fichier CSV pour mettre à jour le stock de produits, les lignes de la table `cataloginventory_stock` sont supprimées.
* **MDVA-26639** (*pour Adobe Commerce >=2.3.3-p1 &lt;2.3.6*) - Correction du problème en raison duquel, si un nouveau modèle d’email de confirmation de commande est créé, les éléments de commande sont manquants dans le courrier électronique de commande.
* **MDVA-15546** (*pour Adobe Commerce >=2.3.0*) - Correction du problème qui, après la création d’une commande, affiche une erreur *Column entity_id où la clause est ambiguous* dans le journal des exceptions.
* **MDVA-21095** (*pour Adobe Commerce >=2.3.0 &lt;2.3.5*) - Correction du problème lorsqu’une requête `INSERT INTO search_tmp` ne se terminera pas après la mise à jour de la valeur d’attribut de masse.
* **MDVA-23845** (*pour Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - Correction du problème en raison duquel les modèles de courrier électronique ne peuvent pas être prévisualisés une fois la minification JavaScript activée.
* **MDVA-22026** (*pour Adobe Commerce >=2.3.2 &lt;2.3.4*) - Correction du problème d’échec de l’importation de produits à partir d’un fichier CSV comprenant des images d’URL externes.
* **MDVA-22383** (*pour Adobe Commerce >=2.3.0 &lt;2.3.4*) - Correction du problème en raison duquel l’enregistrement d’un produit prend beaucoup de temps et les sauts de page.
* **MC-41359** (*pour Adobe Commerce >=2.3.6-p1 &lt;2.3.7, >=2.4.2 &lt;2.4.3*) - Correction du problème des paramètres de cookie SameSite incorrects.

## v1.0.19 {#v1-0-19}

* **MDVA-33614** (*pour Adobe Commerce 2.4.1*) - Correction du problème où Page Builder générait l’erreur suivante : *Une erreur s’est produite lors du lancement de Page Builder. Veuillez consulter votre contact de support technique.*
* **MDVA-35356** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Correction du problème lié à un retour de crédit de magasin incorrect après l’annulation de commande partiellement facturée.
* **MDVA-33289** (*pour Adobe Commerce >=2.4.0 &lt;2.4.3*) - Correction du problème d’affichage du code JavaScript brut dans l’interface utilisateur des adresses de facturation lors de l’extraction si [!DNL Google Tag Manager] est activé.
* **MDVA-35982** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Correction du problème en raison duquel les utilisateurs administrateurs limités à un site web spécifique ne pouvaient pas créer d’envoi pour la commande passée sur le même site web.
* **MDVA-35155** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6*) - Correction du problème où il est impossible d’acheter un produit en regroupement si le titre de l’option a été modifié.
* **MDVA-35910** (*pour Adobe Commerce >=2.4.1 &lt;2.4.3*) - Correction du problème en raison duquel il est impossible de créer un nouveau compte client après avoir désactivé la fonctionnalité Se connecter en tant que client .
* **MDVA-34474** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Correction du problème lié à l’ajout d’un produit à la liste de demandes à l’aide de l’API.
* **MDVA-34591** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Correction du problème lié à un calcul de remise de règle de panier incorrect pour *La remise de quantité maximale est appliquée à* et *Étape de qualité de remise (Buy X)*.
* **MDVA-33704** (*pour Adobe Commerce >=2.4.0 &lt;2.4.3*) - Correction du problème en raison duquel l’option d’expédition *In store pickup* ne s’affichait pas, bien que configurée pour être disponible.
* **MDVA-34928** (*pour Adobe Commerce >=2.3.5 &lt;2.3.5-p2*) - Correction du problème d’affichage indéfini du chargeur de page après suppression du paiement du crédit de la boutique.
* **MDVA-35254** (*pour Adobe Commerce >=2.3.1 &lt;2.4.3*) - Correction des problèmes liés à CAPTCHA pendant l’extraction.
* **MDVA-35569** (*pour Adobe Commerce >=2.3.4 &lt;2.4.2*) - Correction du problème en raison duquel le champ *taxes fixes sur les produits* n’est pas renseigné dans la réponse GraphQL lorsque l’état est spécifié.
* **MDVA-35847** (*pour Adobe Commerce >=2.4.1 &lt;2.4.3*) - Correction du problème B2B où le formulaire Utilisateurs de l’entreprise se brise si un attribut client personnalisé est utilisé.
* **MDVA-31307** (*pour Adobe Commerce >=2.4.0 &lt;2.4.2*) - Correction du problème qui entraînait des erreurs *de mémoire insuffisante* sur certaines catégories en raison de problèmes de mise en whiteliste dynamique de la CSP pour les blocs mis en cache.

## v1.0.18 {#v1-0-18}

* **MDVA-32655** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Correction de l’état incorrect du message *en cours* sur le message *complete* correct pour le consommateur `quoteItemCleaner` après la suppression de plusieurs produits.
* **MDVA-34102** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Correction de la quantité de Stock par défaut à zéro pour les produits désactivés sur les pages Grille de produits et Modifier le produit dans la zone d’administration.
* **MDVA-35286** (*pour Adobe Commerce >=2.4.0 &lt;2.4.2*) - Correction du problème en raison duquel une erreur survenait si un client avait regroupé des produits dans son panier et passait de l’extraction à l’extraction à plusieurs adresses à l’extraction à une seule page.
* **MDVA-35312** (*pour Adobe Commerce >=2.4.1-p1 &lt;2.4.2*) - Correction du code de réponse 500 lorsqu’une requête GraphQL vide.
* **MDVA-34189** (*pour Adobe Commerce >=2.3.4 &lt;2.4.3*) - Correction du délai d’attente de 503 premiers octets sur les requêtes [!DNL Visual Merchandiser] lors du chargement de la page Catégorie d’administration.
* **MDVA-34695** (*pour Adobe Commerce >=2.3.0 &lt;2.4.1*) - Correction de la valeur négative `children_count` après suppression des catégories.

## v1.0.17 {#v1-0-17}

* **MDVA-34012** (*pour Adobe Commerce >=2.3.1 &lt;2.4.3*) - Correction du problème en raison duquel la case à cocher *Utiliser la valeur par défaut* est décochée après l’application des modifications planifiées. Le problème s’affiche une fois que les modifications planifiées ne sont plus en vigueur.
* **MDVA-35064** (*pour Adobe Commerce >=2.3.3 &lt;2.4.3*) - Correction du problème en raison duquel les réécritures d’URL ne sont pas générées pour les produits configurables créés via l’API.
* **MDVA-34943** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème en raison duquel l’ordre rapide met en cache les SKU précédemment saisis.
* **MDVA-35197** (*pour Adobe Commerce >=2.3.5 &lt;2.4.0*) - Correction du problème en raison duquel une erreur se produisait lors de l’ajout au panier à l’aide de GraphQL si des produits précédemment ajoutés devenaient en rupture de stock.
* **MDVA-34850** (*pour Adobe Commerce >=2.3.1 &lt;2.4.0*) - Correction du problème en raison duquel les options en rupture de stock d’un produit configurable ne s’affichaient pas au lieu d’être affichées comme étant ponctuelles.
* **MDVA-34867** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Correction du problème en raison duquel les valeurs d’un champ de condition défini pour une mise à jour planifiée ne sont pas enregistrées.
* **MDVA-35092** (*pour Adobe Commerce >=2.3.5 &lt;2.4.3*) - Correction du problème en raison duquel les utilisateurs ne pouvaient pas ajouter [!DNL Vimeo] vidéos en raison d’une API [!DNL Vimeo] obsolète.

## v1.0.16 {#v1-0-16}

* **MDVA-33453** (*pour Adobe Commerce >=2.3.6 &lt;2.4.3*) - Correction du problème d’interruption de l’aperçu du type de contenu de produits Page Builder lorsque les produits correspondants ont des prix différents pour chaque site web.
* **MDVA-32634** (*pour Adobe Commerce ^2.3.1*) - Correction du problème en raison duquel le `url_path` de la catégorie affectée à tous les magasins reste inchangé après le déplacement de la catégorie dans la hiérarchie.
* **MDVA-33344** (*pour Adobe Commerce ^2.3.0*) - Correction du problème en raison duquel l’identifiant de jeu d’attributs par défaut d’entité `rma_item` codé en dur est utilisé à la place de la valeur de la base de données.
* **MDVA-34192** (*pour Adobe Commerce >=2.3.4 &lt;2.4.3*) - Correction du problème où il est impossible de modifier/spécifier la date de naissance du client à l’aide du format jj/mm/aaaa.
* **MDVA-34847** (*pour Adobe Commerce ^2.3.0*) - Correction d’une conversion de type ID de magasin en entier pour les conditions SQL dans les collections d’administration pour les utilisateurs administrateurs avec des autorisations personnalisées.
* **MDVA-34886** (*pour Adobe Commerce ^2.3.2*) - Correction du problème où la recherche ne renvoie pas de résultats si l’attribut de produit *weight* est configuré comme pouvant faire l’objet d’une recherche.

## v1.0.15 {#v1-0-15}

* **MDVA-33559** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Correction du problème d’échec du paiement [!DNL PayPal Payflow Pro] avec une erreur de format de liste de paramètres de redirection.
* **MDVA-34023** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Correction du problème qui entraînait l’affichage aléatoire de l’erreur *Aucune entité de ce type avec addressId* sur les navigateurs des visiteurs.
* **MDVA-32759** (*pour Adobe Commerce >=2.3.1 &lt;2.4.3 avec extension B2B*) - Correction du problème en raison duquel les catalogues partagés supprimaient les tarifs de niveau existants.
* **MDVA-33482** (*pour Adobe Commerce ^2.3.5*) - Correction du problème en raison duquel la génération d’un Avoir de crédit sur une facture partielle générait une taxe sur la commande totale au lieu de la taxe sur cette facture partielle.
* **MDVA-33393** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction de l’erreur *L’ID de pays fourni n’existe pas*.
* **MDVA-33632** (*pour Adobe Commerce >=2.3.0 &lt;2.3.7*) - Fournit un correctif où le message d’exception *Ce produit est en rupture de stock* s’affiche désormais pour un utilisateur administrateur lors d’une tentative de réorganisation d’un produit en rupture de stock.
* **MDVA-34469** (*pour Adobe Commerce >=2.4.1 &lt;2.4.2*) - Correction du problème d’échec des mutations GraphQL sur le panier d’un client lors de l’utilisation de plusieurs vues de magasin.
* **MDVA-33976** (*pour Adobe Commerce >=2.3.0 &lt;2.3.7*) - Correction du problème en raison duquel le produit du lot s’affiche en rupture de stock sur le storefront après avoir supprimé la deuxième option du produit du lot.
* **MDVA-33894** (*pour Adobe Commerce >=2.4.0 &lt;2.4.1 avec extension B2B*) - Correction de plusieurs problèmes pour la fonctionnalité de commande rapide, notamment l’ajout et la suppression de plusieurs produits et le respect de la casse des SKU.
* **MDVA-27664** (*pour Adobe Commerce >=2.3.4 &lt;2.3.6*) - Correction du problème dans le formulaire d’enregistrement du client provoquant l’affichage d’une erreur : *ERROR - La date de naissance ne doit pas être supérieure à aujourd’hui.*
* **MDVA-33970** (*pour Adobe Commerce >=2.3.4 &lt;2.4.2*) - Correction du problème en raison duquel un mauvais signe de devise s’affichait dans la Note de crédit lorsque la portée de l’attribut de prix était définie sur le site web.
* **MDVA-33992** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème des prix spéciaux B2B qui s’affichaient incorrectement lors du passage en caisse.
* **MDVA-34100** (*pour Adobe Commerce >=2.3.4 &lt;2.4.2 avec extension B2B*) - Correction du problème qui empêchait la création d’un compte d’entreprise à partir de la page de structure de l’entreprise.

## v1.0.14 {#v1-0-14}

* **MDVA-31969** (*pour Adobe Commerce >=2.3.3 &lt;2.3.5, >=2.4.0 &lt;2.4.2*) - Correction du problème lié aux images dupliquées après l’importation de produits à partir d’un fichier CSV.
* **MDVA-33382** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction des problèmes d’invalidation des indexeurs après suppression de produits d’une catégorie.
* **MDVA-28511** (*pour Adobe Commerce >=2.3.5 &lt;2.3.6*) - Correction du problème en raison duquel il n’est pas possible d’effectuer l’extraction [!DNL PayPal] si le champ Nom contient certains caractères (comme les majuscules accentuées).
* **MDVA-31519** (*pour Adobe Commerce >=2.3.5 &lt;2.3.6*) - Correction du problème lié aux délais d’attente dans le passage en caisse des invités lorsqu’une règle de vente à l’échelle du site est en cours d’utilisation.
* **MDVA-33281** (*pour Adobe Commerce >=2.3.4 &lt;2.3.6*) - Correction du problème en raison duquel une erreur fatale se produisait dans `inventory:reservation:list-inconsistencies` en raison d’un type de paramètre SKU incorrect.
* **MDVA-24201** (*pour Adobe Commerce >=2.3.0 &lt;2.3.5*) - Correction du problème en raison duquel les prix ne reflètent pas la règle de prix du panier planifiée tant qu’ils n’ont pas été réindexés manuellement.
* **MDVA-32694** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6 || >= 2.4.0 &lt;2.4.2*) - Correction du problème qui empêchait un utilisateur administrateur d’ajouter un produit à un guillemet négociable s’il était lié à un magasin autre qu’un magasin par défaut.
* **MDVA-33516** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6*) - Correction du problème qui entraînait une erreur lors de la modification d’un produit en bundle dans une liste de demandes.
* **MDVA-33975** (*pour Adobe Commerce >=2.3.4 &lt;2.4.2*) - Correction de plusieurs problèmes liés au calcul des prix dans les demandes GraphQL.

## v1.0.13 {#v1-0-13}

* **MDVA-30858** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème en raison duquel les [!DNL PayPal] rapports de règlement n’étaient pas disponibles sous **Rapports** > **Ventes** > **[!DNL PayPal]** comme prévu.
* **MCP-87** (*pour Adobe Commerce >=2.3.1 &lt;2.4.2*) - Amélioration du temps d’indexation pour les indexeurs de produits de catégorie et de stock pour les profils volumineux.
* **MDVA-33106** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème en raison duquel les modifications de produit reprogrammées sont effacées après l’exécution de la commande cron `run`.
* **MDVA-19391** (*pour Adobe Commerce >=2.3.0 &lt;2.3.5*) - Correction du problème en raison duquel `analytics_collect_data` renvoyait une erreur en raison des enregistrements de description NULL dans la table `catalog_category_entity_text`.
* **MDVA-20376** (*pour Adobe Commerce >=2.3.2 &lt;2.3.4*) - Correction du problème lié à l’erreur *Aucune entité de ce type avec customerId = 1* dans `exception.log` pour les clients connectés après l’emplacement de la commande.
* **MDVA-23764** (*pour Adobe Commerce >=2.3.2 &lt;2.3.5*) - Correction du bogue dans `JsFooterPlugin.php` qui affecte l’affichage des blocs dynamiques.
* **MDVA-13203** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème en raison duquel l’erreur *Integrity contrainte de violation search_tmp_ table* s’affiche après une réindexation complète.
* **MDVA-23426** (*pour Adobe Commerce >=2.3.3 &lt;2.3.5*) - Correction du problème en raison duquel les emails de notification envoyés par Adobe Commerce contenaient un corps vide avec du contenu ajouté en pièce jointe.
* **MDVA-22150** (*pour Adobe Commerce >=2.3.1 &lt;2.3.4*) - Correction du problème qui empêchait les clients ayant un produit configurable dans le panier et un coupon appliqué de se connecter si ce produit configurable était désactivé dans l’administrateur.
* **MDVA-32545** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème en raison duquel les factures ne sont pas envoyées automatiquement lors de la création de commandes de l’administrateur.
* **MDVA-32714** (*pour Adobe Commerce >=2.3.4 &lt;2.4.1*) - Correction du problème en raison duquel le prix du groupe de clients ne fonctionnait pas dans la requête de produit GraphQL.

## v1.0.12 {#v1-0-12}

* **MDVA-31399** (*pour Adobe Commerce >=2.3.2 &lt;2.4.2*) - Ajoute le *Sous-total (Incl. Taxe)* pour définir les conditions des règles de prix.
* **MDVA-31236** (*pour Adobe Commerce >=2.4.0 &lt;2.4.2*) - Correction du problème qui empêchait les administrateurs disposant d’un accès aux ressources personnalisées de configurer 2FA ou de se connecter.
* **MDVA-30845** (*pour Adobe Commerce >=2.3.5 &lt;2.3.7*) - Correction du problème en raison duquel l’erreur *Désolé, aucun guillemet n’est disponible pour cette commande à l’heure actuelle* s’affiche lorsque vous ne vous connectez pas à UPS XML/USPS/DHL et aucune autre méthode de livraison n’est disponible.
* **MDVA-32133** (*pour Adobe Commerce >=2.4.0 &lt;2.4.1*) - Correction du problème en raison duquel la galerie multimédia ne se charge pas à partir du créateur de pages dans certains cas.
* **MDVA-12304** (*pour Adobe Commerce >=2.3.0*) - Augmente le nombre maximum de cookies de 50 à 200.
* **MDVA-32632** (*pour Adobe Commerce >=2.3.2 &lt;2.3.5*) - Correction du problème en raison duquel les commandes s’affichaient dans le système de paiement, mais pas dans Adobe Commerce.
* **MDVA-32449** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || >=2.4.1 &lt;2.4.2 avec extension B2B*) - Correction du problème en raison duquel l’historique des commandes se charge très lentement ou ne se charge pas du tout.
* **MDVA-32739** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème qui entraînait l’envoi d’anciens emails de vente par l’activation des notifications par courrier électronique asynchrones.

## v1.0.11 {#v1-0-11}

* **MC-38509** (*pour Adobe Commerce 2.3.6, 2.4.1*) - Correction du problème en raison duquel le bouton *Créer un compte* reste désactivé après avoir corrigé des données non valides dans le formulaire *Créer un compte client*.
* **MDVA-31006** (*pour Adobe Commerce 2.3.0, 2.3.1*) - Correction du problème d’affichage des commandes dupliquées après le placement d’une commande à l’aide du paiement [!DNL Paypal Express].
* **MDVA-25602** (*pour Adobe Commerce 2.3.0*) - Correction d’un problème lié au mode de paiement [!DNL PayPal Payflow Pro] et traitement des cookies comme `SameSite=Lax` par défaut dans la page de connexion du navigateur Chrome 80 et de la réponse de l’API redirigée vers la page de connexion du client.

## v1.0.10 {#v1-0-10}

Correctifs mineurs pour les versions de correctif

## v1.0.9 {#v1-0-9}

* **MDVA-31363** (*pour Adobe Commerce >=2.3.2 &lt;2.4.2*) - Correction du problème en raison duquel la règle du prix du panier avec coupon ne s’applique pas via GraphQL lorsque l’action *Remise de montant fixe pour le panier entier* est utilisée.
* **MDVA-3089** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème qui se produit lorsqu’une erreur se produit après la facturation d’un lot avec des produits virtuels et simples comme options.
* **MDVA-31791** (*pour Adobe Commerce >=2.3.4 &lt;2.3.5*) - Améliore les performances de la page de produits lorsque des règles cibles ou des produits liés sont utilisés.
* **MDVA-31168** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème en raison duquel le fichier CSV d’exportation de produit n’apparaissait pas et il y a une erreur d’allocation de mémoire.
* **MDVA-32313** (*pour Adobe Commerce >=2.3.0 &lt;2.3.4*) - Correction du problème en raison duquel des produits configurables pouvaient être ajoutés à la liste des souhaits avec des options de configuration incorrectes.
* **MDVA-31759** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème où les produits ne sont pas mis à jour avec les valeurs d’attribut *dropdown* et *textarea* lors de l’importation CSV.
* **MDVA-32012** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème en raison duquel les codes postaux en Corée et en Argentine ne pouvaient pas être validés.
* **MDVA-31640** (*pour Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) - Correction d’un problème en raison duquel un prix spécial ne pouvait pas être mis à jour via l’API REST.
* **MDVA-28651** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6 || >2.4.0 avec extension B2B* - Correction du problème de performances lors du chargement de guillemets négociables via l’API REST.

## v1.0.8 {#v1-0-8}

* **MDVA-31242** (*pour Adobe Commerce >=2.3.0 &lt;2.4.1 avec extension B2B*) - Correction du problème d’affichage d’un signe de devise incorrect dans la grille Monnaie de crédit.
* **MDVA-31295** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème en raison duquel les points de récompense ne sont pas calculés lorsqu’une commande partielle est terminée et que les éléments sont taxés.
* **MDVA-30112** (*pour Adobe Commerce >=2.3.4 &lt;2.4.2*) - Correction du problème en raison duquel, si le nombre de commandes dépasse la valeur *bunch-size*, Adobe Commerce considère les commandes dont le statut est *en attente* comme des incohérences.
* **MDVA-31150** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème en raison duquel les soldes des cartes de crédit et de cadeau de la boutique ne sont pas renvoyés par l’appel de l’API REST de la facture, lorsque la facture a été validée par l’appel de l’API REST et que la commande a été partiellement payée par les comptes de carte de crédit de magasin et les comptes de crédit et de carte de cadeau.
* **MDVA-30963** (*pour Adobe Commerce >=2.3.2 &lt;2.4.2*) - Correction du problème en raison duquel les résultats de filtrage des produits ne contenaient que les valeurs spécifiées pour la portée *Toutes les vues de magasin* dans l’administration, incluait les produits dont les valeurs étaient remplacées au niveau de la vue de magasin.
* **MDVA-29954** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || 2.4.2 avec extension B2B* - Correction du problème en raison duquel les *Nouvelle demande d’enregistrement de société* et *Vous avez été lié à une société* emails sont envoyés à partir d’une adresse incorrecte.
* **MDVA-28357** (*pour Adobe Commerce >=2.3.2 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) : remplace l’analyseur standard par un analyseur personnalisé avec un jeton de mot-clé pour le champ SKU de l’index [!DNL ElasticSearch] pour que les requêtes de recherche par caractères génériques fonctionnent avec des SKU contenant un trait d’union (&quot;-&quot;).

## v1.0.7 {#v1-0-7}

* **MDVA-30972** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème en raison duquel l’état de commande personnalisée était remplacé par *Traitement* après la création d’une expédition partielle à l’aide de WebApi.
* **MDVA-30428** (*pour Adobe Commerce >=2.3.4 &lt;2.3.5*) - Correction du problème qui empêchait les clients d’ajouter un produit à une liste bloquée si ce produit était affecté à une source d’inventaire personnalisée.
* **MDVA-30594** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème qui empêchait l’enregistrement d’une commande contenant plusieurs adresses lors de l’extraction lorsque FPT était configuré.
* **MDVA-29148** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème lors de la création d’un produit via un appel API, l’attribut personnalisé de produit de type `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (comme Multiselect) n’utilise pas sa valeur par défaut si aucune valeur n’a été fournie dans la payload.
* **MDVA-30837** (*pour Adobe Commerce >=2.3.1 &lt;2.3.5*) - Ajout d’un paramètre de configuration *Inclure la taxe au montant : Oui/Non* dans la configuration de la méthode d’expédition gratuite. Lorsque *Inclure la taxe au montant* est défini sur *Oui*, le montant minimum de la commande est calculé comme sous-total + taxe. Lorsque *Inclure la taxe au montant* est défini sur *Non*, le montant minimum de la commande est calculé sous forme de sous-total.
* **MDVA-25028** (*pour Adobe Commerce >=2.3.2 &lt;2.3.3 || >=2.3.5 &lt;2.3.6*) - Correction du problème lorsque les commandes passées à l’aide de [!DNL PayPal Payflow Pro] ne sont pas définies sur l’état Fraude suspectée lorsque des filtres de fraude sont déclenchés.
* **MDVA-31224** (*pour Adobe Commerce >=2.3.3 &lt;2.3.5*) - Améliore les performances de l’opération de réindexation `catalog_product_price` pour les produits du lot.
* **MDVA-31321** (*pour Adobe Commerce >=2.3.2 &lt;2.3.5*) - Correction d’une page vierge (erreur) lorsque l’option *Tout afficher* est sélectionnée. [!DNL Elasticsearch] renvoie une grande liste d’identifiants de produit. Dans ce scénario, la clause order by est convertie dans un format SQL incorrect.
* **MDVA-30815** (*pour Adobe Commerce >=2.3.2 &lt;2.3.4*) - Correction du problème en raison duquel, lorsque vous modifiez le nombre de résultats de recherche à afficher sur la page des résultats de recherche, Adobe Commerce affiche une page vierge. [!DNL Elasticsearch] affiche désormais correctement les résultats des pages de catégorie lorsque vous modifiez le nombre de résultats de recherche affichés par page.
* **MDVA-30782** (*pour Adobe Commerce >=2.3.5 &lt;2.4.2*) - Correction du problème d’affichage du bloc dynamique, quelle que soit la règle du panier.
* **MDVA-31021** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème de performances dans `module-catalog-import-export/Model/Import/Product/Option.php`. S’il existe plus de ~100 000 enregistrements dans la table `catalog_product_option`, un nouveau fichier CSV avec un seul produit prend moins de 10 secondes pour être validé.
* **MDVA-31007** (*pour Adobe Commerce >=2.4.0 &lt;2.4.1*) - Correction du problème en raison duquel les attributs d’adresse personnalisée ne s’affichent pas correctement dans la page des détails de la commande dans la zone de mon compte et dans le serveur principal.
* **MDVA-29389** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème lié aux rapports avancés où le `analytics_collect_data` cronjob indique : *Le port doit être configuré dans le paramètre hôte (comme localhost:3306)*.
* **MDVA-31343** (*pour Adobe Commerce >=2.3.4 &lt;2.3.6*) - Correction du problème avec la classe de corps supprimée `page-layout-category-full-width` lorsqu’une catégorie est planifiée.
* **MDVA-30945** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème en raison duquel vous recevez un message d’erreur fatal lors de la mise à jour des paniers `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.

## v1.0.6 {#v1-0-6}

* **MDVA-28993** (*pour Adobe Commerce >=2.3.4 &lt;2.4.0*) - Met en oeuvre la fonctionnalité *Minimum doit correspondre à* et la recherche partielle pour le moteur [!DNL Elasticsearch]. Résout les problèmes liés aux tirets dans les requêtes de recherche.
* **MDVA-30102** (*pour Adobe Commerce >=2.3.2 &lt;=2.4.0*) - Correction du problème en raison duquel le cache Redis augmente rapidement puisque les caches de mise en page n’ont pas TTL.
* **MDVA-30599** (*pour Adobe Commerce >=2.3.4 &lt;=2.4.0*) - Correction du problème en raison duquel les guillemets d’invité créés à l’aide de l’API sont incorrectement marqués comme guillemets pour les clients connectés.
* **MDVA-29446** (*pour Adobe Commerce >=2.3.3 &lt;=2.4.0*) - Correction du problème en raison duquel le prix de la méthode d’expédition non applicable s’affiche comme zéro pendant le passage en caisse.
* **MDVA-30357** (*pour Adobe Commerce >=2.3.2 &lt;=2.4.0*) - Correction du problème lié à la création d’URL d’image incorrectes lors de la génération d’un plan de site par cron.
* **MDVA-30565** (*pour Adobe Commerce >=2.3.2 &lt;=2.3.3-p1*) - Correction du problème en raison duquel *Aucune entité de ce type avec cartid = 0* une erreur s’affiche pour les clients invités lors du passage en caisse en cas d’activation du panier persistant.
* **MDVA-29787** (*pour Adobe Commerce >=2.3.0 &lt;=2.4.0*) - Correction du problème en raison duquel la règle cible pour les produits associés ne fonctionne pas lorsque *est l’une des conditions* est utilisée pour définir les produits à afficher.
* **MDVA-30977** (*pour Adobe Commerce >=2.3.4 &lt;=2.3.5-p2*) - Correction du problème lié aux produits aléatoires manquants dans les catégories après la réindexation.
* **MDVA-28202** (*pour Adobe Commerce >=2.3.4 &lt;=2.4.2*) - Correction du problème en raison duquel la navigation par couches ne filtre pas correctement les produits configurables lorsque MSI est utilisé.
* **MDVA-28300** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6*) - Correction du problème en raison duquel la demande GQL ne reflétait pas les modifications de prix des règles de prix du catalogue.
* **MDVA-31006** (*pour Adobe Commerce >=2.3.2 &lt;=2.4.2*) - Correction du problème d’affichage des commandes dupliquées après le placement d’une commande à l’aide du paiement [!DNL Paypal Express].

## v1.0.5 {#v1-0-5}

* **MDVA-30841** (*pour Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Correction du problème de navigation par couches, où la valeur *Non* pour les attributs de produit de type booléen n’était pas incluse dans la navigation par couches si [!DNL Elasticsearch] était utilisé comme moteur de recherche.
* **MDVA-28191** (*pour Adobe Commerce >=2.3.3 &lt;2.4.2*) - Correction du problème en raison duquel aucun mode de paiement n’est chargé lors de la création de la commande via l’administrateur.
* **MDVA-29959** (*pour Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 avec extension B2B*) - Correction du problème en raison duquel l’utilisateur administrateur restreint avec les autorisations *Entreprises* n’est pas autorisé à supprimer le compte de la société.
* **MDVA-30265** (*pour Adobe Commerce >=2.3.3 &lt;2.4.2*) - Correction du problème en raison duquel le lien de suivi des envois ne fonctionnait plus après la création de la facture.
* **MDVA-28409** (*pour Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Correction du problème d’échec de la tâche `sales_clean_quotes` cron avec l’erreur *out-of-memory* lorsque le nombre de guillemets expirés dans la base de données est énorme.
* **MDVA-30593** (*pour Adobe Commerce >=2.3.0 &lt;2.3.4*) - Correction du problème en raison duquel les guillemets qui ont expiré selon le paramètre Durée de vie des citations ne sont pas nettoyés.
* **MDVA-30107** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6*) - Correction du problème en raison duquel le sélecteur de magasin ne fonctionne pas comme prévu si différentes URL de base sont utilisées pour les vues de magasin.
* **MDVA-28763** (*pour Adobe Commerce >=2.3.2 &lt;2.3.4*) - Correction du problème de duplication de l’image du produit après la mise à jour des informations sur le produit à l’aide de l’API REST plusieurs fois.
* **MDVA-30284** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème d’échec de l’indexeur de recherche catalogue en raison de l’erreur *[!DNL Elasticsearch]suivante : la limite du nombre total de champs dans l’index a été dépassée.*
* **MDVA-29042** (*pour Adobe Commerce >=2.3.3 &lt;=2.3.4-p2 avec extension B2B*) - Correction du problème en raison duquel les autorisations de catalogue étaient remplacées automatiquement par *Autoriser* après l’ajout d’un nouveau produit au catalogue partagé.
* **MDVA-30428** (*pour Adobe Commerce >=2.3.3 &lt;2.4.2*) - Correction du problème qui empêchait les clients d’ajouter un produit à une liste bloquée si ce produit était affecté à une source d’inventaire personnalisée.
* **MDVA-28661** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2 avec extension B2B*) - Correction du problème qui entraînait l’apparition d’une erreur dans la section Compte de société Utilisateurs de la société après la modification de l’administrateur de la société.

## v1.0.4 {#v1-0-4}

* **MDVA-30195** (*pour Adobe Commerce 2.3.1 - 2.3.4-p2*) - Correction du problème d’échec des tâches cron lorsque le nom de la base de données est trop long, ce qui entraîne la non-mise à jour des catégories sur le front-end.
* **MDVA-30106** (*pour Adobe Commerce ^2.3.0*) - Correction d’un problème en raison duquel, lors des paiements de passage en caisse, aucune erreur *Impossible de lire la propriété ’length’ de null* n’est chargée dans la console JS.
* **MDVA-28656** (*pour Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.2*) - Correction du problème en raison duquel, si une commande a été passée sans aucune information de paiement requise (par exemple, avec une remise de 100 %) et qu’une facture a été créée pour la commande, l’état de la commande passe à *Fermé* au lieu de Terminé.
* **MDVA-30209** (*pour Adobe Commerce 2.3.0 - 2.3.3-p1*) - Correction du problème en raison duquel le groupe de clients était remplacé par défaut si le client mettait à jour les informations de son compte.
* **MDVA-30123** (*pour Adobe Commerce >=2.3.4 &lt;2.4.2*) - Correction du problème en raison duquel les libellés des options d’attribut ne sont pas correctement traduits pour les requêtes GraphQL.
* **MDVA-2996** (*pour Adobe Commerce >=2.3.3 &lt;2.4.2*) - Correction du problème en raison duquel, après l’activation de l’autorisation de catégorie, la page de catégorie n’est pas mise en cache par le cache de page complète.
* **MDVA-30164** (*pour Adobe Commerce >=2.3.1 &lt;2.4.2*) - Correction du problème en raison duquel les enregistrements de clients ne peuvent pas être exportés à partir de la grille Clients s’il existe des attributs de client personnalisés.
* **MDVA-3044** (*pour Adobe Commerce >=2.3.0 &lt;2.4.1*) - Correction du problème en raison duquel aucun courrier électronique de confirmation n’est envoyé pour les commandes passées à l’aide de GraphQL.
* **MDVA-30490** (*pour Adobe Commerce 2.3.4 - 2.3.5-p2*) - Correction du problème en raison duquel la comparaison des produits renvoie la page d’erreur 500 si l’un des produits a une brève description vide.
* **MDVA-30232** (*pour Adobe Commerce >=2.3.1 &lt;2.4.1*) - Correction du problème qui empêche la réorganisation si la commande d’origine contient une carte-cadeau.
* **MDVA-29965** (*pour Adobe Commerce >=2.3.3 &lt;2.4.0*) - Correction du problème en raison duquel les clients obtenaient une erreur de clé de formulaire non valide lors de l’ajout d’un produit au panier.
* **MDVA-3008** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème B2B où il n’est pas possible de passer des commandes par le biais de l’API d’administration pour un produit qui se trouve dans un catalogue public.
* **MDVA-22469** (*pour Adobe Commerce 2.3.2-p2 - 2.3.3-p1*) - Correction du problème en raison duquel, après la mise à niveau vers Adobe Commerce 2.3.3, le générateur de pages ne fonctionnait pas dans le panneau d’administration et certains fichiers JS et CSS ne se chargeaient pas.
* **MC-35984** (*pour Adobe Commerce >=2.4.0 &lt;2.4.1*) - Correction du problème qui empêchait les marchands d’interagir avec des éléments de page sur la page Retours après la création d’une étiquette d’expédition pour une autorisation de marchandisage de retour (RMA).

## v1.0.3 {#v1-0-3}

* **MDVA-25602** (*pour Adobe Commerce 2.3.0 - 2.3.4*) - Correction du problème lié au mode de paiement [!DNL PayPal Payflow Pro] et au traitement des cookies comme `SameSite=Lax` par défaut dans la page de connexion du navigateur Chrome 80 et de la réponse de l’API redirigée vers la page de connexion du client.
* **MDVA-26694** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0*) - Correction du problème lié à l’expiration quotidienne des caches de produit et de catalogue, bien que l’expiration soit planifiée différemment.
* **MDVA-27825** (*pour Adobe Commerce >=2.3.0 &lt;2.4.1*) - Correction du problème d’échec de l’exportation de grandes quantités de données en raison d’une fuite de mémoire.
* **MDVA-29085** (*pour Adobe Commerce >=2.3.0 &lt;=2.3.5-p1*) - Correction du problème B2B où aucun nouveau courrier électronique d’entreprise n’est envoyé si une entreprise est créée par l’API.
* **MDVA-29344** (*pour Adobe Commerce >=2.3.5 &lt;=2.4.0-p1*) - Correction du problème de blocage de Page Builder après la copie de texte d’un élément d’en-tête vers un élément de texte.
* **MDVA-29835** (*pour Adobe Commerce >2.3.1 &lt;2.4.2*) - Correction du problème en raison duquel les commandes de carte-cadeau contenaient deux codes au lieu d’un.
* **MDVA-30052** (*pour Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - Correction du problème en raison duquel le contenu privé (stockage local) n’était pas correctement renseigné, ce qui entraînait des problèmes de performances.
* **MDVA-30131** (*pour Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Correction du problème de navigation par couches, où la valeur *Non* pour les attributs de produit de type booléen n’était pas incluse dans la navigation par couches si [!DNL Elasticsearch] était utilisé comme moteur de recherche.
* **MDVA-35514** (*pour Adobe Commerce >=2.4.0 &lt;2.4.1*) - Correction du problème lié à la création d’une étiquette d’expédition et à l’ajout de produits commandés à un package dans la fenêtre modale Créer des packages.
