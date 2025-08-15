---
source-git-commit: 0d5eeb691281d7c62aa64a9d8cd042f18504a67f
workflow-type: tm+mt
source-wordcount: '6370'
ht-degree: 0%

---
# Glossaire Adobe Commerce

## A

### au-dessus du pli

_adjectif_

Dans une fenêtre de navigateur, contenu immédiatement visible après le chargement d’une page web et avant qu’un utilisateur ne la fasse défiler vers le bas de la page.
Lors de la conception de votre disposition, utilisez des formats flexibles pour afficher au mieux les produits, fonctionnalités, ventes, notifications, options prioritaires, etc. dans cette zone.

Avec les appareils mobiles et les tablettes, la zone au-dessus du pli diffère considérablement, en particulier en ce qui concerne la taille et les dimensions de l&#39;écran et l&#39;orientation lors du visionnage (portrait vs paysage).
L’utilisation de thèmes et de tests réactifs peut vous aider à trouver le bon dosage de contenu et de mise en page.

_Attributs de terme :_

* _Champ : conception_

### branche active

_nom_

Une branche ou un environnement actif est connecté à une instance déployée ou en cours d’exécution avec un accès aux services.
Lorsque vous désactivez cette option, la connexion aux services et à l’instance en cours d’exécution est supprimée, mais le code est conservé.
Cela devient une branche Git ordinaire.

_Attributs de terme :_

* _Champ : cloud_

### adaptateur

_nom_

Classe qui permet à deux systèmes incompatibles de fonctionner ensemble sans modifier le code source des systèmes.
Par exemple, des adaptateurs de base de données, des adaptateurs de cache, des adaptateurs de système de fichiers, des adaptateurs de bibliothèques de post-processeurs et d&#39;autres types d&#39;adaptateurs informatiques.

_Attributs de terme :_

* _Champ : programmation_

### admin

_nom_

Dans le logiciel, un rôle d’utilisateur disposant de droits d’administrateur complets permet de gérer toutes les fonctionnalités.
Dans Adobe Commerce, les utilisateurs administrateurs disposent d’autorisations complètes et d’un accès à toutes les fonctionnalités et options d’Admin.
Ils peuvent également créer des utilisateurs et des rôles.

En savoir plus : [Ajout d’utilisateurs](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-users-all.html?lang=fr)

_Attributs de terme :_

* _Champ : logiciel de commerce_
* _Synonymes : administrateur, super utilisateur_
* _Termes associés : administrateur de commerce_

### Zone d’administration

_nom_

Back-office protégé par mot de passe de votre magasin où les commandes, le catalogue, le contenu et les configurations sont gérés.
Les utilisateurs accèdent à la zone d’administration pour gérer la boutique, notamment les produits, les commandes, les envois, le contenu CMS, la conception de la vitrine, les informations client, etc.
Les utilisateurs administrateurs disposent d’un rôle associé avec des autorisations qui contrôle l’accès aux fonctionnalités, options et capacités.

En savoir plus : [Guide de l’utilisateur Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html?lang=fr)

_Attributs de terme :_

* _Champ : logiciel de commerce_
* _Synonymes : administrateur, panneau d’administration, serveur principal, interface d’administration, interface utilisateur d’administration_
* _Termes associés : admin_

### Variables ADMIN

_nom_

Les variables ADMIN sont des variables d’environnement de projet qui remplacent les paramètres de configuration permettant au compte utilisateur administrateur d’accéder à l’interface utilisateur d’administration.

En savoir plus : [variables ADMIN](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html?lang=fr)

_Attributs de terme :_

* _Champ : administrateur, cloud_

### adminhtml

_nom_

Nom de la zone interne attribué à l’administrateur.

En savoir plus : [Guide de l’utilisateur Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html?lang=fr)

_Attributs de terme :_

* _Champ : logiciel de commerce_
* _Termes associés : domaine, administrateur de commerce_

### zone

_nom_

« Zone » est un terme abstrait désignant la portée d’une application Magento.
Les zones sont des composants logiques qui organisent le code pour un traitement des demandes optimisé.
Les zones réduisent la demande de mémoire des objets de configuration accessibles à partir du storefront et rationalisent les appels aux services web en chargeant uniquement le code dépendant requis.
Chaque zone peut contenir un code complètement différent pour traiter les URL et les requêtes.

Les domaines d’Adobe Commerce sont les suivants :

* Admin (adminhtml)
* Storefront
* REST d’API web (webapi_rest)

_Attributs de terme :_

* _Champ : logiciel de commerce_
* _Termes associés : composant Commerce, storefront_

### attribut

_nom_

Caractéristique ou propriété d’un produit qui décrit certains aspects du produit.
Les utilisateurs d’Adobe Commerce peuvent créer des attributs personnalisés à ajouter au jeu d’attributs par défaut ou à un jeu d’attributs personnalisé.
Créez ces attributs via Admin ou par programmation.
Exemples : couleur, taille, poids, prix, âge, sexe, etc.

Les attributs personnalisés sont un type d’attribut Entity-Attribute-Value (EAV).

Pour les intégrations telles que le canal des annonces d’achats Google et Amazon Sales Channel, vous mappez les attributs Commerce aux attributs du tiers pour afficher et vendre correctement les produits et les annonces.

En savoir plus : [EAV et extension_attributes](https://developer.adobe.com/commerce/php/development/components/attributes/)

_Attributs de terme :_

* _Champ : logiciel de commerce, produit_
* _Synonymes : attribut de produit, attribut personnalisé_
* _Termes associés : attribut d’extension_

### groupe d’attributs

_nom_

Regroupement logique d’attributs dans un jeu d’attributs.

_Attributs de terme :_

* _Champ : logiciel de commerce_
* _Termes associés : attribut_

### jeu d’attributs

_nom_

Ensemble de groupes d’attributs personnalisés pour un produit spécifique.
Exemple : un jeu d’attributs de t-shirt peut inclure la couleur, la taille, le sexe et la marque.

_Attributs de terme :_

* _Champ : logiciel de commerce, produit_
* _Termes associés : attribut_

### coût moyen des stocks

_nom_

Prix du produit, moins les coupons ou les remises, plus le fret et les taxes applicables.
La moyenne est déterminée en ajoutant le coût de début des stocks chaque mois, plus le coût de fin des stocks pour le dernier mois de la période.

_Attributs de terme :_

* _Champ : produit, prix, stock_

## B

### devise de base

_nom_

Devise principale utilisée par vue de magasin pour tous les paiements en ligne.
Les magasins peuvent accepter des devises de plus de 200 pays dans le monde.
Le storefront fournit un sélecteur de devise pour plusieurs devises acceptées pour un pays ou un paramètre régional spécifique.
Les symboles de devise apparaissent dans les prix des produits et les documents de vente tels que les commandes et les factures.
Vous pouvez personnaliser les symboles de devise selon vos besoins et définir l&#39;affichage du prix séparément pour chaque magasin ou vue.

En savoir plus : [Devise](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency.html?lang=fr)

_Attributs de terme :_

* _Champ : tarification_

### traitement par lots

_nom_

Pour effectuer une tâche ou modifier plusieurs éléments en même temps, sans répétition manuelle.

_Attributs de terme :_

* _Champ : programmation_
* _Synonymes : opérations en bloc_

### bloquer

_nom_

Unité de sortie de page qui rend un contenu distinctif (un élément d’information, un élément d’interface utilisateur) tout ce qui est visuellement tangible pour l’utilisateur final.
Les [blocs](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/blocks/blocks.html?lang=fr) sont implémentés et fournis par les modules.
Les blocs utilisent des modèles pour générer HTML.
Parmi les exemples de blocs, citons une liste de catégories, un mini panier, des balises de produit et une liste de produits.

Les [blocs dynamiques](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/dynamic-blocks/dynamic-blocks.html?lang=fr) fournissent du contenu en fonction d’une logique, telle que des règles de prix.

Page Builder développe l’interactivité et la création de [blocs](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/block.html?lang=fr) et [blocs dynamiques](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/dynamic-block.html?lang=fr).

_Attributs de terme :_

* _Champ : logiciel de commerce_
* _Synonymes : blocs dynamiques_
* _Termes associés : bloc cms, bloc statique, conteneur, disposition_

### marque

_substantif, verbe_

Identité unique qui définit un produit ou groupe de produits particulier par le fabricant ou Designer.
Il s’agit notamment des noms de marques pour les vêtements, les appareils ménagers, les articles de luxe, etc.
Votre société peut également être la marque, vendant des produits sous plusieurs marques en fonction de l’entité professionnelle, du public cible, etc.

Utilisez des attributs personnalisés pour enregistrer les informations de marque des produits.

Certaines extensions et intégrations peuvent utiliser ou nécessiter une marque pour vos produits, tels que le canal des annonces Google Shopping et Amazon Sales Channel.

_Attributs de terme :_

* _Champ : entreprise_

### brique et mortier

_adjectif_

Une entreprise de vente au détail ayant un emplacement physique permanent, par opposition aux entreprises qui fonctionnent virtuellement ou uniquement par Internet.

Pour [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/sources/sources-manage.html?lang=fr) et [Order Management](#oms), ce magasin est une source pour le suivi des quantités de produits, des commandes d’expédition et la prise en charge du retrait en magasin.

_Attributs de terme :_

* _Champ : entreprise, inventaire_

### opérations en bloc

_nom_

Les opérations en bloc sont des actions qui sont effectuées à grande échelle.
Exemples de tâches d&#39;opérations en masse : importation ou exportation d&#39;articles, modification des prix en masse et affectation de produits à un entrepôt.

En savoir plus : [Opérations en bloc DevDocs](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)

_Attributs de terme :_

* _Champ : programmation_

### produit groupé

_nom_

Permet aux clients d’assembler un produit personnalisable « créer le leur » à partir de diverses options et configurations.
Chaque élément du lot est un produit simple ou virtuel distinct.

En savoir plus : [Produits configurables](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-configurable.html?lang=fr)

_Attributs de terme :_

* _Champ : logiciel de commerce, produit_
* _Termes connexes : produit simple, produit virtuel, types de produits_

### extension groupée

_nom_

Le code qui étend ou personnalise le comportement d’Adobe Commerce est considéré comme une extension groupée.
Il peut inclure des modules, des thèmes et des modules linguistiques.

_Attributs de terme :_

* _Champ : extension groupée, extension_
* _Synonymes : extension_
* _Termes associés : extension, extension groupée avec un fournisseur_

## C

### mettre en cache le serveur principal

_nom_

Stocke les enregistrements du cache dans un système principal à deux niveaux dans le framework par défaut d’Envoi.
Un cache de premier niveau est rapide (par exemple, un serveur principal APC ou Memcached), mais il est limité et ne prend pas en charge le balisage et le regroupement des entrées du cache.
Un cache de deuxième niveau, par exemple un système de fichiers ou un serveur principal Redis, est plus lent, mais prend en charge le balisage et le regroupement.

_Attributs de terme :_

* _Champ : programmation_
* _Termes associés : serveur principal_

### cache frontal

_nom_

Indique le type de données stocké dans le serveur principal du cache.

_Attributs de terme :_

* _Champ : programmation_
* _Termes associés : frontend_

### type de cache

_nom_

Un cache stocke les données afin que les prochains appels pour ces données se chargent plus rapidement.

Adobe Commerce comprend les types suivants :
* Configuration
* Mises en page
* Bloquer la sortie HTML
* Données de collections
* Données de réflexion
* Opérations DDL de la base de données
* Configuration compilée
* Types et attributs EAV
* Notification du client
* Configuration des intégrations
* Configuration de l’API d’intégration
* Cache de page (le plus connu)
* Configuration des services web
* Traductions
* Règle cible
* Cache du produit Google
* Vertex

D’autres types peuvent être créés et définis.

_Attributs de terme :_

* _Champ : programmation_

### capturer

_verbe_

Processus de conversion d&#39;un montant de commande autorisé en une transaction facturable.
Les transactions ne peuvent pas être saisies tant qu&#39;elles ne sont pas autorisées, et les autorisations ne peuvent pas être saisies tant que les biens ou services n&#39;ont pas été expédiés.

_Attributs de terme :_

* _Champ : entreprise_
* _Termes associés : autorisation, statut de la commande_

### détenteur de carte

_nom_

Personne autorisée par une institution financière à effectuer des achats sur un compte de carte de crédit.

_Attributs de terme :_

* _Champ : entreprise, commande_

### règles du panier

_nom_

Règles de prix appliquées au panier et déclenchant une action en réponse à un ensemble de conditions.
Utilisé pour créer des promotions.

_Attributs de terme :_

* _Domaine : logiciel de commerce, prix, produit_
* _Termes associés : règles de catalogue, panier_

### catalogue

_nom_

Pour les commerçants, le catalogue représente leur inventaire de produits.
Dans l’architecture Adobe Commerce, le catalogue se compose de catégories, de produits et d’attributs de produit.

Chaque magasin Commerce ne comporte qu’un seul catalogue de produits, qui est partagé par toutes les vues du magasin.
Dans une installation multi-magasin, chaque magasin peut avoir un catalogue distinct ou partager le catalogue.
Le catalogue actuel du magasin est déterminé par la catégorie racine par défaut, visible par l’utilisateur dans le volet de navigation supérieur (menu principal) du magasin.
(Le terme « catégorie racine » peut prêter à confusion, car « catégorie racine » n’est pas vraiment une catégorie, mais un conteneur pour le menu, qui se compose de catégories et de sous-catégories.)

Vous pouvez créer autant de catégories racine que vous le souhaitez, mais une seule (la valeur par défaut) peut être utilisée à la fois.

_Attributs de terme :_

* _Domaine : logiciel de commerce, prix, produit_
* _Termes associés : catalogue partagé, règle de catalogue_

### règles de catalogue

_nom_

Règles de prix appliquées à des produits spécifiques et déclenchant une action en réponse à un ensemble de conditions.
Utilisé pour créer des promotions.

_Attributs de terme :_

* _Domaine : logiciel de commerce, prix, produit_
* _Termes associés : règles de panier, catalogue_

### catégorie

_nom_

Groupe de produits ayant quelque chose en commun.
Le menu principal du magasin est organisé en catégories et sous-catégories de produits.

_Attributs de terme :_

* _Champ : logiciel de commerce, produit_

### passage en caisse

_nom_

Processus de collecte des informations de paiement et d’expédition nécessaires pour terminer l’achat d’articles dans le panier.
Une fois que le client a consulté les informations et envoyé la commande, une confirmation par e-mail lui est envoyée.

Le passage en caisse offre de nombreuses options et configurations prêtes à l’emploi et via l’extension.

En savoir plus : [tutoriel de passage en caisse](https://developer.adobe.com/commerce/php/tutorials/frontend/custom-checkout/)

_Attributs de terme :_

* _Champ : entreprise, conception, commande, produit, programmation_

### variables cloud

_nom_

Les variables cloud sont des variables d’environnement spécifiques à Adobe Commerce sur l’infrastructure cloud et utilisent le préfixe **`MAGENTO_CLOUD`** .

En savoir plus : [Variables cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud.html?lang=fr)

_Attributs de terme :_

* _Champ : cloud_

### bloc CMS

_nom_

Variante spéciale de [block](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/blocks/blocks.html?lang=fr) qui ne peut être créée que dans l’administration et ne peut pas être référencée via des fichiers de disposition.

_Attributs de terme :_

* _Champ : logiciel de commerce_
* _Termes associés : bloc, bloc statique_

### données complexes

_nom_

Données associées à plusieurs options de produit.

_Attributs de terme :_

* _Champ : programmation_

### composant

_nom_

Utilisé pour faire référence à un module, un thème ou un package de langue dans Adobe Commerce.

_Attributs de terme :_

* _Champ : logiciel de commerce_
* _Synonymes : composant_
* _Termes associés : composant d’interface utilisateur_

### produit configurable

_nom_

Un produit configurable ressemble à un produit unique avec des listes déroulantes d’options pour chaque variation.
Chaque option est en fait un produit simple distinct avec un SKU unique, ce qui permet d’effectuer le suivi de l’inventaire pour chaque variation de produit.
Pour obtenir un effet similaire, un produit simple peut être utilisé avec des options personnalisées, mais sans la possibilité d’effectuer le suivi de l’inventaire pour chaque variation.
Les produits comportant plusieurs options sont parfois appelés produits composites.

Bien qu’un produit configurable utilise plus de SKU et puisse prendre un peu plus de temps à configurer au début, il peut vous faire gagner du temps à la fin.
Si vous prévoyez faire croître votre entreprise, le type de produit configurable pourrait être un meilleur choix pour un produit à options multiples.

Exemple : T-shirts disponibles en deux couleurs et trois tailles.
Six variantes doivent être créées en tant que produits individuels (chacun ayant son propre SKU).
Ensuite, toutes les variantes sont ajoutées à un produit configurable dont les clients peuvent choisir la taille et la couleur, puis l’ajouter à leur panier.

_Attributs de terme :_

* _Champ : logiciel de commerce, produit_
* _Termes associés : types de produits_

### taux de conversion

_nom_

Pourcentage de visiteurs et visiteuses qui sont convertis en acheteurs.

_Attributs de terme :_

* _Champ : entreprise, commande_

### mise à l’échelle du niveau principal

_nom_

La mise à l’échelle du niveau principal se compose de trois nœuds de service pour le stockage des données, le cache et les services, tels qu’OpenSearch, Elasticsearch, MariaDB et Redis.

_Attributs de terme :_

* _Champ : cloud_

### avoir

_nom_

Document émis par le commerçant à un client pour annuler un solde impayé en raison d&#39;un surcoût, d&#39;une remise ou d&#39;un retour de marchandises.
Le mémo restaure les fonds sur le compte du client.

_Attributs de terme :_

* _Champ : entreprise, commande_

### commentaire de note de crédit

_nom_

Détails sur la raison pour laquelle un montant d&#39;avoir a été crédité au client.

_Attributs de terme :_

* _Champ : entreprise, commande_

### article avoir

_nom_

Article facturé pour lequel un commerçant crée un avoir.

_Attributs de terme :_

* _Champ : entreprise, commande_

### vente croisée

_substantif, adjectif, verbe_

Un produit qui s’affiche à côté du panier.
Lorsque le client accède à la page du panier, ces produits s’affichent sous forme de ventes croisées avec les articles figurant déjà dans le panier.
Ils sont semblables aux achats impulsifs, comme les magazines et les bonbons dans les caisses des épiceries.

_Attributs de terme :_

* _Champ : entreprise, produit_
* _Termes associés : montée en gamme_

### CVM

_nom_

Abréviation de « Méthode de vérification du titulaire de carte ».
Un moyen de vérifier l&#39;identité du client en confirmant un code de sécurité de carte de crédit à 3 ou 4 chiffres avec le processeur de paiement.

_Attributs de terme :_

* _Champ : entreprise, commande_
* _Synonymes : Méthode de vérification du titulaire de carte_
* _Termes associés : code de sécurité_

## D

### schéma de la base de données

_nom_

Structure des données dans une base de données.
Définit l’organisation des données et la manière dont les relations de données sont gouvernées, y compris toutes les contraintes appliquées aux données.
Un module peut contenir des fragments du schéma de base de données si ce module contient des données qui doivent être stockées dans la base de données.

_Attributs de terme :_

* _Champ : programmation_
* _Synonymes : schéma_

### injection de dépendance

_nom_

Modèle de conception logicielle qui permet à une classe de spécifier ses dépendances sans avoir à les construire.
Cette classe délègue la responsabilité d’injecter la dépendance à la classe appelante.
Utilisé pour faciliter les tests.
Pour définir des dépendances pour les classes, modifiez le fichier de configuration di.xml.

_Attributs de terme :_

* _Champ : programmation_

### clé de déploiement

_nom_

Une clé de déploiement est la clé publique SSH de votre projet et permet un accès en lecture seule ou en lecture-écriture (si activé) à un référentiel Git.

En savoir plus : [ Connexions sécurisées ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=fr)

_Attributs de terme :_

* _Champ : cloud_

### double opt-in

_substantif, verbe_

Processus de vérification des e-mails qui oblige les abonnés potentiels à effectuer une deuxième étape qui confirme leur intention de s’abonner.

_Attributs de terme :_

* _Champ : entreprise_

### produit téléchargeable

_nom_

Produit téléchargeable numériquement qui se compose d’un ou de plusieurs fichiers téléchargés, tels qu’un livre numérique, de la musique, des vidéos, une application logicielle ou une mise à jour.
Vous pouvez proposer un album à la vente et vendre chaque chanson individuellement.
Un produit téléchargeable peut fournir une version électronique de votre catalogue de produits.

Les fichiers téléchargeables peuvent résider sur votre serveur ou être fournis sous forme d’URL à tout autre serveur ou réseau de diffusion de contenu.

_Attributs de terme :_

* _Champ : logiciel de commerce, produit_
* _Termes associés : types de produits_

### contenu dynamique

_nom_

Contenu généré par code plutôt que lu à partir d’un modèle statique.
Une fois que le contenu dynamique est initialement rendu lorsqu’un utilisateur visite une page, il est parfois possible de mettre le contenu en cache et de le réutiliser sans avoir à recourir à un autre appel dynamique lors d’une nouvelle visite.

_Attributs de terme :_

* _Champ : conception_
* _Termes associés : php_

### URL de dynamic media

_nom_

Adresse URL générée dynamiquement par le système pour référencer une image ou d’autres médias.
L’adresse renvoie directement aux ressources stockées sur un serveur ou un réseau de diffusion de contenu.
Pour utiliser une URL statique, modifiez le paramètre de configuration.
Cependant, si des URL Dynamic Media sont incluses dans votre catalogue lorsque vous désactivez le paramètre , chaque référence de votre catalogue devient un lien rompu.
Les liens peuvent être restaurés en activant à nouveau les URL Dynamic Media.
L’utilisation d’URL Dynamic Media peut affecter les performances de la recherche catalogue.

Format de code : media url= »path/to/image.jpg »

_Attributs de terme :_

* _Champ : programmation_
* _Termes associés : réseau de diffusion de contenu, URL_

## E

### ensemble d&#39;outils cee

_nom_

Ensemble de scripts et d’outils conçu pour gérer et déployer l’application Commerce. Ce package simplifie de nombreux processus Adobe Commerce sur les infrastructures cloud, notamment le déploiement dans un environnement Docker, la gestion des crons, la vérification de la configuration du projet et l’application de correctifs Adobe.

En savoir plus : [package ece-tools](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview.html?lang=fr)

_Attributs de terme :_

* _Champ : interface en ligne de commande, cloud, déploiement_

### entité

_nom_

Unité ou objet unique dans la programmation.
Contient des attributs ou des paramètres qui peuvent être modifiés.
Par exemple, l’évaluation (où une mise à jour peut modifier des entités telles que des règles de prix, des produits ou des catégories) et les enregistrements de base de données (où les contrats de service incluent des structures de données envoyées et reçues).

_Attributs de terme :_

* _Champ : logiciel de commerce_
* _Termes associés : attribut, règles de panier, règles de catalogue_

### valeur d’attribut d’entité

_nom_

Pour les entités de base de données, modèle de données qui code efficacement les entités.
Stocke l’ID d’entité, le nom d’attribut et la valeur sous la forme d’un triple, ce qui permet de créer de nouveaux noms d’attribut d’entité à tout moment.
Dans le codage, le nombre d’attributs pouvant être utilisés pour décrire des entités peut être mis à l’échelle de manière étendue, mais le nombre qui s’applique à une entité donnée est réduit au minimum.
Ce modèle de données est flexible, mais peut être lent.

En savoir plus : [EAV et extension_attributes](https://developer.adobe.com/commerce/php/development/components/attributes/)

_Attributs de terme :_

* _Champ : programmation_
* _Synonymes : eav_

### contenu permanent

_nom_

Contenu ayant une longue durée de conservation ou contenu pouvant être réutilisé.

_Attributs de terme :_

* _Champ : entreprise_

### extension

_nom_

Code qui étend ou personnalise le comportement d’Adobe Commerce.
Vous pouvez éventuellement regrouper et distribuer une extension sur Commerce Marketplace ou un autre système de distribution d’extensions.
Une extension Commerce peut inclure des modules, des thèmes et des modules linguistiques.

_Attributs de terme :_

* _Champ : logiciel de commerce_
* _Termes associés : composant, module, package_

### attribut d’extension

_nom_

Étendez les fonctionnalités et utilisez souvent des types de données plus complexes que les attributs personnalisés. Ces attributs n’apparaissent pas sur l’interface utilisateur graphique.

En savoir plus : [Ajout d’attributs d’extension à une entité](https://developer.adobe.com/commerce/php/development/components/add-attributes/)

_Attributs de terme :_

* _Champ : logiciel de commerce_
* _Termes associés : attribut, valeur d’attribut d’entité_

## F

### fret à bord

_nom_

Dans le transport maritime international, ce terme signifie que la partie destinataire est responsable des frais d&#39;expédition.
FOB peut être basé sur le lieu d&#39;origine ou de destination, et être désigné comme fret à percevoir ou fret prépayé.

_Attributs de terme :_

* _Champ : entreprise, commande, tarification_
* _Synonymes : fob_

### front-end

_adjectif_

Dans une application client-serveur, il existe le serveur principal et frontal.
Le composant frontal, ou client, est une interface qui permet aux utilisateurs de manipuler le code principal sous-jacent ou d’interagir avec lui.
Le code du serveur principal s’exécute sur un serveur.
Un utilisateur ne peut pas accéder directement au code du serveur principal.
Un utilisateur interagit avec le storefront, qui à son tour utilise le code exécuté sur le serveur Commerce.

Remarque : dans le passé, le storefront était appelé le « front-end » et l’administrateur était appelé le « back-end ». Cette utilisation n’est plus prise en charge.

_Attributs de terme :_

* _Domaine : conception, programmation_
* _Synonymes : côté client_
* _Termes associés : serveur principal, storefront, cache frontal_

### propriétés frontend

_nom_

Propriétés qui déterminent la présentation et le comportement d’un attribut du point de vue du client dans votre boutique.

_Attributs de terme :_

* _Domaine : conception, programmation_

### accomplissement

_nom_

Processus de gestion des expéditions client.

_Attributs de terme :_

* _Champ : entreprise_

## G

### carte-cadeau

_nom_

Une carte prépayée ou un certificat-cadeau qui peut être utilisé pour effectuer des achats dans le magasin.
Chaque carte cadeau se voit attribuer un code unique qui est saisi lors du passage en caisse.
La valeur de la carte cadeau est reflétée dans le solde du compte de carte cadeau.
Il existe trois types de cartes-cadeaux :

* Les cartes-cadeaux « physiques » peuvent être produites à partir de plastique ou de stock de cartes, expédiées au client.
* Les cartes-cadeaux « virtuelles » sont envoyées par courriel.
* Les cartes-cadeaux « combinées » sont une combinaison des deux, expédiées au destinataire sous forme de carte physique et également livrées par e-mail.
Les cartes-cadeaux sont configurables, y compris les options d’éligibilité du produit et de sélection des montants ouverts ou fixes.

Une carte cadeau peut également être échangée par l’administrateur de la boutique à la demande du client lorsque la commande est créée sur le serveur principal.

Les cartes-cadeaux aident également les promotions, car les administrateurs du magasin peuvent créer manuellement les comptes de carte-cadeau dans le serveur principal et envoyer les codes de carte-cadeau au segment de client spécifique.
Les cartes-cadeaux peuvent servir de programme de fidélité ciblé sur les clients les plus actifs qui effectuent de nombreux achats dans la boutique en ligne ou une campagne promotionnelle spécifique pendant les vacances.

_Attributs de terme :_

* _Champ : logiciel de commerce_
* _Termes associés : types de produits_

### marge brute

_nom_

Différence entre le coût et le prix d’un produit.

_Attributs de terme :_

* _Champ : entreprise_

### produit groupé

_nom_

Type de produit comprenant plusieurs produits autonomes similaires, regroupés sur une seule page.
Peut être proposé avec des variations d’un seul produit ou en les regroupant par saison ou thème pour créer un ensemble coordonné.
Chaque produit peut être acheté séparément ou dans le cadre du groupe.

Par exemple, pour un couteau disponible en quatre tailles, les quatre couteaux peuvent tous être affichés dans une page produit groupée.
Les clients peuvent sélectionner les tailles de leur choix et les ajouter au panier à partir de cette page.

_Attributs de terme :_

* _Champ : logiciel de commerce, produit_
* _Termes connexes : produit simple, types de produits_

## H

### poignée

_nom_

En règle générale, une poignée est un moyen de référencer un objet.
Dans Adobe Commerce, les poignées sont utilisées à de nombreux endroits, le plus souvent pour identifier une page.
Pour les descripteurs de page, le nom du descripteur est dérivé de l’URL, puis utilisé pour localiser et charger les fichiers de mise en page de la page référencée.
Par exemple, dans le module Client, il existe un fichier de disposition appelé « view/frontend/layout/checkout_cart_index.xml ».
Ici, « frontend » est le nom de la zone et « checkout_cart_index » est le nom du handle, tous deux dérivés de l’URL.

_Attributs de terme :_

* _Champ : programmation_
* _Synonymes : identificateur de page_

### mise à l&#39;échelle horizontale

_nom_

La mise à l’échelle horizontale (également appelée mise à l’échelle) est le processus d’ajout de nœuds ou de machines supplémentaires à votre infrastructure pour répondre à une demande croissante.

_Attributs de terme :_

* _Champ : cloud_

## I

### interception

_nom_

Processus d’injection d’un nouveau code avant, après ou autour d’une fonction publique existante d’une classe PHP.

Pour intercepter une fonction, un plug-in implémente le code supplémentaire à appeler.
Les plug-ins sont associés aux points d&#39;interception par le fichier de configuration d&#39;injection de dépendance (di.xml).
Si plusieurs plug-ins sont définis sur la même fonction, la configuration d’injection de dépendance définit l’ordre d’appel des plug-ins, ce qui permet d’utiliser plusieurs plug-ins sans conflit.

_Attributs de terme :_

* _Champ : programmation_
* _Termes associés : plug-in_

## L

### mise en page

_nom_

Dans la construction d’une page Commerce, une mise en page est une série de blocs assemblés dans une hiérarchie, représentant la structure de la page.

Les fichiers de mise en page sont axés sur le niveau le plus élevé de la structure de la page (en-tête, pied de page, zone de contenu principale, barre latérale gauche, etc.).
Les fichiers de disposition assemblent ensuite le contenu (blocs) dans ces différentes zones de la page.

_Attributs de terme :_

* _Domaine : conception, logiciel de commerce_
* _Termes associés : instructions de mise en page, bloc_

### instructions de mise en page

_nom_

Balisage dans un fichier de disposition qui décrit les modifications à appliquer à une arborescence d’éléments structurés de blocs, de conteneurs et de composants d’interface utilisateur.
Un seul fichier de disposition peut contenir plusieurs instructions de disposition.
Les instructions de mise en page sont codées au format XML dans des fichiers de mise en page.

_Attributs de terme :_

* _Domaine : conception, programmation_
* _Termes associés : disposition, bloc, conteneur, composant d’interface utilisateur_

### mise à jour de la disposition

_nom_

Utilisé pour les fragments de code ajoutés afin de modifier la disposition XML ou d’importer les instructions de disposition d’un autre fichier.

_Attributs de terme :_

* _Domaine : conception, logiciel de commerce_

### Propriétaire de la licence

_nom_

Le Propriétaire de la licence (également appelé Propriétaire du compte) est la personne désignée dans une organisation commerciale qui gère les paiements et d’autres problèmes professionnels pour le compte d’Adobe Commerce sur l’infrastructure cloud.
Cette personne sert de point de contact avec Adobe.
Une fois qu’une entreprise a acheté un abonnement à l’infrastructure cloud Adobe Commerce, l’accès initial au projet et au code n’est disponible que pour la personne désignée comme propriétaire de la licence.

_Attributs de terme :_

* _Champ : entreprise_

## M

### MAGEID

_nom_

MAGEID est généralement le contact de facturation sur le compte Adobe Commerce (et peut ne pas être le propriétaire du projet d’infrastructure cloud Adobe Commerce).
Pour obtenir le droit d’accès à Adobe Commerce et Adobe Commerce sur les packages d’infrastructure cloud, vous devez utiliser les clés d’accès associées à un MAGEID qui a reçu l’accès à ces packages.

En savoir plus : [Obtenir vos clés d’authentification](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html?lang=fr)

_Attributs de terme :_

* _Champ : logiciel de commerce_

### balisage

_nom_

Dans le marketing et la vente au détail, pourcentage ajouté au coût d’un article pour déterminer le prix de détail.
[Configurez le balisage](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/settings/settings-advanced-custom-options.html?lang=fr) ou markdown, d’un produit au moyen d’options personnalisables pour le produit.

En développement, langage informatique qui contrôle le traitement, la présentation et la mise en forme du texte.
En outre, les balises de balisage sont des fragments de code qui ajoutent des fonctionnalités ou du contenu à une page ou à un bloc CMS.

_Attributs de terme :_

* _Domaine : entreprise, programmation_
* _Synonymes : Markdown_

### environnement principal

_nom_

Sur Adobe Commerce sur les infrastructures cloud, les projets Pro utilisent un environnement PaaS (Platform as a Service) actif appelé maître qui comprend une copie de la base de données et du serveur web de votre environnement de production.

_Attributs de terme :_

* _Champ : cloud_

### compte marchand

_nom_

Compte auprès d’une banque ou d’une institution financière qui permet d’accepter des transactions par carte de crédit.

_Attributs de terme :_

* _Champ : entreprise_

### MFTF

_nom_

MFTF est un [cadre de test fonctionnel](https://developer.adobe.com/commerce/testing/functional-testing-framework/).
Il fournit un cadre de test aux développeurs Commerce et aux ingénieurs en logiciels, tels que les spécialistes de l’assurance qualité, les développeurs PHP et les intégrateurs système.
Les développeurs et le contrôle qualité peuvent écrire des tests pour tenter d’interagir avec les utilisateurs et utilisatrices avec les applications web, vérifier les fonctionnalités et automatiser les tests de régression.

_Attributs de terme :_

* _Domaine : logiciel de commerce, programmation_
* _Termes associés : bloc cms, bloc statique, conteneur, disposition_

### module

_nom_

Code qui modifie ou étend les fonctionnalités fournies par l’application Magento.
Un module est contenu dans une structure de répertoires qui contient des fichiers PHP et XML (configuration, blocs, contrôleurs, assistants, modèles, etc.) associés à une fonctionnalité spécifique pour fournir une collection distincte de fonctionnalités de produit.
L’objectif de chaque module est de fournir des fonctionnalités de produit spécifiques en implémentant de nouvelles fonctionnalités ou en étendant les fonctionnalités d’autres modules.
Chaque module est conçu pour fonctionner indépendamment, de sorte que l’inclusion ou l’exclusion d’un module particulier n’a aucune incidence sur la fonctionnalité des autres modules.

Un module peut également implémenter des widgets, qui sont des éléments de page qui peuvent être personnalisés par les utilisateurs professionnels dans l’administration.

Les modules peuvent être désactivés ou supprimés sans compromettre la cohérence de l’application Magento.
Une exception : lorsque le module dépend d’autres modules, ce qui nécessite de désactiver ou de supprimer les modules dépendants.

_Attributs de terme :_

* _Champ : logiciel de commerce_
* _Termes associés : php, xml, block_

## O

### OMS

_nom_

OMS est l’offre système d’Adobe Order Management.

>[!IMPORTANT]
>
>Adobe Commerce Order Management (OMS) a atteint sa fin de vie et n’est plus pris en charge.

OMS est une solution flexible et abordable pour gérer, vendre et réaliser des stocks à partir de n’importe quel canal de vente.
OMS offre une expérience client transparente, ce qui augmente les ventes tout en réduisant les coûts, et accélère le délai de mise sur le marché.

Les fonctionnalités d’OMS incluent :

* Visibilité mondiale et gestion de l&#39;ensemble des stocks
* Possibilité d&#39;expédier vers et depuis n&#39;importe où
* Un service client plus facile et plus réactif
* Meilleure expérience client et fidélité

En savoir plus : [Site des documents OMS archivés](https://commerce-docs.github.io/oms-documentation-archive/)

_Attributs de terme :_

* _Champ : fonctionnalité, logiciel de commerce, gestion des commandes_
* _Synonymes : gestion des commandes, MOM, système de gestion des commandes, Magento Order Management_
* _Termes associés : gestion des commandes_

### revêtement d&#39;origine

_nom_

Le cloaking d&#39;origine est une fonctionnalité de sécurité qui permet à Adobe Commerce sur les infrastructures cloud de bloquer tout trafic non Fastly pour empêcher les attaques DDoS, vers les infrastructures cloud (origine).

En savoir plus : [Fastly origin cloaking](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/fastly-origin-cloaking-enablement-faq.html?lang=fr)

_Attributs de terme :_

* _Champ : security_
* _Termes associés : pare-feu d’application web_

## P

### Page Builder

_nom_

Page Builder est une extension de Commerce permettant de créer des pages riches en contenu en faisant glisser et en déposant des contrôles préconfigurés pour définir des mises en page personnalisées.
Ces contrôles sont également appelés « types de contenu ».
Les commerçants peuvent concevoir des mises en page et des pages sans expérience de codage.
La prise en charge de l’extension est fournie pour permettre aux développeurs d’étendre Page Builder.

En savoir plus : [Guide de l’utilisateur de Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/introduction.html?lang=fr), [Documentation de développement de Page Builder](https://developer.adobe.com/commerce/frontend-core/page-builder/)

_Attributs de terme :_

* _Domaine : logiciel de commerce, conception_
* _Synonymes : administrateur, panneau d’administration, serveur principal, interface d’administration, interface utilisateur d’administration_
* _Termes associés : admin_

### passerelle de paiement

_nom_

Une passerelle de paiement est un service tiers qui traite de manière transparente les transactions par carte de crédit sans que le client quitte le site du commerçant.

_Attributs de terme :_

* _Champ : entreprise, commande, programmation_

## R

### produit connexe

_nom_

Une sélection de produits présentée comme une incitation à acheter des articles supplémentaires.
Par exemple, si le client consulte la page produit d’un appareil photo, les produits associés peuvent inclure d’autres appareils photo comparables, un boîtier d’appareil photo et un trépied.

_Attributs de terme :_

* _Champ : logiciel de commerce, produit_

## S

### règles de vente

_nom_

Inclut les règles de panier et de catalogue, qui sont utilisées pour fixer le prix d’un produit pour des promotions.

_Attributs de terme :_

* _Champ : logiciel de commerce, produit_
* _Termes associés : règles de panier, règles de catalogue_

### portée

_nom_

Dans Adobe Commerce, la portée décrit l’étendue de la hiérarchie de votre boutique qu’un paramètre peut affecter.
La portée peut s’appliquer aux éléments suivants :

* Global : tous les sites web, boutiques et affichages de boutique
* Site Web : site Web sélectionné et tous les magasins et affichages de magasin qui s&#39;y trouvent.
* Magasin : magasin sélectionné et toutes les vues de magasin situées en dessous
* Vue de magasin : vue de magasin sélectionnée.

Dans la hiérarchie, les paramètres appliqués à un niveau inférieur peuvent remplacer certains paramètres de niveau supérieur.

_Attributs de terme :_

* _Champ : logiciel de commerce_

### contrat de service

_nom_

Un ensemble d&#39;interfaces PHP définies pour un module.
Un contrat de service comprend des interfaces de données, qui préservent l’intégrité des données, et des interfaces de service, qui masquent les détails de logique commerciale aux demandeurs de service tels que les contrôleurs, les services web et d’autres modules.
Les API Web peuvent être liées à des contrats de service via des fichiers de configuration.

_Attributs de terme :_

* _Champ : programmation_
* _Termes associés : php, api web_

### établissement

_nom_

Le règlement intervient lorsque la banque acquéreuse et l&#39;émetteur échangent des fonds et que le produit est déposé sur le compte du commerçant.

_Attributs de terme :_

* _Champ : entreprise_

### Catalogue partagé

_nom_

Une fonctionnalité qui permet aux commerçants de créer un catalogue pouvant servir de catalogue complet ou de sous-ensemble de celui-ci, puis d’attribuer des prix personnalisés pour un ou plusieurs produits.
Les commerçants peuvent ensuite attribuer ce catalogue à une ou plusieurs entreprises.

Par exemple, un commerçant B2B a trois clients qui ont négocié des tarifs spécifiques pour son site de distribution électronique.
Grâce à la fonctionnalité de catalogue partagé, le commerçant dispose des éléments suivants :

* Un catalogue principal
* Un catalogue client 1 (il s’agit peut-être de trois SKU seulement avec de fortes remises sur ceux du catalogue principal).
* Catalogue client 2 (peut être l’ensemble du catalogue avec une réduction de 10 %)
* Catalogue client 3 (quelques dizaines de produits avec des remises sur le catalogue principal allant de 5 % à 60 %).

_Attributs de terme :_

* _Champ : logiciel de commerce, produit_
* _Termes associés : catalogue, b2b_

### expédition

_nom_

Une expédition contient les produits à livrer et génère un enregistrement des produits dans une commande qui ont été expédiés.
Plusieurs expéditions peuvent être associées à une seule commande.

_Attributs de terme :_

* _Champ : entreprise, commande_

### document d&#39;expédition

_nom_

Document qui accompagne une expédition. Le document répertorie les produits et leurs quantités dans le kit de livraison.

_Attributs de terme :_

* _Champ : entreprise, commande_

### transporteur

_nom_

Société qui transporte des packages. Les transporteurs courants comprennent UPS, FedEx, DHL et USPS.

_Attributs de terme :_

* _Champ : entreprise, commande_

### panier

_nom_

Ensemble de produits qu’un client a choisi d’acheter, mais qu’il n’a pas encore achetés.
Fait également référence à une zone d’un site d’e-commerce où ces produits peuvent être trouvés pour examen et passage en caisse.

_Attributs de terme :_

* _Domaine : entreprise, conception, produit, programmation_
* _Synonymes : panier, panier_
* _Termes associés : règles de panier_

### produit simple

_nom_

Type de produit le plus basique : un article physique avec un seul SKU.
Les produits simples ont divers contrôles de prix et d&#39;entrée qui permettent de vendre des variantes du produit.
Les produits simples peuvent être utilisés en association avec des produits groupés, groupés et configurables.
Un produit simple avec des options personnalisées est parfois appelé produit composite.

_Attributs de terme :_

* _Champ : logiciel de commerce, produit_
* _Termes associés : types de produits_

### SKU

_nom_

Abréviation de Stock Keeping Unit.
Numéro ou code attribué à un produit pour identifier le produit, les options, le prix et le fabricant.

_Attributs de terme :_

* _Champ : entreprise, tarification, produit, programmation_
* _Termes associés : catalogue partagé_

### splash page

_nom_

Une page promotionnelle avec un produit ou une publicité ; normalement affichée avant la page d’accueil.

_Attributs de terme :_

* _Champ : conception_

### bloc statique

_nom_

Unité modulaire de contenu pouvant être placée par un utilisateur dans le CMS sur une page pour afficher du texte et des images, ou exécuter des fragments de code.
Les blocs statiques contiennent du contenu modifiable et peuvent servir de pages de destination pour les catégories de produits.
Les widgets peuvent être ajoutés aux blocs statiques pour fournir des fonctionnalités supplémentaires.

_Attributs de terme :_

* _Champ : logiciel de commerce_
* _Termes associés : bloc cms, bloc_

### contenu statique

_nom_

Contenu généré par l’utilisateur (non généré par du code) et qui ne change pas fréquemment.

_Attributs de terme :_

* _Champ : conception_
* _Termes associés : contenu dynamique_

### fichiers statiques

_nom_

Ensemble de ressources, telles que CSS, polices, images et JavaScript, utilisées par un thème.

_Attributs de terme :_

* _Champ : logiciel de commerce_

### magasin

_nom_

Le niveau d’étendue Commerce de « magasin » est le deuxième niveau de la hiérarchie de votre site web, qui se présente comme suit : site web > magasin > affichage du magasin.
Les magasins peuvent être organisés en un ou plusieurs. Chaque magasin peut avoir sa propre catégorie racine et tous partagent des données de catalogue et de client.

Chaque magasin peut avoir plusieurs vues de magasin, qui sont généralement utilisées pour présenter le storefront dans des paramètres régionaux et une langue différents.

_Attributs de terme :_

* _Champ : logiciel de commerce, produit_
* _Termes associés : affichage de la boutique, site web_

### vue magasin

_nom_

Le niveau d’étendue Commerce de la « vue du magasin » fait référence au troisième niveau de la hiérarchie des sites web, des magasins et des vues de magasin.
Les vues de magasin présentent généralement le storefront dans des paramètres régionaux et linguistiques différents.
Pour modifier les affichages de la boutique, utilisez le programme de sélection de boutique dans l’en-tête.

_Attributs de terme :_

* _Champ : logiciel de commerce, produit_
* _Termes associés : boutique, site web_

### storefront

_nom_

Boutique en ligne que les clients découvrent lorsqu’ils visitent votre site Commerce.

_Attributs de terme :_

* _Champ : logiciel de commerce, produit_

## T

### règle fiscale

_nom_

Combinaison d&#39;une classe de taxe de produit, d&#39;une classe de taxe client et d&#39;un taux de taxe. Cette règle définit le calcul de taxe appliqué.

_Attributs de terme :_

* _Champ : entreprise_

### modèle

_nom_

Abréviation de modèle HTML ou de modèle HTML.
Un fichier HTML contient un mélange de balisage HTML et de code PHP pour injecter du contenu dynamique dans HTML.
La plupart des blocs ont au moins un fichier HTML (modèle) qui contient l’HTML statique générée par le bloc.
Dans l’administration, les modèles d’e-mail et de newsletter associent du texte, des images et des variables à des balises HTML afin de produire du contenu personnalisé envoyé par le système.

_Attributs de terme :_

* _Champ : logiciel de commerce_
* _Termes associés : bloc_

### thème

_nom_

Contient des graphiques et des informations d’aspect.
Personnalise l’aspect et la fonctionnalité du magasin.
Adobe Commerce peut envoyer des thèmes dans des packages (de compositeur).
Mais les thèmes peuvent être placés sous application / conception, qui n&#39;est pas fourni dans un package.
Les packages sont l’unité de téléchargement du compositeur et, via Commerce Marketplace, les utilisateurs de Commerce peuvent télécharger CE ou EE sous la forme d’une série de packages, où les packages contiennent des modules, des thèmes ou des modules linguistiques.

_Attributs de terme :_

* _Champ : logiciel de commerce_

## U

### Composant de l’interface utilisateur

_nom_

Balise conçue pour le logiciel Adobe Commerce permettant un rendu de l’interface utilisateur (IU) plus simple et plus flexible.
Les objectifs du système de composants de l’interface utilisateur sont les suivants :

* Simplification des fichiers XML de gestion de disposition
* Déplacement des éléments de l’interface utilisateur d’administration d’HTML+JavaScript vers un système de widgets personnalisés « JavaScript pur »
* Activation de la création de composants d’IU plus complexes à partir de composants plus petits
* Pré-rendu des données pour les composants de l’interface utilisateur au format JSON, liaison étroite aux objets de données du serveur principal
* Utilisation d’AJAX pour mettre à jour les données de composant
* Présentation d’un nouveau DSL pour créer les éléments ci-dessus

En savoir plus : [guide des composants de l’interface utilisateur](https://developer.adobe.com/commerce/frontend-core/ui-components/), [Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/introduction.html?lang=fr)

_Attributs de terme :_

* _Champ : programmation_
* _Termes associés : JavaScript, mise en page, composant, générateur de page_

### VERS LE HAUT

_nom_

[PWA Studio](https://github.com/magento/pwa-studio) utilise [UPWARD](https://developer.adobe.com/commerce/pwa-studio/guides/packages/upward/) en développement.
UPWARD est un acronyme de Unified Progressive Web App Response Definition.
Un fichier de définition UPWARD décrit comment un serveur web diffuse et prend en charge un Progressive Web Application.

Les fichiers de définition UPWARD fournissent des détails sur le comportement du serveur à l’aide d’un langage déclaratif indépendant de la plateforme.
Cela permet à un Progressive Web Application de s’exécuter sur un serveur compatible UPWARD dans n’importe quelle langue et sur n’importe quel tech stack, car l’application ne s’intéresse qu’au comportement du point d’entrée HTTP à partir du serveur UPWARD.

Un serveur UPWARD utilise un fichier de définition pour déterminer le processus ou le service approprié pour une requête provenant d&#39;un shell d&#39;application.
Il décrit comment le serveur doit gérer une requête et créer la réponse pour celle-ci.

Un projet PWA peut inclure un fichier de définition UPWARD pour spécifier ses dépendances de service.

_Attributs de terme :_

* _Domaine : conception, logiciel de commerce, programmation_
* _Synonymes : PWA Studio, Définition De Réponse D’Application Web Progressive Unifiée_
* _Termes associés : pwa_

## V

### Extension groupée fournisseur

_nom_

Le code produit par le fournisseur qui étend ou personnalise le comportement de Commerce et fonctionne comme une extension tierce est considéré comme une extension groupée par fournisseur (VBE).
Les VBE sont minutieusement testés et inclus dans chaque version prise en charge d’Adobe Commerce.
Un VBE peut inclure des modules, des thèmes et des modules linguistiques.

Pour en savoir plus, consultez la [rubrique Extension groupée avec un fournisseur](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/modules/upgrade.html?lang=fr).

_Attributs de terme :_

* _Champ : extension Commerce, extension groupée avec un fournisseur, extension, VBE_
* _Synonymes : extension, VBE_
* _Termes associés : extension, extension groupée_

### mise à l&#39;échelle verticale

_nom_

La mise à l’échelle verticale fait référence à l’augmentation de la puissance de traitement d’un seul serveur ou cluster par l’ajout d’E/S de disque ou de réseau, de processeurs ou de RAM.

_Attributs de terme :_

* _Champ : environnement_

### produit virtuel

_nom_

Représente un produit non physique qui peut être vendu, tel qu’un abonnement, un service, une garantie ou un abonnement.
Les produits virtuels peuvent être vendus individuellement ou inclus dans les types de produits suivants : produit groupé et produit groupé.
Ne nécessite ni expédition ni inventaire.

Le processus de création d’un produit virtuel et d’un produit simple est presque le même.
Cependant, comme un produit virtuel n&#39;est pas expédié, il n&#39;y a pas de champ Poids ou d&#39;option pour inclure une carte cadeau.

_Attributs de terme :_

* _Champ : logiciel de commerce, produit_
* _Termes associés : types de produits_

### type virtuel

_nom_

Les types virtuels sont un moyen d&#39;injecter différentes dépendances dans des classes PHP existantes sans affecter d&#39;autres classes et sans avoir à créer de fichier de classe.
Les types virtuels ne peuvent être référencés que par des remplacements d’argument dans un élément `<type>` dans les fichiers di.xml, jamais dans le code source.
Elles ne peuvent pas être étendues et ne peuvent pas être des références en tant que dépendances dans un constructeur de classes.

_Attributs de terme :_

* _Champ : programmation_
* _Termes associés : php_

## W

### site internet

_nom_

Dans le logiciel Adobe Commerce, niveau le plus élevé de la hiérarchie d’un site web, au-dessus de la vue du magasin et de la vue du magasin.
Vous pouvez avoir plusieurs sites web et chaque site web peut avoir un nom de domaine différent.
Les sites web peuvent être configurés pour partager des données client ou pour ne pas partager de données.

_Attributs de terme :_

* _Domaine : logiciel de commerce, conception, produit_
* _Termes associés : magasin, vue de magasin_

### widget

_nom_

Un [widget](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/widgets/widgets.html?lang=fr) est un fragment de code préparé qui peut être utilisé pour placer des blocs, des liens et du contenu dynamique à des emplacements spécifiques sur les pages de la boutique.
Vous pouvez utiliser des widgets pour créer des pages de destination pour les campagnes marketing, afficher du contenu promotionnel à des emplacements spécifiques dans l’ensemble du magasin.
Les widgets peuvent également être utilisés pour ajouter des éléments interactifs et des blocs d’action pour les systèmes de révision externes, les conversations vidéo, le vote et les formulaires d’abonnement, ou pour fournir des éléments de navigation pour les nuages de balises et les curseurs d’image.

_Attributs de terme :_

* _Domaine : commerce, logiciel commercial, design_
* _Termes associés : bloc_
