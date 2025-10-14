---
source-git-commit: 151272eed6c4bb2e1c2e5138a5c8a3a7e7bd8fe6
workflow-type: tm+mt
source-wordcount: '6077'
ht-degree: 0%

---
# Problèmes résolus dans Adobe Commerce (v2.4.9-alpha3)

## Correction de problèmes dans v2.4.9-alpha3

Nous avons corrigé 129 problèmes dans le code principal 2.4.9-alpha3 d’Adobe Commerce. Un sous-ensemble des problèmes résolus inclus dans cette version est décrit ci-dessous.

### API

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

#### Le point d’entrée de l’API REST export-stock-salable-qty renvoie des éléments incorrects total_count

Correction d’un problème de pagination dans l’API de quantité vendable de stock d’exportation de stock où total_count était incorrectement limité à la taille de la page. Auparavant, lorsque vous utilisiez le point d’entrée /rest/all/V1/inventory/export-stock-salable-qty/website/base avec des paramètres de pagination tels que page_size=5, le champ total_count de la réponse renvoyait 5 au lieu du nombre total réel de produits correspondant aux critères de recherche. Après ce correctif, le champ total_count reflète désormais correctement le nombre total de produits disponibles, quel que soit le paramètre page_size , ce qui garantit un comportement de pagination cohérent sur tous les points d’entrée de l’API REST Magento.

_ACP2E-4086 - [contribution du code GitHub](https://github.com/magento/inventory/commit/5632fb5e)_

#### Un attaquant peut utiliser la requête POST à l’aide de l’API REST et envoyer une payload RCE

Les API REST V1/guest-carts/&lt;cartId>/items/ et V1/carts/mine/items/ valident désormais « product_options.extension_attributes.custom_options ».*.option_id » pour être valide option_id dans le SKU de l’article du panier. Auparavant, cette option était traitée et enregistrée dans la base de données sans validation.

_ACP2E-4138 - [contribution du code GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

### Compte

#### [Problème] Suppression de l’espacement inutile sur la grille du serveur principal

Le système supprime désormais l’espacement inutile dans la grille du serveur principal lorsque des éléments sont sélectionnés

_AC-11579 - [Problème GitHub](https://github.com/magento/magento2/issues/38502) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/32622)_

#### Impossible d’effacer le commentaire d’élément de la liste de souhaits via `updateProductsInWishlist` mutation GraphQL

Correction d’un problème en raison duquel les commentaires de la liste de souhaits n’étaient pas mis à jour via les mutations de GraphQL.
Désormais, les commentaires sont correctement mis à jour et répercutés dans la réponse de l’API et dans le storefront.

_AC-14682 - [Problème GitHub](https://github.com/magento/magento2/issues/39911) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

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

#### Problème après connexion dans magento 2.4.8-p1

Correction d’un problème sur Magento 2.4.8-p1 en raison duquel le lien « Créer un compte » était toujours visible sur la page d’accueil après la connexion.
Désormais, le lien est correctement masqué après la connexion, ce qui est cohérent avec les autres pages.

_AC-15292 - [Problème GitHub](https://github.com/magento/magento2/issues/40120)_

### Interface utilisateur d’administration

#### [Problème] remplacer l’échappement obsolète

Cette requête PR supprime l’échappement obsolète () et l’ajoute par injection de constructeur

_AC-15132 - [Problème GitHub](https://github.com/magento/magento2/issues/40062) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38135)_

#### Message de bienvenue qui chevauche la catégorie de produits dans la vue mobile.

Correction d’un problème de l’interface utilisateur en raison duquel le nom de bienvenue chevauchait des catégories de produits dans la vue mobile, bloquant les clics.
Désormais, les catégories sont entièrement visibles et cliquables sans problèmes de chevauchement.

_AC-15166 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/1b1baf1d)_

#### « Impossible de résoudre les entrées du paramètre reCAPTCHA » dans exception.log pour le panneau d’administration reCAPTCHA de Google

Une erreur reCaptcha dans le fichier `var/log/exception.log` pour la connexion d’administrateur reCAPTCHA de Google V3 a été résolue, et aucun message d’erreur n’est consigné. Auparavant, l’erreur suivante était générée toutes les quelques secondes lorsqu’un utilisateur administrateur configurait les paramètres **Configuration** > **Sécurité** > **Panneau d’administration reCAPTCHA de Google** : `main.ERROR: Can not resolve reCAPTCHA parameter. {&quot;exception&quot;:&quot;[object] (Magento\Framework\Exception\InputException(code: 0): Can not resolve reCAPTCHA parameter. at /home/xxxxxxx/public_html/vendor/magento/module-re-captcha-ui/Model/CaptchaResponseResolver.php:25)&quot;} []`.  [GitHub-34975](https://github.com/magento/magento2/issues/34975)

_AC-3179 - [Problème GitHub](https://github.com/magento/magento2/issues/34975) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/4f7e5983) - [Contribution du code GitHub](https://github.com/magento/security-package/commit/804dbc2a)_

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

_ACP2E-4052 - [contribution du code GitHub](https://github.com/magento/magento2/commit/52f46328)_

### Interface utilisateur d’administration, fiscalité

#### Erreur de l’interface utilisateur d’administration du taux de taxe

Ce ticket a corrigé un problème d’interface utilisateur d’administration du taux d’imposition en raison duquel le changement de pays (par exemple, des États-Unis → du Royaume-Uni) affichait toujours l’état des États-Unis sélectionné précédemment, induisant les utilisateurs en erreur.
Dans la version 2.4.9-alpha3, le champ État est désormais réinitialisé sur * lorsque le pays sélectionné n’a pas d’État.

_AC-8440 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

### B2B

#### Rest API products-render-info renvoie un prix final incorrect pour le client connecté

Le ticket comporte un correctif pour API REST products-render-info qui renvoie un prix final incorrect pour le client connecté

_AC-5979 - [Problème GitHub](https://github.com/magento/magento2/issues/35757) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/)_

#### Le bouton Ajouter à la liste des demandes d&#39;approvisionnement disparaît lorsque nous essayons de l&#39;ajouter à partir de la page Catégorie

Le bouton Précédent Ajouter à la liste des demandes d&#39;approvisionnement disparaît lorsque nous essayons de l&#39;ajouter à partir de la page Catégorie qui est maintenant corrigée et nous pouvons voir le bouton de demande d&#39;approvisionnement sur la page Catégorie

_AC-8575_

### B2B, panier et passage en caisse

#### Aucune entité de ce type avec cartId = X erreur ne s’affiche sur Storefront lors de la connexion à l’utilisateur de la société B2B à partir de la fonctionnalité d’administration « Connexion en tant que client »

Désormais, l’erreur « Aucune entité de ce type avec cartId = X » n’est plus visible après la connexion réussie à partir du serveur principal d’administration lors de l’utilisation de la fonctionnalité « Connexion en tant que client ».

_ACP2E-3994 - [contribution du code GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

### Panier et passer en caisse

#### [Problème] Ajoutez EventPrefix et EventObject au modèle de contrat d’extraction

Le système inclut désormais EventPrefix et EventObject pour le modèle de contrat de passage en caisse, ce qui permet de déclencher les événements avec un préfixe d’événement. Cette amélioration offre davantage de flexibilité aux développeurs lorsqu’ils travaillent avec des événements d’accord de passage en caisse. Auparavant, le modèle d’accord de passage en caisse ne prenait pas en charge EventPrefix et EventObject, ce qui limitait la possibilité de personnaliser la gestion des événements.

_AC-13252 - [Problème GitHub](https://github.com/magento/magento2/issues/32510) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/32451)_

#### [Graphql] Impossible de renvoyer la valeur null pour le champ « SelectedCustomizableOption.label » qui n’accepte pas les valeurs Null

Le système ne renvoie plus d’erreur de serveur interne avec le message lorsque l’option sélectionnée n’existe plus

_AC-14256 - [Problème GitHub](https://github.com/magento/magento2/issues/39729) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39888)_

#### [2.4.8] Impossible de passer des commandes lorsque la ville comporte les chiffres 0 à 9, l&#39;esperluette, un point ou une parenthèse dans le nom de la ville

Correction d’un problème en raison duquel le passage en caisse échouait pour les noms de ville contenant des caractères spéciaux tels que . , &amp;, ou des parenthèses.
Désormais, les commandes avec ces noms de ville sont passées sans erreurs de validation.

_AC-14495 - [Problème GitHub](https://github.com/magento/magento2/issues/39854) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### La sous-sélection de règle de vente avec la condition Quantité ne s&#39;applique pas

Correction d’un problème en raison duquel les règles de prix de panier avec des conditions de sous-sélection de produit ne s’appliquaient pas au passage en caisse.
Désormais, les remises sont appliquées conformément aux règles configurées.

_AC-14884 - [Problème GitHub](https://github.com/magento/magento2/issues/39965) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/fe72c407)_

#### Graphql - Le panier de fusion ne fonctionne pas correctement lorsque la commande Backorder est activée

Correction d’un problème en raison duquel les articles du panier d’invités n’étaient pas fusionnés avec le panier client lors de la fusion du panier via GraphQL.
Désormais, le panier client reflète correctement la quantité combinée des paniers client et invité.

_AC-15148 - [Problème GitHub](https://github.com/magento/magento2/issues/40064) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### [Intégration] [Passage en caisse] directives dépendantes mises à jour dans le modèle d’e-mail de paiement ayant échoué

Modèle d&#39;e-mail de paiement en échec mis à jour pour gérer correctement les directives dépendantes.
Correction garantit que l’adresse et le mode d’expédition s’affichent correctement, le cas échéant.
Auparavant, ces champs étaient manquants dans les e-mails de paiement en échec.

_AC-15363 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

#### [Cloud] réduction sur la livraison gratuite non correctement supprimée lorsque le panier ne répond plus aux exigences

Le Sous-Total (Hors Taxe) dans la règle de prix de panier incorporera désormais les remises des règles précédentes.

_ACP2E-3973 - [contribution du code GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Commande en double trouvée pour le même client dans Multishipping

Les demandes simultanées de passation de commande avec plusieurs adresses d’expédition n’entraînent plus de commandes dupliquées pour un même client

_ACP2E-4117 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

### Panier et passer en caisse, commande, produit

#### L&#39;e-mail de carte cadeau est envoyé même si la facture de commande échoue

Avant la mise en œuvre de ce correctif, les e-mails de carte cadeau étaient envoyés après la création de la facture. Cependant, une fois le correctif appliqué, les e-mails de carte cadeau sont désormais envoyés une fois les factures enregistrées et validées.

_ACP2E-3905_

### Panier et passage en caisse, sécurité

#### [CLOUD] Obtention du fichier 404 pour JS sur la page de passage en caisse à la première tentative après l’implémentation du correctif SRI

Avant la correction, les mixins n’avaient pas été chargés dans le panier et lors du passage en caisse lorsque la miniaturisation et le regroupement étaient activés. Après le correctif, tous les mixins doivent se charger comme prévu.

_ACP2E-4128 - [contribution du code GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

### Catalogue

#### Problèmes de prix et de config.php

Dans Magento 2.4.2, la modification du périmètre de prix via config.php ne met pas correctement à jour la valeur is_global dans catalog_eav_attribute pour l’attribut de prix.
Par conséquent, les prix des produits restent globaux et ne peuvent pas être enregistrés par site web, même si la portée du prix est définie sur site web.
La solution nécessite la mise à jour manuelle de la colonne is_global dans la base de données, ce qui n’est pas idéal pour les environnements de production.
Ce comportement est cohérent avec la conception par défaut de Magento, où la portée du prix est soit Globale soit Site Web, mais pas par vue de magasin.

_AC-13857 - [Problème GitHub](https://github.com/magento/magento2/issues/33559)_

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

#### La génération d’images dynamiques génère un grand nombre d’images

Après la correction, les images seront générées uniquement pour les sites web auxquels le produit est affecté.

_ACP2E-3927 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/fab20b00)_

#### Une erreur 500 se produit sur le front-end, car une structure de disposition incorrecte est mise en cache dans la disposition

Correction d’un problème en raison duquel une page renvoyait un code d’erreur 500 en raison d’une structure de mise en page incorrecte mise en cache dans la mise en page

_ACP2E-4040 - [contribution du code GitHub](https://github.com/magento/magento2/commit/47721be6)_

#### Erreur de validation pour le champ du montant de remise de la règle de prix du catalogue dans la mise à jour planifiée

Auparavant, avant de résoudre ce problème, pour la mise à jour de programme de la règle de prix catalogue, si le montant de remise est by_fixed, il n&#39;a pas été validé correctement en raison de la règle validation-numéro-fourchette. Une fois ce correctif appliqué, la validation fonctionne correctement pour la règle de prix catalogue fixe.

_ACP2E-4054 - [contribution du code GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Les produits s’affichent comme étant en rupture de stock après désactivation

Après le correctif, les produits désactivés ne sont pas présents dans le widget de produits.

_ACP2E-4136 - [contribution du code GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [Cloud] Erreurs avec entrées en double (temp_category_descendants_%)

Correction d’un problème lié aux entrées en double lors des mises à jour planifiées de création pour les environnements comportant un grand nombre de catégories imbriquées

_ACP2E-4159 - [contribution du code GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

### Catalogue, GraphQL

#### Calcul de remise GraphQl non valide

GraphQL affiche désormais correctement les pourcentages de remise et les prix de base lorsque les prix de catalogue sont configurés pour inclure la taxe. Auparavant, des erreurs d’arrondi se produisaient, par exemple l’affichage de 19,99 % au lieu de 20 %.

_ACP2E-3993 - [contribution du code GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

### Catalogue, produit

#### Produits associés via la règle de produit associé ne s’affichant pas dans PDP via GraphQL

Auparavant, avant l’application de ce correctif, la règle de produit relatif renvoyait une valeur vide/nulle pour un produit correspondant à la règle. Une fois ce correctif appliqué, la règle relative pour les produits correspondants est renvoyée avec succès.

_ACP2E-3949_

### Contenu

#### graphql (magento 2.4.6-p4 ) : erreur lors de la tentative d’obtention d’une page cms dont le statut est inactif

Correction d’un problème en raison duquel la requête GraphQL sur une page CMS désactivée renvoyait une erreur de serveur interne.
Désormais, la requête récupère une réponse appropriée sans erreur.

_AC-12302 - [Problème GitHub](https://github.com/magento/magento2/issues/38877) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/1b1baf1d)_

#### [GraphQl] Boucle infinie de requête d’itinéraire

Ce ticket corrige le problème où une requête d’itinéraire GraphQL avec un chemin de requête et un chemin de cible identiques provoquait une boucle infinie et expirait par la suite.
Dans la version 2.4.9-alpha3, la requête renvoie désormais la réponse d’erreur correcte au lieu de faire une boucle.

_AC-14269 - [Problème GitHub](https://github.com/magento/magento2/issues/39707) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### Pour plus de flexibilité, définissez la constante IMAGE_FILE_NAME_PATTERN sur public visible

La constante IMAGE_FILE_NAME_PATTERN dans GenerateRenditions.php a été rendue publique pour permettre aux développeurs plus de flexibilité lors de l&#39;utilisation de rendus d&#39;image. Le correctif est inclus dans Magento 2.4.9-alpha3 avec une couverture d&#39;unité complète et de test d&#39;intégration.

_AC-15338 - [Problème GitHub](https://github.com/magento/magento2/issues/39733) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### L’aperçu de l’évaluation du contenu ne fonctionne pas avec les résultats de recherche

La recherche dans l’aperçu intermédiaire renvoie désormais des produits en fonction de la portée sélectionnée. Auparavant, la recherche renvoyée affichait les résultats dans la portée par défaut, sans tenir compte du magasin sélectionné.

_ACP2E-4095_

#### Page Builder - Problème de logique de condition du produit (la logique OU se comporte incorrectement en affichant moins de produits)

Le widget Produits de Page Builder renvoie désormais un résultat correct lorsqu’un attribut avec une portée globale est utilisé dans la condition « Ne correspond à aucun »

_ACP2E-4096 - [contribution du code GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

### Client/Clients

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

#### [Problème] Rendre la signature de méthode cohérente avec l’interface

La signature de méthode pour getAttributes est désormais cohérente avec son interface, ce qui empêche toute erreur lors du remplacement de la méthode. Auparavant, les incohérences dans la signature de méthode provoquaient des erreurs lors de la tentative de remplacement de la méthode getAttributes.

_AC-11578 - [Problème GitHub](https://github.com/magento/magento2/issues/38501) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/31955)_

#### [Problème] Correction de la règle validate-emails pour le composant de l’interface utilisateur

Le système valide désormais correctement plusieurs adresses e-mail saisies dans les composants de l’interface utilisateur, en s’assurant que chaque adresse e-mail est correctement tronquée et validée. Auparavant, le système utilisait une méthode incorrecte pour supprimer les adresses e-mail, ce qui pouvait entraîner des erreurs de validation.

_AC-11719 - [Problème GitHub](https://github.com/magento/magento2/issues/38528) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/33470)_

#### [Problème] Supprimer les méthodes redondantes

Qualité du code : suppression des méthodes redondantes dans les composants Opérations asynchrones et Ventes qui appelaient uniquement des méthodes parentes sans ajouter de fonctionnalité, ce qui améliore la facilité de maintenance du code.

_AC-11915 - [Problème GitHub](https://github.com/magento/magento2/issues/29748) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/29147)_

#### la validation xsd échoue sur les fichiers etc/adminhtml/system.xml qui contiennent des commentaires sous les éléments de champ.

Ce PR corrige les définitions de schéma XML dans phpstorm pour le nœud comment

_AC-12945 - [Problème GitHub](https://github.com/magento/magento2/issues/39148) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39867)_

#### Magento 2.4.8 utilise des packages de développement qui ne respectent pas le contrôle de version sémantique

Magento 2.4.8 nécessite les versions de développement de pdependance/pdependance et phpmd/phpmd (3.x-dev) pour la compatibilité avec PHP 8.4.
Ces versions de développement entrent en conflit avec les outils tiers qui attendent des packages compatibles avec SemVer, empêchant certaines mises à niveau.
Une solution temporaire consiste à alias les versions de développement dans composer.json (par exemple, « 3.x-dev as 3.99.0 »), ce qui permet une compatibilité tout en respectant le contrôle de version sémantique.
Cela garantit la prise en charge de PHP 8.4 et évite les conflits jusqu&#39;à ce que des versions stables soient disponibles.

_AC-14519 - [Problème GitHub](https://github.com/magento/magento2/issues/39796)_

#### API REST : appel à une fonction membre getVideoProvider() sur null

Correction d’un problème en raison duquel l’appel de l’API enfant du produit configurable renvoyait une erreur de serveur interne 500 si un produit enfant n’avait qu’une vidéo YouTube et aucune autre image.
L’erreur est due à une référence nulle dans ExternalVideoEntryConverter.
Désormais, l’API renvoie correctement les produits enfants avec des entrées de galerie multimédia, y compris des données vidéo externes, sans générer d’erreurs.
Cela permet de récupérer correctement tous les types de médias pour les produits enfants via l’API REST.

_AC-15046 - [Problème GitHub](https://github.com/magento/magento2/issues/40021)_

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

#### Mettre à jour les fichiers Lisez-moi du module et corriger les liens vers les documents

_AC-15340 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/ec9459d0)_

#### [Problème] Ne consignez le plug-in non déclaré que s’il n’est pas désactivé

Cette requête d’extraction corrige et consigne les plug-ins qui ne sont pas déclarés et qui ne sont pas utilisés (instance activée et manquante).

_AC-15386 - [Problème GitHub](https://github.com/magento/magento2/issues/40086) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40081)_

#### Magento 2.4.8-p2, magento/framework version 103.0.8-p2 : classe EmailMessage appelant une méthode inexistante

_AC-15446 - [Problème GitHub](https://github.com/magento/magento2/issues/40170) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/059fd469) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/e9412b24)_

#### [Les correctifs de données/schémas de Magento 2.3.x] getAliases() provoquent des erreurs lors de l’`setup:upgrade`

getAliases() provoque des erreurs lors de la configuration:upgrade, ce PR les corrige

_AC-15559 - [Problème GitHub](https://github.com/magento/magento2/issues/31396) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38239)_

#### Type attendu &#39;Magento\Customer\Api\Data\GroupInterface&#39;. &#39;Magento\Customer\Model\Group&#39; trouvé.

Correction d’un problème en raison duquel l’enregistrement d’un groupe de clients via GroupRepositoryInterface à l’aide de GroupFactory provoquait une erreur de type.
Auparavant, le référentiel attendait GroupInterface, mais les instances de modèle de groupe étaient transmises, ce qui entraînait une erreur irrécupérable.
Désormais, les groupes de clients peuvent être enregistrés via le référentiel en assurant une implémentation correcte de l’interface.
Cela résout les avertissements IDE et les erreurs d’exécution lors de la création ou de la mise à jour par programmation de groupes de clients.

_AC-6909 - [Problème GitHub](https://github.com/magento/magento2/issues/36269)_

#### [Problème] Supprimer la balise `@author` interdite

Cette requête d’extraction supprime `@author` balise de la base de code

_AC-8349 - [Problème GitHub](https://github.com/magento/magento2/issues/37266) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37016)_

#### [Problème] Supprimer la balise `@author` interdite

Cette requête d’extraction supprime `@author` balise de la base de code

_AC-8350 - [Problème GitHub](https://github.com/magento/magento2/issues/37265) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37015)_

#### [Problème] Supprimer la balise `@author` interdite

Cette requête d’extraction supprime `@author` balise de la base de code

_AC-8359 - [Problème GitHub](https://github.com/magento/magento2/issues/37262) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37012)_

#### [Problème] Supprimer la balise `@author` interdite

Cette requête d’extraction supprime `@author` balise de la base de code

_AC-8362 - [Problème GitHub](https://github.com/magento/magento2/issues/37259) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37009)_

#### [Problème] Supprimer la balise `@author` interdite de `Magento_Backup` et `Magento_Bundle`

Cette requête d’extraction supprime `@author` balise de la base de code

_AC-8367 - [Problème GitHub](https://github.com/magento/magento2/issues/37244) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/36979)_

#### [Problème] Correction du nom de variable dans la recherche de catalogues

Le système nomme désormais correctement les variables dans le module du moteur de recherche, ce qui améliore la clarté du code et la facilité de maintenance. Auparavant, un nom de variable non pertinent, $defaultCountry, était utilisé dans le module du moteur de recherche, ce qui entraînait de la confusion.

_AC-9215 - [Problème GitHub](https://github.com/magento/magento2/issues/37810) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/33533)_

#### Problème [QUANS]Server potentiellement causé par une clé d’accès S3 non valide

Des informations d’identification AWS S3 incorrectes ne provoquent plus le chargement infini des pages sur le storefront.

_ACP2E-3890 - [contribution du code GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

#### [QUANS] [Cloud] Minify ne fonctionne pas

Les fichiers JS suivants sont désormais entièrement et correctement minimisés lorsque la minimisation JS est activée : mage/backend/tabs.min.j, jquery/jquery.validate.min.js et Magento_PageBuilder/js/form/element/validator-rules-mixin.min.js. Par conséquent, la validation des champs de classe CSS de Page Builder fonctionne comme prévu.

_ACP2E-3925 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/47721be6)_

#### La tâche cron n’efface pas la table de base de données, ce qui entraîne une panne de la Galera.

Le nettoyage des tables de journaux des modifications s’exécute désormais par lots pour éviter des opérations de suppression importantes.

_ACP2E-3995 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/52f46328)_

#### Le JS non miniaturisé se charge parfois en ignorant « activer les minifications js »

Avant la correction, même si la minimisation était activée, certains fichiers JS étaient demandés sans le préfixe « min », ce qui entraînait l’apparition du code d’état 404. Après le correctif, lorsque la minimisation est activée, aucune ressource JS non minimisée n’est demandée.

_ACP2E-4058 - [contribution du code GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Échec de l’affichage du sélecteur de date dans Admin dans le groupe d’attributs personnalisé

Correction d’un problème en raison duquel la fenêtre contextuelle de calendrier des attributs de date s’affichait hors écran lorsqu’elle était affectée à des groupes d’attributs personnalisés.

_ACP2E-4060 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

### GraphQL

#### GraphQL de commande client : la récupération des catégories de produits pour le produit associé n’est « pas visible individuellement ».

Avant la correction, si la commande contenait un produit masqué, ses catégories affichaient un tableau vide dans la réponse GraphQl de commande client.
Désormais, après la correction, les catégories de produits sont incluses dans la réponse d’une requête GraphQl de commande client même si le produit est masqué.

_ACP2E-3945 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

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

### GraphQL, Inventaire / MSI

#### Incohérences de mutation mergeCart GraphQL

Après le correctif, la demande GraphQL de panier de fusion vérifie correctement la quantité de produit, en prenant en compte la configuration du stock.

_ACP2E-4184 - [contribution du code GitHub](https://github.com/magento/inventory/commit/5632fb5e)_

### GraphQL, Sécurité

#### La réinitialisation du mot de passe du client via GraphQL ne respecte pas les restrictions

Correction d’un problème en raison duquel les demandes de réinitialisation de mot de passe client effectuées par le biais de mutations de GraphQL ne respectaient pas les restrictions de réinitialisation de mot de passe configurées sous Stocker > Configuration > Clients > Configuration client > Options de mot de passe. Ces paramètres sont désormais correctement appliqués.

_ACP2E-3992 - [contribution du code GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

### Importer/exporter

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

### Inventaire / MSI

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

### Ordre

#### Magento 2.4.8 GraphQL - Mise en forme incorrecte des éléments de commande order_date

Correction d’un problème en raison duquel le champ order_date dans la réponse GraphQL était renvoyé au format aaaa-mm-jj.
Désormais, order_date s’affiche correctement au format jj-mm-aaaa.

_AC-14431 - [Problème GitHub](https://github.com/magento/magento2/issues/39805) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### L’e-mail d’expédition n’est pas envoyé lorsqu’il est envoyé à partir de la vue Commande admin bien qu’activé dans la configuration du magasin

Le système envoie désormais un e-mail de confirmation d’expédition, car il est activé dans la configuration du magasin où la commande a été passée.

_AC-14563 - [Problème GitHub](https://github.com/magento/magento2/issues/39861) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39897)_

#### Le filtrage sur la date ne fonctionne pas en raison de noms de champ ambigus

Dans Magento 2.4.7-p6, le filtrage de la grille d’ordre par date a été signalé comme provoquant une erreur en raison de jointures avec les modules Braintree.
Le problème impliquait des requêtes joignant les tables braintree_transaction_details et sales_order lors de l&#39;application de filtres de date.
L’ingénierie Adobe Commerce a examiné le cas, mais n’a pas pu reproduire l’erreur dans l’environnement.
Le filtrage par date devrait renvoyer les commandes correspondant au filtre sans erreur.

_AC-15037 - [Problème GitHub](https://github.com/magento/magento2/issues/40024)_

#### Magento2 : impossible de créer la règle de promotion

Ce correctif de relations publiques, on a
Modèle \Magento\Catalog\Model\ResourceModel\Eav\Attribute au lieu de \Magento\Catalog\Model\ResourceModel\Eav\Attribute dans la méthode \Magento\SalesRule\Model\Rule\Condition\Product::loadAttributeOptions

_AC-15358 - [Problème GitHub](https://github.com/magento/magento2/issues/12176) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/30479)_

#### Annuler les redirections de facture vers 404

L&#39;annulation de la facture effectuée avec le type Not Capture ne mène plus à la page 404.

_ACP2E-4001 - [contribution du code GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Les tâches d’archivage des ventes provoquent des problèmes de verrouillage de la base de données

Avant le correctif, les requêtes DELETE non liées situées dans l’archive cron provoquaient des problèmes avec Galera. Désormais, après la mise à jour, les requêtes de suppression sont exécutées avec des limites.

_ACP2E-4010_

#### Problème lié aux commandes mises à jour avec des options configurables à l’aide de l’API REST

Conservez les options de produit existantes sur les articles de commande client lors de la mise à jour d’une commande via les points d’entrée de l’API REST.

_ACP2E-4061 - [contribution du code GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

### Autres outils de développement

#### [Problème] Nettoyage du code inutilisé.

Le système supprime désormais le code inutilisé concernant les importations inutilisées.

_AC-10980 - [Problème GitHub](https://github.com/magento/magento2/issues/38424) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/33499)_

#### [Problème] Accessibilité : les rôles WAI-ARIA s’imbriquent mal dans le menu

Le système génère désormais l’accessibilité lighthouse sans que les rôles WAI-ARIA ne s’imbriquent mal dans l’erreur de menu et le rapport doit être vert

_AC-15082 - [Problème GitHub](https://github.com/magento/magento2/issues/40045) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38617)_

#### Erreur de console dans l’aperçu d’e-mail de l’administrateur Magento

Le système ne renvoie aucune erreur de console lors de la prévisualisation du modèle d’e-mail

_AC-9245 - [Problème GitHub](https://github.com/magento/magento2/issues/37820) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37933)_

### Paiements

#### Des adresses IP inconnues de PayPal abusent du processeur IP de l&#39;application

Le gestionnaire d’adresses IP ignore désormais les types d’adresses IP non pris en charge ou inconnus. Au lieu de renvoyer une erreur 500, il consigne le problème et poursuit le traitement sans interruption.

_ACP2E-4049 - [contribution du code GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Échec du jeton de carte enregistré PayflowPro lors du paiement

Les identifiants de transaction PayPal PayFlow Pro (PNREF) peuvent désormais être utilisés dans les transactions de référence pendant une période fixe de 12 mois. Une fois expirée, la carte enregistrée ne s’affiche plus et doit être ajoutée à nouveau. Auparavant, la validité était déterminée par la date d’expiration de la carte de paiement utilisée dans la transaction initiale.

_ACP2E-4064 - [contribution du code GitHub](https://github.com/magento/magento2/commit/52f46328)_

### Performances

#### [Problème] Mettre à jour utilise le contrôle de cache non modifiable pour le site statique

Cette requête d’extraction ajoute une amélioration des performances en ne validant pas le contenu statique sur chaque chargement de page jusqu’à ce que et sauf si son contenu a été modifié.

_AC-15171 - [Problème GitHub](https://github.com/magento/magento2/issues/39486) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39484)_

#### [CLOUD] Impossible d’ajouter des produits aux catégories

Amélioration des performances lors de l’ajout d’un produit à une catégorie via le marchandiseur visuel.

_ACP2E-3946 - [Contribution du code GitHub](https://github.com/magento/inventory/commit/29653b1d)_

#### [Cloud] cache_invalidate plus de 10 000 journaux

Auparavant, le cache était effacé à chaque visite d’un PLP ou d’un panier, ce qui entraînait une surcharge de performances inutile. Le cache des règles de Target n’est plus invalidé sur ces pages, ce qui améliore l’efficacité de la navigation.

_ACP2E-4059_

### Tarification

#### Le produit est enregistré même lorsque la date de début du prix spécial est postérieure à la date de fin à l&#39;aide d&#39;une action en masse

Correction d’un problème en raison duquel les produits pouvaient être enregistrés avec une période de prix spéciaux non valide sans validation.
Désormais, un message d’erreur s’affiche : « Assurez-vous que la date de fin est postérieure ou identique à la date de début. »

_AC-15252 - [Problème GitHub](https://github.com/magento/magento2/issues/40113) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Les informations d&#39;expédition ne correspondent pas après avoir effectué un passage en caisse express paypal pour un devis négociable.

Ce problème a corrigé une discordance des frais d&#39;expédition lors de l&#39;exécution d&#39;un paiement PayPal Express pour un devis négociable approuvé.
Avant la correction, l’expédition était incorrectement doublée (indiquant 10 $ au lieu de 5 $), ce qui entraînait des totaux gonflés.
Le correctif dans Magento 2.4.9-alpha3 garantit l’application des frais d’expédition corrects

_AC-15280_

#### Le prix spécial ne prend pas en compte les sites web créés avec des fuseaux horaires différents

Avant la correction, la validité de la date du prix spécial était créée dans la portée de l’horodatage actuel du magasin. Désormais, après la correction, le fuseau horaire par défaut du magasin est pris en compte.

_ACP2E-4002_

#### Le prix normal n’est pas visible, même si un prix spécial est appliqué.

Correction d’un problème où le prix normal n’était pas affiché lorsqu’un prix spécial était appliqué. Le prix normal apparaît désormais correctement avec le prix spécial comme prévu.

_ACP2E-4100 - [contribution du code GitHub](https://github.com/magento/magento2/commit/47721be6)_

### Produit

#### Le libellé « Aussi bas que » reste affiché pour un produit configurable pour le cas de test AC-6158

Produits configurables mis en œuvre et vérifiés (P1-P7) avec des variations et des affectations de catégories respectives. Affichage correct des prix de storefront et comportement de l&#39;étiquette « Aussi bas que » pour les produits de la catégorie C.

_AC-10847 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Échec De La Journalisation Supplémentaire Lors De La Demande D’Un Produit Via Le Référentiel

Amélioration des messages d’erreur pour ProductRepository::get et getById lorsqu’un SKU ou un ID est introuvable.
Auparavant, les exceptions ne fournissaient aucun contexte sur le SKU ou l’ID à l’origine de l’erreur.
Désormais, le message d’exception inclut l’ID ou le SKU manquant, ce qui contribue au débogage et à l’amélioration de l’expérience du développeur.
Cette modification n’affecte aucun comportement fonctionnel de l’API.

_AC-15199 - [Problème GitHub](https://github.com/magento/magento2/issues/40090) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/1b1baf1d)_

#### L’affectation des produits simples est annulée lorsque le produit configurable est modifié par un rôle limité

Avant ce correctif, si un utilisateur administrateur restreint enregistrait un produit configurable contenant des produits simples auxquels il n’avait pas accès, il était supprimé du produit configurable lors de l’enregistrement. Après le correctif, le produit configurable est conservé tel qu’il est enregistré à partir d’un administrateur disposant de droits complets.

_ACP2E-4081_

#### Les performances de génération du plan de site [Cloud] se dégradent considérablement

La génération de plans de site pour les produits avec des images ne connaît plus de ralentissement exponentiel. Auparavant, la génération de plans de site pour les magasins dont l’inclusion d’images était activée entraînait des temps de traitement longs.

_ACP2E-4153 - [contribution du code GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

### Promotion

#### Erreur lors de l’obtention des remises sur article de commande appliquées_à pour la commande client via la demande client GraphQl.

Auparavant, lorsque des remises appliquées_à pour une commande client via une demande de client GraphQl, une erreur de serveur interne était observée, qui est désormais corrigée et des données de commande client appropriées avec une remise appliquée sont récupérées

_AC-14888 - [Problème GitHub](https://github.com/magento/magento2/issues/39963) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/fe72c407)_

#### Erreur lors de l’obtention du code de bon d’article de commande pour la commande client via la demande client GraphQl

Correction d’un problème en raison duquel la récupération de commandes avec des détails de coupon via GraphQL renvoyait une erreur de serveur interne.
Désormais, la requête s’exécute correctement et renvoie les informations correctes sur le coupon dans la réponse.

_AC-14889 - [Problème GitHub](https://github.com/magento/magento2/issues/39962) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/fe72c407)_

### SEO

#### Clé de tableau non définie dans ProductRepository getById

Le problème se produisait lorsque ProductRepository::getById() était appelé avec un ID non valide tel que 123abc, ce qui entraînait une erreur de type « Clé de tableau non définie ».
Après le correctif dans Magento 2.4.9-alpha3, ces requêtes renvoient désormais correctement une page 404 au lieu de générer une exception.
Le contrôle qualité a confirmé que les identifiants étaient valides et incorrects, et aucun autre problème n’a été observé.

_AC-15345 - [Problème GitHub](https://github.com/magento/magento2/issues/40146) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### La génération du plan de site [Cloud] ne se termine jamais

Avant le correctif, la génération du plan de site ne pouvait pas se terminer correctement si le catalogue contenait plus d’un million de produits. Après le correctif, la génération du plan de site se terminera avec une allocation de mémoire plus faible et avec jusqu’à un million de produits par magasin.

_ACP2E-3902 - [contribution du code GitHub](https://github.com/magento/magento2/commit/52f46328)_

#### Le sélecteur de boutique [Cloud] ne fonctionne pas de EN à FR pour la page de FAQ

Correction d’un problème en raison duquel le changement d’affichage des magasins redirigeait les utilisateurs vers la page d’accueil au lieu de la page CMS traduite correspondante. Le sélecteur de magasin recherche désormais les réécritures d’URL dans le magasin cible afin de garantir une redirection correcte (par exemple, la page FAQ en anglais → la page FAQ en français).

_ACP2E-4112_

### Évaluation et prévisualisation

#### L’aperçu de la mise à jour intermédiaire s’interrompt lors du passage en caisse avec un autre domaine d’administration

Un client peut se connecter et afficher son panier en mode d’aperçu de magasin lorsque l’URL de base du magasin est différente de l’URL d’administration.

_ACP2E-3906_

#### Affichage incorrect de l’heure dans le tableau de bord d’évaluation du contenu

Désormais, les filtres de date « Heure de début » et « Heure de fin » dans « Tableau de bord de test de contenu » affichent la date et l’heure correctes. Auparavant, une date et une heure incorrectes s’affichaient après avoir sélectionné la date et l’heure dans le sélecteur de date

_ACP2E-3969_

#### La portée affiche une vue de magasin différente pendant la prévisualisation pour les produits et la catégorie de mise à jour planifiés

Avant cette correction, le lien d’aperçu pour les catégories et les produits n’était pas généré pour le magasin approprié. Après cette correction, le lien d’aperçu sélectionne automatiquement le magasin sur lequel l’aperçu a été créé.

_ACP2E-4053_

### Framework de l’interface utilisateur

#### [Problème] Supprimer la balise `@author` interdite de `Magento_Backend`

Cette requête d’extraction supprime `@author` balise de la base de code

_AC-8814 - [Problème GitHub](https://github.com/magento/magento2/issues/37522) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/36976)_
