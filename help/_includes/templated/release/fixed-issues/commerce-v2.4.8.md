---
source-git-commit: 92907752d92cd7f4a81377a5239dfded10fe3655
workflow-type: tm+mt
source-wordcount: '27924'
ht-degree: 0%

---
# Problèmes résolus dans Adobe Commerce (v2.4.8)

## Correction de problèmes dans la version v2.4.8

Nous avons corrigé 581 problèmes dans le code principal d’Adobe Commerce 2.4.8. Un sous-ensemble des problèmes résolus inclus dans cette version est décrit ci-dessous.

### API

#### L’API REST /V1/transactions renvoie une erreur lorsque parent_txn_id = txn_id

Le système gère désormais correctement les transactions du concept parent et enfant où l’ID de transaction parent est identique à l’ID de transaction, ce qui empêche une boucle infinie lors de l’interrogation du point d’entrée /V1/transactions de l’API REST. Auparavant, ce scénario entraînait une erreur fatale en raison du dépassement du temps d’exécution maximal.

_AC-10042 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/1bafc571)_

#### Problème de type [Graphql] dans la version 2.4.7

Le système gère désormais correctement les valeurs entières dans la fonction GetCustomSelectedOptionAttributes lors de l&#39;exécution d&#39;une requête GraphQL, ce qui empêche toute erreur liée au type. Auparavant, le lancement d’une requête GraphQL qui utilisait GetCustomSelectedOptionAttributes avec un argument entier entraînait une erreur de type.

_AC-11878 - [Problème GitHub](https://github.com/magento/magento2/issues/38662) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38663)_

#### Caractères spéciaux dans la catégorie url_key (lorsqu’ils sont créés via l’API REST)

Auparavant, dans category_url_key, le caractère spécial n&#39;était pas présent après le correctif ; il était affiché dans category_url_key

_AC-3223 - [Problème GitHub](https://github.com/magento/magento2/issues/35577) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/c699c206)_

#### API REST affichant les commandes provenant d’un autre site web. 

Le système prend désormais en charge l’accès autorisé de la portée pour les jetons d’administration de l’API REST et les points d’entrée Magento_Sales, ce qui garantit que l’API REST affiche uniquement les commandes auxquelles l’administrateur a accès. Auparavant, l’API REST affichait les commandes de tous les sites web, quel que soit le site web affecté à l’utilisateur administrateur.

_ACP2E-2703_

#### Problème avec l’api rest après l’activation de 2FA Duo

2FA avec option de sécurité Duo génère désormais la signature correcte pour l’API Rest

_ACP2E-2755 - [Contribution du code GitHub](https://github.com/magento/security-package/commit/412fa642)_

#### [API REST] : l’option Utiliser la valeur par défaut dans la vue du magasin ne reste pas cochée après l’ajout de configurations pour un produit configurable

Le problème a été corrigé en veillant à ce que les entrées de base de données soient correctes pour les options personnalisables d’un magasin autre que celui par défaut. La case à cocher du magasin personnalisé dans la section « Admin > Catalogue > Modification de produit > Options personnalisables » n’était auparavant pas cochée en raison d’entrées de base de données inexactes, même si le titre de l’option du magasin personnalisé restait identique au magasin par défaut.

_ACP2E-2927 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/3056e9cb)_

#### L’API REST ne peut pas effectuer de requêtes avec une barre oblique (/) dans le SKU lors de l’utilisation d’Oauth1

Avant la correction, vous ne pouviez pas effectuer d’appel API réussi pour un produit dont le SKU contenait le caractère « / ». Désormais, vous pouvez émettre une requête d’obtention d’API réussie pour les détails du produit, même si son SKU comporte une barre oblique.

_ACP2E-2969 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/b21e5d91)_

#### Échec de la mise à jour de l’adresse du client lors de la mise à jour via l’API REST si « validateDefaultAddress » activé

Le point d’entrée de l’API fonctionne désormais comme prévu une fois le problème lié à la clé d’ID manquante dans la payload de l’API résolu.

_ACP2E-3079 - [contribution du code GitHub](https://github.com/magento/magento2/commit/9af794a4)_

#### [Cloud] Création du groupe de prix de site web en double dans l’Api Prix de niveau.

Désormais, l’API Tier Price REST ne permet pas de créer le groupe de prix de site web dupliqué.
Auparavant, il était possible de créer le groupe de clients de prix de groupe de sites Web en double dans l’Api Prix de niveau qui ne réussissait pas la validation dans Admin lors de l’enregistrement du produit.

_ACP2E-3091 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/148c3ead)_

#### Impossible d’ajouter un commentaire de commande avec le statut via l’API REST

Le problème a été résolu en autorisant la modification du statut de l’ordre uniquement s’il s’agit de l’état actuel . Auparavant, il ne respectait pas l’état de la commande et n’empêchait aucune modification de l’état de la commande, même s’il provenait du même état.

_ACP2E-3130 - [contribution du code GitHub](https://github.com/magento/magento2/commit/93d50f8d)_

#### L’opération asynchrone échoue lorsque le SKU est absent de la payload

Les opérations asynchrones et de synchronisation échouaient auparavant en raison d’erreurs d’enregistrement du produit si le sku est manquant dans la payload. Après le correctif, les opérations de l’api rest d’enregistrement de produit asynchrones et synchronisées échouent avec un message d’exception approprié.

_ACP2E-3236 - [contribution du code GitHub](https://github.com/magento/magento2/commit/66dea0de)_

#### [CLOUD] Impossible de mettre à jour les prix de base à l’aide de l’API REST (la valeur de « value_id » dans « catalog_product_entity_decimal » n’est pas incrémentée correctement.)

Avant ce correctif, lorsque l’api rest /rest/default/V1/products/base-prices était appelée, l’ID d’incrément était augmenté par erreur, laissant un écart entre les valeurs. Après la correction, l’ID d’incrément est augmenté comme prévu, de manière incrémentielle. La plage de champs value_id a également été augmentée.

_ACP2E-3376 - [contribution du code GitHub](https://github.com/magento/magento2/commit/d50f6b5d)_

#### Les articles de commande ne sont pas visibles dans les e-mails d’avoir pour l’API POST V1/order/:orderId/restore

Auparavant, avant ce correctif, lorsqu’un client crée un avoir à partir d’une requête API notifiant send_email, il ne contient pas la grille des détails du produit. Après application de ce correctif, le client envoie une demande d’API d’avoir et trouve les détails de l’élément de produit apparaissant dans l’e-mail.

_ACP2E-3460 - [contribution du code GitHub](https://github.com/magento/magento2/commit/3f12d152)_

#### Les valeurs par défaut ne sont pas définies pour les attributs date et heure avec les produits RestAPI

Les valeurs par défaut sont désormais correctement définies pour les attributs de date et de date et d’heure via RestAPI

_ACP2E-3486 - [contribution du code GitHub](https://github.com/magento/magento2/commit/1984c61c)_

### API, panier et passage en caisse

#### Erreur critique 500 : Magento\Framework\Webapi\Exception liée à l’en-tête HTTP Accept

Après le correctif, il n’y a aucun problème avec la spécification de l’en-tête « Accepter ».

_ACP2E-3343 - [contribution du code GitHub](https://github.com/magento/magento2/commit/1366ae5e)_

### API, GraphQL

#### aucune GraphQl disponible pour l’abonnement aux mises à jour des Points de récompense pour le client

Auparavant, les attributs du client reward_warning_notification ne pouvaient pas être mis à jour par le biais de la mutation GraphQL et de l’appel de l’API REST. Peut désormais être mis à jour de la même manière que l’attribut client reward_update_notification.

_ACP2E-3348_

### API, GraphQL, taxe

#### Luma (API REST) et Graphql ne calculent pas les taxes lorsque seul le code postal est fourni.

Le système calcule désormais correctement les taxes lorsqu’un seul code postal est fourni, ce qui permet d’obtenir des estimations de taxe précises pour Luma (API REST) et GraphQL. Auparavant, seules les estimations d’expédition étaient calculées et les taxes n’étaient pas incluses lorsqu’un code postal était fourni.

_AC-12060_

### Compte

#### Le formulaire d’adresse du client autorise le code aléatoire dans les champs de nom

Le système valide désormais l’entrée dans les champs Prénom et Nom du formulaire d’adresse du client, empêchant l’utilisation de code aléatoire. Auparavant, le système permettait d’utiliser du code aléatoire dans ces champs sans générer d’erreur.

_AC-10782 - [Problème GitHub](https://github.com/magento/magento2/issues/38331) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38345)_

#### Mise à jour du mot de passe de l’administrateur.

_AC-10886 - [Problème GitHub](https://github.com/magento/magento2/issues/38352) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/4bca5dfe)_

#### plantage de l’ajout d’adresse à mon compte lors de l’enregistrement

Le système enregistre désormais correctement les adresses des clients même lorsque le champ Région n’est pas affiché, ce qui empêche un blocage pendant le processus d’enregistrement. Auparavant, toute tentative d’ajout ou de modification d’une adresse sans champ de région affiché entraînait une erreur d’exception.

_AC-10990 - [Problème GitHub](https://github.com/magento/magento2/issues/38406) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38407)_

#### Boucle de redirection lorsque les URL sont en majuscules

Le système convertit désormais automatiquement les caractères majuscules des URL en minuscules, ce qui empêche une boucle de redirection lors de l’accès à la page d’accueil. Auparavant, la présence de caractères majuscules dans l’URL de base sécurisée entraînait une boucle de redirection continue lors de la tentative d’accès à la page d’accueil.

_AC-11718 - [Problème GitHub](https://github.com/magento/magento2/issues/38538) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38539)_

#### middlename(s) non enregistré(s) pour les comptes invités

Le système enregistre désormais correctement le deuxième prénom pour les comptes invités lors du passage en caisse, ce qui le rend accessible dans le modèle de courrier électronique. Auparavant, le deuxième prénom n’était pas enregistré dans le tableau des devis et n’était pas accessible dans le modèle d’e-mail pour les comptes invités.

_AC-11755 - [Problème GitHub](https://github.com/magento/magento2/issues/38593) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39067)_

#### Administrateur : boutons d’actions de page flottant à gauche et non à droite

Le système aligne désormais correctement les boutons d’actions de page sur le côté droit de l’en-tête persistant dans le panneau d’administration, améliorant ainsi l’aspect professionnel. Auparavant, ces boutons flottaient incorrectement sur le côté gauche de l’en-tête persistant.

_AC-11919 - [Problème GitHub](https://github.com/magento/magento2/issues/38701) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/44cef3a9)_

#### `dev:di:info` erreur dans magento 2.4.7

Le système affiche désormais correctement les paramètres du constructeur lors de l’exécution de la commande `dev:di:info`, ce qui empêche toute erreur. Auparavant, l’exécution de cette commande entraînait une erreur en raison d’une incohérence de type dans l’argument .

_AC-11999 - [Problème GitHub](https://github.com/magento/magento2/issues/38740) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/0c53bbf7)_

#### Case à cocher Se connecter en tant que client non traduisible

Le système permet désormais de définir les champs « Case à cocher Se connecter en tant que client opt-in » et « Info-bulle se connecter en tant que client ou cliente » sur la portée « Affichage de la boutique », ce qui permet d’obtenir des traductions pour différents affichages de la boutique. Auparavant, ces champs n’étaient définis que sur la portée « Site web », ce qui empêchait les traductions pour les vues de magasin individuelles.

_AC-13000 - [Problème GitHub](https://github.com/magento/magento2/issues/32329) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/32359)_

#### Page d’accueil de l’interface utilisateur front-end dans le menu déroulant de mon profil n’est pas présent.(par intermittence)

_AC-14299_

#### Le client est connecté mais affiche une erreur 404 dans le serveur frontal.

La page du tableau de bord du client storefront se charge désormais comme prévu lorsqu’un client se connecte. Auparavant, les clients pouvaient se connecter, mais cette page affichait une erreur 404. [GitHub-35838](https://github.com/magento/magento2/issues/35838)

_AC-6071 - [Problème GitHub](https://github.com/magento/magento2/issues/35838) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/36263)_

#### Impossible d’enregistrer les informations d’attribut du client dans la section Modifier le client administrateur ;

L’ID de magasin du client est désormais correctement implémenté par portée de site web pour le formulaire de modification du client administrateur.

_ACP2E-2791 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/488c1034)_

#### [Cloud] Impossible de créer un client via l’API lorsque la vente privée est activée

Désormais, le client peut être créé par un utilisateur administrateur authentifié, ainsi qu’avec un jeton d’intégration authentifié via l’api REST lorsque la restriction de site web est activée.

_ACP2E-3115_

#### Après s’être connecté, les produits ajoutés à la liste de comparaison en tant qu’utilisateur invité ne sont pas visibles.

Les produits qui ont été ajoutés à la liste de comparaison de produits avant de se connecter en tant que client sont maintenant conservés après la connexion.
Auparavant, après s’être connecté, les produits ajoutés à la liste de comparaison en tant qu’utilisateur invité n’étaient pas visibles.

_ACP2E-3329 - [contribution du code GitHub](https://github.com/magento/magento2/commit/078c387e)_

#### La configuration Autoriser les pays entraîne des problèmes dans les configurations d’adresses client

Désormais, la sélection de la configuration Autoriser les pays n’influence pas les pays affichés pour en dehors de la portée donnée. Auparavant, la configuration Autoriser les pays avait influencé l’attribut d’adresse du client en dehors de la portée donnée

_ACP2E-3433 - [contribution du code GitHub](https://github.com/magento/magento2/commit/078c387e)_

#### Le registre des cadeaux partagé indique la date de l’événement 1 jour plus tôt

La date d&#39;enregistrement du cadeau s&#39;affiche correctement sur Storefront

_ACP2E-3445_

#### VAPT : erreur de logique commerciale - date future comme date de naissance du client

La date de naissance du client ne peut pas être fixée plus tard qu&#39;aujourd&#39;hui

_ACP2E-3501 - [contribution du code GitHub](https://github.com/magento/magento2/commit/d4de4726)_

### Compte, API, GraphQL

#### API Client - Le Nombre D’Échecs De Connexion Ne Peut Pas Être Réinitialisé À 0 Après Une Connexion Réussie

Désormais, le numéro d’échec est réinitialisé sur zéro dans la table des entités client après la connexion réussie du client via les points d’entrée de l’API.

_ACP2E-3246 - [contribution du code GitHub](https://github.com/magento/magento2/commit/ec7e32a9)_

### Compte, interface utilisateur d’administration, B2B

#### Les utilisateurs administrateurs restreints ne peuvent pas toujours voir les catalogues partagés personnalisés

Les utilisateurs administrateurs restreints peuvent désormais afficher et gérer de manière cohérente les clients et tous les catalogues partagés auxquels les produits sont affectés, à condition d’avoir accès à un magasin spécifique. Auparavant, un utilisateur administrateur restreint ayant accès à une boutique particulière ne pouvait pas toujours voir tous les catalogues partagés auxquels les produits étaient affectés ou pouvait voir les clients qui ne pouvaient pas effectuer d’enregistrement, ce qui entraînait des incohérences dans le système.

_ACP2E-3038 - [contribution du code GitHub](https://github.com/magento/magento2/commit/7377de59)_

### Compte, panier et passage en caisse

#### l’attribut d’adresse du client personnalisé « select » ne s’affiche pas pour la nouvelle adresse du client

_AC-2341 - [Problème GitHub](https://github.com/magento/magento2/issues/34950)_

### Interface utilisateur d’administration

#### [Problème] ajouter une vérification des autorisations pour le bouton de données « recharger les données »

Le système inclut désormais une vérification des autorisations pour le bouton « Recharger les données », afin de s’assurer qu’elles ne sont affichées et accessibles qu’aux utilisateurs disposant des autorisations appropriées. Auparavant, le bouton « Recharger les données » était visible et cliquable par tous les utilisateurs et utilisatrices, ce qui entraînait l’affichage d’une page « non autorisée » lorsque les utilisateurs et utilisatrices cliquaient dessus sans les autorisations nécessaires.

_AC-10705 - [Problème GitHub](https://github.com/magento/magento2/issues/38283) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38279)_

#### [Problème ] libellés incohérents pour les attributs dans les règles marketing

Le système renseigne désormais correctement les libellés de manière cohérente pour les options de catégorie et d’attribut dans la règle de prix de panier

_AC-11427 - [Problème GitHub](https://github.com/magento/magento2/issues/31232) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/31231)_

#### La validation des données a réussi et le bouton Importer est présent lors de l’importation de produits avec le comportement Remplacer

Le système valide désormais correctement les données et masque le bouton « Importer » pendant le processus d’importation du produit avec le comportement « Remplacer », empêchant tout remplacement involontaire des données. Auparavant, le système ne validait pas correctement les données et affichait le bouton « Importer », ce qui entraînait des incohérences potentielles des données.

_AC-11588 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/0574ac23)_

#### [Bug] Magento 2.4.7 n’autorise pas les photos de produit avec extension de fichier majuscule.

Le système accepte désormais les chargements d’images de produit avec des extensions de fichier de lettre majuscule, ce qui garantit un processus de création de produit fluide. Auparavant, les chargements d’images avec des extensions de fichier en majuscules étaient refusés, ce qui forçait les utilisateurs à modifier l’extension de fichier en minuscules.

_AC-12167 - [Problème GitHub](https://github.com/magento/magento2/issues/38831) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/c8f87c25)_

#### Liste déroulante masquée dans les grilles avec l’action de sélection (par exemple, Contenu > Éléments > Pages)

Le système a maintenant été corrigé dans toutes les listes déroulantes similaires pour toutes les grilles.

_AC-12319 - [Problème GitHub](https://github.com/magento/magento2/issues/38891) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39371)_

#### [Problème] Avertissement de correctif : « filtres » de clé de tableau non définis

Le système gère désormais les scénarios dans lesquels un nouvel utilisateur n’a pas encore interagi avec les signets, empêchant la journalisation d’un avertissement de « filtres » de clé de tableau non défini. Auparavant, cet avertissement était consigné lorsqu’un nouvel utilisateur n’avait pas interagi avec des signets.

_AC-13131 - [Problème GitHub](https://github.com/magento/magento2/issues/39013) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38996)_

#### Le fichier CSV d&#39;importation de produit avec des caractères spéciaux échoue en raison de changements de code dans le fichier Validate.php

Le système valide et importe désormais correctement les fichiers CSV de produit contenant des caractères spéciaux, ce qui permet de réussir le transfert des données. Auparavant, toute tentative d’importation d’un fichier CSV de produit avec des caractères spéciaux entraînait une erreur, empêchant le processus d’importation.

_AC-13529 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/6cfb9b6b)_

#### Lorsque le nombre maximal de demandes de réinitialisation de mot de passe est défini sur « supérieur à 0 », par exemple : 3 , « Les messages d’erreur de dépassement de limite sont envoyés avant d’atteindre la limite, c’est-à-dire à partir de la deuxième fois.

_AC-13767_

#### Bien que le Nombre maximal de demandes de réinitialisation de mot de passe soit défini sur 0 ( désactivé) , « Les messages d’erreur de dépassement de limite sont envoyés à partir de la 2e fois »

_AC-13768_

#### Il n’y a pas d’astérisque rouge pour le champ du numéro de téléphone obligatoire

L&#39;astérisque rouge précédent ne s&#39;affichait pas pour le numéro de téléphone mais  le numéro de téléphone était obligatoire. Qui est maintenant fixe astérisque rouge peut être vu sur le numéro de téléphone comme un champ obligatoire.

_AC-13850 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/c699c206)_

#### Dans Admin, il n’est pas possible de cliquer sur le bouton Envoyer la commande lorsque nous tentons de la réorganiser. (par intermittence)

_AC-14300_

#### [Problème ] Définir le mode d’indexeur par défaut sur « planifier »

Tous les nouveaux indexeurs sont configurés par défaut en mode **[!UICONTROL Update by Schedule]**.  Auparavant, le mode par défaut était **[!UICONTROL Update on Save]**. Les indexeurs existants ne sont pas affectés. [GitHub-36419](https://github.com/magento/magento2/issues/36419)

_AC-6975 - [Problème GitHub](https://github.com/magento/magento2/issues/36419) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/0b410856)_

#### [Problème] Déposez les tables de journal des modifications de l&#39;indexeur sur mview unsubscribe

Le système supprime désormais automatiquement les tables de journaux des modifications inutilisées lorsqu&#39;un index passe de « mise à jour selon le calendrier » à « mise à jour lors de l&#39;enregistrement », marquant l&#39;index comme non valide pour s&#39;assurer qu&#39;aucune entrée n&#39;est manquée. Auparavant, le fait de passer un index à « mettre à jour lors de l&#39;enregistrement » laissait des tables de journaux des modifications inutilisées dans le système et marquait tous les index modifiés comme « valides ».

_AC-7700 - [Problème GitHub](https://github.com/magento/magento2/issues/29789) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/25859)_

#### Aucun lien vers l’expédition lors des paiements en passage en caisse dans la vue Téléphone mobile

Le système garantit désormais que les titres/liens de passage en caisse « Expédition » et « Révision et paiements » sont toujours visibles en haut de la page en mode mobile, ce qui permet aux utilisateurs de naviguer facilement entre les étapes et d’effectuer les corrections nécessaires. Auparavant, ces titres/liens étaient masqués en mode mobile, ce qui rendait difficile pour les utilisateurs de connaître l’étape en cours ou de revenir aux étapes précédentes.

_AC-7962 - [Problème GitHub](https://github.com/magento/magento2/issues/36856) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/36982)_

#### les commentaires d&#39;expédition de la requête de commandes client created_at sont renvoyés dans le fuseau horaire +0 qui n&#39;est pas dans le fuseau horaire configuré du magasin

Le système affiche désormais correctement le champ &#39;created_at&#39; à partir des commentaires d&#39;expédition dans le fuseau horaire configuré du client lors de l&#39;utilisation de la requête Commandes client. Auparavant, le champ « created_at » s’affichait dans le fuseau horaire +0, quel que soit le fuseau horaire configuré du client.

_AC-8109 - [Problème GitHub](https://github.com/magento/magento2/issues/36947) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37642)_

#### i18n:collect-phrases rompt l&#39;intégrité des traductions

La commande `bin/magento i18n:collect-phrases -o` collecte et ajoute désormais correctement les nouvelles expressions des fichiers JavaScript et .phtml, en veillant à ce que les traductions soient reflétées avec précision dans le fichier de traduction. Auparavant, le système n’incluait pas les expressions de traduction multiligne des fichiers JavaScript et les expressions des fichiers .phtml dans le fichier de traduction, ce qui entraînait des traductions incomplètes ou incorrectes.

_AC-9843 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/0c53bbf7)_

#### Problème d’autorisation d’accès au bloc dynamique

Auparavant, pour l’administration restreinte, l’ajout d’un nouveau bloc dynamique générait une erreur. Après l’implémentation de ce correctif, l’administrateur restreint peut ajouter le bloc dynamique et le modifier sans erreur

_ACP2E-2687_

#### L’apostrophe dans le nom de la vue du magasin est remplacée par &#039;

Les filtres de vue de magasin de la grille affichent désormais correctement les apostrophes

_ACP2E-2787 - [Problème GitHub](https://github.com/magento/magento2/issues/38395) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/39d54c2d)_

#### Le chargement de Favicon ne parvient pas à valider les fichiers .ico

L’erreur de validation du fichier a été mise à jour sur « Échec de la validation du fichier ». Vérifiez les paramètres de traitement des images dans la configuration de la boutique. » Auparavant, il s’agissait simplement de « Échec de la validation du fichier ».

_ACP2E-2847 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/39d54c2d)_

#### La Galerie dans PageBuilder affiche l’ancienne miniature de l’image au lieu de l’image nouvellement chargée

Régénérez les aperçus d’image pour les images supprimées et rechargées avec le même nom via la galerie de médias dans le contenu du générateur de page.

_ACP2E-2957 - [Contribution du code GitHub](https://github.com/magento/magento2-page-builder/commit/60140cd2) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/001e5188)_

#### L’enregistrement d’un produit par un utilisateur administrateur avec une étendue de rôle différente remplace/supprime les informations existantes sur les produits associés dans le produit

Auparavant, avant le correctif, les produits associés étaient réinitialisés et étaient vides lorsque l’utilisateur administrateur secondaire cliquait sur le bouton d’enregistrement sans modifier les produits associés. Après ce correctif, l’utilisateur administrateur secondaire clique sur le bouton d’enregistrement et le produit ne se réinitialise pas et est enregistré avec succès.

_ACP2E-2978 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/3056e9cb)_

#### Impossible d&#39;exporter plus de 200 commandes

Les limites du serveur pour la taille de requête des identifiants sélectionnés précédemment envoyés ont été négligées en modifiant la requête HTTP de GET vers POST afin de résoudre le problème. Auparavant, en raison des limitations du serveur pour la taille de requête GET, le problème était rencontré.

_ACP2E-3033 - [contribution du code GitHub](https://github.com/magento/magento2/commit/93d50f8d)_

#### Message de validation de la page de passage en caisse incorrect.

Si un champ obligatoire reste vide, tel que « adresse », la validation côté serveur n’affiche pas le message. La validation côté client garantit que la notification d’erreur de champ obligatoire s’affiche, indiquant « Ceci est un champ obligatoire ». Auparavant, le message « l’adresse est requise » s’affichait si un champ obligatoire restait vide, en plus du message de validation côté client.

_ACP2E-3037 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/9af794a4)_

#### Problème de modèle de réinitialisation de mot de passe avec l’utilisateur administrateur

Le problème a été résolu à l&#39;aide de la clé correcte, qui inclut désormais le nom d&#39;utilisateur de l&#39;administrateur dans le modèle d&#39;e-mail et complète correctement l&#39;objet. Auparavant, le problème provenait d’une clé obsolète utilisée.

_ACP2E-3125 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/93d50f8d)_

#### Barres obliques doubles dans l’URL du segment client

Les barres obliques doubles n’apparaissent pas dans l’URL lorsque l’utilisateur clique sur « Réinitialiser le filtre » dans la grille.

_ACP2E-3149 - [contribution du code GitHub](https://github.com/magento/magento2/commit/8459b17d)_

#### La DCO n’est pas disponible pour les pays spécifiques autorisés

Désormais, le paiement à la livraison est disponible pour les pays spécifiques autorisés dès que cela est nécessaire et   AC-3216 fonctionne comme prévu.

_ACP2E-3171 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/6f4805f8)_

#### Impossible de mettre à jour le statut de la commande créée personnalisée

« Nous pouvons maintenant mettre à jour les statuts de commande personnalisés, alors qu&#39;auparavant le statut ne pouvait être modifié que si le statut actuel était soit « traitement » soit « fraude ».

_ACP2E-3178 - [Problème GitHub](https://github.com/magento/magento2/issues/38659) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/8459b17d)_

#### L’état de l’adresse d’expédition n’est pas mis à jour automatiquement

Avant le correctif, la région de l’adresse d’expédition (ou l’ID de région) n’était pas synchronisée avec les informations de facturation de l’adresse. Désormais, la région et l’ID de région de l’adresse de livraison sont correctement mis à jour lorsque les informations de l’adresse de facturation sont modifiées.

_ACP2E-3294 - [contribution du code GitHub](https://github.com/magento/magento2/commit/581b7ef1)_

#### Le bouton Réinitialiser ne fonctionne pas sur Ajouter/Modifier un utilisateur administrateur

Auparavant, le bouton Réinitialiser ne fonctionnait pas sur la page Ajouter/modifier un utilisateur administrateur . Désormais, dans le panneau d’administration sous Système -> Autorisations -> Tous les utilisateurs, le bouton Réinitialiser fonctionnera correctement sur la page Ajouter/modifier un utilisateur administrateur .

_ACP2E-3364 - [contribution du code GitHub](https://github.com/magento/magento2/commit/5184c067)_

#### Détection des erreurs de routage des URL d’administration Magento et erreurs CORS

Après le correctif, si le domaine d’administration personnalisé est un sous-domaine du domaine principal, l’administrateur n’est accessible qu’à partir du sous-domaine configuré.

_ACP2E-3373 - [Problème GitHub](https://github.com/magento/magento2/issues/37663) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/3f12d152)_

#### Non-validation de la « Quantité maximale autorisée dans le panier »

Auparavant, lorsque nous placions `Maximum Qty Allowed in Shopping Cart` vide, aucune exception n’était générée, bien qu’une valeur vide ne soit pas acceptée ici. Une fois que ce correctif est appliqué, le fait de placer une chaîne vide génère des exceptions et ne permet pas d’enregistrer le produit.

_ACP2E-3392 - [contribution du code GitHub](https://github.com/magento/magento2/commit/d50f6b5d)_

#### [Problème d’interface utilisateur de l’aperçu de Pagebuilder] Les boutons de la colonne Page Builder ne s’alignent pas correctement

Les boutons des colonnes du Générateur de page sont désormais correctement alignés. Auparavant, ils n’étaient pas alignés correctement dans les colonnes du Page Builder.

_ACP2E-3408 - [contribution du code GitHub](https://github.com/magento/magento2-page-builder/commit/1a52ef4c)_

#### Le rapport Produits commandés n&#39;est pas exporté. Erreur 404 à la place.

L’exportation du rapport Produits commandés au format CSV et XML fonctionne désormais comme prévu

_ACP2E-3431 - [contribution du code GitHub](https://github.com/magento/magento2/commit/88660e79)_

#### Erreur Minuscule MCE JS dans la console après l’activation de la minimisation JS avec le mode de production

Auparavant, l’activation de la minimisation JavaScript en mode production dans le panneau d’administration entraînait l’affichage d’erreurs JavaScript liées à TinyMCE 6 dans la console du navigateur, ce qui affectait les fonctionnalités et l’expérience utilisateur. Maintenant, ce problème a été résolu, en veillant à ce que TinyMCE 6 fonctionne correctement sans générer d’erreurs, même lorsque la minimisation JS est activée.

_ACP2E-3457 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/56463d5e)_

#### Demande de modifications supplémentaires pour terminer complètement le correctif ACP2E-3375

&#39;-

_ACP2E-3459 - [contribution du code GitHub](https://github.com/magento/magento2/commit/d50f6b5d)_

#### Activation automatique des nouvelles autorisations ACL

Les nouvelles autorisations ajoutées à des modules personnalisés n’accordent plus automatiquement l’accès à tous les rôles utilisateur existants, sauf si elles sont configurées explicitement.

_ACP2E-3503 - [contribution du code GitHub](https://github.com/magento/magento2/commit/3f12d152)_

#### Le rapport d’utilisateur du journal des actions d’administration n’affiche pas de détails sur adminhtml_user_delete

L’adminhtml_user_delete consigne désormais correctement les détails importants. Auparavant, les journaux n’étaient pas générés pour les suppressions d’utilisateurs.

_ACP2E-3509 - [contribution du code GitHub](https://github.com/magento/magento2/commit/4de008a9)_

#### Règle de panier avec condition d’expédition non applicable lors de la commande auprès de l’administrateur

Auparavant, si la règle de prix du panier bénéficie d’une réduction sur les méthodes d’expédition avec le coupon, elle ne peut pas être appliquée via l’interface utilisateur d’administration. Une fois ce correctif appliqué, la remise de la règle de prix du panier avec un coupon pour une méthode d’expédition spécifique sera appliquée correctement à partir de l’interface utilisateur d’administration.

_ACP2E-3536 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a52ff98f) - [Contribution du code GitHub](https://github.com/magento/inventory/commit/11ce816b)_

#### Le code [FRESH] HEX ne se met pas correctement à jour dans SWATCH

Le code HEX saisi manuellement par l’utilisateur dans le sélecteur de couleurs de l’échantillon visuel n’est plus modifié par le système. Auparavant, certains codes HEX subissaient de légers ajustements en raison d’erreurs de conversion entre les modèles de couleurs.

_ACP2E-3559 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/344fce23) - [Contribution du code GitHub](https://github.com/magento/inventory/commit/1ef984c0)_

### Interface utilisateur d’administration, B2B

#### La connexion B2B en tant qu’en-tête client comporte toujours l’identité de marque Magento

Auparavant, l’en-tête du storefront affichait « Vous êtes désormais connecté en tant que &lt;nom du client> sur &lt;nom du magasin> » avec l’identité graphique de Magento. Ce problème est maintenant résolu et l’en-tête s’affiche avec le branding ADOBE.

_AC-13628 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/96dec499)_

### Interface utilisateur d’administration, catalogue

#### Impossible de modifier les positions des produits de la catégorie dans le site web autorisé en tant qu’utilisateur administrateur restreint

Autorisez un utilisateur administrateur restreint à ajouter et à trier des produits sous une catégorie contenue dans la catégorie racine affectée sous le site web restreint.

_ACP2E-2708_

### Interface utilisateur d’administration, Modes de paiement, Commande

#### Autorisation de transaction non affichée dans l&#39;onglet Transaction après la commande du bouton intelligent PayPal

Le système affiche désormais correctement l&#39;autorisation de transaction dans l&#39;onglet Transaction après qu&#39;une commande a été passée à l&#39;aide du bouton intelligent PayPal. Auparavant, la transaction d’autorisation n’apparaissait pas dans l’onglet Transaction après avoir cliqué sur le bouton « Autoriser », et aucune nouvelle transaction de type « Autorisation » n’a été créée.

_AC-13520 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/6cfb9b6b)_

### Interface utilisateur d’administration, Performances

#### Après la mise à jour vers la version 2.4.5-p8, 500 erreurs se produisent lors de la création d’une commande auprès de l’administrateur

Auparavant, lors de l’activation de la minimisation HTML, une commande de l’administrateur ne pouvait pas être passée. Désormais, lorsque la minimisation HTML est activée, la commande auprès de l’administrateur peut être passée avec succès.

_ACP2E-3169 - [contribution du code GitHub](https://github.com/magento/magento2/commit/b21e5d91)_

### Interface utilisateur d’administration, Expédition

#### Le nombre de codes coupon n’est pas mis à jour dans le   Colonne « Temps utilisé » de l’onglet Gérer les codes coupon si une commande est passée avec une expédition multiple.

Auparavant, lorsqu’une commande était passée avec expédition multiple, le nombre de codes coupon n’était pas mis à jour dans la colonne « Durée d’utilisation » de l’onglet Gérer les codes coupon. Désormais, le nombre correct s’affiche à la fois dans le « Temps utilisé », reflétant les valeurs souhaitées avec une expédition multiple.

_ACP2E-2519 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/4745100c)_

### Interface utilisateur d’administration, évaluation et prévisualisation

#### [Cloud] la suppression d’un modèle avec des images manquantes entraîne la suppression de pub/media

Auparavant, si le nom de l’image d’aperçu était manquant pour un modèle pagebuilder, le dossier pub/media était supprimé. Après la correction, seul le modèle est supprimé et l’image d’aperçu, si elle est trouvée.

_ACP2E-3424 - [contribution du code GitHub](https://github.com/magento/magento2-page-builder/commit/0986853b)_

### Analyses / Rapports

#### Erreur CSP de Google Analytics https://region1.analytics.google.com

Le système autorise désormais correctement les connexions à « https://region1.analytics.google.com&#39; » lorsque Google Analytics est activé, ce qui empêche les erreurs de politique de sécurité du contenu (CSP). Auparavant, l’activation de Google Analytics et l’affichage du site web depuis l’UE entraînaient des erreurs de console CSP en raison d’un refus de connexion à « https://region1.analytics.google.com&#39; ».

_AC-9922 - [Problème GitHub](https://github.com/magento/magento2/issues/37750) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38991)_

#### Le rapport avancé ne fonctionne pas

Le système prend désormais en charge la génération de fichiers de données de rapports avancés pour les jeux de données très volumineux en chargeant et en écrivant des rapports par lots de 10 000. Auparavant, le module de création de rapports avancés ne pouvait pas générer de fichiers de données pour les jeux de données très volumineux, ce qui provoquait des erreurs « MySQL Server has gone away » lors de l’exécution de la tâche analytics_collect_data cron.

_ACP2E-2570 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a12063bd)_

#### Problème de visibilité de la période du rapport Produits commandés par l’administrateur.

L’utilisateur pourra sélectionner n’importe quelle date dans le rapport des produits commandés. Auparavant, après une actualisation du tableau, la sélection de la date « DE » réinitialisait la date « À ».

_ACP2E-3080 - [contribution du code GitHub](https://github.com/magento/magento2/commit/6f4805f8)_

#### En-têtes de curl incorrects rendant le `newrelic:create:deploy-marker` inopérant

Le système formate désormais correctement les en-têtes curl, ce qui permet à la commande `newrelic:create:deploy-marker` de créer un marqueur de déploiement dans New Relic. Auparavant, des en-têtes curl incorrects empêchaient la création d’un marqueur de déploiement dans New Relic.

_ACP2E-3096 - [Problème GitHub](https://github.com/magento/magento2/issues/37641) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/6a185204)_

#### Événement addToCart manquant dans la couche de données pour le produit configurable avec option personnalisée.

Auparavant, l’événement addToCart n’était pas déclenché pour les produits configurables. Désormais, l’événement est correctement ajouté à la variable dataLayer de GMT.

_ACP2E-3146_

#### La surveillance du navigateur New Relic par le script inlineJS provoque des erreurs CSP

Les scripts de surveillance du navigateur New Relic sont désormais injectés par l’application au lieu de l’agent APM pour assurer la conformité avec la CSP (Content Security Policy, politique de sécurité du contenu). Auparavant, les scripts de surveillance du navigateur NewRelic injectés par l’agent APM n’étaient pas conformes à la CSP et empêchaient leur exécution.

_ACP2E-3183 - [contribution du code GitHub](https://github.com/magento/magento2/commit/66dea0de)_

#### Les requêtes INSERT dans la table sales_bestsellers_aggregated_daily deviennent lentes sur les projets avec un volume de commandes client important

Auparavant, le rapport quotidien agrégé des meilleures ventes prenait beaucoup de temps à générer pour un grand volume de commandes passées. Le rapport est maintenant généré en temps voulu.

_ACP2E-3189 - [contribution du code GitHub](https://github.com/magento/magento2/commit/7377de59)_

#### Rapports de commande affichant un symbole de devise incorrect

Le symbole de devise pour les montants des commandes dans l&#39;état des commandes provient incorrectement de devise/options/base. Correction de l’utilisation de la devise, des options et de la valeur par défaut pour un compte rendu des performances précis.

_ACP2E-3276 - [contribution du code GitHub](https://github.com/magento/magento2/commit/fd5cf3af)_

#### [Cloud] calculs incorrects dans le rapport Utilisation des coupons

Le total des ventes dans la grille d&#39;état des coupons est maintenant calculé avec précision en incorporant le « Montant de la remise de taxe » et le « Montant de la remise de taxe d&#39;expédition ». Auparavant, ces montants étaient absents du calcul, ce qui entraînait des écarts entre le total des ventes et les données des commandes client.

_ACP2E-3302 - [contribution du code GitHub](https://github.com/magento/magento2/commit/d75cff27)_

#### Problèmes avec « &lt;project_id>/var/tmp » partagé

Les fichiers temporaires DataExport d’Analytics utiliseront le répertoire tmp système, qui est plus adapté aux accès et aux modifications fréquents. Pour éviter les collisions si plusieurs instances sont exécutées sur le même serveur, le chemin tmp a été mis à jour pour utiliser l’ID unique d’une instance

_ACP2E-3339 - [contribution du code GitHub](https://github.com/magento/magento2/commit/a4cf5e62)_

### Analytics/Reporting, B2B

#### B2B - Le plan de site comprend des produits/catégories non affectés au catalogue partagé

Limitez les catégories et produits générés par le plan de site aux catégories et produits affectés uniquement au catalogue public partagé et/ou à la configuration des autorisations de catégorie de catalogue.

_ACP2E-2300 - [contribution du code GitHub](https://github.com/magento/magento2/commit/ea79f7dd)_

### Analytics/Création de rapports, Cloud

#### Magento ignore la plupart des transactions cron New Relic #34108

AC signale correctement les transactions liées aux tâches cron à NewRelic. Auparavant, certaines transactions liées à la tâche cron s’affichaient sous la forme « Autre transaction/Action/inconnu » dans NR

_ACP2E-3067 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/35b1b1da)_

#### La mesure dans NR pourrait être trompeuse pour les transactions de fond - Suivi de la ACP2E-3067

Les transactions en arrière-plan (cron) utiliseront le nom de l’application New Relic défini dans les paramètres de configuration

_ACP2E-3187 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/ec7e32a9)_

### B2B

#### Package 2.4.8-bêta102 L’édition Entreprise échoue avec des exceptions d’application

_AC-13501_

#### Les produits affectés au catalogue partagé ne sont pas reflétés sur le front-end lorsque l’index partiel est exécuté

Les produits affectés au catalogue partagé via l’API REST sont désormais immédiatement visibles sur storefront une fois l’indexation partielle terminée. Auparavant, les produits n’étaient visibles qu’après une réindexation complète.

_ACP2E-2139 - [contribution du code GitHub](https://github.com/magento/magento2/commit/7377de59)_

#### [Cloud] L’affichage des prix dans la version pour mobiles et pour ordinateurs de bureau n’est pas le même dans « Mes devis »

La ligne Inclure taxe inutile n&#39;apparaît plus dans le devis négociable lorsque la section du prix total du catalogue est dépensée.

_ACP2E-2873_

#### Bordures inutiles dans la section Mes commandes

Auparavant, un conteneur supplémentaire (références de commande) était créé pour appliquer des classes CSS supplémentaires, ce qui entraînait l’affichage de lignes de bordure inutiles sous le numéro de commande dans la section Mes commandes, qui n’est pas visible actuellement.

_ACP2E-3044 - [contribution du code GitHub](https://github.com/magento/magento2/commit/9af794a4)_

#### sales_clean_quotes cron supprime les devis de pour les commandes fournisseur qui n&#39;ont pas encore été approuvées

Les devis utilisés dans les commandes fournisseur ne seront pas supprimés par la tâche cron sales_clean_quotes

_ACP2E-3247 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/581b7ef1)_

#### Le bouton Passer une commande disparaît dans les détails du bon de commande

Correction d&#39;un problème en raison duquel le bouton Passer une commande était masqué pour les commandes fournisseur approuvées lorsqu&#39;une variation de produit avait un nombre minimum dans la carte spécifiée

_ACP2E-3465_

#### [CLOUD] Aucune entité de ce type avec l’id = 0 avec le module b2b

L’utilisateur connecté peut ajouter un produit au panier lorsque les fonctionnalités de catalogue partagé sont activées.
L’ajout précédent du produit au panier entraînait l’erreur « aucune entité de ce type avec l’id = 0 »

_ACP2E-3474_

#### Aucun message d&#39;erreur affiché pour les produits en rupture de stock lors de l&#39;ajout en bloc à partir de la liste des demandes d&#39;approvisionnement

Avant la correction, un message de réussite s’affichait, quel que soit le nombre de produits qui n’ont pas été ajoutés au panier. Désormais, des messages distincts s’affichent pour les produits qui ont été ajoutés avec succès au panier et pour les produits qui ont échoué.

_ACP2E-3562_

#### Problème lié aux mises à jour de SKU après les mises à jour planifiées entraînant des autorisations de produit incorrectes (-2 Refuser)

La modification du SKU d’un produit avec les mises à jour planifiées antérieures n’entraîne plus l’inaccessibilité du produit pour les clients du catalogue partagé autorisés à voir le produit.

_ACP2E-3628_

### B2B, Catalogue

#### Produits/catégories visibles lors de la réindexation lors de l’utilisation de NoDDL et des autorisations de catégorie

Évitez d’afficher sur les catégories restreintes de storefront et leur contenu pendant l’indexation des autorisations de catalogue.

_ACP2E-2860_

### B2B, Framework

#### Le filtrage de la grille d’entreprise, puis la tentative d’exportation CSV de grille échoueront et généreront une exception

Le système permet désormais d’exporter au format CSV les données de la grille Entreprises dans le panneau d’administration, même lorsque des filtres tels que « Solde restant à payer » et « Type d’entreprise » sont appliqués. Auparavant, l’application de certains filtres et la tentative d’exportation des données de la grille entraînaient un échec et une exception.

_AC-9607 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/44cef3a9)_

### B2B, GraphQL

#### [Cloud] Impossible de définir custom_attributes lors de la création de la société via l’appel GraphQL

Après le correctif, il est possible de définir l’attribut « custom_attributes » pour l’administrateur de la société lors de la création de la société à l’aide d’une requête GraphQL.

_ACP2E-3391_

### Braintree

#### Le bouton Passage en caisse express d’administration est désactivé.

_AC-14293_

#### Payer via LPM

Le système effectue désormais correctement le rendu des modes de paiement locaux (LPM) lors du chargement initial, même lorsque les adresses d’expédition et de facturation d’un client connecté ne correspondent pas, ce qui garantit un processus de passage en caisse fluide. Auparavant, une incohérence entre les adresses d’expédition et de facturation d’un client empêchait le rendu du LPM, ce qui entraînait des perturbations potentielles lors du passage en caisse.

_LOT-3367_

#### Configurable avec Virtual en tant que produit enfant

Le système permet désormais des méthodes de paiement express pour les produits configurables qui ont un produit enfant virtuel, assurant ainsi un processus de paiement fluide. Auparavant, les modes de paiement express n’étaient pas disponibles lorsqu’un produit configurable avec un produit enfant virtuel était ajouté au panier.

_LOT-3368_

#### Erreur d’échec de la vérification du fichier CSV

_LOT-3369_

#### Mise en chambre forte via le compte Area Issues 247

Le système permet désormais aux clients d’enregistrer les informations de leur nouvelle carte ou de leur compte PayPal sur plusieurs sites web sans rencontrer d’erreurs d’autorisation. Auparavant, les clients ne pouvaient pas enregistrer les nouveaux modes de paiement sur différents sites web et un message d’erreur d’autorisation leur était présenté.

_LOT-3370_

#### Envoyer à une adresse d&#39;un autre pays

Le système permet désormais de traiter les transactions sans erreur lors de l’expédition vers une adresse d’un autre pays, ce qui garantit un processus de passage en caisse fluide. Auparavant, toute tentative d’expédition vers une adresse provenant d’un autre pays entraînait des erreurs de console, même si aucune erreur visible n’était générée sur le serveur frontal.

_LOT-3371_

#### Carte de crédit - Fonction de démontage

Le système gère désormais correctement la désactivation des composants PayPal Braintree lorsqu’un client revient de la page de paiement à la page d’expédition, ce qui évite les erreurs et garantit le rendu correct des boutons PayPal Express. Auparavant, le fait de revenir à la page d’expédition à partir de la page de paiement entraînait parfois une erreur lors de la tentative de démontage des composants PayPal Braintree.

_LOT-3372_

#### Rappel d&#39;expédition pour PayPal Express

Le système affiche désormais correctement les modes d&#39;expédition disponibles dans la fenêtre modale PayPal Express, ce qui permet aux clients de sélectionner leur mode d&#39;expédition préféré avant de passer à la page de révision ou de terminer leur transaction. Auparavant, aucune méthode d&#39;expédition n&#39;était disponible dans la fenêtre modale PayPal Express, ce qui obligeait les clients à sélectionner une méthode d&#39;expédition sur une page de révision distincte avant de pouvoir terminer leur transaction.

_LOT-3373_

### Bundle

#### Le nombre de messages d&#39;erreur de validation du lot Storefront est supérieur à 1

Le système n’affiche désormais qu’un seul message d’erreur de validation lorsque l’utilisateur clique sur le bouton « Ajouter au panier » sans cocher d’option pour un produit groupé. Auparavant, le système affichait plusieurs messages d’erreur de validation pour chaque case à cocher désélectionnée.

_AC-10826 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/3ea26621)_

#### Exception Magento générée dans certains cas de test liés à l’ordre

Le système gère désormais correctement l’étape « sendGuestPaymentInformation » dans divers cas de test, ce qui empêche la génération d’exceptions Magento. Auparavant, ces exceptions se produisaient en raison d’un mode de paiement nul, ce qui provoquait des échecs dans plusieurs cas de test.

_AC-13321_

### Panier et passer en caisse

#### L’exception n’est pas correctement gérée lors de l’ajout d’un produit au panier sur la page Comparer les produits .

Le système gère désormais correctement les exceptions lors de l’ajout d’un produit au panier à partir de la page Comparer les produits , affichant un message du gestionnaire de messages dans le contrôleur. Auparavant, une exception entraînait le renvoi d’une page codée en JSON au lieu d’être correctement capturée et gérée.

_AC-10660 - [Problème GitHub](https://github.com/magento/magento2/issues/38200) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38257) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/0c53bbf7)_

#### GTag n&#39;envoie pas les prix et totaux des transactions.

Le système envoie désormais correctement les prix et totaux des transactions à Google Tag lorsque GTag est activé, assurant ainsi un suivi précis des données d’e-commerce. Auparavant, la devise était incorrectement envoyée dans le cadre des commandes « all », plutôt que d’être associée à la commande individuelle.

_AC-10698 - [Problème GitHub](https://github.com/magento/magento2/issues/37348) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37504) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37349)_

#### [Problème] [Passage en caisse] directives de dépendance mises à jour dans le modèle d&#39;e-mail de paiement ayant échoué

Le système omet désormais correctement l’adresse et le mode d’expédition du modèle d’e-mail de paiement en échec pour les produits virtuels, en s’assurant que seules les informations pertinentes sont incluses dans l’e-mail. Auparavant, l’e-mail de paiement ayant échoué pour les produits virtuels incluait incorrectement l’adresse et le mode d’expédition.

_AC-11641 - [Problème GitHub](https://github.com/magento/magento2/issues/32781) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/32511)_

#### La connexion à Magento 2 lors du passage en caisse avec l’erreur de console de dons client existant dans le navigateur Firefox

Le système permet désormais aux utilisateurs de se connecter pendant le processus de passage en caisse sans rencontrer d&#39;erreur de console dans le navigateur Firefox. Auparavant, toute tentative de connexion en tant que client existant lors du passage en caisse entraînait une erreur de console dans Firefox.

_AC-11717 - [Problème GitHub](https://github.com/magento/magento2/issues/38557) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39509)_

#### [Problème] régression des règles de vente dans la version 2.4.7

Le système valide désormais correctement les règles de vente, ce qui empêche l’application d’un code de coupon à un panier lorsque la condition du produit ne correspond à aucun nom de produit. Auparavant, une règle de vente pouvait être appliquée et une remise accordée sur le montant de l’expédition, même si la condition du produit ne correspondait à aucun nom de produit.

_AC-11876 - [Problème GitHub](https://github.com/magento/magento2/issues/38671) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/0574ac23)_

#### [Problème] Règle de vente Calcul CartFixed : montant de remise incorrect

Le système calcule désormais correctement le montant de la remise pour les règles de vente avec des montants fixes de panier, en veillant à ce que des remises précises soient appliquées quelles que soient les modifications apportées aux articles du panier. Auparavant, le montant de la remise pouvait varier de manière incorrecte lorsque les articles du panier étaient modifiés, ce qui entraînait parfois des remises considérablement plus importantes que prévu.

_AC-11914 - [Problème GitHub](https://github.com/magento/magento2/issues/38694) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/581b7ef1)_

#### [Problème ] le chargeur bloque les méthodes d’expédition après la modification du code postal et les règles de validation des taux d’expédition

Le système gère désormais correctement les méthodes d’expédition personnalisées sans règles de validation des taux d’expédition, en veillant à ce que le chargeur ne bloque pas les méthodes d’expédition après le changement du code postal dans l’adresse d’expédition lors du passage en caisse. Auparavant, la modification du code postal dans l’adresse d’expédition lors du passage en caisse entraînait le blocage du chargeur des méthodes d’expédition et ne disparaissait pas lorsque des méthodes d’expédition personnalisées sans règles de validation des taux d’expédition étaient utilisées.

_AC-11993 - [Problème GitHub](https://github.com/magento/magento2/issues/38742) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/1bafc571)_

#### La fonctionnalité de code promotionnel ne fonctionne pas correctement dans la page de passage en caisse de Magento 2.4.7.

Le système active désormais le champ d’entrée code de remise/coupon sur la page de passage en caisse pour les produits virtuels et téléchargeables, ce qui permet aux utilisateurs d’appliquer des codes de remise comme prévu. Auparavant, la saisie du code de remise/coupon était désactivée et le texte du titre du bouton affichait « Annuler le coupon », ce qui empêchait les utilisateurs d’appliquer des codes de remise.

_AC-12170 - [Problème GitHub](https://github.com/magento/magento2/issues/38826) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/1bafc571)_

#### La case à cocher Termes et conditions n’autorise pas HTML sur storefront

Le système prend désormais en charge le formatage d’HTML dans la case à cocher « Termes et conditions » du storefront, ce qui permet une personnalisation et une lisibilité améliorées. Auparavant, le texte de la case à cocher s’affichait au format texte brut, ignorant les balises HTML utilisées.

_AC-12479 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/6cfb9b6b)_

#### La règle de prix de panier créée pour l’utilisateur connecté est incorrectement appliquée pour l’utilisateur non connecté

Le système supprime désormais correctement la règle de prix du panier pour les utilisateurs connectés lorsqu’ils sont automatiquement déconnectés en raison de l’expiration du cookie, en veillant à ce que la remise ne soit pas appliquée aux utilisateurs non connectés. Auparavant, la règle de prix du panier était toujours appliquée même lorsque l’utilisateur était déconnecté, ce qui entraînait l’application d’une remise incorrecte aux utilisateurs non connectés.

_AC-12541 - [Problème GitHub](https://github.com/magento/magento2/issues/38944) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/7d5e3906)_

#### [Problème] [FONCTIONNALITÉ] Optimisation des performances des grands paniers en empêchant...

Le système optimise désormais les performances des paniers volumineux en empêchant les appels getActions en double, ce qui améliore la vitesse et l’efficacité des opérations sur les paniers. Auparavant, pour un panier contenant plusieurs articles, la fonction getActions était appelée plusieurs fois, ce qui ralentissait les performances du système.

_AC-13302 - [Problème GitHub](https://github.com/magento/magento2/issues/39292) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39290)_

#### Le produit du registre des cadeaux ne s&#39;affiche pas correctement

_AC-13797_

#### Le produit du registre des cadeaux ne s&#39;affiche pas correctement

_AC-13841_

#### TVA de traduction dans le moteur de rendu d&#39;adresses

Le système permet désormais de traduire les termes « VAT », « T » et « F » dans les moteurs de rendu d’adresse, ce qui permet aux utilisateurs et aux utilisatrices de traduire ces termes dans la langue spécifique du magasin. Auparavant, ces termes n’étaient pas traduisibles, ce qui obligeait les utilisateurs à recourir à une solution de contournement.

_AC-8103 - [Problème GitHub](https://github.com/magento/magento2/issues/36942) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/36943)_

#### Dupliquer les commandes avec le même ID de devis en même temps avec peu de décalage horaire

Correction du problème lorsque les clients Adobe Commerce rencontraient des commandes en double placées avec le même QuoteID

_ACP2E-2055 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/f89a447e)_

#### Panier persistant effacé lors de l’étape de passage en caisse

Après la correction, la sélection du mode de paiement lors du passage en caisse sans être connecté ne met pas fin à la session persistante.

_ACP2E-2470 - [contribution du code GitHub](https://github.com/magento/magento2/commit/a4fbf702)_

#### La réorganisation ajoute le produit non affecté au panier.

Auparavant, pour les différents magasins, les produits pouvaient être réorganisés à partir de l’autre magasin. Une fois ce correctif appliqué, seul le même magasin , le même produit de la portée peut être réorganisé lorsque le partage du compte client est activé

_ACP2E-2518 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/f89a447e)_

#### Dans l’administration, le « Panier » sur le côté gauche n’est pas mis à jour lors de la sélection des articles et « Déplacer vers le panier » sur le côté droit

Le « Panier » sur le côté gauche est mis à jour lors de la sélection des articles et « Déplacer vers le panier » sur le côté droit dans le côté administrateur. Auparavant, cette fonctionnalité ne fonctionnait pas, car les éléments de panier transformés ne devenaient pas vides à partir de la session.

_ACP2E-2620 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/39d54c2d)_

#### [Cloud] Règle de vente non appliquée à la première commande de livraison multiple

Après la correction, la remise s&#39;affiche correctement pour chaque commande du même devis multi-expédition.

_ACP2E-2646 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/f89a447e)_

#### Les requêtes [Cloud] en production parallèle visant à ajouter le même produit au panier entraînent la création de deux éléments distincts dans l’API Cart REST

Le système traite désormais correctement plusieurs demandes parallèles pour ajouter le même produit au panier dans un seul élément de ligne, ce qui empêche la création d’éléments de ligne distincts pour le même SKU. Auparavant, la réalisation de requêtes parallèles pour ajouter le même produit au panier via l’API REST entraînait plusieurs éléments de ligne pour le même SKU.

_ACP2E-2664 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/f89a447e)_

#### Problème de commande depuis Gift Registry Magento 2.4.4 Enterprise/Commerce

Le problème empêchant l&#39;achat réussi d&#39;un produit à partir d&#39;un registre des cadeaux a été résolu, ce qui permet de passer des commandes et de mettre à jour le registre des cadeaux de manière appropriée. Auparavant, une erreur se produisait lorsque vous tentiez de passer une commande dans un registre des cadeaux, ce qui empêchait la conclusion de l’achat.

_ACP2E-2676 - [Problème GitHub](https://github.com/magento/magento2/issues/35432)_

#### Obtention Impossible d’envoyer le cookie. Taille des &#39;messages-image&#39; lors de la tentative de réorganisation

Le processus de réorganisation ne génère pas ses propres erreurs pour le moment. Elle s’appuie sur les vérifications d’articles intégrées de la liste du panier.

_ACP2E-2704 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/ba25af8a)_

#### L’adresse de livraison par défaut n’est pas sélectionnée lors du passage en caisse

L’adresse de livraison par défaut est désormais sélectionnée comme événement dans le contexte de l’activation de la recherche d’adresses.

_ACP2E-2798 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/7e0e5582)_

#### Problème d’api [CLOUD] graphql addProductsToCart avec l’option personnalisée

GraphQL ajoute correctement au panier le même produit avec différentes options personnalisées

_ACP2E-2897 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/c971859e)_

#### [Cloud] Les règles relatives aux produits associés ne fonctionnent pas lors du changement d’affichage de la boutique

Le problème a été corrigé en confirmant que la valeur de la propriété personnalisée est reçue avec succès sur la page du panier. Auparavant, elle n’était pas récupérée correctement lors du changement entre les magasins sur la page du panier de storefront.

_ACP2E-2917_

#### Plusieurs adresses ajoutées au compte lors du passage en caisse en tant que nouveau client

Le système enregistre désormais une seule fois une nouvelle adresse client si la commande n’a pas été créée, ce qui empêche la création de plusieurs adresses identiques en cas d’erreurs de placement de commande. Auparavant, le système enregistrait une nouvelle adresse chaque fois qu’une tentative de placement de commande était effectuée, que la commande ait été créée avec succès ou non.

_ACP2E-2923 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/001e5188) - [Contribution du code GitHub](https://github.com/magento/inventory/commit/2ebcef39)_

#### La réorganisation de la commande client via le formulaire de commande invité génère un panier vide

Auparavant, lorsque le client passait une nouvelle commande sur la page Commandes et retours, il était redirigé vers la page de connexion. Une fois ce correctif appliqué, le client enregistré est correctement redirigé vers la page Afficher le panier lors d’une nouvelle commande. Le flux fonctionne de la même manière que pour les clients invités.

_ACP2E-3004 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/6a185204)_

#### Un utilisateur administrateur avec des ressources de rôle limitées ne peut pas afficher les paniers

Auparavant, l’administrateur restreint ne pouvait pas voir le panier abandonné dans le panneau d’administration d’un site web associé. Une fois ce correctif appliqué, l’administrateur restreint peut voir le panier abandonné dans le panneau d’administration.

_ACP2E-3025 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/d1f7dc95)_

#### [Cloud] commande rapide : performances élevées des SKU

Les performances de passage en caisse ont été améliorées lorsque les attributs utilisés dans les conditions des règles de prix de panier ne sont pas présents pour tous les produits et lorsque la fonctionnalité MAP (Prix minimum annoncé) est activée.

_ACP2E-3176 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/66dea0de)_

#### Éléments dupliqués dans le panier

Le système traite désormais correctement plusieurs demandes parallèles pour ajouter le même produit au panier dans un seul élément de ligne, ce qui empêche la création d’éléments de ligne distincts pour le même SKU. Auparavant, la réalisation de requêtes parallèles pour ajouter le même produit au panier sur Storefront entraînait plusieurs éléments de ligne pour le même SKU.

_ACP2E-3211 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/66dea0de)_

#### L’e-mail de confirmation de commande de passage en caisse est envoyé aux e-mails saisis en prénom/nom

L’e-mail de confirmation de commande de passage en caisse, précédemment envoyé lorsqu’un modèle de type e-mail était saisi dans les champs Prénom et Nom, n’est plus envoyé.

_ACP2E-3296 - [contribution du code GitHub](https://github.com/magento/magento2/commit/5184c067)_

#### Le formulaire d&#39;adresse de livraison de passage en caisse est mis à jour avec une adresse incorrecte

shippingAddressFromData est désormais enregistré dans le stockage local par site web. Auparavant, une adresse du mauvais site web pouvait être automatiquement renseignée dans le formulaire d’adresse d’expédition lors du passage en caisse si un code de magasin était utilisé dans l’URL et que le passage en caisse était initié à partir de plusieurs sites web au cours de la même session de personne invitée.

_ACP2E-3402 - [contribution du code GitHub](https://github.com/magento/magento2/commit/078c387e)_

#### [CLOUD] Le passage en caisse ne conserve pas l’adresse de facturation sélectionnée lorsque la recherche d’adresses est activée

La page de paiement du paiement en caisse conserve désormais l’adresse de facturation sélectionnée lorsque la recherche d’adresse est activée. Auparavant, si la valeur « Limite du nombre d’adresses client » était configurée sur 1 et que le client possède plusieurs adresses, l’adresse de facturation sélectionnée disparaissait après le rechargement de la page.

_ACP2E-3405_

#### Produit de carte cadeau | Fusion de panier en cours de fusion de cartes-cadeaux

Les produits de carte cadeau sont désormais correctement fusionnés dans le panier

_ACP2E-3407 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/88660e79)_

#### La persistance du panier n’est pas respectée lors de la déconnexion

Ajout de la fonctionnalité Mémoriser mon identifiant client dans la fenêtre contextuelle d’authentification et les connexions à la caisse.

_ACP2E-3415 - [contribution du code GitHub](https://github.com/magento/magento2/commit/344fce23)_

#### Les données de devis existantes ne sont pas mises à jour / non visibles, mais créent un nouvel enregistrement de devis lorsque trigger_recollect = 1

Les articles du panier du client ne disparaissent plus suite à la suppression d’un produit après son ajout au panier.

_ACP2E-3488 - [contribution du code GitHub](https://github.com/magento/magento2/commit/1984c61c)_

#### Lorsqu&#39;un article d&#39;enregistrement cadeau est acheté, le client voit des articles qui ne figurent pas dans son registre

La mise à jour du registre des cadeaux n’inclut plus les objets qui n’appartiennent pas au registre des cadeaux.

_ACP2E-3495_

#### [Cloud] problème avec la fenêtre contextuelle de confirmation « Tout supprimer » suppression des éléments du panier sans confirmation

Désormais, cliquer sur le bouton « Tout supprimer » pour les produits nécessitant de l’attention invite une fenêtre contextuelle de confirmation à s’assurer que les éléments ne sont supprimés qu’avec votre confirmation. Auparavant, les éléments étaient supprimés immédiatement sans confirmation

_ACP2E-3510_

#### [CLOUD] Fonctionnalité du bouton de réorganisation

La réorganisation d&#39;une commande de la zone d&#39;administration ajoutera désormais des produits en stock au devis, même si certains produits de la commande d&#39;origine ne sont plus en stock. Avant la correction, aucun produit n’était ajouté au nouveau devis si le produit sans stock se trouvait dans la commande d’origine.

_ACP2E-3618 - [contribution du code GitHub](https://github.com/magento/magento2/commit/a52ff98f)_

#### Les magasins de recherche ne fonctionnent pas par code postal.

La recherche de lieux de retrait par code postal ne fonctionnait pas correctement pour les localisations en néerlandais. Après la correction, la recherche de l’emplacement de retrait fournit des résultats en fonction du code postal.

_ACP2E-3622 - [contribution du code GitHub](https://github.com/magento/magento2/commit/344fce23)_

### Panier et passer en caisse, passage en caisse/passage en caisse d’une page

#### Le champ [BUG aléatoire] E-mail n’est pas rendu ou prend beaucoup de temps s’afficher sur la page Expédition ou paiement du paiement du paiement

Commerce effectue désormais le rendu du champ **[!UICONTROL Email]** sur les pages de paiement et d’expédition de passage en caisse comme prévu. Auparavant, ce champ était absent ou son rendu était lent.

_AC-9386 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/e1babcfd)_

### Panier et passer en caisse, commander

#### Le sélecteur de date pour un produit avec plusieurs options personnalisables avec des champs de date ne fonctionne pas lors de la commande auprès de l’administrateur

Le système affiche désormais correctement le sélecteur de date pour tous les champs de date lors de la configuration d’un produit avec plusieurs options de date personnalisables dans le processus de création de commande administrateur. Auparavant, le sélecteur de date s’affichait uniquement pour le premier champ de date, laissant les champs restants sans sélecteur de date.

_ACP2E-3097 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/b21e5d91)_

### Panier et passer en caisse, expédition

#### Achat instantané « livraison la moins chère » cassé pour les produits configurables

La fonction d’achat instantané a incorrectement sélectionné l’option de livraison en magasin la plus coûteuse pour les produits configurables au lieu de la méthode de taux forfaitaire la moins chère. Ce correctif garantit que la méthode d’expédition correcte est choisie en fonction du prix réel. »

_AC-12119 - [Problème GitHub](https://github.com/magento/magento2/issues/38811) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38819) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/29fe9097)_

### Catalogue

#### Le nettoyage de la table de base de données cron_schedule ne nettoie pas les tâches non existantes

Le système nettoie désormais automatiquement la table de base de données cron_schedule, supprimant les entrées des tâches qui n&#39;existent plus dans le système. Vous obtiendrez ainsi des performances optimales en conservant un nombre minimal de lignes dans le tableau. Auparavant, les entrées des tâches des modules inactifs ou supprimés n’étaient pas nettoyées, ce qui entraînait une accumulation de données inutile dans le tableau cron_schedule.

_AC-10910 - [Problème GitHub](https://github.com/magento/magento2/issues/38217) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38693)_

#### Le prix de niveau n&#39;est pas supprimé du produit configurable

Le système supprime désormais correctement le prix de niveau d’un produit lorsqu’il est converti d’un produit simple en un produit configurable, assurant ainsi un affichage précis des prix sur le serveur frontal. Auparavant, le prix de niveau d’un produit configurable n’était pas supprimé lorsqu’un produit était converti d’un produit simple en produit configurable, ce qui entraînait une incohérence du prix affiché.

_AC-10953 - [Problème GitHub](https://github.com/magento/magento2/issues/38390) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38427)_

#### Le WYSIWYG de description de catégorie est vide dans un magasin autre que le magasin par défaut

Le système enregistre et affiche désormais correctement la description de la catégorie dans l’éditeur WYSIWYG lors de la modification d’une catégorie au niveau de l’affichage du magasin. Auparavant, l’éditeur WYSIWYG s’affichait vide après l’enregistrement d’une description de catégorie au niveau de l’affichage du magasin.

_AC-11804 - [Problème GitHub](https://github.com/magento/magento2/issues/38622) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38623)_

#### Impossible de réorganiser les produits configurables avec une case à cocher sélectionnée pour l’option personnalisée

Le système traite désormais correctement la réorganisation des produits configurables avec une seule option personnalisée de case à cocher sélectionnée, ce qui permet de créer un panier avec succès. Auparavant, toute tentative de réorganisation de ces produits entraînait une erreur et empêchait l’ajout d’articles dans le panier.

_AC-11970 - [Problème GitHub](https://github.com/magento/magento2/issues/38736) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/1d144bce)_

#### [Problème] Correction du libellé de l’élément de filtre sur la navigation superposée

Le système utilise désormais correctement les mots « élément » et « éléments » dans l’élément de filtre de navigation superposé, ce qui améliore la clarté et la précision des descriptions des filtres. Auparavant, ces mots n’étaient pas utilisés correctement, ce qui pouvait prêter à confusion pour les utilisateurs et utilisatrices qui parcouraient les options de filtre.

_AC-12076 - [Problème GitHub](https://github.com/magento/magento2/issues/38789) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37852)_

#### Le format de date et d’heure de l’option personnalisée ne fonctionne pas

Le système applique désormais correctement le format de date configuré aux options personnalisées de produit de type Date, en s’assurant que le format de date s’affiche correctement sur le front-end. Auparavant, les modifications apportées à la configuration du format de date n’étaient pas répercutées sur le front-end pour les options personnalisées de produit de type Date.

_AC-12164 - [Problème GitHub](https://github.com/magento/magento2/issues/32990) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38925)_

#### Options de liste déroulante manquantes

Le système affiche désormais correctement toutes les valeurs dans la liste déroulante lors de la création d’un nouvel attribut avec plus de 20 valeurs. Auparavant, seules les 20 premières valeurs ou une autre valeur de page sélectionnée s’affichait, ce qui entraînait l’absence des valeurs restantes.

_AC-13068 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/47b448e2)_

#### [Problème ] utilisez l’ID de magasin actuel pour le cache d’exécution de catégorie

Le système utilise désormais correctement l’ID de magasin actuel pour le cache d’exécution de catégorie, ce qui empêche le remplacement des données lorsque l’émulation est utilisée ou que le code personnalisé enregistre la catégorie dans différents magasins. Auparavant, l’objet stocké dans l’exécution pouvait provenir d’un magasin incorrect, ce qui entraînait le remplacement des données.

_AC-13296 - [Problème GitHub](https://github.com/magento/magento2/issues/39310) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/36394)_

#### bin/magento sampledata :deploy —no-update renvoie une exception

Le système accepte désormais correctement une valeur booléenne lors de l’utilisation de l’option —no-update dans la commande sampledata:deploy, ce qui empêche toute erreur lors du déploiement des données d’exemple. Auparavant, une erreur était générée lors de l’utilisation de cette commande, car le système s’attendait incorrectement à une valeur entière.

_AC-13324 - [Problème GitHub](https://github.com/magento/magento2/issues/39344) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39345)_

#### [Problème] Corrigez l’utilisation du type de cache EAV

Le système utilise désormais correctement le type de cache EAV dans tous les emplacements pertinents, ce qui garantit une mise en cache des données cohérente et efficace. Auparavant, le type de cache EAV n’était pas utilisé de manière cohérente, ce qui entraînait des inefficacités et des incohérences potentielles dans la mise en cache des données.

_AC-13355 - [Problème GitHub](https://github.com/magento/magento2/issues/32322) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/31264)_

#### La recherche avancée du catalogue avec des données vides accède à la page de résultats de recherche[branche 2.4.dev]

Le système conserve désormais correctement les utilisateurs sur la page Recherche avancée et affiche un message d’erreur lorsqu’ils tentent d’effectuer une recherche sans saisir de données. Auparavant, l’exécution d’une recherche vide redirigeait les utilisateurs vers la page de recherche avancée du catalogue avec un message les invitant à modifier leur recherche.

_AC-13596 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/6cfb9b6b)_

#### [Problème] Mise en page du produit basée sur attribute_set

Le système permet désormais d’ajuster la mise en page du produit en fonction du jeu d’attributs, offrant ainsi un moyen plus pratique et plus efficace de gérer l’affichage du produit dans le magasin frontal. Auparavant, la mise en page ne pouvait être ajustée que par SKU ou par type de produit, ce qui n’était pas toujours pratique pour de nombreux produits ou articles spécifiques.

_AC-13622 - [Problème GitHub](https://github.com/magento/magento2/issues/38790) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/36244)_

#### Clé unique manquante dans la table eav_attribute_option_value

Le système inclut désormais une clé unique sur les colonnes &#39;option_id&#39; et &#39;store_id&#39; dans la table &#39;eav_attribute_option_value&#39;, ce qui empêche qu&#39;une option ait plusieurs valeurs pour la même vue de magasin. Auparavant, un code incorrect pouvait entraîner l’affichage de plusieurs valeurs pour une même vue de magasin, ce qui provoquait des problèmes lors de la modification de produits ou d’attributs.

_AC-6738 - [Problème GitHub](https://github.com/magento/magento2/issues/24718) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/28796)_

#### [Problème ] utilisez la classe de visibilité pour l’indexeur de produit de catégorie, au lieu des valeurs codées en dur

Le système utilise désormais la classe de visibilité pour l’indexeur de produits de catégorie au lieu des valeurs codées en dur, ce qui améliore la modularité. Auparavant, les valeurs codées en dur étaient utilisées dans l’indexeur de produits de catégorie, ce qui limitait la flexibilité et l’adaptabilité.

_AC-8297 - [Problème GitHub](https://github.com/magento/magento2/issues/37200) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37199)_

#### Le code de devise n’a pas été modifié dans le widget Nouveau produit.

Le système met désormais correctement à jour le code de devise dans le widget Nouveau produit lorsque la devise est modifiée dans le serveur frontal, assurant ainsi la cohérence de l’affichage de la devise sur l’ensemble du site. Auparavant, la modification de la devise dans le front-end n’affectait pas le code de devise affiché dans le widget Nouveau produit.

_AC-9375 - [Problème GitHub](https://github.com/magento/magento2/issues/37898) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37899)_

#### Le prix normal ne s’affiche pas sur le PLP pour le produit configurable

Le prix normal est désormais affiché sur les pages de liste de produits pour les produits configurables qui ont des produits enfants avec un prix spécial.

_ACP2E-2224 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a4fbf702)_

#### Les informations de stock ne s’affichent pas correctement sur la grille de marchandisage visuel.

Le stock s’affiche désormais en fonction du magasin sélectionné.

_ACP2E-2478 - [contribution du code GitHub](https://github.com/magento/inventory/commit/bdbf97ea)_

#### Le contenu du widget n’est pas mis à jour sur la page cms.

Le système met désormais à jour le contenu du widget sur une page CMS lorsqu’un produit est défini comme nouveau et enregistré, en s’assurant que la page affiche la collection de produits mise à jour. Auparavant, la page n’était pas mise à jour pour afficher le nouveau produit en raison d’identités de cache incorrectes utilisées pour le widget dans le cache.

_ACP2E-2621 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/f89a447e)_

#### Problèmes d’enregistrement de la tarification avancée sur les produits groupés

Offre groupée d&#39;amélioration des performances d&#39;économie de produits.

_ACP2E-2630 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/b2286ecf)_

#### [On-Premise] Le processus de réindexation est inefficace lors de la création de règles de prix de catalogue

Désormais, l’enregistrement de la règle de prix de catalogue n’invalide pas les indexeurs, mais réindexe uniquement les produits affectés

_ACP2E-2652 - [contribution du code GitHub](https://github.com/magento/magento2/commit/f89a447e)_

#### Mise à jour de l’heure des attributs de produit de type Date et Heure via l’importation CSV

Désormais, les attributs datetime auront une partie temporelle dans les données exportées. Il sera également possible de mettre à jour l’heure de ces attributs à l’aide de l’importation. De même, si l’option « Enceinte de champs » est activée, les valeurs d’attribut dans la colonne « additional_attributes » sont placées entre guillemets doubles.

_ACP2E-2679 - [Problème GitHub](https://github.com/magento/magento2/issues/38306) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/ea79f7dd)_

#### Aucun message d’erreur approprié lorsque l’identifiant du site web est incorrect dans la requête

Désormais, le message d’erreur approprié a été ajouté pour s’afficher lorsque l’identifiant du site web est incorrect dans la requête. Auparavant, il n’existait aucune validation lorsque l’ID de site web était incorrect dans la requête.

_ACP2E-2689 - [contribution du code GitHub](https://github.com/magento/magento2/commit/39d54c2d)_

#### L’image du produit est perdue après la suppression d’une mise à jour planifiée existante qui n’affecte pas l’image

Les images de produit ne sont pas supprimées lors de la suppression de la mise à jour d’évaluation.

_ACP2E-2785 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/c8931218)_

#### [Cloud] Prix de produit groupé incorrect lorsqu’il est utilisé avec des prix de niveau

Auparavant, lors du calcul de certaines remises en pourcentage arrondies à 2 décimales maximum, générait différents prix finaux pour le panier et la page de liste de produits/page de détails des produits. Une fois ce correctif appliqué, le prix final du bundle du produit est le même que dans les pages de détails du produit, de liste des produits et de panier.

_ACP2E-2799 - [Problème GitHub](https://github.com/magento/magento2/issues/38091) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/b2286ecf)_

#### La règle de promotions de catalogue ne fonctionne pas avec l&#39;attribut quantity_and_stock_status

L’attribut quantity_and_stock_status sera désormais pris en compte par la règle de promotion du catalogue, qui n’était pas prise en compte auparavant lors de la génération d’un nouveau produit du côté administrateur.

_ACP2E-2805 - [Problème GitHub](https://github.com/magento/magento2/issues/35627) - [Contribution du code GitHub](https://github.com/magento/inventory/commit/cf34971d)_

#### Les valeurs de la colonne updated_at de l’entité produit ne sont pas mises à jour lors de la mise à jour du prix via l’API REST

La colonne « Dernière mise à jour à » du produit depuis l’administration est mise à jour à la date et à l’heure appropriées lors de la mise à jour des produits existants via l’API REST. Auparavant, la colonne « Dernière mise à jour à » n’était pas mise à jour correctement.

_ACP2E-2837 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/39d54c2d)_

#### Il est possible de définir des valeurs non uniques par le biais de l’importation de produits

Le système applique désormais correctement la contrainte de valeur unique pour les attributs de produit uniques lors de l’importation du produit, ce qui empêche d’avoir des valeurs en double pour cet attribut. Auparavant, il était possible de définir des valeurs non uniques pour les attributs de produit configurés pour avoir des valeurs uniques via l’importation du produit.

_ACP2E-2840 - [Problème GitHub](https://github.com/magento/magento2/issues/38445) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/7e0e5582)_

#### Les produits sur le serveur frontal utilisent des données spécifiques au magasin lorsque le mode de magasin unique est activé

Auparavant, lorsque nous activions le mode Boutique unique pour l’affichage par défaut de la boutique, les modifications n’étaient pas migrées vers la portée au niveau du site web. Une fois ce correctif appliqué, lorsque nous activons le mode de magasin unique, les données par défaut spécifiques à la vue du magasin sont synchronisées avec les données spécifiques au niveau du site web et résolvent les conflits possibles pour les produits et les catégories.

_ACP2E-2843 - [contribution du code GitHub](https://github.com/magento/magento2/commit/c8931218)_

#### Impossible de définir « Trier par défaut » dans une catégorie à l’aide de l’API REST

Mettre à jour correctement default_sort_by sur une catégorie via une requête API REST/SOAP

_ACP2E-2857 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/57a32313)_

#### [Cloud] Le commerçant est confronté à des problèmes liés au nombre de listes de souhaits

L’ajout d’un produit à la liste de souhaits d’un magasin n’augmente plus le nombre de listes de souhaits dans d’autres magasins ouverts dans le même navigateur. Auparavant, si les deux magasins étaient chargés dans le même navigateur, le nombre de listes de souhaits augmentait également dans l’autre magasin.

_ACP2E-2871 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/3a7c4d17)_

#### La page de catégorie du serveur frontal affiche des emplacements vides lors de l’utilisation du produit groupé

Les produits groupés qui ne sont pas commercialisables dans le contexte actuel du magasin ne sont plus indexés.

_ACP2E-2874 - [Contribution du code GitHub](https://github.com/magento/inventory/commit/bc37ec76)_

#### [CLARIFICATION] Problèmes de table de séquence de produits groupés

Les enregistrements des tables de séquence de produits groupés (sequence_product_bundle_option, sequence_product_bundle_selection) sont désormais supprimés lorsque le produit groupé est supprimé ou que les options du produit groupé sont supprimées.
Auparavant, les enregistrements des tables de séquences de produits groupées n’étaient pas supprimés.

_ACP2E-2888_

#### [Cloud] Émission de devis dans l&#39;architecture multi-sites

Auparavant, une architecture multi-sites web avec différentes devises et groupes de clients ne pouvait pas appliquer correctement les remises au magasin. Une fois ce correctif implémenté, une architecture multi-sites web avec des remises sur les prix de différents groupes de clients s’appliquera correctement à différents magasins.

_ACP2E-2905 - [Problème GitHub](https://github.com/magento/magento2/issues/38506) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a4fbf702)_

#### dynamic-rows.js :658 erreur de type non interceptée : dataRecord.slice lors de la modification des produits groupés

Il n’y a aucune erreur JavaScript dans la console du navigateur lors de la suppression de l’option du produit groupé.

_ACP2E-2909 - [Problème GitHub](https://github.com/magento/magento2/issues/38505) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/93d50f8d)_

#### [Cloud] Offre groupée mauvais prix du produit dans la confirmation de commande

Le montant correct s’affiche pour les options de lot dans l’ordre sur Storefront lorsque une devise autre que la base a été utilisée.

_ACP2E-2950 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a4fbf702)_

#### Bogue d’ajout de vidéo YouTube

Les images et vidéos des produits sont configurées dans la portée globale. Étant donné que vous ne pouvez pas avoir une vidéo de produit dans une portée et pas dans une autre, le paramètre de clé API Youtube a été défini sur une portée globale.

_ACP2E-2956 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a4fbf702)_

#### [Cloud] Mise à jour de l’URL uniquement pour store_id=0

Le « Chemin d’URL » est désormais stocké avec l’ID de magasin approprié. Auparavant, l’ID de magasin était incorrect, ce qui entraînait le maintien de chemins d’URL incorrects dans la base de données lors du déplacement de catégories.

_ACP2E-2964 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/9af794a4)_

#### async.operations.all a exécuté et créé une erreur.

Les données de lien de produit incorrectes dans les appels API REST ne provoquent plus d’erreurs critiques.

_ACP2E-3009 - [contribution du code GitHub](https://github.com/magento/magento2/commit/a4fbf702)_

#### [Cloud] Problème mobile Impossible uniquement de pincer l’image PDP

Le système prend désormais en charge la fonctionnalité de pincement pour zoom sur les images de la page des détails du produit dans la vue mobile de Chrome, ce qui améliore l’expérience de l’utilisateur mobile. Auparavant, le double-appui sur l’image en mode mobile dans Chrome n’effectuait pas un zoom avant sur l’image comme prévu.

_ACP2E-3029 - [contribution du code GitHub](https://github.com/magento/magento2/commit/148c3ead)_

#### Libellé manquant dans LayeredNavigation avec le nom d&#39;option 0

Le problème a été résolu en ignorant un vérificateur de valeur vide pour la valeur d’attribut 0. Auparavant, il était considéré comme vide et provoquait le problème.

_ACP2E-3058 - [contribution du code GitHub](https://github.com/magento/magento2/commit/3a7c4d17)_

#### Les clients voient les prix d&#39;autres groupes de clients

Correction d’un problème en raison duquel les informations liées au groupe de clients étaient enregistrées dans un segment incorrect en raison de l’ancienne valeur de X-Magento-Vary dans la requête

_ACP2E-3069 - [contribution du code GitHub](https://github.com/magento/magento2/commit/d1f7dc95)_

#### Erreur lors de la suppression des options du lot

Le système supprime désormais correctement les options de lot sans déclencher d’erreur ni empêcher la page de répondre. Auparavant, toute tentative de suppression des options de lot entraînait une erreur « La page ne répondait pas » et empêchait l’enregistrement du produit.

_ACP2E-3076 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/6a185204)_

#### Problème de navigateur d&#39;autorisations de catégorie sans mémoire

L’interface utilisateur des autorisations de catégorie a été repensée afin de permettre le rendu d’un grand nombre d’autorisations à l’aide du composant d’interface utilisateur prêt à l’emploi et de la pagination. Auparavant, les autorisations de catégorie entraînaient le blocage du navigateur avec une grande quantité d’autorisations attribuées à la catégorie.

_ACP2E-3094_

#### Le fichier image [Cloud] n’existe pas dans le journal des erreurs New Relic

Le système synchronise désormais les images d’espace réservé personnalisées avec le stockage local, en s’assurant qu’elles s’affichent correctement lors de l’utilisation du stockage distant, tel qu’AWS S3. Auparavant, les images d’espace réservé personnalisées ne s’affichaient pas lors de l’utilisation du stockage distant, ce qui entraînait un affichage d’image rompu et des journaux d’erreurs.

_ACP2E-3100 - [contribution du code GitHub](https://github.com/magento/magento2/commit/d1f7dc95)_

#### Nouveaux produits Le flux RSS n&#39;est pas mis à jour avec de nouveaux produits en raison du cache

Le flux Rss pour les nouveaux produits est désormais mis à jour lorsqu’un produit est défini comme nouveau et enregistré

_ACP2E-3103 - [contribution du code GitHub](https://github.com/magento/magento2/commit/d01ee51e)_

#### La réponse GQL de la Galerie de médias du produit [Cloud] n’est pas triée par position de l’image

Le système trie désormais correctement les éléments de la galerie de médias par position dans la réponse GraphQL, en veillant à l’ordre d’affichage précis. Auparavant, les éléments de la galerie de médias n’étaient pas triés par position, ce qui entraînait un ordre d’affichage incorrect.

_ACP2E-3126 - [Problème GitHub](https://github.com/magento/magento2/issues/37671) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/b21e5d91)_

#### Les éléments de sous-catégorie [Cloud] ne sont pas affichés sur la modification de widgets sur le serveur principal d’administration

L’arborescence de catégories de la nouvelle page de widget ne devrait plus rencontrer de problèmes lors du chargement des catégories de niveau 5 et ultérieure. Auparavant, certaines catégories étaient manquantes lors du chargement de l’arborescence au-delà des catégories de niveau 5.

_ACP2E-3136 - [contribution du code GitHub](https://github.com/magento/magento2/commit/148c3ead)_

#### [cloud] Problème de zoom et de déplacement avec deux doigts sur l’appareil mobile réel

Le système assure désormais une fonctionnalité de zoom d’image cohérente sur les appareils mobiles, offrant ainsi une expérience utilisateur fluide et prévisible. Auparavant, la fonction de zoom sur l’image était incohérente et effectuait soudainement un zoom arrière après un certain point lorsqu’elle était affichée sur un appareil mobile.

_ACP2E-3198 - [contribution du code GitHub](https://github.com/magento/magento2/commit/1366ae5e)_

#### Lorsque nous annulons l’affectation des produits du catalogue partagé, les produits de la liste de souhaits ne sont pas effacés

Désormais, aucun élément n’est visible dans la liste de souhaits si un produit n’est pas disponible dans le catalogue partagé. Auparavant, la page de liste de souhaits affichait incorrectement un nombre de « 1 élément » même si aucun élément n’était réellement disponible dans la liste de souhaits.

_ACP2E-3282 - [contribution du code GitHub](https://github.com/magento/magento2/commit/5184c067)_

#### Produits connexes Tout sélectionner/Tout désélectionner Événement

Auparavant, les boutons « Tout sélectionner »/« Tout désélectionner » pour les produits associés ne fonctionnaient pas correctement si un produit était sélectionné manuellement. Après la correction, ces boutons fonctionnent désormais de manière cohérente, même après une sélection manuelle, garantissant que tous les produits sont correctement sélectionnés ou non sélectionnés.

_ACP2E-3286 - [contribution du code GitHub](https://github.com/magento/magento2/commit/fd5cf3af)_

#### [Cloud] La traduction des e-mails d’alerte Stock dans la mauvaise langue

Lors de l’envoi d’alertes de stock/prix pour un site web avec plusieurs vues de magasin dans différentes langues, la langue de la vue de magasin dans laquelle l’alerte a été créée est utilisée dans l’e-mail.

_ACP2E-3336 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a4cf5e62) - [Contribution du code GitHub](https://github.com/magento/inventory/commit/9f3e63d1)_

#### Les catégories désactivées n’ont plus leurs noms grisés dans l’arborescence des catégories

Auparavant, les catégories désactivées n’étaient pas grisées dans l’arborescence des catégories. Désormais, elles s’affichent avec un effet de gris.

_ACP2E-3350 - [contribution du code GitHub](https://github.com/magento/magento2/commit/d75cff27)_

#### Le chargement configurable du formulaire de modification de produit entraîne un délai d’expiration et un épuisement de la mémoire

Avant la correction, des variations de produit configurables étaient créées en fonction de toutes les combinaisons d’options d’attribut possibles. Dans les cas où les attributs disposaient de nombreuses options, une opération longue et gourmande en ressources s’est produite. Désormais, les variations de produit configurables sont construites en fonction des attributs de produit enfant existants. Il en résulte beaucoup moins de calculs, ce qui améliore l’utilisation des ressources.

_ACP2E-3410 - [contribution du code GitHub](https://github.com/magento/magento2/commit/078c387e)_

#### Torama ne charge pas correctement la vidéo lors de l’utilisation de Nuanciers et l’option est présélectionnée via l’URL

Les vidéos sur les produits s’affichent désormais correctement sur la page des détails des produits configurables, si l’URL contient les options sélectionnées.

_ACP2E-3454 - [contribution du code GitHub](https://github.com/magento/magento2/commit/078c387e)_

#### Le widget de carrousel PageBuilder affiche les produits qui ne correspondent pas aux conditions

La liste de produits utilisée dans les widgets respecte désormais la condition de catégorie.

_ACP2E-3461 - [contribution du code GitHub](https://github.com/magento/magento2/commit/078c387e)_

#### Erreur de validation déclenchée pour tous les produits du groupe lorsque la quantité d’un produit n’est pas valide

Désormais, l’erreur de validation est correctement déclenchée pour tous les produits du groupe lorsqu’un produit présente une quantité non valide, ce qui ne se produisait pas auparavant.

_ACP2E-3469 - [contribution du code GitHub](https://github.com/magento/magento2/commit/56463d5e)_

#### [CLOUD] Prix spécial non affiché dans le produit configurable

Après la correction, la modification de la valeur « Utilisé dans la liste de produits » pour l’attribut de prix spécial n’affecte pas l’affichage du prix spécial pour les produits configurables.

_ACP2E-3513 - [contribution du code GitHub](https://github.com/magento/magento2/commit/d4de4726)_

#### Les tables temporaires des indexeurs ne sont pas nettoyées si le processus est arrêté

Les tables temporaires de l’indexeur CatalogRule sont désormais nettoyées si le processus de l’indexeur est arrêté

_ACP2E-3516 - [contribution du code GitHub](https://github.com/magento/magento2/commit/1984c61c)_

#### [QUANS] Échecs des tests unitaires principaux dans 2.4.7-p3

Les notes de mise à jour de ce test ne sont pas nécessaires, car il s’agit d’une amélioration du test unitaire.

_ACP2E-3520 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/1984c61c)_

#### Problème de performance lors de la récupération de la quantité de stock pour les produits regroupés avec plusieurs sources

La page de modification des produits groupés et des produits groupés est désormais optimisée lorsque les produits affectés ont un grand nombre de sources de stock.

_ACP2E-3533 - [contribution du code GitHub](https://github.com/magento/inventory/commit/0208e433)_

#### Refix ACP2E-3389

Amélioration des performances de la page de catégorie d’administration pour les nombreuses catégories d’ancrage

_ACP2E-3641 - [contribution du code GitHub](https://github.com/magento/magento2/commit/982b1c42)_

### Catalogue, Contenu

#### Le cache [Cloud] n’est pas invalidé.

Auparavant, lors de l’enregistrement d’une page CMS avec une mise en page de conception mise à jour, la représentation n’était pas appropriée sur le front-end. Une fois ce correctif appliqué, la mise en page de conception appropriée est visible sur le front-end lorsque nous modifions la mise en page de conception et enregistrons la page CMS.

_ACP2E-3063 - [contribution du code GitHub](https://github.com/magento/magento2/commit/66dea0de)_

#### [Cloud] Catégories ancre/non-ancre inversées dans le widget de contenu

Auparavant, lorsque nous sélectionnions Afficher sur -> Catégories d’ancrage, toutes les catégories qui ne reflétaient pas la relation parent-enfant entre l’ancre et la non-ancre étaient affichées. Une fois ce correctif appliqué, l’option Afficher sur -> Catégories d’ancrage affiche uniquement les catégories d’ancrage (sélectionnables) et l’option Afficher sur -> Catégories non ancrées affiche les catégories non ancrées (sélectionnables)

_ACP2E-3131 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/7377de59)_

#### Catégories ne fonctionnant pas avec les widgets

Auparavant, si nous avions enregistré le bloc CMS pour différentes catégories ancre/non-ancre, il ne fonctionnait pas pour les catégories enfants lorsqu’il s’affichait sur le front-end. Une fois ce correctif appliqué, le bloc s’affiche en front-end pour différentes catégories.

_ACP2E-3152 - [contribution du code GitHub](https://github.com/magento/magento2/commit/d01ee51e)_

### Catalogue, Framework

#### Order get(Shipments|Creditmemos|Invoice)Collection - Le recouvrement ne doit pas être chargé

Le système garantit désormais que les recouvrements des expéditions et des avoirs ne sont pas préchargés lors de la récupération d&#39;une commande, ce qui permet d&#39;appliquer des filtres ou des commandes supplémentaires à ces recouvrements. Auparavant, ces collections étaient automatiquement chargées, ce qui empêchait toute modification ultérieure.

_AC-9111 - [Problème GitHub](https://github.com/magento/magento2/issues/37561) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37562)_

#### [Cloud]Suivi : incohérence dans la comparaison des données lors de la vérification des modifications apportées aux données

Auparavant, l’objet d’enregistrement était appelé à chaque fois sans modification des données (pour tout champ de données numériques, comme int/float/double). Cela déclenche l’indicateur _hasDataChanges sur true et appelle la fonction d’enregistrement. Il ne vérifie pas non plus les nombres flottants encapsulés par une chaîne. Une fois que ce correctif est appliqué, la fonction d’enregistrement n’appelle que si les données sont modifiées. La valeur de données pour int/float/double-check avec la valeur transmise à la fonction et effectue une correspondance de type stricte

_ACP2E-2949 - [contribution du code GitHub](https://github.com/magento/magento2/commit/c8931218)_

### Catalogue, GraphQL

#### Gestion des filtres de catégorie dans GraphQL : includeDirectChildrenOnly et category_uid

Seules les catégories enfants directes sont récupérées lors du filtrage par category_uid.

_ACP2E-3090 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/93d50f8d)_

#### Le tri des produits [Cloud] Graphql ne fonctionne pas

Le tri des produits GraphQl par plusieurs champs lorsque les champs sont transmis dans des variables fonctionne désormais comme prévu.

_ACP2E-3166 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/8459b17d)_

#### Les prix de niveau renvoient une valeur incorrecte dans les produits GraphQL (par rapport à Storefront)

Après la correction, les prix de niveau du produit renvoyés pour les requêtes GraphQL ont un prix par article.

_ACP2E-3312 - [contribution du code GitHub](https://github.com/magento/magento2/commit/1366ae5e)_

#### [CLOUD] B2B : problème de catégorie via GraphQL

Après la correction, la requête GraphQL Catégories renvoie les catégories avec une autorisation autorisée même si la catégorie racine ne dispose pas de l’autorisation Autoriser.

_ACP2E-3385_

### Catalogue, tarification, évaluation et prévisualisation

#### Le point d’entrée de l’API [Cloud] Prix spécial renvoie une erreur lors de la mise à jour simultanée d’un grand nombre de produits

Désormais, l’API de mise à jour en bloc des prix spéciaux crée une seule campagne pour chaque période au lieu de plusieurs mises à jour planifiées pour chaque produit et période. En outre, il prend en charge les requêtes d’API simultanées pour accélérer le traitement d’un grand nombre de SKU.

_ACP2E-2672 - [contribution du code GitHub](https://github.com/magento/magento2/commit/f89a447e)_

### Catalogue, produit

#### L’arborescence de sélection de catégorie dans la modification du produit ne suit pas le même ordre que celui défini dans Catalogue->Catégories .

Le système affiche désormais correctement l’arborescence de sélection des catégories dans la section d’édition du produit, dans l’ordre défini dans Catalogue->Catégories, ce qui facilite l’administration des produits dans les catalogues volumineux. Auparavant, l’arborescence de catégories de la section de modification de produits s’affichait dans l’ordre de création des catégories, quel que soit l’ordre d’affichage défini dans Catalogue->Catégories.

_AC-7050 - [Problème GitHub](https://github.com/magento/magento2/issues/36101) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/36104)_

### Catalogue, SEO

#### URL canonique incorrecte pour la catégorie lorsque la page > 1

Auparavant, l’URL canonique du contenu multi-pages ne fonctionnait pas correctement, affichant systématiquement l’URL de base. Cependant, une fois le correctif implémenté, l’URL canonique pour le contenu multi-pages affiche désormais correctement l’URL avec l’ID de page.

_ACP2E-3653 - [contribution du code GitHub](https://github.com/magento/magento2/commit/982b1c42)_

### Catalogue, recherche

#### Les produits ne s’affichent pas dans la catégorie et la recherche, mais les liens directs fonctionnent

Auparavant, l’attribut personnalisé Oui/Non avec price_* attribute_code ne fonctionnait pas avec l’indexation. Après ce correctif, l’attribut personnalisé Oui/Non fonctionne comme prévu.

_ACP2E-2757 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/ba25af8a)_

#### [Cloud] Erreur de recherche élastique sur certaines pages de catégorie

Auparavant, avec le ticket de configuration mentionné, lorsque nous fixions le prix 0 pour plusieurs produits, une exception était générée sur la page de catégorie front-end. Une fois ce correctif appliqué lorsque le prix de plusieurs produits est égal à 0 et que nous chargeons la page de catégorie sur le front-end, aucune exception ne sera générée et la page de catégorie sera chargée correctement.

_ACP2E-3053 - [contribution du code GitHub](https://github.com/magento/magento2/commit/c8931218)_

#### Erreur de type lors de la création de l&#39;objet : Magento\CatalogSearch\Model\Indexer\Fulltext\Interceptor Exception

Après le correctif, une instance de la classe Magento\CatalogSearch\Model\Indexer\Fulltext peut être créée sans spécifier $data.

_ACP2E-3345 - [contribution du code GitHub](https://github.com/magento/magento2/commit/1366ae5e)_

#### [CLOUD] Le problème lié aux produits n’est pas visible dans le front-end après l’enregistrement dans Magento Admin

Après le correctif, les produits configurables qui ont des produits enfants avec des noms longs ne seront pas manqués dans le storefront.

_ACP2E-3521 - [contribution du code GitHub](https://github.com/magento/magento2/commit/1984c61c)_

### Catalogue, Livraison

#### Adresse d&#39;expédition vide lors de la commande d&#39;un article de registre cadeau

Auparavant, pour les articles de registre des cadeaux des utilisateurs invités, lorsqu’ils étaient renvoyés par la fonction d’e-mail, une adresse vide était générée, ce qui est incorrect pour passer une commande. Une fois ce correctif appliqué, le registre des cadeaux vérifie les utilisateurs connectés/invités et les adresses attribuées s&#39;ils existent.

_ACP2E-3195_

### Cloud

#### [Cloud] PHPSESSID modifie chaque requête POST

PHPSESSID ne se régénère plus sur les requêtes POST sur la zone frontale pour un client connecté si le cache L2 Redis est activé et que le client a été mis à jour du serveur principal

_ACP2E-3010 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/6a185204)_

#### Avertissements de génération de plan de site

Après la correction, le plan du site est généré dans le répertoire tmp du système et copié vers la destination finale.

_ACP2E-3532 - [contribution du code GitHub](https://github.com/magento/magento2/commit/d4de4726)_

### Contenu

#### [Problème] problème d’affichage du prix dans le widget Récemment consultés

Le système affiche désormais correctement le prix des produits simples en rupture de stock dans le widget « Produit récemment consulté », ce qui garantit la cohérence entre tous les widgets et les pages de liste de produits. Auparavant, le prix des produits simples en rupture de stock n’était pas affiché dans le widget « Produit récemment consulté » en raison d’une condition dans les modèles de chargement de prix.

_AC-10539 - [Problème GitHub](https://github.com/magento/magento2/issues/38167) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38159)_

#### [Problème ] correction de la faute de frappe et de la grammaire dans le fichier acl.xsd

Le système corrige désormais une erreur de frappe et de grammaire dans le fichier acl.xsd, ce qui améliore la clarté et la précision de la documentation. Auparavant, le fichier acl.xsd contenait une faute de frappe et une grammaire incorrecte, ce qui pouvait prêter à confusion.

_AC-10596 - [Problème GitHub](https://github.com/magento/magento2/issues/38061) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38046)_

#### Image de bannière Pagebuilder non visible dans la galerie

Le système affiche désormais correctement les images de bannière chargées dans les dossiers nouvellement créés dans la galerie Pagebuilder, ce qui élimine les erreurs de console précédentes. Avant cette correction, les images de bannière n’étaient pas visibles dans la galerie si elles étaient chargées dans un nouveau dossier, provoquant une erreur de console.

_AC-10845 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/c8f87c25)_

#### « Indicatif régional non défini » après la mise à jour vers la version 2.4.5-p8

Le système termine désormais avec succès le processus de déploiement de contenu statique lorsque le module Magento_CSP est activé et que « dev/js/translate_strategy » est défini sur « bedded », sans déclencher l’erreur « Indicatif régional non défini ». Auparavant, dans ces conditions, le processus de déploiement de contenu statique échouait avec une erreur « Code zone non défini ».

_AC-12283 - [Problème GitHub](https://github.com/magento/magento2/issues/38845) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38922)_

#### L’arborescence de catégorie du widget n’est pas rendue correctement.

_AC-12692 - [Problème GitHub](https://github.com/magento/magento2/issues/39008) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/58e40ceb)_

#### Impossible de voir le message « Utilisation de la valeur par défaut » lors de la modification du thème dans la page de configuration de la conception

Le système inclut désormais une colonne distincte pour afficher le message « Utilisation de la valeur par défaut » en fonction du thème sélectionné dans la page de configuration de la conception . Cela garantit la clarté et la visibilité du statut de la valeur par défaut. Auparavant, le message « Utiliser la valeur par défaut » ne s’affichait pas, ce qui entraînait une confusion sur le statut du thème sélectionné.

_AC-13054 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/47b448e2)_

#### [Problème] Restaure à nouveau la rétrocompatibilité avec les plug-ins TinyMCE (après cela...

Le système restaure désormais la rétrocompatibilité avec les modules externes Minuscules MCE, ce qui permet d’appeler les fonctions définies dans le module externe lors de l’utilisation du widget à partir d’un autre emplacement. Auparavant, en raison d’une modification de la version de TinyMCE, les modules externes ne renvoyaient pas les widgets en tant qu’objet, ce qui entraînait une erreur lors de la tentative d’appel de certaines fonctions sur l’instance de widget.

_AC-13569 - [Problème GitHub](https://github.com/magento/magento2/issues/39262) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39258)_

#### [Problème] problème de chargement de fichier dans l’éditeur WYSIWYG sur la page du produit

Le système affiche désormais correctement l’arborescence de dossiers et permet les chargements d’images dans l’éditeur de WYSIWYG sur la page de produit, même après avoir développé l’onglet « Image et vidéos » en premier. Auparavant, le développement de l’onglet « Image et vidéos » entraînait d’abord l’affichage de l’arborescence de dossiers et un message d’erreur lors de la tentative de chargement d’une image dans l’éditeur de WYSIWYG.

_AC-9638 - [Problème GitHub](https://github.com/magento/magento2/issues/38026) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38025)_

#### Problème de bloc dynamique [On-PREM]

Les widgets sont désormais correctement rendus dans les blocs dynamiques.

_ACP2E-2392 - [contribution du code GitHub](https://github.com/magento/magento2/commit/a12063bd)_

#### L’URL de nocookie YouTube ne fonctionne pas dans Page Builder

Désormais, le générateur de pages autorise l’URL de non-cookie de YouTube dans les paramètres d’élément de formulaire des règles de validation. Auparavant, l’URL de non-cookie Youtube ne fonctionnait pas dans le générateur de page.

_ACP2E-2606_

#### [Cloud] Frontend ne se charge pas en raison d’un problème dans le modèle de newsletter

L’ajout de blocs via la section Contenu de la page CMS ne génère plus d’exception

_ACP2E-2693 - [contribution du code GitHub](https://github.com/magento/magento2/commit/ea79f7dd)_

#### ACP2E-2836: [Cloud] Examiner l’exception trouvée dans le journal : InvalidArgumentException : la classe n’existe pas dans vendor/magento/module-rule/Model/ConditionFactory.php

La suppression d’une condition sur les paramètres de contenu des produits PageBuilder n’entraîne plus l’enregistrement d’une exception dans les fichiers journaux. Auparavant, la suppression d’une condition sur les paramètres de contenu des produits PageBuilder entraînait l’enregistrement d’une exception critique dans les journaux, même si elle ne provoquait aucun problème sur le serveur frontal.

_ACP2E-2836 - [Contribution du code GitHub](https://github.com/magento/magento2-page-builder/commit/36c0f5df)_

#### Le passage en mode magasin unique : le contenu global n’apparaît plus

Le système synchronise désormais les configurations de conception d’affichage du magasin avec les configurations de conception de site web lors de l’activation du mode magasin unique, en veillant à ce que les mises à jour de contenu soient visibles sur le front-end. Auparavant, le passage en mode boutique unique empêchait la répercussion des mises à jour de contenu sur le storefront.

_ACP2E-2842 - [contribution du code GitHub](https://github.com/magento/magento2/commit/7e0e5582)_

#### Page Builder remplace l’image lors de la tentative d’ajout d’un lien et d’autres problèmes de convivialité.

Désormais, cliquer sur une image, des liens dans l’éditeur wysiwyg de l’élément de texte Page Builder chargera les données appropriées dans l’image, la boîte de dialogue de configuration des liens. L’ajout d’un lien vers une image dans l’éditeur fonctionne désormais correctement. Auparavant, l’image était remplacée par un lien.

_ACP2E-2903 - [contribution du code GitHub](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_

#### L’ancienne galerie de médias ne parvient pas à générer les images lorsqu’une image de 0 octet est placée dans le répertoire

Le système gère désormais les images de 0 octet dans la galerie multimédia sans perturber le fonctionnement, ce qui permet d’afficher et de sélectionner d’autres images du répertoire comme prévu. Auparavant, la présence d’une image de 0 octet dans la galerie de médias empêchait l’affichage ou la sélection de toutes les images du répertoire.

_ACP2E-2970 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/35b1b1da)_

#### Erreur du générateur de page lors de la modification du bloc CMS

Le système enregistre désormais correctement les modifications apportées à la zone d’administration à l’aide de Page Builder, sans générer l’erreur « Page Builder effectuait le rendu pendant 5 secondes sans libérer les verrous ». dans la console du navigateur. Auparavant, cette erreur se produisait lors de la tentative d’enregistrement des modifications, empêchant la mise à jour réussie du contenu.

_ACP2E-3064 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/35b1b1da) - [Contribution du code GitHub](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_

#### [CLOUD] Aucun bouton de passage en caisse ou de modification de panier dans la section Panier

Le produit groupé est désormais ajouté au panier via des widgets sans erreur.

_ACP2E-3092 - [contribution de code GitHub](https://github.com/magento/magento2/commit/b21e5d91) - [contribution de code GitHub](https://github.com/magento/magento2-page-builder/commit/4ebe3f1d)_

#### L’aperçu de l’évaluation du contenu sur les pages de catégorie n’affiche pas les widgets de produit

Le problème a été corrigé en veillant à ce que les entrées de produits pour la catégorie supplémentaire liée au bloc CMS aient été enregistrées avec précision dans la base de données. Auparavant, il renvoyait un jeu de résultats vide lorsque la page d’aperçu de catégorie était demandée.

_ACP2E-3113_

#### [CLOUD] Le bouton Charger l’image ne fonctionne pas

Auparavant, le bouton Charger l’image pour la bannière et le curseur de PageBuilder ne fonctionnait pas comme prévu. Désormais, lorsque vous appuyez dessus, le gestionnaire de fichiers local s’ouvre pour sélectionner l’image à charger.

_ACP2E-3122 - [contribution du code GitHub](https://github.com/magento/magento2-page-builder/commit/476ef8ea)_

#### imagecreatetruecolor() : la #2 de l’argument ($height) doit être supérieure à 0. Impossible de charger une image spécifique

Correction du problème qui provoquait des erreurs dans l’administration lors du chargement d’images d’une hauteur de 0 via la galerie de médias et de la synchronisation réussie des ressources à l’aide de la commande de synchronisation. Auparavant, ne pouvait pas charger l’image via la galerie de médias et la commande de synchronisation échouait également lorsqu’une image spécifique se trouvait dans la galerie.

_ACP2E-3127 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/6f4805f8)_

#### Prototype.js Array.from en conflit avec l’API Google Maps

Google Maps s’affiche désormais correctement dans l’éditeur PageBuilder. Auparavant, une erreur Javascript empêchait le rendu correct des cartes Google.

_ACP2E-3154 - [contribution du code GitHub](https://github.com/magento/magento2/commit/148c3ead)_

#### [Cloud] - Curseur CMS ne reflétant pas les dernières modifications

Le problème a été corrigé en veillant à ce que la liste des curseurs soit actualisée pendant que l’événement d’enregistrement est déclenché sur l’écran de modification de la diapositive. Auparavant, cela se déclenchait et provoquait le problème.

_ACP2E-3275 - [Contribution du code GitHub](https://github.com/magento/magento2-page-builder/commit/ae2cdeb0)_

#### Une erreur se produit dans la page CSM lorsque les blocs CMS sont insérés à l’aide de page builder dans un certain ordre

Auparavant, sur certaines versions de PHP et OS (Linux), le rendu des blocs qui référençaient d’autres blocs cms via PageBuilder aurait échoué avec une erreur « Une erreur inconnue s’est produite. Veuillez réessayer. » Désormais, le contenu des blocs cms est correctement rendu dans un contenu contrôlé par PageBuilder.

_ACP2E-3326 - [contribution du code GitHub](https://github.com/magento/magento2-page-builder/commit/ae2cdeb0)_

#### [Cloud] Les blocs dynamiques ne fonctionneront pas correctement

Les segments de clients connectés sont maintenant effacés après la déconnexion, ce qui empêche la session d’invités d’hériter des segments précédemment connectés

_ACP2E-3388_

#### Échec de l’aperçu du modèle de Pagebuilder pour le contenu volumineux

Un contenu volumineux entraînait le dépassement des limites du navigateur par l’élément zone de travail et le renvoi d’une valeur incorrecte, ce qui enfreignait le code du serveur principal (impossible de décoder correctement l’image). Correction apportée à en limitant la taille de la zone de travail à la limite du navigateur universel.

_ACP2E-3428 - [contribution du code GitHub](https://github.com/magento/magento2-page-builder/commit/adfb1747)_

#### Dernières mises à jour de sécurité avec TinyMCE 7 taille de police manquante

Les sélecteurs de taille de police et de famille de polices sont désormais disponibles dans l’éditeur de WYSIWYG. Avant ce correctif, avec TinyMCE 7, ils n’étaient pas disponibles dans l’interface de l’éditeur.

_ACP2E-3430 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/d50f6b5d) - [Contribution du code GitHub](https://github.com/magento/magento2-page-builder/commit/2c2f7a0e)_

#### Taille de police de l&#39;éditeur TinyMCE 7 dans l&#39;administrateur en PT et non en PX veuillez clarifier

Avant la correction, vous ne pouviez pas spécifier la taille de police en px dans les zones WYSIWYG. Vous pouvez maintenant définir la taille de la police en px au lieu de pt.

_ACP2E-3483 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/3f12d152) - [Contribution du code GitHub](https://github.com/magento/magento2-page-builder/commit/20aa5d7a)_

#### Le type de contenu de produit dans Page Builder est réduit sans messages corrects

Avant la correction, le code HTML de l’aperçu n’était pas généré correctement lorsqu’il n’y avait aucun produit dans le widget. Désormais, la réponse vide est correctement générée et le widget Products s’affiche correctement dans l’aperçu.

_ACP2E-3490 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/3f12d152) - [Contribution du code GitHub](https://github.com/magento/magento2-page-builder/commit/20aa5d7a)_

#### [page builder]l’ajout d’une liste de produits pour bloquer génère des erreurs

Désormais, l’ajout d’une liste de produits groupée au bloc via le générateur de page ne génère pas d’erreurs

_ACP2E-3534 - [contribution du code GitHub](https://github.com/magento/magento2/commit/344fce23)_

### Contenu, SEO

#### La hiérarchie des pages CMS peut entraîner des problèmes de réécriture d’URL

Auparavant, pour la réécriture d’URL permanente personnalisée pour les pages racine autres que le site web, redirigez à l’infini et la page n’était jamais chargée. Une fois ce correctif appliqué, la réécriture d’URL personnalisée pour la page racine non site web fonctionne comme prévu et aucune boucle de redirection ne se produit.

_ACP2E-2870_

### Contenu, évaluation et aperçu

#### La règle de prix de catalogue ne s’affiche pas lorsqu’elle est définie pour la planification avec des blocs dynamiques

Le système affiche désormais correctement le contenu dynamique associé aux règles de prix de catalogue planifiées sur la page des détails du produit. Auparavant, le chargement du contenu dynamique échouait lorsque les règles de prix de catalogue étaient planifiées.

_ACP2E-2979_

### Client/Clients

#### Front-end - La validation de la date de naissance échoue dans la page de création du client

Assurez-vous que toutes les validations fonctionnent après la mise à niveau de la dépendance du système moment.js vers la dernière version mineure.

_AC-12162 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/de4dfb8e)_

#### Le segment client > Condition > Historique des produits* > « produit consulté » ne fonctionne pas

Le système affiche désormais correctement les clients enregistrés correspondants dans la condition « Le produit a été consulté » sous Segments de clients, lorsque la condition est remplie. Auparavant, même lorsque la condition était remplie, le nombre de clients enregistrés appariés restait à zéro.

_AC-13060_

#### Le champ de texte Région n’est pas réinitialisé lorsque la liste déroulante Pays est modifiée

Le système réinitialise désormais le champ de texte Région lorsque le pays est modifié dans le menu déroulant, en s’assurant que les valeurs précédentes ne persistent pas. Auparavant, la modification du pays de la liste déroulante ne réinitialisait pas le champ Région, ce qui entraînait la conservation de la dernière valeur enregistrée.

_AC-8499 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/3ea26621)_

#### La suppression du client ne nettoie pas toutes les données de session du navigateur sur Storefront pour le client connecté et supprimé

La suppression d’un client nettoie désormais toutes les données de session du navigateur du storefront pour les clients connectés et supprimés comme prévu. L’acheteur peut continuer à faire des achats et son navigateur traite sa session comme une session d’invité. Auparavant, lorsque le compte client d’un acheteur connecté était supprimé de l’administration, le navigateur de l’acheteur générait des erreurs JavaScript.

_AC-9240 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/7d5e3906)_

### Framework

#### [Question]Unused Type configuration in `app/code/Magento/Translation/etc/di.xml`

Le système supprime désormais les dépendances inutilisées dans la configuration, améliorant ainsi la propreté et l’efficacité globales du code. Auparavant, il y avait des dépendances inutilisées dans la configuration qui ne contribuaient à aucune fonctionnalité.

_AC-10037 - [Problème GitHub](https://github.com/magento/magento2/issues/38030) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38064)_

#### Question/problème lié au point d’entrée V1/clients/mot de passe

Le système respecte désormais les contraintes définies dans l’interface utilisateur graphique de gestion lors du traitement des demandes de changement de mot de passe via l’API, ce qui empêche tout abus potentiel de la fonction de réinitialisation du mot de passe. Auparavant, l’API pouvait traiter les demandes de changement de mot de passe en dehors des règles définies dans l’interface utilisateur graphique de gestion, ce qui pouvait permettre de disposer d’un flux constant d’e-mails de réinitialisation si des e-mails valides étaient connus.

_AC-10654 - [Problème GitHub](https://github.com/magento/magento2/issues/38238) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/0c53bbf7)_

#### La configuration du vernis n’exclut pas tous les paramètres marketing

Le système exclut désormais correctement tous les paramètres marketing courants dans la configuration de Varnish, ce qui permet d’assurer un suivi et des analyses précis. Auparavant, certains paramètres marketing tels que gad_source, srsltid et msclkid n’étaient pas exclus, ce qui entraînait des inexactitudes potentielles dans la collecte des données.

_AC-10738 - [Problème GitHub](https://github.com/magento/magento2/issues/38298) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39188)_

#### Processus d’indexation des erreurs du processus d’index de recherche catalogue

Le système exécute maintenant correctement la commande de réindexation sans rencontrer d&#39;erreur, quelle que soit la version libxml compilée avec PHP. Auparavant, l&#39;exécution de la commande re-index provoquait une erreur de type « Erreur de processus d&#39;index de recherche de catalogue pendant le processus d&#39;indexation » lorsque PHP était compilé avec certaines versions de libxml.

_AC-10838 - [Problème GitHub](https://github.com/magento/magento2/issues/38254) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38553) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/0574ac23)_

#### Ajout de filtres created_at, status et grand_total à la requête Commandes client et correction de plusieurs échecs de filtres

Le système prend désormais en charge l’utilisation des filtres created_at, status et grand_total dans les requêtes Commandes client et a résolu un problème où plusieurs filtres n’étaient pas appliqués correctement. Auparavant, le système ne prenait pas en charge ces filtres et ne pouvait pas les appliquer tous lorsque plusieurs d’entre eux étaient utilisés dans une requête.

_AC-10941 - [Problème GitHub](https://github.com/magento/magento2/issues/38392) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/36949)_

#### Inondation aléatoire de requêtes provenant de blocs de ventes croisées / de ventes incitatives et connexes et indexation des prix

Le système optimise désormais les requêtes provenant des blocs de ventes croisées, de montée en gamme et connexes, ce qui améliore les performances et empêche le site de tomber en panne en raison de requêtes excessives. Auparavant, le système pouvait être surchargé de requêtes provenant de ces blocs, ce qui provoquait des ralentissements importants et pouvait entraîner l’arrêt du site.

_AC-10991 - [Problème GitHub](https://github.com/magento/magento2/issues/36667) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38050)_

#### Exception : Avertissement : Tentative d&#39;accès au décalage de tableau en... -> Calendar.php depuis la mise à niveau vers ICU 74.1 (PHP Intl)

Commerce ne consigne plus l’exception suivante dans le fichier exception.log chaque fois qu’un acheteur ou un commerçant visite le storefront ou l’administrateur : `main.CRITICAL: Exception: Warning: Trying to access array offset on value of type null in /vendor/magento/framework/View/Element/Html/Calendar.php on line 114 in /vendor/magento/framework/App/ErrorHandler.php:62`. [GitHub-38214](https://github.com/magento/magento2/issues/38214)

_AC-11423 - [Problème GitHub](https://github.com/magento/magento2/issues/38214) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38364)_

#### [Problème] Résolvez les problèmes liés aux données client lorsque le formulaire contient un élément dont le nom est `method`

Le système identifie désormais correctement l’attribut « method » dans les envois de formulaire, même lorsqu’un élément nommé « method » est présent dans le formulaire. Cela garantit un traitement précis des données client. Auparavant, si un élément de formulaire était nommé « méthode », cela interférait avec l’identification de l’attribut « méthode » dans les envois de formulaire, ce qui entraînait des problèmes potentiels avec la gestion des données client.

_AC-11476 - [Problème GitHub](https://github.com/magento/magento2/issues/38484) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38449)_

#### [Problème] Correction de PHPDocs pour \Magento\Framework\Data\Collection::getItemById

Les PHPDocs de la méthode \Magento\Framework\Data\Collection::getItemById ont été mis à jour afin d’inclure la valeur null comme type de retour possible, ce qui résout les problèmes liés aux outils d’analyse statique. Auparavant, les PHPDocs de la méthode ne spécifiaient pas la valeur null comme type de retour possible, ce qui entraînait des avertissements ou des erreurs dans l’analyse statique lorsque la méthode était utilisée dans des instructions conditionnelles.

_AC-11489 - [Problème GitHub](https://github.com/magento/magento2/issues/38485) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38439)_

#### [Problème] Autoriser uniquement les préférences valides pendant l’`setup:di:compile`

Le système renvoie désormais une erreur lors de la commande `setup:di:compile` si une préférence est créée pour une classe qui n’existe pas ou qui est spécifiquement exclue, en s’assurant que seules des préférences valides sont autorisées. Auparavant, ces scénarios échouaient en silence, ce qui rendait inutiles les modules externes associés aux classes d’origine.

_AC-11592 - [Problème GitHub](https://github.com/magento/magento2/issues/38517) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/33161)_

#### Magento tente de modifier la propriété en lecture seule dans __ méthode wakeup de LoggerProxy

Le système permet désormais de modifier les propriétés précédemment en lecture seule dans la méthode de réveil __wakeup de LoggerProxy, assurant ainsi un fonctionnement fluide sans forcer les utilisateurs à recourir à une solution de contournement. Auparavant, une tentative de réaffectation de la valeur d’une propriété en lecture seule dans la méthode __wakeup de LoggerProxy provoquait des problèmes.

_AC-11651 - [Problème GitHub](https://github.com/magento/magento2/issues/38526) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/c8f87c25)_

#### [Numéro ] AC-2039 AC-1667 Mise à niveau TinyMCE Références

Dernière version de tinymce mise à jour dans composer.json

_AC-11681 - [Problème GitHub](https://github.com/magento/magento2/issues/38533) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/36543) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/b34c0a75)_

#### ChangelogBatchWalker ne fonctionne pas dans plusieurs threads

Le système prend désormais en charge le branchement de processus pour l’indexation MView, ce qui évite les erreurs lors de l’exécution de l’indexeur lorsque le système fonctionne sur plusieurs threads. Auparavant, l’exécution du ChangelogBatchWalker sur plusieurs threads entraînait la suppression des tables utilisées par d’autres threads, provoquant une erreur lors de l’exécution de l’indexeur.

_AC-11696 - [Problème GitHub](https://github.com/magento/magento2/issues/38246) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38248)_

#### [Problème] Renommer une variable nommée de manière incorrecte

Le système nomme désormais correctement la variable qui contient le montant d’argent qui peut toujours être remboursé, ce qui évite toute confusion lors du débogage. Auparavant, cette variable était incorrectement nommée totalRefund, ce qui pouvait entraîner des malentendus pour les développeurs.

_AC-11781 - [Problème GitHub](https://github.com/magento/magento2/issues/38609) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/36205)_

#### [Problème] Transmettre des attributs personnalisés au lien actuel via XML

Le système permet désormais de transmettre des attributs personnalisés au lien actif via XML, en veillant à ce que ces attributs s’affichent correctement même lorsque le lien est la page active. Auparavant, les attributs personnalisés n’étaient pas affichés pour le lien de la page en cours, car la méthode getAttributesHtml() n’était pas utilisée pour le lien en cours.

_AC-11809 - [Problème GitHub](https://github.com/magento/magento2/issues/38500) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/30070)_

#### Le cache FPC intégré est endommagé dans la version 2.4.7 pour certaines configurations

Le système met désormais correctement en cache les pages lorsque le paramètre MAGE_RUN_CODE est défini, assurant ainsi des performances optimales. Auparavant, les pages n’étaient pas mises en cache dans ces conditions, ce qui entraînait des problèmes de performances potentiels.

_AC-11819 - [Problème GitHub](https://github.com/magento/magento2/issues/38626) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38646) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/0c53bbf7)_

#### [Problème ] correction de l’incohérence dans la gestion des exceptions entre les modes développeur et production

Le système gère désormais de manière cohérente les exceptions entre les modes de développement et de production, ce qui empêche toute redirection inattendue vers la page de connexion lorsqu’une exception est générée. Auparavant, une incohérence dans la gestion des exceptions pouvait entraîner une redirection vers la page de connexion en mode de production au lieu d’afficher le message d’exception.

_AC-11829 - [Problème GitHub](https://github.com/magento/magento2/issues/38639) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37712)_

#### Remplacer la traduction &#39;Compte PayPal&#39; dans token_list.phtml

Le système nomme désormais la section pour les méthodes de paiement de compte pouvant être segmentées en unités lexicales « Compte » au lieu de « Compte PayPal » sur la page Modes de paiement stockés , ce qui le rend plus représentatif de sa fonction. Auparavant, cette section était spécifiquement étiquetée comme « Compte PayPal », ce qui était trompeur lorsque d&#39;autres méthodes de paiement de compte jetable ont été ajoutées.

_AC-11852 - [Problème GitHub](https://github.com/magento/magento2/issues/35622) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37959)_

#### La rétrocompatibilité a été perdue sur la classe Magento\Catalog\Model\ProductRepository

La classe ProductRepository conserve désormais la rétrocompatibilité en restaurant la classe Initialization Helper en tant que deuxième paramètre, en veillant à ce que les modules s’étendant à partir de cette classe fonctionnent comme prévu. Auparavant, la suppression de l&#39;Assistant d&#39;initialisation du constructeur dans la classe ProductRepository entraînait une perte de rétrocompatibilité, forçant les utilisateurs à employer une solution de contournement.

_AC-11874 - [Problème GitHub](https://github.com/magento/magento2/issues/38669)_

#### [Problème] Déploiement de contenu statique - Erreur de type

Le système gère désormais correctement les fichiers LESS vides lors du déploiement du contenu statique, affichant un message d’erreur « Le fichier LESS est vide ». Auparavant, une erreur de type incorrect était générée lors de la détection d’un fichier LESS vide lors du déploiement.

_AC-11905 - [Problème GitHub](https://github.com/magento/magento2/issues/38682) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38683)_

#### [Problème] [Affichage] Suppression de l’espace supplémentaire dans le lien et la balise du script

Le système garantit désormais qu’il n’y a pas d’espace supplémentaire dans les balises de lien et de script, fournissant ainsi un code plus propre et plus efficace. Auparavant, il était possible de trouver des espaces doubles entre les attributs dans les balises de lien et de script.

_AC-12002 - [Problème GitHub](https://github.com/magento/magento2/issues/32920) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/32919)_

#### [Problème] éviter une mauvaise configuration de boucle infinie

Le système évite désormais une boucle infinie en empêchant le mappage autoréférentiel dans les configurations de type virtuel. Cela permet de s’assurer que l’application n’est pas bloquée dans une boucle sans fin lors de la tentative de déréférencement d’un nœud autoréférentiel. Auparavant, si une configuration de type virtuel était auto-référentielle, l’application tournait indéfiniment.

_AC-12127 - [Problème GitHub](https://github.com/magento/magento2/issues/38822) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38794)_

#### Gestionnaire d&#39;objets non utilisé pour Magento\Csp\Model\Mode\Data\ModeConfigured

Le système utilise désormais correctement le Gestionnaire d’objets lors de la création de l’objet ModeConfigured, ce qui permet d’utiliser des modules externes sur cet objet. Auparavant, le Gestionnaire d&#39;objets n&#39;était pas utilisé, empêchant l&#39;application de modules externes à l&#39;objet ModeConfigured.

_AC-12299 - [Problème GitHub](https://github.com/magento/magento2/issues/38875) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38886)_

#### Commentaire de bloc de document inexact dans les alertes de stock de produits et de prix

Le commentaire du bloc de document pour la méthode deleteCustomer dans les alertes de stock de produits et de prix a été corrigé afin de refléter précisément le fait que la méthode supprime du site web toutes les alertes de produit ou de prix de stock associées à un client et à un site web donnés, et non au client. Auparavant, le commentaire indiquait à tort que la méthode était destinée à supprimer un client du site web.

_AC-12540 - [Problème GitHub](https://github.com/magento/magento2/issues/38939) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39001)_

#### [Problème ] utilisez la configuration compilée pour les données générées au lieu de la configuration générale.

Le système utilise désormais la configuration compilée pour les données générées au lieu de la configuration générale, ce qui réduit le transfert réseau et la surcharge de données qui dépendent d’une certaine version du code. Cette modification empêche le remplacement du cache dans les instances partagées lors de la permutation de conteneur, ce qui améliore la stabilité et réduit les temps d’arrêt. Auparavant, certaines classes principales utilisaient le type de configuration partagé, ce qui pouvait entraîner le remplacement du cache ou des temps d’arrêt de l’application en raison de différences dans les versions de code sur plusieurs serveurs.

_AC-12594 - [Problème GitHub](https://github.com/magento/magento2/issues/38785) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/29954)_

#### [Problème] Supprimez les références aux fichiers d&#39;extjs qui ont été supprimés dans e1ccdb...

Le système supprime désormais les références aux fichiers d’extjs qui ont été supprimés, éliminant ainsi les erreurs dans la console du navigateur et le fichier journal du système. Auparavant, ces références provoquaient des erreurs en raison de l’absence des fichiers référencés.

_AC-12597 - [Problème GitHub](https://github.com/magento/magento2/issues/38960) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38951)_

#### [Problème] Nettoyage mineur : correction d’une utilisation incorrecte de sprintf. Il ne prend que 2 espaces réservés ici et...

Le système utilise désormais correctement la fonction sprintf avec le nombre approprié d’espaces réservés, ce qui améliore la propreté et la cohérence du code. Auparavant, la fonction sprintf était incorrectement utilisée avec un argument supplémentaire, ce qui ne provoquait aucun problème majeur, mais n’était pas l’utilisation correcte.

_AC-12778 - [Problème GitHub](https://github.com/magento/magento2/issues/39062) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38628)_

#### Extension FTP supprimée pour PHP 8.2.15

Le système inclut désormais l’extension FTP en tant que dépendance dans le fichier composer.json, ce qui garantit la réussite de la configuration des importations CSV via FTP. Auparavant, une erreur était générée lors de la tentative de configuration des imports de fichiers CSV via FTP en raison de l’absence de l’extension FTP dans le package PHP.

_AC-12857 - [Problème GitHub](https://github.com/magento/magento2/issues/39083) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/47b448e2)_

#### [Problème] corrige les classes incorrectes référencées dans les modules Magento.

Le système référence désormais correctement les classes dans les modules, ce qui garantit un fonctionnement plus fluide et empêche les blocages dus à des classes non existantes. Cela inclut un correctif de bugs dans les modules Indexer et Creditmemo, ainsi que l’implémentation de HttpGetActionInterface dans la classe PrintAction. Auparavant, des références de classe incorrectes entraînaient des erreurs et des blocages système potentiels, et certaines fonctionnalités, telles que le nom de fichier pour les fichiers PDF creditmemo et la réindexation des stocks, ne fonctionnaient pas comme prévu.

_AC-12869 - [Problème GitHub](https://github.com/magento/magento2/issues/39126) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37784)_

#### Possibilité de définir une zone pour `dev:di:info` commande d’interface de ligne de commande

Le système permet désormais aux développeurs de définir une zone pour la commande de l’interface de ligne de commande `dev:di:info`, ce qui améliore le processus de développement et de débogage. Auparavant, cette commande ne pouvait afficher que les informations relatives à la zone GLOBAL.

_AC-12964 - [Problème GitHub](https://github.com/magento/magento2/issues/38758) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38759)_

#### [Problème] ajoutez la propriété isMultipleFiles au modèle d’élément de formulaire d’image

Ce correctif empêche le bouton « Parcourir pour trouver ou faire glisser l’image ici » de disparaître lorsqu’une image est ajoutée à un élément de formulaire d’image à plusieurs fichiers.

_AC-13149 - [Problème GitHub](https://github.com/magento/magento2/issues/39219) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/36325)_

#### échec de la configuration :upgrade avec la version 11.4 de MariaDB en raison de modifications du jeu de caractères et du classement

_AC-13247_

#### [Problème ] supprimez tous les paramètres marketing get pour réduire le cache

Le système supprime désormais tous les paramètres marketing get pour optimiser l’utilisation du cache, reflétant la logique utilisée lorsque Varnish est en cours d’utilisation. Auparavant, ces paramètres pouvaient entraîner un gonflement du cache et une réduction des performances.

_AC-13279 - [Problème GitHub](https://github.com/magento/magento2/issues/39266) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39099)_

#### [Problème] [PHPDOC] Correction d’un phpdoc incorrect Magento\Directory\Model\AllowedCountries::getAllowedCountries()

La PHPDoc de la méthode AllowedCountries::getAllowedCountries() a été corrigée afin de fournir des informations précises, améliorant la clarté et l’utilité de la documentation. Auparavant, la PHPDoc de cette méthode contenait des informations incorrectes, ce qui pouvait entraîner une confusion ou une mauvaise utilisation de la méthode.

_AC-13345 - [Problème GitHub](https://github.com/magento/magento2/issues/39246) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39241)_

#### [Problème] Supprime du code pour les versions PHP que nous ne prenons plus en charge.

Suppression du code des versions PHP qui ne sont plus prises en charge dans Magento

_AC-13348 - [Problème GitHub](https://github.com/magento/magento2/issues/39361) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39202)_

#### [Problème ] Rendre l&#39;Adaptateur ImageMagick compatible avec php8 (Conversion implicite de float en int)

Le système assure désormais la compatibilité avec PHP8 en gérant correctement les nombres flottants lors du calcul des dimensions des images, évitant ainsi les erreurs dues à la conversion implicite de float en int. Auparavant, le calcul des dimensions de l’image pouvait entraîner des nombres flottants qui, lorsqu’ils étaient implicitement arrondis, provoquaient une erreur.

_AC-13417 - [Problème GitHub](https://github.com/magento/magento2/issues/39402) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37362)_

#### [Problème] [PHPDOC] Correction d’un mauvais phpdoc Magento\Framework\App\Config\ScopeConfigInterface

Cette mise à jour corrige les annotations PHPDoc dans le fichier Magento\Framework\App\Config\ScopeConfigInterface afin de refléter précisément le type de l’argument $scopeCode pour les méthodes getValue et isSetFlag.

_AC-13537 - [Problème GitHub](https://github.com/magento/magento2/issues/39492) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39199)_

#### Magento\Framework\Filesystem\Driver\Http dépend de l’expression de raison OK

Suppression de la vérification de l’expression « OK » de Magento\Framework\Filesystem\Driver\Http::isExists

_AC-13725 - [Problème GitHub](https://github.com/magento/magento2/issues/39546) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39558)_

#### L’indexeur de grille client ne fonctionne pas correctement en mode Mise à jour par planification

La grille cliente précédente a été mise à jour instantanément, mais après le correctif La grille cliente est mise à jour après l’exécution de cron, mais pas instantanément.

_AC-13810 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/1da9ba6f)_

#### erreur de frappe sur un fichier js.

Le système utilise désormais correctement le terme « abonnés » dans le fichier JavaScript, ce qui permet de garantir le bon fonctionnement des fonctionnalités associées. Auparavant, une erreur typographique dans le fichier JavaScript entraînait l’utilisation incorrecte du terme « abonnés ».

_AC-6754 - [Problème GitHub](https://github.com/magento/magento2/issues/36163) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/36171)_

#### [Problème] Supprimer la balise `@author` interdite

Le système respecte désormais les normes de codage en supprimant la balise `@author` interdite de certains modules, ce qui garantit un code plus propre et plus normalisé. Auparavant, la balise `@author` était présente dans certains modules, ce qui était contraire aux normes de codage établies.

_AC-8353 - [Problème GitHub](https://github.com/magento/magento2/issues/37253) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37003)_

#### [Problème] Supprimer la balise `@author` interdite de `Magento_Customer` (partie 2)

Le système respecte désormais la norme de codage en supprimant la balise `@author` interdite de certains modules, ce qui garantit un code plus propre et plus normalisé. Auparavant, la balise `@author` était présente dans certains modules, ce qui était contraire aux normes de codage établies.

_AC-8356 - [Problème GitHub](https://github.com/magento/magento2/issues/37250) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37000)_

#### L’espace dans la syntaxe editorconfig rompt la règle pour les `[&lbrace;composer,auth&rbrace;.json]`

Le système applique désormais correctement un retrait de 4 espaces aux fichiers composer et auth.json, suite à un correctif apporté à une erreur de syntaxe dans editorconfig. Auparavant, en raison d’un espace dans la syntaxe editorconfig, ces fichiers étaient incorrectement formatés avec un retrait de 2 espaces.

_AC-8659 - [Problème GitHub](https://github.com/magento/magento2/issues/37394) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37395)_

#### [Problème] Amélioration de la journalisation des erreurs cron

Le système capture et enregistre désormais à la fois STDERR et STDOUT pour les processus cron, fournissant ainsi des informations de diagnostic précieuses dans les scénarios où les processus cron échouent. Auparavant, tous les messages d’erreur des processus cron n’étaient pas enregistrés et STDERR et STDOUT pour les groupes cron s’exécutant dans des processus distincts étaient perdus.

_AC-8662 - [Problème GitHub](https://github.com/magento/magento2/issues/37453) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/32690)_

#### [Problème] Ajoute d’autres couleurs à la sortie de certaines commandes de l’interface de configuration

Le système ajoute désormais plus de couleurs à la sortie de certaines commandes de l’interface de ligne de commande (CLI) de la configuration, améliorant ainsi la lisibilité et l’expérience utilisateur. Auparavant, la sortie de ces commandes était plus difficile à lire en raison de l’absence de différenciation des couleurs.

_AC-8984 - [Problème GitHub](https://github.com/magento/magento2/issues/29335) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/29298)_

#### La mise à niveau de Magento réinitialise general/region/state_required lorsqu’un nouveau pays avec l’état/la région requis est ajouté.

Le système ajoute désormais uniquement le pays modifié à la configuration « general/region/state_required » lorsqu’un nouveau pays avec les états obligatoires est ajouté, ce qui empêche toute interruption du code personnalisé qui suppose que la région est désactivée. Auparavant, l’ajout d’un nouveau pays avec les états obligatoires réinitialisait la configuration « general/region/state_required » aux pays par défaut avec l’état obligatoire, ce qui pouvait entraîner l’interruption de l’activité.

_AC-9630 - [Problème GitHub](https://github.com/magento/magento2/issues/37796) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38076)_

#### Différence dans la compilation moindre entre php &amp; nodejs library (grount) avec des expressions `calc` compliquées

Correction de la différence de compilation entre la bibliothèque php et nodejs (grunt) après la mise à jour wikimedia/less.php:^5.x

_AC-9712 - [Problème GitHub](https://github.com/magento/magento2/issues/37841) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/b34c0a75)_

#### L’erreur « Table ou vue de base introuvable » se produit lors de l’exécution de l’indexation partielle

La réindexation partielle fonctionne désormais correctement avec un journal des modifications volumineux en cas de connexion à la base de données secondaire

_ACP2E-2692 - [contribution du code GitHub](https://github.com/magento/magento2/commit/ba25af8a)_

#### Problèmes après la mise à niveau de MariaDB vers 10.5.1 ou une version ultérieure

Correction du problème lorsque les valeurs datetime dans une base de données étaient converties en 0000-00-00 00:00:00 après la mise à niveau de Mysql

_ACP2E-2844 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a12063bd)_

#### Erreur de correspondance de type dans la comparaison de données lors de la vérification des modifications apportées aux données

Auparavant, l’objet d’enregistrement était appelé à chaque fois sans modification des données (pour tout champ de données numériques, comme int/float/double). Cela déclenche l’indicateur _hasDataChanges sur true et appelle la fonction d’enregistrement. Une fois que ce correctif est appliqué, la fonction d’enregistrement n’appelle que si les données sont modifiées. La valeur des données pour int/float/double-check avec la valeur transmise à la fonction et effectue une correspondance de type stricte.

_ACP2E-2855 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/57a32313)_

#### L’importation [Cloud] ne peut pas être utilisée avec la variable de répertoire

Le produit peut être importé sans problème, quel que soit le nom du fichier.

_ACP2E-2959 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/3a7c4d17)_

#### Dans ipad mini, le menu et l’en-tête se chargent comme s’ils étaient mobiles, mais ils doivent se charger comme s’ils étaient sur le bureau.

Le système traite désormais les appareils d’une largeur de 768 pixels comme des ordinateurs de bureau, en s’assurant que le menu et l’en-tête se chargent correctement. Auparavant, les appareils d’une largeur de 768 pixels étaient traités comme des appareils mobiles, ce qui entraînait le chargement du menu et de l’en-tête dans une vue mobile.

_ACP2E-2966 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/35b1b1da) - [Contribution du code GitHub](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_

#### Erreur de table ou de vue de base introuvable lors de l&#39;exécution de mview cron pendant une opération DDL

Le système gère désormais correctement les opérations de mise à jour de la base de données lorsque la mise à jour de la vue s&#39;exécute en arrière-plan, ce qui empêche l&#39;apparition d&#39;erreurs « Table de base ou vue introuvable ». Auparavant, certaines opérations de mise à jour de la base de données pouvaient entraîner l’erreur « Table de base ou vue introuvable » si la mise à jour de la mview était exécutée en même temps.

_ACP2E-3046_

#### La modification de la longueur des colonnes à l’aide du fichier db_schema.xml ne fonctionne pas en cas de clés étrangères

La modification d’une colonne avec une clé étrangère via un schéma déclaratif ne génère désormais pas d’erreurs avec MariaDB.

_ACP2E-3230 - [contribution du code GitHub](https://github.com/magento/magento2/commit/581b7ef1)_

#### Certains enregistrements de relations sont enregistrés dans la base de données lorsque l&#39;enregistrement de commande est enregistré

Avant le correctif, les requêtes UPDATE inutiles étaient déclenchées, ce qui peut avoir un impact sur les performances. Après le correctif, les requêtes UPDATE inutiles ont été éliminées.

_ACP2E-3361 - [contribution du code GitHub](https://github.com/magento/magento2/commit/1366ae5e)_

#### [CLOUD] Il existe de nombreuses erreurs JavaScript dans la console Administrateur

Auparavant, dans le panneau d’administration, il existait de nombreuses erreurs javascript dans la console. Désormais, dans le panneau d’administration, il n’y aura aucune erreur JavaScript dans la console et toutes les fonctions JavaScript par défaut s’exécuteront correctement sans problème.

_ACP2E-3375 - [contribution du code GitHub](https://github.com/magento/magento2/commit/d75cff27)_

#### [Cloud] Magento : le message de la file d’attente a été supprimé

Les messages en file d’attente sont maintenant correctement effacés. Avant la correction, étant donné que le système de file d’attente SQL était utilisé, les nouveaux messages pouvaient être supprimés si le message de la file d’attente de nettoyage était en cours d’exécution au même moment.

_ACP2E-3387 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/d50f6b5d)_

#### Les entrées de clé de cache correspondantes ne sont pas disponibles dans les balises de cache, donc le nettoyage du cache ne fonctionne pas correctement

Le mode LUA est désormais activé par défaut pour le nettoyeur de la mémoire cache Redis afin d’empêcher les conditions de concurrence.

_ACP2E-3537 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a52ff98f)_

#### La valeur Magento_DC_INDEXER__USE_APPLICATION_LOCK est ignorée

Après le correctif, une variable ENV définie sur « false » sera traitée comme bool false, et non comme chaîne « false ».

_ACP2E-3681 - [contribution du code GitHub](https://github.com/magento/magento2/commit/982b1c42)_

### Framework, GraphQL

#### [Problème ] Introduction de la prise en charge des types scalaires personnalisés pour le schéma GraphQL

Le système prend désormais en charge les types scalaires personnalisés pour le schéma GraphQL, ce qui permet aux développeurs et développeuses de définir des types scalaires personnalisés et des implémentations. Cette fonction peut s’avérer particulièrement utile pour exprimer des valeurs qui peuvent nécessiter une validation, telles qu’HTML, les e-mails, les URL, les dates, etc., ainsi que pour les cas plus avancés tels que les attributs EAV. Auparavant, le système ne prenait pas en charge le traitement des types scalaires personnalisés dans GraphQL.

_AC-7976 - [Problème GitHub](https://github.com/magento/magento2/issues/36877) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/34651) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/0574ac23)_

### Framework, Produit

#### 2.4.8-beta1 Les rapports EE ne sont pas générés en raison d’une exception magento

_AC-13011_

### Framework, framework d’interface utilisateur

#### Possibilité de remplacer la valeur de configuration même si elle est verrouillée

Auparavant, la configuration de conception ne pouvait pas être définie via la commande bin/magento config:set et les valeurs verrouillées pouvaient être modifiées en manipulant le formulaire qui les affichait. Après la correction, les valeurs verrouillées définies depuis l’interface en ligne de commande avec —lock-env ou —lock-conf ne peuvent plus être mises à jour.

_ACP2E-3324 - [contribution du code GitHub](https://github.com/magento/magento2/commit/55615e61)_

### GraphQL

#### Magento_GraphQl exécute le traitement des en-têtes même si la valeur de l’en-tête n’est pas validée

Le système garantit désormais que le traitement de l’en-tête n’est exécuté qu’une seule fois et uniquement si la valeur de l’en-tête réussit la validation, ce qui renforce la sécurité et empêche les vulnérabilités potentielles. Auparavant, le traitement de l’en-tête était exécuté même si la valeur de l’en-tête n’était pas validée, ce qui entraînait des vulnérabilités potentielles et un comportement inattendu en raison du double traitement des valeurs d’en-tête.

_AC-11729 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/c8f87c25)_

#### Les options de la carte-cadeau physique n&#39;ont pas le bon ordre de tri

Le système trie désormais correctement les options des produits de carte cadeau physique lors de l’interrogation via GraphQL, en assurant un rendu cohérent avec le thème Luma. Auparavant, l’ordre de tri était incorrect en fonction du thème Luma, ce qui entraînait un affichage et un ordre incorrects des options telles que le nom de l’expéditeur, le nom du destinataire et le montant.

_AC-8951 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/1bafc571)_

#### [GraphQL ] le cache du résolveur est invalidé lors de la création, de la modification, du déplacement ou de la suppression d’une mise à jour d’évaluation

Le système garantit désormais que le cache du résolveur n’est pas invalidé lors de la création, de la modification, du déplacement ou de la suppression d’une mise à jour d’évaluation, mais uniquement lorsque la mise à jour d’évaluation est appliquée à l’entité. Auparavant, le cache du résolveur était invalidé prématurément, avant même l’application de la mise à jour de l’évaluation, ce qui entraînait des invalidations inutiles du cache.

_AC-9157 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/0c53bbf7)_

#### Le cache Fastly n’est pas effacé pour la mise à jour de l’évaluation du contenu

Désormais, GraphQL avec le cache de réponse de contenu PageBuilder est invalidé lorsque les entités liées au contenu PageBuilder sont mises à jour.

_ACP2E-2642 - [contribution du code GitHub](https://github.com/magento/magento2/commit/ba25af8a)_

#### Désactivation de l’ajout en couches - Ne supprime pas l’agrégation de Graphql

Le problème a été corrigé après l’application de la vérification lors de la demande d’une recherche de produit avec des agrégations de catégories par le biais d’une requête GraphQL lorsque le paramètre de configuration d’administration de « Catalogue > Navigation superposée > Afficher le filtre de catégorie ».

_ACP2E-2653 - [contribution du code GitHub](https://github.com/magento/magento2/commit/12e071c3)_

#### L’appel aux produits GraphQL contenant le filtre de prix `&lbrace;from:&quot;0&quot;&rbrace;` ne renvoie aucun résultat

Auparavant, la recherche de produits GraphQL avec un filtre à prix nuls ne renvoyait aucun résultat en raison d’une exception levée. Désormais, la recherche renvoie les résultats attendus.

_ACP2E-2928 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/c971859e)_

#### Les traductions des attributs de retour client ne sont pas reflétées dans l’API GraphQL pour StoreView respectif

Les traductions des attributs de retour client sont reflétées dans l’API GraphQL pour l’affichage de magasin correspondant.
Auparavant, les attributs de retour client pour les StoreView respectifs n’étaient pas reflétés dans l’API GraphQL.

_ACP2E-2974 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/ec7e32a9)_

#### [Cloud] Appel GraphQL rompu pour getPurchaseOrder avec devis de nœud

L’appel GraphQL au bon de commande pourra exécuter la tâche sans rencontrer d’erreur de serveur interne.

_ACP2E-3128 - [contribution du code GitHub](https://github.com/magento/magento2/commit/6f4805f8)_

#### [Cloud] Produits configurables non affichés sur le site de production si le produit n’est pas activé dans « Toutes les vues de la boutique »

Le système affiche désormais correctement les produits configurables sur le site même si le produit n’est pas activé dans « Toutes les vues de la boutique », mais est activé dans des portées d’affichage de boutique spécifiques.
Auparavant, si un produit était désactivé dans « Toutes les vues de la boutique » et activé uniquement dans des portées d’affichage de boutique spécifiques, les attributs de produit ne s’affichaient pas correctement dans la réponse GraphQL, ce qui entraînait un affichage incorrect du produit.

_ACP2E-3184 - [contribution du code GitHub](https://github.com/magento/inventory/commit/3f300077)_

#### [Cloud] Produits Graphql présentant une erreur lorsque le même produit simple a été affecté à plusieurs produits configurables

Auparavant, avec des produits configurables distincts utilisant le même produit simple, GraphQL renvoyait une erreur. Après application de ce correctif, différents produits configurables avec le même produit simple, grapQL renvoie le résultat sans erreur.

_ACP2E-3190 - [contribution du code GitHub](https://github.com/magento/magento2/commit/148c3ead)_

#### [Cloud] problème lié à l’authentification des utilisateurs et à l’accès aux jetons intersites dans la configuration multisite

Les informations sur le client GraphQl et les requêtes de panier dans la configuration multisite vérifient si le client existe sur un site web autre que celui par défaut.
La requête précédente fonctionnait sans s’assurer que le client existe sur un site web autre que celui par défaut dans la configuration multisite.

_ACP2E-3215 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/581b7ef1)_

#### La pagination des éléments du panier GraphQL V2 ne fonctionne pas correctement.

Le problème a été résolu en transmettant la valeur correcte de l’argument de page actuel dans la requête de collection. Auparavant, une valeur incorrecte était transmise pour définir la page active, ce qui provoquait le problème.

_ACP2E-3253 - [contribution du code GitHub](https://github.com/magento/magento2/commit/8459b17d)_

#### [GRAPHQL] la valeur du modèle doit être spécifiée lors de l&#39;obtention de customerCart

La requête « customerCart » de GraphQL peut désormais créer un panier vide même si le devis n’est pas disponible dans la base de données. Auparavant, cette opération échouait en raison de problèmes de validation du pays lors de la création du panier vide.

_ACP2E-3255 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/fd5cf3af)_

#### Les éléments de liste de souhaits [GraphQl] sont visibles via GraphQl, mais non visibles sur storefront

Les produits de liste de souhaits n’étaient pas correctement répertoriés lorsqu’ils étaient demandés via GraphQL. Désormais, les produits de la liste de souhaits sont filtrés en fonction du contexte de magasin fourni.

_ACP2E-3380 - [contribution du code GitHub](https://github.com/magento/magento2/commit/55615e61)_

#### [GraphQL ] Réinitialiser l&#39;incohérence de l&#39;e-mail de mot de passe entre le contenu et l&#39;objet/lien

Le problème a été résolu en simulant le magasin correct où le compte du client est enregistré lors de l’envoi de la demande de réinitialisation de mot de passe, quelle que soit le magasin de sites web.

_ACP2E-3404 - [contribution du code GitHub](https://github.com/magento/magento2/commit/5184c067)_

#### La requête [Cloud] products de GraphQL renvoie les produits associés qui ne sont pas affectés au site Web actuel

Auparavant, pour les requêtes GraphQL, les produits associés à plusieurs magasins ne s’affichaient pas correctement pour les requêtes de produit. Une fois ce correctif appliqué, pour les produits , graphQL interroge les produits associés à plusieurs magasins et les affiche en conséquence.

_ACP2E-3419 - [contribution du code GitHub](https://github.com/magento/magento2/commit/078c387e)_

#### L’utilisation d’un ID de magasin incorrect dans l’en-tête GraphQL entraîne une erreur de mémoire fatale

L’envoi d’un code de magasin incorrect dans la requête GraphQL n’entraîne plus une consommation excessive de mémoire.

_ACP2E-3447 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/d50f6b5d)_

#### [Cloud] réponse 500 à une réponse Graphql vide sur 2.4.7

Après le correctif, les requêtes graphql non valides ne seront pas consignées dans le fichier exception.log.

_ACP2E-3467 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/1984c61c)_

#### [Cloud] problèmes liés à l’API Graphql

Avant la correction à l’aide du serveur d’applications Graphql, la demande d’adresse du client ne renvoyait pas les données les plus récentes.

_ACP2E-3492 - [contribution du code GitHub](https://github.com/magento/magento2/commit/3f12d152)_

#### Le produit désactivé apparaît toujours dans les éléments liés, de montée en gamme et de vente croisée dans la requête GraphQL

Graphql fournit désormais une réponse correcte pour les produits associés, de montée en gamme et de vente croisée désactivés

_ACP2E-3505 - [contribution du code GitHub](https://github.com/magento/magento2/commit/d4de4726)_

#### [CLOUD] : erreur GraphQl Erreur de serveur interne placeOrder mutation

La mutation « placeOrder » avec les informations de code de coupon dans la requête ne renvoie plus d’erreur interne. La commande a été passée avec succès. Auparavant, il échouait avec « Erreur de serveur interne ».

_ACP2E-3647 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/982b1c42)_

#### Le pourcentage_escompte n’est pas calculé pour les produits groupés au prix dynamique

Correction ajoutée pour le pourcentage de remise de product.price_details n’affichant pas la valeur correcte pour les produits groupés avec le prix dynamique activé et le coupon de remise appliqué.

_LYNX-426_

#### Les produits groupés affichent toujours « IN_STOCK » lorsqu’un de leurs produits groupés est en rupture de stock

Correction du problème en raison duquel les produits groupés affichaient toujours « IN_STOCK » même si l’un de leurs produits groupés était en rupture de stock.

_LYNX-485_

#### not_available_message et only_x_left_in_stock n&#39;affiche pas le même stock disponible

Correction du problème en raison duquel not_available_message et only_x_left_in_stock affichaient une disponibilité incohérente du stock.

_LYNX-486_

#### le champ original_row_total renvoie une valeur incorrecte

Correction du problème lié au champ original_row_total, qui renvoyait des valeurs incorrectes lorsque des options personnalisées étaient sélectionnées

_LYNX-488_

#### Les miniatures de produits regroupées doivent être affichées en fonction de la configuration     .

Résolution du problème pour s’assurer que la miniature groupée du produit s’affiche en fonction des paramètres de configuration

_LYNX-503_

#### Erreur lors de l’interrogation de selected_options dans OrderAddress

Mise à jour d’AttributeSelectedOptions en custom_attributesV2 dans la réponse GraphQL de l’adresse de commande.

_LYNX-510_

#### original_item_price n&#39;inclut pas les remises

Mise à jour de original_item_price pour inclure les remises.

_LYNX-512_

#### Le message Non disponible n&#39;affiche pas la quantité en stock disponible

Résolution du message d’erreur et du code d’erreur pour la mutation AddProductsToCart pour s’aligner sur la configuration du message « non disponible »

_LYNX-530_

#### Le statut « OUT_OF_STOCK » renvoie la valeur Simple avec des options personnalisées pour les produits avec des options à sélection multiple

Mise à jour du résolveur StockStatusProvider dans le package d’inventaire pour corriger le stock_status pour les produits simples avec des options personnalisées.

_LYNX-532_

#### Erreur (GQL) : cart.itemsV2.items.product.custom_attributesV2 renvoie une erreur de serveur

Correction de l’erreur de serveur qui se produisait lorsqu’une requête de panier incluait les attributs personnalisés d’un produit en ajoutant un produit sans attribut personnalisé.

_LYNX-533_

#### orders/date_of_first_order renvoie toujours null.

Correction du problème en raison duquel commandes > date_of_first_order renvoyait toujours la valeur null.

_LYNX-536_

#### Le client ne doit pas pouvoir annuler une commande partiellement expédiée

Une validation a été ajoutée pour empêcher les clients d&#39;annuler une commande partiellement expédiée.

_LYNX-544_

#### Codes d’erreur pour l’annulation de la commande en fonction du message d’erreur

Les codes d’erreur pour l’annulation de la commande sont désormais basés sur le message d’erreur spécifique.

_LYNX-548_

#### Retour des propriétés liées aux cookies du statut privé au statut protégé

Rétablit la visibilité des propriétés du constructeur de classe Magento\Framework\App\PageCache\Version de private à protected

_LYNX-581_

#### Augmentez la complexité maximale de requête GraphQL par défaut à 1 000.

Augmentation de la complexité maximale par défaut des requêtes GraphQL de 300 à 1 000.

_LYNX-600_

#### GQL - itemsV2 > Total de la ligne d’origine, les prix des plages de prix sont renvoyés à 0,00 $ pour les produits téléchargeables avec des options de fichier qui ont des prix distincts.

Correction d’un problème en raison duquel les produits téléchargeables avec des options d’achat de lien distinctes activées renvoyaient 0 $ pour les articlesV2 > Total de la ligne d’origine, la plage de prix renvoyée était de 0,00 $ pour les produits avec des options de fichier ayant des prix distincts.

_LYNX-620_

#### Schéma d’une table lors de la création tout nouveau différent de celui lors de la mise à niveau

Correction d’un problème en raison duquel l’ajout d’une nouvelle colonne VARCHAR à une table existante entraînait des échecs de test en raison de différences de schémas entre les nouvelles installations et les mises à niveau. La méthode modifyColumn() gère désormais correctement les colonnes VARCHAR en définissant le jeu de caractères et le classement par défaut.

_LYNX-711_

#### Compatibilité GraphQl pour la version PHP-8.4

Correction de problèmes de compatibilité GraphQL avec PHP 8.4 dans plusieurs résolveurs, assurant ainsi une fonctionnalité fluide. Mise à jour des fichiers concernés dans les modules CatalogRule, Customer, GiftMessage, GiftCard et GiftWrapping.

_LYNX-772_

### GraphQL, Inventaire / MSI

#### La mutation MergeCart renvoie une exception lorsque les paniers source et de destination ont les mêmes éléments de lot

&#39;-

_ACP2E-2607 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/c971859e) - [Contribution du code GitHub](https://github.com/magento/inventory/commit/db0620da)_

### GraphQL, Inventaire / MSI, Performances

#### Site arrêté après la mise à niveau

Les performances de récupération des produits groupés via GraphQl sont améliorées.

_ACP2E-1716 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/ba25af8a) - [Contribution du code GitHub](https://github.com/magento/inventory/commit/bdbf97ea)_

### GraphQL, Performances

#### [Résolveur GraphQL ] les données du résolveur client ne sont pas invalidées de l&#39;importation

Le cache du résolveur client de GraphQL est désormais invalidé comme prévu lorsqu’un client est modifié ou supprimé lors des importations. Auparavant, le cache n’était pas invalidé et les données client pouvaient être modifiées ou supprimées lors de l’importation.

_AC-9569 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/0574ac23)_

### GraphQL, Recherche

#### Le tri des listes de produits GraphQL en fonction de plusieurs paramètres ne fonctionne pas

Le tri des produits par plusieurs champs dans GraphQl fonctionne désormais comme décrit dans la documentation

_ACP2E-2809 - [contribution du code GitHub](https://github.com/magento/magento2/commit/c971859e)_

#### Requête GraphQL de liste de produits limitée à total_count 10 000 produits uniquement

Après la correction, le résultat de la recherche ne se limite pas à 10000 produits. Il devient alors possible d’obtenir tous les produits correspondant aux critères de recherche, même si le nombre est supérieur à 10000.

_ACP2E-948 - [contribution du code GitHub](https://github.com/magento/magento2/commit/a4cf5e62)_

### GraphQL, framework de test

#### Échec du test d’intégration de Magento\GraphQl\App\GraphQlCustomerMutationsTest.php

&#39;-

_ACP2E-3363 - [contribution du code GitHub](https://github.com/magento/magento2/commit/a4cf5e62)_

### Importer/exporter

#### Problème lors de l’importation du produit lorsque le type d’options personnalisé est fourni : fichier (le produit créé ne contient pas le prix de l’option personnalisée et affiche uniquement la première extension de type de fichier fournie)

Le système importe désormais correctement les données de produit avec les options personnalisées de type &#39;fichier&#39;, en s’assurant que toutes les extensions de fichier fournies sont affichées et que le prix de l’option personnalisée est inclus. Auparavant, lors de l’importation du produit, si une option personnalisée de type « fichier » était fournie avec plusieurs extensions de fichier, seule la première extension s’affichait et le prix de l’option personnalisée était manquant.

_AC-12172 - [Problème GitHub](https://github.com/magento/magento2/issues/38805) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38926)_

#### Mauvaise heure d&#39;exécution pour l&#39;opération d&#39;import dans la grille Historique d&#39;import

Le temps d’exécution du rapport d’importation est correctement indépendant des paramètres régionaux d’administration.

_ACP2E-2710 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/ea79f7dd)_

#### Dupliquer les clients créés avec la même adresse électronique à l’aide de l’importation

Importation du client lorsque le partage de compte est défini sur Global, le client importé qui existe dans le système est mis à jour.
Le client précédemment importé a été dupliqué.

_ACP2E-2737 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/c971859e)_

#### Ajouter/mettre à jour l’importation des options personnalisables de duplication de produits

Le problème a été résolu en attribuant le magasin approprié aux options de produit lors des importations d’options de produit au format CSV.
Auparavant, affecté à l’admin store au lieu de leur magasin respectif.

_ACP2E-2902 - [contribution du code GitHub](https://github.com/magento/magento2/commit/3a7c4d17)_

#### Date « created_at » du client non convertie en fuseau horaire de magasin lors de l’exportation

Une valeur de date de colonne « created_at » est convertie au format de date approprié en fonction du fuseau horaire du magasin dans la section CSV d’exportation du client.

_ACP2E-2990 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/3056e9cb)_

#### [Cloud] Erreur lors de la vérification des données dans les données d’importation à l’aide de CSV

Aucune erreur ne se produit lors de la vérification des données lors de l’importation du fichier CSV. Auparavant, le message d’erreur affiché était le suivant : « Nous ne parvenons pas à trouver un client qui correspond à cet e-mail et au code de site web dans ligne(s) : 1 » lors de la vérification des données dans la section d’importation à l’aide du fichier CSV de l’administrateur.

_ACP2E-3165 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/8459b17d)_

#### Bouton Importer manquant

Résolvez le problème d’absence du bouton Importer après la vérification des données avec des enregistrements corrects et incorrects dans le fichier CSV. Auparavant, le bouton d’importation ne s’affichait pas après la vérification des données avec des enregistrements corrects et incorrects dans le fichier CSV.

_ACP2E-3172 - [contribution du code GitHub](https://github.com/magento/magento2/commit/1819fe73)_

#### Impossible d&#39;importer l&#39;adresse du client exportée

L&#39;importation des adresses du client se déroulera comme prévu. Auparavant, un fichier d’importation d’adresses client n’était pas validé si Partager les comptes client = Global et il existe deux sites web où le site web par défaut comporte une liste de pays restreinte et l’adresse importée correspond à un autre site web où les pays autorisés sont différents

_ACP2E-3382 - [contribution du code GitHub](https://github.com/magento/magento2/commit/ec7e32a9)_

#### [Cloud] Une quantité incorrecte dans le fichier CSV n’a pas donné d’erreur

Désormais, l’importation des origines de stock générera une erreur de validation pour les valeurs non numériques dans la colonne de quantité. Auparavant, l&#39;importation d&#39;origines de stock avec une valeur non numérique dans la colonne Quantité entraînait la définition de la quantité sur 0.

_ACP2E-3448 - [contribution du code GitHub](https://github.com/magento/inventory/commit/5b21b7af)_

#### Le message d’erreur de clé URL dupliquée généré lors de l’importation d’un produit est incorrect lorsque la clé URL appartient déjà à une catégorie

Affichage du message d’erreur correct lors de la vérification de l’importation du produit, lorsque le client a tenté d’importer le produit alors que la clé URL du produit appartient déjà à une catégorie.

_ACP2E-3455 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/d4de4726)_

#### L&#39;export de produits provoque un OOM même avec une limite de mémoire 4G

Avant ce correctif, l’exportation du produit échouait si les attributs de produit avaient des milliers de valeurs d’option même avec la mémoire disponible 4G. Après ce correctif, l’exportation du produit doit terminer l’exportation du fichier CSV.

_ACP2E-3475 - [contribution du code GitHub](https://github.com/magento/magento2/commit/1984c61c)_

#### [Cloud] les processus d’importation interfèrent les uns avec les autres

Des messages corrects s’affichent si le même administrateur effectue plusieurs opérations d’importation à l’aide de la même session utilisateur.

_ACP2E-3527 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/d4de4726)_

### Importation/exportation, Performances

#### Le temps d’importation des produits [Cloud] a considérablement augmenté

Avant le correctif, l’importation de produits de catalogue avec plus de 10 000 entrées présentait une dégradation temporelle significative. Après le correctif, l’importation des produits du catalogue s’exécute dans les délais impartis.

_ACP2E-3476 - [contribution du code GitHub](https://github.com/magento/magento2/commit/87d012e5)_

### Installer et administrer

#### La mise à niveau de Magento échoue sur MariaDB 11.4 + 2.4.8-beta1

La mise à niveau doit s’être produite sans erreur.

_AC-13242 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/7b336d0a)_

#### Pas de VCL d&#39;exportation pour le bouton Vernis 7 dans le panneau d&#39;administration

Le bouton « Exporter VCL pour vernis 7 » a été ajouté au panneau d’administration.

_ACP2E-2102 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a4fbf702)_

### Inventaire / MSI

#### La mise à jour de l&#39;inventaire des produits configurables échoue lorsque la base de données utilise des préfixes

Le système met désormais correctement à jour l’inventaire des produits configurables lorsque la base de données utilise des préfixes, ce qui empêche tout message d’erreur et garantit que la quantité correcte est enregistrée. Auparavant, une erreur se produisait lors de la tentative d&#39;enregistrement de la quantité en stock de produits simples dans un produit configurable si la base de données utilisait des préfixes.

_AC-10750 - [Problème GitHub](https://github.com/magento/magento2/issues/38045)_

#### La clé API Google Google ne fonctionne pas lors de l’ajout d’une carte avec des attributs

Le système prend désormais en charge la dernière version de l’API Google Maps 3.56, ce qui permet aux utilisateurs d’ajouter un bloc de contenu Map du menu PageBuilder à l’étape sans rencontrer d’erreurs. Auparavant, les utilisateurs ne pouvaient pas ajouter de bloc de contenu Map en raison de problèmes de compatibilité avec la version de l’API Google Maps, ce qui entraînait un message d’erreur « une erreur s’est produite ».

_AC-11593 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/0574ac23)_

#### Impossible de créer une expédition pour l&#39;article de commande avec plusieurs sources et un SKU corrompu

Auparavant, lorsque des espaces étaient ajoutés par erreur dans le SKU par le biais de la base de données, une erreur se produisait dans la page d&#39;expédition. Cette erreur est maintenant corrigée et la correction automatique est considérée comme une erreur conviviale. Aucun impact n&#39;a été trouvé. Par conséquent, l&#39;expédition a été créée avec succès.

_AC-13922 - [Contribution du code GitHub](https://github.com/magento/inventory/commit/c18eb5fa)_

#### [Test] Regroupez les produits avec 0 inventaire sur la vitrine

Le produit groupé ne s’affiche pas sur les sites Web supplémentaires utilisant un stock supplémentaire.

_ACP2E-1411_

#### [Cloud] problème critique lié à la liste des produits avec des espaces vides

Le système affiche désormais correctement les listes de produits sans espaces vides lorsque les produits sont définis sur « En rupture de stock », ce qui garantit un affichage cohérent et précis des produits disponibles. Auparavant, la définition d’un produit sur « En rupture de stock » entraînait l’affichage d’un espace vide dans la liste des produits, ce qui perturbait la mise en page et pouvait dérouter les clients.

_ACP2E-2794 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/ea79f7dd) - [Contribution du code GitHub](https://github.com/magento/inventory/commit/b59e48ca)_

#### Impossible d&#39;expédier la commande lorsque le magasin de prélèvement MSI est activé

Amélioration des performances des stocks de création d’expédition pour de nombreuses sources avec retrait en magasin

_ACP2E-3335 - [contribution du code GitHub](https://github.com/magento/inventory/commit/9f3e63d1)_

#### La réindexation cron ne parvient pas à mettre à jour la disponibilité du produit sur le front-end.

Auparavant, les produits restaient en rupture de stock sur le serveur frontal après la mise à jour du statut de la commande en attente via l’API REST. Désormais, après la mise à jour du statut de la commande en attente via l’API REST, les produits s’affichent comme en stock.

_ACP2E-3355 - [Contribution du code GitHub](https://github.com/magento/inventory/commit/e6fe0aa7)_

#### L’ajout d’images à configurable ne fonctionne pas lorsque MSI est activé.

Le chargement des images pour les produits configurables fonctionne désormais comme prévu lorsque le module d’inventaire est utilisé. Auparavant, le chargement de l’image ne fonctionnait pas

_ACP2E-3357 - [Contribution du code GitHub](https://github.com/magento/inventory/commit/fdf409aa)_

#### Problème avec le produit groupé + MSI dans Clean M2.4.7-p3

Auparavant, pour les produits groupés en stock après duplication avec le même produit simple, le produit simple ne peut pas être enregistré. Une fois ce correctif appliqué, le produit simple peut être enregistré sans aucune exception.

_ACP2E-3470 - [Problème GitHub](https://github.com/magento/magento2/issues/39358) - [Contribution du code GitHub](https://github.com/magento/inventory/commit/0208e433)_

### Inventaire / MSI, Recherche

#### Tous les produits sont indexés avec [is_out_of_stock] = 1 lorsque le SKU n’est pas défini comme attribut consultable

Après le correctif, la valeur « is_out_of_stock » dans l’index de recherche catalogue est correcte, même lorsque le SKU ne peut pas faire l’objet de recherches.

_ACP2E-3413 - [contribution du code GitHub](https://github.com/magento/inventory/commit/5b21b7af)_

### Ordre

#### Ecran de présentation des commandes du serveur principal : Quantité en reliquat non visible au niveau article de commande

Le système affiche désormais le nombre d&#39;articles en reliquat dans la colonne Quantité de l&#39;écran de présentation des commandes du serveur principal. Cela permet aux utilisateurs et utilisatrices de suivre avec précision le statut de tous les éléments d’une commande. Auparavant, la colonne Quantité affichait uniquement le nombre d’articles commandés, facturés et expédiés, mais n’affichait pas le nombre d’articles en reliquat.

_AC-10828 - [Problème GitHub](https://github.com/magento/magento2/issues/38252) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38320)_

#### [Problème] ID de magasin incorrect utilisé dans le moteur de rendu d’adresse de commande

Le système utilise désormais correctement l’ID de magasin associé à une commande lors du rendu de l’adresse de commande, en veillant à ce que les adresses soient formatées correctement en fonction de leur ID de magasin respectif. Auparavant, le système utilisait incorrectement l’ID de magasin actuel, ce qui pouvait entraîner un formatage incorrect de l’adresse dans les cas où plusieurs e-mails de commande provenant de différents magasins devaient être envoyés.

_AC-10994 - [Problème GitHub](https://github.com/magento/magento2/issues/38412) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37932)_

#### Problème de mise en cache du processeur Join

Le système applique désormais correctement le JoinProcessor pour chaque itération, même avec des appels consécutifs, ce qui garantit une récupération précise des données. Auparavant, JoinProcessor était incorrectement marqué comme étant déjà appliqué dans des itérations consécutives, ce qui entraînait des erreurs dans la récupération des données.

_AC-11690 - [Problème GitHub](https://github.com/magento/magento2/issues/27504) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37550)_

#### [Problème] Le prix d’expédition s’affiche différemment dans le pdf imprimé

Le système affiche désormais correctement les prix d&#39;expédition dans les fichiers PDF imprimés en fonction des paramètres de configuration de taxe, ce qui garantit la cohérence entre la page de vue de la facture de commande client et la facture imprimée. Auparavant, le prix d’expédition affiché dans le PDF imprimé excluait la taxe, quels que soient les paramètres de configuration de la taxe.

_AC-11798 - [Problème GitHub](https://github.com/magento/magento2/issues/38608) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38595) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/1bafc571)_

#### Réorganiser avec un produit configurable parent supprimé

Désormais, lors de la réorganisation avec le produit supprimé, le système n&#39;affichera pas le bouton de réorganisation pour réorganiser

_AC-13839 - [Problème GitHub](https://github.com/magento/magento2/issues/39568) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39601)_

#### [Problème] Correction d’une propriété \Magento\Sales\Model\Order\Email\Container\Template::$id incorrecte

Cela corrige le mauvais phpdoc pour \Magento\Sales\Model\Order\Email\Container\Template::$id, en fait $id est de type int mais en réalité est string.

_AC-13924 - [Problème GitHub](https://github.com/magento/magento2/issues/39151) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39150)_

#### Impossible d’enregistrer les modifications apportées au numéro de téléphone dans les détails de la commande existante

L&#39;utilisateur peut maintenant ajouter le préfixe international 00 dans le champ téléphonique de l&#39;adresse de commande

_ACP2E-2622 - [Problème GitHub](https://github.com/magento/magento2/issues/38201) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/12e071c3)_

#### Échec de l’envoi des e-mails

Le système comprend désormais une option de configuration async_sending_attempts pour spécifier le nombre de tentatives d’envoi d’un e-mail avant l’arrêt, ce qui améliore la gestion des envois d’e-mail ayant échoué lorsque l’option « Envoi asynchrone » est activée. Auparavant, si l’envoi d’un e-mail échouait, le système tentait continuellement de le renvoyer, ce qui entraînait une boucle sans fin de messages d’erreur dans le journal système.

_ACP2E-2734 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/b2286ecf)_

#### [Cloud] Statut de la commande modifié en Terminé lors du remboursement partiel d’une commande partiellement expédiée

Lors de l&#39;émission d&#39;un avoir, le statut de la commande ne passe plus à « terminé » si des articles n&#39;ont pas encore été expédiés.

_ACP2E-2756 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/7e0e5582)_

#### [CLOUD] Impossible de désactiver l’envoi d’e-mails depuis l’interface utilisateur d’administration comme indiqué dans la documentation de développement

Le système empêche désormais correctement l’envoi d’e-mails de vente lorsque la communication par e-mail est désactivée. Ces e-mails ne seront plus envoyés lorsque la communication par e-mail sera réactivée. Auparavant, les e-mails de vente initiés alors que la communication par e-mail était désactivée étaient toujours envoyés une fois la communication par e-mail réactivée.

_ACP2E-3002 - [contribution du code GitHub](https://github.com/magento/magento2/commit/c8931218)_

#### Commande clôturée sans remboursement intégral

Le système conserve désormais correctement le statut de la commande comme &#39;Traitement&#39; et le statut de la facture comme &#39;En attente&#39; lorsqu&#39;une commande avec un paiement non capturé a une expédition créée. Cela garantit que les commandes ne sont marquées comme « Fermées » qu&#39;après avoir été entièrement remboursées. Auparavant, la création d&#39;une livraison pour une commande avec une facture en attente modifiait incorrectement le statut de la commande en « Fermée ».

_ACP2E-3045 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/6a185204)_

#### [Cloud] Impossible de créer une commande dans l’administration sur un magasin si seule l’adresse de facturation par défaut n’a pas été configurée

Message d’erreur « Un client ou une cliente avec la même adresse e-mail existe déjà dans un site web associé ». s’affiche si un client ne dispose pas d’une adresse de facturation par défaut et tente de créer une commande dans un autre magasin.

_ACP2E-3311 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/d75cff27)_

#### Admin duplicated place order requests sent

Auparavant, il était possible de cliquer plusieurs fois sur le bouton « Envoyer la commande » du panneau d’administration ou de l’activer en appuyant à plusieurs reprises sur la touche « Entrée », ce qui entraînait des envois en double ou des commandes avec une erreur. Vous pouvez désormais empêcher d’autres actions tant que la commande n’est pas entièrement traitée, en veillant à ce qu’une seule commande soit envoyée.

_ACP2E-3416 - [contribution du code GitHub](https://github.com/magento/magento2/commit/5184c067)_

#### L’administrateur peut toujours passer commande même sans mode de paiement

Le mode de paiement précédemment sélectionné est désormais conservé lorsque le mode de paiement réapparaît dans la liste des paiements disponibles.

_ACP2E-3425 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/d50f6b5d)_

#### Les éléments sont dupliqués après la création d&#39;une commande à partir de Admin sur - navigateur Mozilla Firefox

Les produits ajoutés à l’aide de l’option « Ajouter des produits par SKU » ne sont plus dupliqués dans Firefox lors de la création d’une commande dans admin.

_ACP2E-3518_

### Commande, Paiements

#### L’administrateur peut toujours passer commande même sans mode de paiement

Auparavant, le commerçant pouvait passer des commandes à partir du panneau d’administration sans sélectionner de mode de paiement. Maintenant, le commerçant doit utiliser un mode de paiement pour passer une commande.

_ACP2E-3233 - [contribution du code GitHub](https://github.com/magento/magento2/commit/fd5cf3af)_

### Commande, Retours

#### Le remboursement de la commande génère un avoir en double

L&#39;émission du remboursement via l&#39;API REST lorsque deux demandes identiques ont été exécutées simultanément ne crée plus d&#39;avoirs en double.

_ACP2E-2982 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a4fbf702)_

### Commande, Taxe

#### [CLOUD] Base_row_total incorrect dans l’API de commande RESTFUL lors de l’activation des transactions transfrontalières et de l’application des remises sur coupon

Désormais, un total base_row_total correct est renvoyé par l’API de commande RESTFUL lorsque la transaction transfrontalière est activée et qu’une remise de coupon est appliquée.

_ACP2E-3003 - [contribution du code GitHub](https://github.com/magento/magento2/commit/9af794a4)_

### Autres frais

#### [Braintree ] Rembourser la transaction de stockage en ligne en tant que transactionid-remboursement

_LOT-3394_

#### [Braintree] + [CLOUD] Les commandes Braintree (carte de crédit) ne peuvent pas fractionner les frais

_LOT-3421_

#### Le certificat SSL de [Braintree] [Cloud]Braintree expire le 30 juin

_LOT-3422_

#### Cookie private_content_version renvoyé dans les requêtes GQL

Correction d’un problème en raison duquel le cookie private_content_version était renvoyé dans les requêtes GraphQL, même lorsque le cookie de session était désactivé. Le cookie n’est plus inclus dans les réponses de GraphQL lorsque la session est désactivée, comme prévu.

_LYNX-339_

#### Erreur du serveur sur les props d’e-mail dans les requêtes de carte cadeau physique

Correction d’un problème en raison duquel les requêtes sender_email et recipient_email sur les cartes-cadeaux physiques entraînaient une erreur de serveur. Ces props sont désormais correctement renvoyées pour les cartes-cadeaux virtuelles et le comportement de la requête est cohérent.

_LYNX-366_

#### L’attribut is_available dans CartItemInterface renvoie toujours false pour les produits configurables

Correction d’un problème en raison duquel l’attribut is_available dans CartItemInterface renvoyait toujours la valeur false pour les produits configurables en stock. Désormais, elle reflète correctement la disponibilité comme vraie, le cas échéant.

_LYNX-380_

#### L&#39;attribut is_available dans CartItemInterface renvoie la valeur true même lorsque le stock vendable est inférieur à la quantité du produit

Correction d’un problème en raison duquel l’attribut is_available dans CartItemInterface renvoyait incorrectement la valeur true même lorsque la quantité d’articles du panier dépassait le stock vendable.

_LYNX-382_

#### l’attribut only_x_left_in_stock dans ProductInterface n’est pas précis sur les produits configurables

Correction d’un problème en raison duquel l’attribut only_x_left_in_stock dans ProductInterface ne reflétait pas précisément le stock disponible pour les variantes de produit configurables dans le panier. Désormais, la valeur only_x_left_in_stock correspond correctement aux niveaux de stock des variantes réelles, ce qui garantit que des données d’inventaire précises sont renvoyées dans la requête GQL du panier.

_LYNX-395_

#### La miniature de l’espace réservé est renvoyée lorsqu’un produit simple est ajouté au panier dans un produit groupé

Correction d’un problème en raison duquel l’ajout d’un produit simple (partie d’un produit groupé) au panier renvoyait une image miniature d’espace réservé, même si le produit était associé à une image.
Détails du correctif :
* La miniature du produit affiche désormais correctement l’image affectée, le cas échéant.
* La sélection de miniature respecte la configuration d’administration sous :
Magasins > Paramétrage > Ventes > Passage en caisse > Panier > Image de produit groupé.
Cela garantit un comportement cohérent des miniatures pour les produits regroupés en fonction des paramètres du magasin.

_LYNX-399_

#### Les attributs d’option personnalisés du client ne fonctionnent pas avec des valeurs entières

Correction d’un problème en raison duquel les attributs d’option personnalisés du client ne fonctionnaient pas lorsque la valeur renvoyée était un entier. Les options personnalisées gèrent et renvoient désormais correctement les valeurs entières comme prévu.

_LYNX-400_

#### Erreur de serveur interne lors de la tentative d’obtention de priceDetails pour les produits groupés avec un prix dynamique

Correction d’un problème où l’interrogation de price_details pour les produits groupés avec une tarification dynamique via GraphQL entraînait une erreur de serveur interne. Cette amélioration garantit la stabilité des requêtes de panier lors de l’utilisation de produits groupés configurés avec une tarification dynamique.

_LYNX-402_

#### only_x_left_in_stock renvoie toujours 0 pour les produits configurables

Correction d’un problème en raison duquel l’attribut only_x_left_in_stock renvoyait toujours 0 pour les produits configurables lorsqu’il était ajouté à l’aide du SKU parent avec des options.
Détails du correctif :
* La valeur only_x_left_in_stock reflète désormais précisément le stock de la variante enfant sélectionnée au lieu du SKU parent.
* Cela permet de s’assurer que les niveaux de stock sont correctement affichés pour les variations de produit configurables dans le panier et les pages de produit.

_LYNX-403_

#### Erreur GraphQL : type &#39;fichier&#39; non pris en charge dans la requête d&#39;options personnalisables

Correction d’un problème en raison duquel GraphQL renvoyait une erreur pour les options personnalisables de type « fichier » dans les éléments de panier. La requête renvoie désormais correctement les détails de tous les types d’options personnalisables, y compris les options basées sur des fichiers, sans causer d’erreurs.

_LYNX-405_

#### La requête GraphQL ne renvoie pas le prix normal calculé correct pour les produits personnalisables.

Correction d’un problème en raison duquel GraphQL ne renvoyait pas le prix normal calculé correct pour les produits personnalisables. La requête inclut désormais correctement le prix normal calculé avec des valeurs personnalisables appliquées (par exemple, 125 $) dans la propriété de prix, reflétant à la fois le prix de base et tous les coûts de personnalisation supplémentaires.

_LYNX-411_

#### Les taxes appliquées via les totaux estimés persistent avec des mutations mises à jour

Correction d’un problème lié à la mutation EstimatedTotals en raison duquel les taxes appliquées persistaient sur un panier même après la mise à jour de la région ou du code postal. La mutation met désormais correctement à jour les taxes appliquées lors de la modification entre les valeurs de région et de code postal, en veillant à ce que seule la règle de taxe correcte soit appliquée en fonction des données actuelles du panier.

_LYNX-412_

#### L&#39;attribut is_available dans CartItemInterface renvoie la valeur true même lorsque le stock vendable est inférieur à la quantité du produit

Correction d’un problème en raison duquel l’attribut is_available dans CartItemInterface renvoyait incorrectement la valeur true même lorsque le stock vendable était inférieur à la quantité de produit demandée. Le champ is_available renvoie désormais correctement la valeur false lorsque la quantité du produit dépasse le stock disponible.

_LYNX-420_

#### Impossible d’ajouter un coupon au panier pour l’expédition uniquement.

Correction d’un problème en raison duquel un coupon ne pouvait pas être appliqué à un panier pour les remises sur les frais d’expédition uniquement. Le coupon est désormais correctement appliqué au montant de l’expédition lors de l’utilisation d’une règle de vente sans conditions de produit, ce qui garantit que la remise attendue est appliquée aux frais d’expédition.

_LYNX-421_

#### Prix normal du produit avec 12 décimales et une valeur incorrecte

Correction d’un problème en raison duquel la valeur du prix normal dans les chemins GraphQL product.price_range.maximum_price et minimum_price ne correspondait pas au prix du catalogue lorsque plusieurs taux de taxe étaient appliqués. Le prix normal reflète désormais de manière cohérente le prix catalogue dans toutes les configurations de taxe, ce qui garantit une tarification unitaire précise, des calculs de coût total des lignes et des contrôles de remise dans le résumé du panier.

_LYNX-425_

#### Erreur de serveur GraphQL sur le panier avec le produit en rupture de stock groupé

Correction d’un problème en raison duquel GraphQL renvoyait une erreur de serveur interne lors de la récupération d’un panier contenant un produit groupé avec un article en rupture de stock, en particulier lorsque la requête incluait la propriété itemsV2. GraphQL renvoie désormais correctement une liste d’éléments avec des messages d’erreur pertinents joints à l’entrée d’élément de produit groupé, comme prévu.

_LYNX-430_

#### Impossible de créer une adresse avec des attributs personnalisés

Correction d’un problème lié à la mutation createCustomerAddress qui empêchait la création d’adresses avec les attributs personnalisés obligatoires. La mutation gère désormais correctement les attributs d’adresse personnalisés lorsque la payload appropriée est fournie.

_LYNX-441_

#### Erreur de serveur GraphQL sur le panier avec only_x_left_in_stock sur le produit groupé

Correction d’un problème en raison duquel la récupération d’un panier contenant un produit groupé avec le champ only_x_left_in_stock dans la requête GraphQL entraînait une erreur de serveur interne. GraphQL renvoie désormais correctement un flottant ou une valeur null pour le champ only_x_left_in_stock sans erreurs.

_LYNX-447_

#### Erreur GraphQL lors de la suppression d’autres produits avec un produit configurable insuffisant dans le panier

Correction d’un problème en raison duquel la tentative de suppression des produits en stock du panier entraînait une erreur GraphQL « La quantité demandée n’est pas disponible » si le panier contenait également des produits configurables avec un stock insuffisant. La suppression fonctionne désormais comme prévu sans déclencher d’erreurs.

_LYNX-464_

#### Impossible d’ajouter des produits en raison du respect de la casse dans le SKU de la mutation

Correction d’un problème en raison duquel la mutation addProductsToCart renvoyait une erreur « PRODUCT_NOT_FOUND » lors de l’utilisation de SKU avec une casse différente. La mutation gère désormais les SKU sans respect de la casse, ce qui garantit la cohérence avec les requêtes du service de catalogue et le comportement du PDP.

_LYNX-469_

#### Attribut de produit > forme abrégée de marque &trade; est renvoyé sous la forme &trade;

Résolution d’un problème de codage des caractères avec le nom du produit pour l’API GraphQL

_LYNX-603_

#### problème de mutation updateCustomerEmail

Correction d’un problème lié à la mutation updateCustomerEmail en raison duquel les clients sans attributs personnalisés obligatoires (ajoutés après la création du compte) ne pouvaient pas mettre à jour leur e-mail.

_LYNX-619_

#### Mutation setShippingAddressesOnCart renvoie une erreur lors de l’utilisation de pickup_location_code

Correction d’un problème en raison duquel la mutation setShippingAddressesOnCart renvoyait une erreur lors de l’utilisation de pickup_location_code sans spécifier customer_address_id ni d’adresse. La mutation permet désormais de définir correctement une adresse d’expédition avec uniquement le code pickup_location_code.

_LYNX-626_

#### La liste CustomerOrder.items_eligibility_for_return doit être cohérente avec les éléments de commande

Correction des incohérences concernant l’éligibilité des retours dans les commandes :
1. La liste CustomerOrder.items_eligibility_for_return est désormais cohérente avec les éléments de commande réels.
2. Le champ OrderItemInterface.eligibility_for_return renvoie correctement la valeur false lorsque la quantité complète a déjà été renvoyée.
3. CustomerOrder.items_eligibility_for_return inclut désormais uniquement les éléments qui ne sont pas déjà en cours de retour.

_LYNX-627_

#### Ajouter le champ quantity_return_requested

Ajout du champ quantity_return_requested à OrderItemInterface, ce qui permet d&#39;identifier la quantité d&#39;articles pour lesquels un retour a été soumis. Cela améliore le suivi des retours avec le champ quantity_returned existant.

_LYNX-628_

#### Les actions de commande disponible ne doivent pas contenir de RETOUR après les retours créés pour tous les articles en quantité totale

Correction d’un problème en raison duquel le champ available_actions de la requête customer.orders de GraphQL incluait incorrectement RETURN après la création d’un retour complet pour tous les articles. L’action RETOUR est désormais correctement supprimée une fois le processus de retour terminé.

_LYNX-634_

#### Compatibilité Storefront - Mettez à jour la logique pour obtenir le nom de la table avec le préfixe et d’autres améliorations mineures

Mise à jour de la logique pour récupérer le nom de la table avec le préfixe (lié aux modifications SCP).

_LYNX-637_

#### L’enregistrement dans le carnet d’adresses ne fonctionne pas lors de l’utilisation du champ same_as_shipping de la GQL setBillingAddressOnCart.

Correction d’un problème en raison duquel l’adresse d’expédition n’était pas enregistrée dans le carnet d’adresses du client lors de l’utilisation de la mutation de GraphQL setBillingAddressOnCart avec le champ same_as_shipping défini sur true. Désormais, l’adresse de livraison est correctement stockée comme prévu.

_LYNX-643_

#### Standardiser order_id dans les mutations

Normalisation de l’entrée order_id dans les mutations et mise à jour du modèle d’e-mail de confirmation d’annulation de commande afin d’exposer l’ID d’incrément au lieu de l’ID de commande.

_LYNX-650_

#### CustomerOrder n&#39;affiche pas les commentaires de commande

Correction d&#39;un problème lié à CustomerOrder afin d&#39;inclure des commentaires de commande dans les requêtes GraphQL de commande de clients et d&#39;invités.

_LYNX-651_

#### original_item_price ne doit pas inclure de remise

Mise à jour de la logique de original_item_price dans les prix des articles du panier GraphQL afin d&#39;exclure les remises.

_LYNX-652_

#### Les produits groupés affichent toujours « IN_STOCK » lorsqu’un de leurs produits groupés est en rupture de stock

Correction d’un problème en raison duquel product.stock_status pour les produits groupés affichait toujours « IN_STOCK » même si l’un des éléments groupés était en rupture de stock.

_LYNX-681_

#### La requête du client renvoie une erreur de serveur interne si la valeur de l’attribut personnalisé supprimé existe pour un client

Correction du problème en raison duquel la requête client renvoyait une erreur de serveur interne lorsqu’un attribut personnalisé supprimé avait toujours une valeur stockée. Désormais, un message d’erreur correct est renvoyé si un attribut non existant est demandé. Le cache nécessaire est invalidé lors de la suppression de l’attribut personnalisé du client.

_LYNX-686_

#### Paramètre d&#39;action pour le retour et l&#39;annulation des liens de confirmation

Paramètre d’action ajouté pour le retour et l’annulation des liens liés aux e-mails de confirmation

_LYNX-687_

#### L’URL de confirmation de l’utilisateur invité est redirigée vers la page de statut de la commande, car il manque orderRef (pour GuestRMA).

Ajout du paramètre orderRef au lien dans l&#39;e-mail de confirmation RMA invité

_LYNX-688_

#### L’URL de confirmation de l’utilisateur invité est redirigée vers la page de statut de la commande, car il manque orderRef

Ajout du paramètre orderRef au lien dans l’e-mail de confirmation d’annulation de commande invité

_LYNX-689_

#### Problèmes avec la requête du client lorsque RMA est désactivé

Mise à jour de la logique GraphQL pour s&#39;assurer que les retours précédemment créés restent accessibles même lorsque RMA est désactivé globalement. Le message d’erreur a été supprimé pour améliorer l’expérience utilisateur de storefront, afin que les clients puissent toujours consulter leurs retours précédents.

_LYNX-690_

#### GraphQL ne renvoie pas les données de panier mises à jour lors de l’application de coupons en conflit

Correction d’un problème en raison duquel l’application d’un coupon en conflit avec une priorité plus élevée entraînait un message d’erreur sans renvoyer les données de panier mises à jour. Désormais, lorsqu’un nouveau coupon invalide le coupon existant, la mutation renvoie correctement le panier avec le coupon valide appliqué.

_LYNX-696_

#### Impossible de renvoyer la valeur null pour le champ « TaxItem.title » non nullable dans le GQL placeOrder

Correction d’un problème en raison duquel la mutation placeOrder échouait avec une erreur de serveur interne en raison d’une valeur nulle pour le champ TaxItem.title non nullable. Désormais, le champ renvoie toujours une valeur valide, ce qui garantit la réussite du placement de la commande.

_LYNX-699_

#### EstimateTotals : les remises sont nulles pour les types de produits virtuels

Correction du problème en raison duquel la mutation estimateTotals renvoyait une valeur nulle pour les remises lorsqu’un code de remise est appliqué à un panier contenant des produits virtuels.

_LYNX-702_

#### Le produit groupé ne renvoie pas le pourcentage et le montant de remise corrects

De nouvelles propriétés « catalog_discount » et « row_catalog_discount » ont été introduites pour les prix des articles de catalogue afin d&#39;afficher les montants et pourcentages de remise corrects au niveau de la ligne et au niveau d&#39;un seul article.

_LYNX-703_

#### Configuration du message de cadeau au niveau du produit

Correction d’un problème où les messages cadeau n’étaient pas appliqués au niveau du produit lorsqu’ils étaient désactivés au niveau mondial. Désormais, si les messages cadeau sont activés pour un produit spécifique, ils peuvent être ajoutés à l’aide de la mutation updateCartItems et seront correctement enregistrés et reflétés.

_LYNX-714_

#### Problème lié à la suppression de l’emballage-cadeau de l’article du panier

Correction d’un problème en raison duquel la suppression de l’emballage cadeau d’un article du panier à l’aide de la mutation updateCartItems ne fonctionnait pas comme prévu. Désormais, l&#39;application et la suppression de l&#39;emballage cadeau fonctionnent correctement sans erreurs.

_LYNX-717_

#### La fonctionnalité de client enregistré correspondant ne fonctionne pas dans Boilerplate et la mutation trackViewedProduct doit être activée pour les invités.

Exposition de la mutation trackViewedProduct pour suivre l’événement d’affichage du produit pour le client et les invités

_LYNX-751_

#### la requête cart.rules renvoie une erreur au lieu d’un tableau vide si aucune règle de panier active n’est appliquée

Correction de la requête cart.rules pour renvoyer un tableau vide au lieu d’une erreur lorsqu’aucune règle de panier active n’est appliquée.

_LYNX-757_

#### Problème lors de la récupération des emballages-cadeaux pour les articles du panier

Mise à jour de la logique de récupération pour renvoyer les options d’emballage de cadeaux pour les articles du panier lorsqu’elles sont désactivées au niveau du produit, mais activées au niveau du produit

_LYNX-758_

#### les appels GraphQL avec la méthode OPTIONS renvoient un code de réponse 500 lors de l’installation du package de compatibilité adobe-commerce/storefront

Correction d’un problème en raison duquel les appels GraphQL à l’aide de la méthode OPTIONS renvoyaient une erreur de serveur interne 500 lors de l’installation du package de compatibilité adobe-commerce/storefront. Le point d’entrée renvoie désormais correctement une réponse 200/204 comme prévu.

_LYNX-778_

### Autres outils de développement

#### [Problème ] correction de l’erreur de syntaxe HTML dans visual.phtml.

Le système ferme désormais correctement la balise de démarrage dans le fichier visual.phtml, en veillant à utiliser la syntaxe HTML appropriée. Auparavant, la balise de début n’était pas fermée correctement, ce qui provoquait une erreur de syntaxe HTML.

_AC-10658 - [Problème GitHub](https://github.com/magento/magento2/issues/38247) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37457)_

#### [Problème ] modification de « actif » en « activé » dans la commande de maintenance bin/magento:status

Le système fournit désormais des messages de statut plus précis pour la commande du mode de maintenance, changeant le statut de « actif » en « activé » et de « non actif » en « désactivé ». Auparavant, le message d’état de la commande du mode de maintenance s’affichait comme « actif » ou « non actif », ce qui pouvait prêter à confusion.

_AC-11474 - [Problème GitHub](https://github.com/magento/magento2/issues/38486) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38410)_

#### La navigation dans l’arborescence des catégories entraîne des erreurs dans Redis : « La session Redis a dépassé les connexions simultanées »

_AC-12571 - [Problème GitHub](https://github.com/magento/magento2/issues/38851) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/0611e750)_

#### Problèmes de CSP combinés avec dev/css/use_css_critical_path

Le système charge désormais correctement les fichiers CSS de manière asynchrone sur les pages de passage en caisse, même lorsque le paramètre « dev/css/use_css_critical_path » est activé, ce qui garantit que ces pages sont rendues avec les styles CSS appropriés. Auparavant, une politique de sécurité du contenu (CSP) restreinte empêchait l’exécution du JavaScript intégré, ce qui entraînait le chargement inattendu des fichiers CSS.

_AC-12731 - [Problème GitHub](https://github.com/magento/magento2/issues/39020) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39040)_

#### En utilisant le type virtuel pour configurer le plug-in, la méthode intercepteur ne peut pas être générée correctement dans `setup:di:compile` commande

Le système génère désormais correctement des méthodes d&#39;interception lors de l&#39;utilisation d&#39;un type virtuel pour configurer un plug-in, assurant ainsi des résultats cohérents qu&#39;ils soient précompilés ou compilés à l&#39;exécution. Auparavant, le système générait des résultats incorrects lors de la précompilation par rapport à la compilation à l’exécution.

_AC-13398 - [Problème GitHub](https://github.com/magento/magento2/issues/33980) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38141)_

#### Les tests unitaires Adobe Commerce 2.4.7-p3 échouent

Aucune note de mise à jour n’est requise.

_ACP2E-3631 - [contribution du code GitHub](https://github.com/magento/magento2/commit/982b1c42)_

### Paiement / Modes de paiement, Commande

#### Les informations de carte de crédit de payflow papal enregistrées pour une utilisation ultérieure ne s’affichent pas sur la page des modes de paiement stockés

Les informations de carte de crédit de payflow papal enregistrées précédemment pour une utilisation ultérieure ne s&#39;affichaient pas sur la page de méthode de paiement stockée qui est maintenant fixe les informations de carte de crédit s&#39;affichent sur la page de méthode de paiement stockée.

_AC-13699 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/96dec499)_

### Paiements

#### Le paiement par carte de crédit (lien de flux de paiements) ne fonctionne pas

Erreur d&#39;obtention précédente (le paiement a été refusé) lors de la commande avec la carte de crédit après la correction Commande passée avec succès.

_AC-13414 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a68324bc)_

#### Payflow crée une transaction chaque fois que nous cliquons sur le bouton de récupération sur l&#39;écran Afficher la transaction

Le système récupère désormais correctement les informations de transaction sans créer de transaction de paiement chaque fois que le système clique sur le bouton de récupération sur l&#39;écran d&#39;affichage des transactions. Auparavant, cliquer sur le bouton de récupération créait incorrectement une nouvelle transaction de paiement pour une commande qui avait déjà été payée.

_ACP2E-2841 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/b2286ecf)_

#### Le message Paylater ne s&#39;affiche pas dans le PDP pour le compte de commerçant paypal canadien

Le système affiche désormais correctement le message PayLater pour les comptes marchands PayPal canadiens sur la page des détails du produit (PDP) lorsque le pays de l&#39;acheteur peut être déterminé à partir de l&#39;adresse de facturation du compte ou de l&#39;expédition. Auparavant, le message PayLater ne s’affichait pas en raison d’un paramètre manquant, ce qui entraînait une erreur dans la console du navigateur.

_ACP2E-3028 - [contribution du code GitHub](https://github.com/magento/magento2/commit/6a185204)_

#### Le remboursement de la commande PayPal génère un avoir en double

Correction du problème de simultanéité des avoirs créés par IPN pour le service de paiement PayPal.

_ACP2E-3143 - [contribution du code GitHub](https://github.com/magento/magento2/commit/d01ee51e)_

#### La règle de prix du panier ne fonctionne pas pour Paypal

Le montant correct s&#39;affiche côté PayPal lorsque la remise est appliquée par mode de paiement

_ACP2E-3163 - [contribution du code GitHub](https://github.com/magento/magento2/commit/7377de59)_

#### [Cloud] Les utilisateurs disposant d’un rôle spécifique ne peuvent pas se connecter

Un utilisateur administrateur dont le rôle contient uniquement un accès à la section PayPal peut désormais se connecter sans erreur

_ACP2E-3208 - [contribution du code GitHub](https://github.com/magento/magento2/commit/66dea0de)_

### Performances

#### Problème de paramètres d’attributs de produit par défaut

Le système permet désormais aux utilisateurs et utilisatrices de désélectionner une option par défaut pour un attribut de produit, en s’assurant que l’attribut n’a pas toujours de valeur par défaut définie. Auparavant, une fois qu’une valeur par défaut était définie pour un attribut de produit, il n’était pas possible de la désélectionner, ce qui définissait toujours une valeur par défaut pour l’attribut.

_AC-11932 - [Problème GitHub](https://github.com/magento/magento2/issues/38703) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/7d5e3906)_

#### [Problème] Nettoyage du code, ajout d’un nouveau bloc principal critique et déplacement du code CSS critique avant les ressources

Le système comprend désormais un nouveau bloc d’en-tête critique et déplace le CSS critique avant les ressources, ce qui permet une plus grande personnalisation et optimisation des performances sur le front-end. Auparavant, le CSS critique n’était pas positionné avant les ressources, ce qui limitait les opportunités de personnalisation et d’optimisation.

_AC-12000 - [Problème GitHub](https://github.com/magento/magento2/issues/38748) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/35580)_

#### La compilation du thème s&#39;interrompt lorsque l&#39;hôte mysql contient des informations sur le port

Le système gère désormais correctement la configuration de l’hôte MySQL qui inclut les informations de port, assurant ainsi une compilation réussie du thème. Auparavant, la compilation du thème échouait si la configuration de l’hôte MySQL dans la connexion à la base de données incluait des informations sur le port.

_AC-12176 - [Problème GitHub](https://github.com/magento/magento2/issues/38799) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38842)_

#### Prise en charge de l’interface CommandLoaderInterface de Symfony dans l’interface de ligne de commande Magento

Cette modification réduit le temps d’initialisation de l’application de ligne de commande Magento en permettant l’initialisation différée des commandes jusqu’à ce qu’elles soient nécessaires.

_AC-13471 - [Problème GitHub](https://github.com/magento/magento2/issues/29266) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/29355)_

#### Problème de performance lors du chargement des attributs de produit dans les règles de panier

Amélioration des performances des requêtes pour les règles de vente (d’environ 150 ms à un seul chiffre).

_ACP2E-2494 - [contribution du code GitHub](https://github.com/magento/magento2/commit/ba25af8a)_

#### Performances d’indexation partielle du prix

Les performances de l’indexation partielle du prix ont été améliorées en optimisant certaines des requêtes de suppression utilisées dans le processus d’indexation.

_ACP2E-2673 - [contribution du code GitHub](https://github.com/magento/magento2/commit/ba25af8a)_

#### La commande est rejetée lors de la configuration multi-magasin lors de l’utilisation du traitement asynchrone des commandes + Conditions générales

Les commandes passées à partir de sites web autres que ceux par défaut dont les conditions générales sont activées sont maintenant traitées.
Avant qu&#39;ils ne soient automatiquement rejetés.

_ACP2E-2850 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/57a32313)_

#### L’exécution de l’appel de l’API REST de commande prend beaucoup de temps

Le système exécute désormais l’appel API Order Rest dans un délai raisonnable, ce qui améliore les performances lors de la récupération d’un grand nombre de commandes. Auparavant, l’exécution de l’appel de l’API REST Order prenait beaucoup de temps, ce qui entraînait des retards lors de la récupération d’un grand nombre de commandes.

_ACP2E-2910 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/001e5188)_

### Performances, promotion

#### L’indexeur des règles de vente a cessé de fonctionner

Le système termine désormais l’indexeur de règles de vente avec succès, même avec un grand nombre de groupes de filtres combinés, en veillant à ce que les conditions des règles du panier soient appliquées au panier comme prévu. Auparavant, l’indexeur de règles de vente ne se terminait pas lorsqu’il y avait un grand nombre de groupes de filtres combinés, ce qui entraînait un message d’erreur et empêchait l’application des conditions des règles du panier.

_ACP2E-2617_

### Tarification

#### Magento2.4.6-p4 Order API Simple Item Prix manquant

Le système affiche désormais correctement le prix des produits simples lorsqu’ils sont interrogés via l’API de commande, garantissant ainsi une représentation précise des données. Auparavant, le prix de produits simples s’affichait incorrectement comme zéro dans la réponse de l’API.

_AC-11810 - [Problème GitHub](https://github.com/magento/magento2/issues/38603)_

#### Erreur d’arrondi de centime dans la règle de catalogue

_AC-13855 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/276e0acd)_

### Produit

#### Des caractères spéciaux dans le nom de produit associé configurable sont en cours de conversion en entités HTML.

Le système conserve désormais correctement les caractères spéciaux dans les noms des produits associés lors de la modification d’un produit configurable, ce qui empêche leur conversion en entités HTML. Auparavant, les caractères spéciaux dans les noms de produits associés étaient convertis en entités HTML lorsque le produit configurable était modifié.

_AC-10535 - [Problème GitHub](https://github.com/magento/magento2/issues/38146) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38447)_

#### La fonction ProductRepository GetById ne crée pas la clé de cache correcte

Le système crée désormais correctement une clé de cache dans la fonction GetById du référentiel de produits, que l’ID de magasin soit transmis sous la forme d’une chaîne ou d’un entier. Cela garantit que le produit est récupéré de la mémoire lors des appels suivants, ce qui améliore les performances. Auparavant, le système récupérait le produit de la base de données chaque fois que la fonction était appelée, même avec les mêmes paramètres, en raison d’une création de clé de cache incorrecte.

_AC-10947 - [Problème GitHub](https://github.com/magento/magento2/issues/38384) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38433)_

#### [Problème] [MFTF] Ajouté AdminClickAddOptionForBundleItemsActionGroup

Le système inclut désormais AdminClickAddOptionForBundleItemsActionGroup, ce qui améliore les fonctionnalités du panneau d’administration. Auparavant, ce groupe d’actions n’était pas disponible.

_AC-11992 - [Problème GitHub](https://github.com/magento/magento2/issues/30857) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/30838)_

#### [Problème] Correction d’une faute de frappe dans le bloc PHPDoc

Le système supprime désormais correctement une variable référencée inconnue dans PHPDoc pour la déclaration de variable $helper, ce qui améliore la clarté et la précision du code. Auparavant, cette variable référencée inconnue dans PHPDoc provoquait une confusion et des inexactitudes potentielles dans le code.

_AC-13173 - [Problème GitHub](https://github.com/magento/magento2/issues/38961) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38940)_

#### [Problème ] Correction d’un lot rompu et de la mise en page des pages de produits téléchargeables dans Magento >= 2.4.7

La mise en page du lot et des pages de produits téléchargeables a été corrigée, ce qui garantit un affichage cohérent et correct sur tous les appareils. Auparavant, ces pages rencontraient des problèmes de mise en page en raison d’une réorganisation du bloc de médias d’informations sur le produit.

_AC-13423 - [Problème GitHub](https://github.com/magento/magento2/issues/39403) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/6cfb9b6b)_

#### AlertProcessor - L’argument #2 ($storeId) doit être de type int, chaîne donnée.

Le système déclenche désormais correctement les e-mails d’alerte de produit en s’assurant que l’identifiant du magasin est du type de données correct. Auparavant, les e-mails d’alerte de produit n’étaient pas envoyés en raison d’une incohérence de type dans l’identifiant du magasin.

_AC-5969 - [Problème GitHub](https://github.com/magento/magento2/issues/35602) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/0574ac23)_

#### La fonction [Cloud] addFilterToMap ne fonctionne pas pour certaines colonnes

Désormais, le module personnalisé peut être utilisé dans la grille de commande. Des erreurs se produisaient précédemment lors de l’utilisation d’un module personnalisé.

_ACP2E-2944 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/3a7c4d17)_

#### [Cloud] Produits dans la catégorie - Ajouter des produits - Attribuer - Tout sélectionner

Les utilisateurs peuvent désormais sélectionner ou désélectionner des produits à l’aide du bouton (bascule).

_ACP2E-3471_

### Promotion

#### Attribut du client non visible lors de la création du compte à partir de l’invitation

Les attributs du client sont disponibles lors de la création du compte à partir d’une invitation.

_ACP2E-2602 - [contribution du code GitHub](https://github.com/magento/magento2/commit/39d54c2d)_

#### Le code de coupon avec la limite Utilisés par coupon n&#39;est pas libéré pour le paiement a échoué avec l&#39;annulation de la commande

Le système met désormais immédiatement à jour les utilisations des coupons lorsqu’une commande est créée ou annulée, et ajoute les utilisations des règles à une file d’attente pour éviter les blocages potentiels. Cela permet de libérer un code de coupon avec une limite « Utilisations par coupon » et de le réutiliser si une commande est annulée en raison d’un échec de paiement. Auparavant, le système ne libérait pas le code de coupon pour le réutiliser dans de tels cas, ce qui entraînait un message d’erreur indiquant que le code de coupon n’était pas valide.

_ACP2E-2627 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/c971859e)_

#### [Cloud] Réindexation de la règle de catalogue L’indexeur de produit lance SQLSTATE[HY000] : Erreur générale : le serveur MySQL 2006 est parti.

Le système gère désormais correctement la valeur « batchCount » personnalisée dans le fichier di.xml pour « Magento\CatalogRule\Model\Indexer\IndexBuilder », ce qui empêche les erreurs SQL telles que « Erreur générale : le serveur MySQL 2006 est parti » lors de la réindexation de l’indexeur de produit de règle de catalogue en raison d’une taille de lot incorrecte sur les catalogues volumineux

_ACP2E-2811 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/b2286ecf)_

#### [CLOUD]Règle de prix de panier pour les visiteurs Segment client n’appliquant pas de remise au panier

Le système applique désormais correctement les règles de prix du panier pour les segments de clientèle des visiteurs, même si la règle n’utilise pas de coupon, en s’assurant que les remises appropriées sont appliquées au panier. Auparavant, les remises n’étaient pas appliquées au panier pour les segments de clientèle des visiteurs, sauf si la règle de prix du panier utilisait un coupon.

_ACP2E-2926_

#### Attribut « Type » manquant dans l’onglet « Produits à faire correspondre » des règles de produits associés

L’attribut « Type » est désormais disponible sous la forme d’une option de filtre dans l’onglet « Produits à faire correspondre » du module « Règles de produits associés », ce qui permet de définir des règles plus précises. Auparavant, cet attribut était absent de l’onglet « Produits à faire correspondre », ce qui limitait la possibilité de créer des critères de correspondance précis.

_ACP2E-3024_

#### La règle de vente avec l&#39;attribut Étape de quantité de remise (Achat X) empêche l&#39;application d&#39;autres règles

La règle de prix du panier n’annule pas les règles précédemment appliquées si la quantité du produit dans le panier est insuffisante pour que la règle soit appliquée.

_ACP2E-3139 - [contribution du code GitHub](https://github.com/magento/magento2/commit/d01ee51e)_

#### Problème de performance sur la règle de prix de panier - Module Règle de vente anticipée

Ajout d’index de base de données manquants pour les filtres AdvancedSalesRule.

_ACP2E-3331_

#### Émettre des règles de vente avec une remise de montant fixe et une remise de quantité maximale est appliquée à

Correction d’un problème lié à la remise relative aux règles du panier, lorsque la remise de montant fixe est configurée pour être appliquée à une quantité limitée de produits dans le panier. Auparavant, la valeur « Remise Qté maximale appliquée à » était utilisée pour calculer le prix de l’article actuel dans le panier, et pas seulement pour calculer la remise de la règle.

_ACP2E-3332 - [contribution du code GitHub](https://github.com/magento/magento2/commit/581b7ef1)_

#### La mise à niveau de [CLOUD] Magento entraînait le respect de la casse des coupons

Avant la correction, vous deviez saisir le code de coupon tel qu’il était configuré en tenant compte des majuscules et des minuscules. Désormais, le coupon sera validé dans le serveur principal, quelle que soit la configuration du code en majuscules ou en minuscules.

_ACP2E-3342_

#### Règles de panier « Remise de montant fixe pour l’ensemble du panier »  L’action applique incorrectement les remises

Les codes promotionnels seront validés correctement, indépendamment des majuscules ou des minuscules, lorsqu’ils sont utilisés pour la création de la commande à partir de la zone d’administration. Auparavant, le code de coupon n’était pas validé s’il ne correspondait pas à la casse exacte de la lettre du code de règle de panier configuré.

_ACP2E-3349 - [contribution du code GitHub](https://github.com/magento/magento2/commit/581b7ef1)_

#### Dans le serveur principal, stockez les valeurs par défaut des attributs de produit (au lieu des valeurs d’administration attendues).

Désormais, dans le serveur principal, les valeurs d’administration sont utilisées au lieu des valeurs de magasin par défaut pour les attributs de produit.

_ACP2E-3374 - [contribution du code GitHub](https://github.com/magento/magento2/commit/5184c067)_

#### L’action Règles de panier « Remise de montant fixe pour l’ensemble du panier » applique incorrectement les remises lors de l’ajout de produits groupés

Les règles de panier à montant fixe n’étaient pas correctement appliquées pour les produits groupés. Désormais, lors du calcul du montant de la remise totale, les produits enfants groupés sont pris en compte, ce qui permet d’obtenir un calcul de remise correct.

_ACP2E-3377 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/1366ae5e)_

#### Règles de prix de panier calculant incorrectement la remise

Les escomptes à montant fixe sont maintenant correctement calculés. Avant la correction, les remises sur montant fixe n’étaient pas correctement totalisées pour les produits groupés.

_ACP2E-3403 - [contribution du code GitHub](https://github.com/magento/magento2/commit/0b488dd1)_

#### Les catégories imbriquées dans les conditions de règle ne s’affichent pas

Correction d’un problème en raison duquel les catégories imbriquées sous la catégorie de niveau 3 ne s’affichaient pas dans les règles marketing pour la condition de catégorie

_ACP2E-3406 - [contribution du code GitHub](https://github.com/magento/magento2/commit/88660e79)_

#### usage_limit et uses_per_customer ne sont pas mis à jour dans la table salesrule_coupon.

La mise à jour des Utilisations par coupon et des Utilisations par client dans la règle de prix du panier affecte désormais les coupons générés automatiquement existants. Auparavant, les nouvelles valeurs affectaient uniquement les nouveaux coupons

_ACP2E-3432 - [contribution du code GitHub](https://github.com/magento/magento2/commit/88660e79)_

#### La règle de prix du panier ne prend pas en compte la catégorie parent lorsqu’elle utilise la condition « égal à ou supérieur à ».

Les règles de prix de panier considèrent désormais correctement la catégorie parent lorsqu’elle est utilisée dans des conditions avancées

_ACP2E-3456 - [contribution du code GitHub](https://github.com/magento/magento2/commit/93359343)_

#### Calcul de remise non valide avec priorité

Dans le cas d’un montant fixe appliqué pour le type de remise Panier entier, le montant n’était pas calculé correctement pour les articles du panier qui étaient déjà remis par une promotion précédente. Désormais, les remises sont correctement résumées.

_ACP2E-3463 - [contribution du code GitHub](https://github.com/magento/magento2/commit/078c387e)_

#### [CLOUD] Le calcul des frais d’expédition ne prend pas en compte la règle du panier

Avant la correction, une règle de panier avec une condition de région n’était pas appliquée de manière cohérente. Après le correctif, les règles de panier avec des conditions de région sont correctement appliquées.

_ACP2E-3472 - [contribution du code GitHub](https://github.com/magento/magento2/commit/d4de4726)_

#### La condition de SKU de la règle de panier échoue pour la facture.

La remise sur le produit groupé avec prix dynamique est désormais correctement répercutée dans la facture. Auparavant, la remise n&#39;était pas reflétée sur la facture.

_ACP2E-3491 - [contribution du code GitHub](https://github.com/magento/magento2/commit/3f12d152)_

#### Valeur de remise incorrecte lorsque plusieurs règles de prix de panier sont appliquées simultanément avec des produits à prix réduit/spéciaux

Avant la correction, le montant fixe pour l’ensemble des règles du panier n’était pas correctement appliqué si plusieurs règles étaient appliquées. Désormais, les règles de panier de remises à montant fixe sont correctement appliquées.

_ACP2E-3498 - [contribution du code GitHub](https://github.com/magento/magento2/commit/1984c61c)_

### Renvoie

#### [CLOUD] Les utilisateurs administrateurs restreints peuvent voir le menu et les boutons de retour

Les utilisateurs administrateurs restreints n’ont désormais pas accès aux contrôles liés à RMA (menu et boutons).
Les utilisateurs administrateurs précédemment restreints pouvaient voir le menu et les boutons de retour.

_ACP2E-3330_

#### L’écran de retour est corrompu lors de l’actualisation de l’écran

L’utilisateur ou l’utilisatrice peut actualiser la page sans distorsion d’écran.

_ACP2E-3443_

### SEO

#### L’ajout de réécritures d’URL avec un accent entraîne un chargement infini

Le système réussit désormais à créer et à faire fonctionner les réécritures d’URL avec des accents, empêchant le chargement infini pendant le processus d’enregistrement. Auparavant, l’ajout d’une réécriture d’URL avec un accent provoquait un problème de chargement infini.

_AC-11907 - [Problème GitHub](https://github.com/magento/magento2/issues/38692) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/44cef3a9)_

#### Réécriture d’URL de catégorie erronée pour plusieurs magasins pour la catégorie de troisième niveau

Générer des réécritures d’URL correctes pour les enfants avec un parent avec une clé d’URL étendue personnalisée

_ACP2E-2641 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/ea79f7dd)_

#### Des caractères à deux octets (caractères spéciaux) dans le champ Nom du produit bloquent la création du produit en arrière-plan

Un nouveau paramètre a été ajouté pour vous permettre d’appliquer ou non une translittération à l’URL du produit. Le paramètre est disponible ici : Magasins > Configuration > Catalogue > Catalogue > Optimisation du moteur de recherche : « Appliquer la translittération à l’URL du produit »

_ACP2E-2770 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/b2286ecf)_

#### Création d’entrées url_rewrite incorrecte avec plusieurs magasins dans un groupe de magasins

Avant la correction, vous ne pouviez générer des réécritures d’URL qu’au niveau d’un site web lors de la modification d’un produit. Avec le correctif, un nouveau paramètre a été introduit (Magasins > Configuration > Catalogue > Catalogue > Optimisation du moteur de recherche, « Portée de la réécriture des URL de produit » avec les options « Vue du magasin », « Site Web ») qui vous permet de générer des réécritures d’URL au niveau du magasin ou du site Web.

_ACP2E-3383 - [contribution du code GitHub](https://github.com/magento/magento2/commit/2d627301)_

### Ventes

#### La deuxième règle de prix de panier n’est pas appliquée si la première règle de panier est déjà appliquée.

_AC-13751_

### Rechercher

#### Obtention de « Saisissez un terme de recherche et réessayez ». erreur sur la page de recherche avancée dans storefront dans 2.4.8-beta1

Le système affiche désormais correctement les résultats de la recherche sur la page Recherche avancée lorsqu’un attribut de produit est défini sur « Non ». Auparavant, la définition d’un attribut de produit sur « Non » et l’exécution d’une recherche entraînait un message d’erreur « Saisissez un terme de recherche et réessayez ».

_AC-13053 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/3ea26621)_

#### magento/module-open-search dépend d’une branche opensearch-php inexistante

_AC-13721 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/05dc0bbf)_

#### la table search_query, lorsqu’elle est de taille importante, a un impact important sur le temps de chargement frontal

Amélioration du temps de chargement de la page de liste de recherche. Avant la correction, la page de liste de recherche était retardée en raison d’une requête non optimisée.

_ACP2E-3362 - [contribution du code GitHub](https://github.com/magento/magento2/commit/55615e61)_

### Sécurité

#### [Problème] Menu contextuel Paylater de police manquant

Le système permet désormais de charger la police « https://www.paypalobjects.com/webstatic/mktg/2014design/font/PP-Sans/PayPalSansBig-Medium.woff&#39; » sans enfreindre la directive de la politique de sécurité du contenu, ce qui garantit l’affichage correct de la fenêtre contextuelle Paylater. Auparavant, le chargement de la police était refusé en raison d’une violation de la directive de la politique de sécurité du contenu, ce qui provoquait des problèmes d’affichage avec la fenêtre contextuelle Paylater.

_AC-11855 - [Problème GitHub](https://github.com/magento/magento2/issues/38624) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/37401)_

#### [Problème ] mettez à jour le texte DOM js.js réinterprété comme HTML.

L’utilisation d’innerText évite le risque d’injection dans HTML, car ces propriétés échappent automatiquement aux caractères spéciaux HTML dans le texte fourni. Ce correctif permet d’éviter les vulnérabilités de type cross-site scripting (XSS) en traitant l’entrée comme du texte brut plutôt que comme une interprétation d’HTML.

_AC-12035 - [Problème GitHub](https://github.com/magento/magento2/issues/38767)_

#### ReCaptcha V2 s’affiche incorrectement lors du passage en caisse pour la langue allemande

Auparavant, le recaptcha de sous l’adresse e-mail du passage en caisse s’affichait sans style pour les langues comportant des mots longs, comme l’allemand. Ensuite, le recaptcha sera identique à tous les éléments recaptcha du reste des zones.

_ACP2E-3273 - [contribution du code GitHub](https://github.com/magento/magento2/commit/7377de59)_

#### Captcha lors de la connexion administrateur ne nécessite pas d’interaction pour certains utilisateurs

ReCaptcha pour la connexion admin est validé comme prévu

_ACP2E-3300 - [contribution du code GitHub](https://github.com/magento/security-package/commit/8f64ab3c)_

### Expédition

#### [Problème ] Correction d’une faute de frappe dans tracking.phtml - les fonctions JS « currier » ont été renommées « carrier »

Le système utilise désormais correctement le terme « carrier » au lieu du « currier » mal orthographié dans les fonctions de gestionnaire de JavaScript utilisées dans le modèle de suivi des commandes, ce qui permet d’assurer un nom de fonction et une clarté de code corrects. Auparavant, le terme mal orthographié « currier » était utilisé, ce qui entraînait une confusion et une incohérence potentielles dans la base de code.

_AC-10757 - [Problème GitHub](https://github.com/magento/magento2/issues/34523) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/33414)_

#### REPOS UPS « Un envoi ne peut pas avoir un KGS/IN ou un LBS/CM ou un OZS/CM comme unité de mesure »

Assurez-vous que les taux d’onduleur sont visibles dans le passage en caisse et le panier.

_AC-11938 - [Problème GitHub](https://github.com/magento/magento2/issues/38618) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/493e01f5)_

#### Mises à jour des instructions de configuration « sandbox » et « prod » du REST UPS dans devdoc

_AC-12938_

#### [Problème ] orthographe correcte des variables pour l’adresse du client

Le système épelle désormais correctement les variables pour les adresses des clients, ce qui garantit un affichage précis dans la zone de compte du front-end. Auparavant, une orthographe incorrecte de ces variables pouvait entraîner des erreurs lors des révisions du code local.

_AC-13172 - [Problème GitHub](https://github.com/magento/magento2/issues/32817) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/32815)_

#### Fenêtre de tracking indiquant une date de livraison prévue incorrecte

Afficher la date de livraison correcte pour l’opérateur Fedex.

_ACP2E-2738 - [contribution du code GitHub](https://github.com/magento/magento2/commit/57a32313)_

#### Les Taux Du Tableau S’Affichent Toujours Même Si La Livraison Gratuite Est Appliquée

La méthode d&#39;expédition au tarif du tableau s&#39;affiche maintenant même si l&#39;expédition gratuite devient disponible après l&#39;application du coupon

_ACP2E-2763 - [contribution du code GitHub](https://github.com/magento/magento2/commit/b2286ecf)_

#### Échec du test MFTF AdminCreatingShippingLabelTest en raison d&#39;informations d&#39;identification non ajoutées dans l&#39;environnement Jenkins

correctif de test mftf

_ACP2E-2765 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/ea79f7dd)_

#### L’API de suivi FedEx ne fonctionne pas avec les informations d’identification REST

Auparavant, l’intégration FedEx ne nécessitait pas de clés API supplémentaires pour l’API de suivi. Une nouvelle configuration a été ajoutée pour prendre en charge les clés d’API de suivi.

_ACP2E-3340 - [contribution du code GitHub](https://github.com/magento/magento2/commit/ec7e32a9)_

#### [Cloud] Taux négociés FedEx non retournés sur REST

Avant la correction, les taux spécifiques au compte FedEx n&#39;étaient pas envoyés sur la réponse, même si selon la documentation de FedEx, ils auraient dû être envoyés. Après la correction, les taux spécifiques au compte sont envoyés sur la réponse en modifiant la requête de notre côté.

_ACP2E-3354 - [contribution du code GitHub](https://github.com/magento/magento2/commit/55615e61)_

### Évaluation et prévisualisation

#### Les paramètres de mise à jour planifiée ne sont pas enregistrés s’ils ont été initialement ajoutés en exécutant la mise à jour

Le système efface désormais correctement les valeurs des attributs de produit dans les mises à jour planifiées suivantes lorsque ces attributs sont modifiés dans la mise à jour en cours d’exécution. Auparavant, lorsqu’un attribut de produit était modifié par une mise à jour planifiée en cours d’exécution, il était impossible d’effacer ces valeurs d’attribut lors de la création d’une mise à jour planifiée, ce qui nécessitait que l’utilisateur les modifie après la création.

_ACP2E-2901_

#### La règle de prix du panier à partir de la date et jusqu’à la date n’a pas été synchronisée avec la mise à jour intermédiaire

Les dates sont enregistrées en fonction des mises à jour de l’évaluation des règles de prix de panier.

_ACP2E-2999_

#### Erreur JS dans l’aperçu intermédiaire

Désormais, le fichier form-mini-stub.js se charge sans erreur de syntaxe Js dans les outils de développement.

_ACP2E-3104_

#### Impossible de mettre à jour le contenu échelonné du prix spécial du produit

Le système permet désormais de modifier la date de fin d’une campagne de mise à jour des prix après son lancement, ce qui permet aux utilisateurs d’apporter les ajustements nécessaires à leurs campagnes. Auparavant, une erreur était générée lors de la tentative de mise à jour de la date de fin d’une campagne active, empêchant les utilisateurs d’apporter des modifications.

_ACP2E-3162_

#### Impossible de mettre à jour la mise à jour planifiée lors de l’utilisation de l’attribut de catégorie personnalisée unique

Correction d’un problème en raison duquel la mise à jour d’une mise à jour planifiée pour une catégorie n’était pas possible si la catégorie avait un attribut unique

_ACP2E-3453 - [contribution du code GitHub](https://github.com/magento/magento2/commit/078c387e)_

### Ciblage

#### [Problème ] Autoriser l’utilisation de plages CIDR dans la liste autorisée de maintenance

Le système prend désormais en charge l’utilisation de plages CIDR dans la liste d’adresses IP autorisées du mode de maintenance, ce qui permet à une plage d’adresses IP de contourner le mode de maintenance. Auparavant, la liste autorisée d’adresses IP du mode de maintenance autorisait uniquement les adresses IP individuelles à contourner le mode de maintenance.

_AC-9432 - [Problème GitHub](https://github.com/magento/magento2/issues/37943) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/30699)_

### Taxe

#### [Problème] promotion de propriété de constructeur Feature/php8.1 wee graph ql

Remplacez presque toutes les propriétés par la promotion de propriété du constructeur dans le module GraphQL :

_AC-13295 - [Problème GitHub](https://github.com/magento/magento2/issues/39309) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/36975)_

#### La taxe sur les produits fixes (FPT) ne fonctionne pas avec les produits configurables

FPT pour que les variations de produit configurables fonctionnent correctement.

_ACP2E-3193 - [contribution du code GitHub](https://github.com/magento/magento2/commit/ec7e32a9)_

### Framework de test

#### Échec du test d’intégration testDbSchemaUpDate en raison du type de colonne JSON

Le système reconnaît désormais correctement les types de colonnes JSON dans le schéma de base de données lors des tests d&#39;intégration, ce qui empêche les échecs de test en raison d&#39;une incohérence entre le schéma de base de données et le schéma déclaratif. Auparavant, le système identifiait incorrectement les types de colonnes JSON en tant que LONGTEXT dans MariaDB, ce qui entraînait l’échec des tests d’intégration.

_AC-11654 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/ef81f5a2)_

#### [Problème] Orthographe de correction PHPDoc

Le système reconnaît désormais correctement les méthodes obsolètes dans les IDE en raison d’une correction orthographique dans le PHPDoc. Auparavant, une erreur d’orthographe dans le PHPDoc empêchait les IDE de reconnaître certaines méthodes comme obsolètes.

_AC-13362 - [Problème GitHub](https://github.com/magento/magento2/issues/31399) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/31398)_

#### MAGETWO-95118 : vérification du comportement avec le panier persistant après l’expiration de la session

_AC-13478 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/7d5e3906)_

#### Échec des tests d’intégration Magento\NegotiableQuote\Controller\Quote\DownloadTest::testCompanyManagerDownloadWithNQSubPermission

_AC-13716_

#### [Comparaison de base de données] Erreur fatale si la base de données contient un enregistrement sur la règle cible sans conditions

Auparavant, si la base de données contenait des enregistrements sur la règle cible sans condition obtenait des erreurs fatales, mais après que l&#39;outil de comparaison de base de données de correctif soit correctement exécuté sans erreurs fatales.

_AC-13722_

#### Correction des tests statiques pour permettre leur utilisation par des extensions tierces

_AC-13848 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/9e383b4d)_

#### [Interne] l’échec de l’application des correctifs n’est pas affiché pendant l’exécution ou dans les journaux

&#39;-

_ACP2E-3334 - [contribution du code GitHub](https://github.com/magento/magento2/commit/d4de4726)_

#### [MFTF] StorefrontCheckoutProcessForQuoteWithoutNegotiatedPriceTest

Mftfs fixes

_ACP2E-3458 - [contribution du code GitHub](https://github.com/magento/magento2/commit/078c387e)_

### Framework de l’interface utilisateur

#### Correctif de vulnérabilité de sécurité Prototype.js CVE-2020-27511

Le système a été mis à jour pour résoudre la vulnérabilité de sécurité CVE-2020-27511 dans Prototype.js 1.7.3, ce qui améliore la sécurité globale du système. Avant cette mise à jour, le système était susceptible de subir un déni de service d’expression régulière (ReDOS) par le biais de la suppression des balises HTML conçues.

_AC-12128 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/de4dfb8e)_

#### Grunt Less utilise pub/ préfixe pour les mappages source

Le système génère désormais moins de mappages source /css sans le préfixe /pub pour les chemins d’accès lors de l’utilisation de Grunt, ce qui élimine la nécessité d’une solution de contournement dans la configuration du serveur web. Auparavant, l’utilisation du préfixe /pub dans les chemins d’accès des plans de source nécessitait une configuration spécifique dans le serveur web pour fonctionner correctement.

_AC-12189 - [Problème GitHub](https://github.com/magento/magento2/issues/38837) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38840)_

#### Champ Du Fichier De Composant De L’Interface Utilisateur

Le système valide désormais correctement le champ de fichier dans un formulaire de composant d’interface utilisateur, ce qui permet d’envoyer le formulaire sans erreur lorsqu’un fichier est sélectionné. Auparavant, la validation échouait même lorsqu’un fichier était sélectionné, ce qui empêchait l’envoi du formulaire.

_AC-12432 - [Problème GitHub](https://github.com/magento/magento2/issues/38908) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39004)_

#### [Problème ] Format de date amélioré dans la console js : passez de 12 heures à 24 heures pour...

Amélioration du format de date dans la console js : passez de 12 heures à 24 heures.

_AC-12645 - [Problème GitHub](https://github.com/magento/magento2/issues/38983) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38972)_

#### [Problème] ajouter la génération sourceMap pour moins de fichiers en mode développeur

Le système génère désormais des mappages source pour moins de fichiers en mode de développement, ce qui facilite l’identification de la source d’un style. Auparavant, l’identification de la source d’un style était difficile lors de l’exécution du système en mode développeur avec une compilation côté serveur moins .

_AC-12650 - [Problème GitHub](https://github.com/magento/magento2/issues/38982) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38977)_

#### Du contenu statique est déployé pour les modules désactivés

Le système exclut désormais les fichiers CSS liés aux modules désactivés des fichiers de sortie CSS finaux, en veillant à ce que les styles inutiles ne soient pas chargés. Auparavant, le code CSS relatif aux modules désactivés était inclus dans les fichiers de sortie CSS finaux, ce qui entraînait le chargement de styles supplémentaires et inutiles.

_AC-1306 - [Problème GitHub](https://github.com/magento/magento2/issues/24666) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/32922)_

#### Comportement incohérent dans le tri « en rupture de stock » avec le seuil minimum de stock

Le système trie désormais correctement les produits du catalogue en fonction des niveaux de stock, en respectant le seuil minimal de stock défini et en déplaçant régulièrement les articles en rupture de stock au bas de la liste. Auparavant, le comportement du tri était incohérent, les articles n’apparaissant pas toujours dans le bon ordre en fonction de leur niveau de stock, et les modifications du tri pouvaient se produire de manière imprévisible après l’enregistrement, l’actualisation ou la modification de la hiérarchie des catégories.

_AC-13459 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/47b448e2)_

#### Suggestion pour l’amélioration des rapports d’erreurs pour les problèmes de chargement de required.js

Cette requête d’extraction améliore le message d’erreur lorsque la configuration requise ne parvient pas à charger un composant.

_AC-13472 - [Problème GitHub](https://github.com/magento/magento2/issues/36761) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38971)_

#### Erreurs d&#39;obsolescence de PHP 8.4 provoquant des échecs de build dans 2.4-development

_AC-14004 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/1da9ba6f)_

#### [Problème] Ne chargez pas le contexte du bloc principal sur frontend.

Le système garantit désormais que le contexte du bloc principal n’est pas chargé sur le serveur frontal, ce qui empêche la création de sessions principales inutiles et de verrous de session potentiels. Auparavant, le système chargeait incorrectement le contexte du bloc principal sur le front-end, ce qui entraînait la création de sessions principales et de verrous de session potentiels.

_AC-9007 - [Problème GitHub](https://github.com/magento/magento2/issues/37617) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/36368)_

#### [Problème] Supprimer les scripts inutiles Résumé de la révision

Le système optimise désormais le temps de chargement des pages en supprimant les scripts JavaScript inutiles de la section d’évaluation, au lieu d’utiliser des styles CSS intégrés pour un code plus efficace et plus lisible. Auparavant, l’utilisation de scripts JavaScript pour la section d’évaluation pouvait potentiellement ralentir le temps de chargement des pages.

_AC-9168 - [Problème GitHub](https://github.com/magento/magento2/issues/37776) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/34643)_

#### Exception lors de la vérification du solde d&#39;une carte cadeau lorsque Recaptcha est activé

Les utilisateurs pourront récupérer le solde de la carte cadeau dans l’écran d’affichage et de modification du panier. Auparavant, ces détails n’étaient pas affichés lorsque reCAPTCHA était activé.

_ACP2E-2529 - [contribution du code GitHub](https://github.com/magento/magento2-page-builder/commit/4a2795ea)_

#### [CLARIFICATION] Demande de fonctionnalité Conformité ADA

Le système assure désormais la conformité ADA en supprimant les propriétés CSS non prises en charge et en les remplaçant par des propriétés prises en charge dans le fichier print.css. Auparavant, l’utilisation de propriétés CSS non prises en charge entraînait des problèmes de compatibilité avec les navigateurs.

_ACP2E-2729 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/57a32313)_

#### Code de bibliothèque [Cloud] Confusion dans effect-drop.js sur AC 2.4.4-p8

Le système met désormais correctement en œuvre la bibliothèque effect-drop.js , assurant ainsi le bon fonctionnement des effets de l’interface utilisateur jQuery. Auparavant, la bibliothèque effect-drop.js était remplacée par erreur par la bibliothèque effect-clip.js, ce qui entraînait des problèmes potentiels avec les effets de l’interface utilisateur jQuery.

_ACP2E-3061 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/35b1b1da)_

#### En-tête de site | Caractères spéciaux Rompant la section Bienvenue du client

Après la correction, les caractères spéciaux s’affichent correctement dans la section d’accueil du client.

_ACP2E-3367 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/1366ae5e)_

#### Échec de la modification du segment client avec la période

Il est possible d’enregistrer le segment client avec la condition de période, lorsqu’une seule des dates a été modifiée.

_ACP2E-3561 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/a52ff98f)_
