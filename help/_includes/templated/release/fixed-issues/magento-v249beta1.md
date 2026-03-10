---
source-git-commit: 0a22d08d6965c6abc288a1a171d25f4ff8bbd7ce
workflow-type: tm+mt
source-wordcount: '24356'
ht-degree: 0%

---
# Problèmes résolus dans Magento Open Source (v2.4.9-beta1)

## Correction de problèmes dans la version v2.4.9-beta1

Nous avons corrigé 501 problèmes dans le code principal 2.4.9-beta1 de Magento Open Source. Un sous-ensemble des problèmes résolus inclus dans cette version est décrit ci-dessous.

### API

#### Prix spécial à ce jour est validé de manière incorrecte sur applySpecialPrice

Le système fonctionne correctement en ce qui concerne le Prix spécial et le Prix spécial du produit expirera à la date définie par l’administrateur ou un système tiers par l’API REST

_AC-13130 - [Problème GitHub](https://github.com/magento/magento2/issues/39169) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39690)_

#### [WebAPI] confirmation par e-mail du client via le paradoxe WebAPI

Correction d’un problème en raison duquel les clients ne pouvaient pas activer leurs comptes via WebAPI en raison d’un paradoxe d’autorisation nécessitant un jeton avant confirmation. La mise à jour permet aux clients non confirmés d’activer leurs comptes avec succès via l’API, assurant ainsi un flux de confirmation cohérent et fonctionnel.

_AC-13281 - [Problème GitHub](https://github.com/magento/magento2/issues/39255) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/c95ed7d7)_

#### Erreur d’adresse de facturation manquante dans le tableau de bord d’administration lors de la création d’une commande via l’API REST avec uniquement des informations de paiement

Correction d’un problème en raison duquel les commandes pouvaient être créées via l’API sans adresse de facturation, provoquant des blocages du tableau de bord d’administration.
Désormais, les commandes sans adresse de facturation sont restreintes et ne sont plus créées.

_AC-14049 - [Problème GitHub](https://github.com/magento/magento2/issues/39651) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Problème d’ajout de produit au panier dans l’API REST

Correction d’un problème en raison duquel les produits non affectés à un site web spécifique pouvaient toujours être ajoutés au panier et achetés.
Un message d’erreur s’affiche maintenant : « Le produit que vous essayez d’ajouter n’est pas disponible. »

_AC-15054 - [Problème GitHub](https://github.com/magento/magento2/issues/40029) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/f5cc09fc)_

#### Le Libellé De L’Option D’Attribut Est Remplacé Lors De La Mise À Jour Des Libellés De La Boutique

Correction d’un problème en raison duquel la mise à jour d’un attribut de produit à sélection multiple via l’API REST remplacait tous les store_labels, supprimant les libellés spécifiques au magasin existants.
Désormais, lors de la mise à jour du libellé d’affichage de la boutique par défaut, Magento fusionne les libellés fournis avec les libellés existants au lieu de les remplacer entièrement.
Cela permet de s’assurer que les libellés spécifiques aux magasins des autres affichages de magasin restent intacts après les mises à jour.

_AC-15208 - [Problème GitHub](https://github.com/magento/magento2/issues/40093) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

#### [Problème] L’option d’attribut clarifié existe déjà une réponse

Le système a désormais remplacé l’expression gênante « Obtenir un nouveau nom de fichier si le même nom existe déjà » par une version plus claire et grammaticalement correcte : « Obtenir un nouveau nom de fichier s’il existe déjà ». Cela améliore la lisibilité et la compréhension de l’utilisateur.
Idem pour la réponse de l’option d’attribut.

_AC-15473 - [Problème GitHub](https://github.com/magento/magento2/issues/39943) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39941)_

#### Erreur de serveur interne dans le point d’entrée /V1/products/special-price de l’API

Correction d’un problème en raison duquel des requêtes incorrectes à /V1/products/special-price et aux API de tarification associées renvoyaient une erreur de serveur interne 500 en raison d’une erreur de type nulle.
Désormais, les API valident correctement les entrées et renvoient une erreur 400 pour les payloads non valides, ce qui améliore la gestion des erreurs et la fiabilité des API.

_AC-6419 - [Problème GitHub](https://github.com/magento/magento2/issues/35934) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a7ef6300)_

#### Erreur de serveur interne dans le point d’entrée de l’API `/V1/order/&lbrace;orderId&rbrace;/ship`

Le système corrige désormais l’erreur de serveur interne dans `/V1/order/{orderId}/ship` point d’entrée de l’API et renvoie une erreur 400, car la requête est incorrecte.

_AC-6420 - [Problème GitHub](https://github.com/magento/magento2/issues/35931) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38282)_

#### Erreur de serveur interne dans le point d’entrée /V1/creditmemo de l’API

Correction d’un problème en raison duquel des requêtes incorrectes à l’API /V1/creditmemo renvoyaient une erreur de serveur interne 500.
Désormais, l’API valide correctement la requête et renvoie une erreur 400 pour les payloads non valides, ce qui améliore la gestion des erreurs et la stabilité.

_AC-6422 - [Problème GitHub](https://github.com/magento/magento2/issues/35924) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a7ef6300)_

#### L’API REST et le serveur principal Magento utilisent des méthodes de validation différentes pour attribute_code lors de la création de nouveaux attributs

Correction d’une incohérence en raison de laquelle l’administrateur Magento autorisait les lettres majuscules dans attribute_code, mais que l’API REST les rejetait lors de la création de l’attribut de produit.
Désormais, les API Admin et REST suivent la même validation, ce qui permet de créer des attributs avec des lettres majuscules.

_AC-6660 - [Problème GitHub](https://github.com/magento/magento2/issues/33138) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/8670a2b4)_

#### Validation différente entre la création et la mise à jour d’attributs via l’API REST

Correction d’un problème en raison duquel une validation incohérente lors de la création d’attributs via l’API REST entraînait l’affectation d’un backend_type incorrect.
Désormais, le système définit le type de serveur principal correct lorsqu’il est valide, renvoie une exception pour les valeurs non valides ou revient en arrière de manière appropriée s’il n’est pas fourni, garantissant ainsi un comportement d’attribut cohérent.

_AC-6885 - [Problème GitHub](https://github.com/magento/magento2/issues/36327) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/64823f95)_

#### Le corps ou les paramètres de la requête incorrects provoquent une « Erreur de serveur interne »

Les corps ou paramètres de requête incorrects renvoient désormais une réponse claire « 400 Bad Request ».
Auparavant, l’envoi de corps de requête ou de paramètres incorrects à divers points d’entrée de l’API REST (tels que /V1/carts/search, /V1/orders, /V1/products, etc.) entraînait une « erreur de serveur interne » générique (500), ce qui rendait difficile le diagnostic des problèmes d’entrée.
Désormais, Adobe Commerce renvoie une réponse « 400 Bad Request », fournissant des commentaires plus clairs lorsque les requêtes ne sont pas valides.

_AC-746 - [Problème GitHub](https://github.com/magento/magento2/issues/32784) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/f1adb44e)_

#### Point d’entrée `/orders`(ou `/orders/:id`) sans champs « state » et « status »

Correction d’un problème en raison duquel les réponses de l’API `/orders` et `/orders/{id}` omettaient les champs d’état et de statut lorsque les valeurs de base de données étaient nulles.
Désormais, les deux champs sont systématiquement renvoyés dans la réponse, ce qui garantit la conformité à la documentation de l’API et améliore la fiabilité des données.

_AC-9244 - [Problème GitHub](https://github.com/magento/magento2/issues/37807) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/01cee3c3)_

#### L’opération en bloc asynchrone reste à l’état ouvert pour async.magento.configurableproduct.api.optionrepositoryinterface.save.post

Les points d’entrée de l’API en bloc renvoient désormais une erreur si le corps de la requête n’est pas un tableau, ce qui nécessite que les clés d’élément en bloc soient des nombres consécutifs commençant à 0. Auparavant, le statut de l’élément en bloc n’était pas mis à jour en raison de la clé d’élément arbitraire envoyée dans la requête en bloc.

_ACP2E-3544 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/9608ca21)_

#### Le bogue REST de l’API [CLOUD] sur la valeur is_subscribed ne prend pas en compte les éléments du magasin actuel à l’aide de searchCriteria.

La requête client REST d’API récupère la valeur « is_subscribed » correcte dans le magasin approprié à l’aide de critères de recherche
Auparavant, la requête du client REST de l’API ne tenait pas compte du magasin lors de la récupération de la valeur is_subscribed ».

_ACP2E-3621 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/9608ca21)_

#### async.operations.all peut créer plusieurs entrées pour 1 SKU

Les demandes simultanées d’enregistrement et de mise à jour du même produit sont désormais sérialisées afin d’éviter les conditions de concurrence qui peuvent entraîner une incohérence des données ou des produits dupliqués

_ACP2E-3744 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/520f9e30)_

#### La commande « base_row_total » et « row_total » affichent le prix d’un seul article dans la réponse de l’API REST

La réponse de l’api REST pour les détails de la commande contient désormais des valeurs correctes pour les attributs « base_row_total » et « row_total » dans le cas où plusieurs mêmes éléments ont été commandés

_ACP2E-3874 - [contribution du code GitHub](https://github.com/magento/magento2/commit/4ca73607)_

#### Le point d’entrée de l’API REST export-stock-salable-qty renvoie des éléments incorrects total_count

Correction d’un problème de pagination dans l’API de quantité vendable de stock d’exportation de stock où total_count était incorrectement limité à la taille de la page. Auparavant, lorsque vous utilisiez le point d’entrée /rest/all/V1/inventory/export-stock-salable-qty/website/base avec des paramètres de pagination tels que page_size=5, le champ total_count de la réponse renvoyait 5 au lieu du nombre total réel de produits correspondant aux critères de recherche. Après ce correctif, le champ total_count reflète désormais correctement le nombre total de produits disponibles, quel que soit le paramètre page_size , ce qui garantit un comportement de pagination cohérent sur tous les points d’entrée de l’API REST Magento.

_ACP2E-4086 - [contribution du code GitHub](https://github.com/magento/inventory/commit/5632fb5e)_

#### Problème de validation avec les identifiants d’options personnalisées dans les API REST d’article de panier.

Les API REST V1/guest-carts/&lt;cartId>/items/ et V1/carts/mine/items/ valident désormais « product_options.extension_attributes.custom_options ».*.option_id » pour vous assurer qu’il référence un option_id valide pour le SKU de l’article du panier. Auparavant, ce paramètre était traité et enregistré dans la base de données sans validation.

_ACP2E-4138 - [contribution du code GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

#### Lors de la récupération du produit du panier et de la modification de la langue d’en-tête de magasin sans modification

La requête du panier client GraphQL renvoie désormais des valeurs d’attribut de produit en fonction de la valeur de l’en-tête du magasin. Auparavant, la modification de la langue d’en-tête de magasin lors de la récupération d’un produit du panier via GraphQL ne reflétait pas la langue mise à jour, ce qui entraînait une localisation incohérente.

_ACP2E-4227 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/6e134409)_

#### Échec du point d’entrée /media de l’API REST pour les produits de carte cadeau - renvoie « Le produit ne peut pas être enregistré »

Avant la correction, vous étiez autorisé à créer des produits de carte cadeau qui n’incluaient pas de montant dans la portée globale. Avec le correctif, une validation a été ajoutée pour vérifier les montants dans la portée globale.

_ACP2E-4395 - [Problème GitHub](https://mcstaging.panini.it/shp_ita_it/)_

### API, panier et passage en caisse

#### Pour les informations d&#39;expédition, la validation côté serveur ne fonctionne pas à l&#39;aide de l&#39;API REST

Correction d’un problème dans l’API REST en raison duquel la validation des informations de l’adresse d’expédition ne respectait pas la configuration d’attribut définie dans le serveur principal d’administration. La validation suit désormais correctement les paramètres configurés.

_ACP2E-4156 - [contribution du code GitHub](https://github.com/magento/magento2/commit/45cbf9b6)_

### API, catalogue

#### Supprimer le point d’entrée par défaut de l’API de prix de niveau Causes de site web/magasin

Auparavant, la suppression du site web de base par défaut et l’utilisation du site web secondaire en tant que site web par défaut entraînaient une erreur lors de la tentative de mise à jour du prix de niveau pour le site web secondaire. Cependant, après application de ce correctif, le prix de niveau peut être mis à jour avec succès même si le site web de base est supprimé ou désactivé.

_ACP2E-4334 - [contribution du code GitHub](https://github.com/magento/magento2/commit/0a3b7032)_

### API, framework

#### Exception RedisRequestLogger\RedisClient (limiteur de débit) sur le serveur d’applications

Après le correctif, la fonction de limitation de débit peut être utilisée avec le serveur d’applications GraphQL dans les cas où l’extension PHP redis est installée.

_ACP2E-4237 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/e885088b)_

### API, import/export

#### L’API de remboursement de facture asynchrone crée des remboursements hors ligne au lieu des remboursements en ligne

Correction des opérations de remboursement asynchrones pour lesquelles les demandes de remboursement avec le paramètre `is_online` n’étaient pas traitées correctement.

_ACP2E-4394 - [contribution du code GitHub](https://github.com/magento/magento2/commit/61c96348)_

### API, Ordre

#### [CLOUD] Problème d’informations de commande avec l’apparence du total de la ligne pour le 000075568 de commande

Correction du problème en raison duquel la valeur de row_total_incl_tax dans la réponse de l’API de commande était renvoyée comme une valeur résiduelle proche de zéro au lieu de 0,00 lorsqu’un article était entièrement actualisé.

_ACP2E-3950 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/462ede94)_

### Compte

#### [Problème] Corrigez les fautes de frappe dans les options du modèle Widget de catalogue

Le système corrige désormais les fautes de frappe dans les options du modèle Widget de catalogue .

_AC-11576 - [Problème GitHub](https://github.com/magento/magento2/issues/38185) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38178)_

#### [Problème] Suppression de l’espacement inutile sur la grille du serveur principal

Le système supprime désormais l’espacement inutile dans la grille du serveur principal lorsque des éléments sont sélectionnés

_AC-11579 - [Problème GitHub](https://github.com/magento/magento2/issues/38502) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/32622)_

#### Le code de groupe client enregistré ne correspond pas à l’entrée lors de l’utilisation de caractères à plusieurs octets

Correction d’un problème où les codes de groupe client utilisant des caractères multioctet étaient tronqués et ne correspondaient pas à la valeur saisie. La mise à jour garantit que l’entrée complète est enregistrée correctement, ce qui permet la création précise de groupes de clients avec des noms à plusieurs octets.

_AC-13335 - [Problème GitHub](https://github.com/magento/magento2/issues/39342) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a06a4a57)_

#### Problème lors de la mise à jour de l’e-mail du client dans le Panneau d’administration avec les domaines ö et .swiss

Le panneau d’administration accepte désormais les e-mails des clients avec des caractères spéciaux et des domaines .swiss.
Auparavant, la mise à jour d’un e-mail client vers une adresse telle que max@möstermann.swiss échouait avec des erreurs sur les noms d’hôtes et les TLD non valides.
AC-13409

_AC-13409 - [Problème GitHub](https://github.com/magento/magento2/issues/39394) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/d3ea191d)_

#### Le commutateur d’abonnement à la newsletter ne fonctionne pas par site web/magasin.

Le système gère correctement l’abonnement à la newsletter lorsqu’il y a plusieurs sites web/magasins lorsqu’il a été désactivé au niveau mondial

_AC-14283 - [Problème GitHub](https://github.com/magento/magento2/issues/39751) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39752)_

#### [Problème] Suppression de la divulgation des e-mails

Le système affiche désormais Afficher un message d’erreur indiquant un e-mail incorrect si l’e-mail saisi n’est pas nécessaire pour confirmer le compte, que le client existe ou non.

_AC-14561 - [Problème GitHub](https://github.com/magento/magento2/issues/39574) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39570)_

#### Impossible d’effacer le commentaire d’élément de la liste de souhaits via `updateProductsInWishlist` mutation GraphQL

Correction d’un problème en raison duquel les commentaires de la liste de souhaits n’étaient pas mis à jour via les mutations de GraphQL.
Désormais, les commentaires sont correctement mis à jour et répercutés dans la réponse de l’API et dans le storefront.

_AC-14682 - [Problème GitHub](https://github.com/magento/magento2/issues/39911) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Le produit supprimé sur le mobile apparaît toujours dans la mini section de comparaison du web jusqu’à la reconnexion

Le système supprime désormais immédiatement le produit de toutes les vues de comparaison sur les appareils mobiles et le web, y compris la mini section de comparaison.

_AC-14703 - [Problème GitHub](https://github.com/magento/magento2/issues/39905) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40023)_

#### Afficher le paramètre de préfixe/suffixe ignoré lorsqu’il est défini sur Non

Correction d’un problème en raison duquel le préfixe/suffixe du nom du client continuait de s’afficher dans les commandes même lorsqu’il était désactivé dans la configuration.
Désormais, les valeurs de préfixe/suffixe sont supprimées des détails de commande en fonction du paramètre de configuration.

_AC-15074 - [Problème GitHub](https://github.com/magento/magento2/issues/40036) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Enregistrement de compte client Storefront : le format d’adresse e-mail est converti avec un format de domaine différent

Ce bogue corrige un problème où les e-mails des clients avec des caractères spéciaux dans le domaine (par exemple, tec55241@adòbe.com) étaient automatiquement convertis au format punycode (tec55241@xn--adbe-mqa.com).
Dans Magento 2.4.9-alpha3, le correctif garantit que ces ID d’e-mail restent inchangés et valides, évitant ainsi les erreurs de diffusion.

_AC-15177 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### Messages de validation manquants (erreur d’image) sur le formulaire d’enregistrement

Correction d’un problème en raison duquel les champs obligatoires de la page de création de compte client n’affichaient aucun message de validation lorsqu’ils étaient vides.
Désormais, les messages d’erreur appropriés s’affichent pour tous les champs vides ou incorrects.

_AC-15185 - [Problème GitHub](https://github.com/magento/magento2/issues/40076) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Le Titre Modal D’Annulation De Commande N’A Pas Été Traduit

Le système corrige désormais une traduction manquante dans la boîte de dialogue modale d’annulation de commande sur le storefront. Lorsqu’un client clique sur le bouton « Annuler » de la page Mon compte > Mes commandes , une fenêtre modale s’affiche pour demander un motif d’annulation. Toutefois, le titre modal était auparavant codé en dur et non traduisible. Cette modification garantit que le titre modal utilise une méthode de traduction appropriée.

_AC-15260 - [Problème GitHub](https://github.com/magento/magento2/issues/40098) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40100)_

#### Problème après connexion dans magento 2.4.8-p1

Correction d’un problème sur Magento 2.4.8-p1 en raison duquel le lien « Créer un compte » était toujours visible sur la page d’accueil après la connexion.
Désormais, le lien est correctement masqué après la connexion, ce qui est cohérent avec les autres pages.

_AC-15292 - [Problème GitHub](https://github.com/magento/magento2/issues/40120)_

#### [Problème] Définir isSecureArea avant de supprimer le client

Le système fonctionne maintenant correctement et cette requête d’extraction définit isSecureArea pour le processus de suppression. Le client peut s’enregistrer à nouveau avec succès.

_AC-15723 - [Problème GitHub](https://github.com/magento/magento2/issues/40211) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38462)_

#### L’opération de suppression [Cloud] est interdite pour l’erreur de zone actuelle lors de la création du compte client

Après le correctif, la sauvegarde d’un client avec une adresse non valide renvoie un message décrivant la raison de l’invalidité au lieu de non pertinent « L’opération de suppression est interdite pour la zone actuelle ».

_ACP2E-3791 - [contribution du code GitHub](https://github.com/magento/magento2/commit/6ea61121)_

#### [B2B] Les requêtes Webapi passent en boucle infinie pour les clients connectés lorsque le cache « eav » est désactivé

Après le correctif, la désactivation du cache de lecture n’entraîne pas une boucle infinie lors de certaines requêtes REST.

_ACP2E-4191 - [contribution du code GitHub](https://github.com/magento/magento2/commit/45cbf9b6)_

#### Erreur lors du chargement de certains paramètres régionaux

Correction d’un problème en raison duquel la création d’un compte client échouait lors de l’utilisation du paramètre régional arabe et l’attribut Date de naissance était défini pour s’afficher sur le storefront. Le compte peut maintenant être créé avec succès dans cette configuration.

_ACP2E-4311 - [contribution du code GitHub](https://github.com/magento/magento2/commit/2687b487)_

#### Erreur Date non valide lors de la mise à jour des informations de compte

Les clients peuvent désormais mettre à jour leur compte avec succès en utilisant les paramètres régionaux arabes. Auparavant, lors des tentatives d’enregistrement des informations de compte, la date de naissance échouait en raison d’une erreur de date non valide.

_ACP2E-4344 - [contribution du code GitHub](https://github.com/magento/magento2/commit/31258bf6)_

### Compte, interface utilisateur d’administration

#### [Cloud] Aucune entité de ce type avec cartId

Correction d’un problème en raison duquel l’utilisation de l’option Connexion en tant que client avec deux comptes d’administration d’entreprise dans la même session provoquait une erreur « Aucune entité de ce type avec cartId ».

_ACP2E-4137 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/e885088b)_

#### Les messages d’erreur de formulaire créés par le client ne sont pas traduits

Correction d’un problème en raison duquel les messages d’erreur de validation du client n’étaient pas correctement traduits et formatés sur différentes interfaces. Les erreurs de validation affichent désormais les messages correctement traduits dans toutes les zones de l’application : storefront, adminhtml, api REST et graphql.

_ACP2E-4354 - [contribution du code GitHub](https://github.com/magento/magento2/commit/31258bf6)_

### Interface utilisateur d’administration

#### Les colonnes Produits de la catégorie Grille > Statut et visibilité sont vides lors du tri par nom

Correction d’un problème en raison duquel les colonnes Statut et Visibilité apparaissaient vides dans la grille Produits de catégorie lors du tri par nom de produit.
La grille affiche désormais correctement toutes les données de colonne après le tri, ce qui garantit l’exactitude des informations sur les produits dans le panneau d’administration.

_AC-10659 - [Problème GitHub](https://github.com/magento/magento2/issues/38233) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/3cf1a106)_

#### Sélecteur de magasin de modèles d’e-mail

Correction d’un problème en raison duquel le sélecteur de boutiques dans l’aperçu du modèle d’e-mail de la newsletter ne s’ouvrait pas lorsque l’utilisateur cliquait dessus en raison d’un code jQuery obsolète. La mise à jour de l’événement de chargement a restauré les fonctionnalités appropriées, permettant aux utilisateurs d’accéder au sélecteur de magasin comme prévu.

_AC-12334 - [Problème GitHub](https://github.com/magento/magento2/issues/38892) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/8670a2b4)_

#### Les valeurs FPT dans la page de panier et la page de produit sont différentes pour les mêmes configurations pour les produits simples

Les valeurs FPT sont désormais cohérentes entre les pages de panier et de produit pour les produits simples.
Auparavant, les valeurs de taxe sur les produits fixes (FPT) pouvaient différer en chiffres décimaux entre le panier et les pages de produits, même lorsque les mêmes configurations étaient appliquées.
AC-13066

_AC-13066 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/8953613e)_

#### Les options d’attribut Sélection multiple/Sélection multiple ne peuvent pas être enregistrées lorsque les modules Nuanciers sont désactivés

Les options d’attribut Sélection multiple/Sélection multiple peuvent désormais être enregistrées lorsque les modules Nuanciers sont désactivés.
Auparavant, la désactivation des modules Nuanciers provoquait des exceptions lors de la création d’options d’attributs de sélection multiple/sélection.
AC-13071

_AC-13071 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/8953613e)_

#### Les valeurs FPT dans la page de panier et la page de produit sont différentes pour les mêmes configurations pour un produit dynamique

Les valeurs FPT sont désormais cohérentes entre les pages de panier et de produit pour les produits dynamiques.
Auparavant, les valeurs FPT (taxe fixe sur les produits) pouvaient différer en termes de décimales entre le panier et les pages de produits pour les mêmes configurations.
AC-13075

_AC-13075 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/8953613e)_

#### Format de date non respecté dans le composant d’interface utilisateur de date

Correction d’un problème en raison duquel le composant d’interface utilisateur de date ignorait le format configuré et affichait des valeurs incorrectes. Le correctif garantit que le champ de date respecte désormais le format spécifié (par exemple, Y-m-d) pour l’affichage et la saisie.

_AC-13174 - [Problème GitHub](https://github.com/magento/magento2/issues/39218) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/913bf1a6)_

#### Aucune option disponible pour supprimer des sources

Ajout d’une option de suppression pour les sources d’inventaire dans l’interface utilisateur d’administration, qui permet aux administrateurs de supprimer des sources supplémentaires au lieu de seulement les activer ou les désactiver. Cette amélioration améliore la gestion des stocks en permettant un meilleur contrôle des sources inutilisées.

_AC-13354 - [Problème GitHub](https://github.com/magento/magento2/issues/32362) - [Contribution du code GitHub](https://github.com/magento/inventory/commit/1b6c8a3e)_

#### L’arborescence des catégories dans admin n’est pas développée pour afficher toutes les catégories imbriquées sélectionnées du niveau 3

Correction d’un problème en raison duquel l’arborescence de catégories d’administration ne s’étendait pas pour afficher les catégories imbriquées sélectionnées au-delà du niveau 3. Après la correction, toutes les catégories sélectionnées sont automatiquement étendues, améliorant la visibilité et la convivialité dans toutes les conditions liées aux catégories.

_AC-13363 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/913bf1a6)_

#### [Problème] Améliorer l’expérience utilisateur grâce à l’arborescence des rôles

Cette demande d’extraction ajoute des boutons pour tout réduire, tout développer et développer les branches avec les éléments sélectionnés. Cette fonctionnalité est similaire à celle fournie dans l’arborescence des catégories (Catalogue -> Inventaire -> Catégories)

_AC-14020 - [Problème GitHub](https://github.com/magento/magento2/issues/39654) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/36511)_

#### Les journaux d’actions d’import/export ne sont pas créés dans Système > Journaux d’actions > Grille de rapports

Journalisation implémentée pour les actions d’administration d’import/export afin qu’elles apparaissent désormais dans Système > Journaux d’actions > Rapport. Vous obtiendrez ainsi un meilleur suivi des audits en enregistrant les activités d’importation qui étaient auparavant manquantes.

_AC-14266 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/b5e99d20)_

#### Symfony\Component\Mime\Exception\LogicException : l’en-tête « Sender » doit être une instance de « Symfony\Component\Mime\Header\MailboxHeader » (obtenu « Symfony\Component\Mime\Header\MailboxListHeader »)

Adobe Commerce envoie désormais avec succès des e-mails d’enregistrement lorsqu’une adresse de chemin de retour personnalisée est configurée pour SMTP. Auparavant, sur Adobe Commerce 2.4.8 classique avec system/smtp/set_return_path défini sur 2 et system/smtp/return_path_email défini sur une adresse personnalisée, l’enregistrement du client s’est terminé mais l’e-mail d’enregistrement n’a pas été envoyé, et Adobe Commerce a consigné cette erreur : Symfony\Component\Mime\Exception\LogicException : l’en-tête « Sender » doit être une instance de « Symfony\Component\Mime\Header\MailboxHeader » (obtenu « Symfony\Component\Mime\Header\MailboxListHeader »).

_AC-14520 - [Problème GitHub](https://github.com/magento/magento2/issues/39823) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/1e14bd72) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/1514117f)_

#### L’ordre d’actualisation n’obtient pas les dernières données d’attribut personnalisé

Correction d’un problème en raison duquel l’actualisation de la page de commande n’affichait pas les dernières données d’attribut personnalisé du client ; après le correctif, les valeurs d’attribut mises à jour sont désormais reflétées sans qu’il soit nécessaire d’annuler et de recréer la commande.

_AC-14690 - [Problème GitHub](https://github.com/magento/magento2/issues/30301)_

#### [Problème] remplacer l’échappement obsolète

Suppression de l’échappement obsolète getEscaper() et ajout par injection de constructeur.

_AC-15132 - [Problème GitHub](https://github.com/magento/magento2/issues/40062) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38135)_

#### Message de bienvenue qui chevauche la catégorie de produits dans la vue mobile

Correction d’un problème de l’interface utilisateur en raison duquel le nom de bienvenue chevauchait des catégories de produits dans la vue mobile, bloquant les clics.
Désormais, les catégories sont entièrement visibles et cliquables sans problèmes de chevauchement.

_AC-15166 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/1b1baf1d)_

#### Le bouton de réinitialisation du formulaire de l’interface utilisateur ne fonctionne pas comme prévu

Le système fonctionne maintenant correctement lorsque vous cliquez sur le bouton de réinitialisation sans recharger la page entière, les données du formulaire sont réinitialisées.

_AC-15204 - [Problème GitHub](https://github.com/magento/magento2/issues/40092) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40094)_

#### [Problème] PageCache/AccessList : ajouter la prise en charge CIDR

Le système accepte désormais les demandes de purge au sein d’un réseau. Il est plus facile de simplement fournir une plage CIDR.

_AC-15804 - [Problème GitHub](https://github.com/magento/magento2/issues/39953) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37809)_

#### [Problème ] ajoutez des titres explicatifs aux boutons de gestion du cache.

Le système ajoute désormais des titres explicatifs aux boutons de gestion du cache lorsque vous déplacez le curseur

_AC-16212 - [Problème GitHub](https://github.com/magento/magento2/issues/38607) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38598)_

#### Fournir une fonctionnalité pour supprimer en masse les taux de taxe à l’aide de la grille

Les utilisateurs administrateurs peuvent désormais supprimer simultanément plusieurs taux de taxe de la grille Taux de taxe d&#39;administration .  [GitHub-33399](https://github.com/magento/magento2/issues/33399)

_AC-2238 - [Problème GitHub](https://github.com/magento/magento2/issues/33399) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/33484) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/5cd64dd0)_

#### Couleur de pointage non appliquée aux grilles statiques dans l’administration

Les couleurs de survol sont désormais appliquées comme prévu sur les lignes des grilles statiques d’administration.[GitHub-35358](https://github.com/magento/magento2/issues/35358)

_AC-2916 - [Problème GitHub](https://github.com/magento/magento2/issues/35358) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/35384)_

#### « Impossible de résoudre les entrées du paramètre reCAPTCHA » dans exception.log pour le panneau d’administration reCAPTCHA de Google

Une erreur reCaptcha dans le fichier `var/log/exception.log` pour la connexion d’administrateur reCAPTCHA de Google V3 a été résolue, et aucun message d’erreur n’est consigné. Auparavant, l’erreur suivante était générée toutes les quelques secondes lorsqu’un utilisateur administrateur configurait les paramètres **Configuration** > **Sécurité** > **Panneau d’administration reCAPTCHA de Google** : `main.ERROR: Can not resolve reCAPTCHA parameter. {"exception":"[object] (Magento\Framework\Exception\InputException(code: 0): Can not resolve reCAPTCHA parameter. at /home/xxxxxxx/public_html/vendor/magento/module-re-captcha-ui/Model/CaptchaResponseResolver.php:25)"} []`.  [GitHub-34975](https://github.com/magento/magento2/issues/34975)

_AC-3179 - [Problème GitHub](https://github.com/magento/magento2/issues/34975) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/4f7e5983) - [Contribution du code GitHub](https://github.com/magento/security-package/commit/804dbc2a)_

#### La règle de prix du panier avec la condition SKU ne prend pas en compte les « zéros de début » dans le SKU (SKU : 01234 est le même que 1234)

Le système gère désormais correctement la règle de prix du panier avec la condition SKU prenant en compte les « zéros au début » dans le SKU

_AC-9428 - [Problème GitHub](https://github.com/magento/magento2/issues/37919) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39525)_

#### Problème lié au comportement de la valeur d’option d’attribut par défaut pour la sélection multiple

Avant la correction, les valeurs par défaut de plusieurs attributs d’options n’étaient pas enregistrées correctement. Désormais, après le correctif, les valeurs sont correctement stockées dans la base de données.

_ACP2E-3523 - [contribution du code GitHub](https://github.com/magento/magento2/commit/9608ca21)_

#### Problème lors du déplacement de la quantité de produit de l’administrateur vers le panier

Lors de la création d’une commande à partir de l’administrateur, les produits du panier client dans la barre latérale ne disparaissent pas lorsqu’ils sont ajoutés à la commande.

_ACP2E-3563 - [contribution du code GitHub](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### [Staging2] Les cartes stockées ne sont pas visibles dans le panneau d’administration.

Correction du problème en raison duquel l’option de paiement « Carte stockée » n’apparaissait plus dans le formulaire de placement de commande du serveur principal après une mise à niveau.

_ACP2E-3830 - [contribution du code GitHub](https://github.com/magento/magento2/commit/7accebfa)_

#### L’utilisateur administrateur restreint peut enregistrer/mettre à jour les configurations par défaut malgré les autorisations spécifiques au magasin.

Correction du problème en raison duquel des utilisateurs administrateurs restreints pouvaient afficher et tenter de mettre à jour la portée « Configuration par défaut » bien qu’elle ait été affectée uniquement à des portées de site web spécifiques, ce qui pouvait prêter à confusion.

_ACP2E-4011 - [contribution du code GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Prix du produit configurable enregistré sous la base de données pour toute portée d’affichage du magasin, ce qui entraîne des problèmes dans la fonctionnalité de tri des produits de la catégorie lorsque le prix enregistré n’a aucune pertinence dans frontend.

Suppression de la case à cocher « Utiliser la valeur par défaut » pour un produit configurable lorsque le prix est configuré par site web et qu’une vue de magasin est sélectionnée sur la page de modification de produit configurable de l’interface utilisateur d’administration.

_ACP2E-4036 - [contribution du code GitHub](https://github.com/magento/magento2/commit/fab20b00)_

#### La politique de mot de passe [QUANS]Admin ne respecte pas la conformité PCI DSS 4.0 (minimum 12 caractères)

Les administrateurs peuvent désormais configurer la longueur minimale de mot de passe requise pour les utilisateurs administrateurs via Magasins > Configuration > Avancé > Admin > Sécurité. Cette amélioration offre une plus grande flexibilité en matière de sécurité tout en conservant les politiques de mot de passe existantes. La validation est appliquée à la fois lors de la création/modification de l’utilisateur administrateur et des enregistrements de configuration, avec une validation frontale en temps réel pour une expérience utilisateur améliorée.

_ACP2E-4044 - [contribution du code GitHub](https://github.com/magento/magento2/commit/47721be6)_

#### Problème de filtre de date lorsque la langue de l’interface d’administration est le japonais

Le filtre et la colonne Anniversaire utiliseront le format unifié J/J/a, identique au filtre/à la colonne « Client depuis »

_ACP2E-4052 - [Problème GitHub](https://stg1.navi-online.kakuyasu.co.jp/adminCgWN7zCh/admin/system_account/index/key/d6fdbee50ff25178d1fef981ec823c5e82e8cee6959717790031bb900c4d6633/) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/52f46328)_

#### Blocs blancs apparaissant des deux côtés de l’en-tête de la grille d’administration

Correction d’un problème d’alignement visuel dans les grilles d’administration. Auparavant, lors du défilement horizontal dans les grilles de produit du panneau d’administration, les blocs blancs semblaient mal alignés sur les côtés gauche et droit de l’en-tête de grille. Les éléments d’en-tête de grille conservent désormais un alignement vertical correct lors du défilement, offrant ainsi une expérience visuelle plus nette aux administrateurs et administratrices qui gèrent des catalogues de produits volumineux.

_ACP2E-4104 - [Problème GitHub](https://mcprod.pap-store.acer.com/index.html)_

#### Le composant d’interface utilisateur fileUploader ne fonctionne pas correctement sous 2.4.8-p1/ 2.4-develop

Amélioration du chargement de fichier pour le composant d’interface utilisateur personnalisé avec plusieurs sélections pour autoriser le chargement lors des clics de la zone de chargement.

_ACP2E-4162 - [contribution du code GitHub](https://github.com/magento/magento2/commit/ee918f0d)_

#### [Sur site] les commandes/sociétés/clients nouvellement créées automatiquement incluses dans la portée « Tout sélectionner » pendant le processus de sélection

Correction du problème en raison duquel la sélection manuelle de tous les enregistrements sur une page de grille d’administration obsolète supprimait involontairement tous les enregistrements lors de l’exécution d’actions en masse. Auparavant, la grille passait automatiquement en mode « tout sélectionner » en interne lorsque le nombre d’éléments sélectionnés correspondait au nombre total, ce qui entraînait des actions en masse affectant tous les enregistrements au lieu de seulement ceux explicitement sélectionnés.

_ACP2E-4202 - [contribution du code GitHub](https://github.com/magento/magento2/commit/6e134409)_

#### La solution de ACP2E-3362 fonctionne lentement sur MariaDB 10.6

Amélioration des performances de la page de recherche front-end en cas de grand nombre de requêtes de recherche historiques.

_ACP2E-4225 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/ab891304)_

#### Le filtre de date ne fonctionne pas selon le fuseau horaire du magasin dans la grille Avoirs

Avant la correction, les listes de filtrage par attributs de date provoquaient des éléments manquants en raison des différences de fuseau horaire entre la date sélectionnée et les dates stockées. Maintenant, une fois les filtres de date de correction correctement appliqués.

_ACP2E-4239 - [contribution du code GitHub](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### La boîte de dialogue de chargement de fichier s’ouvre deux fois lorsque pagebuilder est installé

Avant que le bouton Corriger le chargement de composant personnalisé ne se déclenche deux fois. Après la correction, le bouton Charger fonctionne comme prévu.

_ACP2E-4241 - [contribution du code GitHub](https://github.com/magento/magento2-page-builder/commit/5c4ae802)_

#### Erreurs de validation sur les attributs du client supprimés lors de la modification des données client.

Avant la correction, l’enregistrement du client et de l’adresse du client échouait s’ils incluaient plusieurs options d’attribut qui avaient été supprimées. Après le correctif, les deux peuvent être enregistrés avec succès même lorsque plusieurs options d’attribut sont toujours présentes.

_ACP2E-4281 - [contribution du code GitHub](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### Avertissement JS dans le tableau de bord d&#39;administration : « Il était prévu de démarrer le chargeur, mais aucun n&#39;a été trouvé dans le DOM »

Correction de l’avertissement JavaScript qui s’affichait dans la console du navigateur lorsque les graphiques étaient activés pour le tableau de bord d’administration. Auparavant, lors de l’accès au tableau de bord d’administration avec les graphiques activés, une vérification de débogage obsolète avertissait à tort « Il était prévu de démarrer le chargeur, mais n’en a pas trouvé un dans le DOM », même si la fonctionnalité fonctionnait correctement.

_ACP2E-4336 - [contribution du code GitHub](https://github.com/magento/magento2/commit/2687b487)_

#### Configuration [CLOUD] avec configuration de dépendance modifiable lors de l’utilisation de la configuration de magasin par défaut archivée

Correction du problème en raison duquel les champs de configuration système pouvaient être activés après le chargement de la page, bien que l’option « Utiliser par défaut/site web » soit cochée.

_ACP2E-4337 - [Problème GitHub](https://mcstaging.pap-store.acer.com) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/31258bf6)_

#### Le graphique d’ordre du tableau de bord d’administration s’anime en taille finale

Le graphique d’ordre du tableau de bord d’administration s’affiche désormais immédiatement, sans qu’il soit nécessaire d’ajouter une animation de redimensionnement.

_ACP2E-4398 - [Problème GitHub](https://github.com/magento/magento2/issues/38860) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/f7bbcb4e)_

#### Page Builder ne parvient pas à enregistrer le contenu en mode mobile en raison d’une erreur JS (TypeError : impossible de lire les propriétés de l’élément non défini)

Correction d’un problème qui empêchait l’enregistrement des pages dans Page Builder lors de l’ajout de bannières dans la vue mobile.

_ACP2E-4399 - [Problème GitHub](https://github.com/magento/magento2/issues/38565) - [Contribution du code GitHub](https://github.com/magento/magento2-page-builder/commit/bdac5bca)_

### Interface utilisateur d’administration, B2B

#### La connexion B2B en tant qu’en-tête client comporte toujours l’identité de marque Magento

Auparavant, l’en-tête du storefront affichait « Vous êtes désormais connecté en tant que &lt;nom du client> sur &lt;nom du magasin> » avec l’identité graphique de Magento. Ce problème est maintenant résolu et l’en-tête s’affiche avec le branding ADOBE.

_AC-14361 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/fadcfa8b)_

### Interface utilisateur d’administration, catalogue

#### L’enregistrement du produit échoue lorsque la règle de catalogue est active et que le mode Temps réel est activé

Correction d’un problème en raison duquel l’indexation des règles de catalogue pouvait échouer avec une erreur de transaction DDL lors des opérations d’enregistrement de produit en découplant l’indexation des règles de catalogue de la transaction de produit.

_ACP2E-4378 - [contribution du code GitHub](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Interface utilisateur d’administration, contenu

#### Exception « Impossible de créer un rendu pour les chemins d’accès aux ressources multimédias » lors de l’insertion de l’image

Après avoir supprimé les valeurs de Largeur maximale et Hauteur maximale de la configuration de l’optimisation des images de la Galerie de médias, l’erreur ne s’est plus produite pendant le processus d’optimisation des images.

_ACP2E-3781 - [contribution du code GitHub](https://github.com/magento/magento2/commit/520f9e30)_

### Interface utilisateur d’administration, commande

#### Création de commande administrateur : dépassement de la taille de la session lors de l’ajout de 20 produits et plus (la taille de la session a dépassé la limite de 256KB)

Correction d’un dépassement de taille de session lors de la création d’une commande d’administration en empêchant le stockage de réponses HTML volumineuses dans la session pour les requêtes JSON, ce qui garantissait le bon fonctionnement des ajouts de produits en bloc sans déconnecter l’administrateur.

_AC-15893_

### Interface utilisateur d’administration, sécurité

#### Gestion des mots de passe faibles

L’utilisateur administrateur ne peut pas être enregistré avec le même mot de passe. Auparavant, il était enregistré sans validation appropriée.

_ACP2E-3657 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/df92debe)_

### Interface utilisateur d’administration, fiscalité

#### Erreur de l’interface utilisateur d’administration du taux de taxe

Ce ticket a corrigé un problème d’interface utilisateur d’administration du taux d’imposition en raison duquel le changement de pays (par exemple, des États-Unis → du Royaume-Uni) affichait toujours l’état des États-Unis sélectionné précédemment, induisant les utilisateurs en erreur.
Dans la version 2.4.9-alpha3, le champ État est désormais réinitialisé sur * lorsque le pays sélectionné n’a pas d’État.

_AC-8440 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

### Analyses / Rapports

#### placer sur la liste autorisée [Problème] Ajout du scp pour Analytics si vous utilisez uniquement Google Analytics

Cette requête de modification ajoute une liste autorisée CSP au module Google Analytics, lui permettant de fonctionner indépendamment sans dépendance Google Adwords. Google Analytics fonctionne désormais correctement même lorsque le module Google Adwords est désactivé.

_AC-16311 - [Problème GitHub](https://github.com/magento/magento2/issues/40051) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40032)_

#### Les en-têtes de fichier en double dans les fichiers CSV de rapports avancés entraînent des rapports vides

Après la correction, les rapports générés pour la fonctionnalité de création de rapports avancée ne contiennent plus de lignes d’en-tête dupliquées dans les cas où le nombre de lignes dépasse la taille du lot.

_ACP2E-4187 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/45cbf9b6)_

#### Le rapport de panier abandonné contient des caractères non valides

Le rapport de panier abandonné exporté sous forme de fichier CSV contient désormais des caractères correctement rendus pour les symboles de devise tels que la roupie indienne lorsqu’il est ouvert dans MS Excel.

_ACP2E-4288 - [contribution du code GitHub](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### Mise à jour de la compatibilité avec MDVA-19640 pour la version 2.4.8

Le correctif déplace les tâches de tâche cron Analytics du groupe par défaut vers le groupe Analytics

_ACP2E-4309 - [contribution du code GitHub](https://github.com/magento/magento2/commit/c135fc3a)_

#### Les revenus ne s&#39;affichent pas dans les rapports de commandes/factures sur le site Web/dans la devise d&#39;Admin for Canada

Certains des rapports liés aux commandes n&#39;appliquaient pas les taux de change du magasin. Après le correctif, les rapports appliquent correctement les taux de magasin configurés.

_ACP2E-4361 - [contribution du code GitHub](https://github.com/magento/magento2/commit/31258bf6)_

### B2B

#### la validation du champ entreprise échoue pour le passage en caisse des invités

Le passage en caisse des invités valide désormais correctement le champ société.
Auparavant, lorsque l’attribut d’entreprise était obligatoire, l’extraction des invités échouait avec l’erreur « La société est une valeur obligatoire », même lorsque le champ était rempli.
AC-14987

_AC-14987 - [Problème GitHub](https://github.com/magento/magento2/issues/40011) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/f1adb44e)_

#### Rest API products-render-info renvoie un prix final incorrect pour le client connecté

Le ticket comporte un correctif pour API REST products-render-info qui renvoie un prix final incorrect pour le client connecté

_AC-5979 - [Problème GitHub](https://github.com/magento/magento2/issues/35757)_

### B2B, panier et passage en caisse

#### Aucune entité de ce type avec cartId = X erreur ne s’affiche sur Storefront lors de la connexion à l’utilisateur de la société B2B à partir de la fonctionnalité d’administration « Connexion en tant que client »

Désormais, l’erreur « Aucune entité de ce type avec cartId = X » n’est plus visible après la connexion réussie à partir du serveur principal d’administration lors de l’utilisation de la fonctionnalité « Connexion en tant que client ».

_ACP2E-3994 - [contribution du code GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

#### L&#39;adresse de facturation manquante empêche de passer une commande avec la méthode d&#39;expédition « Livraison en magasin »

Correction d’un problème en raison duquel l’adresse de facturation n’était pas automatiquement renseignée lors du passage en caisse lorsque la cueillette en magasin était sélectionnée comme méthode de diffusion. Sans adresse de facturation, le passage en caisse n’a pas pu être effectué.

_ACP2E-4030 - [contribution du code GitHub](https://github.com/magento/inventory/commit/42d23211)_

### Panier et passer en caisse

#### mise à jour de Magento 2.4.7 (mini)panier aucune quantité décimale autorisée

Désormais, Magento gère correctement lorsque nous mettons à jour la quantité avec des décimales du mini panier lorsque le paramètre régional était NL (néerlandais)

_AC-13238 - [Problème GitHub](https://github.com/magento/magento2/issues/39236) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39669)_

#### [Problème] Ajoutez EventPrefix et EventObject au modèle de contrat d’extraction

Le système inclut désormais EventPrefix et EventObject pour le modèle de contrat de passage en caisse, ce qui permet de déclencher les événements avec un préfixe d’événement. Cette amélioration offre davantage de flexibilité aux développeurs lorsqu’ils travaillent avec des événements d’accord de passage en caisse. Auparavant, le modèle d’accord de passage en caisse ne prenait pas en charge EventPrefix et EventObject, ce qui limitait la possibilité de personnaliser la gestion des événements.

_AC-13252 - [Problème GitHub](https://github.com/magento/magento2/issues/32510) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/32451)_

#### [Problème ] Expérience de développement : style de code Quote AbstractItem (SOP-348 de SwiftOtter)

Cette demande d&#39;extraction corrige les déclarations de méthode trompeuses pour les méthodes d&#39;élément abstrait.

_AC-13334 - [Problème GitHub](https://github.com/magento/magento2/issues/39340)_

#### Les validations de quantité frontale de produit groupé sont manquantes.

Le système fonctionne maintenant correctement et affiche une erreur de validation lorsque nous tentons d’ajouter une quantité négative et une quantité maximale

_AC-13524 - [Problème GitHub](https://github.com/magento/magento2/issues/39479) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39480)_

#### [Problème] Mettre à jour le sous-total.phtml

Le système met à jour le fichier subtotal.phtml avec l&#39;espacement approprié

_AC-13907 - [Problème GitHub](https://github.com/magento/magento2/issues/39619) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39612)_

#### Impossible de passer la commande auprès de l’invité

Adobe Commerce permet désormais aux acheteurs invités de passer des commandes avec succès lorsque le champ Deuxième prénom est configuré comme requis dans l’administration. Auparavant, dans Adobe Commerce 2.4.8-beta1 (PHP 8.3/8.4), la configuration du deuxième prénom selon les besoins et le passage en caisse en tant qu’invité empêchaient le placement de la commande même si un deuxième prénom était fourni, bloquant ainsi la fin du passage en caisse. AC-14241

_AC-14241 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/27217d0e)_

#### [Graphql] Impossible de renvoyer la valeur null pour le champ « SelectedCustomizableOption.label » qui n’accepte pas les valeurs Null

Le système ne renvoie plus d’erreur de serveur interne avec le message lorsque l’option sélectionnée n’existe plus

_AC-14256 - [Problème GitHub](https://github.com/magento/magento2/issues/39729) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39888)_

#### GraphQL addWishlistItemsToCart ne parvient pas à mettre à jour la quantité d’éléments de panier existants lorsqu’un élément de liste de souhaits n’est pas valide (Magento 2.4.7-p3)

Correction d’un problème en raison duquel la mutation GraphQL addWishlistItemsToCart arrêtait le traitement lorsqu’un produit configurable non valide était rencontré. Après la correction, les articles de liste de souhaits valides sont ajoutés au panier et les quantités sont mises à jour, tandis que les articles non valides sont ignorés avec les erreurs appropriées renvoyées.

_AC-14464 - [Problème GitHub](https://github.com/magento/magento2/issues/39820) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/3cf1a106)_

#### [2.4.8] Impossible de passer des commandes lorsque la ville comporte les chiffres 0 à 9, l&#39;esperluette, un point ou une parenthèse dans le nom de la ville

Correction d’un problème en raison duquel le passage en caisse échouait pour les noms de ville contenant des caractères spéciaux tels que . , &amp;, ou des parenthèses.
Désormais, les commandes avec ces noms de ville sont passées sans erreurs de validation.

_AC-14495 - [Problème GitHub](https://github.com/magento/magento2/issues/39854) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### Préfixe invité non enregistré dans l’adresse de devis 2.4.8

Le préfixe client invité (M./Mme) est désormais enregistré lors du passage en caisse.
Auparavant, les salutations sélectionnées par les clients invités étaient perdues avant d’atteindre la commande finale, tandis que tous les autres champs d’adresse étaient correctement transférés.
AC-14705

_AC-14705 - [Problème GitHub](https://github.com/magento/magento2/issues/39915) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/f1adb44e)_

#### La sous-sélection de règle de vente avec la condition Quantité ne s&#39;applique pas

Correction d’un problème en raison duquel les règles de prix de panier avec des conditions de sous-sélection de produit ne s’appliquaient pas au passage en caisse.
Désormais, les remises sont appliquées conformément aux règles configurées.

_AC-14884 - [Problème GitHub](https://github.com/magento/magento2/issues/39965) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/fe72c407)_

#### [Problème ] supprimer l’espace dans l’attribut de classe

Le système supprime désormais un espace supplémentaire dans l’attribut class

_AC-14939 - [Problème GitHub](https://github.com/magento/magento2/issues/39977) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39970)_

#### Graphql - Le panier de fusion ne fonctionne pas correctement lorsque la commande Backorder est activée

Correction d’un problème en raison duquel les articles du panier d’invités n’étaient pas fusionnés avec le panier client lors de la fusion du panier via GraphQL.
Désormais, le panier client reflète correctement la quantité combinée des paniers client et invité.

_AC-15148 - [Problème GitHub](https://github.com/magento/magento2/issues/40064) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### [Intégration] [Passage en caisse] directives dépendantes mises à jour dans le modèle d’e-mail de paiement ayant échoué

Modèle d&#39;e-mail de paiement en échec mis à jour pour gérer correctement les directives dépendantes.
Correction garantit que l’adresse et le mode d’expédition s’affichent correctement, le cas échéant.
Auparavant, ces champs étaient manquants dans les e-mails de paiement en échec.

_AC-15363 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

#### [Panier] La page Panier ne se charge pas lorsque la taxe fixe sur les produits est activée

Correction d’un problème en raison duquel la page du panier entrait en chargement infini lorsque la taxe sur les produits fixes (FPT) était activée. Le problème était dû à des calculs de sous-totaux incorrects en raison de la taxe incluse dans le même élément HTML que le prix de l&#39;article, ce qui entraînait une incohérence entre les sous-totaux centraux et les sous-totaux de synthèse. Après le correctif, le panier se charge correctement et affiche des totaux précis.

_AC-16096 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/01cee3c3)_

#### Règle de prix du panier Action Condition « Prix dans le panier », applicable dans le cas contraire

Correction d’un problème en raison duquel les règles de prix de panier avec la condition « Prix dans le panier inférieur à » étaient incorrectement appliquées aux produits non éligibles.
Désormais, les coupons sont correctement validés et rejetés lorsque les prix des articles du panier ne répondent pas aux conditions de la règle configurée.

_AC-6997 - [Problème GitHub](https://github.com/magento/magento2/issues/36433) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/01cee3c3)_

#### [Problème] Définissez le prix sur l&#39;article du devis au lieu de prix_de_base

Le système gère correctement le prix de l&#39;article du devis défini sur base_price au lieu du prix si vous avez plusieurs devises dans un site Web sur le front-end

_AC-9985 - [Problème GitHub](https://github.com/magento/magento2/issues/38094) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/36878)_

#### Les devis persistants expirés ne sont pas nettoyés par un traitement cron sales_clean_quotes

Les guillemets persistants expirés sont désormais effacés lorsque la tâche cron &#39;persistent_clear_expired&#39; s&#39;exécute. Auparavant, les guillemets persistants expirés n’étaient effacés par aucune autre tâche cron.

_ACP2E-3493 - [contribution du code GitHub](https://github.com/magento/magento2/commit/11be3dff)_

#### Erreur « Un problème est survenu » lors du passage en caisse pour une entreprise inactive

Avant le correctif, l’action de déconnexion n’était pas correctement effectuée sur la page du panier si la société de l’utilisateur connecté n’était plus activée. Désormais, si l’entreprise n’est plus disponible, la déconnexion est correctement effectuée.

_ACP2E-3541 - [contribution du code GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### La sélection des adresses n’est pas enregistrée lorsque nous « Extrayons avec plusieurs adresses »

Avant la correction lors de l’annulation de l’option d’expédition multiple, l’adresse n’était pas présélectionnée lors du retour à l’expédition multiple. Désormais, l’adresse par défaut est remplacée par l’une des sélections effectuées dans l’écran d’expédition multiple.

_ACP2E-3646 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/6ea61121)_

#### [Cloud] Les commandes récentes n’apparaissent pas dans l’autre vue de magasin si les commandes sont créées sur une vue de magasin.

Correction d’un problème en raison duquel la page « Mon compte » n’affichait pas les commandes récentes provenant d’autres affichages de la boutique dans la même boutique. La logique de récupération des commandes a été mise à jour afin de garantir une visibilité cohérente des commandes dans toutes les vues de la boutique, conformément au comportement de la page « Mes commandes ».

_ACP2E-3807 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a20a6ff2)_

#### qté sous forme  0 dans la section panier client administrateur lors de l’ajout de produits BUNDLE  

La section Panier des Activités clients affiche désormais la quantité correcte. Auparavant, la quantité s’affichait sous la forme 0.

_ACP2E-3872 - [contribution du code GitHub](https://github.com/magento/magento2/commit/3ad96f6a)_

#### [Cloud] réduction sur la livraison gratuite non correctement supprimée lorsque le panier ne répond plus aux exigences

Le Sous-Total (Hors Taxe) dans la règle de prix de panier incorporera désormais les remises des règles précédentes.

_ACP2E-3973 - [contribution du code GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Commande en double trouvée pour le même client dans Multishipping

Les demandes simultanées de passation de commande avec plusieurs adresses d’expédition n’entraînent plus de commandes dupliquées pour un même client

_ACP2E-4117 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [Cloud] Le message de notification Limite de stock dépassée s’affiche deux fois lorsque le seuil de rupture de stock est atteint

Correction du problème en raison duquel les mises à jour du panier pouvaient afficher des bannières d’erreur en double. Auparavant, après une erreur de validation AJAX, le serveur principal ajoutait à nouveau le même message lors de l’envoi du formulaire, de sorte que les acheteurs voyaient deux alertes identiques. Maintenant, nous ignorons l’ajout du message d’arrière-plan supplémentaire, ce qui conserve la page du panier sur une seule bannière d’erreur claire.

_ACP2E-4192 - [contribution du code GitHub](https://github.com/magento/magento2/commit/e885088b)_

#### Pour les informations de facturation, la validation côté serveur ne fonctionne pas à l’aide de l’API REST shipping-information

La validation des données d’adresses client a été améliorée afin d’être plus cohérente entre REST et GraphQl pour le passage en caisse.

_ACP2E-4223 - [contribution du code GitHub](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### [Cloud] Problème de prix de bundle du produit sur la page du panier

Correction du problème de prix du produit groupé sur la page du panier pour les magasins multidevises

_ACP2E-4245 - [Problème GitHub](https://www.techbuyer.com/) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/cbca0396)_

#### Gérer les problèmes d’étendue du magasin de panier

Désormais, les erreurs de panier s’affichent pour l’utilisateur administrateur lors de la gestion du panier d’un client affecté à un site web autre que celui par défaut. Auparavant, les erreurs n’étaient pas affichées.

_ACP2E-4348 - [contribution du code GitHub](https://github.com/magento/magento2/commit/31258bf6)_

#### Le coupon times_used se réinitialise après l&#39;annulation partielle de la facture

Le comptage des heures de coupon_utilisées est désormais correctement mis à jour lorsqu’une commande est partiellement annulée.

_ACP2E-4365 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/61c96348)_

### Panier et passer en caisse, GraphQL

#### Erreur lors du mappage du message au code d’erreur lors de la commande via GraphQL

Les appels GraphQL pour passer une commande pour un panier inexistant ou inactif renvoient désormais correctement les codes d’erreur CART_NOT_ACTIVE ou CART_NOT_FOUND dans toutes les vues du magasin. Cela résout un problème en raison duquel les messages d’erreur traduits entraînaient auparavant un code UNDEFINED.

_ACP2E-3942 - [contribution du code GitHub](https://github.com/magento/magento2/commit/7accebfa)_

#### Problème de remise d’article de panier de requête de panier [GraphQl] sur les devis virtuels

Correction d’un problème en raison duquel la requête de panier GraphQL renvoyait un montant de remise incorrect pour les devis virtuels. Auparavant, les remises étaient appliquées de manière incorrecte à certains produits virtuels qui n’étaient pas éligibles.

_ACP2E-4248 - [contribution du code GitHub](https://github.com/magento/magento2/commit/cbca0396)_

#### [Cloud] ACSD-68499_2.4.8-p2 crée un autre problème

Lorsqu’une demande graphQL pour un article avec une quantité insuffisante a été effectuée, un message d’erreur correct avec un code d’erreur a été renvoyé et si la quantité demandée est disponible, la mise à jour du panier a réussi.

_ACP2E-4404 - [contribution du code GitHub](https://github.com/magento/magento2/commit/1c547060)_

### Panier et passer en caisse, GraphQL, Inventaire / MSI

#### L&#39;attribut is_available dans CartItemInterface renvoie la valeur false même lorsque le stock vendable est élevé

L&#39;attribut is_available renvoie la valeur true lorsque le stock vendable est élevé. Auparavant, elle renvoyait toujours la valeur false.

_ACP2E-3885 - [contribution du code GitHub](https://github.com/magento/magento2/commit/3ad96f6a)_

### Panier et passer en caisse, Inventaire / MSI

#### Erreur 414 sur le point d’entrée « Rechercher l’emplacement du retrait » avec des tailles de panier élevées

La sélection d’un magasin lors du passage en caisse à l’aide de « Choisir en magasin » n’échoue plus en raison des longues URL lorsque de nombreux produits se trouvent dans le panier.
Auparavant, cela déclenchait une erreur 414 en raison d’URL trop longues générées lors de la sélection de la boutique, empêchant les clients de terminer le passage en caisse.

_ACP2E-4266 - [Problème GitHub](https://mcstaging.casamyers.com.mx/) - [Contribution du code GitHub](https://github.com/magento/inventory/commit/ae1f272f)_

### Panier et passer en caisse, promotion

#### Le solde affiché sur la carte cadeau n&#39;est pas limité par la portée du site Web

Restriction de la vérification du solde de la carte cadeau avec la portée du site Web attribuée.

_ACP2E-4379 - [problème GitHub](https://www.panini.it)_

### Panier et passage en caisse, sécurité

#### [CLOUD] Obtention du fichier 404 pour JS sur la page de passage en caisse à la première tentative après l’implémentation du correctif SRI

Avant la correction, les mixins n’avaient pas été chargés dans le panier et lors du passage en caisse lorsque la miniaturisation et le regroupement étaient activés. Après le correctif, tous les mixins doivent se charger comme prévu.

_ACP2E-4128 - [Problème GitHub](https://ansg.integration-5ojmyuq-f46gejjrfa7be.ap-3.magentosite.cloud/) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

### Panier et passer en caisse, expédition

#### [Ligne principale] la règle de prix du panier ne respecte pas la livraison multiple

Avant la mise en œuvre de cette correction, la règle de prix du panier pour les produits à expédition multiple ne s’appliquait pas correctement lorsque des conditions de sous-sélection étaient appliquées et que l’expédition gratuite était activée. Cependant, depuis l’application de la correction, la règle de prix de panier pour les paniers à expéditions multiples fonctionne désormais comme prévu.

_ACP2E-3666 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

### Catalogue

#### Dupliquer le fpc de cache pour la même page avec la même requête

Le système identifie et utilise désormais correctement le même Cache de page complet (FPC) pour les pages avec les mêmes paramètres de requête, quel que soit leur ordre ou leurs caractères de fin. Cela évite toute augmentation inutile de la taille du dossier de cache de page. Auparavant, le système créait un identifiant FPC différent pour la même page si l’ordre des paramètres de requête était différent ou s’il y avait des caractères de fin, ce qui entraînait une augmentation de la taille du dossier de cache de page.

_AC-10722 - [Problème GitHub](https://github.com/magento/magento2/issues/38269) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38270)_

#### Indexation manquante des colonnes obligatoires dans la table catalog_product_entity_int

Ajout de l’indexation manquante des colonnes obligatoires dans la table catalog_product_entity_int

_AC-10844 - [Problème GitHub](https://github.com/magento/magento2/issues/38315) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38316)_

#### Bogue d’étendue dans la ressource d’URL de catalogue (_getCategories)

Cette requête de modification ajoute une portée de secours à la portée par défaut si aucune valeur n’est définie sur la portée du magasin dans la ressource d’URL de catégorie.

_AC-11011 - [Problème GitHub](https://github.com/magento/magento2/issues/38393) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38394)_

#### [Problème] Vérifiez si OpenGraph peut afficher le prix

Le système fonctionne correctement lorsque nous utilisons le plug-in qui masque le prix et, avec cette modification, le prix n&#39;est pas visible dans la balise OG.

_AC-11635 - [Problème GitHub](https://github.com/magento/magento2/issues/38512) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38510)_

#### Problème d&#39;arrondi sur les prix lors de l&#39;ajout de la taxe pour afficher les prix

Le système corrige désormais le problème d&#39;arrondi des prix lors de l&#39;ajout de la taxe aux prix affichés

_AC-11725 - [Problème GitHub](https://github.com/magento/magento2/issues/18025) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/35730)_

#### [Problème] Autoriser les conditions des règles de catalogue personnalisées

Correction d’un problème qui empêchait l’utilisation des conditions des règles de catalogue personnalisées en raison d’une vérification de type stricte. Le correctif remplace le contrôle d’égalité de classe par l’instance de , ce qui permet aux classes de conditions personnalisées de fonctionner correctement et d’activer la validation et l’indexation des règles.

_AC-13338 - [Problème GitHub](https://github.com/magento/magento2/issues/39339) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/913bf1a6)_

#### Options de perte de produit configurables lorsqu’elles sont ajoutées à la liste de souhaits

Correction d’un problème en raison duquel les options de produit configurables étaient perdues après l’ajout du produit à la liste de souhaits. Désormais, les options sélectionnées sont conservées, ce qui permet d’ajouter facilement le produit au panier sans inviter les utilisateurs à sélectionner à nouveau les options.

_AC-13373 - [Problème GitHub](https://github.com/magento/magento2/issues/39363) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/cc0ec250)_

#### Le prix spécial ne s&#39;affiche pas correctement pour le produit enfant du produit configurable (produit simple)

Correction d’un problème en raison duquel le prix spécial d’un produit enfant (simple) configurable n’était pas affiché correctement sur la page de liste des produits lorsque la mention « Utilisé dans la liste des produits » était définie sur Non. Désormais, le prix spécial s’affiche correctement avec le prix normal, ce qui garantit une affichage cohérent des prix pour tous les types de produits.

_AC-13594 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/3cf1a106)_

#### [Bug] API REST : la mise à jour des prix spéciaux ne définit pas de valeurs pour toutes les vues de la boutique

L’API REST met désormais à jour les prix spéciaux pour toutes les vues de boutique sur un site web.
Auparavant, la mise à jour des prix spéciaux via l’API REST affectait uniquement l’affichage du magasin spécifié, et non tous les affichages du magasin dans le site web.
AC-13671

_AC-13671 - [Problème GitHub](https://github.com/magento/magento2/issues/39521) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

#### Problèmes de prix et de config.php

Dans Magento 2.4.2, la modification du périmètre de prix via config.php ne met pas correctement à jour la valeur is_global dans catalog_eav_attribute pour l’attribut de prix.
Par conséquent, les prix des produits restent globaux et ne peuvent pas être enregistrés par site web, même si la portée du prix est définie sur site web.
La solution nécessite la mise à jour manuelle de la colonne is_global dans la base de données, ce qui n’est pas idéal pour les environnements de production.
Ce comportement est cohérent avec la conception par défaut de Magento, où la portée du prix est soit Globale soit Site Web, mais pas par vue de magasin.

_AC-13857 - [Problème GitHub](https://github.com/magento/magento2/issues/33559)_

#### [\Magento\ConfigurableProduct\Model\Product\Type\Configurable] Erreur PHP ignorée

Modification du nom d’une variable de boucle afin d’ajouter correctement les données « _cache_instance_product_ids » sur le produit donné à utiliser lors des appels suivants.

_AC-14159 - [Problème GitHub](https://github.com/magento/magento2/issues/39641) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39642)_

#### La recherche élastique interfère avec l’ordre de tri par défaut des produits (du plus récent au plus ancien)

Le système trie désormais les produits les plus récents de la base de données (celui dont le paramètre entity_id est le plus élevé) sont affichés en premier

_AC-14411 - [Problème GitHub](https://github.com/magento/magento2/issues/31043) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/36900)_

#### Après le changement de boutique, la page provient du cache (le sélecteur de boutique ne fonctionne pas) dans la version 2.4.8.

Correction d’un problème en raison duquel le changement de vue de magasin à partir de l’en-tête du storefront ne fonctionnait pas tant que le cache n’était pas effacé manuellement.
Désormais, le changement d’affichage de la boutique fonctionne correctement sans nécessiter de nettoyage du cache.

_AC-14426 - [Problème GitHub](https://github.com/magento/magento2/issues/39806)_

#### Styles .less ignorés avec une largeur minimale : (@screen__l)

Correction d’un problème en raison duquel seuls trois produits s’affichaient par ligne sur les pages de catégorie.
Désormais, quatre produits s’affichent par ligne comme prévu.

_AC-14463 - [Problème GitHub](https://github.com/magento/magento2/issues/39817) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### Nombre de listes de souhaits non affichées sur la page d’accueil/autres pages à l’exception de la page de liste de souhaits dans le menu client

Correction d’un problème en raison duquel le nombre de listes de souhaits s’affichait sous forme de parenthèses vides sur les pages hors liste de souhaits.
Désormais, le nombre correct d’éléments de liste de souhaits s’affiche en regard de « Ma liste de souhaits » sur toutes les pages.

_AC-14607 - [Problème GitHub](https://github.com/magento/magento2/issues/39892) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a3b1abc2) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/b3774fbe)_

#### catalog_product_save_before observe renvoie une erreur liée à la date lors de l’utilisation de l’API REST sans valeurs au niveau du magasin (problème getFinalPrice())

Cette requête d’extraction ajuste le traitement de SpecialFromDate pour garantir une mise en forme correcte lorsque la date est fournie en tant qu’instance DateTimeInterface. Cela empêche les erreurs qui se produisent lors de l’exécution de getFinalPrice() dans certains scénarios.

_AC-14847 - [Problème GitHub](https://github.com/magento/magento2/issues/39959) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40003)_

#### URGENT - Impossible d’ajouter le produit au lot lorsque le produit à ajouter comporte des options personnalisables

Correction d’un problème en raison duquel les produits dotés d’options personnalisables ne pouvaient pas être ajoutés aux produits groupés.
Auparavant, ces produits étaient exclus de la liste « Ajouter des produits à l’option » lors de la création du bundle.
Désormais, les produits dotés d’options personnalisables peuvent être ajoutés aux lots sans inclure leurs options personnalisées, ce qui permet une gestion adéquate des stocks.
Cela permet de créer des lots sans dupliquer de produits ni affecter les niveaux de stock.

_AC-14958 - [Problème GitHub](https://github.com/magento/magento2/issues/39993)_

#### Une chaîne de requête `?p=` négative entraîne une exception Elasticsearch

Le système traite désormais la valeur négative ?p= dans la pagination Catégorie, qui entraîne actuellement une exception et est considérée comme une requête valide

_AC-15191 - [Problème GitHub](https://github.com/magento/magento2/issues/40079) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40080)_

#### L’étiquette de prix « Aussi bas que » s’affiche pour les produits configurables avec une seule option

Correction d’un problème en raison duquel les produits configurables affichaient le prix avec un libellé incorrect « Aussi bas que » sur PDP/PLP.
Maintenant, le produit affiche le prix correct (500 $) sans aucune étiquette trompeuse.

_AC-15237 - [Problème GitHub](https://github.com/magento/magento2/issues/40104) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Méthode incorrecte appelée pour le bouton Ajouter à la comparaison

Correction de la méthode utilisée dans \Magento\Catalog\Ui\DataProvider\Product\Listing\Collector\Url::collect().
Auparavant, getAddToCartButton() était incorrectement appelé à la place de getAddToCompareButton().
Cette modification permet de garantir le comportement correct du rendu du bouton « Ajouter pour comparer » dans les listes de produits.
Aucun changement de comportement fonctionnel n’est introduit ; la mise à jour améliore l’expérience du développeur et l’exactitude du code.

_AC-15323 - [Problème GitHub](https://github.com/magento/magento2/issues/39754) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Un prix de produit incorrect est affiché sur le panier avec différentes devises dans différentes vues de la boutique

Correction d’un problème en raison duquel un prix de produit incorrect était affiché dans le panier lors de l’utilisation de différentes devises dans les vues de la boutique. Après la correction, le panier affiche désormais le prix converti correct en fonction de la devise configurée, ce qui garantit la cohérence entre la page de produits et le panier.

_AC-15385 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a8cf637b)_

#### Erreur d’affichage du prix « Aussi bas que » pour les produits configurables lorsque le protocole FPT est activé

Confirmation que le prix incorrect « Aussi bas que » pour les produits configurables lorsque FPT a été activé était dû à l&#39;application double de la taxe ; le correctif garantit que le calcul du prix final respecte la configuration de la taxe et affiche désormais le prix correct.

_AC-15718 - [Problème GitHub](https://github.com/magento/magento2/issues/40171) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a06a4a57)_

#### La complexité temporelle de _loadAttributes dans Eav\Model\Entity\Collection\AbstractCollection augmente avec le nombre de produits dans le panier et les attributs

Cette requête persistante a optimisé _loadAttributes dans Eav\Model\Entity\Collection\AbstractCollection en remplaçant les boucles imbriquées par l’union de tableau (+) et en réduisant les appels à _setItemAttributeValue, ce qui améliore les performances des paniers de produits volumineux.

_AC-15833 - [Problème GitHub](https://github.com/magento/magento2/issues/40216) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40217)_

#### Interaction boguée entre le cache de collection et la galerie de produits configurables

Correction d’un problème de mise en cache avec les galeries de produits configurables en ajoutant une vérification de type défensive pour s’assurer que media_galerie_images est toujours traité comme une collection, évitant les erreurs fatales causées par des données de cache corrompues.

_AC-16066 - [Problème GitHub](https://github.com/magento/magento2/issues/33965) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/3b5ac075)_

#### La page produit renvoie une erreur en raison de réécritures d’URL.

Désormais, la page produit est chargée avec succès lorsque des réécritures d’URL sont disponibles

_AC-2950 - [Problème GitHub](https://github.com/magento/magento2/issues/35371) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39670)_

#### erreur cron indexer_update_all_views avec MAGE_INDEXER_THREADS_COUNT

Correction d’un problème de MAGE_INDEXER_THREADS_COUNT > 2 avec l’indexeur de segments client

_ACP2E-3538 - [contribution du code GitHub](https://github.com/magento/magento2/commit/9608ca21)_

#### Exception lors de l’ajout de la « Combinaison de conditions » dans la condition de widget Produits Page Builder

Le problème a été corrigé en ajoutant une vérification pour ignorer les conditions manquantes ou incomplètes. Auparavant, cela entraînait la génération de journaux d’erreurs en raison de la gestion de conditions incomplètes dans le système.

_ACP2E-3545 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/11be3dff)_

#### Panne du navigateur lors du chargement du jeu d’attributs

Le navigateur ne se bloque plus sur la page de modification du jeu d’attributs s’il existe plus de 4 000 attributs de produit

_ACP2E-3633 - [Problème GitHub](https://github.com/magento/magento2/issues/38810) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

#### [CLOUD] Réécritures d’URL de produit non créées pour le nouveau magasin : bloqueur de mise en production

Les réécritures d’URL de produit pour un nouveau magasin ont été créées.
L’opération précédente s’est terminée avec une fuite de mémoire ou un délai d’expiration.

_ACP2E-3669 - [contribution du code GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### La valeur par défaut de l’attribut pour les options ne fonctionne pas

Auparavant, lorsque nous modifiions la valeur par défaut d’un attribut de sélection de produit, elle s’affichait sous la forme d’un élément de tableau avec les valeurs précédentes. Une fois ce correctif appliqué, lorsque nous mettons à jour une valeur d’attribut de produit, il est enregistré en tant qu’élément unique dans la table eav_attribute.

_ACP2E-3688 - [contribution du code GitHub](https://github.com/magento/magento2/commit/520f9e30)_

#### [Mainline] [CLOUD] Le redimensionnement d’image consomme plus de 400GB d’espace disque

Après le correctif, la commande `catalog:images:resize` utilisée avec `--skip_hidden_images` indicateur ne génère pas de caches d’images pour les sites web où les images ne sont pas présentes.

_ACP2E-3869 - [contribution du code GitHub](https://github.com/magento/magento2/commit/9ad7d277)_

#### La génération d’images dynamiques génère un grand nombre d’images

Après la correction, les images seront générées uniquement pour les sites web auxquels le produit est affecté.

_ACP2E-3927 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/fab20b00)_

#### L&#39;ID de pays fourni n&#39;existe pas - Irlande (IE)

Après le correctif, des codes postaux irlandais sont disponibles pour rechercher les lieux de retrait.

_ACP2E-3932 - [contribution de code GitHub](https://github.com/magento/magento2/commit/4ca73607) - [contribution de code GitHub](https://github.com/magento/inventory/commit/d2f1d6c6)_

#### Une erreur 500 se produit sur le front-end, car une structure de disposition incorrecte est mise en cache dans la disposition

Correction d’un problème en raison duquel une page renvoyait un code d’erreur 500 en raison d’une structure de mise en page incorrecte mise en cache dans la mise en page

_ACP2E-4040 - [contribution du code GitHub](https://github.com/magento/magento2/commit/47721be6)_

#### Rapport incorrect sur les consultations de produits - Nombre inférieur par rapport à GA

Correction d’un bug en raison duquel la table report_viewed_product_index n’affichait pas le nombre correct de pages vues de produits.

_ACP2E-4045 - [contribution du code GitHub](https://github.com/magento/magento2/commit/6e134409)_

#### Erreur de validation pour le champ du montant de remise de la règle de prix du catalogue dans la mise à jour planifiée

Auparavant, avant de résoudre ce problème, pour la mise à jour de programme de la règle de prix catalogue, si le montant de remise est by_fixed, il n&#39;a pas été validé correctement en raison de la règle validation-numéro-fourchette. Une fois ce correctif appliqué, la validation fonctionne correctement pour la règle de prix catalogue fixe.

_ACP2E-4054 - [contribution du code GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### La validation de la TVA échoue en raison du limiteur de taux API de TVA - déclenche une modification de groupe de clients faussement positive

Optimisation des requêtes envoyées à l’outil de validation Europa Vat, afin de réduire le nombre d’erreurs de « limitation de taux ».

_ACP2E-4072 - [contribution du code GitHub](https://github.com/magento/magento2/commit/ee918f0d)_

#### Suppression en bloc dans l’indexeur principal déclenchant l’erreur de taille maximale de l’ensemble d’écriture en production

Optimise le nettoyage de l’index de produit des règles de catalogue en implémentant deux stratégies de suppression basées sur le volume de données.

_ACP2E-4085 - [contribution du code GitHub](https://github.com/magento/magento2/commit/0a3b7032)_

#### Les produits s’affichent comme étant en rupture de stock après désactivation

Après le correctif, les produits désactivés ne sont pas présents dans le widget de produits.

_ACP2E-4136 - [contribution du code GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [Cloud] Erreurs avec entrées en double (temp_category_descendants_%)

Correction d’un problème lié aux entrées en double lors des mises à jour planifiées de création pour les environnements comportant un grand nombre de catégories imbriquées

_ACP2E-4159 - [contribution du code GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [CLOUD] Comparer les produits Non-correspondance du nombre de produits Problème pour différents magasins

La comparaison de la liste de produits fonctionne désormais correctement après le passage à une autre boutique

_ACP2E-4249 - [contribution du code GitHub](https://github.com/magento/magento2/commit/98f028ab)_

#### Aucune option permettant d’« utiliser la valeur par défaut » sur « Images et vidéos » pour l’affectation de rôle d’image

Les options « Utiliser la valeur par défaut » ont été ajoutées à la section des images et des vidéos du produit, ce qui permet d’hériter des paramètres de la portée par défaut.

_ACP2E-4280 - [contribution du code GitHub](https://github.com/magento/magento2/commit/61c96348)_

#### Les produits de catégorie restreinte restent dans la liste de souhaits après la mise à jour du groupe de clients

Avant la correction, les autorisations de catégorie n’étaient pas correctement appliquées aux éléments de la liste de souhaits du client. Désormais, après le correctif, les éléments de liste de souhaits sont correctement affichés et paginés sur le web et dans GraphQL.

_ACP2E-4294 - [contribution du code GitHub](https://github.com/magento/magento2/commit/c135fc3a)_

#### [Cloud] Problème de prix de bundle du produit sur PDP et PLP

Le prix du produit groupé au prix normal s&#39;affiche correctement sur PDP/PLP pour une devise autre que celle par défaut

_ACP2E-4298 - [contribution du code GitHub](https://github.com/magento/magento2/commit/0a3b7032)_

#### Le client peut commander un produit inaccessible après un changement de groupe de clients

Auparavant, lors de la modification du groupe de clients à partir d’admin, le catalogue front-end et le panier ne reflétaient pas les modifications apportées aux autorisations du catalogue. Cependant, après l’application de ce correctif, le devis frontal change désormais en fonction des autorisations de catalogue mises à jour lorsque le groupe de clients est modifié à partir de l’adresse admin.

_ACP2E-4300 - [contribution du code GitHub](https://github.com/magento/magento2/commit/f7bbcb4e)_

#### Réindexation bloquée en raison d’une utilisation élevée de la mémoire

Correction du problème en raison duquel l’indexeur de règles de catalogue consommait trop de mémoire et ne s’exécutait pas, provoquant une instabilité et des erreurs de mémoire insuffisante.

_ACP2E-4303 - [contribution du code GitHub](https://github.com/magento/magento2/commit/c135fc3a)_

#### [CMS ] Le lien Aperçu de la mise à jour planifiée redirige vers la page Maintenance

L’aperçu de la mise à jour planifiée du lien de la page d’accueil avec les produits configurables affiche correctement la liste des produits. Auparavant, il redirigeait les utilisateurs vers la page de maintenance.

_ACP2E-4401 - [contribution du code GitHub](https://github.com/magento/magento2/commit/1c547060)_

### Catalogue, GraphQL

#### Calcul de remise GraphQl non valide

GraphQL affiche désormais correctement les pourcentages de remise et les prix de base lorsque les prix de catalogue sont configurés pour inclure la taxe. Auparavant, des erreurs d’arrondi se produisaient, par exemple l’affichage de 19,99 % au lieu de 20 %.

_ACP2E-3993 - [contribution du code GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

#### Le champ Galerie de médias GraphQL GetCart renvoie des données vides après le vidage du cache

Après le correctif, la media_gallery du produit est renvoyée comme prévu dans la réponse GraphQL pour la requête de panier.

_ACP2E-4185 - [contribution du code GitHub](https://github.com/magento/magento2/commit/45cbf9b6)_

### Catalogue, GraphQL, Recherche

#### Le graphql des produits a renvoyé des catégories désactivées dans les agrégations de catégories

Après la correction, les catégories désactivées ne sont pas renvoyées pour la requête GraphQl des produits.

_ACP2E-2885 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

### Catalogue, Performances

#### Les catégories dans l’administration se chargent très lentement

Les performances de chargement des catégories ont été considérablement améliorées. Auparavant, le chargement de la catégorie qui provoquait un problème de délai d’expiration prenait trop de temps.

_ACP2E-3891 - [contribution du code GitHub](https://github.com/magento/magento2/commit/4ca73607)_

### Catalogue, tarification

#### Escompte de règle de prix de catalogue incorrect appliqué au produit enfant

Correction d’un problème en raison duquel la règle de prix de catalogue pour la variation était remplacée par le produit configurable parent, dans le cas où les deux règles avaient la même priorité.

_ACP2E-3693 - [contribution du code GitHub](https://github.com/magento/magento2/commit/a20a6ff2)_

#### Problème de prix du produit groupé [Cloud]

Le prix du produit groupé avec un prix spécial s&#39;affiche correctement sur PDP/PLP pour une devise autre que celle par défaut

_ACP2E-4110 - [contribution du code GitHub](https://github.com/magento/magento2/commit/6e134409)_

### Catalogue, produit

#### [Bogue aléatoire] la bibliothèque Fotorama n’est pas chargée

Le système s’assure désormais que la bibliothèque Fotorama est correctement chargée, ce qui permet à toutes les images jointes d’être affichées dans la galerie d’images comme prévu. Auparavant, seule la première image était visible en raison d’un problème de chargement incorrect de la bibliothèque Fotorama.

_AC-12124 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/45b51c9c) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/27217d0e)_

#### Le lien « Ajouter des produits manuellement » doit toujours être visible

Correction d’un problème en raison duquel le lien « Ajouter manuellement des produits » n’était pas visible lors de la création d’un produit configurable sans configurations existantes. Le lien est désormais toujours affiché, ce qui permet aux administrateurs d’associer facilement des produits simples sans créer de configurations factices.

_AC-13866 - [Problème GitHub](https://github.com/magento/magento2/issues/39595) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/ef666cd9)_

#### Modifier un produit en arrière-plan Supprime les décimales supplémentaires du prix des options de produit

Correction d’un problème en raison duquel la modification d’un produit dans le prix de l’option de produit tronqué par l’administrateur était évaluée à deux décimales. Le système conserve désormais la tarification avec une précision décimale plus élevée, ce qui garantit que les valeurs exactes sont conservées après l’enregistrement.

_AC-14050 - [Problème GitHub](https://github.com/magento/magento2/issues/39655) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/3b5ac075)_

### Catalogue, recherche

#### La requête RestApi « /rest/default/V1/categories?searchCriteria%5Bpage_size%5D=1 » échoue avec une erreur de délai d’expiration

Les requêtes d’API REST de catégorie n’échouent plus avec des erreurs de délai d’expiration.
Auparavant, les requêtes envoyées à /rest/default/V1/categories?searchCriteria[page_size]=1 pouvaient échouer avec un délai d’expiration après certaines modifications de code.
AC-13358

_AC-13358 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

### Contenu

#### graphql (magento 2.4.6-p4 ) : erreur lors de la tentative d’obtention d’une page cms dont le statut est inactif

Correction d’un problème en raison duquel la requête GraphQL sur une page CMS désactivée renvoyait une erreur de serveur interne.
Désormais, la requête récupère une réponse appropriée sans erreur.

_AC-12302 - [Problème GitHub](https://github.com/magento/magento2/issues/38877) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/1b1baf1d)_

#### Le formulaire de partage de liste de souhaits autorise le code aléatoire dans les champs de nom

Correction d’une vulnérabilité critique liée à l’injection de modèle côté serveur (SSTI) dans le formulaire de partage de liste de souhaits, en raison de laquelle du code malveillant pouvait être saisi dans le champ du message et envoyé par e-mail. La mise à jour ajoute la validation des entrées aux directives de modèle de bloc et aux modèles non sécurisés, affichant désormais un message d’erreur lorsque du contenu non valide est détecté.

_AC-12730 - [Problème GitHub](https://github.com/magento/magento2/issues/39024) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/01cee3c3)_

#### L’insertion du fichier csp_whitelist.xml dans le thème ne fonctionne pas et crée un problème intermittent

Mise en cache implémentée de la liste autorisée CSP par zone du site web.

_AC-13069 - [Problème GitHub](https://github.com/magento/magento2/issues/38933) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39672)_

#### Après la mise à niveau vers magento 2.4.7 p2 ne peut pas voir les fichiers récemment chargés galerie de médias

Les fichiers récemment chargés apparaissent désormais dans la Galerie de médias après la mise à niveau.
Auparavant, après la mise à niveau vers Magento 2.4.7 p2, les images nouvellement chargées n’apparaissaient pas dans la Galerie de médias tant qu’une synchronisation manuelle n’était pas effectuée.
AC-13262

_AC-13262 - [Problème GitHub](https://github.com/magento/magento2/issues/39275)_

#### La galerie de médias affiche des images incorrectes provenant de répertoires portant des noms identiques mais avec des casse différentes

Le système résout désormais un problème en raison duquel les fichiers chargés dans un répertoire spécifique de la Galerie de médias sont également visibles dans des répertoires portant des noms similaires, mais avec des majuscules et des minuscules différentes.

_AC-13489 - [Problème GitHub](https://github.com/magento/magento2/issues/39382) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39502)_

#### Lorsque vous supprimez complètement une image de galerie de be, les rôles/types de l’étendue sont conservés (base/small/thumbnail) et, après avoir rajouté les « anciens » rôles/types, s’affichent

Le système fonctionne comme prévu dans les portées de magasin. Les images héritent des rôles/types de la nouvelle image ajoutée selon la portée par défaut

_AC-13556 - [Problème GitHub](https://github.com/magento/magento2/issues/39481) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39680)_

#### [Petit bogue] le filtre du panneau d’administration `listing component` ne peut pas être atteint lorsque la valeur du champ contient `\`

Le système fonctionne correctement lorsque nous filtrons le titre de la page avec une barre oblique (par exemple : Magento\Store)

_AC-13661 - [Problème GitHub](https://github.com/magento/magento2/issues/39513) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39535)_

#### Erreur : erreur de script pour « Magento_Catalog/js/validate-product » pour le générateur de page du contenu de l’administrateur avec le chargement des produits

Cette requête d’extraction corrige l’erreur de script de catalogAddToCart lors de la modification de pagebuilder avec la condition products

_AC-13891 - [Problème GitHub](https://github.com/magento/magento2/issues/39604) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39677)_

#### Erreur de script catalogAddToCart lors de la configuration du widget de produit.

Correction d’une erreur de script qui se produisait lors de la configuration du widget Produits avec « Combinaison de conditions » dans Page Builder. Le problème était dû à des fichiers JS frontaux manquants, ce qui entraînait des erreurs de console. Après le correctif, le widget se charge correctement sans erreur de console.

_AC-13892 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/528af81a)_

#### Bloquer la sélection dans les widgets portant le même identifiant

Le système gère désormais correctement la sélection de blocs lors de la création de widgets lorsque nous avons les mêmes blocs d’identifiant

_AC-14132 - [Problème GitHub](https://github.com/magento/magento2/issues/39692) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39722)_

#### Inondation de journal « La page CMS avec l’ID « 0 » n’existe pas

Le système fonctionne comme prévu après la création d’un utilisateur administrateur et lorsque nous créons une nouvelle page, system.log n’a aucun message d’erreur

_AC-14254 - [Problème GitHub](https://github.com/magento/magento2/issues/39743) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39746)_

#### [GraphQl] Boucle infinie de requête d’itinéraire

Ce ticket corrige le problème où une requête d’itinéraire GraphQL avec un chemin de requête et un chemin de cible identiques provoquait une boucle infinie et expirait par la suite.
Dans la version 2.4.9-alpha3, la requête renvoie désormais la réponse d’erreur correcte au lieu de faire une boucle.

_AC-14269 - [Problème GitHub](https://github.com/magento/magento2/issues/39707) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### Un plan de site inexistant répond avec une image de produit.

Le système corrige désormais les erreurs lorsque nous accédons au plan de site inexistant et répond avec l’image de produit en indiquant Réponse : 404 INTROUVABLE

_AC-14295 - [Problème GitHub](https://github.com/magento/magento2/issues/39756) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40135)_

#### Les widgets de lien de catalogue utilisent une URL incorrecte

Le système gère désormais correctement les widgets après l’ajout du lien de produit de catalogue et du lien de catégorie de catalogue. Il affiche également les URL correctes dans la source HTML

_AC-14437 - [Problème GitHub](https://github.com/magento/magento2/issues/39464) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39710)_

#### Le préfixe de la table n’est pas pris en compte.

Adobe Commerce respecte désormais correctement les préfixes de table de base de données lors du chargement de la grille de thème Conception > Configuration dans l’Administration. Auparavant, sur Adobe Commerce 2.4.8, avec un préfixe de tableau configuré dans app/etc/env.php, l’accès à Contenu > Conception > Configuration entraînait une erreur, car le préfixe du tableau n’était pas pris en compte et la grille de thèmes n’était pas rendue.

_AC-14556 - [Problème GitHub](https://github.com/magento/magento2/issues/39847) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### Pour plus de flexibilité, définissez la constante IMAGE_FILE_NAME_PATTERN sur public visible

La constante IMAGE_FILE_NAME_PATTERN dans GenerateRenditions.php a été rendue publique pour permettre aux développeurs plus de flexibilité lors de l&#39;utilisation de rendus d&#39;image. Le correctif est inclus dans Magento 2.4.9-alpha3 avec une couverture de test d’intégration et d’unité complète.

_AC-15338 - [Problème GitHub](https://github.com/magento/magento2/issues/39733) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### Mode d&#39;expédition incorrect affiché dans la page de vérification de l&#39;ordre pour une expédition multiple

Correction d’un problème lors du passage en caisse multi-expédition en raison duquel la page de révision de la commande affichait un coût d’expédition incorrect (5 INR au lieu de 10 INR) ; la mise à jour garantit que le montant d’expédition correct s’affiche pour chaque adresse.

_AC-15664 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/3cf1a106)_

#### échec de bin/magento config:show(ou set) design/theme/theme_id

Correction d’un problème en raison duquel les commandes de l’interface de ligne de commande bin/magento config:show et config:set échouaient pour le chemin design/theme/theme_id malgré la présence de la configuration.
Désormais, les commandes s’exécutent correctement et permettent d’afficher et de définir l’identifiant du thème sans erreurs.

_AC-5915 - [Problème GitHub](https://github.com/magento/magento2/issues/35751) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/64823f95)_

#### Impossible de charger l’image avec une largeur relativement faible

Le système ne parvient plus à redimensionner l’image avec une largeur relativement faible par rapport à sa hauteur.

_ACP2E-3558 - [contribution du code GitHub](https://github.com/magento/magento2/commit/9608ca21)_

#### Le composant Produit de Page Builder ne fonctionne pas si l’utilisateur ne dispose pas de l’autorisation Widget

Avant la correction, lors de l’accès à un widget sans autorisations, la page renvoyait une erreur générique et affichait un GIF « chargement ». Désormais, après la correction, une fenêtre modale s’affiche avec « Désolé, vous avez besoin d’autorisations pour afficher ce contenu ». message.

_ACP2E-3664 - [Contribution du code GitHub](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### Chemin de configuration incorrect pour la configuration du style du chemin de stockage distant

Après le correctif, la définition de la configuration du style de chemin d’accès de stockage distant aura un impact sur la configuration réelle du style de chemin d’accès AWS S3.

_ACP2E-3734 - [contribution du code GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### Ordre du widget de produit Page Builder non appliqué dans GraphQL

Correction du problème en raison duquel la réponse de requête « itinéraire » de GraphQL ne renvoyait pas les produits dans l’ordre de tri correct dans un type de contenu de produits Page Builder.

_ACP2E-3898 - [contribution du code GitHub](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### Problème d&#39;affichage du prix sur les vitrines non anglaises en raison de la version de la bibliothèque ICU

Après la correction, le prix du produit s’affiche correctement dans le paramètre régional Hébreu (Israël).

_ACP2E-3938 - [contribution du code GitHub](https://github.com/magento/magento2/commit/7accebfa)_

#### Mise à jour du code de magasin effacé de la configuration de conception

Correction du problème en raison duquel la mise à jour du code d’affichage du magasin effaçait les paramètres de configuration de conception en raison d’une actualisation incorrecte du cache de configuration.

_ACP2E-3941 - [contribution du code GitHub](https://github.com/magento/magento2/commit/462ede94)_

#### Page Builder - Problème de logique de condition du produit (la logique OU se comporte incorrectement en affichant moins de produits)

Le widget Produits de Page Builder renvoie désormais un résultat correct lorsqu’un attribut avec une portée globale est utilisé dans la condition « Ne correspond à aucun »

_ACP2E-4096 - [contribution du code GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

#### Le carrousel de produits ajoute des produits incorrects à Page Builder

Avant la correction, un produit configurable avait été automatiquement inclus dans les listes de carrousel de produits PageBuilder si l’un de ses enfants répondait aux conditions de filtrage. Désormais, après la correction, le produit parent n’est inclus que si le produit enfant n’est pas visible par lui-même.

_ACP2E-4341 - [contribution du code GitHub](https://github.com/magento/magento2/commit/61c96348)_

#### Le widget Liste de produits renvoie un résultat incorrect si plusieurs catégories sont répertoriées dans la condition de catégorie

Le widget « Liste de produits du catalogue » affiche désormais des résultats précis lorsque plusieurs catégories répertoriées dans la condition « Catégorie fait partie de ». Auparavant, seule la première catégorie de la liste était traitée.

_ACP2E-4353 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/0a3b7032) - [Contribution du code GitHub](https://github.com/magento/magento2-page-builder/commit/1c1b3419)_

#### [Cloud] La création de dossiers dans la Galerie de médias nécessite l’autorisation delete_folder dans la Galerie de nouveaux médias - les rôles avec uniquement create_folder ne peuvent pas créer de dossiers

Auparavant, avant l’implémentation de ce correctif, un utilisateur administrateur disposant uniquement de l’autorisation de création de dossier de contenu ne pouvait pas créer de dossier dans la galerie de médias CMS. Cependant, après le correctif, les créateurs et créatrices de contenu dans la galerie multimédia peuvent désormais créer des dossiers avec uniquement l’autorisation Créer un dossier .

_ACP2E-4376 - [contribution du code GitHub](https://github.com/magento/magento2/commit/61c96348)_

#### [QUANS] Duplication d’une page CMS

Avant ce correctif, la duplication d’une page cms avec mise à jour de la disposition personnalisée aurait échoué. Désormais, les pages CMS avec des mises à jour de disposition personnalisées peuvent être dupliquées sans erreur.

_ACP2E-4449 - [contribution du code GitHub](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Client/Clients

#### Exception sur Storefront lorsque l’administrateur ajoute un bloc CustomerCustomAttribute via le contenu de la page CMS

Correction d’un problème en raison duquel l’ajout du bloc CustomerCustomAttribute via le contenu de la page CMS provoquait une exception de storefront et empêchait le chargement de la page.
Storefront s’affiche désormais normalement et affiche un message significatif lorsque le contenu ne peut pas être rendu, évitant ainsi les erreurs critiques.

_AC-11004_

#### La Grille D’Administration En Ligne Des Clients Affiche Des Lignes En Double Chaque Fois Qu’Un Utilisateur Se Connecte, Puis Se Déconnecte, Puis Se Connecte

Correction d’un problème en raison duquel la grille d’administration de Customers Now Online affichait des lignes en double lorsqu’un client se déconnectait et se reconnectait.
La grille met désormais à jour l’enregistrement existant avec la dernière activité au lieu de créer des entrées en double, assurant ainsi un suivi précis des sessions client.

_AC-11511 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/528af81a)_

#### La validation des valeurs minimales et maximales ne fonctionne pas pour l’attribut DOB sur Storefront

Ce bug corrigeait le problème en raison duquel la validation des dates minimale et maximale pour l’attribut Date de naissance (DOB) ne fonctionnait pas sur le storefront (même si elle fonctionnait dans Admin).
Dans la version 2.4.9-alpha3, la validation bloque désormais correctement l’enregistrement des clients avec DOB en dehors de la plage autorisée, affichant un message d’erreur.

_AC-13535 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### Chargement d’erreur Ajax 401 sur l’écran Avertissement du panneau d’administration lors de la révocation de l’autorisation Connexion en tant que client

Ce bogue corrige un problème en raison duquel une révocation de l’autorisation Connexion en tant que client entraînait l’affichage d’une erreur Ajax 401 avec HTML brut dans la fenêtre contextuelle d’avertissement.
Après le correctif, le système affiche désormais correctement un message d’avertissement classique au lieu d’HTML brut.
La solution a été fournie dans Magento 2.4.9-alpha3

_AC-15336 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

### Framework

#### Code de complétion du module désactivé.

Cette demande d’extraction désactive les modules avant la compilation du code.

_AC-10933 - [Problème GitHub](https://github.com/magento/magento2/issues/38241) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39723)_

#### Erreur lors de l’exécution de la configuration de commande:upgrade avec le déclencheur de base de données personnalisé

Les déclencheurs de base de données personnalisés ne provoquent plus d’erreurs lors de la configuration:upgrade.
Auparavant, l’exécution de la configuration bin/magento:upgrade avec un déclencheur de base de données personnalisé (par exemple, AFTER INSERT sur la table de magasin) pouvait entraîner l’erreur :
« Avertissement : tentative d’accès au décalage de tableau sur une valeur de type null dans vendor/magento/framework/Mview/View/Subscription.php à la ligne 357 »
AC-11487

_AC-11487 - [Problème GitHub](https://github.com/magento/magento2/issues/38481)_

#### [Problème] Rendre la signature de méthode cohérente avec l’interface

La signature de méthode pour getAttributes est désormais cohérente avec son interface, ce qui empêche toute erreur lors du remplacement de la méthode. Auparavant, les incohérences dans la signature de méthode provoquaient des erreurs lors de la tentative de remplacement de la méthode getAttributes.

_AC-11578 - [Problème GitHub](https://github.com/magento/magento2/issues/38501) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/31955)_

#### Le formulaire d’entité de site web/groupe/magasin ne peut pas être étendu avec un élément de formulaire à plusieurs valeurs pour les attributs d’extension

Cette requête d’extraction permet aux éléments de formulaire à plusieurs valeurs d’envoyer des données au formulaire de site web/groupe/magasin.

_AC-11657 - [Problème GitHub](https://github.com/magento/magento2/issues/24070) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/24094)_

#### [Problème] Correction de la règle validate-emails pour le composant de l’interface utilisateur

Le système valide désormais correctement plusieurs adresses e-mail saisies dans les composants de l’interface utilisateur, en s’assurant que chaque adresse e-mail est correctement tronquée et validée. Auparavant, le système utilisait une méthode incorrecte pour supprimer les adresses e-mail, ce qui pouvait entraîner des erreurs de validation.

_AC-11719 - [Problème GitHub](https://github.com/magento/magento2/issues/38528) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/33470)_

#### [Problème] Supprimer l’utilisation du résolveur d’étendue

Cette requête PR résout globalement les paramètres d’URL d’administration au lieu du magasin actuel

_AC-11736 - [Problème GitHub](https://github.com/magento/magento2/issues/38566) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38554)_

#### [Problème] Supprimer les méthodes redondantes

Qualité du code : suppression des méthodes redondantes dans les composants Opérations asynchrones et Ventes qui appelaient uniquement des méthodes parentes sans ajouter de fonctionnalité, ce qui améliore la facilité de maintenance du code.

_AC-11915 - [Problème GitHub](https://github.com/magento/magento2/issues/29748) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/29147)_

#### Magento_Theme title.phtml template non valide pour PHP 8.2

Cette requête de tirage corrige un problème en raison duquel la page CMS créée avec l’en-tête null comme dans Php 8.x transmettant null à trim() renvoie Exception : fonctionnalité obsolète : trim() : transmission de null au paramètre #1 ($string) de type chaîne

_AC-12856 - [Problème GitHub](https://github.com/magento/magento2/issues/39092) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39398)_

#### la validation xsd échoue sur les fichiers etc/adminhtml/system.xml qui contiennent des commentaires sous les éléments de champ.

Ce PR corrige les définitions de schéma XML dans phpstorm pour le nœud comment

_AC-12945 - [Problème GitHub](https://github.com/magento/magento2/issues/39148) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39867)_

#### Exposition de la version de Magento via l’itinéraire d’installation avec la configuration Nginx par défaut

Le système fonctionne maintenant comme prévu et n’expose pas la version exacte de Magento que le site exécute

_AC-13205 - [Problème GitHub](https://github.com/magento/magento2/issues/39227) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39228)_

#### [Problème] Décompressez les arguments d’objet en tant que paramètres nommés

Le système utilise désormais la fonctionnalité PHP 8.1 de décompresser un tableau avec des paramètres nommés, ce qui élimine le besoin d&#39;appels array_values et améliore potentiellement les performances globales. Auparavant, le système exigeait que array_values appelle pour décompresser les arguments d&#39;objet.

_AC-13210 - [Problème GitHub](https://github.com/magento/magento2/issues/39233) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37411)_

#### [Problème] refactoriser l’adresse de devis pour valider la méthode

Cette requête d’extraction comprend des améliorations de lisibilité de la méthode doValidate.

_AC-13214 - [Problème GitHub](https://github.com/magento/magento2/issues/38230) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38219)_

#### option Magento : magento-init-params n’est-il jamais utilisé lors de l’exécution de l’interface de ligne de commande ?

L’option —magento-init-params est désormais utilisée lors de l’exécution des commandes de l’interface de ligne de commande.
Auparavant, la transmission de —magento-init-params aux commandes CLI n’avait aucun effet sur les paramètres tels que MAGE_MODE.
AC-13231

_AC-13231 - [Problème GitHub](https://github.com/magento/magento2/issues/39248) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/132b9e68)_

#### Déclaration de type incorrecte de getItemsByColumnValue

Le système définit désormais correctement le paramètre d’entrée $value comme un type primitif, et non comme un tableau, dans la fonction getItemsByColumnValue , en s’assurant que la fonction renvoie la collection attendue. Auparavant, si un tableau avec une seule valeur était utilisé comme paramètre d’entrée, la fonction renvoyait la valeur null et les IDE le marquaient comme une erreur.

_AC-13240 - [Problème GitHub](https://github.com/magento/magento2/issues/33070) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/33120)_

#### Lors de l&#39;utilisation du stockage de fichiers pour le fournisseur de verrouillage, nous obtenons un répertoire de fichiers en constante augmentation sans aucun nettoyage

Cette demande d’extraction introduit une nouvelle tâche cron qui s’exécute une fois par jour et recherche les fichiers de verrouillage qui n’ont pas été modifiés au cours des dernières 24 heures et qui peuvent donc être supprimés en toute sécurité. Le contenu du répertoire des fichiers verrouillés restera ainsi sous contrôle.
Cette tâche cron n’exécute un élément que lorsque le fournisseur de verrouillage est configuré pour utiliser des fichiers et non lorsque l’un des autres est utilisé (base de données : valeur par défaut, zookeeper ou cache)

_AC-13367 - [Problème GitHub](https://github.com/magento/magento2/issues/39369) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39372)_

#### [Problème] Nettoyage : n’utilisez pas la valeur de retour void des appels de méthode.

Ce PR effectue un nettoyage mineur. Parfois, nous appelions des méthodes qui ne renvoyaient rien (void), puis utilisions cette valeur de résultat. Ce qui n&#39;est vraiment pas nécessaire.

_AC-13664 - [Problème GitHub](https://github.com/magento/magento2/issues/39524) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39516)_

#### Clés de cache associées à FPC sur les implémentations multi-magasin Magento 2.4.7

Correction d’un problème en raison duquel les clés de cache Full Page (FPC) dans les configurations multi-magasin n’incluaient pas MAGE_RUN_CODE et MAGE_RUN_TYPE, ce qui entraînait un comportement de clé de cache incohérent par rapport aux versions précédentes. Les clés de cache incluent désormais correctement le contexte du magasin, ce qui garantit une isolation correcte du cache entre les magasins.

_AC-13719 - [Problème GitHub](https://github.com/magento/magento2/issues/39456) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/ae6f305b)_

#### [Problème] [PHPDOC] Correction du mauvais phpdoc pour Magento\Framework\Message\ManagerInterface

Ce PR corrige le phpdoc incorrect pour \Magento\Framework\Message\ManagerInterface et supprime tous les phpdoc en double dans \Magento\Framework\Message\Manager (utilisez la syntaxe inheritdoc).

_AC-14312 - [Problème GitHub](https://github.com/magento/magento2/issues/39593) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39153)_

#### L’indexation partielle ne fonctionne plus pour les clients qui ont un grand nombre de mises à jour

L’indexation partielle fonctionne désormais pour les clients et clientes qui disposent d’un grand nombre de mises à jour.
Auparavant, le fait d&#39;atteindre la valeur maximale pour la colonne version_id dans la table des journaux des modifications entraînait l&#39;arrêt des mises à jour de l&#39;index.
AC-14424

_AC-14424 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

#### Magento 2.4.8 utilise des packages de développement qui ne respectent pas le contrôle de version sémantique

Magento 2.4.8 nécessite les versions de développement de pdependance/pdependance et phpmd/phpmd (3.x-dev) pour la compatibilité avec PHP 8.4.
Ces versions de développement entrent en conflit avec les outils tiers qui attendent des packages compatibles avec SemVer, empêchant certaines mises à niveau.
Une solution temporaire consiste à alias les versions de développement dans composer.json (par exemple, « 3.x-dev as 3.99.0 »), ce qui permet une compatibilité tout en respectant le contrôle de version sémantique.
Cela garantit la prise en charge de PHP 8.4 et évite les conflits jusqu&#39;à ce que des versions stables soient disponibles.

_AC-14519 - [Problème GitHub](https://github.com/magento/magento2/issues/39796)_

#### Le mécanisme MView ignore silencieusement les erreurs lors de l’exécution du déclencheur

Le mécanisme MView signale désormais correctement les erreurs lors de l’exécution du déclencheur.
Auparavant, les erreurs survenant lors de l’exécution du déclencheur étaient silencieusement ignorées, ce qui pouvait entraîner l’absence de mises à jour d’index sans notification.
AC-14567

_AC-14567 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/ae6f305b)_

#### [Problème] Évitez de nombreuses exceptions inutiles lors du chargement de la fusion XML de disposition

Cette requête d’extraction introduit une nouvelle fonction (pour la compatibilité B/C, nous ne remplaçons pas la valeur _loadXmlString protégée) pour charger et ne pas générer d’exception

_AC-14580 - [Problème GitHub](https://github.com/magento/magento2/issues/39877) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37570)_

#### [Problème] utilisez la promotion de propriété du constructeur dans le module Vault Graph Ql.

Cette requête remplace les propriétés du constructeur par la promotion de propriété dans le module VaultGraphQl

_AC-14616 - [Problème GitHub](https://github.com/magento/magento2/issues/39900) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/36996)_

#### [Problème ] suppression de la redondance de code pour les dispositions front-end du module.

Cette requête de tirage supprime la redondance de code pour les mises en page de thème des modules Magento_Msrp, Magento_LoginAsCustomerAssistance, Magento_Newsletter et Magento_Sitemap.

_AC-14625 - [Problème GitHub](https://github.com/magento/magento2/issues/30673) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/30644)_

#### [Problème ] incluez le constructeur pour qu’il fasse partie de `CommandListInterface`’API, étendez la documentation intégrée.

Cette mise à jour de PR marque Magento\Framework\Console\CommandList comme API et introduit le constructeur dans CommandListInterface pour une meilleure extensibilité. Elle améliore également la documentation intégrée afin d’améliorer la clarté et la facilité de maintenance pour les développeurs et développeuses étendant les commandes de console.

_AC-14680 - [Problème GitHub](https://github.com/magento/magento2/issues/31102) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37901)_

#### [Problème] Supprimer le code associé à Microsoft IIS

Ce PR nettoie le code associé à Microsoft IIS conformément à la documentation des exigences du système Magento qui indique que le système d&#39;exploitation Windows Microsoft n&#39;est pas pris en charge

_AC-14702 - [Problème GitHub](https://github.com/magento/magento2/issues/39910) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39894)_

#### Erreur de syntaxe du fichier Magnifier.js

La fonctionnalité Loupe du système doit continuer à fonctionner comme avant et la fonction loupeOptions ne doit pas être disponible dans une portée globale

_AC-14722 - [Problème GitHub](https://github.com/magento/magento2/issues/36200) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39321)_

#### Mode détaillé du rétroportage dans `setup:db:status` commande CLI

La commande de l’interface de ligne de commande `setup:db:status` prend désormais en charge le mode verbeux.
Auparavant, il était difficile de comprendre les modifications de base de données requises pour les mises à niveau. L’exécution de `bin/magento setup:db:status -v` fournit désormais des informations détaillées sur les différences de schémas et de données.
AC-14807

_AC-14807 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

#### Envoi d’e-mails SMTP avec tls et 2.4.8

L’envoi d’e-mails SMTP avec TLS fonctionne désormais comme prévu.
Auparavant, l’envoi d’e-mails via SMTP avec TLS entraînait l’erreur : error:1408F10B:SSL routines:ssl3_get_record:bad version number.
AC-14883

_AC-14883 - [Problème GitHub](https://github.com/magento/magento2/issues/39947) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/3717e6cb) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/8b453942) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/d3ea191d)_

#### [Problème] Correction d’un problème de simultanéité dans le déploiement de contenu statique

Cette requête de résolution corrige un bug en raison duquel plusieurs processus simultanés s’exécutent pour gérer le même package de thème, selon la définition des thèmes avec leurs parents.

_AC-14944 - [Problème GitHub](https://github.com/magento/magento2/issues/39990) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39954)_

#### [Problème] Supprimez le code de compatibilité hérité pour les versions PHP &lt; 8.1

Cette demande de tirage supprime le code conçu pour être exécuté sur PHP &lt;8.1.
En outre, supprimé vérifie la disponibilité des contacts PHP_VERSION_ID, puisqu&#39;il est disponible dans toutes les versions PHP

_AC-14971 - [Problème GitHub](https://github.com/magento/magento2/issues/39891) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39882)_

#### FPC ne fonctionne pas lors de la connexion

Le Cache de page complet (FPC) fonctionne désormais correctement pour les clients connectés.
Auparavant, après la connexion, la page d’accueil ne se chargeait pas à partir du cache et l’en-tête x-magento-cache-debug affichait MISS au lieu de HIT.
AC-14999

_AC-14999 - [Problème GitHub](https://github.com/magento/magento2/issues/40007)_

#### Ajouter des types génériques dans certaines classes php, pour une meilleure prise en charge de l&#39;analyse statique

Le système utilise désormais une définition de type générique pour améliorer considérablement ce paramètre en l’interprétant comme la classe exacte renvoyée par un appel de méthode .

_AC-15013 - [Problème GitHub](https://github.com/magento/magento2/issues/40017) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40119)_

#### [Problème] amélioration de la gestion des erreurs dans SchemaBuilder

Cette requête d’extraction améliore la gestion des messages d’erreur du schéma de base de données. Cela nous aide à identifier les problèmes sans procéder à un débogage détaillé.

_AC-15020 - [Problème GitHub](https://github.com/magento/magento2/issues/39816) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39799)_

#### API REST : appel à une fonction membre getVideoProvider() sur null

Correction d’un problème en raison duquel l’appel de l’API enfant du produit configurable renvoyait une erreur de serveur interne 500 si un produit enfant n’avait qu’une vidéo YouTube et aucune autre image.
L’erreur est due à une référence nulle dans ExternalVideoEntryConverter.
Désormais, l’API renvoie correctement les produits enfants avec des entrées de galerie multimédia, y compris des données vidéo externes, sans générer d’erreurs.
Cela permet de récupérer correctement tous les types de médias pour les produits enfants via l’API REST.

_AC-15046 - [Problème GitHub](https://github.com/magento/magento2/issues/40021)_

#### [W3C] Supprimer le texte/javascript de la déclaration de balise de script de cookie

Ce PR a supprimé l’attribut type=« text/javascript » inutile de la balise de script de cookie pour la conformité à HTML5.

_AC-15061 - [Problème GitHub](https://github.com/magento/magento2/issues/39982) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39983)_

#### [Problème] Corrigez quelques fautes de frappe dans les commentaires PHPDoc.

Ce PR corrige les quelques fautes de frappe dans le phpdoc

_AC-15075 - [Problème GitHub](https://github.com/magento/magento2/issues/40042) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38809)_

#### [Problème] Supprimer l’utilisation de sprintf dans les appels d’expression

Cette requête d’extraction supprime l’utilisation de sprintf dans l’appel de fonction d’expression dans le cœur de Magento.

_AC-15183 - [Problème GitHub](https://github.com/magento/magento2/issues/40050) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40033)_

#### Impossible de réindexer tous les non valides sur les indexeurs multi-threads avec le verrouillage d’application actif

Ce problème corrige un échec de l’indexeur multithread lorsque use_application_lock était activé.
Auparavant, les verrous de base de données étaient perdus lors du traitement parallèle, ce qui laissait les indexeurs « en état de fonctionnement » et provoquait des erreurs SQL (table introuvable).
Dans Magento 2.4.9-alpha3, le correctif garantit que les indexeurs se réindexent correctement avec le verrouillage d’application activé.

_AC-15270 - [Problème GitHub](https://github.com/magento/magento2/issues/40102) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### Types de retour non clairs/non valides dans Magento\Framework\Escaper

Le système accepte les types pour les méthodes d&#39;échappement Lors de l&#39;analyse statique à l&#39;aide de phpstan au niveau 5

_AC-15272 - [Problème GitHub](https://github.com/magento/magento2/issues/40012) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40114)_

#### [Problème ] autoriser la configuration spécifique à la file d’attente à dépasser la valeur max-messages par défaut

Le système autorise désormais la configuration spécifique à la file d’attente à dépasser la valeur max-messages par défaut

_AC-15284 - [Problème GitHub](https://github.com/magento/magento2/issues/40121) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40110)_

#### [Problème ] Dupliquez le fpc de cache pour la même page avec la même requête lorsque vous utilisez un vernis

Cette requête PR corrige les entrées de cache pleine page en double lors de l’utilisation du vernis en normalisant l’ordre des paramètres de requête, assurant ainsi la cohérence des clés de cache pour des requêtes identiques.
Améliore le taux d’accès au cache et les performances des URL avec les mêmes paramètres dans différentes séquences.

_AC-15325 - [Problème GitHub](https://github.com/magento/magento2/issues/39706) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39704)_

#### Les thèmes de la communauté contiennent des ressources pour les modules d’édition Commerce

Suppression des ressources de style Commerce uniquement des thèmes de la communauté en les déplaçant vers leurs répertoires de module respectifs. Cela empêche le CSS inutilisé d’être regroupé dans l’édition de la communauté, ce qui réduit la charge utile inutile et élimine les règles de style inactives tout en assurant un style approprié lorsque les modules Commerce sont activés.

_AC-15347 - [Problème GitHub](https://github.com/magento/magento2/issues/21446) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/9bcd880a)_

#### [Problème] le code de magasin ajouté aux URL doit être global

Ce PR résout le problème en s’assurant que le paramètre « Ajouter le code de la boutique aux URL » est récupéré à l’aide de la portée globale dans le code principal

_AC-15365 - [Problème GitHub](https://github.com/magento/magento2/issues/40069) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40065)_

#### [Problème] Ne consignez le plug-in non déclaré que s’il n’est pas désactivé

Cette requête d’extraction corrige et consigne les plug-ins qui ne sont pas déclarés et qui ne sont pas utilisés (instance activée et manquante).

_AC-15386 - [Problème GitHub](https://github.com/magento/magento2/issues/40086) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40081)_

#### [Problème] Petit nettoyage, suppression des clés dupliquées du tableau

Le système a maintenant effectué un petit nettoyage et aucune erreur trouvée concernant le tableau ne comporte 2 clés en double avec la valeur &#39;Poids (et au-dessus)&#39;

_AC-15414 - [Problème GitHub](https://github.com/magento/magento2/issues/39851) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39844)_

#### Magento 2.4.8-p2, magento/framework version 103.0.8-p2 : classe EmailMessage appelant une méthode inexistante

La classe EmailMessage gère désormais correctement la récupération du corps de l’e-mail.
Auparavant, dans Magento 2.4.8-p2 avec magento/framework version 103.0.8-p2, la classe Magento\Framework\Mail\EmailMessage tentait d’appeler une méthode inexistante (getTextBody) sur l’objet de message électronique Symfony. Cette erreur se produisait lorsque des modules tiers ou des personnalisations utilisaient cette méthode pour le traitement des e-mails.
Désormais, la classe EmailMessage n’appelle plus de méthodes non définies, ce qui empêche ces erreurs. AC-15446

_AC-15446 - [Problème GitHub](https://github.com/magento/magento2/issues/40170) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/059fd469) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/e9412b24)_

#### [Les correctifs de données/schémas de Magento 2.3.x] getAliases() provoquent des erreurs lors de l’`setup:upgrade`

getAliases() provoque des erreurs lors de la configuration:upgrade, ce PR les corrige

_AC-15559 - [Problème GitHub](https://github.com/magento/magento2/issues/31396) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38239)_

#### Combinaison non autorisée de classements pour l&#39;opération

_AC-15614 - [Problème GitHub](https://github.com/magento/magento2/issues/40138) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/44329e9d)_

#### [Problème] [PHPDOC] Correction d’un phpdoc incorrect Magento\Framework\DB\Adapter\AdapterInterface::quoteColumnAs()

Ce PR met à jour la PHPDoc pour \Magento\Framework\DB\Adapter\AdapterInterface::quoteColumnAs() afin de refléter correctement le fait que le paramètre $alias peut être nul en plus de la chaîne. Cela résout les problèmes PHPStan au niveau 5+ et améliore la compatibilité de l’outillage de qualité du code.

_AC-15626 - [Problème GitHub](https://github.com/magento/magento2/issues/39598) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39581)_

#### Combinaison non autorisée de classements dans le module urlrewrite

_AC-15647 - [Problème GitHub](https://github.com/magento/magento2/issues/40189) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/44329e9d)_

#### La condition n’est jamais remplie dans `\Magento\Framework\Escaper::escapeScriptIdentifiers`

Correction d’une condition inatteignable dans \Magento\Framework\Escaper::escapeScriptIdentifiers en remplaçant la vérification de false par null, en l’alignant avec les valeurs de retour preg_replace et en améliorant la précision du code sans affecter la fonctionnalité.

_AC-15667 - [Problème GitHub](https://github.com/magento/magento2/issues/40195) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/cc0ec250)_

#### Vernis 7.3 (dernière version) - Liens de sous-catégories / options de la catégorie par défaut ne s&#39;affichent pas sur la page d&#39;accueil du front de la boutique

Confirmation que les liens de sous-catégorie manquants sur la page d&#39;accueil du storefront lors de l&#39;utilisation de Varnish 7.3 étaient dus à la gestion des requêtes ESI et à la configuration du serveur plutôt qu&#39;à un défaut de code Magento ; le problème est résolu par les ajustements de configuration recommandés de Varnish, sans changements de code de base requis.

_AC-15674 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/3cf1a106) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/9a62604c)_

#### [Problème] Ajoutez des données de débogage supplémentaires `cache_invalidate` journal

Cette requête d’extraction a amélioré le journal cache_invalidate afin d’inclure le contexte de la requête et la trace de la pile pour les purges complètes du cache, améliorant ainsi le débogage et la visibilité.
Cela permet d’identifier la source des invalidations inattendues du cache complet sans modifier les fonctionnalités existantes.

_AC-15719 - [Problème GitHub](https://github.com/magento/magento2/issues/40204) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40196)_

#### [Problème ] Amélioration de la liste d’exclusion du chargeur automatique du compositeur.

Cette requête d’extraction affine les exclusions du chargeur automatique du compositeur pour ignorer les classes de test, réduire les entrées de classmap inutiles et empêcher les avertissements PSR-4.

_AC-15743 - [Problème GitHub](https://github.com/magento/magento2/issues/40109) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40107)_

#### [Problème] Empêchez les déclarations `db_schema.xml` avec `comment=""` de ne pas interrompre les déploiements sans temps d’arrêt

Le système empêche désormais les déclarations db_schema.xml avec comment= » » d’interrompre les déploiements sans interruption

_AC-15980 - [Problème GitHub](https://github.com/magento/magento2/issues/40254) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40242)_

#### Impossible d’effacer le cache `\Magento\Framework\Filesystem\Glob::glob(...)`

Cette mise à jour du PR introduit un moyen d’effacer le cache statique interne utilisé par \Magento\Framework\Filesystem\Glob, assurant ainsi des résultats nouveaux et précis lorsque les structures de fichiers changent. Elle améliore la fiabilité et l’expérience des développeurs, en particulier dans les scénarios de test et les processus de longue durée pour lesquels les résultats globaux doivent rester à jour.

_AC-15989 - [Problème GitHub](https://github.com/magento/magento2/issues/35741) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/35742)_

#### L’URL du lien Leaders ReadME possède une redirection permanente.

Mise à jour du lien README Leaders en remplaçant l’URL définitivement redirigée et expirée par des liens de travail corrects, afin de garantir que les pages des contributeurs et des responsables s’ouvrent correctement.

_AC-16046 - [Problème GitHub](https://github.com/magento/magento2/issues/40292) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/913bf1a6)_

#### [Problème] [PHPDOC] Correction d’un mauvais phpdoc Magento\Eav\Model\ResourceModel\Entity\Attribute\Collection

Correction des annotations PHPDoc pour joinLeft() dans la collection d’attributs afin de permettre des définitions de tableau appropriées, ce qui améliore l’exactitude du code et la compatibilité avec des outils tels que PHPStan.

_AC-16187 - [Problème GitHub](https://github.com/magento/magento2/issues/40354) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39155)_

#### Assurez-vous qu’une seule commande échoue à consigner l’erreur (fichier ou stderr) sans arrêter l’exécution des commandes d’interface de ligne de commande suivantes.

Le système s’assure désormais qu’une seule commande échoue et consigne l’erreur (fichier ou stderr) sans arrêter l’exécution des commandes d’interface de ligne de commande suivantes

_AC-16244 - [Problème GitHub](https://github.com/magento/magento2/issues/40006) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40063)_

#### [Problème ] ajoutez le type int à $maxAge dans le noyau PageCache

Cette requête PR garantit que le paramètre $maxAge dans le noyau PageCache est strictement typé comme un entier pour améliorer la sécurité du type et empêcher les erreurs d&#39;analyse PHPStan/statique dans la gestion du cache.

_AC-16313 - [Problème GitHub](https://github.com/magento/magento2/issues/40438) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/36600)_

#### Événement Ajouter au panier : prix vides

Correction d’un problème en raison duquel les prix des produits étaient renvoyés comme nuls dans l’observateur d’événement checkout_cart_product_add_after lors du processus d’ajout au panier.
Désormais, le prix de base et les valeurs de prix associées sont correctement récupérés, ce qui garantit que des données précises sont disponibles pour les observateurs et les implémentations personnalisées.

_AC-5966 - [Problème GitHub](https://github.com/magento/magento2/issues/35638) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/3b5ac075)_

#### Correctif de type PHP8.1

Les produits associés sont désormais initialisés à un tableau vide au lieu de false lorsque le mode de traitement strict n’est pas actif ou lorsque des informations sur les produits sont disponibles. Cette modification garantit que la logique ultérieure traitant les produits associés se comporte de manière cohérente, améliorant la stabilité et la prévisibilité du processus de préparation du produit.

_AC-6017 - [Problème GitHub](https://github.com/magento/magento2/issues/35808) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/35842)_

#### Type attendu &#39;Magento\Customer\Api\Data\GroupInterface&#39;. &#39;Magento\Customer\Model\Group&#39; trouvé.

Correction d’un problème en raison duquel l’enregistrement d’un groupe de clients via GroupRepositoryInterface à l’aide de GroupFactory provoquait une erreur de type.
Auparavant, le référentiel attendait GroupInterface, mais les instances de modèle de groupe étaient transmises, ce qui entraînait une erreur irrécupérable.
Désormais, les groupes de clients peuvent être enregistrés via le référentiel en assurant une implémentation correcte de l’interface.
Cela résout les avertissements IDE et les erreurs d’exécution lors de la création ou de la mise à jour par programmation de groupes de clients.

_AC-6909 - [Problème GitHub](https://github.com/magento/magento2/issues/36269)_

#### Validation des champs dans les avoirs

Correction d&#39;un problème en raison duquel la validation du champ sur la page de l&#39;avoir empêchait l&#39;envoi même après le remplissage des champs personnalisés obligatoires.
Désormais, la validation fonctionne correctement et le bouton d’envoi est activé une fois tous les champs obligatoires renseignés.

_AC-8308 - [Problème GitHub](https://github.com/magento/magento2/issues/37182) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/64823f95)_

#### [Problème] Supprimer la balise `@author` interdite du framework (partie 3)

Le système adhère désormais aux normes de codage en supprimant la balise `@author` interdite de certains modules, ce qui améliore la qualité globale du code. Auparavant, la présence de cette balise dans certains modules enfreignait les normes de codage établies.

_AC-8343 - [Problème GitHub](https://github.com/magento/magento2/issues/37270) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37020)_

#### [Problème ] utilisez la promotion de propriété du constructeur dans le module pour envoyer le graphe ami ql

Le système utilise désormais la promotion de propriétés du constructeur dans le module GraphQL « Envoyer un ami », ce qui améliore la lisibilité du code et réduit la complexité. Auparavant, le module utilisait des propriétés qui occupaient de nombreuses lignes, ce qui rendait le code plus complexe et moins lisible.

_AC-8346 - [Problème GitHub](https://github.com/magento/magento2/issues/37235) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37197)_

#### [Problème] Supprimer la balise `@author` interdite

Cette requête d’extraction supprime `@author` balise de la base de code

_AC-8349 - [Problème GitHub](https://github.com/magento/magento2/issues/37266) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37016)_

#### [Problème] Supprimer la balise `@author` interdite

Cette requête d’extraction supprime `@author` balise de la base de code

_AC-8350 - [Problème GitHub](https://github.com/magento/magento2/issues/37265) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37015)_

#### [Problème] Supprimer la balise `@author` interdite de `Magento_Downloadable`

Le système adhère désormais aux normes de codage en supprimant la balise `@author` interdite de certains modules, ce qui améliore la qualité globale du code. Auparavant, la présence de cette balise dans certains modules enfreignait les normes de codage établies.

_AC-8355 - [Problème GitHub](https://github.com/magento/magento2/issues/37251) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37001)_

#### [Problème] Supprimer la balise `@author` interdite

Le système respecte désormais les normes de codage en supprimant la balise `@author` interdite de certains modules, ce qui améliore la qualité et la cohérence du code. Auparavant, la présence de cette balise dans certains modules enfreignait les normes de codage établies.

_AC-8358 - [Problème GitHub](https://github.com/magento/magento2/issues/37264) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37014)_

#### [Problème] Supprimer la balise `@author` interdite

Cette requête d’extraction supprime `@author` balise de la base de code

_AC-8359 - [Problème GitHub](https://github.com/magento/magento2/issues/37262) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37012)_

#### [Problème] Supprimer la balise `@author` interdite

Le système respecte désormais les normes de codage en supprimant la balise `@author` interdite de certains modules, ce qui améliore la qualité globale du code. Auparavant, la présence de cette balise dans certains modules enfreignait les normes de codage établies.

_AC-8360 - [Problème GitHub](https://github.com/magento/magento2/issues/37261) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37011)_

#### [Problème] Supprimer la balise `@author` interdite

Le système respecte désormais les normes de codage en supprimant la balise `@author` interdite de certains modules, ce qui garantit un code plus propre et plus normalisé. Auparavant, la présence de cette balise dans certains modules enfreignait les normes de codage établies.

_AC-8361 - [Problème GitHub](https://github.com/magento/magento2/issues/37260) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37010)_

#### [Problème] Supprimer la balise `@author` interdite

Cette requête d’extraction supprime `@author` balise de la base de code

_AC-8362 - [Problème GitHub](https://github.com/magento/magento2/issues/37259) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37009)_

#### [Problème] Supprimer la balise `@author` interdite

Le système adhère désormais aux normes de codage en supprimant la balise `@author` interdite de certains modules, ce qui améliore la qualité globale du code. Auparavant, la présence de cette balise dans certains modules enfreignait les normes de codage établies.

_AC-8363 - [Problème GitHub](https://github.com/magento/magento2/issues/37258) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37008)_

#### [Problème] Supprimer la balise `@author` interdite de `Magento_Backup` et `Magento_Bundle`

Cette requête d’extraction supprime `@author` balise de la base de code

_AC-8367 - [Problème GitHub](https://github.com/magento/magento2/issues/37244) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/36979)_

#### [Problème] Supprimer la balise `@author` interdite

Le système adhère désormais aux normes de codage en supprimant la balise `@author` interdite de certains modules, ce qui améliore la qualité globale du code. Auparavant, la présence de cette balise dans certains modules enfreignait les normes de codage établies.

_AC-8375 - [Problème GitHub](https://github.com/magento/magento2/issues/37257) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37007)_

#### [Problème] Supprimer la balise `@author` interdite

Le système adhère désormais aux normes de codage en supprimant la balise `@author` interdite de certains modules, ce qui améliore la qualité globale du code. Auparavant, la présence de cette balise dans certains modules enfreignait les normes de codage établies.

_AC-8376 - [Problème GitHub](https://github.com/magento/magento2/issues/37256) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37006)_

#### [Problème] Supprimer la balise `@author` interdite

Le système adhère désormais aux normes de codage en supprimant la balise `@author` interdite de certains modules, ce qui améliore la qualité globale du code. Auparavant, la présence de cette balise dans certains modules enfreignait les normes de codage établies.

_AC-8400 - [Problème GitHub](https://github.com/magento/magento2/issues/37254) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37004)_

#### [Problème] Supprimer la balise `@author` interdite

Le système adhère désormais aux normes de codage en supprimant la balise `@author` interdite de certains modules, ce qui améliore la qualité globale du code. Auparavant, la présence de cette balise dans certains modules enfreignait les normes de codage établies.

_AC-8401 - [Problème GitHub](https://github.com/magento/magento2/issues/37255) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37005)_

#### [Problème ] améliorer l’extensibilité de la génération d’URL de service

Le système permet désormais de personnaliser la fonction de génération d’URL de service par le biais de modules externes, ce qui favorise une approche plus facile à gérer des modifications. Auparavant, la personnalisation de cette fonction était réalisée par le biais de préférences, qui n’étaient peut-être pas aussi efficaces ou gérables.

_AC-8813 - [Problème GitHub](https://github.com/magento/magento2/issues/37404) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37403)_

#### [Problème] Correction du nom de variable dans la recherche de catalogues

Le système nomme désormais correctement les variables dans le module du moteur de recherche, ce qui améliore la clarté du code et la facilité de maintenance. Auparavant, un nom de variable non pertinent, $defaultCountry, était utilisé dans le module du moteur de recherche, ce qui entraînait de la confusion.

_AC-9215 - [Problème GitHub](https://github.com/magento/magento2/issues/37810) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/33533)_

#### allow_parallèle_generation doit être défini via la variable d’environnement .

Après le correctif, la variable d’environnement « MAGENTO_DC_CACHE__ALLOW_PARALLEL_GENERATION » peut être utilisée pour définir la configuration « allow_parallèle_generation ».

_ACP2E-3673 - [contribution du code GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

#### [Cloud] La modification du type de colonne du tableau de Int à Decimal à l’aide du fichier db_schema.xml dans Magento 2 entraîne des erreurs

La modification du type de données de colonne ne fonctionne pas correctement. Auparavant, il renvoyait une erreur : l’attribut « identity » n’est pas autorisé.

_ACP2E-3709 - [contribution du code GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### Prise en charge de la nouvelle devise (XCG) dans Adobe

Caribbean Builder (XCG) est ajouté à la liste des devises.

_ACP2E-3790 - [contribution du code GitHub](https://github.com/magento/magento2/commit/520f9e30)_

#### Problème de mise à niveau 2.4.7-p5 en raison de l’ajout d’une nouvelle validation

Correction d’un problème dans la classe SchemaBuilder en raison duquel une « colonne » de clé de tableau non définie provoquait un blocage lors de la création ou des mises à jour de schéma. Cela se produisait lors du traitement des données de table qui n&#39;incluaient pas de clé « colonne ».

_ACP2E-3871 - [contribution du code GitHub](https://github.com/magento/magento2/commit/9ad7d277)_

#### Problème [QUANS]Server potentiellement causé par une clé d’accès S3 non valide

Des informations d’identification AWS S3 incorrectes ne provoquent plus le chargement infini des pages sur le storefront.

_ACP2E-3890 - [contribution du code GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

#### [QUANS] [Cloud] Minify ne fonctionne pas

Les fichiers JS suivants sont désormais entièrement et correctement minimisés lorsque la minimisation JS est activée : mage/backend/tabs.min.j, jquery/jquery.validate.min.js et Magento_PageBuilder/js/form/element/validator-rules-mixin.min.js. Par conséquent, la validation des champs de classe CSS de Page Builder fonctionne comme prévu.

_ACP2E-3925 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/47721be6)_

#### Erreur d’obsolescence de PHP8.4 : E_USER_ERROR après la mise à niveau vers Adobe Commerce 2.4.8

*AUCUNE NOTE DE MISE À JOUR N’EST REQUISE*
Les scénarios concernant les clients et clientes ne sont pas affectés par le correctif.

_ACP2E-3963 - [contribution du code GitHub](https://github.com/magento/magento2/commit/7accebfa)_

#### La tâche cron n’efface pas la table de base de données, ce qui entraîne une panne de la Galera.

Le nettoyage des tables de journaux des modifications s’exécute désormais par lots pour éviter des opérations de suppression importantes.

_ACP2E-3995 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/52f46328)_

#### Le JS non miniaturisé se charge parfois en ignorant « activer les minifications js »

Avant la correction, même si la minimisation était activée, certains fichiers JS étaient demandés sans le préfixe « min », ce qui entraînait l’apparition du code d’état 404. Après le correctif, lorsque la minimisation est activée, aucune ressource JS non minimisée n’est demandée.

_ACP2E-4058 - [contribution du code GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Échec de l’affichage du sélecteur de date dans Admin dans le groupe d’attributs personnalisé

Correction d’un problème en raison duquel la fenêtre contextuelle de calendrier des attributs de date s’affichait hors écran lorsqu’elle était affectée à des groupes d’attributs personnalisés.

_ACP2E-4060 - [Problème GitHub](https://integration-5ojmyuq-3ssteurpe3xzy.us-5.magentosite.cloud/) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### La vérification des autorisations ACL de production a provoqué une dégradation des performances - la méthode populateAcl est le goulot d’étranglement

Traitement optimisé des règles ACL

_ACP2E-4114 - [contribution du code GitHub](https://github.com/magento/magento2/commit/98f028ab)_

#### Passage en caisse ne se chargeant pas dans la dernière version avec AC-15867 + ACP2E-4296 et SCD compact

Avant la correction, le chargement de scripts JavaScript personnalisés par le biais de la section head pouvait entraîner des problèmes. Après l’introduction du nouveau paramètre, ces scripts peuvent être automatiquement différés, ce qui garantit une meilleure compatibilité avec le framework Magento 2.

_ACP2E-4319 - [contribution du code GitHub](https://github.com/magento/magento2/commit/1c547060)_

#### Avertissement d’obsolescence : utilisez moment.updateLocale(localeName, config) pour modifier un paramètre régional existant. moment.defineLocale(localeName, config)

Avant la correction, un avertissement obsolète était généré dans la console du navigateur. Désormais, après la correction, cet avertissement n’est plus affiché.

_ACP2E-4338 - [contribution du code GitHub](https://github.com/magento/magento2/commit/2687b487)_

#### Incompatibilité avec MariaDB 10.11

Auparavant, l’installation de la dernière version de Magento 2 échouait lors de l’utilisation de MariaDB 10.11, ce qui empêchait l’achèvement du processus de configuration. Ce problème a été résolu en mettant à jour la gestion de la compatibilité de la base de données pour prendre en charge MariaDB 10.11.x pendant l’installation.

_ACP2E-4367 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/31258bf6)_

### Framework, Recherche

#### Opensearch 2.19.1 legal_argument_exception sur les catégories à prix unique

Opensearch ne lance plus d&#39;exception d&#39;argument illégal_argument_exception sur les catégories contenant tous les produits au même prix. Auparavant, elle comportait l’exception « [from] le paramètre ne peut pas être négatif ».

_ACP2E-3896 - [contribution du code GitHub](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL

#### La commande est passée dans GraphQL avec un mode d’expédition non valide

Correction d’un problème en raison duquel les commandes pouvaient être passées via GraphQL à l’aide d’une méthode d’expédition désactivée ou non valide.
Désormais, le système valide le mode d’expédition sélectionné et renvoie une erreur s’il n’est pas disponible, empêchant la création de la commande.

_AC-10472 - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38268) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a8cf637b)_

#### Exception générée lors de l’exécution de la requête GraphQl

Correction d’un problème en raison duquel une requête GraphQL générait une exception en raison d’un paramètre de tri non valide. Après le correctif, la requête s’exécute correctement sans générer d’erreurs ou de journaux d’exceptions.

_AC-14835 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a8cf637b)_

#### Erreur de serveur interne lors de l’ajout du produit de carte cadeau au panier via la mutation AddProductsToCart, y compris custom_attributesV2.

Correction d’une erreur de serveur interne déclenchée lors de l’ajout de produits de carte cadeau (et d’options personnalisées similaires) au panier via GraphQL avec custom_attributesV2 ; le correctif gère correctement les valeurs d’attribut complexes, ce qui permet d’ajouter des produits sans erreur.

_AC-15856 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/7fa400a7)_

#### Champs nuls dans la requête `Country`

Correction d&#39;un problème en raison duquel les commandes contenant des articles virtuels, remboursés et expédiés restaient en cours de traitement en veillant à ce que les articles virtuels soient inclus dans les calculs de quantité expédiée, ce qui permettait à l&#39;état de la commande de passer correctement à l&#39;état terminé.

_AC-7731 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/ef666cd9)_

#### La requête GraphQL « customerOrders » avec l’attribut « number » entraîne une erreur de serveur interne

Correction d’un problème en raison duquel la requête GraphQL customerOrders renvoyait une erreur de serveur interne lors de la demande du champ numérique.
Désormais, le résolveur renvoie correctement l’identifiant d’incrément de commande, ce qui permet à la requête de s’exécuter correctement et de récupérer le numéro de commande.

_AC-8949 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/3b5ac075)_

#### La réponse GraphQL pour l&#39;emplacement de commande n&#39;inclut pas le message d&#39;exception

Annulation de la modification précédente qui renvoyait des erreurs dans un format différent. Désormais, les erreurs potentielles sont renvoyées de manière cohérente, sans interrompre le schéma GraphQL. Ceci doit être ajouté en tant que BIC connu, approuvé par PM ici : https://jira.corp.adobe.com/browse/ACP2E-3399?focusedId=45248897&page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel#comment-45248897

_ACP2E-3399 - [contribution du code GitHub](https://github.com/magento/magento2/commit/9608ca21)_

#### La réponse GraphQL pour l&#39;emplacement de la commande est partiellement localisée

Les erreurs renvoyées par la mutation placeOrder GraphQl n’ont pas été entièrement localisées. Désormais, dans un contexte multilingue, les erreurs sont correctement traduites.

_ACP2E-3506 - [contribution du code GitHub](https://github.com/magento/magento2/commit/9608ca21)_

#### Appels simultanés pour réorganiser l’API GraphQL - Mêmes produits ajoutés à différentes lignes

Correction du problème où les appels simultanés à l’API Reorder GraphQL entraînent l’ajout des mêmes produits sous forme de lignes différentes, ce qui entraînait des incohérences au niveau des données.

_ACP2E-3774 - [contribution du code GitHub](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### La mutation updateCustomerEmail GraphQL (Modifier l’adresse e-mail) ne déclenche pas l’envoi de la notification par e-mail

Auparavant, les e-mails n’étaient pas envoyés aux clients après la mise à jour réussie de leurs adresses e-mail sur leurs comptes. Une fois le correctif appliqué, les clients et clientes reçoivent désormais des notifications par e-mail après avoir correctement mis à jour leurs adresses e-mail.

_ACP2E-3785 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### Attribut dynamique non mis à jour dans Gift Registry via updateGiftRegistry Mutation

Auparavant, avant ce correctif par le biais de la mutation updateGiftRegistry, l’attribut personnalisé du registre des cadeaux n’était pas modifié ou mis à jour par le biais de mutations GraphQL. Une fois ce correctif appliqué, l&#39;attribut dynamique du registre des cadeaux peut être mis à jour avec la mutation updateGiftRegistry.

_ACP2E-3805 - [Problème GitHub](https://mcstaging.briscoes.co.nz/)_

#### GraphQL de commande client : la récupération des catégories de produits pour le produit associé n’est « pas visible individuellement ».

Avant la correction, si la commande contenait un produit masqué, ses catégories affichaient un tableau vide dans la réponse GraphQl de commande client.
Désormais, après la correction, les catégories de produits sont incluses dans la réponse d’une requête GraphQl de commande client même si le produit est masqué.

_ACP2E-3945 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Les éléments de liste de souhaits ne sont pas partagés entre les vues de magasins dans un site web dans la requête GraphQL.

Avant la correction, les éléments de la liste de souhaits étaient filtrés par ID de magasin. Désormais, après le correctif, les éléments de liste de souhaits sont filtrés par site web.

_ACP2E-3987 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/2a252ae6)_

#### [Cloud] getRemoteAddress 127.0.0.1 de retour sur production

Avant ce correctif, l’adresse distante n’était pas déterminée correctement lorsque le serveur d’applications est utilisé. Après le correctif, l’adresse distante est correctement déterminée, associée à une configuration d’en-tête appropriée dans nginx et une configuration d’en-tête .

_ACP2E-3991 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/47721be6)_

#### [QUANS] Confirmer la réversion du comportement de gestion des exceptions d&#39;emplacement d&#39;ordre GQL

Correction d’une modification rétrocompatible pour la mutation placeOrder.

_ACP2E-4031 - [contribution du code GitHub](https://github.com/magento/magento2/commit/52f46328)_

#### Mappage de problème du message traduit en code d’erreur lors de la commande via GraphQL

Correction d’un problème en raison duquel le message d’exception traduit était utilisé pour mapper le code d’erreur pour les requêtes GraphQL, provoquant des codes d’erreur inconnus pour les erreurs connues.

_ACP2E-4033 - [contribution du code GitHub](https://github.com/magento/magento2/commit/fab20b00)_

#### Le filtre [CLOUD] Commandes client ne fonctionne pas pour les dates

Après la correction, la récupération des commandes via GraphQL à l’aide d’un filtre de période renvoie le résultat correct.

_ACP2E-4090 - [contribution du code GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

#### Répondre aux questions soulevées dans le ACP2E-4031

Avant la correction, la position du nœud d’erreur ne permettait pas une compatibilité transparente avec les versions 2.4.7 et 2.4.9. Désormais, après le correctif, le nœud d’erreur est correctement placé pour s’adapter aux deux versions.

_ACP2E-4115 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

#### Parent du lot présentant en rupture de stock même l’enfant a un stock dans l’appel Graphql.

Après le correctif, la demande d’une liste de produits à l’aide de GraphQL renvoie le statut de stock correct pour les produits groupés.

_ACP2E-4168 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a1c57b2e) - [Contribution du code GitHub](https://github.com/magento/inventory/commit/5632fb5e)_

#### Exception GraphQL dans SWAT

Après le correctif, les réponses aux requêtes GraphQL sont alignées sur les spécifications GraphQL via HTTP. Un code de réponse 4XX est renvoyé lorsqu’il est impossible d’analyser la requête, que la requête n’est pas autorisée ou qu’il existe un autre problème général avec la requête. Si la requête est analysée et peut être traitée, un code de réponse 200 est renvoyé.

_ACP2E-4194 - [contribution du code GitHub](https://github.com/magento/magento2/commit/45cbf9b6)_

#### Produit non supprimé de la liste de comparaison une fois la liste affectée au client

Une fois la liste de comparaison d’un utilisateur invité attribuée à un compte client, les produits ajoutés en tant qu’invité peuvent désormais être supprimés par le client.
Auparavant, les opérations de suppression échouaient, car les éléments ajoutés par les invités n’étaient pas correctement liés au compte du client après l’affectation.

_ACP2E-4244 - [contribution du code GitHub](https://github.com/magento/magento2/commit/c135fc3a)_

#### Réponse d’erreur incorrecte du GraphQL updateCartItems

Auparavant, lorsqu’une demande graphQL était envoyée pour un article en quantité insuffisante, un message d’erreur correct avec un code d’erreur était renvoyé, ainsi que le calcul de la quantité et du prix demandé, même si l’article n’était pas disponible. Une fois ce correctif appliqué, un message d’erreur correct avec un code d’erreur est maintenant renvoyé et la quantité de l’élément est définie sur son ancienne valeur si elle n’est pas disponible dans la réponse.

_ACP2E-4283 - [contribution du code GitHub](https://github.com/magento/magento2/commit/cbca0396)_

#### Bogue d’affectation de commande d’invité intersite dans le plug-in MergeGuestOrder

Avant la correction, l’affectation d’un client de commande invité ne prenait pas en compte les options de partage de compte. Désormais, après la correction, une commande est affectée à un client si le client et la boutique de commandes correspondent (étant donné que l’option de partage du compte client est définie sur « Par site web ».

_ACP2E-4312 - [contribution du code GitHub](https://github.com/magento/magento2/commit/c135fc3a)_

### GraphQL, Inventaire / MSI

#### Problème avec only_x_left_in_stock dans Magento 2 GraphQL - Calcul incorrect lors de l’utilisation de seuils

Correction d’un problème en raison duquel le champ GraphQL only_x_left_in_stock renvoyait la valeur null en raison d’une double déduction incorrecte de MinQty. Le calcul a été corrigé, de sorte qu’il renvoie désormais la valeur boursière exacte en fonction des seuils.

_AC-15832 - [Contribution du code GitHub](https://github.com/magento/inventory/commit/35458c7f)_

#### Incohérences de mutation mergeCart GraphQL

Après le correctif, la demande GraphQL de panier de fusion vérifie correctement la quantité de produit, en prenant en compte la configuration du stock.

_ACP2E-4184 - [contribution du code GitHub](https://github.com/magento/inventory/commit/5632fb5e)_

### GraphQL, Produit

#### Type_média manquant dans l’interface MediaGalleryInterface de GraphQL du produit

La requête GraphQL MediaGallery inclut désormais le champ « types » pour les types d’images de produit. Auparavant, ce champ « types » n’existait pas dans la requête GraphQL MediaGallery.

_ACP2E-3880 - [contribution du code GitHub](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL, Sécurité

#### La réinitialisation du mot de passe du client via GraphQL ne respecte pas les restrictions

Correction d’un problème en raison duquel les demandes de réinitialisation de mot de passe client effectuées par le biais de mutations de GraphQL ne respectaient pas les restrictions de réinitialisation de mot de passe configurées sous Stocker > Configuration > Clients > Configuration client > Options de mot de passe. Ces paramètres sont désormais correctement appliqués.

_ACP2E-3992 - [contribution du code GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

### Importer/exporter

#### [Problème] Corriger le type de paramètre

Correction d’une incohérence de type de paramètre dans le module Import/Export où une valeur précédemment définie en tant que chaîne est désormais correctement définie sous la forme d’un tableau. Cela correspond à l’entrée attendue du contrôleur d’exportation et empêche les avertissements d’analyse statique.

_AC-11665 - [Problème GitHub](https://github.com/magento/magento2/issues/38529) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/64823f95)_

#### [Problème] Copyedit : remplacer « copie » par « copie »

PR corrige la modification de copie mineure pour corriger l’orthographe de « copie »

_AC-13300 - [Problème GitHub](https://github.com/magento/magento2/issues/39311) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39307)_

#### Le fichier JSON d’importation de produit de point d’entrée REST ne valide pas les champs obligatoires

Le champ Nom est désormais requis lors de la création de nouveaux produits par le biais du processus d’importation (administrateur ou API). Avant la correction, vous auriez pu créer de nouveaux produits sans nom, ce qui aurait rompu l’interface d’administration et créé des produits non valides.

_ACP2E-3660 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### Option de filtre de site web manquante dans le processus d’exportation

Il est désormais possible de filtrer les produits par site web lors de la création d’une exportation de produits.

_ACP2E-3720 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/520f9e30)_

#### Dupliquer AC-13913 - Nettoyage statique des attributs de manière asynchrone.

Après le correctif, il n’y a plus d’erreur de clé de tableau « apply_to » non définie lorsque de nombreuses instances de \Magento\CatalogImportExport\Model\Import\Product\Type\AbstractType sont créées.

_ACP2E-3752 - [contribution du code GitHub](https://github.com/magento/magento2/commit/520f9e30)_

#### Import de produit Csv : impossible de déparamétrer une image d’échantillon

Avant la correction, vous ne pouviez pas mettre à jour l’image d’échantillon d’un produit par le biais de l’importation du produit. Désormais, après la correction, si vous marquez la colonne d’image d’échantillon de produit avec le marqueur vide configuré, l’image sera définie sur masquée.

_ACP2E-3972 - [contribution du code GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

#### L’importation de produits génère des URL vides pour la portée de la boutique

La clé URL du produit dans la vue de magasin hérite désormais de la valeur définie dans la portée par défaut si url_key a une valeur vide dans la source de données d’importation. Auparavant, la définition de url_key sur une valeur vide dans la source de données d&#39;importation pour un enregistrement d&#39;affichage de magasin entraînait le remplacement de url_key par une valeur vide dans cette portée.

_ACP2E-4038 - [contribution du code GitHub](https://github.com/magento/magento2/commit/52f46328)_

#### Le processus d’importation de produit rencontre une erreur si un attribut à sélection multiple est configuré comme requis

Correction d’un problème en raison duquel les importations de produits échouaient si un attribut obligatoire de type sélection multiple était inclus. La validation des données réussit désormais correctement, ce qui permet au processus d’importation du produit de se terminer correctement.

_ACP2E-4057 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [CLOUD] Les produits sans reliquat sélectionnés sur gérer le stock permettent toujours aux clients de passer commande au-dessus de nos niveaux de stock lors de l&#39;importation

Après le correctif, il n’est plus possible d’importer une valeur inacceptable pour l’attribut « allow_backorders » du produit.

_ACP2E-4116 - [contribution du code GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

#### Échec de l’importation du produit en raison d’une longueur de description supérieure à 65 536 caractères Validation

Après le correctif, il est possible d’importer des attributs de produit avec du texte de type dont les valeurs dépassent 65 536 caractères.

_ACP2E-4119 - [contribution du code GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

#### Les filtres d’exportation des attributs Oui-Non du produit ne fonctionnent pas comme prévu

Après la correction, les produits exportés filtrés par un attribut Oui/Non contiennent les produits attendus qui respectent les filtres appliqués.

_ACP2E-4160 - [contribution du code GitHub](https://github.com/magento/magento2/commit/ee918f0d)_

#### Problème lié à la mise à jour du prix de l’option de bundle par site web via l’importation

Il est désormais possible d’exporter et d’importer les prix de sélection des options de bundle par site web

_ACP2E-4243 - [contribution du code GitHub](https://github.com/magento/magento2/commit/98f028ab)_

#### Impossible d’importer un client avec une adresse e-mail en majuscules

Correction d’une erreur de clé de tableau non définie lors de l’importation de clients avec des e-mails en majuscules lorsque le Partage de compte est défini sur Global. La normalisation des e-mails est désormais cohérente tout au long du processus d’importation, ce qui permet d’importer les clients indépendamment de la casse des e-mails. Le comportement de partage de compte au niveau du site web reste inchangé.

_ACP2E-4373 - [contribution du code GitHub](https://github.com/magento/magento2/commit/31258bf6)_

### Import/export, client/clients

#### L’administrateur peut importer un client dont la date de naissance est postérieure à la date actuelle.

Correction d’un problème en raison duquel les administrateurs pouvaient importer des clients dont la date de naissance était définie dans le futur. Le système valide désormais la BD lors de l’importation, affiche un message d’erreur pour les enregistrements non valides et empêche l’importation des clients dont la date de naissance est à venir, garantissant ainsi l’exactitude des données client.

_AC-13641 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/8670a2b4)_

### Inventaire / MSI

#### Le retrait de la boutique ne respecte pas le rayon de recherche maximal lorsque l’adresse est modifiée au passage en caisse

Désormais, le magasin présélectionné dans « Choisir en magasin » sera mis à jour si l’adresse de livraison change. Auparavant, une fois qu’un magasin était présélectionné, il ne changeait pas même si la nouvelle adresse de livraison ne se trouvait pas dans le rayon du magasin sélectionné

_ACP2E-3728 - [contribution du code GitHub](https://github.com/magento/inventory/commit/07620383)_

#### Aucun magasin n’est disponible après la redirection vers la page d’accueil et le passage en caisse

Le magasin précédemment sélectionné sera maintenant présélectionné dans l’expédition « Choisir en magasin » si le client accède à la page de paiement, puis revient à la page d’accueil et revient enfin à la page de passage en caisse. Auparavant, après être revenu à plusieurs reprises à la page de passage en caisse, le magasin sélectionné dans « Choisir en magasin » était effacé.

_ACP2E-3793 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a20a6ff2) - [Contribution du code GitHub](https://github.com/magento/inventory/commit/62c0d79b)_

#### L’opération de suppression de stocks ne se termine pas

Après la correction, la suppression d’un élément source n’entraîne pas une réindexation complète et ne met à jour que les produits affectés afin d’améliorer les performances.

_ACP2E-3917 - [Contribution du code GitHub](https://github.com/magento/inventory/commit/ee0bf4ad)_

#### [MSI] L&#39;administrateur n&#39;indique pas si le client a été averti de manière asynchrone que la commande est prête pour le retrait

Ajout à l&#39;historique des commandes d&#39;une notification indiquant que le client a été averti de manière asynchrone que la commande est prête pour le retrait

_ACP2E-3968 - [contribution du code GitHub](https://github.com/magento/inventory/commit/29653b1d)_

#### Requêtes de statut du stock dupliquées sur le chargement du devis

Correction de l’exécution en double de la requête cataloginventory_stock_status lors du chargement d’un devis sur le storefront, provoquant des appels de base de données redondants.

_ACP2E-4102 - [contribution du code GitHub](https://github.com/magento/inventory/commit/fc15a9ae)_

#### Après le correctif ACP2E-4118 : la modification du seuil de stock dans l’administration entraîne des quantités vendables négatives et une inadéquation de l’état du stock

Le statut du stock de stock est désormais automatiquement ajusté lorsque les configurations de stock globales Quantité, Commandes en souffrance et Seuil de rupture de stock sont mises à jour via l&#39;importation.

_ACP2E-4142 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a1c57b2e) - [Contribution du code GitHub](https://github.com/magento/inventory/commit/5632fb5e)_

#### Le rapport [CLOUD] Admin n’affiche pas de détails lorsque l’inventaire est mis à jour

Les modifications de la source de l’inventaire des produits sont désormais consignées par le module de journalisation. Avant la correction, lors de l’enregistrement d’un produit et de l’exécution de modifications liées à l’inventaire, les détails n’étaient pas consignés.

_ACP2E-4167 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/cbca0396) - [Contribution du code GitHub](https://github.com/magento/inventory/commit/76b88f7c)_

#### Le produit groupé ne peut pas être ajouté au panier lorsqu’il est marqué comme en stock.

Le statut du stock de produits groupés reflète désormais correctement les réservations de produits enfants et les seuils de rupture de stock.
Auparavant, les produits groupés étaient marqués comme étant « en stock » même lorsqu’un ou plusieurs produits enfants manquaient de quantité vendable suffisante. Cela entraînait des erreurs « Pas assez d’articles en vente » lors de l’ajout du lot au panier.

_ACP2E-4220 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/cbca0396) - [Contribution du code GitHub](https://github.com/magento/inventory/commit/76b88f7c)_

#### Le produit regroupé s’affiche incorrectement comme En rupture de stock sur PDP après l’importation à partir du fichier CSV lorsque l’enfant est affecté à une source/un stock personnalisé (corrigé après une réindexation manuelle)

Après le correctif, la création d’un produit composite à l’aide de l’importation effectue automatiquement la réindexation des stocks, rendant le produit disponible sans avoir à recourir à une réindexation manuelle.

_ACP2E-4233 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/98f028ab) - [Contribution du code GitHub](https://github.com/magento/inventory/commit/5704166a)_

#### [MSI] Échec des tests MFTF liés aux dernières modifications de la ligne principale.

Avant la correction, les clients invités qui choisissaient la cueillette en magasin sans adresse d’expédition recevaient automatiquement l’adresse de facturation de la boutique, qui ne pouvait pas être modifiée, ce qui entraînait des détails de facture incorrects. Après la correction, l’adresse de facturation est désormais modifiable dans ce scénario, ce qui permet aux invités de saisir leurs propres détails. Les utilisateurs enregistrés verront leur adresse de facturation enregistrée au lieu de celle du magasin.

_ACP2E-4260 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/ab891304) - [Contribution du code GitHub](https://github.com/magento/inventory/commit/13e432a6)_

#### Réservation d&#39;inventaire incorrecte créée pour les cartes-cadeaux virtuelles

Avant la mise en œuvre de ce correctif, la quantité d’une carte cadeau virtuelle contenant plusieurs articles n’était pas reflétée avec précision dans la réservation de stock. Cependant, une fois le correctif appliqué, la quantité de la réservation de stock et les stocks ont été synchronisés.

_ACP2E-4267 - [Contribution du code GitHub](https://github.com/magento/inventory/commit/5704166a)_

#### Échec de la commande de compensation de réservation de stock avec des références de produit nulles et inexistantes

Correction d’un problème en raison duquel l’interface de ligne de commande de compensation de réservation de stock générait une exception si la combinaison traitée avait un ID de commande manquant

_ACP2E-4301 - [contribution du code GitHub](https://github.com/magento/inventory/commit/76b88f7c)_

#### Le produit est en rupture de stock après avoir modifié le boîtier de SKU.

La modification du boîtier de SKU n’entraîne plus la rupture de stock du produit sur le storefront.

_ACP2E-4375 - [contribution du code GitHub](https://github.com/magento/inventory/commit/0836c2ed)_

#### Classer par facettes de prix/prix avec des données non valides

Avant la correction, les prix des offres groupées n’étaient pas correctement indexés lorsque les produits enfants étaient en stock sous des sources personnalisées. Désormais, après la correction, les prix des bundles sont correctement indexés, quelle que soit l&#39;affectation des stocks de produits enfants.

_ACP2E-4380 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/1c547060) - [Contribution du code GitHub](https://github.com/magento/inventory/commit/1f83ed24)_

### Ordre

#### AbstractAddress setData(&#39;custom_attributes&#39;, AttributeValue[]) rompt customAttributes

Les attributs personnalisés sur les adresses sont désormais correctement gérés lors des opérations de passage en caisse et d’API.
Auparavant, l’utilisation de $address->setCustomAttributes(&#39;custom_attributes&#39;, $attributes) pouvait interrompre la gestion des attributs personnalisés, ce qui entraînait une structure incorrecte des valeurs d’attribut.
AC-10568

_AC-10568 - [Problème GitHub](https://github.com/magento/magento2/issues/31644)_

#### Lorsque le client est défini pour une commande de devis, il s&#39;agit toujours d&#39;une commande invité

_AC-11689 - [Problème GitHub](https://github.com/magento/magento2/issues/38540)_

#### La commande n&#39;est pas complète lorsque les articles virtuels, remboursés et expédiés sont mélangés

Correction d&#39;un problème en raison duquel les commandes contenant des articles virtuels, remboursés et expédiés restaient en cours de traitement en veillant à ce que les articles virtuels soient inclus dans les calculs de quantité expédiée, ce qui permettait à l&#39;état de la commande de passer correctement à l&#39;état terminé.

_AC-11691 - [Problème GitHub](https://github.com/magento/magento2/issues/38547)_

#### v2.4.7-p1 Magento reorder -1 numéros de commande

Le système fonctionne comme prévu et, après la réorganisation à partir du serveur principal, le numéro de commande sera unique à 8 chiffres

_AC-12854 - [Problème GitHub](https://github.com/magento/magento2/issues/39089) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39399)_

#### Perte du chargement du fichier d’option personnalisée de produit lors de la récupération avec le mode de paiement par carte de crédit Adobe

Les chargements de fichiers d’option personnalisée du produit sont désormais conservés lors de l’extraction avec le mode de paiement par carte de crédit Adobe.
Auparavant, les chargements de fichiers étaient perdus lors de l’utilisation de ce mode de paiement, mais fonctionnaient avec d’autres.
AC-14306

_AC-14306 - [Problème GitHub](https://github.com/magento/magento2/issues/39647)_

#### Commandes d’administration - impossible de rechercher Will

Correction d’un problème en raison duquel la recherche de commandes par nom de client (par exemple, « Will ») dans la grille de commandes de l’administrateur ne renvoyait aucun résultat. Après la correction, les commandes pertinentes s’affichent correctement lorsqu’elles sont filtrées par nom de client.

_AC-14360 - [Problème GitHub](https://github.com/magento/magento2/issues/36596) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a8cf637b)_

#### Magento 2.4.8 GraphQL - Mise en forme incorrecte des éléments de commande order_date

Correction d’un problème en raison duquel le champ order_date dans la réponse GraphQL était renvoyé au format aaaa-mm-jj.
Désormais, order_date s’affiche correctement au format jj-mm-aaaa.

_AC-14431 - [Problème GitHub](https://github.com/magento/magento2/issues/39805) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Impossible de renvoyer la valeur null pour un problème inattendu concernant le champ non nullable \« AppliedCoupon.code\ »

Adobe Commerce renvoie désormais correctement les codes coupon appliqués via GraphQL lors de l’interrogation des commandes client. Auparavant, dans Adobe Commerce 2.4.8, la récupération d’une commande avec le champ applied_coupons.code (par exemple via la requête customer.orders) pouvait échouer avec une erreur de serveur interne et le message Impossible de renvoyer la valeur null pour le champ « AppliedCoupon.code » non nullable, et applied_coupons était renvoyé en tant que [null] au lieu d’une liste contenant le code de coupon. AC-14484

_AC-14484 - [Problème GitHub](https://github.com/magento/magento2/issues/39841) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/97b2ea42)_

#### L’e-mail d’expédition n’est pas envoyé lorsqu’il est envoyé à partir de la vue Commande admin bien qu’activé dans la configuration du magasin

Le système envoie désormais un e-mail de confirmation d’expédition, car il est activé dans la configuration du magasin où la commande a été passée.

_AC-14563 - [Problème GitHub](https://github.com/magento/magento2/issues/39861) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39897)_

#### Le filtrage sur la date ne fonctionne pas en raison de noms de champ ambigus

Dans Magento 2.4.7-p6, le filtrage de la grille d’ordre par date a été signalé comme provoquant une erreur en raison de jointures avec les modules Braintree.
Le problème impliquait des requêtes joignant les tables braintree_transaction_details et sales_order lors de l&#39;application de filtres de date.
L’ingénierie Adobe Commerce a examiné le cas, mais n’a pas pu reproduire l’erreur dans l’environnement.
Le filtrage par date devrait renvoyer les commandes correspondant au filtre sans erreur.

_AC-15037 - [Problème GitHub](https://github.com/magento/magento2/issues/40024)_

#### La création de commande dans le back-office avec plusieurs produits dont au moins un contient des options personnalisées, entraîne l’ajout de produits supplémentaires indésirables à la commande

Correction d’un problème en raison duquel la création d’une commande dans le backoffice avec plusieurs produits, y compris un avec des options personnalisées, ajoutait involontairement des produits supplémentaires et provoquait des erreurs. Le système ajoute désormais uniquement les produits sélectionnés, ce qui permet de créer des commandes sans éléments inattendus.

_AC-15286 - [Problème GitHub](https://github.com/magento/magento2/issues/40122) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/b5e99d20)_

#### Magento2 : impossible de créer la règle de promotion

Ce correctif de relations publiques, on a
Modèle \Magento\Catalog\Model\ResourceModel\Eav\Attribute au lieu de \Magento\Catalog\Model\ResourceModel\Eav\Attribute dans la méthode \Magento\SalesRule\Model\Rule\Condition\Product::loadAttributeOptions

_AC-15358 - [Problème GitHub](https://github.com/magento/magento2/issues/12176) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/30479)_

#### Magento a modifié le type d’entité de $order après les appels $facture = $this->_factureService->preparationInvoice($order);

Correction d’un problème en raison duquel la modification d’une mise à jour planifiée existante pour une sous-catégorie augmentait incorrectement le nombre d’enfants pour les catégories parents dans la base de données. Le problème entraînait des données de hiérarchie de catégories inexactes après l’enregistrement des mises à jour. Après la correction, le nombre d’enfants reste correct et n’augmente plus de manière inattendue.

_AC-15401 - [Problème GitHub](https://github.com/magento/magento2/issues/40154)_

#### La commande reste dans l&#39;état &#39;traitement&#39; après l&#39;expédition, si les articles sont partiellement remboursés

Correction d’un problème en raison duquel les commandes conservaient le statut Traitement après un remboursement partiel des articles et l’expédition du reste. Le statut de la commande est désormais correctement mis à jour sur Terminé une fois que le total des quantités expédiées et remboursées correspond à la quantité facturée, ce qui garantit une gestion précise du cycle de vie des commandes.

_AC-15419 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/cc0ec250)_

#### L’envoi d’un e-mail de vente à partir du serveur principal donne toujours des résultats, même lorsque désactivé

Correction de la notification par e-mail des ventes du serveur principal pour afficher des messages précis en validant le résultat du service de messagerie, en s’assurant que les utilisateurs sont informés lorsque les e-mails de commande ou de facture sont désactivés et ne sont pas envoyés.

_AC-16059 - [Problème GitHub](https://github.com/magento/magento2/issues/40309) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/c95ed7d7)_

#### Le prix personnalisé de 0 est réinitialisé sur le prix d&#39;origine lors de la réorganisation.

Correction d’un problème en raison duquel les produits avec un prix personnalisé de 0 revenaient à leur prix d’origine lors de la réorganisation.
Désormais, le prix personnalisé est correctement conservé, ce qui garantit un prix précis lors de la réorganisation des articles.

_AC-8147 - [Problème GitHub](https://github.com/magento/magento2/issues/36970) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/01cee3c3)_

#### Passer une commande avec le mode de paiement désactivé

Correction d&#39;un problème en raison duquel les commandes pouvaient être passées à l&#39;aide d&#39;un mode de paiement désactivé via GraphQL.
Désormais, une erreur est renvoyée lors de la tentative de définition ou d’utilisation d’un mode de paiement indisponible, empêchant la création de la commande.

_AC-9605 - [Problème GitHub](https://github.com/magento/magento2/issues/37983) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a8cf637b)_

#### Statut de la commande bloqué lors du traitement

Avant la correction, lors de la commande d’un produit groupé avec l’option « Expédier ensemble » activée, le statut de la commande ne passait pas automatiquement à « terminé » après la facture et l’expédition. Désormais, après correction, le statut de la commande passe automatiquement à « terminé » une fois la commande facturée et expédiée.

_ACP2E-3947 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/2a252ae6)_

#### [Cloud]Code prêt à l’emploi Magento - Problème de configuration du modèle d’e-mail

Avant la correction, lors de l’utilisation de l’envoi asynchrone d’e-mails, les e-mails d’expédition étaient incohérents avec la commande du magasin. Désormais, après le correctif, la commande par e-mail d’expédition de magasin appropriée est livrée.

_ACP2E-3998 - [contribution du code GitHub](https://github.com/magento/magento2/commit/462ede94)_

#### Annuler les redirections de facture vers 404

L&#39;annulation de la facture effectuée avec le type Not Capture ne mène plus à la page 404.

_ACP2E-4001 - [contribution du code GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Problème lié aux commandes mises à jour avec des options configurables à l’aide de l’API REST

Conservez les options de produit existantes sur les articles de commande client lors de la mise à jour d’une commande via les points d’entrée de l’API REST.

_ACP2E-4061 - [contribution du code GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Ventes asynchrones par insertion d’ID limitée à 100 entrées par exécution cron

Amélioration du traitement de l’insertion asynchrone de la grille de ventes. Une exécution cron insère désormais toutes les lignes en attente par lots, au lieu d’une stricte exécution de 100 lignes.

_ACP2E-4360 - [contribution du code GitHub](https://github.com/magento/magento2/commit/31258bf6)_

#### Message d’erreur « Le produit portant l’ID « 1 » n’existe pas. » est consigné de manière répétée dans exception.log

Avant la correction, des erreurs critiques étaient consignées lorsque des produits supprimés étaient rencontrés dans la section Derniers articles commandés. Après le correctif, les commerçants peuvent configurer s’ils souhaitent consigner ou ignorer les produits supprimés via le paramètre `skipDeletedProductLogging` dans di.xml. Par défaut, le comportement reste inchangé pour des raisons de rétrocompatibilité, mais les commerçants peuvent définir le paramètre sur `true` pour ignorer silencieusement les produits supprimés et empêcher le bruit des logs.

_ACP2E-4366 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/61c96348)_

#### Double taxe sur le deuxième remboursement d&#39;avoir

Correction d&#39;un calcul de taxe incorrect dans les avoirs lors de la création d&#39;un remboursement partiel à partir d&#39;une facture après la création d&#39;un avoir précédent à partir de la page de vue de commande.

_ACP2E-4384 - [contribution du code GitHub](https://github.com/magento/magento2/commit/61c96348)_

### Commande, Tarifs

#### L’administrateur affiche un symbole de devise incorrect lors de la création du retour

Dans une configuration multi-site avec différentes devises (EUR/USD/GBP), la page de sélection de produit de retour dans l’administration affiche désormais le symbole de devise correct. Auparavant, il affichait le symbole de devise par défaut.

_ACP2E-3658 - [contribution du code GitHub](https://github.com/magento/magento2/commit/df92debe)_

### Commande, Retours

#### Erreur lors de la création d&#39;un avoir pour remboursement hors ligne

Correction d&#39;un problème en raison duquel la création d&#39;un avoir échouait pour les produits groupés avec le paramètre Prix dynamique = Non. Les avoirs peuvent maintenant être créés sans erreur.

_ACP2E-4157 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/45cbf9b6)_

### Autres outils de développement

#### [Problème ] conseil de type incorrect pour le membre protégé $_urlHelper

Le système corrige désormais le mauvais type hint avec le bon, qui est également utilisé dans le constructeur

_AC-10716 - [Problème GitHub](https://github.com/magento/magento2/issues/32503) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/32496)_

#### [Problème] Nettoyage du code inutilisé.

Le système supprime désormais le code inutilisé concernant les importations inutilisées.

_AC-10980 - [Problème GitHub](https://github.com/magento/magento2/issues/38424) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/33499)_

#### Échec d’accessibilité de Lighthouse

Le système réussit maintenant avec un score d’accessibilité de 100

_AC-12783 - [Problème GitHub](https://github.com/magento/magento2/issues/39054) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39164)_

#### Désactiver la configuration de storefront captcha tout en chargeant les fichiers js captcha

Le système ne charge plus les fichiers captcha js lorsque nous avons désactivé captcha
pour storefront

_AC-14267 - [Problème GitHub](https://github.com/magento/magento2/issues/32987) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39154)_

#### [Problème] Accessibilité : les rôles WAI-ARIA s’imbriquent mal dans le menu

Le système génère désormais l’accessibilité lighthouse sans que les rôles WAI-ARIA ne s’imbriquent mal dans l’erreur de menu et le rapport doit être vert

_AC-15082 - [Problème GitHub](https://github.com/magento/magento2/issues/40045) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38617)_

#### Erreur de console dans l’aperçu d’e-mail de l’administrateur Magento

Le système ne renvoie aucune erreur de console lors de la prévisualisation du modèle d’e-mail

_AC-9245 - [Problème GitHub](https://github.com/magento/magento2/issues/37820) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37933)_

### Paiement / Modes de paiement

#### Le message Paylater ne s’affiche pas dans le storefront lors de la configuration dans le serveur principal

Correction d’un problème en raison duquel le message PayPal Pay Later n’était pas affiché sur les pages Accueil et Panier malgré sa configuration en arrière-plan. Le rendu de la bannière a échoué lorsque le pays de l’acheteur était nul pour les invités ou les clients sans adresse par défaut. Après la correction, le message Payer plus tard s’affiche correctement sur le storefront.

_AC-12335 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/528af81a)_

### Paiements

#### [Problème] Correction de la capture de factures hors ligne (404)

Il corrige l’erreur de page 404 lors de la capture de factures pour les modes de paiement hors ligne par l’administrateur Magento

_AC-13336 - [Problème GitHub](https://github.com/magento/magento2/issues/39298) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39297)_

#### Des adresses IP inconnues de PayPal abusent du processeur IP de l&#39;application

Le gestionnaire d’adresses IP ignore désormais les types d’adresses IP non pris en charge ou inconnus. Au lieu de renvoyer une erreur 500, il consigne le problème et poursuit le traitement sans interruption.

_ACP2E-4049 - [contribution du code GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Échec du jeton de carte enregistré PayflowPro lors du paiement

Les identifiants de transaction PayPal PayFlow Pro (PNREF) peuvent désormais être utilisés dans les transactions de référence pendant une période fixe de 12 mois. Une fois expirée, la carte enregistrée ne s’affiche plus et doit être ajoutée à nouveau. Auparavant, la validité était déterminée par la date d’expiration de la carte de paiement utilisée dans la transaction initiale.

_ACP2E-4064 - [contribution du code GitHub](https://github.com/magento/magento2/commit/52f46328)_

#### Problème de carte voûtée lors de la commande sur l’administrateur

Le fait de passer une commande avec une carte de crédit stockée dans un site web avec une configuration d’action de paiement différente n’entraîne plus d’erreur ou un type de transaction incorrect

_ACP2E-4270 - [contribution du code GitHub](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### Les 4 derniers chiffres de la carte enregistrée [Cloud] PayflowPro (coffre) ne s’affichent pas dans l’ordre

Les informations de carte sont désormais correctement conservées et affichées lors de l&#39;utilisation de cartes enregistrées avec l&#39;action de paiement Ventes, correspondant au comportement lors de l&#39;utilisation de l&#39;action de paiement Autorisation pour PayflowPro.

_ACP2E-4346 - [contribution du code GitHub](https://github.com/magento/magento2/commit/0a3b7032)_

### Performances

#### [Problème] Mettre à jour Store.php

Cette requête d’extraction améliore les performances en ignorant la résolution actuelle du magasin.

_AC-14791 - [Problème GitHub](https://github.com/magento/magento2/issues/39949) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38717)_

#### [Problème] Mettre à jour utilise le contrôle de cache non modifiable pour le site statique

Cette requête d’extraction ajoute une amélioration des performances en ne validant pas le contenu statique sur chaque chargement de page jusqu’à ce que et sauf si son contenu a été modifié.

_AC-15171 - [Problème GitHub](https://github.com/magento/magento2/issues/39486) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39484)_

#### [Problème ] mettez en cache les résultats des appels isCacheable pour améliorer les performances

Cette requête de mise en cache ajoute la mise en cache pour la méthode isCacheable() , ce qui entraîne le processus de rendu de disposition pour réduire les contrôles redondants et améliorer les performances globales de rendu des pages.

_AC-16054 - [Problème GitHub](https://github.com/magento/magento2/issues/40156) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40112)_

#### [Problème ] Amélioration mineure des performances du traitement asynchrone des grilles de commandes

Ce PR introduit une optimisation des performances pour le traitement de la grille de commande asynchrone de Magento en remplaçant la recherche transitoire last_updated_at basée sur le cache par un indicateur persistant soutenu par la base de données stocké dans la table des indicateurs. Cela permet de s’assurer que le système conserve systématiquement la dernière date et l’heure traitées même après les vidages du cache ou les déploiements, évitant ainsi les analyses de table complète inutiles sur les jeux de données de commande client volumineux. Par conséquent, les mises à jour asynchrones de la grille deviennent plus efficaces et plus prévisibles, en particulier sur les magasins à volume élevé où l’activité des commandes est fréquente.

_AC-16109 - [Problème GitHub](https://github.com/magento/magento2/issues/40282) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40271)_

#### [CLOUD] Impossible d’ajouter des produits aux catégories

Amélioration des performances lors de l’ajout d’un produit à une catégorie via le marchandiseur visuel.

_ACP2E-3946 - [Contribution du code GitHub](https://github.com/magento/inventory/commit/29653b1d)_

#### Problème de performance de nettoyage du journal des modifications après ACP2E-3995

Après le correctif, la tâche cron indexer_clean_all_changelogs nettoie entièrement les journaux des modifications, en maintenant le traitement par lots en place.

_ACP2E-4211 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/ee918f0d)_

#### [CLOUD] Le cache Fastly ne fonctionne pas après la mise à niveau vers la version 2.4.8

Correction d’un problème où les pages pouvant être mises en cache n’étaient pas correctement stockées ou diffusées à partir du cache Fastly, ce qui entraînait un comportement de mise en cache incohérent et une réduction des performances.

_ACP2E-4324 - [contribution du code GitHub](https://github.com/magento/magento2/commit/2687b487)_

#### Découvrez les raisons de la création accrue de clés de lecture et de clés de cache

Avant le correctif, les clés de cache utilisées pour les métadonnées de stockage distant n’expiraient pas. Désormais, après le correctif, vous pouvez définir une TTL pour ces clés de cache par injection de dépendance.

_ACP2E-4345 - [contribution du code GitHub](https://github.com/magento/magento2/commit/0a3b7032)_

### Tarification

#### Le prix est toujours de 0 pour les articles groupés sans prix dynamique dans l’API REST de commande

L’API REST Order renvoie désormais des prix corrects pour les éléments de bundle de produits sans prix dynamique.
Auparavant, lors de l’exportation de commandes via l’API REST, le prix des articles groupés sans tarification dynamique était toujours renvoyé en tant que 0, au lieu du prix réel affiché sur la page du bundle.
AC-11925

_AC-11925 - [Problème GitHub](https://github.com/magento/magento2/issues/38687) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/7da46f52)_

#### Portée incorrecte affectée aux attributs de prix lors de la création

Correction d’un problème en raison duquel les attributs de prix nouvellement créés étaient incorrectement affectés à la portée Vue du magasin, quelle que soit la configuration ; après la correction, la portée des attributs s’aligne désormais par défaut sur le paramètre Portée du prix du catalogue (global ou site web).

_AC-14945 - [Problème GitHub](https://github.com/magento/magento2/issues/39986) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/8670a2b4)_

#### Le produit est enregistré même lorsque la date de début du prix spécial est postérieure à la date de fin à l&#39;aide d&#39;une action en masse

Correction d’un problème en raison duquel les produits pouvaient être enregistrés avec une période de prix spéciaux non valide sans validation.
Désormais, un message d’erreur s’affiche : « Assurez-vous que la date de fin est postérieure ou identique à la date de début. »

_AC-15252 - [Problème GitHub](https://github.com/magento/magento2/issues/40113) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Le prix normal n’est pas visible, même si un prix spécial est appliqué.

Correction d’un problème où le prix normal n’était pas affiché lorsqu’un prix spécial était appliqué. Le prix normal apparaît désormais correctement avec le prix spécial comme prévu.

_ACP2E-4100 - [contribution du code GitHub](https://github.com/magento/magento2/commit/47721be6)_

### Produit

#### Produit configurable avec un comportement incorrect en front-end

Correction d’un problème en raison duquel les produits configurables affichaient un comportement frontal incorrect lorsqu’un attribut d’échantillon de couleur était inclus, ce qui entraînait l’affichage incorrect des prix, de la disposition des listes déroulantes et des indicateurs de champ obligatoires.
Désormais, les produits configurables s’affichent correctement avec un prix correct, des listes déroulantes alignées et un comportement d’interface utilisateur attendu.

_AC-1014 - [Problème GitHub](https://github.com/magento/magento2/issues/14296) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/ef666cd9)_

#### Erreur de correspondance de chaîne d’assertion de prix lorsque le produit configurable est affecté au stock de test et au site web de test avec l’option d’affichage des produits en rupture de stock activée

Mise à jour du test d’échec pour s’aligner sur le comportement de tarification réel pour les produits configurables lorsque tous les produits enfants ont le même prix.
L’assertion valide désormais correctement le prix affiché, empêchant les échecs de test erronés sans affecter la fonctionnalité.

_AC-10843 - [Contribution du code GitHub](https://github.com/magento/inventory/commit/1ccc786b)_

#### Le libellé « Aussi bas que » reste affiché pour un produit configurable pour le cas de test AC-6158

Produits configurables mis en œuvre et vérifiés (P1-P7) avec des variations et des affectations de catégories respectives. Affichage correct des prix de storefront et comportement de l&#39;étiquette « Aussi bas que » pour les produits de la catégorie C.

_AC-10847 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Remise en pourcentage sur le prix de niveau et la règle de prix de catalogue calculée sur le prix d’origine sans les options sélectionnées.

Les remises en pourcentage sur le prix de niveau et les règles de prix de catalogue incluent désormais des options personnalisées sélectionnées.
Auparavant, les remises en pourcentage étaient calculées sur le prix initial du produit sans tenir compte des options personnalisées sélectionnées, ce qui entraînait des prix finaux incorrects.
AC-12004

_AC-12004 - [Problème GitHub](https://github.com/magento/magento2/issues/38750)_

#### [Problème] la validation de l’évaluation ne fonctionne pas, le sélecteur de l’évaluation de révision est modifié

Correction d’un problème en raison duquel la validation de la note de révision n’était pas déclenchée en raison d’un sélecteur modifié. Auparavant, les avis pouvaient être enregistrés sans sélectionner d’évaluation. Après la correction, la validation fonctionne correctement et empêche d’enregistrer une révision à moins qu’une évaluation ne soit sélectionnée.

_AC-12686 - [Problème GitHub](https://github.com/magento/magento2/issues/33424) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/528af81a)_

#### Magento 2.4.7 minQuantité de commande de produit manquante autorisée

Le système fonctionne correctement et la source de la page affiche correctement la quantité minimale du produit

_AC-12909 - [Problème GitHub](https://github.com/magento/magento2/issues/39142) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39480)_

#### Collection de produits - addMediaGalleryData appelle getSize lorsque la collection peut ou va être chargée (peut utiliser count pour éviter une requête de base de données supplémentaire)

Cette requête PR réduit l’appel de requête supplémentaire à l’aide de count() si la collection de produits est déjà chargée lors de l’appel de Product Graphql avec le champ media_gallery inclus.

_AC-13055 - [Problème GitHub](https://github.com/magento/magento2/issues/39111) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39681)_

#### Gestion des SKU non valide pour les produits liés dans Magento

Correction d’un problème en raison duquel les produits avec le SKU « 0 » ne pouvaient pas être liés en tant qu’articles associés, de vente incitative ou de vente croisée en raison d’une validation de SKU non valide. La mise à jour garantit que ces produits peuvent être liés avec succès, ce qui permet au produit d’être enregistré sans erreur.

_AC-13311 - [Problème GitHub](https://github.com/magento/magento2/issues/39329) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a8cf637b)_

#### Problème lié à la grille Options personnalisables sur la page produit du panneau d’administration

Le système fonctionne comme prévu lorsque nous créons des options personnalisables avec une liste déroulante de type .

_AC-14003 - [Problème GitHub](https://github.com/magento/magento2/issues/39640) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39694)_

#### Erreur de page de produit Admin lorsque tous les attributs de produit sont définis sur la portée globale

Correction d’un problème en raison duquel la page de modification du produit d’administration affichait une erreur lorsque tous les attributs de produit étaient définis sur la portée globale. L’erreur est due à une requête de base de données vide, ce qui rend la page inutilisable. Après le correctif, la page produit s’affiche correctement et les produits peuvent être créés sans problème.

_AC-14011 - [Problème GitHub](https://github.com/magento/magento2/issues/39646)_

#### [2.4.8] Aucun rappel trouvé pour la tâche cron catalog_product_alert

Adobe Commerce empêche désormais correctement la planification des tâches cron catalog_product_alert erronées après le changement du nom de la tâche cron d’alerte de produit en product_alert. Auparavant, dans Adobe Commerce 2.4.8, la configuration de Magasins > Configuration > Catalogue > Catalogue > Paramètres d’exécution des alertes de produit entraînait la création d’une entrée cron catalog_product_alert dans core_config_data, et lorsque cron s’exécutait, l’erreur Magento_Cron.CRITICAL : Exception : aucun rappel n’a été trouvé pour la tâche cron catalog_product_alert même si les tâches product_alert valides s’exécutaient correctement.

_AC-14494 - [Problème GitHub](https://github.com/magento/magento2/issues/39800) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### [Comparaison de produits] La liste de comparaison sera inutilisable.

Correction d’un problème en raison duquel la liste de comparaison devenait inutilisable lorsque le même produit était ajouté à partir de différentes vues de magasin. Après le correctif, la liste de comparaison se charge correctement et affiche les éléments en fonction du magasin spécifique.

_AC-14885 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/8670a2b4)_

#### Échec De La Journalisation Supplémentaire Lors De La Demande D’Un Produit Via Le Référentiel

Amélioration des messages d’erreur pour ProductRepository::get et getById lorsqu’un SKU ou un ID est introuvable.
Auparavant, les exceptions ne fournissaient aucun contexte sur le SKU ou l’ID à l’origine de l’erreur.
Désormais, le message d’exception inclut l’ID ou le SKU manquant, ce qui contribue au débogage et à l’amélioration de l’expérience du développeur.
Cette modification n’affecte aucun comportement fonctionnel de l’API.

_AC-15199 - [Problème GitHub](https://github.com/magento/magento2/issues/40090) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/1b1baf1d)_

#### L’erreur « Aucun jeu d’attributs » rompt la page

Correction d’un problème en raison duquel la saisie d’un identifiant de jeu d’attributs non valide dans l’URL provoquait une erreur fatale ; le système affiche désormais un message d’erreur correct indiquant que le jeu d’attributs n’existe pas, au lieu d’interrompre la page.

_AC-15753 - [Problème GitHub](https://github.com/magento/magento2/issues/40213) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a06a4a57)_

#### Remboursement avec remise de remboursement de qté toujours négative

Correction d&#39;un problème en raison duquel la création d&#39;un avoir avec une quantité négative remboursait incorrectement le montant de la remise.
Désormais, les remises ne sont pas remboursées pour les quantités négatives et la quantité remboursée est correctement définie sur zéro.

_AC-9424 - [Problème GitHub](https://github.com/magento/magento2/issues/37917) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/ef666cd9)_

#### La requête lente est exécutée lorsque le widget de produit est inclus via le générateur de page.

La requête pour la création de widgets de produit, y compris les SKU de produit, est optimisée.

_ACP2E-3449 - [contribution du code GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### Les images du produit ne sont pas redimensionnées lorsqu’elles sont ajoutées en tant que produit configurable

Auparavant, les images ajoutées par le biais des configurations dans le panneau d’administration ne respectaient pas la limite de taille de chargement maximale, ce qui pouvait entraîner des incohérences et des problèmes de gestion. Désormais, un correctif a été implémenté pour s’assurer que les images sont automatiquement redimensionnées lors du chargement afin de respecter la limite de taille maximale, ce qui simplifie le processus et maintient les normes système.

_ACP2E-3504 - [contribution du code GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### Tous les éléments des listes de comparaison des autres clients sont affectés au client après s’être connecté via l’administrateur

Auparavant, lorsqu’un administrateur utilisait la fonctionnalité « Connexion en tant que client » sur le serveur principal, les produits de la liste de comparaison d’un client précédemment connecté étaient incorrectement affectés au client dont l’identité est actuellement empruntée.  Une fois la correction effectuée, la liste de comparaison se charge correctement pour le client connecté approprié.

_ACP2E-3818 - [contribution du code GitHub](https://github.com/magento/magento2/commit/462ede94)_

#### L’Enregistrement Du Catalogue Partagé [B2B] Renvoie Une Erreur De Fonctionnalité Obsolète

L’administrateur peut annuler l’affectation des produits du catalogue partagé.
L’annulation précédente de l’affectation de produits avec un grand nombre de SKU de produit longs du catalogue partagé entraînait une erreur

_ACP2E-4097 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/ab891304)_

#### Les performances de génération du plan de site [Cloud] se dégradent considérablement

La génération de plans de site pour les produits avec des images ne connaît plus de ralentissement exponentiel. Auparavant, la génération de plans de site pour les magasins dont l’inclusion d’images était activée entraînait des temps de traitement longs.

_ACP2E-4153 - [contribution du code GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

### Produit, taxe

#### La taxe sur les produits fixes (FPT) ne s’affiche pas séparément avec les produits configurables

Correction d’un problème en raison duquel la taxe sur les produits fixes (FPT) ne s’affichait pas séparément pour les produits configurables après la sélection d’une option. Désormais, la répartition FPT s’affiche correctement sur les pages de liste de produits et de détails, correspondant au format d’affichage des produits simples.

_AC-13171 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/b5e99d20)_

### Promotion

#### La règle de prix de panier Buy X Get Y ajoute une remise incorrecte alors qu&#39;une autre règle a déjà été appliquée

Correction d’un problème en raison duquel la règle de prix de panier Buy X Get Y calculait des remises en utilisant le prix du produit d’origine même après qu’une autre règle l’ait déjà réduit. La mise à jour garantit que la deuxième règle applique désormais la remise au prix ajusté, ce qui entraîne des remises totales précises lorsque plusieurs promotions sont actives.

_AC-12325 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/8670a2b4)_

#### Erreur lors de l’obtention des remises sur article de commande appliquées_à pour la commande client via la demande client GraphQl.

Auparavant, lorsque des remises appliquées_à pour une commande client via une demande de client GraphQl, une erreur de serveur interne était observée, qui est désormais corrigée et des données de commande client appropriées avec une remise appliquée sont récupérées

_AC-14888 - [Problème GitHub](https://github.com/magento/magento2/issues/39963) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/fe72c407)_

#### Erreur lors de l’obtention du code de bon d’article de commande pour la commande client via la demande client GraphQl

Correction d’un problème en raison duquel la récupération de commandes avec des détails de coupon via GraphQL renvoyait une erreur de serveur interne.
Désormais, la requête s’exécute correctement et renvoie les informations correctes sur le coupon dans la réponse.

_AC-14889 - [Problème GitHub](https://github.com/magento/magento2/issues/39962) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/fe72c407)_

#### [Cloud][experienceleague] Règle de prix de catalogue non appliquée

Avant, les règles de prix de catalogue fixes ne s’appliquaient pas lorsque `special_price` était défini uniquement au niveau du site web (et non au niveau de « Toutes les vues de la boutique »). Après la correction, les règles de prix de catalogue s’appliquent désormais correctement lorsque la `special_price` est définie au niveau du site web en vérifiant d’abord le magasin par défaut du site web.

_ACP2E-4372 - [contribution du code GitHub](https://github.com/magento/magento2/commit/61c96348)_

### SEO

#### DynamicStorage.findProductRewriteByRequestPath() ne dispose pas du filtrage entity_type, ce qui fait que les pages CMS sont traitées comme des produits dans les URL de catégorie

Correction d’un problème en raison duquel DynamicStorage ne filtrait pas par type_entité, ce qui entraînait un traitement incorrect des pages CMS en tant que produits dans les URL de catégorie ; les URL incorrectes renvoient désormais correctement un 404 au lieu de diffuser du contenu CMS.

_AC-14991 - [Problème GitHub](https://github.com/magento/magento2/issues/39996) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/64823f95)_

#### L’activation du chemin de catégorie dans les URL de produit interrompt le sélecteur de magasin de plusieurs manières

Correction d’un problème en raison duquel l’activation des chemins de catégorie dans les URL de produit entraînait l’échec du sélecteur de magasin. Le changement de magasin résout désormais correctement les URL de produit entre les vues de magasin sans rediriger vers la page d’accueil ni renvoyer d’erreurs.

_AC-15110 - [Problème GitHub](https://github.com/magento/magento2/issues/40037) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a7ef6300)_

#### Clé de tableau non définie dans ProductRepository getById

Le problème se produisait lorsque ProductRepository::getById() était appelé avec un ID non valide tel que 123abc, ce qui entraînait une erreur de type « Clé de tableau non définie ».
Après le correctif dans Magento 2.4.9-alpha3, ces requêtes renvoient désormais correctement une page 404 au lieu de générer une exception.
Le contrôle qualité a confirmé que les identifiants étaient valides et incorrects, et aucun autre problème n’a été observé.

_AC-15345 - [Problème GitHub](https://github.com/magento/magento2/issues/40146) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### Le produit de comparaison de Storefront crée une erreur d’optimisation du moteur de recherche Google - Les liens ne peuvent pas être analysés.

Correction d’un problème d’optimisation du moteur de recherche (SEO) en raison duquel le lien storefront « Comparer les produits » n’était pas analysable par les moteurs de recherche en raison d’un attribut href manquant ou lié de manière incorrecte. La mise à jour garantit que le lien contient désormais une URL valide et analysable, ce qui améliore la visibilité du site et permet de passer les audits d’optimisation du moteur de recherche Google.

_AC-15547 - [Problème GitHub](https://github.com/magento/magento2/issues/40185) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/c95ed7d7)_

#### Mettre à jour la clé_URL du produit via l’API REST ne génère pas de réécriture d’URL 301

Lors de la mise à jour de la clé URL du produit via l’API REST, avec le paramètre « Créer une redirection permanente pour les URL en cas de modification de la clé URL » défini sur Oui, les réécritures d’URL de produit sont créées pour rediriger l’ancienne URL vers une nouvelle.

_ACP2E-3900 - [contribution du code GitHub](https://github.com/magento/magento2/commit/462ede94)_

#### La génération du plan de site [Cloud] ne se termine jamais

Avant le correctif, la génération du plan de site ne pouvait pas se terminer correctement si le catalogue contenait plus d’un million de produits. Après le correctif, la génération du plan de site se terminera avec une allocation de mémoire plus faible et avec jusqu’à un million de produits par magasin.

_ACP2E-3902 - [contribution du code GitHub](https://github.com/magento/magento2/commit/52f46328)_

#### Le sélecteur de boutique [Cloud] ne fonctionne pas de EN à FR pour la page de FAQ

Correction d’un problème en raison duquel le changement d’affichage des magasins redirigeait les utilisateurs vers la page d’accueil au lieu de la page CMS traduite correspondante. Le sélecteur de magasin recherche désormais les réécritures d’URL dans le magasin cible afin de garantir une redirection correcte (par exemple, la page FAQ en anglais → la page FAQ en français).

_ACP2E-4112 - [Problème GitHub](https://adobe-ent.crm.dynamics.com/main.aspx?appid=f2e74f34-7119-ea11-a811-000d3a5936c5&forceUCI=1&pagetype=entityrecord&etn=incident&id=3e1df344-8a69-f011-bec3-6045bd04f475)_

#### [Cloud] Désactiver l’ancienne génération de plan de site

Une nouvelle option de configuration est désormais disponible pour basculer entre le processus standard de génération de plan de site et un mode par lots nouvellement implémenté. Cette amélioration offre davantage de flexibilité et d’évolutivité dans les workflows de création de plans de site.

_ACP2E-4132 - [contribution du code GitHub](https://github.com/magento/magento2/commit/45cbf9b6)_

#### Les requêtes suspectes génèrent des exceptions dans le fichier exception.log.

Correction d’un problème où les requêtes d’URL malveillantes ou malformées provoquaient des erreurs de classement de base de données et remplissaient les journaux d’exceptions.
Auparavant, lorsque des requêtes suspectes contenant des encodages de caractères non valides ou des caractères non pris en charge étaient reçues, le système tentait de les décoder et de les traiter, ce qui entraînait des conflits de classement MySQL.

_ACP2E-4328 - [contribution du code GitHub](https://github.com/magento/magento2/commit/2687b487)_

### Ventes

#### Lorsque le message Cadeau est activé au niveau de la commande, mais que l’utilisateur ne saisit aucune donnée et passe une commande, les champs Nom de l’expéditeur et Nom de l’destinataire dans l’interface d’administration indiquent le prénom et le nom du client.

Correction d’un problème en raison duquel les champs expéditeur et destinataire de messages cadeau étaient automatiquement renseignés avec les noms de clients même si aucun message cadeau n’était saisi ; les champs restent désormais vides sauf si l’utilisateur fournit les détails.

_AC-15140 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a8cf637b)_

### Rechercher

#### « Confirmer le renvoi du formulaire » dans la recherche catalogue avec « Mémoriser la pagination de catégorie »

Le fait de revenir d’une page produit à la page Résultats de la recherche catalogue après avoir modifié les paramètres de la barre d’outils ne déclenche plus la boîte de dialogue « Confirmer la réenvoi du formulaire » lorsque l’option « Mémoriser la pagination de catégorie » est activée.
Auparavant, les utilisateurs rencontraient une erreur de navigateur ou un avertissement à propos du renvoi du formulaire lors du retour à la page des résultats de recherche après avoir modifié les paramètres de la barre d’outils, tels que l’ordre de tri.

_ACP2E-4208 - [contribution du code GitHub](https://github.com/magento/magento2/commit/e885088b)_

#### Le champ de recherche agrégée « _search » n’est plus utilisé dans la requête

Désormais, la recherche en texte intégral renvoie les produits correspondants si la condition minimale doit correspondre est remplie collectivement pour tous les champs pouvant faire l’objet d’une recherche, plutôt que d’exiger que la condition soit remplie par un seul champ.

_ACP2E-4285 - [contribution du code GitHub](https://github.com/magento/magento2/commit/cbca0396)_

### Sécurité

#### Erreur de serveur interne

Magento ajoute désormais avec succès des produits au panier d’un client lors de l’utilisation du point d’entrée REST asynchrone POST /rest/default/async/V1/carts/mine/items. Auparavant, cette demande asynchrone d’« ajout au panier » entraînait une erreur de serveur interne, et Magento consignait l’erreur suivante : Erreur : appel à une fonction membre setFinalPrice() sur null dans app/code/Magento/Quote/Model/Quote/Item/AbstractItem.php:162.

_AC-16344 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/8670a2b4)_

#### JS groupés/fusionnés ne faisant pas partie des hachages SRI

Avant la correction, le lot généré ou les fichiers fusionnés n’étaient pas ajoutés à la liste des hachages SRI. Désormais, les fichiers sont correctement ajoutés aux hachages SRI.

_ACP2E-3854 - [contribution du code GitHub](https://github.com/magento/magento2/commit/4ca73607)_

#### [CLOUD] problème d’autorisation en écriture dans Newrelic

Avant la correction, les journaux étaient encombrés d’exceptions. Après l’application du correctif, les journaux sont désormais propres et exempts d’exceptions.

_ACP2E-4296 - [contribution du code GitHub](https://github.com/magento/magento2/commit/61c96348)_

### Expédition

#### Qté incorrecte à expédier après quelques avoirs

Correction d&#39;un problème en raison duquel la valeur Qté à expédier était incorrectement calculée après plusieurs avoirs, ce qui autorisait l&#39;expédition d&#39;articles remboursés.
Désormais, le système met à jour avec précision la quantité livrable restante en fonction des articles expédiés et remboursés, ce qui empêche les expéditions non valides.

_AC-1479 - [Problème GitHub](https://github.com/magento/magento2/issues/34289) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/913bf1a6)_

#### Problème de performances potentiel lors du chargement des méthodes d’expédition

Optimisation du processus de chargement des méthodes d’expédition en veillant à ce que seuls les transporteurs actifs soient chargés sur demande. Auparavant, les usines pour toutes les méthodes d’expédition étaient initialisées, ce qui entraînait des frais de performance inutiles. Le correctif améliore l’efficacité en chargeant de manière conditionnelle uniquement les transporteurs maritimes actifs, ce qui réduit le temps de chargement et l’utilisation des ressources.

_AC-15415 - [Problème GitHub](https://github.com/magento/magento2/issues/40153) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/cc0ec250)_

#### [Problème ] la destination commerciale ne doit pas être traitée comme une destination résidentielle.

Correction d’un problème dans l’intégration de l’expédition UPS REST en raison duquel les destinations commerciales étaient incorrectement traitées comme des destinations résidentielles. ResidentialAddressIndicator est désormais inclus dans la demande de tarif UPS uniquement pour les adresses résidentielles, ce qui empêche les frais résidentiels involontaires et garantit des tarifs d&#39;expédition commerciale précis.

_AC-16285 - [Problème GitHub](https://github.com/magento/magento2/issues/40314) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40307)_

#### Exception lors de la création de l&#39;étiquette d&#39;expédition UPS

Correction de l’avertissement : conversion de tableau en chaîne lors de la création de l’étiquette d’expédition UPS

_ACP2E-3676 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

#### [QUANS] - Le module principal Magento_Fedex vérifie-t-il la validité d’un jeton actif avant d’envoyer une demande pour en obtenir un nouveau ?

Adobe Commerce n’effectue plus de nombreuses requêtes au service d’API FedEx pour le jeton d’accès. Auparavant, même si le jeton d’accès était toujours valide, Adobe Commerce envoyait toujours de nouvelles requêtes à l’API FedEx, ce qui provoquait un problème de limitation de débit.

_ACP2E-3930 - [contribution du code GitHub](https://github.com/magento/magento2/commit/4ca73607)_

### Évaluation et prévisualisation

#### Le prix du produit dans le panier affecté par la règle de prix de catalogue ne change pas lorsque la règle est ajustée par la mise à jour de l’évaluation

Correction d’un problème en raison duquel les prix des produits du panier n’étaient pas entièrement mis à jour après avoir modifié une règle de prix de catalogue par le biais d’une mise à jour d’évaluation. Auparavant, le prix mis à jour s’affichait uniquement dans la section de résumé, tandis que le bloc de panier central affichait l’ancienne valeur. Désormais, la règle révisée met correctement à jour le prix du produit sur l’ensemble du panier.

_AC-15304 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/913bf1a6)_

#### Lorsque la mise à jour planifiée pour la catégorie est supprimée, le nombre d’enfants n’est pas diminué pour la catégorie parent

Correction d’un problème en raison duquel la suppression d’une mise à jour planifiée pour une catégorie ne réduisait pas le nombre d’enfants de la catégorie parente, en s’assurant que le nombre se mettait correctement à jour lorsque les mises à jour planifiées ou les sous-catégories étaient supprimées.

_AC-15670 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/ef666cd9)_

#### Lors de la modification de la mise à jour planifiée pour les catégories, les enfants sont ajoutés à la catégorie parent

Correction d’un problème en raison duquel la modification d’une mise à jour planifiée existante pour une sous-catégorie augmentait incorrectement le nombre d’enfants pour les catégories parents dans la base de données. Le problème entraînait des données de hiérarchie de catégories inexactes après l’enregistrement des mises à jour. Après la correction, le nombre d’enfants reste correct et n’augmente plus de manière inattendue.

_AC-16239 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/8670a2b4)_

#### L’aperçu d’une mise à jour planifiée ouvre la première vue de magasin par ordre alphabétique au lieu de la vue de magasin qui vous intéresse

Avant la correction, l’aperçu d’une mise à jour planifiée s’ouvrait dans la première vue de magasin par ordre alphabétique au lieu de la vue de magasin affectée.
Après la correction, l’aperçu s’ouvre désormais correctement dans la vue de magasin affectée à la mise à jour de l’évaluation des blocs CMS.

_ACP2E-3671 - [contribution du code GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

#### Impossible de prévisualiser la mise à jour de produit planifiée avec les autorisations de catégorie activées

Avant la correction, un produit futur à activer n’était pas affiché en mode Aperçu. Désormais, il s’affiche même si le statut actuel est désactivé.

_ACP2E-3786 - [contribution du code GitHub](https://github.com/magento/magento2/commit/7accebfa)_

#### Validation manquante pour le champ du montant de remise de la règle de prix du catalogue

Auparavant, le champ discount_amount de la mise à jour du planning d&#39;évaluation n&#39;était pas validé correctement avec les règles de validation actuelles. Cependant, après application du correctif, le champ discount_amount sera validé de manière appropriée.

_ACP2E-3867 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/462ede94)_

#### Regrouper des produits avec des mises à jour planifiées supprime l’option de regroupement d’éléments de l’action d’enregistrement du produit

La suppression des options de bundle de produits ou des produits associés dans la mise à jour planifiée n’affecte plus les options de bundle d’origine et les produits associés, et vice versa. La suppression des options de production groupées dans le produit d’origine et leur remplacement par d’autres options après la planification d’une mise à jour n’entraînent plus la suppression des options nouvellement ajoutées

_ACP2E-4212 - [contribution du code GitHub](https://github.com/magento/magento2/commit/ab891304)_

#### Impossible de naviguer entre les sites web dans l’aperçu de la planification de mise à jour

Avant cette correction, l’aperçu de la mise à jour planifiée était interrompu lors de la tentative de prévisualisation du contenu pour les magasins avec des domaines personnalisés. Après ce correctif, les domaines de magasin personnalisés peuvent être prévisualisés en l’état et navigués dans le cadre de prévisualisation. Le correctif couvre les produits, les catégories, les pages CMS et les blocs CMS, et prend en charge les liens de navigation à l’aide de balises de balisage `{{store url}}`, comme indiqué dans [Variables Adobe Commerce et balises de balisage](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/variables/markup-tags).

_ACP2E-4308 - [contribution du code GitHub](https://github.com/magento/magento2/commit/0a3b7032)_

### Taxe

#### Mauvais total de commande, l&#39;arrondi n&#39;est pas appliqué au calcul du prix.

Le système est désormais correctement géré lors du calcul du montant price_after_discount, discount_amount et taxes.
total réel de la commande

_AC-11389 - [Problème GitHub](https://github.com/magento/magento2/issues/38455) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39687)_

#### [Problème] Correction : La valeur base_weee_tax_applied_row_amnt des éléments d&#39;avoir est incorrecte

Correction du calcul de l&#39;avoir en utilisant le paramètre approprié pour base_weee_tax_applied_row_amnt, en veillant à ce que la valeur de taxe reflète uniquement la quantité remboursée. Auparavant, le montant de la ligne utilisait incorrectement la valeur de commande complète au lieu du montant partiel de l&#39;avoir.

_AC-12049 - [Problème GitHub](https://github.com/magento/magento2/issues/38765) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/3b5ac075)_

#### Les articles du mini-panier affichent les prix en devises sans conversion

Le mini-panier convertit désormais correctement les devises et affiche le montant exact en fonction des taux de conversion configurés.

_ACP2E-4364 - [contribution du code GitHub](https://github.com/magento/magento2/commit/1c547060)_

### Framework de test

#### [Problème] Supprimez une balise &lt;gravité> dupliquée du test MFTF AdminSetUpWatermarkForSwatchImageTest

Le système n’inclut désormais qu’une seule balise de gravité dans l’AdminSetUpWatermarkForSwatchImageTest, ce qui améliore la clarté et la cohérence du code. Auparavant, ce test contenait deux balises de gravité identiques, ce qui était inutile et pouvait prêter à confusion.

_AC-11873 - [Problème GitHub](https://github.com/magento/magento2/issues/38504) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/31862)_

#### [Problème ] ignorer lib/internal/Magento/Framework/App/Test/Unit/_files/app/etc/en...

Le système ignore désormais le fichier « env.php » qui est généré lors de l’exécution de tests unitaires, ce qui garantit que le statut Git reste correct après l’exécution des tests. Auparavant, l’exécution de tests unitaires générait un nouveau fichier « env.php », ce qui entraînait l’affichage d’un nouveau fichier dans le statut Git et donnait l’impression qu’il était sale.

_AC-13293 - [Problème GitHub](https://github.com/magento/magento2/issues/39304) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37631)_

#### [Problème] Correction du problème de test d’intégration avec l’intercepteur

Le système identifie et gère désormais correctement le fichier \Magento\TestFramework\App\Config\Interceptor dans le test d’intégration, en veillant à ce que le test puisse accéder aux données nécessaires même s’il existe un plug-in sur la classe . Auparavant, le système ne tenait pas compte de la possibilité que \Magento\TestFramework\App\Config soit un \Magento\TestFramework\App\Config\Interceptor, ce qui entraînait une erreur lors de la tentative d’accès à la propriété $data.

_AC-13305 - [Problème GitHub](https://github.com/magento/magento2/issues/39324) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37187)_

#### [Problème] MFTF : envoi d&#39;un e-mail à un formulaire d&#39;ami avec captcha activé

Le cas de test traite de la fonctionnalité du formulaire « Envoyer à un ami » lorsque CAPTCHA est activé, en s’assurant que le processus d’envoi du formulaire fonctionne correctement avec des valeurs CAPTCHA incorrectes et correctes.

_AC-13492 - [Problème GitHub](https://github.com/magento/magento2/issues/39462) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/32830)_

#### Échec des chemins d’accès d’installation codés en dur dans les versions du compositeur

_AC-16488_

#### [Problème ] magento/magento2# : mutation GraphQl. Couverture de test supplémentaire pour les paramètres storeConfig du client.

Le système ajoute désormais la couverture de test supplémentaire pour les prochaines options storeConfig du client :
required_character_classes_number
minimum_password_length

_AC-9370 - [Problème GitHub](https://github.com/magento/magento2/issues/37915) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/28761)_

#### Défaillances des tests unitaires spécifiques à l’environnement dans AC 2.4.7-p3

Ce problème corrige les échecs de test unitaire qui ne se reproduisent pas sur toutes les versions et tous les environnements. Auparavant, certains tests unitaires ont échoué en raison de versions de bibliothèque différentes ou d’une fonctionnalité manquante ajoutée dans une version ultérieure.

_ACP2E-3712 - [contribution du code GitHub](https://github.com/magento/magento2/commit/9ad7d277)_

### Framework de l’interface utilisateur

#### [Problème] Supprimer les variables dupliquées d’un ou de plusieurs fichiers

Le système supprime désormais les variables dupliquées de moins de fichiers, ce qui garantit un code plus propre et plus efficace. Auparavant, ces variables dupliquées étaient présentes dans les fichiers less, ce qui entraînait une redondance inutile du code.

_AC-11743 - [Problème GitHub](https://github.com/magento/magento2/issues/31154) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/31150)_

#### WYSIWYG est vide dans les lignes dynamiques

Les champs WYSIWYG des lignes dynamiques sont désormais correctement initialisés et remplis.
Auparavant, les champs WYSIWYG des lignes dynamiques (comme dans les formulaires de configuration de la conception) pouvaient sembler vides ou perdre leur contenu après certaines actions, nécessitant une intervention manuelle pour restaurer les données.
AC-12336

_AC-12336 - [Problème GitHub](https://github.com/magento/magento2/issues/38893) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

#### [Problème] Correction de la faute de frappe de type MIME

Le système gère et corrige correctement le type MIME et la faute de frappe pour l’image gif

_AC-8001 - [Problème GitHub](https://github.com/magento/magento2/issues/36899) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/36669)_

#### [Problème] Supprimer la balise `@author` interdite de `Magento_Backend`

Cette requête d’extraction supprime `@author` balise de la base de code

_AC-8814 - [Problème GitHub](https://github.com/magento/magento2/issues/37522) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/36976)_

#### [Problème] Évitez l&#39;accès direct à la liste des avis Ajax

Le système gère correctement et évite l&#39;accès direct à la liste des avis Ajax

_AC-9381 - [Problème GitHub](https://github.com/magento/magento2/issues/37920) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/33876)_

#### Connexion/déconnexion de l’en-tête sans mise à jour dans la configuration multi-magasin avec des cookies partagés

L’en-tête de connexion est mis à jour correctement lors de la déconnexion conformément aux paramètres de configuration. customer-data.js utilise un cookie pour stocker la valeur « image-customer-login » si les comptes clients sont partagés globalement. Le stockage local sera utilisé dans le cas contraire.

_ACP2E-4149 - [contribution du code GitHub](https://github.com/magento/magento2/commit/e885088b)_

#### [Mobile] Fotorama peut ouvrir le panier Mini dans l’action de fermeture de la visionneuse d’images

Correction du problème lié à Fotorama. Auparavant, un panier s’ouvrait lors de l’action de fermeture de la visionneuse d’images

_ACP2E-4231 - [contribution du code GitHub](https://github.com/magento/magento2/commit/e885088b)_

#### Les fichiers js fusionnés ne sont pas correctement générés sur les projets avec de nombreux magasins.

La fusion des fichiers JavaScript fonctionne désormais correctement lorsque plusieurs magasins sont configurés.
Auparavant, les fichiers ne fusionnaient parfois pas correctement dans les configurations multi-magasin, ce qui entraînait des résultats incomplets ou incohérents.

_ACP2E-4246 - [contribution du code GitHub](https://github.com/magento/magento2/commit/ab891304)_

### Mises à niveau - Outil de compatibilité de mise à niveau

#### Fonctionnalité obsolète : création de la propriété dynamique Magento\Framework\Acl::$_roleRegistry

Les erreurs de fonctionnalité obsolètes n’empêchent plus l’accès au panneau d’administration après la mise à niveau.
Auparavant, après la mise à niveau vers Magento 2.4.6, toute tentative d’accès au panneau d’administration pouvait entraîner l’erreur suivante :
« Fonctionnalité obsolète : la création de la propriété dynamique Magento\Framework\Acl::$_roleRegistry est obsolète dans vendor/magento/framework/Session/SessionManager.php à la ligne 186 »
Cela empêchait les administrateurs de se connecter.
AC-12343

_AC-12343 - [Problème GitHub](https://github.com/magento/magento2/issues/37469)_
