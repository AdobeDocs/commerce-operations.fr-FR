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

Dans une fenêtre de navigateur, le contenu qui est immédiatement visible après le chargement d’une page web et avant qu’un utilisateur ne fasse défiler la page vers le bas.
Lors de la conception de votre mise en page, utilisez des formats flexibles pour afficher au mieux les produits, fonctionnalités, ventes, notifications, options prioritaires, etc. prioritaires dans cette zone.

Avec les appareils mobiles et les tablettes, la zone au-dessus du pli diffère considérablement, en particulier en ce qui concerne la taille et les dimensions de l’écran et de l’orientation lors de l’affichage (portrait ou paysage).
L’utilisation de thèmes réactifs et de tests peut aider à trouver la bonne combinaison de contenu et de mise en page.

_Attributs de terme :_

* _Champ : design_

### branche active

_noun_

Une branche ou un environnement actif est un environnement connecté à une instance déployée ou en cours d’exécution ayant accès aux services.
Lorsque vous désactivez , la connexion aux services et à l’instance en cours d’exécution est supprimée, mais le code est conservé.
Ça devient une branche git ordinaire.

_Attributs de terme :_

* _Champ : cloud_

### adapter

_noun_

Une classe qui permet à deux systèmes incompatibles de fonctionner ensemble sans modifier le code source du système.
Par exemple, les adaptateurs de base de données, les adaptateurs de cache, les adaptateurs de système de fichiers, les adaptateurs de bibliothèques de post-processeur et d’autres types d’adaptateurs de calcul.

_Attributs de terme :_

* _Champ : programmation_

### admin

_noun_

Dans le logiciel, un rôle d’utilisateur avec des droits d’administrateur complets pour gérer toutes les fonctionnalités.
Dans Adobe Commerce, les utilisateurs administrateurs disposent d’autorisations complètes et d’un accès à toutes les fonctionnalités, options et fonctionnalités de l’administrateur.
Ils peuvent également créer des utilisateurs et des rôles.

En savoir plus : [Ajout d’utilisateurs](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-users-all.html)

_Attributs de terme :_

* _Champ : logiciel de commerce_
* _Synonymes : administrateur, super-utilisateur_
* _Termes associés : admin commercial_

### Zone d’administration

_noun_

Le back-office protégé par mot de passe de votre magasin où sont gérées les commandes, le catalogue, le contenu et les configurations.
Les utilisateurs accèdent à la zone d’administration pour gérer le magasin, notamment les produits, les commandes, les envois, le contenu CMS, la conception du storefront, les informations sur les clients, etc.
Les utilisateurs administrateurs sont associés à un rôle qui contrôle l’accès aux fonctionnalités, options et fonctionnalités.

En savoir plus : [Guide de l’utilisateur Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html)

_Attributs de terme :_

* _Champ : logiciel de commerce_
* _Synonymes : Admin, panneau d’administration, serveur principal, interface d’administration, interface utilisateur d’administration_
* _Termes associés : admin_

### Variables ADMIN

_noun_

Les variables ADMIN sont des variables d’environnement de projet qui remplacent les paramètres de configuration du compte d’utilisateur administrateur pour accéder à l’interface utilisateur d’administration.

En savoir plus : [Variables ADMIN](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html)

_Attributs de terme :_

* _Champ : admin, cloud_

### adminhtml

_noun_

Nom de la zone interne affectée à l’administrateur.

En savoir plus : [Guide de l’utilisateur Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html)

_Attributs de terme :_

* _Champ : logiciel de commerce_
* _Termes associés : zone, administrateur de commerce_

### area

_noun_

Zone est un terme abstrait de la portée d’une application Magento.
Les zones sont des composants logiques qui organisent le code pour un traitement optimisé des requêtes.
Les zones réduisent les exigences de mémoire des objets de configuration accessibles à partir du storefront et elles rationalisent les appels de service Web en chargeant uniquement le code dépendant requis.
Chaque zone peut contenir un code complètement différent pour traiter les URL et les requêtes.

Les zones d’Adobe Commerce incluent :

* Admin (adminhtml)
* Storefront
* API Web REST (webapi_rest)

_Attributs de terme :_

* _Champ : logiciel de commerce_
* _Termes associés : composant Commerce, storefront_

### attribute

_noun_

Une caractéristique ou une propriété d’un produit qui décrit un aspect du produit.
Les utilisateurs d’Adobe Commerce peuvent créer des attributs personnalisés à ajouter au jeu d’attributs par défaut ou à un jeu d’attributs personnalisé.
Créez ces attributs par le biais de l’administrateur ou par programmation.
Exemples : couleur, taille, poids, prix, âge, sexe, etc.

Les attributs personnalisés sont un type d’attribut Entity-Attribute-Value (EAV) .

Pour les intégrations telles que Google Shopping ads Channel et Amazon Sales Channel, vous mappez les attributs Commerce aux attributs dans le tiers pour afficher et vendre correctement les produits, les publicités display.

En savoir plus : [EAV et extension extension extension_attributes](https://developer.adobe.com/commerce/php/development/components/attributes/)

_Attributs de terme :_

* _Champ : logiciel de commerce, produit_
* _Synonymes : attribut de produit, attribut personnalisé_
* _Termes associés : attribut d’extension_

### groupe d’attributs

_noun_

Regroupement logique d’attributs dans un jeu d’attributs.

_Attributs de terme :_

* _Champ : logiciel de commerce_
* _Termes associés : attribute_

### jeu d’attributs

_noun_

Collection de groupes d’attributs, personnalisée pour un produit spécifique.
Exemple : un jeu d’attributs de T-shirt peut inclure la couleur, la taille, le sexe et la marque.

_Attributs de terme :_

* _Champ : logiciel de commerce, produit_
* _Termes associés : attribute_

### coût d&#39;inventaire moyen

_noun_

Prix du produit, moins les coupons ou les remises, plus le fret et les taxes applicables.
La moyenne est déterminée en ajoutant le coût initial de l’inventaire chaque mois, plus le coût final de l’inventaire pour le dernier mois de la période.

_Attributs de terme :_

* _Champ : produit, prix, inventaire_

## B

### monnaie de base

_noun_

Devise principale utilisée par vue de magasin pour tous les paiements en ligne.
Les magasins peuvent accepter des devises de plus de 200 pays dans le monde.
L’interface de magasin fournit un sélecteur de devise pour plusieurs devises acceptées pour un pays ou des paramètres régionaux spécifiques.
Les symboles de devise apparaissent dans les prix des produits et les documents de vente, tels que les commandes et les factures.
Vous pouvez personnaliser les symboles de devise selon vos besoins et définir l’affichage du prix séparément pour chaque magasin ou affichage.

En savoir plus : [Currency](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency.html)

_Attributs de terme :_

* _Champ : tarification_

### traitement par lots

_noun_

Pour effectuer une tâche ou modifier plusieurs éléments simultanément, sans répétition manuelle.

_Attributs de terme :_

* _Champ : programmation_
* _Synonymes : opérations en masse_

### block

_noun_

Unité de sortie de page qui effectue le rendu d’un contenu distinct (une information, un élément d’interface utilisateur), tout ce qui est visuellement tangible pour l’utilisateur final.
Les [blocs](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/blocks/blocks.html) sont implémentés et fournis par des modules.
Les blocs utilisent des modèles pour générer des HTMLS.
Parmi les exemples de blocs, citons une liste de catégories, un mini panier, des balises de produits et une liste de produits.

[Les blocs dynamiques](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/dynamic-blocks/dynamic-blocks.html) fournissent du contenu basé sur la logique, comme des règles de prix.

Page Builder développe l’interactivité et la création de [blocs](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/block.html) et de [blocs dynamiques](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/dynamic-block.html).

_Attributs de terme :_

* _Champ : logiciel de commerce_
* _Synonymes : blocs dynamiques_
* _Termes associés : bloc cms, bloc statique, conteneur, mise en page_

### marque

_noun, verb_

Identité unique qui définit un produit ou groupe de produits spécifique par le fabricant ou Designer.
Il s’agit de marques de noms pour les vêtements, les appareils, les articles de luxe, etc.
Votre entreprise peut également être la marque, elle vend des produits sous plusieurs marques en fonction de l’unité opérationnelle, de l’audience cible, etc.

Utilisez des attributs personnalisés pour enregistrer les informations sur la marque des produits.

Certaines extensions et intégrations peuvent utiliser ou nécessiter une marque pour vos produits, par exemple Google Shopping ads Channel et Amazon Sales Channel.

_Attributs de terme :_

* _Champ : business_

### brique et mortier

_adjectif_

Une entreprise de vente au détail avec un emplacement physique permanent, par opposition à des entreprises qui fonctionnent virtuellement ou uniquement par Internet.

Pour [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/sources/sources-manage.html) et [Order Management](#oms), ce magasin est une source pour effectuer le suivi des quantités de produits, des commandes d’expédition et de la prise en charge de la récupération en magasin.

_Attributs de terme :_

* _Champ : entreprise, inventaire_

### opérations en bloc

_noun_

Les opérations en bloc sont des actions exécutées à grande échelle.
Parmi les exemples de tâches d’opérations en bloc, citons l’importation ou l’exportation d’articles, la modification des prix à grande échelle et l’affectation de produits à un entrepôt.

En savoir plus : [Opérations en bloc DevDocs](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)

_Attributs de terme :_

* _Champ : programmation_

### produit groupé

_noun_

Permet aux clients d’assembler un produit personnalisable &quot;à partir de leurs propres options et configurations&quot;.
Chaque élément du lot est un produit simple ou virtuel distinct.

En savoir plus : [Produits configurables](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-configurable.html)

_Attributs de terme :_

* _Champ : logiciel de commerce, produit_
* _Termes associés : produit simple, produit virtuel, types de produits_

### extension groupée

_noun_

Le code qui étend ou personnalise le comportement d’Adobe Commerce est considéré comme une extension groupée.
Il peut inclure des modules, des thèmes et des modules de langue.

_Attributs de terme :_

* _Champ : extension groupée, extension_
* _Synonymes : extension_
* _Termes associés : extension, extension groupée fournisseur_

## C

### cache backend

_noun_

Stocke les enregistrements de cache dans un système principal à deux niveaux dans la structure par défaut de Zend.
Un cache de premier niveau est rapide (par exemple, un APC ou un serveur principal Memcached), mais il est limité et ne prend pas en charge le balisage et le regroupement des entrées de cache.
Un cache de second niveau — par exemple, un système de fichiers ou un serveur principal Redis — est plus lent, mais prend en charge le balisage et le regroupement.

_Attributs de terme :_

* _Champ : programmation_
* _Termes associés : backend_

### front de cache

_noun_

Indique le type de données stocké dans le serveur principal du cache.

_Attributs de terme :_

* _Champ : programmation_
* _Termes associés : frontend_

### type de cache

_noun_

Un cache stocke les données afin que les appels futurs pour ces données se chargent plus rapidement.

Adobe Commerce comprend les types suivants :
* Configuration
* Disposition
* Sortie de l’HTML par bloc
* Données de collections
* Données de réflexion
* Opérations DDL de base de données
* Configuration compilée
* Types et attributs d’EAV
* Notification client
* Configuration des intégrations
* Configuration de l’API d’intégration
* Cache de page (le plus connu)
* Configuration des services web
* Traductions
* Règle Target
* Cache de produit Google
* Vertex

D’autres types peuvent être créés et définis.

_Attributs de terme :_

* _Champ : programmation_

### capture

_verb_

Processus de conversion d’un montant de commande autorisé en transaction facturable.
Les transactions ne peuvent pas être capturées tant qu’elles ne sont pas autorisées et les autorisations ne peuvent pas être capturées tant que les biens ou services n’ont pas été expédiés.

_Attributs de terme :_

* _Champ : business_
* _Termes associés : autorisation, état de la commande_

### détenteur de carte

_noun_

Personne qui est autorisée par une institution financière à effectuer des achats sur un compte de carte de crédit.

_Attributs de terme :_

* _Champ : entreprise, commande_

### règles de panier

_noun_

Règles de prix appliquées au panier et déclenchant une action en réponse à un ensemble de conditions.
Utilisé pour créer des promotions.

_Attributs de terme :_

* _Champ : logiciel de commerce, tarification, produit_
* _Termes associés : règles de catalogue, panier_

### catalogue

_noun_

Pour les commerçants, le catalogue représente leur inventaire de produits.
Dans l’architecture Adobe Commerce, le catalogue se compose de catégories, de produits et d’attributs de produit.

Chaque magasin Commerce ne possède qu’un seul catalogue de produits, qui est partagé par toutes les vues de magasin.
Dans une installation multi-magasin, chaque magasin peut avoir un catalogue distinct ou partager le catalogue.
Le catalogue du magasin actuel est déterminé par la catégorie racine par défaut, visible par l’utilisateur dans la navigation supérieure (menu principal) du magasin.
(Le terme &quot;catégorie racine&quot; peut être déroutant, car la &quot;catégorie racine&quot; n’est pas vraiment une catégorie, mais un conteneur pour le menu, qui se compose de catégories et de sous-catégories.)

Vous pouvez créer autant de catégories racine que vous le souhaitez, mais une seule (valeur par défaut) peut être utilisée à la fois.

_Attributs de terme :_

* _Champ : logiciel de commerce, tarification, produit_
* _Termes associés : catalogue partagé, règle de catalogue_

### règles de catalogue

_noun_

Règles de prix appliquées à des produits spécifiques et déclenchant une action en réponse à un ensemble de conditions.
Utilisé pour créer des promotions.

_Attributs de terme :_

* _Champ : logiciel de commerce, tarification, produit_
* _Termes associés : règles de panier, catalogue_

### category

_noun_

Un groupe de produits qui ont quelque chose en commun.
Le menu principal du magasin est organisé en catégories et sous-catégories de produits.

_Attributs de terme :_

* _Champ : logiciel de commerce, produit_

### passage en caisse

_noun_

Processus de collecte des informations de paiement et d’expédition nécessaires pour terminer l’achat d’articles dans le panier.
Une fois que le client a examiné les informations et envoyé la commande, une confirmation par courrier électronique est envoyée au client.

Le passage en caisse comporte de nombreuses options et configurations prêtes à l’emploi et par extension.

En savoir plus : [Tutoriel sur le passage en caisse](https://developer.adobe.com/commerce/php/tutorials/frontend/custom-checkout/)

_Attributs de terme :_

* _Champ : entreprise, conception, commande, produit, programmation_

### variables cloud

_noun_

Les variables cloud sont des variables d’environnement spécifiques à Adobe Commerce sur l’infrastructure cloud et utilisent le préfixe **`MAGENTO_CLOUD`**.

En savoir plus : [Variables cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud.html)

_Attributs de terme :_

* _Champ : cloud_

### Bloc CMS

_noun_

Une variante spéciale de [block](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/blocks/blocks.html) qui ne peut être créée que dans l’administrateur et ne peut pas être référencée par le biais de fichiers de mise en page.

_Attributs de terme :_

* _Champ : logiciel de commerce_
* _Termes associés : block, static block_

### données complexes

_noun_

Données associées à plusieurs options de produit.

_Attributs de terme :_

* _Champ : programmation_

### component

_noun_

Utilisé pour faire référence à un module, un thème ou un module de langue dans Adobe Commerce.

_Attributs de terme :_

* _Champ : logiciel de commerce_
* _Synonymes : composant_
* _Termes associés : composant ui_

### produit configurable

_noun_

Un produit configurable ressemble à un produit unique avec des listes déroulantes d’options pour chaque variante.
Chaque option est en fait un produit simple distinct avec un SKU unique, ce qui permet de suivre l’inventaire de chaque variation de produit.
Pour obtenir un effet similaire, un produit simple peut être utilisé avec des options personnalisées, mais sans possibilité de suivre l’inventaire pour chaque variation.
Les produits avec plusieurs options sont parfois appelés produits composites.

Bien qu’un produit configurable utilise plus de SKU et qu’il puisse prendre un peu plus de temps au départ à configurer, il peut vous faire gagner du temps au bout du compte.
Si vous prévoyez de développer votre entreprise, le type de produit configurable peut être un meilleur choix pour un produit avec plusieurs options.

Exemple : T-shirts disponibles en deux couleurs et trois tailles.
Six variantes doivent être créées sous la forme de produits individuels (chacun ayant son propre SKU).
Ensuite, toutes les variantes sont ajoutées à un produit configurable dans lequel les clients peuvent choisir la taille et la couleur, puis les ajouter à leur panier.

_Attributs de terme :_

* _Champ : logiciel de commerce, produit_
* _Termes associés : types de produits_

### taux de conversion

_noun_

Pourcentage de visiteurs convertis en acheteurs.

_Attributs de terme :_

* _Champ : entreprise, commande_

### échelle de niveau principal

_noun_

La mise à l’échelle de niveau principal comprend trois noeuds de service pour le stockage des données, le cache et les services, tels qu’OpenSearch, Elasticsearch, MariaDB, Redis.

_Attributs de terme :_

* _Champ : cloud_

### note de crédit

_noun_

Document émis par le marchand à un client pour annuler un solde impayé en raison de frais supplémentaires, de rabais ou de retours de marchandises.
Le mémo récupère les fonds sur le compte du client.

_Attributs de terme :_

* _Champ : entreprise, commande_

### commentaire de note de crédit

_noun_

Explique pourquoi un montant de note de crédit a été crédité au client.

_Attributs de terme :_

* _Champ : entreprise, commande_

### élément de note de crédit

_noun_

Article facturé pour lequel un commerçant crée une note de crédit.

_Attributs de terme :_

* _Champ : entreprise, commande_

### vente croisée

_substantif, adjectif, verb_

Produit qui s’affiche en regard du panier.
Lorsqu’un client accède à la page du panier, ces produits sont affichés sous la forme de ventes croisées aux articles déjà présents dans le panier.
Elles sont similaires aux achats impulsifs, comme les magazines et les bonbons dans les caisses enregistreuses des épiceries.

_Attributs de terme :_

* _Champ : entreprise, produit_
* _Termes associés : upsell_

### CVM

_noun_

Abréviation de &quot;Méthode de vérification du détenteur de carte&quot;.
Un moyen de vérifier l’identité du client en confirmant un code de sécurité de carte de crédit à 3 ou 4 chiffres à l’aide du processeur de paiement.

_Attributs de terme :_

* _Champ : entreprise, commande_
* _Synonymes : Méthode de vérification du détenteur de carte_
* _Termes associés : code de sécurité_

## D

### schéma de base de données

_noun_

Structure des données d’une base de données.
Définit la manière dont les données sont organisées et dont les relations entre les données sont gérées, y compris toutes les contraintes appliquées aux données.
Un module peut contenir des fragments du schéma de base de données si ce module contient des données qui doivent être stockées dans la base de données.

_Attributs de terme :_

* _Champ : programmation_
* _Synonymes : schéma_

### injection de dépendance

_noun_

Un modèle de conception de logiciel qui permet à une classe de spécifier ses dépendances sans avoir à les construire.
Cette classe délègue la responsabilité d’injecter la dépendance à la classe d’appel.
Utilisé pour faciliter les tests.
Pour définir les dépendances des classes, modifiez le fichier de configuration di.xml.

_Attributs de terme :_

* _Champ : programmation_

### clé de déploiement

_noun_

Une clé de déploiement est la clé publique SSH de votre projet et permet l’accès en lecture seule ou en lecture-écriture (s’il est activé) à un référentiel Git.

En savoir plus : [Connexions sécurisées](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html)

_Attributs de terme :_

* _Champ : cloud_

### double opt-in

_noun, verb_

Processus de vérification des emails qui nécessite que les abonnés potentiels effectuent une deuxième étape confirmant leur intention de s’abonner.

_Attributs de terme :_

* _Champ : business_

### produit téléchargeable

_noun_

Produit téléchargeable numériquement constitué d’un ou de plusieurs fichiers téléchargés, tels qu’un livre électronique, de la musique, une vidéo, une application logicielle ou une mise à jour.
Vous pouvez proposer un album à vendre et vendre chaque chanson individuellement.
Un produit téléchargeable peut fournir une version électronique de votre catalogue de produits.

Les fichiers téléchargeables peuvent se trouver sur votre serveur ou être fournis en tant qu’URL à tout autre serveur ou réseau de diffusion de contenu.

_Attributs de terme :_

* _Champ : logiciel de commerce, produit_
* _Termes associés : types de produits_

### contenu dynamique

_noun_

Contenu généré par du code plutôt que lu à partir d’un modèle statique.
Une fois que le contenu dynamique est initialement rendu lorsqu’un utilisateur visite une page, il est parfois possible de le mettre en cache et de le réutiliser sans nécessiter un autre appel dynamique lors d’une nouvelle visite.

_Attributs de terme :_

* _Champ : design_
* _Termes associés : php_

### URL du média dynamique

_noun_

Adresse URL générée dynamiquement par le système pour référencer une image ou un autre média.
L’adresse est liée directement aux ressources stockées sur un serveur ou sur un réseau de diffusion de contenu.
Pour utiliser une URL statique, modifiez le paramètre de configuration.
Cependant, si des URL Dynamic Media sont incluses dans votre catalogue lorsque vous désactivez le paramètre, chaque référence de votre catalogue devient un lien rompu.
Les liens peuvent être restaurés en activant à nouveau les URL de médias dynamiques.
L’utilisation d’URL Dynamic Media peut affecter les performances de recherche de catalogue.

Format de code : media url=&quot;path/to/image.jpg&quot;

_Attributs de terme :_

* _Champ : programmation_
* _Termes associés : réseau de diffusion de contenu, url_

## E

### Module ece-tools

_noun_

Ensemble de scripts et d’outils conçus pour gérer et déployer l’application Commerce. Ce package simplifie de nombreux processus d’infrastructure cloud d’Adobe Commerce, notamment le déploiement dans un environnement Docker, la gestion des crons, la vérification de la configuration du projet et l’application de correctifs d’Adobe.

En savoir plus : [Module ece-tools](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview.html)

_Attributs de terme :_

* _Champ : cli, cloud, deploy_

### entity

_noun_

Unité ou objet unique dans la programmation.
Contient des attributs ou des paramètres qui peuvent être modifiés.
Par exemple, l’évaluation (où une mise à jour peut modifier des entités telles que des règles de prix, des produits ou des catégories) et des enregistrements de base de données (où les contrats de service incluent des structures de données envoyées et reçues).

_Attributs de terme :_

* _Champ : logiciel de commerce_
* _Termes associés : attribut, règles de panier, règles de catalogue_

### valeur d’attribut d’entité

_noun_

Pour les entités de base de données, modèle de données qui code efficacement les entités.
Stocke l’ID d’entité, le nom d’attribut et la valeur sous la forme d’un triple, ce qui permet de créer des noms d’attributs d’entité à tout moment.
Dans le codage, le nombre d’attributs pouvant être utilisés pour décrire les entités peut être mis à l’échelle de manière intensive, mais le nombre qui s’applique à une entité donnée est réduit.
Ce modèle de données est flexible, mais peut être lent.

En savoir plus : [EAV et extension extension extension_attributes](https://developer.adobe.com/commerce/php/development/components/attributes/)

_Attributs de terme :_

* _Champ : programmation_
* _Synonymes : eav_

### contenu vert

_noun_

Contenu ayant une longue durée de conservation ou contenu pouvant être réutilisé.

_Attributs de terme :_

* _Champ : business_

### extension

_noun_

Code qui étend ou personnalise le comportement Adobe Commerce.
Vous pouvez éventuellement regrouper et distribuer une extension sur Commerce Marketplace ou sur un autre système de distribution d’extension.
Une extension Commerce peut inclure des modules, des thèmes et des packs de langue.

_Attributs de terme :_

* _Champ : logiciel de commerce_
* _Termes associés : composant, module, package_

### attribut d’extension

_noun_

Étendez les fonctionnalités et utilisez souvent des types de données plus complexes que les attributs personnalisés. Ces attributs n’apparaissent pas dans l’interface utilisateur graphique.

En savoir plus : [Ajout d’attributs d’extension à l’entité](https://developer.adobe.com/commerce/php/development/components/add-attributes/)

_Attributs de terme :_

* _Champ : logiciel de commerce_
* _Termes associés : attribut, valeur d’attribut d’entité_

## F

### fret à bord

_noun_

Dans le cas de la navigation internationale, ce terme signifie que la partie bénéficiaire est responsable des frais de navigation.
L&#39;OFP peut être établi en fonction du lieu d&#39;origine ou de destination et être désigné comme étant le fret prépayé ou le fret prépayé.

_Attributs de terme :_

* _Champ : entreprise, commande, prix_
* _Synonymes : fob_

### frontend

_adjectif_

Dans une application client-serveur, il y a le serveur principal et le serveur frontal.
Le composant front-end, ou client, est une interface qui permet aux utilisateurs de manipuler ou d’interagir avec le code principal sous-jacent.
Le code principal s’exécute sur un serveur.
Un utilisateur ne peut pas accéder directement au code principal.
Un utilisateur interagit avec le storefront, qui à son tour utilise du code s’exécutant sur le serveur Commerce.

Remarque : Dans le passé, le storefront était appelé &quot;front-end&quot; et l’administrateur était appelé &quot;serveur principal&quot;. Cette utilisation n’est plus prise en charge.

_Attributs de terme :_

* _Champ : conception, programmation_
* _Synonymes : côté client_
* _Termes associés : serveur principal, storefront, front de cache_

### propriétés frontend

_noun_

Propriétés qui déterminent la présentation et le comportement d’un attribut du point de vue du client dans votre boutique.

_Attributs de terme :_

* _Champ : conception, programmation_

### réalisation

_noun_

Processus de gestion des envois de clients.

_Attributs de terme :_

* _Champ : business_

## G

### carte cadeau

_noun_

Carte prépayée ou certificat-cadeau pouvant être utilisé pour effectuer des achats dans la boutique.
Chaque carte cadeau se voit attribuer un code unique qui est saisi lors du passage en caisse.
La valeur de la carte-cadeau est répercutée dans le solde du compte de la carte-cadeau.
Il existe trois types de cartes-cadeaux :

* Les cartes-cadeaux &quot;physiques&quot; peuvent être produites à partir de matériel plastique ou de stock de cartes, expédiées au client.
* Les cartes-cadeaux &quot;virtuelles&quot; sont envoyées par e-mail.
* Les cartes-cadeaux &quot;combinées&quot; sont une combinaison des deux, expédiées au destinataire sous forme de carte physique et également livrées par e-mail.
Les cartes cadeau sont configurables, notamment les options d’éligibilité de produit et de sélection de montants ouverts ou fixes.

Une carte-cadeau peut également être échangée par l’administrateur du magasin à la demande du client lorsque la commande est en cours de création dans le serveur principal.

Les cartes cadeau aident également les promotions, car les administrateurs de magasins peuvent créer manuellement les comptes de carte-cadeau dans le serveur principal et envoyer les codes de carte-cadeau au segment client spécifique.
Les cartes-cadeaux peuvent servir de programme de fidélité destiné aux clients les plus actifs qui effectuent de nombreux achats sur la boutique en ligne ou dans le cadre d’une campagne promotionnelle spécifique pendant les vacances.

_Attributs de terme :_

* _Champ : logiciel de commerce_
* _Termes associés : types de produits_

### marge brute

_noun_

La différence entre le coût et le prix d’un produit.

_Attributs de terme :_

* _Champ : business_

### produit groupé

_noun_

Type de produit avec plusieurs produits autonomes similaires regroupés sur une seule page.
Peuvent être proposées avec des variantes d’un seul produit ou en les regroupant par saison ou thème pour créer un ensemble coordonné.
Chaque produit peut être acheté séparément ou dans le cadre du groupe .

Par exemple, pour un couteau de quatre tailles, les quatre couteaux peuvent être affichés dans une page de produits regroupés.
Les clients peuvent sélectionner les tailles de leur choix et les ajouter au panier à partir de cette page.

_Attributs de terme :_

* _Champ : logiciel de commerce, produit_
* _Termes associés : produit simple, types de produits_

## h

### handle

_noun_

En règle générale, une poignée est une manière de référencer un objet.
Dans Adobe Commerce, les poignées sont utilisées à de nombreux endroits, le plus souvent pour identifier une page.
Pour les gestionnaires de page, le nom d’utilisateur est dérivé de l’URL, puis utilisé pour localiser et charger les fichiers de mise en page de la page référencée.
Par exemple, dans le module Client, il existe un fichier de disposition appelé &quot;view/frontend/layout/checkout_cart_index.xml&quot;.
Ici &quot;frontend&quot; est le nom de la zone et &quot;checkout_cart_index&quot; est le nom de la poignée, qui sont tous deux dérivés de l’URL.

_Attributs de terme :_

* _Champ : programmation_
* _Synonymes : gestionnaire de page_

### mise à l’échelle horizontale

_noun_

La mise à l’échelle horizontale (également appelée mise à l’échelle) est le processus d’ajout de noeuds ou de machines supplémentaires à votre infrastructure pour répondre à une demande croissante.

_Attributs de terme :_

* _Champ : cloud_

## I

### interception

_noun_

Processus d’injection de nouveau code avant, après ou autour d’une fonction publique existante d’une classe PHP.

Pour intercepter une fonction, un plug-in implémente le code supplémentaire à appeler.
Les plug-ins sont associés à des points d’interception par le fichier de configuration d’injection de dépendance (di.xml).
Si plusieurs plug-ins sont définis sur la même fonction, la configuration d’injection de dépendance définit l’ordre dans lequel ils sont appelés, ce qui permet d’utiliser plusieurs plug-ins sans conflit.

_Attributs de terme :_

* _Champ : programmation_
* _Termes associés : plug-in_

## L

### layout

_noun_

Dans la construction d’une page Commerce, une mise en page est une série de blocs assemblés dans une hiérarchie, représentant la structure de la page.

Les fichiers de mise en page se concentrent sur le niveau de structure de page le plus élevé (en-tête, pied de page, zone de contenu principale, barre latérale gauche, etc.).
Les fichiers de mise en page assemblent ensuite du contenu (blocs) dans ces différentes zones de la page.

_Attributs de terme :_

* _Champ : conception, logiciel de commerce_
* _Termes associés : instructions de mise en page, block_

### instructions de mise en page

_noun_

Balisage dans un fichier de disposition qui décrit les modifications à appliquer à une arborescence d’éléments structurés de blocs, de conteneurs et de composants d’IU.
Un seul fichier de mise en page peut contenir plusieurs instructions de mise en page.
Les instructions de mise en page sont codées au format XML dans les fichiers de mise en page.

_Attributs de terme :_

* _Champ : conception, programmation_
* _Termes associés : mise en page, bloc, conteneur, composant ui_

### mise à jour des mises en page

_noun_

Utilisé pour les fragments de code ajoutés afin de modifier la mise en page XML ou d’importer les instructions de mise en page d’un autre fichier.

_Attributs de terme :_

* _Champ : conception, logiciel de commerce_

### Propriétaire de la licence

_noun_

Le propriétaire de la licence (également appelé propriétaire du compte) est la personne désignée d’une entreprise qui gère les paiements et d’autres problèmes liés à l’entreprise pour le compte Adobe Commerce sur l’infrastructure cloud.
Cette personne sert de point de contact avec l’Adobe.
Une fois qu’une entreprise a acheté une Adobe Commerce sur abonnement à l’infrastructure cloud, l’accès initial au projet et au code n’est disponible que pour la personne désignée comme propriétaire de la licence.

_Attributs de terme :_

* _Champ : business_

## M

### MAGEID

_noun_

MAGEID est généralement le contact de facturation sur le compte Adobe Commerce (et peut ne pas être le propriétaire du projet d’infrastructure cloud Adobe Commerce).
Pour les droits d’accès à Adobe Commerce et Adobe Commerce sur les modules d’infrastructure cloud, vous devez utiliser les clés d’accès associées à un MAGEID auquel l’accès à ces modules a été accordé.

En savoir plus : [Obtenir vos clés d’authentification](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html)

_Attributs de terme :_

* _Champ : logiciel de commerce_

### balisage

_noun_

Dans le marketing et la vente au détail, un pourcentage ajouté au coût d’un article pour déterminer le prix de détail.
[Configurez le balisage](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/settings/settings-advanced-custom-options.html), ou Markdown, d’un produit par le biais d’options personnalisables du produit.

En développement, un langage informatique qui contrôle le traitement, la présentation et la mise en forme du texte.
En outre, les balises de balisage sont des fragments de code qui ajoutent des fonctionnalités ou du contenu à une page ou à un bloc CMS.

_Attributs de terme :_

* _Champ : entreprise, programmation_
* _Synonymes : Markdown_

### environnement maître

_noun_

Sur Adobe Commerce sur l’infrastructure cloud, les projets Pro utilisent un environnement actif Platform as a Service (PaaS) appelé master qui comprend une copie de la base de données et du serveur web de votre environnement de production.

_Attributs de terme :_

* _Champ : cloud_

### compte commercial

_noun_

Compte auprès d’une banque ou d’une institution financière permettant d’accepter des transactions par carte de crédit.

_Attributs de terme :_

* _Champ : business_

### MFTF

_noun_

MFTF est un [cadre de test fonctionnel](https://developer.adobe.com/commerce/testing/functional-testing-framework/).
Il fournit une structure de test pour les développeurs Commerce et les ingénieurs logiciels, tels que les spécialistes de l’assurance qualité, les développeurs PHP et les intégrateurs système.
Les développeurs et l’assurance qualité peuvent rédiger des tests pour tenter d’interagir avec les applications web, vérifier les fonctionnalités et automatiser les tests de régression.

_Attributs de terme :_

* _Champ : logiciel de commerce, programmation_
* _Termes associés : bloc cms, bloc statique, conteneur, mise en page_

### module

_noun_

Code qui modifie ou étend les fonctionnalités fournies par l’application de Magento.
Un module est contenu dans une structure de répertoires qui contient des fichiers PHP et XML (configuration, blocs, contrôleurs, assistants, modèles, etc.) associés à une fonctionnalité spécifique afin de fournir une collection distincte de fonctionnalités du produit.
L’objectif de chaque module est de fournir des fonctionnalités de produit spécifiques en implémentant de nouvelles fonctionnalités ou en étendant les fonctionnalités d’autres modules.
Chaque module est conçu pour fonctionner indépendamment, de sorte que l’inclusion ou l’exclusion d’un module particulier n’a aucune incidence sur les fonctionnalités des autres modules.

Un module peut également implémenter des widgets, qui sont des éléments de page qui peuvent être personnalisés par les utilisateurs professionnels dans l’administrateur.

Les modules peuvent être désactivés ou supprimés sans rompre la cohérence de l’application de Magento.
Une exception : lorsque le module dépend d’autres modules, ce qui nécessite la désactivation ou la suppression des modules dépendants.

_Attributs de terme :_

* _Champ : logiciel de commerce_
* _Termes associés : php, xml, block_

## O

### OMS

_noun_

OMS est l’offre Order Management System de l’Adobe.

>[!IMPORTANT]
>
>Adobe Commerce Order Management (OMS) a atteint la fin de vie et n’est plus pris en charge.

OMS est une solution flexible et abordable pour gérer, vendre et réaliser des stocks à partir de n’importe quel canal de vente.
Le système OMS offre une expérience client transparente, qui augmente les ventes tout en réduisant les coûts et accélère le délai de mise sur le marché.

Les fonctionnalités d’OMS incluent :

* Visibilité globale et gestion de l’ensemble de l’inventaire
* Capacité d’envoyer vers et depuis n’importe quel emplacement
* Service client plus facile et plus réactif
* Amélioration de l’expérience client et de la fidélité

En savoir plus : [site de documents OMS archivés](https://commerce-docs.github.io/oms-documentation-archive/)

_Attributs de terme :_

* _Champ : fonctionnalité, logiciel de commerce, gestion des commandes_
* _Synonymes : gestion des commandes, MOM, système de gestion des commandes, Magento Order Management_
* _Termes associés : gestion des commandes_

### cloaking d’origine

_noun_

Le cloaking d’origine est une fonctionnalité de sécurité qui permet à Adobe Commerce sur l’infrastructure cloud de bloquer tout trafic non Fastly afin d’empêcher les attaques DDoS, se rendant dans l’infrastructure cloud (origine).

En savoir plus : [cloaking d’origine Fastly](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/fastly-origin-cloaking-enablement-faq.html)

_Attributs de terme :_

* _Champ : sécurité_
* _Termes associés : pare-feu d’application web_

## P

### Page Builder

_noun_

Page Builder est une extension Commerce permettant de créer des pages riches en contenu en faisant glisser et en déposant des contrôles prédéfinis pour définir des mises en page personnalisées.
Ces contrôles sont également appelés &quot;types de contenu&quot;.
Les marchands peuvent concevoir des mises en page et des pages sans expérience de codage.
Les développeurs peuvent étendre le créateur de pages en prenant en charge les extensions.

En savoir plus : [Guide de l’utilisateur de Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/introduction.html), [Documentation de développement de Page Builder](https://developer.adobe.com/commerce/frontend-core/page-builder/)

_Attributs de terme :_

* _Champ : logiciel de commerce, conception_
* _Synonymes : Admin, panneau d’administration, serveur principal, interface d’administration, interface utilisateur d’administration_
* _Termes associés : admin_

### passerelle de paiement

_noun_

Une passerelle de paiement est un service tiers qui traite en toute transparence les transactions par carte de crédit sans que le client quitte le site du commerçant.

_Attributs de terme :_

* _Champ : entreprise, commande, programmation_

## R

### produit associé

_noun_

Une sélection de produits présentée comme une incitation à l’achat d’articles supplémentaires.
Si, par exemple, le client consulte la page du produit pour une caméra, les produits associés peuvent inclure d’autres caméras comparables, un cas de caméra et un trépied.

_Attributs de terme :_

* _Champ : logiciel de commerce, produit_

## s

### règles de vente

_noun_

Inclut des règles de panier et de catalogue, qui sont utilisées pour évaluer le prix d’un produit pour les promotions.

_Attributs de terme :_

* _Champ : logiciel de commerce, produit_
* _Termes associés : règles de panier, règles de catalogue_

### scope

_noun_

Dans Adobe Commerce, la portée décrit l’étendue de votre hiérarchie de magasins qu’un paramètre peut affecter.
La portée peut s’appliquer aux éléments suivants :

* Global : tous les sites web, magasins et vues de magasin
* Site web : le site web sélectionné, ainsi que tous les magasins et les vues de magasin sous celui-ci
* Magasin : le magasin sélectionné et toutes les vues de magasin sous celui-ci.
* Affichage magasin : vue magasin sélectionnée.

Dans la hiérarchie, les paramètres appliqués à un niveau inférieur peuvent remplacer certains paramètres de niveau supérieur.

_Attributs de terme :_

* _Champ : logiciel de commerce_

### contrat de service

_noun_

Ensemble d’interfaces PHP définies pour un module.
Un contrat de service comprend des interfaces de données, qui préservent l’intégrité des données, ainsi que des interfaces de service, qui masquent les détails de la logique commerciale aux demandeurs de service tels que les contrôleurs, les services web et d’autres modules.
Les API Web peuvent être liées aux contrats de service via des fichiers de configuration.

_Attributs de terme :_

* _Champ : programmation_
* _Termes associés : php, web api_

### accord

_noun_

Le règlement a lieu lorsque la banque qui procède à l&#39;acquisition et les fonds de l&#39;exchange émetteur et que le produit est déposé sur le compte marchand.

_Attributs de terme :_

* _Champ : business_

### Catalogue partagé

_noun_

Fonctionnalité qui permet aux commerçants de créer un catalogue qui peut servir de catalogue entier ou de sous-ensemble de celui-ci, puis d’attribuer des prix personnalisés pour un ou plusieurs produits.
Les vendeurs peuvent ensuite attribuer ce catalogue à une ou plusieurs sociétés.

Par exemple, un commerçant B2B a trois clients qui ont négocié des tarifs spécifiques pour le site de distribution électronique du marchand.
À l’aide de la fonctionnalité de catalogue partagé, le marchand dispose :

* Un catalogue principal
* Un catalogue du client 1 (peut-être que ce ne sont que trois SKU avec de lourdes remises sur eux depuis le catalogue principal)
* Catalogue de clients 2 (peut être le catalogue entier avec 10 % de réduction)
* Catalogue de clients 3 (quelques dizaines de produits avec remises sur le catalogue principal allant de 5 à 60 %).

_Attributs de terme :_

* _Champ : logiciel de commerce, produit_
* _Termes associés : catalogue, b2b_

### envoi

_noun_

Une expédition contient les produits à livrer et génère un enregistrement des produits dans une commande qui a été expédiée.
Plusieurs envois peuvent être associés à une seule commande.

_Attributs de terme :_

* _Champ : entreprise, commande_

### document d&#39;expédition

_noun_

Document accompagnant une expédition. Le document répertorie les produits et leurs quantités dans le package de diffusion.

_Attributs de terme :_

* _Champ : entreprise, commande_

### opérateur de transport

_noun_

Une entreprise qui transporte des packages. Les opérateurs courants sont UPS, FedEx, DHL et USPS.

_Attributs de terme :_

* _Champ : entreprise, commande_

### panier

_noun_

Ensemble de produits qu’un client a choisi d’acheter, mais qu’il n’a pas encore acheté.
Fait également référence à une zone d’un site de commerce électronique où ces produits peuvent être trouvés pour révision et passage en caisse.

_Attributs de terme :_

* _Champ : entreprise, conception, produit, programmation_
* _Synonymes : panier, panier_
* _Termes associés : règles de panier_

### produit simple

_noun_

Le type de produit le plus élémentaire, un élément physique avec un seul SKU.
Les produits simples disposent de divers contrôles de prix et d’entrée qui permettent de vendre des variantes du produit.
Les produits simples peuvent être utilisés en association avec des produits regroupés, regroupés et configurables.
Un produit simple avec des options personnalisées est parfois appelé produit composite.

_Attributs de terme :_

* _Champ : logiciel de commerce, produit_
* _Termes associés : types de produits_

### SKU

_noun_

Abréviation du Groupe de la gestion des stocks.
Numéro ou code attribué à un produit pour identifier le produit, les options, le prix et le fabricant.

_Attributs de terme :_

* _Champ : entreprise, tarification, produit, programmation_
* _Termes associés : catalogue partagé_

### page de démarrage

_noun_

Page promotionnelle avec un produit ou une publicité, normalement affichée avant la page d’accueil.

_Attributs de terme :_

* _Champ : design_

### bloc statique

_noun_

Unité modulaire de contenu pouvant être placée par un utilisateur dans CMS sur une page pour afficher du texte et des images, ou exécuter des fragments de code.
Les blocs statiques contiennent du contenu modifiable et peuvent servir de landing pages pour les catégories de produits.
Des widgets peuvent être ajoutés aux blocs statiques pour fournir des fonctionnalités supplémentaires.

_Attributs de terme :_

* _Champ : logiciel de commerce_
* _Termes associés : bloc cms, bloc_

### contenu statique

_noun_

Contenu généré par l’utilisateur (non généré par le code) qui ne change pas fréquemment.

_Attributs de terme :_

* _Champ : design_
* _Termes associés : contenu dynamique_

### fichiers statiques

_noun_

Collection de ressources, telles que CSS, polices, images et JavaScript, utilisée par un thème.

_Attributs de terme :_

* _Champ : logiciel de commerce_

### store

_noun_

Le niveau de portée Commerce de &quot;magasin&quot; est le second niveau de la hiérarchie de votre site web, qui se présente comme suit : site web > magasin > vue magasin.
Les magasins peuvent être organisés en un ou plusieurs magasins. Chaque magasin, potentiellement, possède sa propre catégorie racine et tous partagent le catalogue et les données client.

Chaque magasin peut avoir plusieurs vues de magasin, qui sont généralement utilisées pour présenter le storefront dans une langue et un paramètre régional différents.

_Attributs de terme :_

* _Champ : logiciel de commerce, produit_
* _Termes associés : vue de magasin, site web_

### vue de magasin

_noun_

Le niveau de portée Commerce de &quot;vue de magasin&quot; fait référence au troisième niveau de la hiérarchie des sites web, des magasins et des vues de magasin.
Les vues de magasin présentent généralement le storefront dans une langue et un paramètre régional différents.
Pour modifier les vues des magasins, utilisez le sélecteur de magasin dans l’en-tête .

_Attributs de terme :_

* _Champ : logiciel de commerce, produit_
* _Termes associés : magasin, site web_

### storefront

_noun_

Boutique en ligne que les clients voient lorsqu’ils visitent votre site Commerce.

_Attributs de terme :_

* _Champ : logiciel de commerce, produit_

## T

### règle fiscale

_noun_

Combinaison d’une classe de taxe sur les produits, d’une classe de taxe sur les clients et d’un taux d’imposition. Cette règle définit le calcul de la taxe à appliquer.

_Attributs de terme :_

* _Champ : business_

### modèle

_noun_

Court pour le modèle d’HTML ou le modèle PHTML.
Un fichier PHTML contient un mélange de balisage d’HTML et de code PHP pour injecter du contenu dynamique dans l’HTML.
La plupart des blocs comportent au moins un fichier PHTML (template) contenant l&#39;HTML statique généré par le bloc.
Dans l’Admin, les modèles d’email et de newsletter combinent du texte, des images et des variables avec des balises d’HTML pour produire du contenu personnalisé envoyé par le système.

_Attributs de terme :_

* _Champ : logiciel de commerce_
* _Termes associés : block_

### thème

_noun_

Contient des informations graphiques et d’aspect.
Personnalise l’aspect du magasin.
Adobe Commerce peut envoyer des thèmes dans des modules (compositeur).
Mais les thèmes peuvent être placés sous application/conception, qui n’est pas fournie dans un package.
Les modules sont l’unité de téléchargement du compositeur d’expérience visuelle et — par Commerce Marketplace — les utilisateurs de Commerce peuvent télécharger CE ou EE sous la forme d’une série de modules, où les modules contiennent des modules, des thèmes ou des modules de langue.

_Attributs de terme :_

* _Champ : logiciel de commerce_

## U

### Composant d’interface utilisateur

_noun_

Balise conçue pour le logiciel Adobe Commerce pour permettre un rendu plus simple et plus flexible de l’interface utilisateur.
Les objectifs du système de composants de l’interface utilisateur sont les suivants :

* Simplification de la gestion des fichiers XML par mise en page
* Déplacement des éléments de l’interface utilisateur d’administration d’HTML+JavaScript vers un système de widgets personnalisés &quot;JavaScript pur&quot;
* Activation de la création de composants d’interface utilisateur plus complexes à partir de composants plus petits
* Prérendu des données pour les composants de l’interface utilisateur au format JSON, liaison étroite aux objets de données du serveur principal
* Utilisation d’AJAX pour mettre à jour les données de composant
* Présentation d’un nouveau DSL pour la création des éléments ci-dessus

En savoir plus : [Guide des composants de l’interface utilisateur](https://developer.adobe.com/commerce/frontend-core/ui-components/), [Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/introduction.html)

_Attributs de terme :_

* _Champ : programmation_
* _Termes associés : JavaScript, mise en page, composant, créateur de pages_

### UPWARD

_noun_

[PWA Studio](https://github.com/magento/pwa-studio) utilise [UPWARD](https://developer.adobe.com/commerce/pwa-studio/guides/packages/upward/) dans le développement.
UPWARD est l’acronyme de Unified Progressive Web App Response Definition.
Un fichier de définition UPWARD décrit comment un serveur web fournit et prend en charge un Progressive Web Application.

Les fichiers de définition UPWARD fournissent des détails sur le comportement du serveur à l’aide d’un langage déclaratif indépendant de la plateforme.
Cela permet à un Progressive Web Application de s’exécuter sur un serveur conforme UPWARD dans n’importe quelle langue sur tech stack, car l’application n’est concernée que par le comportement du point de terminaison HTTP du serveur UPWARD.

Un serveur UPWARD utilise un fichier de définition pour déterminer le processus ou le service approprié pour une demande provenant d’un shell d’application.
Il décrit comment le serveur doit gérer une requête et créer la réponse pour celle-ci.

Un projet de PWA peut inclure un fichier de définition UPWARD pour spécifier ses dépendances de service.

_Attributs de terme :_

* _Champ : conception, logiciel de commerce, programmation_
* _Synonymes : PWA Studio, Unified Progressive Web App Response Definition{1_
* _Termes associés : pwa_

## V

### Extension groupée du fournisseur

_noun_

Le code produit par le fournisseur qui étend ou personnalise le comportement de Commerce et fonctionne comme une extension tierce est considéré comme une extension groupée de fournisseurs (VBE).
Les environnements virtuels sont soigneusement testés et inclus dans chaque version prise en charge d’Adobe Commerce.
Un serveur de diffusion virtuelle peut inclure des modules, des thèmes et des modules de langue.

Pour en savoir plus, consultez la [rubrique Extension groupée de fournisseur](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/modules/upgrade.html).

_Attributs de terme :_

* _Champ : extension de commerce, extension groupée du fournisseur, extension, VBE_
* _Synonymes : extension, VBE_
* _Termes associés : extension, extension groupée_

### mise à l’échelle verticale

_noun_

La mise à l’échelle verticale (mise à l’échelle) fait référence à l’augmentation de la puissance de traitement d’un seul serveur ou d’une seule grappe en ajoutant des E/S de disque ou réseau, des processeurs ou de la mémoire vive.

_Attributs de terme :_

* _Champ : environnement_

### produit virtuel

_noun_

Représente un produit non physique qui peut être vendu, tel qu’un abonnement, un service, une garantie ou un abonnement.
Les produits virtuels peuvent être vendus individuellement ou inclus dans les types de produits suivants : les produits regroupés et les produits regroupés.
Ne nécessite pas d’expédition ou d’inventaire.

Le processus de création d&#39;un produit virtuel et d&#39;un produit simple est presque le même.
Cependant, comme un produit virtuel n’est pas fourni, il n’existe pas de champ de poids ni d’option permettant d’inclure une carte-cadeau.

_Attributs de terme :_

* _Champ : logiciel de commerce, produit_
* _Termes associés : types de produits_

### type virtuel

_noun_

Les types virtuels permettent d’injecter différentes dépendances dans les classes PHP existantes sans affecter d’autres classes et sans avoir à créer un fichier de classe.
Les types virtuels ne peuvent être référencés que par le remplacement d’arguments dans un élément `<type>` dans des fichiers di.xml, et jamais dans le code source.
Ils ne peuvent pas être étendus et ne peuvent pas être des références en tant que dépendances dans un constructeur de classes.

_Attributs de terme :_

* _Champ : programmation_
* _Termes associés : php_

## W

### site web

_noun_

Dans le logiciel Adobe Commerce, niveau supérieur de la hiérarchie d’un site web, au-dessus de la vue magasin et magasin.
Vous pouvez avoir plusieurs sites web et chaque site web peut avoir un nom de domaine différent.
Les sites web peuvent être configurés pour partager des données client ou pour ne pas partager de données.

_Attributs de terme :_

* _Champ : logiciel de commerce, conception, produit_
* _Termes associés : magasin, magasin view_

### widget

_noun_

Un [widget](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/widgets/widgets.html) est un fragment de code préparé qui peut être utilisé pour placer des blocs, des liens et du contenu dynamique à des emplacements spécifiques sur les pages de magasin.
Vous pouvez utiliser des widgets pour créer des landing pages pour les campagnes marketing, afficher du contenu promotionnel à des emplacements spécifiques dans tout le magasin.
Les widgets peuvent également être utilisés pour ajouter des éléments interactifs et des blocs d’action pour les systèmes de révision externes, les conversations vidéo, les formulaires de vote et d’abonnement, ou pour fournir des éléments de navigation pour les nuages de balises et les curseur d’image.

_Attributs de terme :_

* _Champ : entreprise, logiciel de commerce, conception_
* _Termes associés : block_
