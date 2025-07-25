---
source-git-commit: 2f471a1bc1cbf31076aeb67ceaee289196841cd4
workflow-type: tm+mt
source-wordcount: '3326'
ht-degree: 0%

---
# Problèmes résolus dans Adobe Commerce (v2.4.9-alpha1)

## Correction de problèmes dans v2.4.9-alpha1

Nous avons corrigé 84 problèmes dans le code principal 2.4.9-alpha1 d’Adobe Commerce. Un sous-ensemble des problèmes résolus inclus dans cette version est décrit ci-dessous.

### API

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

### Compte

#### L’opération de suppression [Cloud] est interdite pour l’erreur de zone actuelle lors de la création du compte client

Après le correctif, la sauvegarde d’un client avec une adresse non valide renvoie un message décrivant la raison de l’invalidité au lieu de non pertinent « L’opération de suppression est interdite pour la zone actuelle ».

_ACP2E-3791 - [contribution du code GitHub](https://github.com/magento/magento2/commit/6ea61121)_

### Interface utilisateur d’administration

#### [Problème] Améliorer l’expérience utilisateur grâce à l’arborescence des rôles

Cette demande d’extraction ajoute des boutons pour tout réduire, tout développer et développer les branches avec les éléments sélectionnés. Cette fonctionnalité est similaire à celle fournie dans l’arborescence des catégories (Catalogue -> Inventaire -> Catégories)

_AC-14020 - [Problème GitHub](https://github.com/magento/magento2/issues/39654) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/36511)_

#### Symfony\Component\Mime\Exception\LogicException : l’en-tête « Sender » doit être une instance de « Symfony\Component\Mime\Header\MailboxHeader » (obtenu « Symfony\Component\Mime\Header\MailboxListHeader »)

_AC-14520 - [Problème GitHub](https://github.com/magento/magento2/issues/39823) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/1e14bd72)_

#### Fournir une fonctionnalité pour supprimer en masse les taux de taxe à l’aide de la grille

Les utilisateurs administrateurs peuvent désormais supprimer simultanément plusieurs taux de taxe de la grille Taux de taxe d&#39;administration .  [GitHub-33399](https://github.com/magento/magento2/issues/33399)

_AC-2238 - [Problème GitHub](https://github.com/magento/magento2/issues/33399) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/33484) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/5cd64dd0)_

#### La règle de prix du panier avec la condition SKU ne prend pas en compte les « zéros de début » dans le SKU (SKU : 01234 est le même que 1234)

Le système gère désormais correctement la règle de prix du panier avec la condition SKU prenant en compte les « zéros au début » dans le SKU

_AC-9428 - [Problème GitHub](https://github.com/magento/magento2/issues/37919) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39525)_

#### Problème lié au comportement de la valeur d’option d’attribut par défaut pour la sélection multiple

Avant la correction, les valeurs par défaut de plusieurs attributs d’options n’étaient pas enregistrées correctement. Désormais, après le correctif, les valeurs sont correctement stockées dans la base de données.

_ACP2E-3523 - [contribution du code GitHub](https://github.com/magento/magento2/commit/9608ca21)_

#### Les sous-titres du menu d’administration principal ne s’affichent pas

Tous les titres des groupes du menu principal s’affichent désormais correctement. Auparavant, si la deuxième ou la troisième colonne du menu principal ne contenait qu’un seul groupe de liens, le titre du groupe n’était pas affiché.

_ACP2E-3540_

#### Problème lors du déplacement de la quantité de produit de l’administrateur vers le panier

Lors de la création d’une commande à partir de l’administrateur, les produits du panier client dans la barre latérale ne disparaissent pas lorsqu’ils sont ajoutés à la commande.

_ACP2E-3563 - [contribution du code GitHub](https://github.com/magento/magento2/commit/c8ba4ab1)_

### Interface utilisateur d’administration, B2B

#### La connexion B2B en tant qu’en-tête client comporte toujours l’identité de marque Magento

Auparavant, l’en-tête du storefront affichait « Vous êtes désormais connecté en tant que &lt;nom du client> sur &lt;nom du magasin> » avec l’identité graphique de Magento. Ce problème est maintenant résolu et l’en-tête s’affiche avec le branding ADOBE.

_AC-14361 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/fadcfa8b)_

### Interface utilisateur d’administration, contenu

#### Exception « Impossible de créer un rendu pour les chemins d’accès aux ressources multimédias » lors de l’insertion de l’image

Après avoir supprimé les valeurs de Largeur maximale et Hauteur maximale de la configuration de l’optimisation des images de la Galerie de médias, l’erreur ne s’est plus produite pendant le processus d’optimisation des images.

_ACP2E-3781 - [contribution du code GitHub](https://github.com/magento/magento2/commit/520f9e30)_

### Interface utilisateur d’administration, sécurité

#### Gestion des mots de passe faibles

L’utilisateur administrateur ne peut pas être enregistré avec le même mot de passe. Auparavant, il était enregistré sans validation appropriée.

_ACP2E-3657 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/df92debe)_

### Interface utilisateur d’administration, sécurité, évaluation et prévisualisation

#### Logs d’action pour l’évaluation du contenu

Les journaux d’actions affichent désormais les activités de mise à jour de l’évaluation. Auparavant, le journal des mises à jour intermédiaires n’était pas enregistré dans les journaux d’actions d’administration.

_ACP2E-3679_

### B2B

#### Passer une commande ne fonctionne pas sur Passer en caisse via un devis négociable avec le mode de paiement par carte de crédit PayFlow Pro

_AC-11973_

#### Le message de réussite après le changement de nom du devis disparaît par intermittence

_AC-13447_

#### Le calcul du total général n&#39;inclut pas le montant de la taxe

La commande contient des totaux corrects lorsque les commandes fournisseur existantes sont activées pour le commerce transfrontalier.

_ACP2E-3727_

#### L’annulation de l’affectation de catégories dans un catalogue partagé B2B via l’API REST est lente

Désormais, les performances sont considérablement améliorées lors de l’annulation de l’affectation de catégories en B2B. Auparavant, l’annulation de l’affectation de catégories dans le catalogue partagé B2B prenait beaucoup de temps.

_ACP2E-3796_

#### Problème de performance avec le nouveau correctif d’installation dans B2B

Correction du problème de performances en raison duquel la mise à niveau du module Magento_Company après la mise à jour vers B2B 1.5.2 prenait trop de temps lors du traitement d’un grand nombre d’enregistrements (~100 000+) dans la table company_structure.

_ACP2E-3850_

### Panier et passer en caisse

#### mise à jour de Magento 2.4.7 (mini)panier aucune quantité décimale autorisée

Désormais, Magento gère correctement lorsque nous mettons à jour la quantité avec des décimales du mini panier lorsque le paramètre régional était NL (néerlandais)

_AC-13238 - [Problème GitHub](https://github.com/magento/magento2/issues/39236) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39669)_

#### [Problème] Mettre à jour le sous-total.phtml

Le système met à jour le fichier subtotal.phtml avec l&#39;espacement approprié

_AC-13907 - [Problème GitHub](https://github.com/magento/magento2/issues/39619) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39612)_

#### Impossible de passer la commande auprès de l’invité

_AC-14241 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/27217d0e)_

#### Les devis persistants expirés ne sont pas nettoyés par un traitement cron sales_clean_quotes

Les guillemets persistants expirés sont désormais effacés lorsque la tâche cron &#39;persistent_clear_expired&#39; s&#39;exécute. Auparavant, les guillemets persistants expirés n’étaient effacés par aucune autre tâche cron.

_ACP2E-3493 - [contribution du code GitHub](https://github.com/magento/magento2/commit/11be3dff)_

#### Erreur « Un problème est survenu » lors du passage en caisse pour une entreprise inactive

Avant le correctif, l’action de déconnexion n’était pas correctement effectuée sur la page du panier si la société de l’utilisateur connecté n’était plus activée. Désormais, si l’entreprise n’est plus disponible, la déconnexion est correctement effectuée.

_ACP2E-3541 - [contribution du code GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### La sélection des adresses n’est pas enregistrée lorsque nous « Extrayons avec plusieurs adresses »

Avant la correction lors de l’annulation de l’option d’expédition multiple, l’adresse n’était pas présélectionnée lors du retour à l’expédition multiple. Désormais, l’adresse par défaut est remplacée par l’une des sélections effectuées dans l’écran d’expédition multiple.

_ACP2E-3646 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/6ea61121)_

### Panier et passage en caisse, SEO

#### URL de code de carte cadeau incorrecte dans l’e-mail lors de l’achat sur le site web secondaire

Auparavant, la configuration multi-magasin et la carte cadeau pour les magasins non par défaut redirigeaient toujours la demande de carte cadeau vers le site web par défaut. Une fois ce correctif appliqué, l’e-mail redirige le lien de demande de carte cadeau vers la portée ou le site web approprié.

_ACP2E-3699_

### Panier et passer en caisse, expédition

#### [Ligne principale] la règle de prix du panier ne respecte pas la livraison multiple

Avant la mise en œuvre de cette correction, la règle de prix du panier pour les produits à expédition multiple ne s’appliquait pas correctement lorsque des conditions de sous-sélection étaient appliquées et que l’expédition gratuite était activée. Cependant, depuis l’application de la correction, la règle de prix de panier pour les paniers à expéditions multiples fonctionne désormais comme prévu.

_ACP2E-3666 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

### Catalogue

#### Dupliquer le fpc de cache pour la même page avec la même requête

Le système identifie et utilise désormais correctement le même Cache de page complet (FPC) pour les pages avec les mêmes paramètres de requête, quel que soit leur ordre ou leurs caractères de fin. Cela évite une augmentation inutile de la taille du dossier de cache de page. Auparavant, le système créait un identifiant FPC différent pour la même page si l’ordre des paramètres de requête était différent ou s’il y avait des caractères de fin, ce qui entraînait une augmentation de la taille du dossier de cache de page.

_AC-10722 - [Problème GitHub](https://github.com/magento/magento2/issues/38269) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38270)_

#### Indexation manquante des colonnes obligatoires dans la table catalog_product_entity_int

Ajout de l’indexation manquante des colonnes obligatoires dans la table catalog_product_entity_int

_AC-10844 - [Problème GitHub](https://github.com/magento/magento2/issues/38315) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38316)_

#### La page produit renvoie une erreur en raison de réécritures d’URL.

Désormais, la page produit est chargée avec succès lorsque des réécritures d’URL sont disponibles

_AC-2950 - [Problème GitHub](https://github.com/magento/magento2/issues/35371) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39670)_

#### [Cloud] bogue lors de l’ajout de produits à une catégorie

Le libellé pagination et nombre d’enregistrements fonctionne désormais correctement lors de l’ajout de produits à une catégorie via la grille contextuelle. Auparavant, le chargement d’une seule page avec des éléments égaux à la taille de la page provoquait des problèmes avec la liste déroulante de sélection d’éléments.

_ACP2E-3526_

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

#### La validation de la carte cadeau échoue lors de la modification en raison du séparateur de milliers

Correction d’un problème lié à l’enregistrement du type de produit de carte cadeau lorsque le montant de la carte cadeau est de 1 000 et plus.

_ACP2E-3704_

### Catalogue, GraphQL, Recherche

#### Le graphql des produits a renvoyé des catégories désactivées dans les agrégations de catégories

Après la correction, les catégories désactivées ne sont pas renvoyées pour la requête GraphQl des produits.

_ACP2E-2885 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

### Catalogue, produit

#### [Bogue aléatoire] la bibliothèque Fotorama n’est pas chargée

Le système s’assure désormais que la bibliothèque Fotorama est correctement chargée, ce qui permet à toutes les images jointes d’être affichées dans la galerie d’images comme prévu. Auparavant, seule la première image était visible en raison d’un problème de chargement incorrect de la bibliothèque Fotorama.

_AC-12124 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/45b51c9c) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/27217d0e)_

### Contenu

#### L’insertion du fichier csp_whitelist.xml dans le thème ne fonctionne pas et crée un problème intermittent

Mise en cache implémentée de la liste autorisée CSP par zone du site web.

_AC-13069 - [Problème GitHub](https://github.com/magento/magento2/issues/38933) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39672)_

#### Erreur : erreur de script pour « Magento_Catalog/js/validate-product » pour le générateur de page du contenu de l’administrateur avec le chargement des produits

Cette requête d’extraction corrige l’erreur de script de catalogAddToCart lors de la modification de pagebuilder avec la condition products

_AC-13891 - [Problème GitHub](https://github.com/magento/magento2/issues/39604) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39677)_

#### Bloquer la sélection dans les widgets portant le même identifiant

Le système gère désormais correctement la sélection de blocs lors de la création de widgets lorsque nous avons les mêmes blocs d’identifiant

_AC-14132 - [Problème GitHub](https://github.com/magento/magento2/issues/39692) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39722)_

#### Le préfixe de la table n’est pas pris en compte.

_AC-14556 - [Problème GitHub](https://github.com/magento/magento2/issues/39847) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### Impossible de charger l’image avec une largeur relativement faible

Le système ne parvient plus à redimensionner l’image avec une largeur relativement faible par rapport à sa hauteur.

_ACP2E-3558 - [contribution du code GitHub](https://github.com/magento/magento2/commit/9608ca21)_

#### Chemin de configuration incorrect pour la configuration du style du chemin de stockage distant

Après le correctif, la définition de la configuration du style de chemin d’accès de stockage distant aura un impact sur la configuration réelle du style de chemin d’accès AWS S3.

_ACP2E-3734 - [contribution du code GitHub](https://github.com/magento/magento2/commit/df92debe)_

### Framework

#### Compilation du code du module désactivé.

Cette demande d’extraction échappe aux modules désactivés avant la compilation de code.

_AC-10933 - [Problème GitHub](https://github.com/magento/magento2/issues/38241) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39723)_

#### Magento_Theme title.phtml template non valide pour PHP 8.2

Cette requête de tirage corrige un problème en raison duquel la page CMS créée avec l’en-tête null comme dans Php 8.x transmettant null à trim() renvoie Exception : fonctionnalité obsolète : trim() : transmission de null au paramètre #1 ($string) de type chaîne

_AC-12856 - [Problème GitHub](https://github.com/magento/magento2/issues/39092) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39398)_

#### Lors de l&#39;utilisation du stockage de fichiers pour le fournisseur de verrouillage, nous obtenons un répertoire de fichiers en constante augmentation sans aucun nettoyage

Cette demande d’extraction introduit une nouvelle tâche cron qui s’exécute une fois par jour et recherche les fichiers de verrouillage qui n’ont pas été modifiés au cours des dernières 24 heures et qui peuvent donc être supprimés en toute sécurité. Le contenu du répertoire des fichiers verrouillés restera ainsi sous contrôle.
Cette tâche cron s’exécute uniquement lorsque le fournisseur de verrouillage est configuré pour utiliser des fichiers, et non lorsque l’un des autres est utilisé (base de données - valeur par défaut, zookeeper ou cache)

_AC-13367 - [Problème GitHub](https://github.com/magento/magento2/issues/39369) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39372)_

#### [Problème] Nettoyage : n’utilisez pas la valeur de retour void des appels de méthode.

Ce PR effectue un nettoyage mineur. Parfois, nous appelions des méthodes qui ne renvoyaient rien (void), puis utilisions cette valeur de résultat. Ce qui n&#39;est vraiment pas nécessaire.

_AC-13664 - [Problème GitHub](https://github.com/magento/magento2/issues/39524) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39516)_

#### [Problème] [PHPDOC] Correction du mauvais phpdoc pour Magento\Framework\Message\ManagerInterface

Ce PR corrige le phpdoc incorrect pour \Magento\Framework\Message\ManagerInterface et supprime tous les phpdoc en double dans \Magento\Framework\Message\Manager (utilisez la syntaxe inheritdoc).

_AC-14312 - [Problème GitHub](https://github.com/magento/magento2/issues/39593) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39153)_

#### Suppression de la stabilité minimale de la version bêta de composer.json

Suppression de la stabilité minimale de la version bêta de composer.json

_AC-14450 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/1cbbf187)_

#### allow_parallèle_generation doit être défini via la variable d’environnement .

Après le correctif, la variable d’environnement « MAGENTO_DC_CACHE__ALLOW_PARALLEL_GENERATION » peut être utilisée pour définir la configuration « allow_parallèle_generation ».

_ACP2E-3673 - [contribution du code GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

#### [Cloud] La modification du type de colonne du tableau de Int à Decimal à l’aide du fichier db_schema.xml dans Magento 2 entraîne des erreurs

La modification du type de données de colonne ne fonctionne pas correctement. Auparavant, il renvoyait une erreur : l’attribut « identity » n’est pas autorisé.

_ACP2E-3709 - [contribution du code GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### Prise en charge de la nouvelle devise (XCG) dans Adobe

Caribbean Builder (XCG) est ajouté à la liste des devises.

_ACP2E-3790 - [contribution du code GitHub](https://github.com/magento/magento2/commit/520f9e30)_

### GraphQL

#### La réponse GraphQL pour l&#39;emplacement de commande n&#39;inclut pas le message d&#39;exception

Annulation de la modification précédente qui renvoyait des erreurs dans un format différent. Désormais, les erreurs potentielles sont renvoyées de manière cohérente, sans interrompre le schéma GraphQL. Ceci devrait être ajouté en tant que BIC connu, approuvé par PM en ACP2E-3399

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

### Importer/exporter

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

### Inventaire / MSI

#### Le retrait de la boutique ne respecte pas le rayon de recherche maximal lorsque l’adresse est modifiée au passage en caisse

Désormais, le magasin présélectionné dans « Choisir en magasin » sera mis à jour si l’adresse de livraison change. Auparavant, une fois qu’un magasin était présélectionné, il ne changeait pas même si la nouvelle adresse de livraison ne se trouvait pas dans le rayon du magasin sélectionné

_ACP2E-3728 - [contribution du code GitHub](https://github.com/magento/inventory/commit/07620383)_

### Ordre

#### Impossible de renvoyer la valeur null pour le champ \&amp;quot;AppliedCoupon.code\&amp;quot; problème inattendu

_AC-14484 - [Problème GitHub](https://github.com/magento/magento2/issues/39841) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/97b2ea42)_

#### [Cloud] Certains Javascript intégrés ne fonctionnent pas après la mise à niveau vers magento 2.4.6-p7

Cliquer sur le bouton « supprimer » dans « Ajouter à la commande par SKU » dans l’administration supprime désormais le SKU. Auparavant, le fait de cliquer sur le bouton « supprimer » dans « Ajouter à la commande par SKU » ne supprimait pas le SKU.

_ACP2E-3515_

#### les données sérialisées des cartes cadeaux sont incohérentes dans la table sales_order

les données de cartes cadeaux de la table sales_order sont désormais correctement sérialisées. Auparavant, elle était sérialisée chaque fois que la commande était mise à jour.

_ACP2E-3662_

### Commande, Tarifs

#### L’administrateur affiche un symbole de devise incorrect lors de la création du retour

Dans une configuration multi-site avec différentes devises (EUR/USD/GBP), la page de sélection de produit de retour dans l’administration affiche désormais le symbole de devise correct. Auparavant, il affichait le symbole de devise par défaut.

_ACP2E-3658 - [contribution du code GitHub](https://github.com/magento/magento2/commit/df92debe)_

### Autres outils de développement

#### Échec d’accessibilité de Lighthouse

Le système réussit maintenant avec un score d’accessibilité de 100

_AC-12783 - [Problème GitHub](https://github.com/magento/magento2/issues/39054) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39164)_

#### La désactivation de la configuration de storefront captcha charge toujours les fichiers js captcha

Le système ne charge plus les fichiers captcha js lorsque nous avons désactivé captcha pour storefront

_AC-14267 - [Problème GitHub](https://github.com/magento/magento2/issues/32987) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39154)_

### Emballage

#### [Emballage] Correction de la dépendance standard magento/magento-coding+ page-builder

_ACPLTSRV-6383_

### Paiements

#### [Problème] Correction de la capture de factures hors ligne (404)

Il corrige l’erreur de page 404 lors de la capture de factures pour les modes de paiement hors ligne par l’administrateur Magento

_AC-13336 - [Problème GitHub](https://github.com/magento/magento2/issues/39298) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39297)_

### Performances

#### Le module Autorisations de catégorie peut empêcher la mise en cache.

Les contrôleurs tiers sont désormais correctement mis en cache avec les segments clients

_ACP2E-3721_

### Produit

#### Collection de produits - addMediaGalleryData appelle getSize lorsque la collection peut ou va être chargée (peut utiliser count pour éviter une requête de base de données supplémentaire)

Cette requête PR réduit l’appel de requête supplémentaire à l’aide de count() si la collection de produits est déjà chargée lors de l’appel de Product Graphql avec le champ media_gallery inclus.

_AC-13055 - [Problème GitHub](https://github.com/magento/magento2/issues/39111) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39681)_

#### [2.4.8] Aucun rappel trouvé pour la tâche cron catalog_product_alert

_AC-14494 - [Problème GitHub](https://github.com/magento/magento2/issues/39800) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### La requête lente est exécutée lorsque le widget de produit est inclus via le générateur de page.

La requête pour la création de widgets de produit, y compris les SKU de produit, est optimisée.

_ACP2E-3449 - [contribution du code GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### Les images du produit ne sont pas redimensionnées lorsqu’elles sont ajoutées en tant que produit configurable

Auparavant, les images ajoutées par le biais des configurations dans le panneau d’administration ne respectaient pas la limite de taille de chargement maximale, ce qui pouvait entraîner des incohérences et des problèmes de gestion. Désormais, un correctif a été implémenté pour s’assurer que les images sont automatiquement redimensionnées lors du chargement afin de respecter la limite de taille maximale, ce qui simplifie le processus et maintient les normes système.

_ACP2E-3504 - [contribution du code GitHub](https://github.com/magento/magento2/commit/df92debe)_

### Expédition

#### Le document doit être mis à jour pour l&#39;implémentation de % , qui n&#39;est pas correcte dans le document officiel.

Mise à jour du devdoc pour la prise en charge de l’API REST DHL

_AC-14507_

#### [DHL]-Handle Dimensions facultatives dans les paramètres de taille standard et l’écart de prix entre les intégrations d’API REST et XML

_AC-14601 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/1e3bde4c)_

#### Exception lors de la création de l&#39;étiquette d&#39;expédition UPS

Correction de l’avertissement : conversion de tableau en chaîne lors de la création de l’étiquette d’expédition UPS

_ACP2E-3676 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

### Évaluation et prévisualisation

#### L’aperçu d’une mise à jour planifiée ouvre la première vue de magasin par ordre alphabétique au lieu de la vue de magasin qui vous intéresse

Avant la correction, l’aperçu d’une mise à jour planifiée s’ouvrait dans la première vue de magasin par ordre alphabétique au lieu de la vue de magasin affectée.
Après la correction, l’aperçu s’ouvre désormais correctement dans la vue de magasin affectée à la mise à jour de l’évaluation des blocs CMS.

_ACP2E-3671 - [contribution du code GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

#### Problème de comportement Cron de Staging_apply_version - special_price ignoré

Après la correction, les totaux des devis seront recalculés après la modification du prix spécial par mise à jour de produit planifiée.

_ACP2E-3674_

### Taxe

#### Le montant de la taxe n’est pas mis à jour lorsque l’emballage du cadeau est supprimé du panier

_AC-14637_
