---
source-git-commit: bfad68a46b9b1a79a702f04efd39129decda1a1c
workflow-type: tm+mt
source-wordcount: '4173'
ht-degree: 0%

---
# Notes de mise à jour de Magento Open Source (v2.4.9-alpha2)

## Correction de problèmes dans v2.4.9-alpha2

Nous avons corrigé 109 problèmes dans le code principal 2.4.9-alpha2 de Magento Open Source. Un sous-ensemble des problèmes résolus inclus dans cette version est décrit ci-dessous.

### API

#### Prix spécial à ce jour est validé de manière incorrecte sur applySpecialPrice

Le système fonctionne correctement en ce qui concerne le Prix spécial et le Prix spécial du produit expirera à la date définie par l’administrateur ou un système tiers par l’API REST

_AC-13130 - [Problème GitHub](https://github.com/magento/magento2/issues/39169) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39690)_

#### Le corps ou les paramètres de la requête incorrects provoquent une « Erreur de serveur interne »

_AC-746 - [Problème GitHub](https://github.com/magento/magento2/issues/32784) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/f1adb44e)_

#### La commande « base_row_total » et « row_total » affichent le prix d’un seul article dans la réponse de l’API REST

La réponse de l’api REST pour les détails de la commande contient désormais des valeurs correctes pour les attributs « base_row_total » et « row_total » dans le cas où plusieurs mêmes éléments ont été commandés

_ACP2E-3874 - [contribution du code GitHub](https://github.com/magento/magento2/commit/4ca73607)_

### API, Ordre

#### [CLOUD] Problème d’informations de commande avec l’apparence du total de la ligne pour le 000075568 de commande

Correction du problème en raison duquel la valeur de row_total_incl_tax dans la réponse de l’API de commande était renvoyée comme une valeur résiduelle proche de zéro au lieu de 0,00 lorsqu’un article était entièrement actualisé.

_ACP2E-3950 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/462ede94)_

### Compte

#### Problème lors de la mise à jour de l’e-mail du client dans le Panneau d’administration avec les domaines ö et .swiss

_AC-13409 - [Problème GitHub](https://github.com/magento/magento2/issues/39394) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/d3ea191d)_

#### Le commutateur d’abonnement à la newsletter ne fonctionne pas par site web/magasin.

Le système gère correctement l’abonnement à la newsletter lorsqu’il y a plusieurs sites web/magasins lorsqu’il a été désactivé au niveau mondial

_AC-14283 - [Problème GitHub](https://github.com/magento/magento2/issues/39751) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39752)_

#### [Problème] Suppression de la divulgation des e-mails

Le système affiche désormais Afficher un message d’erreur indiquant un e-mail incorrect si l’e-mail saisi n’est pas nécessaire pour confirmer le compte, que le client existe ou non.

_AC-14561 - [Problème GitHub](https://github.com/magento/magento2/issues/39574) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39570)_

### Interface utilisateur d’administration

#### Les valeurs FPT dans la page de panier et la page de produit sont différentes pour les mêmes configurations pour les produits simples

_AC-13066 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/8953613e)_

#### Les options d’attribut Sélection multiple/Sélection multiple ne peuvent pas être enregistrées lorsque les modules Nuanciers sont désactivés

_AC-13071 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/8953613e)_

#### Les valeurs FPT dans la page de panier et la page de produit sont différentes pour les mêmes configurations pour un produit dynamique

_AC-13075 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/8953613e)_

#### Couleur de pointage non appliquée aux grilles statiques dans l’administration

Les couleurs de survol sont désormais appliquées comme prévu sur les lignes des grilles statiques d’administration.[GitHub-35358](https://github.com/magento/magento2/issues/35358)

_AC-2916 - [Problème GitHub](https://github.com/magento/magento2/issues/35358) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/35384)_

#### [Staging2] Les cartes stockées ne sont pas visibles dans le panneau d’administration.

Correction du problème en raison duquel l’option de paiement « Carte stockée » n’apparaissait plus dans le formulaire de placement de commande du serveur principal après une mise à niveau.

_ACP2E-3830 - [contribution du code GitHub](https://github.com/magento/magento2/commit/7accebfa)_

### B2B

#### la validation du champ entreprise échoue pour le passage en caisse des invités

_AC-14987 - [Problème GitHub](https://github.com/magento/magento2/issues/40011) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/f1adb44e)_

### Bundle

#### Exclure les fichiers JS de l’éditeur global de la sortie groupée sur les thèmes

_AC-15128 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/43648891) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/2bc584af)_

### Panier et passer en caisse

#### Les validations de quantité frontale de produit groupé sont manquantes.

Le système fonctionne maintenant correctement et affiche une erreur de validation lorsque nous tentons d’ajouter une quantité négative et une quantité maximale

_AC-13524 - [Problème GitHub](https://github.com/magento/magento2/issues/39479) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39480)_

#### Préfixe invité non enregistré dans l’adresse de devis 2.4.8

_AC-14705 - [Problème GitHub](https://github.com/magento/magento2/issues/39915) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/f1adb44e)_

#### [Problème] Définissez le prix sur l&#39;article du devis au lieu de prix_de_base

Le système gère correctement le prix de l&#39;article du devis défini sur base_price au lieu du prix si vous avez plusieurs devises dans un site Web sur le front-end

_AC-9985 - [Problème GitHub](https://github.com/magento/magento2/issues/38094) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/36878)_

#### [Cloud] Les commandes récentes n’apparaissent pas dans l’autre vue de magasin si les commandes sont créées sur une vue de magasin.

Correction d’un problème en raison duquel la page « Mon compte » n’affichait pas les commandes récentes provenant d’autres affichages de la boutique dans la même boutique. La logique de récupération des commandes a été mise à jour afin de garantir une visibilité cohérente des commandes dans toutes les vues de la boutique, conformément au comportement de la page « Mes commandes ».

_ACP2E-3807 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a20a6ff2)_

#### qté sous forme  0 dans la section panier client administrateur lors de l’ajout de produits BUNDLE  

La section Panier des Activités clients affiche désormais la quantité correcte. Auparavant, la quantité s’affichait sous la forme 0.

_ACP2E-3872 - [contribution du code GitHub](https://github.com/magento/magento2/commit/3ad96f6a)_

### Panier et passer en caisse, GraphQL

#### Erreur lors du mappage du message au code d’erreur lors de la commande via GraphQL

Les appels GraphQL pour passer une commande pour un panier inexistant ou inactif renvoient désormais correctement les codes d’erreur CART_NOT_ACTIVE ou CART_NOT_FOUND dans toutes les vues du magasin. Cela résout un problème en raison duquel les messages d’erreur traduits entraînaient auparavant un code UNDEFINED.

_ACP2E-3942 - [contribution du code GitHub](https://github.com/magento/magento2/commit/7accebfa)_

### Panier et passer en caisse, GraphQL, Inventaire / MSI

#### L&#39;attribut is_available dans CartItemInterface renvoie la valeur false même lorsque le stock vendable est élevé

L&#39;attribut is_available renvoie la valeur true lorsque le stock vendable est élevé. Auparavant, elle renvoyait toujours la valeur false.

_ACP2E-3885 - [contribution du code GitHub](https://github.com/magento/magento2/commit/3ad96f6a)_

### Catalogue

#### Bogue d’étendue dans la ressource d’URL de catalogue (_getCategories)

Cette requête de modification ajoute une portée de secours à la portée par défaut si aucune valeur n’est définie sur la portée du magasin dans la ressource d’URL de catégorie.

_AC-11011 - [Problème GitHub](https://github.com/magento/magento2/issues/38393) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38394)_

#### [Problème] Vérifiez si OpenGraph peut afficher le prix

Le système fonctionne correctement lorsque nous utilisons le plug-in qui masque le prix et, avec cette modification, le prix n&#39;est pas visible dans la balise OG.

_AC-11635 - [Problème GitHub](https://github.com/magento/magento2/issues/38512) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38510)_

#### [Bug] API REST : la mise à jour des prix spéciaux ne définit pas de valeurs pour toutes les vues de la boutique

_AC-13671 - [Problème GitHub](https://github.com/magento/magento2/issues/39521) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

#### [\Magento\ConfigurableProduct\Model\Product\Type\Configurable] Erreur PHP ignorée

Cette requête de modification modifie le nom d’une variable de boucle afin d’ajouter correctement les données « _cache_instance_product_ids » sur le produit donné à utiliser lors des appels suivants.

_AC-14159 - [Problème GitHub](https://github.com/magento/magento2/issues/39641) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39642)_

#### [Mainline] [CLOUD] Le redimensionnement d’image consomme plus de 400GB d’espace disque

Après le correctif, la commande `catalog:images:resize` utilisée avec l’indicateur —skip_hidden_images ne génère pas de caches d’images pour les sites web où les images ne sont pas présentes.

_ACP2E-3869 - [contribution du code GitHub](https://github.com/magento/magento2/commit/9ad7d277)_

#### L&#39;ID de pays fourni n&#39;existe pas - Irlande (IE)

Après le correctif, des codes postaux irlandais sont disponibles pour rechercher les lieux de retrait.

_ACP2E-3932 - [contribution de code GitHub](https://github.com/magento/magento2/commit/4ca73607) - [contribution de code GitHub](https://github.com/magento/inventory/commit/d2f1d6c6)_

### Catalogue, Performances

#### Les catégories dans l’administration se chargent très lentement

Les performances de chargement des catégories ont été considérablement améliorées. Auparavant, le chargement de la catégorie qui provoquait un problème de délai d’expiration prenait trop de temps.

_ACP2E-3891 - [contribution du code GitHub](https://github.com/magento/magento2/commit/4ca73607)_

### Catalogue, tarification

#### Escompte de règle de prix de catalogue incorrect appliqué au produit enfant

Correction d’un problème en raison duquel la règle de prix de catalogue pour la variation était remplacée par le produit configurable parent, dans le cas où les deux règles avaient la même priorité.

_ACP2E-3693 - [contribution du code GitHub](https://github.com/magento/magento2/commit/a20a6ff2)_

### Catalogue, recherche

#### La requête RestApi « /rest/default/V1/categories?searchCriteria%5Bpage_size%5D=1 » échoue avec une erreur de délai d’expiration

_AC-13358 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

### Contenu

#### Après la mise à niveau vers magento 2.4.7 p2 ne peut pas voir les fichiers récemment chargés galerie de médias

_AC-13262 - [Problème GitHub](https://github.com/magento/magento2/issues/39275)_

#### Lorsque vous supprimez complètement une image de galerie de be, les rôles/types de l’étendue sont conservés (base/small/thumbnail) et, après avoir rajouté les « anciens » rôles/types, s’affichent

Le système fonctionne comme prévu dans les portées de magasin. Les images héritent des rôles/types de la nouvelle image ajoutée selon la portée par défaut

_AC-13556 - [Problème GitHub](https://github.com/magento/magento2/issues/39481) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39680)_

#### [Petit bogue] le filtre du panneau d’administration `listing component` ne peut pas être atteint lorsque la valeur du champ contient `\`

Le système fonctionne correctement lorsque nous filtrons le titre de la page avec une barre oblique (par exemple : Magento\Store)

_AC-13661 - [Problème GitHub](https://github.com/magento/magento2/issues/39513) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39535)_

#### Inondation de journal « La page CMS avec l’ID « 0 » n’existe pas

Le système fonctionne comme prévu après la création d’un utilisateur administrateur et lorsque nous créons une nouvelle page, system.log n’a aucun message d’erreur

_AC-14254 - [Problème GitHub](https://github.com/magento/magento2/issues/39743) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39746)_

#### Les widgets de lien de catalogue utilisent une URL incorrecte

Le système gère désormais correctement les widgets après l’ajout du lien de produit de catalogue et du lien de catégorie de catalogue. Il affiche également les URL correctes dans la source HTML

_AC-14437 - [Problème GitHub](https://github.com/magento/magento2/issues/39464) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39710)_

#### Le composant Produit de Page Builder ne fonctionne pas si l’utilisateur ne dispose pas de l’autorisation Widget

Avant la correction, lors de l’accès à un widget sans autorisations, la page renvoyait une erreur générique et affichait un GIF « chargement ». Désormais, après la correction, une fenêtre modale s’affiche avec « Désolé, vous avez besoin d’autorisations pour afficher ce contenu ». message.

_ACP2E-3664 - [Contribution du code GitHub](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### Ordre du widget de produit Page Builder non appliqué dans GraphQL

Correction du problème en raison duquel la réponse de requête « itinéraire » de GraphQL ne renvoyait pas les produits dans l’ordre de tri correct dans un type de contenu de produits Page Builder.

_ACP2E-3898 - [contribution du code GitHub](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### Problème d&#39;affichage du prix sur les vitrines non anglaises en raison de la version de la bibliothèque ICU

Après la correction, le prix du produit s’affiche correctement dans le paramètre régional Hébreu (Israël).

_ACP2E-3938 - [contribution du code GitHub](https://github.com/magento/magento2/commit/7accebfa)_

#### Mise à jour du code de magasin effacé de la configuration de conception

Correction du problème en raison duquel la mise à jour du code d’affichage du magasin effaçait les paramètres de configuration de conception en raison d’une actualisation incorrecte du cache de configuration.

_ACP2E-3941 - [contribution du code GitHub](https://github.com/magento/magento2/commit/462ede94)_

### Framework

#### Erreur lors de l’exécution de la configuration de commande:upgrade avec le déclencheur de base de données personnalisé

_AC-11487 - [Problème GitHub](https://github.com/magento/magento2/issues/38481)_

#### Le formulaire d’entité de site web/groupe/magasin ne peut pas être étendu avec un élément de formulaire à plusieurs valeurs pour les attributs d’extension

Cette requête d’extraction permet aux éléments de formulaire à plusieurs valeurs d’envoyer des données au formulaire de site web/groupe/magasin.

_AC-11657 - [Problème GitHub](https://github.com/magento/magento2/issues/24070) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/24094)_

#### [Problème] Supprimer l’utilisation du résolveur d’étendue

Cette requête PR résout globalement les paramètres d’URL d’administration au lieu du magasin actuel

_AC-11736 - [Problème GitHub](https://github.com/magento/magento2/issues/38566) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38554)_

#### Exposition de la version de Magento via l’itinéraire d’installation avec la configuration Nginx par défaut

Le système fonctionne maintenant comme prévu et n’expose pas la version exacte de Magento que le site exécute

_AC-13205 - [Problème GitHub](https://github.com/magento/magento2/issues/39227) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39228)_

#### [Problème] refactoriser l’adresse de devis pour valider la méthode

Cette requête d’extraction comprend des améliorations de lisibilité de la méthode doValidate.

_AC-13214 - [Problème GitHub](https://github.com/magento/magento2/issues/38230) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38219)_

#### option Magento : magento-init-params n’est-il jamais utilisé lors de l’exécution de l’interface de ligne de commande ?

_AC-13231 - [Problème GitHub](https://github.com/magento/magento2/issues/39248) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/132b9e68)_

#### Déclaration de type incorrecte de getItemsByColumnValue

Le système définit désormais correctement le paramètre d’entrée $value comme un type primitif, et non comme un tableau, dans la fonction getItemsByColumnValue , en s’assurant que la fonction renvoie la collection attendue. Auparavant, si un tableau avec une seule valeur était utilisé comme paramètre d’entrée, la fonction renvoyait la valeur null et les IDE le marquaient comme une erreur.

_AC-13240 - [Problème GitHub](https://github.com/magento/magento2/issues/33070) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/33120)_

#### Clés de cache associées à FPC sur les implémentations multi-magasin Magento 2.4.7

_AC-13719 - [Problème GitHub](https://github.com/magento/magento2/issues/39456) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/ae6f305b)_

#### API REST Magento exposant les PII

_AC-13904 - [Problème GitHub](https://github.com/magento/magento2/issues/39336)_

#### L’indexation partielle ne fonctionne plus pour les clients qui ont un grand nombre de mises à jour

_AC-14424 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

#### Vérifiez que « use strict » est inutile dans les modules

_AC-14517 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/77c589a6)_

#### Le mécanisme MView ignore silencieusement les erreurs lors de l’exécution du déclencheur

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

#### [Problème] Supprimer le code associé à Microsoft IIS

Ce PR nettoie le code associé à Microsoft IIS conformément à la documentation des exigences du système Magento qui indique que le système d&#39;exploitation Windows Microsoft n&#39;est pas pris en charge

_AC-14702 - [Problème GitHub](https://github.com/magento/magento2/issues/39910) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39894)_

#### Erreur de syntaxe du fichier Magnifier.js

La fonctionnalité Loupe du système doit continuer à fonctionner comme avant et la fonction loupeOptions ne doit pas être disponible dans une portée globale

_AC-14722 - [Problème GitHub](https://github.com/magento/magento2/issues/36200) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39321)_

#### Mode détaillé du rétroportage dans `setup:db:status` commande CLI

_AC-14807 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

#### Envoi d’e-mails SMTP avec tls et 2.4.8

_AC-14883 - [Problème GitHub](https://github.com/magento/magento2/issues/39947) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/3717e6cb) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/8b453942) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/d3ea191d)_

#### [Problème] Correction d’un problème de simultanéité dans le déploiement de contenu statique

Cette requête de résolution corrige un bug en raison duquel plusieurs processus simultanés s’exécutent pour gérer le même package de thème, selon la définition des thèmes avec leurs parents.

_AC-14944 - [Problème GitHub](https://github.com/magento/magento2/issues/39990) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39954)_

#### [Problème] Supprimez le code de compatibilité hérité pour les versions PHP &lt; 8.1

Cette demande de tirage supprime le code conçu pour être exécuté sur PHP &lt;8.1.
En outre, supprimé vérifie la disponibilité des contacts PHP_VERSION_ID, puisqu&#39;il est disponible dans toutes les versions PHP

_AC-14971 - [Problème GitHub](https://github.com/magento/magento2/issues/39891) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39882)_

#### FPC ne fonctionne pas lors de la connexion

_AC-14999 - [Problème GitHub](https://github.com/magento/magento2/issues/40007) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/)_

#### [Problème] amélioration de la gestion des erreurs dans SchemaBuilder

Cette requête d’extraction améliore la gestion des messages d’erreur du schéma de base de données. Cela nous aide à identifier les problèmes sans procéder à un débogage détaillé.

_AC-15020 - [Problème GitHub](https://github.com/magento/magento2/issues/39816) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39799)_

#### Échec du test d&#39;intégration sur SYNC PR pour 2.4.9-alpha2-develop en raison de la modification de CliStateTest

_AC-15136 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/2d0f8066)_

#### Correctif de type PHP8.1

Les produits associés sont désormais initialisés à un tableau vide au lieu de false lorsque le mode de traitement strict n’est pas actif ou lorsque des informations sur les produits sont disponibles. Cette modification garantit que la logique ultérieure traitant les produits associés se comporte de manière cohérente, améliorant la stabilité et la prévisibilité du processus de préparation du produit.

_AC-6017 - [Problème GitHub](https://github.com/magento/magento2/issues/35808) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/35842)_

#### [Problème] Supprimer la balise `@author` interdite du framework (partie 3)

Le système adhère désormais aux normes de codage en supprimant la balise `@author` interdite de certains modules, ce qui améliore la qualité globale du code. Auparavant, la présence de cette balise dans certains modules enfreignait les normes de codage établies.

_AC-8343 - [Problème GitHub](https://github.com/magento/magento2/issues/37270) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37020)_

#### [Problème ] utilisez la promotion de propriété du constructeur dans le module pour envoyer le graphe ami ql

Le système utilise désormais la promotion de propriétés du constructeur dans le module GraphQL « Envoyer un ami », ce qui améliore la lisibilité du code et réduit la complexité. Auparavant, le module utilisait des propriétés qui occupaient de nombreuses lignes, ce qui rendait le code plus complexe et moins lisible.

_AC-8346 - [Problème GitHub](https://github.com/magento/magento2/issues/37235) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37197)_

#### [Problème] Supprimer la balise `@author` interdite de `Magento_Downloadable`

Le système adhère désormais aux normes de codage en supprimant la balise `@author` interdite de certains modules, ce qui améliore la qualité globale du code. Auparavant, la présence de cette balise dans certains modules enfreignait les normes de codage établies.

_AC-8355 - [Problème GitHub](https://github.com/magento/magento2/issues/37251) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37001)_

#### [Problème] Supprimer la balise `@author` interdite

Le système respecte désormais les normes de codage en supprimant la balise `@author` interdite de certains modules, ce qui améliore la qualité et la cohérence du code. Auparavant, la présence de cette balise dans certains modules enfreignait les normes de codage établies.

_AC-8358 - [Problème GitHub](https://github.com/magento/magento2/issues/37264) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37014)_

#### [Problème] Supprimer la balise `@author` interdite

Le système respecte désormais les normes de codage en supprimant la balise `@author` interdite de certains modules, ce qui améliore la qualité globale du code. Auparavant, la présence de cette balise dans certains modules enfreignait les normes de codage établies.

_AC-8360 - [Problème GitHub](https://github.com/magento/magento2/issues/37261) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37011)_

#### [Problème] Supprimer la balise `@author` interdite

Le système respecte désormais les normes de codage en supprimant la balise `@author` interdite de certains modules, ce qui garantit un code plus propre et plus normalisé. Auparavant, la présence de cette balise dans certains modules enfreignait les normes de codage établies.

_AC-8361 - [Problème GitHub](https://github.com/magento/magento2/issues/37260) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37010)_

#### [Problème] Supprimer la balise `@author` interdite

Le système adhère désormais aux normes de codage en supprimant la balise `@author` interdite de certains modules, ce qui améliore la qualité globale du code. Auparavant, la présence de cette balise dans certains modules enfreignait les normes de codage établies.

_AC-8363 - [Problème GitHub](https://github.com/magento/magento2/issues/37258) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37008)_

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

#### Problème de mise à niveau 2.4.7-p5 en raison de l’ajout d’une nouvelle validation

Correction d’un problème dans la classe SchemaBuilder en raison duquel une « colonne » de clé de tableau non définie provoquait un blocage lors de la création ou des mises à jour de schéma. Cela se produisait lors du traitement des données de table qui n&#39;incluaient pas de clé « colonne ».

_ACP2E-3871 - [contribution du code GitHub](https://github.com/magento/magento2/commit/9ad7d277)_

#### Erreur d’obsolescence de PHP8.4 : E_USER_ERROR après la mise à niveau vers Adobe Commerce 2.4.8

Les scénarios concernant les clients et clientes ne sont pas affectés par le correctif.

_ACP2E-3963 - [contribution du code GitHub](https://github.com/magento/magento2/commit/7accebfa)_

### Framework, Recherche

#### Opensearch 2.19.1 legal_argument_exception sur les catégories à prix unique

Opensearch ne lance plus d&#39;exception d&#39;argument illégal_argument_exception sur les catégories contenant tous les produits au même prix. Auparavant, elle comportait l’exception « [from] le paramètre ne peut pas être négatif ».

_ACP2E-3896 - [contribution du code GitHub](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL

#### Les éléments de liste de souhaits ne sont pas partagés entre les vues de magasins dans un site web dans la requête GraphQL.

Avant la correction, les éléments de la liste de souhaits étaient filtrés par ID de magasin. Désormais, après le correctif, les éléments de liste de souhaits sont filtrés par site web.

_ACP2E-3987 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/2a252ae6)_

### GraphQL, Produit

#### Type_média manquant dans l’interface MediaGalleryInterface de GraphQL du produit

La requête GraphQL MediaGallery inclut désormais le champ « types » pour les types d’images de produit. Auparavant, ce champ « types » n’existait pas dans la requête GraphQL MediaGallery.

_ACP2E-3880 - [contribution du code GitHub](https://github.com/magento/magento2/commit/3ad96f6a)_

### Inventaire / MSI

#### Aucun magasin n’est disponible après la redirection vers la page d’accueil et le passage en caisse

Le magasin précédemment sélectionné sera maintenant présélectionné dans l’expédition « Choisir en magasin » si le client accède à la page de paiement, puis revient à la page d’accueil et revient enfin à la page de passage en caisse. Auparavant, après être revenu à plusieurs reprises à la page de passage en caisse, le magasin sélectionné dans « Choisir en magasin » était effacé.

_ACP2E-3793 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a20a6ff2) - [Contribution du code GitHub](https://github.com/magento/inventory/commit/62c0d79b)_

### Ordre

#### AbstractAddress setData(&#39;custom_attributes&#39;, AttributeValue[]) rompt customAttributes

_AC-10568 - [Problème GitHub](https://github.com/magento/magento2/issues/31644)_

#### v2.4.7-p1 Magento reorder -1 numéros de commande

Le système fonctionne comme prévu et, après la réorganisation à partir du serveur principal, le numéro de commande sera unique à 8 chiffres

_AC-12854 - [Problème GitHub](https://github.com/magento/magento2/issues/39089) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39399)_

#### Perte du chargement du fichier d’option personnalisée de produit lors de la récupération avec le mode de paiement par carte de crédit Adobe

_AC-14306 - [Problème GitHub](https://github.com/magento/magento2/issues/39647)_

#### Statut de la commande bloqué lors du traitement

Avant la correction, lors de la commande d’un produit groupé avec l’option « Expédier ensemble » activée, le statut de la commande ne passait pas automatiquement à « terminé » après la facture et l’expédition. Désormais, après correction, le statut de la commande passe automatiquement à « terminé » une fois la commande facturée et expédiée.

_ACP2E-3947 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/2a252ae6)_

#### [Cloud]Code prêt à l’emploi Magento - Problème de configuration du modèle d’e-mail

Avant la correction, lors de l’utilisation de l’envoi asynchrone d’e-mails, les e-mails d’expédition étaient incohérents avec la commande du magasin. Désormais, après le correctif, la commande par e-mail d’expédition de magasin appropriée est livrée.

_ACP2E-3998 - [contribution du code GitHub](https://github.com/magento/magento2/commit/462ede94)_

### Autres outils de développement

#### [Problème ] conseil de type incorrect pour le membre protégé $_urlHelper

Le système corrige désormais le mauvais type hint avec le bon, qui est également utilisé dans le constructeur

_AC-10716 - [Problème GitHub](https://github.com/magento/magento2/issues/32503) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/32496)_

### Performances

#### [Problème] Mettre à jour Store.php

Cette requête d’extraction améliore les performances en ignorant la résolution actuelle du magasin.

_AC-14791 - [Problème GitHub](https://github.com/magento/magento2/issues/39949) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38717)_

### Tarification

#### Le prix est toujours de 0 pour les articles groupés sans prix dynamique dans l’API REST de commande

_AC-11925 - [Problème GitHub](https://github.com/magento/magento2/issues/38687) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/7da46f52)_

### Produit

#### Remise en pourcentage sur le prix de niveau et la règle de prix de catalogue calculée sur le prix d’origine sans les options sélectionnées.

_AC-12004 - [Problème GitHub](https://github.com/magento/magento2/issues/38750)_

#### Magento 2.4.7 minQuantité de commande de produit manquante autorisée

Le système fonctionne correctement et la source de la page affiche correctement la quantité minimale du produit

_AC-12909 - [Problème GitHub](https://github.com/magento/magento2/issues/39142) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39480)_

#### Problème lié à la grille Options personnalisables sur la page produit du panneau d’administration

Le système fonctionne comme prévu lorsque nous créons des options personnalisables avec une liste déroulante de type .

_AC-14003 - [Problème GitHub](https://github.com/magento/magento2/issues/39640) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39694)_

#### Tous les éléments des listes de comparaison des autres clients sont affectés au client après s’être connecté via l’administrateur

Auparavant, lorsqu’un administrateur utilisait la fonctionnalité « Connexion en tant que client » sur le serveur principal, les produits de la liste de comparaison d’un client précédemment connecté étaient incorrectement affectés au client dont l’identité est actuellement empruntée.  Une fois la correction effectuée, la liste de comparaison se charge correctement pour le client connecté approprié.

_ACP2E-3818 - [contribution du code GitHub](https://github.com/magento/magento2/commit/462ede94)_

### SEO

#### Mettre à jour la clé_URL du produit via l’API REST ne génère pas de réécriture d’URL 301

Lors de la mise à jour de la clé URL du produit via l’API REST, avec le paramètre « Créer une redirection permanente pour les URL en cas de modification de la clé URL » défini sur Oui, les réécritures d’URL de produit sont créées pour rediriger l’ancienne URL vers une nouvelle.

_ACP2E-3900 - [contribution du code GitHub](https://github.com/magento/magento2/commit/462ede94)_

### Sécurité

#### JS groupés/fusionnés ne faisant pas partie des hachages SRI

Avant la correction, le lot généré ou les fichiers fusionnés n’étaient pas ajoutés à la liste des hachages SRI. Désormais, les fichiers sont correctement ajoutés aux hachages SRI.

_ACP2E-3854 - [contribution du code GitHub](https://github.com/magento/magento2/commit/4ca73607)_

### Expédition

#### [QUANS] - Le module principal Magento_Fedex vérifie-t-il la validité d’un jeton actif avant d’envoyer une demande pour en obtenir un nouveau ?

Adobe Commerce n’effectue plus de nombreuses requêtes au service d’API FedEx pour le jeton d’accès. Auparavant, même si le jeton d’accès était toujours valide, Adobe Commerce envoyait toujours de nouvelles requêtes à l’API FedEx, ce qui provoquait un problème de limitation de débit.

_ACP2E-3930 - [contribution du code GitHub](https://github.com/magento/magento2/commit/4ca73607)_

### Évaluation et prévisualisation

#### Impossible de prévisualiser la mise à jour de produit planifiée avec les autorisations de catégorie activées

Avant la correction, un produit futur à activer n’était pas affiché en mode Aperçu. Désormais, il s’affiche même si le statut actuel est désactivé.

_ACP2E-3786 - [contribution du code GitHub](https://github.com/magento/magento2/commit/7accebfa)_

#### Validation manquante pour le champ du montant de remise de la règle de prix du catalogue

Auparavant, le champ discount_amount de la mise à jour du planning d&#39;évaluation n&#39;était pas validé correctement avec les règles de validation actuelles. Cependant, après application du correctif, le champ discount_amount sera validé de manière appropriée.

_ACP2E-3867 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/462ede94)_

### Taxe

#### Mauvais total de commande, l&#39;arrondi n&#39;est pas appliqué au calcul du prix.

Le système est désormais correctement géré lors du calcul du montant price_after_discount, discount_amount et taxes.
total réel de la commande

_AC-11389 - [Problème GitHub](https://github.com/magento/magento2/issues/38455) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39687)_

### Framework de test

#### [Problème ] ignorer lib/internal/Magento/Framework/App/Test/Unit/_files/app/etc/en...

Le système ignore désormais le fichier « env.php » qui est généré lors de l’exécution de tests unitaires, ce qui garantit que le statut Git reste correct après l’exécution des tests. Auparavant, l’exécution de tests unitaires générait un nouveau fichier « env.php », ce qui entraînait l’affichage d’un nouveau fichier dans le statut Git et donnait l’impression qu’il était sale.

_AC-13293 - [Problème GitHub](https://github.com/magento/magento2/issues/39304) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37631)_

#### [Problème] Correction du problème de test d’intégration avec l’intercepteur

Le système identifie et gère désormais correctement le fichier \Magento\TestFramework\App\Config\Interceptor dans le test d’intégration, en veillant à ce que le test puisse accéder aux données nécessaires même s’il existe un plug-in sur la classe . Auparavant, le système ne tenait pas compte de la possibilité que \Magento\TestFramework\App\Config soit un \Magento\TestFramework\App\Config\Interceptor, ce qui entraînait une erreur lors de la tentative d’accès à la propriété $data.

_AC-13305 - [Problème GitHub](https://github.com/magento/magento2/issues/39324) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37187)_

#### [Problème] MFTF : envoi d&#39;un e-mail à un formulaire d&#39;ami avec captcha activé

Le cas de test traite de la fonctionnalité du formulaire « Envoyer à un ami » lorsque CAPTCHA est activé, en s’assurant que le processus d’envoi du formulaire fonctionne correctement avec des valeurs CAPTCHA incorrectes et correctes.

_AC-13492 - [Problème GitHub](https://github.com/magento/magento2/issues/39462) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/32830)_

#### [TestFramework] Les utilisations de TestCase::getTestResultObject ne sont pas valides depuis phpunit v10

_AC-13502 - [Problème GitHub](https://github.com/magento/magento2/issues/39463)_

#### Défaillances des tests unitaires spécifiques à l’environnement dans AC 2.4.7-p3

Ce problème corrige les échecs de test unitaire qui ne se reproduisent pas sur toutes les versions et tous les environnements. Auparavant, certains tests unitaires ont échoué en raison de versions de bibliothèque différentes ou d’une fonctionnalité manquante ajoutée dans une version ultérieure.

_ACP2E-3712 - [contribution du code GitHub](https://github.com/magento/magento2/commit/9ad7d277)_

### Framework de l’interface utilisateur

#### WYSIWYG est vide dans les lignes dynamiques

_AC-12336 - [Problème GitHub](https://github.com/magento/magento2/issues/38893) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

#### [Problème] Correction de la faute de frappe de type MIME

Le système gère et corrige correctement le type MIME et la faute de frappe pour l’image gif

_AC-8001 - [Problème GitHub](https://github.com/magento/magento2/issues/36899) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/36669)_

#### [Problème] Évitez l&#39;accès direct à la liste des avis Ajax

Le système gère correctement et évite l&#39;accès direct à la liste des avis Ajax

_AC-9381 - [Problème GitHub](https://github.com/magento/magento2/issues/37920) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/33876)_

### Mises à niveau - Outil de compatibilité de mise à niveau

#### Fonctionnalité obsolète : création de la propriété dynamique Magento\Framework\Acl::$_roleRegistry

_AC-12343 - [Problème GitHub](https://github.com/magento/magento2/issues/37469)_
