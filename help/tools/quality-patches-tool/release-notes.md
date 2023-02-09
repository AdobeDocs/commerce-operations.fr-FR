---
title: Notes de mise à jour
description: Découvrez les correctifs disponibles pour Adobe Commerce et les problèmes qu’ils résolvent.
source-git-commit: 76ff1bbcc3a1ca8f73dfdd2ba4f516a201986f62
workflow-type: tm+mt
source-wordcount: '10848'
ht-degree: 0%

---

# Notes de mise à jour

Le [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) fournit des correctifs individuels développés par Adobe et la communauté Magento Open Source. Il vous permet d’appliquer, de rétablir et d’afficher des informations générales sur tous les correctifs individuels disponibles pour la version installée d’Adobe Commerce ou de Magento Open Source. Vous pouvez appliquer des correctifs aux projets Adobe Commerce et Magento Open Source, quel que soit le développeur du correctif. Par exemple, vous pouvez appliquer un correctif développé par la communauté aux projets Adobe Commerce.

>[!INFO]
>
>Voir [Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches) pour obtenir des instructions sur l’application de correctifs à vos projets Adobe Commerce ou Magento Open Source. Voir [Correctifs disponibles](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le Guide de mise à jour du logiciel pour consulter la liste complète des correctifs publiés.

>[!INFO]
>
>Pour plus d’informations sur [!DNL quality patches] créé par la communauté pour les Magento Open Sources, voir la section [notes de mise à jour](https://github.com/magento/quality-patches/blob/master/community-release-notes.md).

## v1.1.27 {#v1-1-27}

* **ACSD-48362** (pour Adobe Commerce >=2.4.1 &lt;2.4.7) - Correction du problème en raison duquel l’adresse de livraison par défaut était utilisée à la place d’une nouvelle adresse lors du placement d’une commande avec un guillemet négociable.
* **ACSD-48059** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction du problème qui empêchait les commerçants d’enregistrer le &quot;[!UICONTROL Match product by rule]&quot; dans la catégorie.
* **ACSD-48216** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7) - Correction du problème en raison duquel [!UICONTROL AUTO_INCREMENT] de [!UICONTROL inventory_source_item] augmente au niveau du tableau [!UICONTROL UPDATE] opération.
* **ACSD-47908** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7) - Correction de l’erreur &quot;Une valeur inférieure ou égale à 0 est attendue&quot; lors de la sélection de la source et de la quantité à l’étape d’expédition lors du passage en caisse.
* **ACSD-49497** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.6) - Correction du problème où une commande reste en état de traitement après l’expédition et qu’un remboursement partiel est appliqué.
* **ACSD-48694** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.1 &lt;2.4.7) - Correction du problème en raison duquel l’erreur &quot;Changement d’état non valide demandé&quot; empêchait un client de passer une commande.
* **ACSD-49013** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème en raison duquel la confirmation par email n’était pas traduite dans les paramètres régionaux du site web lors de la création de clients à l’aide de l’API en bloc.
* **ACSD-48164** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème qui empêchait un administrateur restreint d’enregistrer une valeur au niveau du site web.
* **ACSD-48404** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.4) - Correction du problème en raison duquel &quot;Mémoriser la pagination des catégories = Oui&quot; provoquait une erreur lors de l’activation du bouton Précédent du navigateur.
* **ACSD-48634** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction des erreurs JS sur une page de mise à jour intermédiaire lorsque &quot;[!UICONTROL Google Analytics Content Experiments]&quot; est activé.
* **ACSD-49042** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.5) - Correction du problème qui empêchait la commande d’un produit avec un ordre d’arrière-plan infini à partir de Storefront.
* Correctifs mis à jour : ACSD-48366, ACSD-48661.

## v1.1.26 {#v1-1-26}

* **ACSD-47937** (pour Adobe Commerce et Magento Open Source 2.4.4) || >=2.4.5 &lt;2.4.6) - Correction du problème en raison duquel les notifications de baisse de prix ne sont pas toujours envoyées en raison de la mise en cache au niveau de l’application.
* **ACSD-48661** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel si la limite de crédit de l’entreprise est supérieure à 999, le séparateur de virgules empêche l’enregistrement de l’entreprise en raison d’une erreur de validation.
* **ACSD-48773** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel le modèle d’email des points de récompense provient d’un mauvais magasin.
* **ACSD-48587** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème qui empêchait l’affichage des produits correspondants des caractères spéciaux de HTML dans les règles de correspondance du widget de produits.
* **ACSD-48212** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.6) - Correction du problème en raison duquel l’importation de produit attribue le produit à la mauvaise source.
* **ACSD-47988** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.6) - Correction du problème en raison duquel l’exportation de produits supprimait les balises de HTML de la description du produit du créateur de pages.
* **ACSD-48366** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème en raison duquel l’image du produit ne s’affichait pas dans le modèle de courrier électronique Retour au stock .
* **ACSD-48417** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème d’apparition d’une erreur SQL après la création d’une modification de planification pour un produit et l’enregistrement d’un autre produit.

## v1.1.25 {#v1-1-25}

* **ACSD-48058** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction du problème en raison duquel la réindexation des prix du produit ne fonctionnait pas si le produit du lot n’était affecté à aucun site web.
* **ACSD-48262** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction du problème en raison duquel les produits ne sont pas visibles sur le front-end lorsque le paramètre &quot;Autoriser tous les produits par page&quot; est défini sur Oui.
* **ACSD-48293** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4) - Correction du problème en raison duquel les produits composites étaient en rupture de stock lorsque les produits enfants qui avaient été épuisés étaient retrouvés en stock.
* **ACSD-47520** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème qui entraînait la perte de points de récompense par les clients lors de la création d’une note de crédit.
* **ACSD-48044** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.4) - Correction du problème en raison duquel l’application de plusieurs cartes-cadeaux à une seule commande avec livraison multiple empêchait le placement des commandes.
* **ACSD-48300** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème qui empêchait la création d’un retour en cas de suppression du produit configurable.
* **ACSD-47910** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème des commandes, factures, envois et avoirs manquants dans les grilles d’entités respectives.
* **ACSD-47292** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème en raison duquel les produits en rupture de stock ne sont pas disponibles dans la réponse GraphQL si l’option &quot;Afficher les produits en rupture de stock&quot; est définie sur Oui.
* **ACSD-48234** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction du problème en raison duquel le résultat de la recherche catalogue affichait un nombre d’éléments de catégorie incorrect lorsque l’option &quot;Afficher en rupture de stock&quot; était activée.
* **ACSD-48313** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.5) - Correction du problème en raison duquel la colonne &quot;variations configurables&quot; n’est pas analysée si la valeur de l’attribut contient une virgule. Le même algorithme d’analyse est utilisé pour &quot;additional_attributes&quot;.
* **ACSD-48627** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction du problème en raison duquel le produit configurable en rupture de stock provoquait une erreur lors de l’envoi d’une demande GraphQL pour obtenir les détails du panier.
* Mise à jour du correctif : MDVA-39384.

## v1.1.24 {#v1-1-24}

* **ACSD-45168** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6) - Correction du problème en raison duquel les URL compatibles avec l’optimisation pour les moteurs de recherche ne sont pas générées pour les produits dont la variable *url_key* attributs remplacés au niveau de l’affichage du magasin.
* **ACSD-46865** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème en raison duquel la grille Expédition et Mémo de crédit n’est pas renseignée lorsque l’indexation asynchrone est activée.
* **ACSD-47004** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6) - Correction du problème en raison duquel la TVA n’est pas appliquée à une adresse de facturation sans identifiant de TVA.
* **ACSD-47803** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel les échantillons de produits configurables en rupture de stock s’affichaient comme disponibles.
* **ACSD-47137** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Améliore la vitesse de chargement de la galerie d’images lorsque le dossier pub/média est très volumineux.
* **ACSD-46770** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème d’envoi des emails de l’ordre d’administration même lorsque la variable *Confirmation de commande par e-mail* n’est pas cochée.
* **ACSD-47955** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème en raison duquel GraphQL n’affiche pas correctement la remise au panier.
* **ACSD-46617** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel la variable *Continuer vers l’extraction* est grisé même si le sous-total est supérieur au nombre configuré. *Montant minimal de la commande*.
* **ACSD-47079** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.5) - Correction du problème en raison duquel l’état du stock des produits composites (groupé, groupé et configurable) n’était pas mis à jour lorsque l’état du stock des sous-produits changeait via le POST API REST /rest/V1/inventory/source-items.
* **ACSD-47336** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correctifs *Quelque chose s&#39;est mal passé.* lors de l’affichage des notifications dans l’administrateur Commerce.
* **ACSD-47559** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel la zone Prévisualiser le modèle de courrier électronique n’est pas entièrement visible.
* **ACSD-47920** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel les commandes peuvent être placées via l’API REST en tant qu’utilisateur invité, même lorsque la variable *Autoriser le passage en caisse des invités* est désactivé.
* Correctifs remplacés : MDVA-39305, MDVA-42855.

## v1.1.23 {#v1-1-23}

* **ACSD-47179** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème qui empêchait un administrateur disposant d’un accès limité à une plage spécifique de supprimer les révisions de produits.
* **ACSD-47107** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.5) - Correction du problème en raison duquel la remise de la règle de prix du catalogue était appliquée aux options de produit personnalisées.
* **ACSD-47232** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème qui empêchait l’application des bons avec des conditions de poids total dans l’administrateur.
* **ACSD-46519** (pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.6) - Correction du problème en raison duquel la requête categoryList de GraphQL renvoie un nombre de produits incorrect pour une catégorie d’ancrage.
* **ACSD-47027** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6) - Correction d’une demande GraphQL updateCompanyRole lente.
* **ACSD-47666** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel la fonction de filtre ne fonctionnait pas dans la grille Admin > Système > Autorisations > Rôles utilisateur > un rôle > Utilisateurs de rôle .
* **ACSD-47497** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel l’onglet Services n’était pas visible dans la configuration sous Admin.
* Mise à jour du correctif : ACSD-47743.
* Correctifs remplacés : MDVA-42807.

## v1.1.22 {#v1-1-22}

* **ACSD-47444** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.3) - Correction de la variable _Tentative d’accès au décalage du tableau sur la valeur de type bool_ lors de l’accès à certains chemins de catégorie non existants pour les produits connus sous PHP 7.4.
* **ACSD-47332** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème d’échec de cron avec une erreur qui n’est signalée que lors de l’exécution entre 00:00 et 00:59 UTC.
* **ACSD-47280** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel la désactivation de la fonction de catalogue partagé sur une plage spécifique ne fonctionnait pas correctement.
* **ACSD-47106** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème qui empêchait l’enregistrement d’une valeur dans un nouvel attribut personnalisé sur la page de création d’une entreprise.
* Mise à jour du correctif : ACSD-45143.

## v1.1.21 {#v1-1-21}

* **ACSD-46809** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6) - Correction du problème qui entraînait l’erreur d’un utilisateur lors de l’attribution d’un grand nombre de sources de produits.
* **ACSD-46856** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Améliore les prix des niveaux de mise à jour des performances via Système > Configuration > Import > Advanced Tarification.
* **ACSD-46541** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.4) - Correction du problème qui empêchait un utilisateur administrateur de créer une note de crédit si un article de commande était supprimé.
* **ACSD-46581** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel le total de la taxe estimé n’est pas mis à jour après la sélection d’un pays dans le panier.
* **ACSD-46618** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel le widget de liste de produits affichait des prix en cache incorrects pour un client connecté.
* **ACSD-46674** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème d’affichage des options personnalisées d’un type d’image en tant que HTML dans les emails des clients.
* **ACSD-46988** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème en raison duquel la requête d’API &quot;devise&quot; de GraphQL renvoyait des valeurs NULL pour une devise personnalisée.
* **ACSD-47076** (pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.5) - Correction du problème de lecture des vidéos Vimeo sur le storefront.
* **ACSD-45071** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4) - Correction du problème d’ajout de la source par défaut au produit lors de l’importation.
* **AC-3023** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Mettez à jour le schéma DHL vers la dernière version 10.0.
* Correctifs mis à jour : MDVA-42584.
* Correctifs remplacés : MDVA-36572, ACSD-45241.

## v1.1.20 {#v1-1-20}

* **ACSD-46520** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.5*) : correction d’un problème en raison duquel un utilisateur obtenait un état de commande incorrect lorsqu’il était remboursé à l’aide du crédit de magasin.
* **ACSD-46703** (*pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6*) - Correction d’un problème en raison duquel il n’était pas possible de faire glisser et déposer des options personnalisées sur une page de modification de produit.
* **ACSD-44851** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6*) - Correction du problème qui empêchait l’ouverture ou le développement d’une catégorie avec des sous-catégories.
* **ACSD-46815** (*pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6*) - Correction du problème en raison duquel la requête de l’arborescence de catégories était limitée à 20 catégories.
* **ACSD-45675** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6*) - Correction du problème en raison duquel l’exportation de produits utilisait des noms de catégorie provenant de la variable *Affichage de magasin par défaut* portée.
* **ACSD-46869** (*pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6*) - Correction du problème qui empêchait la mise à jour d’un produit configurable dans un panier via un *API REST PUT* sans modifier la quantité du produit.
* **MDVA-42768-V2** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.3*) - Correction du problème en raison duquel le produit configurable affichait le prix normal comme *0* when *Afficher en rupture de stock* is *Oui*.
* Correctifs mis à jour : MDVA-44562, ACSD-46213, MDVA-41305, MDVA-38346, MDVA-13203.
* Correctif obsolète : MDVA-42768.

## v1.1.19 {#v1-1-19}

* **ACSD-46213** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.3*) - Correction du problème en raison duquel la requête de l’arborescence de catégories était limitée à 20 catégories.
* **ACSD-45781** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.2*) - Correction du problème qui empêchait l’affichage du champ de recherche avant du magasin sur mobile.
* **ACSD-46192** (*pour Adobe Commerce et Magento Open Source >=2.3.6 &lt;2.4.5*) - Correction du problème lié à l’utilisation de la variable `async/bulk/V1/configurable-products/bySku/options` point de terminaison .
* **ACSD-46404** (*pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.5*) - Correction du problème qui empêchait un utilisateur administrateur de se connecter après la mise à niveau vers la version 2.4.4.
* Correctifs mis à jour : MDVA-41305, MDVA-38626, MDVA-38728, MDVA-41061-V4, MDVA-42269, MDVA-39305.

## v1.1.18 {#v1-1-18}

* **ACSD-45817** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Correction du problème en raison duquel une mutation de produit GraphQL pour un magasin spécifique renvoyait toutes les variantes configurables, y compris celles qui n’étaient pas affectées au magasin demandé.
* **ACSD-46146** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.6*) - Correction du problème d’envoi de deux emails de confirmation de commande après le placement d’une commande de la part de l’administrateur.
* **ACSD-45255** (*pour Adobe Commerce >=2.4.3 &lt;2.4.6*) - Correction d’une exception sur la page Rapport Faible Stock pour un utilisateur administrateur restreint.
* **ACSD-45488** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6*) - Correction du problème en raison duquel un produit configurable avec plusieurs sources n’était pas automatiquement renvoyé à In Stock.
* **ACSD-45754** (*pour Adobe Commerce et Magento Open Source >=2.3.1 &lt;2.4.6*) - Correction du problème en raison duquel les points de récompense ne sont pas ajoutés après l’application d’un coupon au panier.
* **ACSD-45849** (*pour Adobe Commerce >=2.4.3 &lt;2.4.4*) - Correction du problème de perte des métadonnées vidéo après l’application d’une mise à jour intermédiaire.
* **ACSD-45257** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;2.4.4*) - Correction du problème qui empêchait GraphQL d’afficher correctement une remise au panier.
* **ACSD-44938** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.4*) - Correction du problème qui `VAT_ID` ne peut pas être appliqué dans une requête GraphQL pour un utilisateur invité.
* Correctifs mis à jour : MDVA-43417.

## v1.1.17 {#v1-1-17}

* **ACSD-45241** (*pour Adobe Commerce et Magento Open Source >=2.3.5 &lt;2.4.4*) : correction d’un problème en raison duquel la quantité en stock d’un produit virtuel était mal calculée après la création d’une note de crédit.
* **ACSD-43887** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.5*) : correction d’un problème en raison duquel des détails incorrects s’affichaient sur la page de paiement du passage en caisse lorsque les commandes d’achat pour les entreprises étaient activées.
* **ACSD-45143** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.5*) - Correction du problème en raison duquel la variable `setShippingAddressesOnCart` mutation ne permet pas de définir le code de région numérique comme *region*.
* **ACSD-44591** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.6*) - Correction de l’erreur qui se produit lorsqu’une commande est passée sans confirmation CAPTCHA.
* **ACSD-45520** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.6*) - Correction du problème en raison duquel les options d’échantillon ne sont pas présélectionnées sur la page des détails du produit lorsqu’un utilisateur modifie des produits configurables à partir du panier.
* **ACSD-45169** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.6*) - Correction du problème qui [!DNL Visual Merchandiser] n’affiche pas le stock et le prix corrects d’un produit configurable après l’application d’une mise à jour intermédiaire.
* **ACSD-45424** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;2.4.6*) - Correction du problème de création d’une compensation de réservation incorrecte après un remboursement partiel (note de crédit).
* **MDVA-42807** (*pour Adobe Commerce et Magento Open Source >=2.3.1 &lt;2.4.6*) : correction d’un problème en raison duquel le symbole de devise personnalisé ne s’affichait pas au recto du magasin.
* Correctifs mis à jour : MDVA-42689, AC-3022.

## v1.1.16 {#v1-1-16}

* **MDVA-44703** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4*) : correction d’un problème en raison duquel les totaux des commandes du rapport Commandes étaient mal calculés pour l’utilisateur administrateur restreint.
* **MDVA-44940** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4*) - Correction de l’erreur SQL qui se produisait lors de l’enregistrement de la catégorie à partir de l’administrateur.
* **MDVA-44562** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.2-p2*) - Correction du problème en raison duquel l’identifiant de magasin autre que l’identifiant par défaut pour les éléments de guillemet est remplacé par l’identifiant de magasin par défaut, en dépit de la requête GraphQL provenant de la vue de magasin autre que celle par défaut.
* **MDVA-43167** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Correction du problème en raison duquel l’action de masse de grille d’ordre d’administration ne s’appliquait pas à plusieurs pages lorsque l’utilisateur administrateur sélectionnait toutes les commandes.
* **MDVA-44044** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.2-p2*) - Correction du problème qui empêchait l’affichage d’un produit sur la page de catégorie après son affectation à un nouveau site web.
* **MDVA-42509** (*pour Adobe Commerce et Magento Open Source >=2.3.3 &lt;2.4.4*) - Correction du problème qui empêchait le téléchargement d’un fichier CSV pour un ordre rapide, ce qui entraînait une *Impossible d’envoyer le cookie* erreur.
* Correctifs mis à jour : MDVA-41061, MDVA-42584.
* Le préfixe du nouveau [!DNL Quality Patches Tool] les correctifs seront modifiés à partir de *MDVA* to *ACSD* en raison de modifications de processus internes.

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4*) - Correction du problème qui empêchait l’ajout d’un élément supplémentaire au panier lorsque la quantité minimale de l’élément était déjà dans le panier.
* **MDVA-44887** (*pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.5*) - Correction de la variable *Uncaught SyntaxError: Jeton inattendu &quot;const&quot;* dans le panneau Admin.
* **MDVA-43718** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correctifs *Le consommateur n’est pas autorisé à accéder à %resources.* s’affiche lors de l’accès à un catalogue partagé à partir d’une intégration personnalisée.
* **MDVA-44660** (*pour Adobe Commerce et Magento Open Source >=2.4.2-p1 &lt;2.4.5*) - Correction du problème en raison duquel le caractère d’accent grave ``` ` ``` n’a pas pu être utilisé pour le prénom et le nom d’un client.
* **MDVA-40896** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4*) - Correction de la variable *Erreur : TypeError : Argument 3 transmis au Magento* erreur dans l’API en bloc de produit asynchrone.
* **MDVA-38559** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.3*) - Correction de la variable */V1/customers/search API* pour les clients ayant plusieurs abonnements.
* **MDVA-44533** (*pour Adobe Commerce et Magento Open Source >=2.3.1 &lt;2.4.4*) - Correction du problème en raison duquel la remise est incorrectement appliquée à un produit enfant groupé.
* Correctifs mis à jour : MDVA-41061, MDVA-42269.

## v1.1.14 {#v1-1-14}

* **MDVA-43983** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.5*) - Correction du problème en raison duquel les produits *Non visible individuellement* apparaît toujours dans les résultats de recherche avancée du catalogue.
* **MDVA-44100** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.5*) - Correction du problème en raison duquel tous les FPT étaient affectés au dernier produit du panier et réinitialisés pour d’autres produits.
* **MDVA-43605** (*pour Adobe Commerce et Magento Open Source >=2.3.1 &lt;2.4.5*) - Correction du problème en raison duquel les données de commande renvoyaient des valeurs négatives pour les totaux des lignes lors de l’utilisation de l’API REST.
* **MDVA-43102** (*pour Adobe Commerce et Magento Open Source >=2.3.1 &lt;2.4.5*) - Correction du problème de mise à jour incorrecte de la quantité vendable lorsqu’un remboursement est effectué via l’API REST.
* **MDVA-43178** (*pour Adobe Commerce et Magento Open Source >=2.4.3-p2 &lt;2.4.5*) - Correction du problème qui empêchait la récupération d’un jeton client pour un magasin personnalisé dans GraphQL.
* **MDVA-43859** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.5*) - Correction du problème qui entraînait l’erreur *Aucune entité de ce type avec customerId =* est consigné lorsqu’un client supprimé tente de se connecter.
* **MDVA-44147** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.5*) - Correction du problème qui empêchait une requête GraphQL de renvoyer des listes de demandes d’acquisition.
* **MDVA-44505** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.3*) - Correction des problèmes en raison desquels le GraphQL Apply Reward Points ne mettait pas à jour le total général et où le crédit de magasin était appliqué plusieurs fois lors du placement de la commande.
* Correctifs mis à jour : MDVA-29148, MDVA-36464-V5, MDVA-42584, MDVA-39993-V2.

## v1.1.13 {#v1-1-13}

* **MDVA-42969** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.3*) - Correction du problème de fonctionnement de la règle de produit connexe uniquement lorsque le segment client est défini sur *Tous*.
* **MDVA-39605** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;2.4.5*) - Correction d’un problème en raison duquel la valeur TTL (date d’expiration) du cache de Redis était incorrecte.
* **MDVA-43862** (*pour Adobe Commerce et Magento Open Source >=2.3.3 &lt;2.4.5*) - Correction du problème qui empêchait le client de mettre à jour les articles du panier à cause d’un GraphQL. *mutation UpdateCartItems* erreur.
* **MDVA-43824** (*pour Adobe Commerce et Magento Open Source >=2.3.6 &lt;=2.3.7-p3 || >=2.4.1 &lt;2.4.5*) - Correction du problème d’apparition d’une erreur lors de l’annulation de commandes avec une remise.
* **MDVA-43451** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.5*) - Correction du problème qui entraînait l’erreur *Le magasin demandé n’a pas été trouvé. Vérifiez le magasin et réessayez.* s’affiche lors de la configuration d’un catalogue partagé pour un site web spécifique.
* **MDVA-43491** (*pour Adobe Commerce et Magento Open Source >=2.3.5 &lt;2.4.5*) - Correction du problème en raison duquel le libellé de l’image de base n’était pas mis à jour lors de l’importation de produits pour un site web multi-magasin.
* **MDVA-43601** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction du problème des déclencheurs manquants après la réindexation complète.
* **MDVA-42046** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;=2.3.5-p2 || >=2.4.0 &lt;2.4.5*) - Correction du problème d’attribution d’une valeur incorrecte à un attribut de produit avec un champ de saisie de date lors de la mise à jour d’un produit.
* **MDVA-43935** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.5*) - Correction du problème qui entraînait l’affichage en double d’un produit de vente par montée en gamme.
* **MDVA-44188** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.5*) - Correction du problème qui entraînait l’envoi par le système d’emails avec `.-` dans les adresses ne sont pas envoyées.
* **MDVA-42283** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) : correction d’un problème en raison duquel le format de date et d’heure dans la grille d’ordre d’administration des paramètres régionaux français n’était pas valide.
* Correctifs mis à jour : MDVA-41061-V2, MDVA-36309, MDVA-30862, MDVA-39713.
* Ajout de métadonnées de correctifs pour le [!DNL Site-Wide Analysis Tool].

## v1.1.12 {#v1-1-12}

* **MDVA-39713** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.3.6*) - Correction du problème en raison duquel l’utilisateur était en mesure de modifier l’heure de début d’une principale mise à jour planifiée.
* **MDVA-42410** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) : correction d’un problème en raison duquel les rapports de coupon n’affichaient que la devise de base par défaut.
* **MDVA-41136** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction du problème en raison duquel la date d’expiration de la variable `mage-cache-sessid` n’est pas étendue, ce qui entraîne un nettoyage des données client.
* **MDVA-39993** (*pour Adobe Commerce et Magento Open Source >=2.3.5 &lt;=2.3.7-p2 || >=2.4.0 &lt;2.4.4*) - Correction du problème en raison duquel les modifications d’inventaire effectuées par le biais de l’API ne se répercutent pas sur la page du produit sur l’interface.
* **MDVA-42855** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.5*) - Correction d’un problème en raison duquel une nouvelle adresse du client n’était pas enregistrée dans le carnet d’adresses lors du passage en caisse.
* **MDVA-42645** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.5*) - Correction du problème qui empêchait l’administrateur de rembourser les points de récompense si la fonctionnalité de stockage du crédit était désactivée.
* **MDVA-43414** (*pour Adobe Commerce et Magento Open Source >=2.3.6 &lt;=2.3.7-p2*) - Correction de l’erreur fatale PHP qui se produit lors de l’exécution de la variable `inventory.reservations.updateSalabilityStatus` client de file d’attente sur des SKU numériques.
* **MDVA-41628** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.5*) - Correction du problème en raison duquel les utilisateurs administrateurs limités existants avaient accès aux nouvelles ressources lors de l’ajout de nouveaux modules.
* **MDVA-43348** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.5*) - Correction du problème qui entraînait l’affichage d’une erreur lors de la demande GraphQL de carte-cadeau si `gift_card_options` contain *uid*.
* **MDVA-39546** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction du problème en raison duquel la date de début de la mise à jour intermédiaire pouvait être définie sur une date antérieure à la date actuelle lors de la modification.
* **MDVA-42950** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction du problème de lecture des vidéos sur la page du produit.
* **MDVA-42689** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction du problème qui entraînait le lancement d’une *Violation des contraintes d’intégrité* lors de la mise à jour des catégories de produits lors de l’importation.
* **MDVA-41229** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction du problème qui empêchait l’affichage des images disponibles sur le serveur principal après l’importation de produits configurables.
* **MDVA-43731** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4*) - Correction du problème qui *Synonymes de recherche* ne fonctionne plus lorsque la valeur ajoutée dans *Termes minimum à faire correspondre*.
* **MDVA-43232** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;2.4.5*) - Correction du problème de tri des produits dans [!DNL Visual Merchandiser] par Prix spécial au bas/en haut provoque une erreur lors de l’enregistrement de la catégorie.
* **MDVA-43726** (*pour Adobe Commerce et Magento Open Source >=2.3.3 &lt;2.4.3*) - Correction du problème en raison duquel la règle de prix du catalogue basée sur la correspondance des attributs au niveau du magasin ne s’appliquait pas après une réindexation partielle.
* Correctifs mis à jour : MDVA-36464, MDVA-37478, MDVA-38608.
* Ajout de métadonnées de correctifs pour le [!DNL Site-Wide Analysis Tool].

## v1.1.11 {#v1-1-11}

* **MDVA-42790** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.5*) - Correction du problème en raison duquel les attributs de prix de produit ne pouvaient pas être mis à jour pour un site web spécifique via l’API REST.
* **MDVA-41350** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction d’un problème en raison duquel une exception était générée lorsqu’un utilisateur administrateur disposant d’un accès limité ajoute un produit en dehors de la portée de son rôle par SKU dans une commande.
* **MDVA-42269** (*pour Adobe Commerce et Magento Open Source >=2.4.3-p1 &lt;2.4.5*) - Correction du problème qui empêchait un utilisateur administrateur de se connecter à l’administrateur en raison de la variable *TypeError : strtotime() exige que le paramètre 1 soit une chaîne, null étant donné* erreur.
* **MDVA-40830** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction du problème en raison duquel le crédit de magasin était appliqué plusieurs fois lors de l’emplacement de la commande.
* **MDVA-42237** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.5*) - Correction du problème qui empêchait la mise à jour du prix spécial d’un produit configurable après modification du prix de son sous-produit.
* **MDVA-42520** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4*) - Correction du problème en raison duquel le taux de taxe était appliqué deux fois si la variable *Activer le commerce transfrontalier* est utilisée.
* Correctifs mis à jour : MDVA-27239, MDVA-39305, MDVA-41236, MDVA-36832.
* Correctif obsolète : MDVA-37725.

## v1.1.10 {#v1-1-10}

* **MDVA-38728** (*pour Adobe Commerce et Magento Open Source >=2.3.2 &lt;2.4.5*) - Correction d’un problème en raison duquel la mise à jour en masse des attributs crée une réécriture de l’URL pour le magasin par défaut uniquement après modification. *Visibilité du produit*.
* **MDVA-43091** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4*) - Correction du problème qui entraînait l’erreur lors de la commande d’un produit en bundle auprès de l’administrateur dans le serveur principal. *Vous ne pouvez pas utiliser de quantité décimale pour ce produit.*.
* **MDVA-40816** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction du problème en raison duquel les règles de produit associées affichaient des produits de catégories non définies dans les conditions de règle.
* **MDVA-41305** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.5*) : correction d’un problème en raison duquel la mutation de GraphQL ne renvoyait pas d’options de produit configurables après l’avoir ajouté à la liste des souhaits.
* **MDVA-39181** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.5*) - Correction du problème en raison duquel les règles de produit associées affichaient des produits de catégories non définies dans les conditions de règle.
* **MDVA-42584** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.3*) - Correction du problème en raison duquel l’état du stock configurable dans le serveur principal n’était pas mis à jour après la modification de l’état du stock et de la quantité via l’importation ou l’API.
* **MDVA-40175** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.3*) - Correction du problème qui *Cliquez pour modifier le mode de livraison.* n’affiche pas de boutons radio pour sélectionner les méthodes de livraison dans l’Admin lors de la réorganisation.
* **MDVA-42768** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;2.4.5*) - Correction du problème en raison duquel le prix normal du produit configurable était de 0 lorsque *Afficher en rupture de stock* est Oui.
* **MDVA-43201** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Correction du problème d’erreur lors de la connexion du client lors de l’utilisation de l’attribut DOB avec certains paramètres régionaux.
* Correctifs mis à jour : MDVA-35092, MDVA-33970.

## v1.1.9 {#v1-1-9}

* **MDVA-38346** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction du problème de dysfonctionnement des filtres de dates lorsque le fuseau horaire Adobe Commerce est différent du fuseau horaire de l’environnement local.
* **MDVA-42657** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.5*) - Correction du problème qui empêchait l’utilisateur administrateur de sélectionner des catégories dans les conditions de segment du client.
* **MDVA-42806** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Correction du problème en raison duquel une *Enregistrement d’une nouvelle société* un email est envoyé chaque fois qu’une société existante est mise à jour via l’API REST.
* **MDVA-37984** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.5*) - Correction du problème en raison duquel la variable [!DNL Visual Merchandiser] *Faire correspondre le produit par règle* ne filtre pas correctement les produits avec des mises à jour intermédiaires.
* **MDVA-40488** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Correction du problème en raison duquel les produits configurables avec des produits enfants en rupture de stock ne s’affichaient pas dans la plage de prix correcte.
* **MDVA-42507** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.5*) - Correction du problème de nettoyage du cache de la page entière après l’application de la mise à jour intermédiaire pour la règle de panier.
* **MDVA-39163** (*pour Adobe Commerce et Magento Open Source >=2.3.5 &lt;2.4.5*) - Correction du problème en raison duquel les méthodes d’expédition n’étaient pas disponibles lorsqu’un nouvel utilisateur était enregistré et que les produits du panier provenaient de la session d’invité.
* **MDVA-38626** (*pour Adobe Commerce et Magento Open Source >=2.3.3 &lt;2.4.5*) - Correction du problème qui empêchait l’utilisateur administrateur de passer une commande sur le serveur principal à l’aide de la variable [!DNL PayPal Payflow Pro] paiement.
* **MDVA-38666** (*pour Adobe Commerce et Magento Open Source >=2.3.2 &lt;2.3.6*) - Correction du problème qui empêchait l’utilisateur administrateur de modifier les options de produit configurables dans le panier du client.
* **MDVA-38526** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.4*) - Correction du problème qui empêchait l’utilisateur administrateur d’accéder à la variable [!DNL Site-Wide Analysis tool].
* Correctifs mis à jour : MDVA-40101.

## v1.1.8 {#v1-1-8}

* **MDVA-41215** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction du problème en raison duquel les utilisateurs obtenaient l’erreur 500 après avoir défini la variable *mage-messages* s’il existe déjà, mais qu’il n’y a aucun nouveau message.
* **MDVA-41139** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4*) - Correction du problème en raison duquel les produits configurables étaient en rupture de stock après l’importation du produit lorsqu’une quantité=0 d’un produit simple était utilisée pour l’une de ses sources.
* **MDVA-42326** (*pour Adobe Commerce et Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Correction du problème qui entraînait une erreur des clients lors de leur passage en caisse après un délai d’expiration de session, même si le panier persistant était activé.
* **MDVA-42341** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Correction du problème en raison duquel la variable `categoryList` La requête GraphQL ne filtre pas les résultats si une requête comporte l’en-tête Magasin .
* **MDVA-38393** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction du problème qui empêchait les règles du catalogue de fonctionner pour un produit configurable si son produit simple était renommé.
* **MDVA-39153** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) : correction d’un problème en raison duquel un montant de remise n’était pas correctement calculé lors d’une réorganisation dans l’Admin.
* Correctifs mis à jour : MDVA-28993, MDVA-41061, MDVA-35984.

## v1.1.7 {#v1-1-7}

* **MDVA-39711** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.3*) - Correction du problème qui empêchait les utilisateurs administrateurs d’accéder à la grille du client après avoir supprimé le site web.
* **MDVA-40311** (*pour Adobe Commerce et Magento Open Source >=2.4.2-p2 &lt;2.4.4*) - Correction du problème en raison duquel les utilisateurs administrateurs recevaient le message d’erreur *Sécurité ou clé de formulaire non valide. Actualisez la page.* après vous être connecté à l’administrateur si le chemin d’accès d’administrateur personnalisé est configuré et que la clé secrète est activée.
* **MDVA-41631** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.4*) - Correction du problème qui entraînait une erreur des utilisateurs lorsqu’ils tentaient de récupérer des informations de commande sans option. *telephone* via GraphQL.
* **MDVA-27239** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.3.6*) - Correction du problème qui empêchait l’affichage des produits de vente croisée.
* Correctifs mis à jour : MDVA-37068, MDVA-35254, MDVA-41164, MDVA-37916, MDVA-37478, MDVA-34551, MDVA-31791.

## v1.1.6 {#v1-1-6}

* **MDVA-40550** (*pour Adobe Commerce et Magento Open Source >=2.3.5 &lt;2.4.4*) - Correction du problème lié aux produits manquants sur le front-end lors de la réindexation.
* **MDVA-40120** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.4*) - Correction du problème en raison duquel le tri GraphQL par DESC/ASC ne fonctionne pas avec des produits ayant la même pertinence ou le même prix.
* **MDVA-41399** (*pour Adobe Commerce et Magento Open Source >=2.3.3 &lt;2.4.2*) - Correction du problème qui empêchait les utilisateurs administrateurs d’accéder à la variable *Gérer le panier* si un client ajoute un produit à la liste des souhaits.
* **MDVA-40609** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.3*) - Correction du problème d’absence des données de produits désactivées dans la variable `cataloginventory_stock_status` table d’index, affichant des quantités de produits désactivées incorrectes.
* **MDVA-39031** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.4*) - Correction du problème qui rendait possible l’ajout d’un produit au panier via GraphQL, même s’il n’est pas affecté au site web cible.
* **MDVA-41597** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Correction du problème qui entraînait une erreur des utilisateurs lors de l’ajout de plusieurs produits configurables au panier à l’aide de GraphQL.
* **MDVA-27456** (*pour Adobe Commerce et Magento Open Source >=2.3.5 &lt;2.3.7*) - Correction d’un problème en raison duquel les utilisateurs obtenaient une erreur lors d’une tentative de chargement. [!DNL Swagger].
* **MDVA-32776** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.2*) - Correction du problème de non-mise à jour de l’état du stock lorsqu’une commande est passée mais n’est pas expédiée.
* **MDVA-30862** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;2.4.0*) - Correction du problème lié à une date de commande incorrecte sur la facture PDF imprimée.
* Amélioration de la page d’index pour la variable [!DNL Quality Patch Tool]. Ajout d’une recherche et d’un filtrage pratiques pour [!DNL quality patches] à la dernière version de l’outil.
* Correctifs mis à jour : MDVA-33382, MDVA-39482.

## v1.1.5 {#v1-1-5}

* **MDVA-41236** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction du problème qui rendait impossible la création ou la modification d’une mise à jour planifiée existante pour un produit si la Date de fin a été supprimée précédemment.
* **MDVA-41046** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction du problème en raison duquel des produits simples avec des options personnalisées étaient disponibles pour l’affectation à des produits configurables/regroupés.
* **MDVA-40545** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction du problème en raison duquel seul le premier noeud d’une page était récupéré même s’il existait plusieurs noeuds pour la même page.
* **MDVA-41164** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.3-p1*) - Correction du problème qui empêchait un utilisateur administrateur d’enregistrer ou de modifier une société avec un attribut client personnalisé de type fichier ou image.
* **MDVA-39229** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction du problème qui entraînait l’affichage de l’erreur suivante après la mise à jour de l’heure de début de mise à jour de la règle de catalogue intermédiaire : *Cron Job staging_synchronize_entities_period présente une erreur : La principale mise à jour ne peut pas être supprimée.*
* **MDVA-40619** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction du problème qui entraînait une erreur 500 lors de la tentative de modification en ligne d’une page CMS suite à des modifications apportées à la hiérarchie de la page CMS.
* **MDVA-41061** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.3*) - Correction du problème de réinitialisation de l’état du stock sur vendable lorsqu’un produit est enregistré depuis l’administrateur.
* **MDVA-31763** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction du problème en raison duquel les règles de prix du catalogue étaient restaurées (ou non appliquées) jusqu’à la réindexation manuelle.
* **MDVA-37748** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.3*) - Correction du problème en raison duquel une requête GraphQL renvoyait des produits non attribués à un catalogue partagé.

## v1.1.4 {#v1-1-4}

* **MDVA-40399** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) : correction d’un problème en raison duquel les factures partielles d’une même commande ne pouvaient pas être créées simultanément via l’API REST.
* **MDVA-40101** (*pour Adobe Commerce et Magento Open Source >=2.3.2 &lt;2.4.0*) - Correction du problème en raison duquel les articles ne sont pas supprimés du mini panier après un placement de commande réussi à l’aide de la commande [!DNL PayPal Express] Passage en caisse.
* **MDVA-40401** (*pour Adobe Commerce et Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) : correction du problème en raison duquel la valeur d’utilisation des coupons changeait même si le placement d’une commande échouait.
* **MDVA-40537** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;=2.4.0-p1*) - Correction du problème qui entraînait une erreur lors de la création d’une vue de magasin si plusieurs pages CMS avec la même clé d’URL existaient.
* **MDVA-37725** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;=2.4.3-p1*) - Correction du problème en raison duquel les courriers électroniques de commande asynchrones envoyés à partir de sites web autres que les sites par défaut contenaient des URL de logo provenant du site web par défaut.
* **MDVA-39482** (*pour Adobe Commerce et Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Correction du problème de rupture de stock d’un produit importé avec une quantité &quot;0&quot; lorsque les commandes en arrière-plan étaient activées.
* **MDVA-40435** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;2.4.4*) : corrige le problème lié à une remise incorrecte sur les produits en bundle avec des prix dynamiques lorsqu’ils sont appliqués via GraphQL.
* **MC-42528** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;=2.4.3-p1*) - Correction du problème en raison duquel la variable `categoryList` La requête GraphQL renvoie les catégories affectées et non affectées.
* **MDVA-29400** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;=2.3.7-p1 || >=2.4.0 &lt;=2.4.0-p1*) - Correction du problème lié aux commandes dupliquées placées avec [!DNL PayPal Express Checkout].
* **MDVA-26005** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;=2.3.5-p2*) - Correction du problème qui rendait impossible la sélection d’une catégorie dans une arborescence de catégories pour les conditions des règles de prix du panier.
* **MDVA-25631** (*pour Adobe Commerce et Magento Open Source >=2.3.3 &lt;=2.3.5-p2*) : améliore les performances pour la modification et l’enregistrement des segments de clients qui contiennent un grand nombre de clients.

## v1.1.3 {#v1-1-3}

* **MDVA-40262** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Correction du problème qui empêchait l’affichage des requêtes de recherche GraphQL dans les termes de recherche courants dans l’Admin.
* **MDVA-40601** (*pour Adobe Commerce et Magento Open Source >=2.3.1 &lt;=2.4.2-p2*) - Correction du problème qui entraînait une erreur des utilisateurs lorsqu’ils tentaient d’obtenir des informations sur la catégorie modifiée par une mise à jour planifiée via GraphQL.
* **MDVA-37234** (*pour Adobe Commerce et Magento Open Source >=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*) - Correction du problème en raison duquel l’ajout d’un élément au panier plusieurs fois (requête parallèle) pour le même SKU créait une ligne en double pour le même ID de panier.
* **MDVA-33606** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;=2.4.2-p2*) - Correction du problème qui entraînait l’obtention d’un *Violation des contraintes uniques* lors de l’enregistrement d’une page CMS affectée à une hiérarchie.
* **MDVA-31590** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;=2.4.1-p1*) - Correction du problème qui empêchait les utilisateurs de mettre à jour les attributs en masse à l’aide des files d’attente asynchrones MySQL.
* **MDVA-36309** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Correction du problème de lenteur de la recherche de produits par attributs dans les grilles d’administration.

## v1.1.2 {#v1-1-2}

* **MDVA-38929** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) : correction d’un problème en raison duquel la facture avec FPT affichait un total général incorrect lorsque la commande était payée à partir du crédit de la boutique.
* **MDVA-37364** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;=2.4.3*) - Correction du problème en raison duquel l’attribut client personnalisé de type date rompt l’interface utilisateur de grille du client.
* **MDVA-39195** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Correction du problème qui *Ajouter au panier* était inactif sur la page de catégorie lorsque la redirection vers le panier était activée.
* **MDVA-37115** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Correction du problème en raison duquel une *Seulement 0 gauche* l’avis s’affiche sur la page produit configurable.
* **MDVA-39521** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.4*) - Correction du problème qui empêchait l’utilisateur de définir des adresses de livraison sur le panier avec un numéro de téléphone vide via GraphQL.
* **MDVA-39384** (*pour Adobe Commerce et Magento Open Source >=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*) - Correction du problème qui empêchait l’enregistrement de l’attribut client personnalisé pour un utilisateur de la société.
* **MDVA-39043** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;=2.4.3*) - Correction du problème qui entraînait une erreur lors de l’ajout de la variable *Produits* sur la page CMS.
* **MDVA-39966** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*) - Correction du problème lié au déploiement de paramètres régionaux incorrects.
* **MDVA-38852** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;=2.3.5-p2*) - Correction du problème en raison duquel l’inventaire des catalogues par conception verrouillait les tableaux pour les mises à jour qui diminuaient considérablement les performances dans les cas de plusieurs commandes parallèles.
* **MDVA-39986** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.3*) - Correction du problème qui empêchait l’utilisateur de passer une commande dans Admin on MacOS à l’aide du navigateur Safari.
* **MDVA-38447** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Correction de deux problèmes : où le *Non visible individuellement* les produits enfants configurables sont renvoyés dans la réponse GraphQL et optimisent la requête de produits MySQL pour GraphQL avec filtre de catégorie.
* **MDVA-40134** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.3*) - Correction du problème en raison duquel GraphQL ne renvoyait aucun produit associé lorsque le catalogue partagé était activé.
* **MDVA-39935** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.4*) - Correction du problème en raison duquel GraphQL renvoyait des produits enfants configurables désactivés au niveau du site web.

## v1.1.1 {#v1-1-1}

* **MDVA-36021** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.4*) - Correction du problème en raison duquel la variable *Appel à une fonction membre getId()* s’affiche sur la page des détails de la commande dans Admin.
* **MDVA-34948** (*pour Adobe Commerce et Magento Open Source >=2.3.6 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.0-p1*) - Correction du problème lié aux requêtes longues, comme `GET_LOCK`.
* **MDVA-39305** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;=2.4.2-p1*) - Correction du problème qui empêchait les clients enregistrés de se connecter avec Google ReCaptcha activé.
* **MDVA-37897** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction d’un problème lié à une redirection incorrecte lorsqu’un client tente d’ajouter des produits avec des options du widget Récemment consultés.

## v1.1.0 {#v1-1-0}

* Des catégories de correctifs ont été introduites afin d’améliorer l’expérience utilisateur et de faciliter la recherche des correctifs requis pour les clients.
* Le `patches.json` a été renommé `support-patches.json`.
* **MDVA-38799** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Correction du problème en raison duquel les produits téléchargeables n’étaient pas enregistrés après la création d’une mise à jour intermédiaire.
* **MDVA-37592** (*pour Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - Correction du problème en raison duquel le tri par prix ne fonctionne pas correctement pour les produits dont le prix zéro est affecté au catalogue partagé.
* **MDVA-38827** (*pour Adobe Commerce >=2.3.3-p1 &lt;2.4.4*) - Correction du problème qui entraînait la réception par les clients d’un courrier électronique d’expédition de commande contenant un message d’erreur.

## v1.0.26 {#v1-0-26}

* **MDVA-38468** (*pour Adobe Commerce >=2.3.2 &lt;=2.3.5-p2*) - Correction de l’erreur lors de l’enregistrement des pages CMS : *L’élément avec le même ID PAGE_ID existe déjà*.
* **MDVA-34680** (*pour Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;2.4.3*) - Correction du problème de l’heure de création du compte client qui n’était pas correctement filtrée dans la grille des clients.
* **MDVA-37068** (*pour Adobe Commerce >=2.3.1 &lt;2.4.4*) : correction d’un problème en raison duquel un taux d’imposition incorrect s’affichait lorsque le panier ne contenait que des produits virtuels.
* **MDVA-38608** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Correction du problème de suppression des tables temporaires lorsque la réindexation n’est pas terminée.
* **MDVA-38308** (*pour Adobe Commerce >=2.3.5 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.1-p1 || >=2.4.2 &lt;2.4.4*) - Correction des problèmes liés à l’ajout de [!DNL Vimeo] des vidéos aux produits.

## v1.0.25 {#v1-0-25}

* **MDVA-37916** (*pour Adobe Commerce >=2.3.6 &lt;2.4.3*) - Correction du problème qui empêchait le client d’accéder à la page de confirmation du paiement lors de l’utilisation de la variable [!DNL Paypal Payment Advanced] .
* **MDVA-37082** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Correction du problème qui se produisait lors de l’enregistrement du stock personnalisé de produits groupés pour que le produit s’affiche en rupture de stock dans le front-end.
* **MDVA-36572** (*pour Adobe Commerce >=2.3.5 &lt;2.4.3*) - Correction du problème en raison duquel les mises à jour Mémo de crédit ne provoquaient plus de mises à jour de réservation de produits en double dans la base de données.
* **MDVA-38132** (*pour Adobe Commerce >=2.3.3 &lt;2.4.3*) - Correction du problème qui se produisait lorsque le panneau d’administration n’était pas accessible en raison d’un événement *trop de redirections* erreur.
* **MDVA-38270** (*pour Adobe Commerce >=2.4.1 &lt;2.4.3*) - Correction du problème lié à l’absence d’informations sur les cartes cadeau dans le total de la commande dans GraphQL.

## v1.0.24 {#v1-0-24}

* **MDVA-37779** (*pour Adobe Commerce >=2.4.2 &lt;=2.4.4*) - Correction du problème lié à l’ajout d’un produit configurable au panier via GraphQL lorsque l’ID de site web ne correspond pas à l’ID de magasin.
* **MDVA-36832** (*pour Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - Correction du problème de duplication des images sur les pages lorsque la largeur d’affichage est de 768 px.
* **MDVA-37874** (*pour Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;=2.4.2-p1*) - Correction du problème qui *Montant de remise fixe pour le panier entier* s’applique incorrectement à un produit groupé contenant plusieurs options.
* **MDVA-37913** (*pour Adobe Commerce >=2.3.0 &lt;=2.4.0-p1*) - Correction du problème de disparition des liens téléchargeables si le produit téléchargeable était mis à jour via l’API.
* **MDVA-34330** (*pour Adobe Commerce >=2.3.1 &lt;=2.4.2-p1*) - Correction du problème en raison duquel les commandes de la grille Commandes ne sont pas filtrées selon le fuseau horaire de l’administrateur.

## v1.0.23 {#v1-0-23}

* **MDVA-37478** (*pour Adobe Commerce >=2.3.0 &lt;=2.3.7*) - Correction d’un problème en raison duquel Adobe Commerce générait une erreur lors de la création d’une facture partielle pour les commandes passées avec la variable *Paiement sur compte* mode de paiement via l’API REST.
* **MDVA-37362** (*pour Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - Correction du problème en raison duquel les valeurs des options de produit configurables et les valeurs d’attribut de variante étaient vides dans la réponse GraphQL.
* **MDVA-37288** (*pour Adobe Commerce 2.4.2*) - Correction du problème en raison duquel des prix de niveau incorrects étaient renvoyés après la demande GraphQL.
* **MDVA-37225** (*pour Adobe Commerce >=2.4.1 &lt;=2.4.2-p1*) - Correction du problème de blocage du processus de chargement lors de la création rapide d’un ordre lorsqu’il existe une valeur entière dans les SKU importés.
* **MDVA-37224** (*pour Adobe Commerce >=2.3.3 &lt;=2.4.2-p1*) - Correction du problème en raison duquel les clients ne pouvaient pas payer pour un devis négociable avec [!DNL PayFlow Pro] avec un autre produit dans le panier.
* **MDVA-36286** (*pour Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - Correction du problème de coupure de l’aperçu du widget des produits Page Builder lorsque le même SKU occupe une position différente dans les sous-catégories.
* **MDVA-30186** (*pour Adobe Commerce >=2.3.4 &lt;=2.3.5-p2, >=2.4.0 &lt;=2.4.0-p1, >=2.4.2 &lt;=2.4.2-p1*) - Correction du problème en raison duquel les options d’attribut étaient triées par valeur d’option au lieu du nombre d’éléments d’attribut dans la réponse GraphQL.

## v1.0.22 {#v1-0-22}

* **MDVA-36718** (*pour Adobe Commerce >=2.3.0 &lt;=2.4.2*) - Correction du problème en raison duquel les anciennes options personnalisées restaient après avoir été modifiées via l’API.
* **MDVA-35773** (*pour Adobe Commerce >=2.3.6 &lt;=2.3.6-p1 || >=2.4.1 &lt;=2.4.2*) - Correction du problème en raison duquel le total général n’était pas affiché comme zéro sur la facture pour les commandes avec une remise de 100 %.
* **MDVA-36833** (*pour Adobe Commerce 2.4.2*) - Correction du problème lié aux résultats de recherche qui affichaient un nombre aléatoire de produits par page après l’exclusion de certains produits du catalogue partagé.
* **MDVA-37182** (*pour Adobe Commerce >=2.4.1 &lt;=2.4.2*) - Correction du problème lié à l’obtention de résultats de recherche incorrects dans les deux [!DNL Elasticsearch] version 6 et version 7.
* **MDVA-36253** (*pour Adobe Commerce >=2.4.0 &lt;=2.4.1-p1*) : correction du problème en raison duquel un sous-total incorrect s’affichait dans le mini panier après la suppression d’un article.
* **MDVA-36853** (*pour Adobe Commerce 2.4.2*) - Correction du problème en raison duquel aucune image n’apparaissait lors du chargement de galeries multimédia volumineuses.

## v1.0.21 {#v1-0-21}

* **MDVA-34665** (*pour Adobe Commerce >=2.3.4 &lt;=2.3.4-p2*) - Correction du problème lié aux produits regroupés manquants sur les pages de catégories.
* **MDVA-36615** (*pour Adobe Commerce 2.4.2*) - Correction du problème lié à un nombre de produits incorrect dans la grille de produits Admin .
* **MDVA-36464** (*pour Adobe Commerce >=2.4.0 &lt;=2.4.2*) - Correction du problème de dysfonctionnement de la configuration des notifications électroniques au niveau de l’affichage en magasin.
* **MDVA-36138** (*pour Adobe Commerce ^2.3.2*) - Correction d’un problème en raison duquel le prix de livraison n’était pas ajusté et le prix de livraison complet était présenté aux clients si tous les articles du panier ne remplissaient pas les critères de la règle du panier de livraison gratuit.
* **MDVA-36424** (*pour Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 || >=2.0.0 &lt;2.2.0*) - Correction du problème de disparition des images multimédia associées aux éléments du créateur de pages lorsque le contenu est modifié à plusieurs reprises si l’URL de base du serveur principal est différente de l’URL de base du storefront.
* **MDVA-35984** (*pour Adobe Commerce ^2.4.0*) - Correction du problème lié à une quantité de produit et une quantité vendable incorrectes après la création de plusieurs envois simultanés pour le même produit.

## v1.0.20 {#v1-0-20}

* **MDVA-36170** (*pour Adobe Commerce >=2.3.4 &lt;2.4.2*) - Ceci corrige le problème en raison duquel la requête GraphQL n’était pas mise en cache à l’aide de la balise de cache de catégorie.
* **MDVA-33168** (*pour Adobe Commerce >=2.3.3 &lt;2.4.2*) - Correction du problème lors de la mise à jour d’un attribut de produit via l’API, tous les autres attributs passant à une valeur vide.
* **MDVA-19640** (*pour Adobe Commerce >=2.3.0*) - Correction du problème qui [!DNL Advanced Reporting] n’affiche aucune donnée.
* **MDVA-11189** (*pour Adobe Commerce >=2.3.0 &lt;2.3.5*) - Correction du problème qui se produisait lors de l’importation d’un fichier CSV pour mettre à jour le stock de produits (lignes du `cataloginventory_stock` sont supprimées.
* **MDVA-26639** (*pour Adobe Commerce >=2.3.3-p1 &lt;2.3.6*) : correction d’un problème en raison duquel, si un modèle d’email de confirmation de commande était créé, les éléments de commande manquaient dans le courrier électronique de commande.
* **MDVA-15546** (*pour Adobe Commerce >=2.3.0*) - Correction du problème qui, après la création d’une commande, *Column entity_id où la clause est ambiguë* s’affiche dans le journal des exceptions.
* **MDVA-21095** (*pour Adobe Commerce >=2.3.0 &lt;2.3.5*) - Correction du problème lors d’une requête `INSERT INTO search_tmp` ne se terminera pas après la mise à jour de la valeur d’attribut de masse.
* **MDVA-23845** (*pour Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - Correction du problème en raison duquel les modèles d’email ne pouvaient pas être prévisualisés une fois la minification JavaScript activée.
* **MDVA-22026** (*pour Adobe Commerce >=2.3.2 &lt;2.3.4*) - Correction du problème d’échec de l’importation de produits à partir d’un fichier CSV, y compris des images provenant d’URL externes.
* **MDVA-22383** (*pour Adobe Commerce >=2.3.0 &lt;2.3.4*) : correction d’un problème en raison duquel l’enregistrement d’un produit prenait beaucoup de temps et les sauts de page.
* **MC-41359** (*pour Adobe Commerce >=2.3.6-p1 &lt;2.3.7, >=2.4.2 &lt;2.4.3*) - Correction du problème des paramètres de cookie SameSite incorrects.

## v1.0.19 {#v1-0-19}

* **MDVA-33614** (*pour Adobe Commerce 2.4.1*) - Correction du problème de renvoi de l’erreur suivante par le Créateur de pages : *Une erreur s’est produite lors du lancement du créateur de pages. Veuillez consulter votre contact du support technique.*
* **MDVA-35356** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Correction du problème lié à un retour de crédit de magasin incorrect après l’annulation de commande partiellement facturée.
* **MDVA-33289** (*pour Adobe Commerce >=2.4.0 &lt;2.4.3*) - Correction du problème d’affichage du code JavaScript brut dans l’interface utilisateur de l’adresse de facturation lors de l’extraction si [!DNL Google Tag Manager] est activée.
* **MDVA-35982** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) : correction d’un problème en raison duquel les utilisateurs administrateurs limités à un site web spécifique ne pouvaient pas créer d’envoi pour la commande passée sur le même site web.
* **MDVA-35155** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6*) - Correction du problème qui rendait impossible l’achat d’un produit en regroupement si le titre de l’option était modifié.
* **MDVA-35910** (*pour Adobe Commerce >=2.4.1 &lt;2.4.3*) - Correction du problème qui rendait impossible la création d’un nouveau compte client après la désactivation de la fonctionnalité Se connecter en tant que client .
* **MDVA-34474** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Correction du problème lors de l’ajout d’un produit à la liste des demandes à l’aide de l’API .
* **MDVA-34591** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Correction d’un problème lié à un mauvais calcul de remise de règle de panier pour *Remise de qualité maximale appliquée à* et *Étape de qualité de remise (Buy X)*.
* **MDVA-33704** (*pour Adobe Commerce >=2.4.0 &lt;2.4.3*) - Correction du problème en raison duquel la variable *Saut en magasin* l’option d’expédition ne s’affiche pas, bien que configurée pour être disponible.
* **MDVA-34928** (*pour Adobe Commerce >=2.3.5 &lt;2.3.5-p2*) - Correction du problème d’affichage indéfini du chargeur de page après la suppression du crédit de magasin du paiement.
* **MDVA-35254** (*pour Adobe Commerce >=2.3.1 &lt;2.4.3*) - Correction des problèmes liés à CAPTCHA lors de l’extraction.
* **MDVA-35569** (*pour Adobe Commerce >=2.3.4 &lt;2.4.2*) - Correction du problème en raison duquel la variable *taxes sur les produits fixes* n’est pas renseigné dans la réponse GraphQL lorsque l’état est spécifié.
* **MDVA-35847** (*pour Adobe Commerce >=2.4.1 &lt;2.4.3*) - Correction du problème B2B qui se produisait lorsque le formulaire Utilisateurs de l’entreprise était rompu si un attribut client personnalisé était utilisé.
* **MDVA-31307** (*pour Adobe Commerce >=2.4.0 &lt;2.4.2*) - Correction du problème en raison duquel *Mémoire insuffisante* des erreurs sur certaines catégories en raison de problèmes liés à l’liste autorisée dynamique CSP pour les blocs mis en cache.

## v1.0.18 {#v1-0-18}

* **MDVA-32655** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) : corrige les erreurs *en cours* l’état du message à la valeur correcte ; *complete* message pour les consommateurs `quoteItemCleaner` après la suppression de plusieurs produits.
* **MDVA-34102** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) : fixe la quantité de Stock par défaut à zéro pour les produits désactivés sur les pages Grille de produits et Modifier le produit dans la zone d’administration.
* **MDVA-35286** (*pour Adobe Commerce >=2.4.0 &lt;2.4.2*) - Correction du problème en raison duquel une erreur se produisait lorsqu’un client regroupait des produits dans le panier et passait de l’extraction à l’extraction sur une seule page.
* **MDVA-35312** (*pour Adobe Commerce >=2.4.1-p1 &lt;2.4.2*) - Correction du code de réponse 500 lorsqu’une requête GraphQL vide.
* **MDVA-34189** (*pour Adobe Commerce >=2.3.4 &lt;2.4.3*) - Correction du délai d’expiration du premier octet de 503 sur . [!DNL Visual Merchandiser] requêtes lors du chargement de la page Catégorie d’administration .
* **MDVA-34695** (*pour Adobe Commerce >=2.3.0 &lt;2.4.1*) - Correctifs négatifs `children_count` après suppression des catégories.

## v1.0.17 {#v1-0-17}

* **MDVA-34012** (*pour Adobe Commerce >=2.3.1 &lt;2.4.3*) - Correction du problème en raison duquel la variable *Utiliser la valeur par défaut* est effacée une fois les modifications planifiées appliquées. Le problème apparaît une fois que les modifications planifiées ne sont plus en vigueur.
* **MDVA-35064** (*pour Adobe Commerce >=2.3.3 &lt;2.4.3*) - Correction du problème en raison duquel les réécritures d’URL ne sont pas générées pour les produits configurables créés via l’API.
* **MDVA-34943** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) : correction d’un problème en raison duquel l’ordre rapide mettait en cache les SKU précédemment saisis.
* **MDVA-35197** (*pour Adobe Commerce >=2.3.5 &lt;2.4.0*) - Correction d’un problème qui entraînait une erreur lors de l’ajout au panier à l’aide de GraphQL si des produits précédemment ajoutés devenaient en rupture de stock.
* **MDVA-34850** (*pour Adobe Commerce >=2.3.1 &lt;2.4.0*) - Correction du problème en raison duquel les options en rupture de stock d’un produit configurable ne s’affichaient pas au lieu d’être affichées comme étant ponctuelles.
* **MDVA-34867** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Correction du problème qui empêchait l’enregistrement des valeurs d’un champ de condition défini pour une mise à jour planifiée.
* **MDVA-35092** (*pour Adobe Commerce >=2.3.5 &lt;2.4.3*) - Correction du problème qui empêchait les utilisateurs d’ajouter [!DNL Vimeo] vidéos en raison d’un abandon [!DNL Vimeo] API.

## v1.0.16 {#v1-0-16}

* **MDVA-33453** (*pour Adobe Commerce >=2.3.6 &lt;2.4.3*) - Correction du problème de coupure de l’aperçu du type de contenu de produits du créateur de pages si les produits correspondants avaient des prix différents pour chaque site web.
* **MDVA-32634** (*pour Adobe Commerce ^2.3.1*) - Correction du problème en raison duquel la variable `url_path` de la catégorie affectée à tous les magasins reste inchangée après le déplacement de la catégorie dans la hiérarchie.
* **MDVA-33344** (*pour Adobe Commerce ^2.3.0*) - Correction du problème de codage en dur `rma_item` L’identifiant du jeu d’attributs par défaut de l’entité est utilisé à la place de la valeur de la base de données.
* **MDVA-34192** (*pour Adobe Commerce >=2.3.4 &lt;2.4.3*) - Correction du problème qui empêchait de modifier/spécifier la date de naissance du client au format jj/mm/aaaa.
* **MDVA-34847** (*pour Adobe Commerce ^2.3.0*) - Correction de la conversion de type ID de magasin en entier pour les conditions SQL dans les collections d’administrateurs pour les utilisateurs administrateurs disposant d’autorisations personnalisées.
* **MDVA-34886** (*pour Adobe Commerce ^2.3.2*) - Correction du problème en raison duquel la recherche ne renvoyait aucun résultat si *poids* l’attribut product est configuré comme pouvant faire l’objet d’une recherche.

## v1.0.15 {#v1-0-15}

* **MDVA-33559** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Correction du problème de [!DNL PayPal Payflow Pro] échec de paiement avec erreur de format de liste des paramètres de redirection.
* **MDVA-34023** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Correction du problème qui entraînait l’erreur *Aucune entité de ce type avec addressId* s’affiche de manière aléatoire sur les navigateurs des visiteurs.
* **MDVA-32759** (*pour Adobe Commerce >=2.3.1 &lt;2.4.3 avec extension B2B*) - Correction du problème en raison duquel les catalogues partagés supprimaient les tarifs de niveau existant.
* **MDVA-33482** (*pour Adobe Commerce ^2.3.5*) : correction d’un problème en raison duquel la génération d’un avoir sur une facture partielle générait une taxe sur le total de la commande au lieu de la taxe sur cette facture partielle.
* **MDVA-33393** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction de l’erreur *countryId fourni n’existe pas*.
* **MDVA-33632** (*pour Adobe Commerce >=2.3.0 &lt;2.3.7*) - Fournit un correctif pour lequel le message d’exception *Ce produit est en rupture de stock* s’affiche désormais pour un utilisateur administrateur lorsqu’il tente de réorganiser un produit en rupture de stock.
* **MDVA-34469** (*pour Adobe Commerce >=2.4.1 &lt;2.4.2*) - Correction du problème d’échec des mutations GraphQL sur le panier d’un client lors de l’utilisation de plusieurs vues de magasin.
* **MDVA-33976** (*pour Adobe Commerce >=2.3.0 &lt;2.3.7*) - Correction du problème qui entraînait l’affichage du produit en rupture de stock sur le storefront après la suppression de la deuxième option du produit en regroupement.
* **MDVA-33894** (*pour Adobe Commerce >=2.4.0 &lt;2.4.1 avec extension B2B*) - Correction de plusieurs problèmes liés à la fonctionnalité de commande rapide, notamment l’ajout et la suppression de plusieurs produits et le respect de la casse des SKU.
* **MDVA-27664** (*pour Adobe Commerce >=2.3.4 &lt;2.3.6*) - Correction du problème dans le formulaire d’enregistrement du client qui provoquait l’affichage d’une erreur : *ERROR - La date de naissance ne doit pas être supérieure à aujourd’hui.*
* **MDVA-33970** (*pour Adobe Commerce >=2.3.4 &lt;2.4.2*) : correction d’un problème en raison duquel un mauvais signe de devise s’affichait dans la Note de crédit lorsque la portée de l’attribut de prix était définie sur le site web.
* **MDVA-33992** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème des prix spéciaux B2B qui s’affichaient incorrectement lors du passage en caisse.
* **MDVA-34100** (*pour Adobe Commerce >=2.3.4 &lt;2.4.2 avec extension B2B*) - Correction du problème qui empêchait la création d’un compte d’entreprise à partir de la page de structure de l’entreprise.

## v1.0.14 {#v1-0-14}

* **MDVA-31969** (*pour Adobe Commerce >=2.3.3 &lt;2.3.5, >=2.4.0 &lt;2.4.2*) - Correction du problème lié aux images dupliquées après l’importation d’un produit à partir d’un fichier CSV.
* **MDVA-33382** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction des problèmes d’invalidation des indexeurs après suppression de produits d’une catégorie.
* **MDVA-28511** (*pour Adobe Commerce >=2.3.5 &lt;2.3.6*) - Correction du problème lorsqu’il n’est pas possible de terminer [!DNL PayPal] passage en caisse si le champ Nom contient certains caractères (comme des majuscules accentuées).
* **MDVA-31519** (*pour Adobe Commerce >=2.3.5 &lt;2.3.6*) - Correction du problème lié aux délais d’attente dans le passage en caisse des invités lorsqu’une règle de vente à l’échelle du site est en cours d’utilisation.
* **MDVA-33281** (*pour Adobe Commerce >=2.3.4 &lt;2.3.6*) - Correction du problème d’erreur fatale dans `inventory:reservation:list-inconsistencies` en raison d’un type de paramètre de SKU incorrect.
* **MDVA-24201** (*pour Adobe Commerce >=2.3.0 &lt;2.3.5*) : correction d’un problème en raison duquel les prix ne reflètent pas la règle de prix du panier planifiée tant qu’ils n’ont pas été réindexés manuellement.
* **MDVA-32694** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6 || >= 2.4.0 &lt;2.4.2*) - Correction du problème qui empêchait un utilisateur administrateur d’ajouter un produit à un guillemet négociable s’il était lié à un magasin autre qu’un magasin par défaut.
* **MDVA-33516** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6*) - Correction du problème qui entraînait une erreur lors de la modification d’un produit groupé dans une liste de demandes.
* **MDVA-33975** (*pour Adobe Commerce >=2.3.4 &lt;2.4.2*) - Correction de plusieurs problèmes liés au calcul des prix dans les requêtes GraphQL.

## v1.0.13 {#v1-0-13}

* **MDVA-30858** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème lié à [!DNL PayPal] Les rapports de règlement ne sont pas disponibles sous **Rapports** > **Ventes** > **[!DNL PayPal]** Accord comme prévu.
* **MCP-87** (*pour Adobe Commerce >=2.3.1 &lt;2.4.2*) - Amélioration du temps d’indexation pour les indexeurs de produits de catégorie et de stocks pour les profils volumineux.
* **MDVA-33106** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème en raison duquel les modifications de produit reprogrammées étaient effacées après le cron . `run` est exécutée.
* **MDVA-19391** (*pour Adobe Commerce >=2.3.0 &lt;2.3.5*) - Correction du problème qui `analytics_collect_data` renvoie une erreur en raison d’enregistrements de description NULL dans la variable `catalog_category_entity_text` table.
* **MDVA-20376** (*pour Adobe Commerce >=2.3.2 &lt;2.3.4*) - Correction du problème lié à la variable *Aucune entité de ce type avec customerId = 1* dans le `exception.log` pour les clients connectés après l’emplacement de la commande.
* **MDVA-23764** (*pour Adobe Commerce >=2.3.2 &lt;2.3.5*) - Correction du bogue dans `JsFooterPlugin.php` qui affecte l&#39;affichage des blocs dynamiques.
* **MDVA-13203** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème en raison duquel la variable *Intégrité contrainte violation search_tmp_table* s’affiche après une réindexation complète.
* **MDVA-23426** (*pour Adobe Commerce >=2.3.3 &lt;2.3.5*) - Correction du problème en raison duquel les emails de notification envoyés par Adobe Commerce contenaient un corps vide avec du contenu ajouté en tant que pièce jointe.
* **MDVA-22150** (*pour Adobe Commerce >=2.3.1 &lt;2.3.4*) - Correction du problème qui empêchait les clients disposant d’un produit configurable dans le panier et d’un bon appliqué de se connecter si ce produit configurable était désactivé dans l’administrateur.
* **MDVA-32545** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) : correction d’un problème qui empêchait l’envoi automatique de factures lors de la création de commandes de la part de l’administrateur.
* **MDVA-32714** (*pour Adobe Commerce >=2.3.4 &lt;2.4.1*) - Correction du problème en raison duquel le prix du groupe de clients ne fonctionnait pas dans la requête de produit GraphQL.

## v1.0.12 {#v1-0-12}

* **MDVA-31399** (*pour Adobe Commerce >=2.3.2 &lt;2.4.2*) - Ajoute la variable *Sous-Total (Incl. Tax)* pour fixer les conditions des règles de prix.
* **MDVA-31236** (*pour Adobe Commerce >=2.4.0 &lt;2.4.2*) - Correction du problème qui empêchait les administrateurs disposant d’un accès aux ressources personnalisées de configurer 2FA ou de se connecter.
* **MDVA-30845** (*pour Adobe Commerce >=2.3.5 &lt;2.3.7*) - Correction du problème en raison duquel la variable *Désolée, aucun guillemet n&#39;est disponible pour l&#39;instant pour cette commande.* s’affiche lorsque vous ne vous connectez pas à UPS XML/USPS/DHL et qu’aucun autre mode de livraison n’est disponible.
* **MDVA-32133** (*pour Adobe Commerce >=2.4.0 &lt;2.4.1*) - Correction du problème en raison duquel la galerie multimédia ne se chargeait pas à partir du Créateur de pages dans certains cas.
* **MDVA-12304** (*pour Adobe Commerce >=2.3.0*) : augmente le nombre maximum de cookies de 50 à 200.
* **MDVA-32632** (*pour Adobe Commerce >=2.3.2 &lt;2.3.5*) - Correction du problème d’affichage des commandes dans le système de paiement, mais pas dans Adobe Commerce.
* **MDVA-32449** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || >=2.4.1 &lt;2.4.2 avec extension B2B*) - Correction d’un problème en raison duquel l’historique des commandes se charge très lentement ou ne se charge pas du tout.
* **MDVA-32739** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème qui entraînait l’envoi d’anciens courriers électroniques de vente lors de l’activation des notifications par courrier électronique asynchrone.

## v1.0.11 {#v1-0-11}

* **MC-38509** (*pour Adobe Commerce 2.3.6, 2.4.1*) - Correction du problème en raison duquel la variable *Création d’un compte* reste désactivé après correction des données incorrectes dans la variable *Créer un compte client* formulaire.
* **MDVA-31006** (*pour Adobe Commerce 2.3.0, 2.3.1*) - Correction du problème d’affichage des commandes dupliquées après le placement d’une commande à l’aide de [!DNL Paypal Express] paiement.
* **MDVA-25602** (*pour Adobe Commerce 2.3.0*) - Correction d’un problème lié à [!DNL PayPal Payflow Pro] mode de paiement et traitement des cookies en tant que `SameSite=Lax` par défaut, dans le navigateur Chrome 80 et la réponse de l’API redirigent vers la page de connexion du client.

## v1.0.10 {#v1-0-10}

Correctifs mineurs pour les versions de correctif

## v1.0.9 {#v1-0-9}

* **MDVA-31363** (*pour Adobe Commerce >=2.3.2 &lt;2.4.2*) - Correction du problème en raison duquel la règle sur le prix du panier avec coupon ne s’appliquait pas via GraphQL lorsque *Remise de montant fixe pour le panier entier* est utilisée.
* **MDVA-30889** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème d’erreur qui se produisait après la facturation d’un lot avec des produits virtuels et simples comme options.
* **MDVA-31791** (*pour Adobe Commerce >=2.3.4 &lt;2.3.5*) - Améliore les performances de la page de produits lorsque des règles cibles ou des produits liés sont utilisés.
* **MDVA-31168** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème qui empêchait l’affichage du fichier CSV d’exportation de produits et provoquait une erreur d’allocation de mémoire.
* **MDVA-32313** (*pour Adobe Commerce >=2.3.0 &lt;2.3.4*) - Correction du problème en raison duquel les produits configurables pouvaient être ajoutés à la liste des souhaits avec des options de configuration incorrectes.
* **MDVA-31759** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème en raison duquel les produits ne sont pas mis à jour avec *menu déroulant* et *textarea* valeurs d’attribut lors de l’importation CSV.
* **MDVA-32012** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème qui empêchait la validation des codes postaux en Corée et en Argentine.
* **MDVA-31640** (*pour Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) - Correction d’un problème en raison duquel un prix spécial ne pouvait pas être mis à jour via l’API REST.
* **MDVA-28651** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6 || >2.4.0 avec extension B2B*) - Correction d’un problème de performances lors du chargement de guillemets négociables via l’API REST.

## v1.0.8 {#v1-0-8}

* **MDVA-31242** (*pour Adobe Commerce >=2.3.0 &lt;2.4.1 avec extension B2B*) - Correction du problème d’affichage d’un signe de devise incorrect dans la grille Mémo de crédit.
* **MDVA-31295** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème en raison duquel les points de récompense ne sont pas calculés lorsqu’une commande partielle est terminée et que les éléments sont taxés.
* **MDVA-30112** (*pour Adobe Commerce >=2.3.4 &lt;2.4.2*) : résout le problème en raison duquel, si le nombre de commandes dépasse la valeur *taille du lot* , Adobe Commerce considère les commandes avec la variable *pending* comme incohérences.
* **MDVA-31150** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) : correction d’un problème en raison duquel les soldes des cartes de crédit et des cadeaux de la boutique n’étaient pas renvoyés par l’appel de l’API REST GET, lorsque la facture était validée par l’appel de l’API REST et que la commande était partiellement payée par les comptes de carte de crédit et de cadeau de la boutique.
* **MDVA-30963** (*pour Adobe Commerce >=2.3.2 &lt;2.4.2*) - Correction du problème en raison duquel les résultats de filtrage de produits définis sur ne contenaient que les valeurs spécifiées pour *Toutes les vues de magasin* dans Admin, incluez les produits dont les valeurs sont remplacées au niveau de la vue de magasin.
* **MDVA-29954** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || 2.4.2 avec extension B2B*) - Correction du problème en raison duquel la variable *Nouvelle demande d’enregistrement d’entreprise* et *Vous avez été lié à une société.* les emails sont envoyés à partir d’une adresse incorrecte.
* **MDVA-28357** (*pour Adobe Commerce >=2.3.2 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) : remplace l’analyseur standard par un analyseur personnalisé avec un jeton de mot-clé pour le champ SKU dans la variable [!DNL ElasticSearch] pour que les requêtes de recherche par caractères génériques fonctionnent avec les SKU contenant un trait d’union (&quot;-&quot;).

## v1.0.7 {#v1-0-7}

* **MDVA-30972** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème en raison duquel l’état de la commande personnalisée était remplacé par *Traitement* après la création d’un envoi partiel à l’aide de WebApi.
* **MDVA-30428** (*pour Adobe Commerce >=2.3.4 &lt;2.3.5*) - Correction du problème qui empêchait les clients d’ajouter un produit à une liste bloquée si ce produit était affecté à une source d’inventaire personnalisée.
* **MDVA-30594** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème qui empêchait l’enregistrement d’une commande contenant plusieurs adresses lors de l’extraction lorsque FPT était configuré.
* **MDVA-29148** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème lors de la création d’un produit via un appel API, l’attribut personnalisé de produit de `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (comme Multiselect) le type n’utilise pas sa valeur par défaut si aucune valeur n’a été fournie dans la payload.
* **MDVA-30837** (*pour Adobe Commerce >=2.3.1 &lt;2.3.5*) - Ajout d’un paramètre de configuration *Inclure la taxe au montant : Oui/Non* dans la configuration de la méthode d’expédition gratuite . When *Inclure la taxe au montant* est défini sur *Oui*, Montant minimum de la commande est calculé comme suit : Sous-total + Taxe. When *Inclure la taxe au montant* est défini sur *Non*, Montant minimum de la commande est calculé comme sous-total
* **MDVA-25028** (*pour Adobe Commerce >=2.3.2 &lt;2.3.3 || >=2.3.5 &lt;2.3.6*) - Correction du problème qui se produisait lorsque des commandes étaient passées à l’aide de [!DNL PayPal Payflow Pro] ne sont pas définies sur l’état Fraude suspectée lorsque des filtres de fraude sont déclenchés.
* **MDVA-31224** (*pour Adobe Commerce >=2.3.3 &lt;2.3.5*) - Améliore les performances de la fonction `catalog_product_price` opération de réindexation pour les produits du lot.
* **MDVA-31321** (*pour Adobe Commerce >=2.3.2 &lt;2.3.5*) - Correction d’une page vierge (erreur) lors de la *Tout afficher* est sélectionnée. [!DNL Elasticsearch] renvoie une grande liste d’identifiants de produit. Dans ce scénario, la clause order by est convertie dans un format SQL incorrect.
* **MDVA-30815** (*pour Adobe Commerce >=2.3.2 &lt;2.3.4*) - Correction du problème qui entraînait l’affichage d’une page vierge dans Adobe Commerce lorsque vous modifiez le nombre de résultats de recherche à afficher sur la page des résultats de recherche. [!DNL Elasticsearch] affiche désormais correctement les résultats des pages de catégorie lorsque vous modifiez le nombre de résultats de recherche affichés par page.
* **MDVA-30782** (*pour Adobe Commerce >=2.3.5 &lt;2.4.2*) - Correction du problème d’affichage du bloc dynamique, quelle que soit la règle du panier.
* **MDVA-31021** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème de performances dans `module-catalog-import-export/Model/Import/Product/Option.php`. S’il y a plus de ~100 000 enregistrements dans `catalog_product_option` , la validation d’un nouveau fichier CSV avec un seul produit prend moins de 10 secondes.
* **MDVA-31007** (*pour Adobe Commerce >=2.4.0 &lt;2.4.1*) - Correction du problème en raison duquel les attributs d’adresse personnalisés ne s’affichaient pas correctement dans la page des détails de la commande dans la zone de mon compte et dans le serveur principal.
* **MDVA-29389** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème lié à la création de rapports avancés où l’événement `analytics_collect_data` cronjob dit : *Le port doit être configuré dans le paramètre d’hôte (comme localhost:3306).*.
* **MDVA-31343** (*pour Adobe Commerce >=2.3.4 &lt;2.3.6*) - Correction du problème lié à la classe body supprimée `page-layout-category-full-width` lorsqu’une catégorie est planifiée.
* **MDVA-30945** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction d’un problème en raison duquel vous recevez un message d’erreur fatal lors de la mise à jour des paniers. `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.

## v1.0.6 {#v1-0-6}

* **MDVA-28993** (*pour Adobe Commerce >=2.3.4 &lt;2.4.0*) : met en oeuvre le *La valeur minimale doit correspondre* fonctionnalité et recherche partielle [!DNL Elasticsearch] moteur. Résout les problèmes liés aux tirets dans les requêtes de recherche.
* **MDVA-30102** (*pour Adobe Commerce >=2.3.2 &lt;=2.4.0*) - Correction du problème de croissance rapide du cache Redis, car les caches de mise en page n’ont pas de durée de vie (TTL).
* **MDVA-30599** (*pour Adobe Commerce >=2.3.4 &lt;=2.4.0*) - Correction du problème en raison duquel les guillemets d’invité créés à l’aide de l’API étaient incorrectement marqués comme guillemets pour les clients connectés.
* **MDVA-29446** (*pour Adobe Commerce >=2.3.3 &lt;=2.4.0*) - Correction d’un problème en raison duquel le prix de la méthode d’expédition non applicable s’affichait comme zéro pendant le passage en caisse.
* **MDVA-30357** (*pour Adobe Commerce >=2.3.2 &lt;=2.4.0*) - Correction du problème lié à la création d’URL d’image incorrectes lors de la génération d’un plan de site par cron.
* **MDVA-30565** (*pour Adobe Commerce >=2.3.2 &lt;=2.3.3-p1*) - Correction du problème qui *Aucune entité de ce type avec cartid = 0* s’affiche pour les clients invités lors du passage en caisse en storefront si le panier persistant est activé.
* **MDVA-29787** (*pour Adobe Commerce >=2.3.0 &lt;=2.4.0*) - Correction du problème en raison duquel la règle de ciblage pour les produits associés ne fonctionnait pas lorsque *est l’un des* est utilisée pour définir les produits à afficher.
* **MDVA-30977** (*pour Adobe Commerce >=2.3.4 &lt;=2.3.5-p2*) - Correction du problème des produits aléatoires manquants dans les catégories après la réindexation.
* **MDVA-28202** (*pour Adobe Commerce >=2.3.4 &lt;=2.4.2*) - Correction du problème de navigation par calques qui ne filtrait pas correctement les produits configurables lorsque MSI est utilisé.
* **MDVA-28300** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6*) - Correction du problème en raison duquel la demande GQL ne reflétait pas les modifications de prix des règles de prix du catalogue.
* **MDVA-31006** (*pour Adobe Commerce >=2.3.2 &lt;=2.4.2*) - Correction du problème d’affichage des commandes dupliquées après le placement d’une commande à l’aide de [!DNL Paypal Express] paiement.

## v1.0.5 {#v1-0-5}

* **MDVA-30841** (*pour Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Correction du problème de navigation par couches, où la variable *Non* La valeur des attributs de produit de type booléen n’était pas incluse dans la navigation par couche si [!DNL Elasticsearch] a été utilisé comme moteur de recherche.
* **MDVA-28191** (*pour Adobe Commerce >=2.3.3 &lt;2.4.2*) - Correction du problème en raison duquel aucun mode de paiement n’était chargé lors de la création de la commande via l’administrateur.
* **MDVA-29959** (*pour Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 avec extension B2B*) - Correction du problème en raison duquel l’utilisateur administrateur restreint avec *Entreprises* Les autorisations ne sont pas autorisées pour supprimer le compte de la société.
* **MDVA-30265** (*pour Adobe Commerce >=2.3.3 &lt;2.4.2*) - Correction du problème en raison duquel le lien de suivi des envois ne fonctionnait plus après la création de la facture.
* **MDVA-28409** (*pour Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Correction du problème en raison duquel la variable `sales_clean_quotes` la tâche cron échoue avec *out de mémoire* lorsque le nombre de guillemets expirés dans la base est énorme.
* **MDVA-30593** (*pour Adobe Commerce >=2.3.0 &lt;2.3.4*) - Correction du problème en raison duquel les guillemets qui ont expiré selon le paramètre Durée de vie des guillemets ne sont pas nettoyés.
* **MDVA-30107** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6*) - Correction du problème en raison duquel le sélecteur de magasin ne fonctionnait pas comme prévu si différentes URL de base étaient utilisées pour les vues de magasin.
* **MDVA-28763** (*pour Adobe Commerce >=2.3.2 &lt;2.3.4*) - Correction du problème de duplication de l’image du produit après la mise à jour des informations sur le produit à l’aide de l’API REST plusieurs fois.
* **MDVA-30284** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème de l’échec de l’indexeur de recherche catalogue en raison de ce qui suit : *[!DNL Elasticsearch]error: la limite du nombre total de champs dans l&#39;index a été dépassée.*
* **MDVA-29042** (*pour Adobe Commerce >=2.3.3 &lt;=2.3.4-p2 avec extension B2B*) - Correction du problème en raison duquel les autorisations du catalogue étaient modifiées en *Autoriser* automatiquement après l’ajout d’un nouveau produit au catalogue partagé.
* **MDVA-30428** (*pour Adobe Commerce >=2.3.3 &lt;2.4.2*) - Correction du problème qui empêchait les clients d’ajouter un produit à une liste bloquée si ce produit était affecté à une source d’inventaire personnalisée.
* **MDVA-28661** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2 avec extension B2B*) - Correction du problème qui entraînait l’apparition d’une erreur dans la section du compte de société Utilisateurs de l’entreprise après la modification de l’administrateur de l’entreprise.

## v1.0.4 {#v1-0-4}

* **MDVA-30195** (*pour Adobe Commerce 2.3.1 - 2.3.4-p2*) - Correction du problème d’échec des tâches cron si le nom de la base de données est trop long, ce qui empêchait la mise à jour des catégories sur le front-end.
* **MDVA-30106** (*pour Adobe Commerce ^2.3.0*) - Correction d’un problème en raison duquel les paiements de passage en caisse ne sont pas chargés avec *Impossible de lire la propriété &quot;length&quot; de null* dans la console JS.
* **MDVA-28656** (*pour Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.2*) : correction d’un problème en raison duquel, si une commande était passée sans aucune information de paiement (avec, par exemple, une remise de 100 %) et qu’une facture était créée pour la commande, l’état de la commande passe à *Fermé* au lieu de Terminé.
* **MDVA-30209** (*pour Adobe Commerce 2.3.0 - 2.3.3-p1*) - Correction du problème en raison duquel le groupe de clients était remplacé par défaut si le client mettait à jour les informations de son compte.
* **MDVA-30123** (*pour Adobe Commerce >=2.3.4 &lt;2.4.2*) - Correction du problème en raison duquel les libellés des options d’attribut ne sont pas correctement traduits pour les requêtes GraphQL.
* **MDVA-29996** (*pour Adobe Commerce >=2.3.3 &lt;2.4.2*) : correction d’un problème en raison duquel, après l’activation de l’autorisation de catégorie, la page de catégorie n’était pas mise en cache par le cache de la page entière.
* **MDVA-30164** (*pour Adobe Commerce >=2.3.1 &lt;2.4.2*) - Correction du problème en raison duquel les enregistrements de clients ne pouvaient pas être exportés à partir de la grille Clients s’il existait des attributs de client personnalisés.
* **MDVA-30444** (*pour Adobe Commerce >=2.3.0 &lt;2.4.1*) - Correction du problème qui empêchait l’envoi d’un email de confirmation pour les commandes passées à l’aide de GraphQL.
* **MDVA-30490** (*pour Adobe Commerce 2.3.4 - 2.3.5-p2*) - Correction du problème en raison duquel la comparaison de produits renvoyait la page d’erreur 500 si l’un des produits avait une brève description vide.
* **MDVA-30232** (*pour Adobe Commerce >=2.3.1 &lt;2.4.1*) - Correction du problème qui empêchait la réorganisation si la commande d’origine contenait une carte-cadeau.
* **MDVA-29965** (*pour Adobe Commerce >=2.3.3 &lt;2.4.0*) - Correction d’un problème en raison duquel les clients recevaient une erreur de clé de formulaire non valide lors de l’ajout d’un produit au panier.
* **MDVA-30008** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème B2B où il n’est pas possible de passer des commandes via l’API d’administration pour un produit qui se trouve dans un catalogue public.
* **MDVA-22469** (*pour Adobe Commerce 2.3.2-p2 - 2.3.3-p1*) - Correction du problème qui, après la mise à niveau vers Adobe Commerce 2.3.3, le Créateur de pages ne fonctionnait pas dans le panneau d’administration et qui empêchait le chargement de certains fichiers JS et CSS.
* **MC-35984** (*pour Adobe Commerce >=2.4.0 &lt;2.4.1*) - Correction du problème qui empêchait les marchands d’interagir avec des éléments de page sur la page Renvoie après la création d’un libellé d’expédition pour une autorisation de marchandisage de retour (RMA).

## v1.0.3 {#v1-0-3}

* **MDVA-25602** (*pour Adobe Commerce 2.3.0 - 2.3.4*) - Correction du problème lié à [!DNL PayPal Payflow Pro] mode de paiement et traitement des cookies en tant que `SameSite=Lax` par défaut, dans le navigateur Chrome 80 et la réponse de l’API redirigent vers la page de connexion du client.
* **MDVA-26694** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0*) - Correction d’un problème en raison duquel les caches de produit et de catalogue expiraient tous les jours, bien que le délai d’expiration soit différent.
* **MDVA-27825** (*pour Adobe Commerce >=2.3.0 &lt;2.4.1*) - Correction du problème d’échec de l’exportation de grandes quantités de données en raison d’une fuite de mémoire.
* **MDVA-29085** (*pour Adobe Commerce >=2.3.0 &lt;=2.3.5-p1*) - Correction du problème B2B qui empêchait l’envoi de nouveaux emails d’entreprise requis si une entreprise était créée par l’API.
* **MDVA-29344** (*pour Adobe Commerce >=2.3.5 &lt;=2.4.0-p1*) - Correction du problème de blocage du Créateur de pages après la copie de texte d’un élément d’en-tête vers un élément de texte.
* **MDVA-29835** (*pour Adobe Commerce >2.3.1 &lt;2.4.2*) : correction d’un problème en raison duquel les commandes de cartes-cadeaux comportaient deux codes au lieu d’un.
* **MDVA-30052** (*pour Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - Correction d’un problème en raison duquel le contenu privé (stockage local) n’était pas renseigné correctement, ce qui entraînait des problèmes de performances.
* **MDVA-30131** (*pour Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Correction du problème de navigation par couches, où la variable *Non* La valeur des attributs de produit de type booléen n’était pas incluse dans la navigation par couche si [!DNL Elasticsearch] a été utilisé comme moteur de recherche.
* **MDVA-35514** (*pour Adobe Commerce >=2.4.0 &lt;2.4.1*) - Correction du problème lié à la création d’un libellé d’expédition et à l’ajout de produits commandés à un package dans la fenêtre modale Créer des packages .
