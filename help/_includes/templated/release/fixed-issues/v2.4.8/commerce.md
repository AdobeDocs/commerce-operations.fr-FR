---
source-git-commit: 3f6776e5dbbf167bbb7b4f831f9a7d4cfbfc0b74
workflow-type: tm+mt
source-wordcount: '28398'
ht-degree: 0%

---
# Problèmes résolus dans Adobe Commerce (v2.4.8)

## Correction de problèmes dans la version v2.4.8

Nous avons corrigé 582 problèmes dans le code principal d’Adobe Commerce 2.4.8. Un sous-ensemble des problèmes résolus inclus dans cette version est décrit ci-dessous.

### API

* _AC-10042_ : l’API REST /V1/transactions renvoie une erreur lorsque parent_txn_id = txn_id
   * _Remarque de correction_ : le système gère désormais correctement les transactions de concept parent et enfant où l’ID de transaction parent est identique à l’ID de transaction, ce qui empêche une boucle infinie lors de l’interrogation du point d’entrée /V1/transactions de l’API REST. Auparavant, ce scénario entraînait une erreur fatale en raison du dépassement du temps d’exécution maximal.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1bafc571>
* _AC-11878_ : problème de type [Graphql] dans 2.4.7
   * _Remarque de correction_ : le système gère désormais correctement les valeurs entières dans la fonction GetCustomSelectedOptionAttributes lors de l’exécution d’une requête GraphQL, ce qui empêche toute erreur liée au type. Auparavant, le lancement d’une requête GraphQL qui utilisait GetCustomSelectedOptionAttributes avec un argument entier entraînait une erreur de type.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38662>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38663>
* _AC-3223_ : caractères spéciaux dans la catégorie url_key (lorsqu’ils sont créés via l’API REST)
   * _Remarque sur la correction_ : Dans category_url_key, le caractère spécial n&#39;est pas présent après la correction. Il est affiché dans category_url_key
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/35577>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c699c206>
* _ACP2E-2703_ : API REST affichant les commandes provenant d’un autre site web. 
   * _Remarque de correction_ : le système prend désormais en charge l’accès autorisé de la portée pour les jetons d’administration de l’API REST et les points d’entrée Magento_Sales, en veillant à ce que l’API REST affiche uniquement les commandes auxquelles l’administrateur a accès. Auparavant, l’API REST affichait les commandes de tous les sites web, quel que soit le site web affecté à l’utilisateur administrateur.
* _ACP2E-2755_ : problème avec l’api rest après l’activation de 2FA Duo
   * _Remarque de correction_ : 2FA avec option de sécurité Duo génère désormais la signature correcte pour l’API Rest
   * _Contribution du code GitHub_ : <https://github.com/magento/security-package/commit/412fa642>
* _ACP2E-2927_ : [API REST] : l’option Utiliser la valeur par défaut dans la vue du magasin ne reste pas cochée après l’ajout de configurations pour un produit configurable
   * _Remarque de correction_ : le problème a été résolu en veillant à ce que les entrées de base de données soient correctes pour les options personnalisables d’un magasin autre que celui par défaut. La case à cocher du magasin personnalisé dans la section « Admin > Catalogue > Modification de produit > Options personnalisables » n’était auparavant pas cochée en raison d’entrées de base de données inexactes, même si le titre de l’option du magasin personnalisé restait identique au magasin par défaut.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-2969_ : l’API REST ne peut pas effectuer de requêtes avec une barre oblique (/) dans le SKU lors de l’utilisation d’Oauth1
   * _Remarque sur la correction_ : avant la correction, vous ne pouviez pas effectuer d’appel API réussi pour un produit dont le SKU contenait le caractère « / ». Désormais, vous pouvez émettre une requête d’obtention d’API réussie pour les détails du produit, même si son SKU comporte une barre oblique.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3079_ : échec de la mise à jour de l’adresse du client lors de la mise à jour via l’API REST si « validateDefaultAddress » est activé
   * _Remarque de correction_ : le point d’entrée de l’API fonctionne désormais comme prévu une fois le problème lié à la clé d’ID manquante dans la payload de l’API résolu.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3091_ : [Cloud] création du groupe de prix de site web dupliqué dans le groupe de clients Prix de niveau Api.
   * _Remarque de correction_ : l’API Tier Price Rest ne permet plus de créer le groupe de prix de site web dupliqué.
Auparavant, il était possible de créer le groupe de clients de prix de groupe de sites Web en double dans l’Api Prix de niveau qui ne réussissait pas la validation dans Admin lors de l’enregistrement du produit.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3130_ : impossible d&#39;ajouter un commentaire de commande avec le statut via l&#39;API REST
   * _Correction de la note_ : le problème a été résolu en autorisant la modification du statut de commande s’il s’agit de l’état actuel uniquement. Auparavant, il ne respectait pas l’état de la commande et n’empêchait aucune modification de l’état de la commande, même s’il provenait du même état.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3236_ : l’opération asynchrone échoue lorsque le SKU est absent de la payload
   * _Remarque de correction_ : les opérations asynchrones et de synchronisation ont précédemment échoué en raison d’erreurs d’enregistrement du produit si le SKU est absent de la payload. Après le correctif, les opérations de l’API REST d’enregistrement du produit asynchrone et synchrone échouent avec le message d’exception correspondant.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3376_ : [CLOUD] impossible de mettre à jour les prix de base à l’aide de l’API REST (la valeur de « value_id » dans « catalog_product_entity_decimal » n’est pas incrémentée correctement.)
   * _Remarque sur la correction_ : auparavant, lorsque l’api rest /rest/default/V1/products/base-prices était appelée, l’ID d’incrément était augmenté par erreur, laissant un écart entre les valeurs. Après la correction, l’ID d’incrément est augmenté comme prévu, de manière incrémentielle. La plage de champs value_id a également été augmentée.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3460_ : les articles de commande ne sont pas visibles dans les e-mails de note de crédit pour l’API POST V1/order/ :orderId/refund
   * _Remarque du correctif_ : Auparavant, avant ce correctif, lorsqu’un client créait une note de crédit à partir d’une demande d’API send_email notifiant, elle ne contenait pas la grille de détails du produit. Après cette correction, le client envoie une demande d’API de note de crédit et trouvera les détails de l’article de produit apparaissant dans l’e-mail.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3486_ : les valeurs par défaut ne sont pas définies pour les attributs de date et d’heure avec les produits RestAPI
   * _Correction d’une remarque_ : les valeurs par défaut sont désormais correctement définies pour les attributs de date et de date et d’heure via RestAPI
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1984c61c>

### API, panier et passage en caisse

* _ACP2E-3343_ : Critique Erreur 500 : Magento\Framework\WebAPI\Exception liée à l’acceptation de l’en-tête HTTP
   * _Remarque correctif_ : Après la correction, il n’y a aucun problème avec la spécification de l’en-tête « Accept ».
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/1366ae5e>

### API, GraphQL

* _ACP2E-3348_ : aucune GraphQl disponible pour l’abonnement aux mises à jour des Points de récompense pour le client
   * _Remarque sur la correction_ : auparavant, l’attribut client reward_warning_notification ne pouvait pas être mis à jour par le biais de la mutation GraphQL et de l’appel de l’API Rest. Peut désormais être mis à jour de la même manière que l’attribut client reward_update_notification.

### API, GraphQL, taxe

* _AC-12060_ : Luma (API REST) et Graphql ne calculent pas les taxes lorsque seul le code postal est fourni.
   * _Remarque correctif_ : Le système calcule désormais correctement les taxes lorsque seul un code postal est fourni, ce qui garantit des estimations fiscales précises pour Luma (API REST) et GraphQL. Auparavant, seules les estimations d’expédition étaient calculées et les taxes n’étaient pas incluses lorsque seul un code postal était fourni.

### Compte

* _AC-10782_ : le formulaire d’adresse du client autorise le code aléatoire dans les champs de nom
   * _Remarque de correction_ : le système valide désormais l’entrée dans les champs Prénom et Nom du formulaire d’adresse du client, empêchant l’utilisation de code aléatoire. Auparavant, le système permettait d’utiliser du code aléatoire dans ces champs sans générer d’erreur.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38331>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38345>
* _AC-10886_ : mise à jour du mot de passe de l’administrateur.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38352>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/4bca5dfe>
* _AC-10990_ : mon compte ajoute une adresse crash lors de l’enregistrement
   * _Correction de la remarque_ : le système enregistre désormais correctement les adresses client même lorsque le champ Région n’est pas affiché, ce qui empêche un blocage pendant le processus d’enregistrement. Auparavant, toute tentative d’ajout ou de modification d’une adresse sans champ de région affiché entraînait une erreur d’exception.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38406>
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/pull/38407>
* _AC-11718_ : Boucle de redirection lorsque l’URL est en majuscule
   * _Remarque correctif_ : Le système convertit désormais automatiquement les caractères majuscules dans les URL en minuscules, empêchant ainsi une boucle de redirection lors de l’accès à la page d’accueil. Auparavant, la présence de caractères majuscules dans l’URL de base sécurisée entraînait une boucle de redirection continue lors de la tentative d’accès à la page d’accueil.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38538>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38539>
* _AC-11755_ : middlename( s) non enregistré pour les comptes invités
   * _Correction de la remarque_ : le système enregistre désormais correctement le deuxième prénom pour les comptes invités lors du passage en caisse, ce qui le rend accessible dans le modèle de courrier électronique. Auparavant, le deuxième prénom n’était pas enregistré dans le tableau des devis et n’était pas accessible dans le modèle d’e-mail pour les comptes invités.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38593>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/39067>
* _AC-11919_ : administrateur : boutons d’actions de page flottant à gauche et non à droite
   * _Remarque à propos de la correction_ : le système aligne désormais correctement les boutons d’actions de page sur le côté droit de l’en-tête autocollant dans le panneau d’administration, ce qui améliore l’aspect professionnel. Auparavant, ces boutons flottaient incorrectement sur le côté gauche de l’en-tête persistant.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38701>
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/44cef3a9>
* _AC-11999_ : Erreur:di:Dev Info dans Magento 2.4.7
   * _Remarque correctif_ : Le système affiche désormais correctement les paramètres du constructeur lors de l’exécution de la commande dev:di:info, empêchant ainsi toute erreur de se produire. Auparavant, l’exécution de cette commande entraînait une erreur due à une incompatibilité de type dans l’argument.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38740>
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-13000_ : la case à cocher Se connecter en tant que client ne peut pas être traduite
   * _Remarque à corriger_ : le système permet désormais de définir les champs « Case à cocher Se connecter en tant que client opt-in » et « Infobulle de la case à cocher Se connecter en tant que client » sur la portée « Affichage de la boutique », ce qui permet d’obtenir des traductions pour différents affichages de la boutique. Auparavant, ces champs n’étaient définis que sur la portée « Site web », ce qui empêchait les traductions pour les vues de magasin individuelles.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/32329>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/32359>
* _AC-14299_ : la page d’accueil de l’interface utilisateur front-end dans la liste déroulante de mon profil n’est pas là.(par intermittence)
* _AC-6071_ : le client est connecté mais affiche une erreur 404 en mode frontal.
   * _Remarque à propos de la correction_ : la page du tableau de bord client du storefront se charge désormais comme prévu lorsqu’un client se connecte. Auparavant, les clients pouvaient se connecter, mais cette page affichait une erreur 404. [GitHub-35838](https://github.com/magento/magento2/issues/35838)
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/35838>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/36263>
* _ACP2E-2791_ : impossible d’enregistrer les informations d’attribut du client dans la section Modifier le client d’administration ;
   * _Remarque à propos de la correction_ : l’ID de magasin du client est désormais correctement implémenté par portée de site web pour le formulaire de modification du client administrateur.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/488c1034>
* _ACP2E-3115_ : [Cloud] Impossible de créer un client via l’API lorsque la vente privée est activée
   * _Remarque de correction_ : désormais, le client peut être créé par un utilisateur administrateur authentifié, ainsi qu’avec un jeton d’intégration authentifié via l’api REST lorsque la restriction de site web est activée.
* _ACP2E-3329_ : après s’être connecté, les produits ajoutés à la liste de comparaison en tant qu’utilisateur invité ne sont pas visibles.
   * _Remarque sur la correction_ : les produits qui ont été ajoutés à la liste de comparaison des produits avant de se connecter en tant que client sont désormais conservés après la connexion.
Auparavant, après s’être connecté, les produits ajoutés à la liste de comparaison en tant qu’utilisateur invité n’étaient pas visibles.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3433_ : la configuration Autoriser les pays entraîne des problèmes dans les configurations d’adresses client
   * _Remarque à propos de la correction_ : la sélection de la configuration Autoriser les pays n’influence pas les pays affichés pour en dehors de la portée donnée. Auparavant, la configuration Autoriser les pays avait influencé l’attribut d’adresse du client en dehors de la portée donnée
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3445_ : le registre des cadeaux partagés affiche la date de l&#39;événement comme étant 1 jour plus tôt
   * _Corriger la note_ : la date d&#39;enregistrement du cadeau s&#39;affiche correctement maintenant sur Storefront
* _ACP2E-3501_ : VAPT : erreur de logique commerciale - date future comme date de naissance du client
   * _Correction de la note_ : la date de naissance du client ne peut pas être définie plus tard qu&#39;aujourd&#39;hui
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d4de4726>

### Compte, API, GraphQL

* _ACP2E-3246_ : API Client - Le Nombre D’Échecs De Connexion Ne Peut Pas Être Réinitialisé À 0 Après Une Connexion Réussie
   * _Remarque de correction_ : le numéro d’échec est désormais réinitialisé sur zéro dans la table des entités client après la connexion réussie du client via les points d’entrée de l’API.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ec7e32a9>

### Compte, interface utilisateur d’administration, B2B

* _ACP2E-3038_ : les utilisateurs administrateurs restreints ne peuvent pas toujours voir les catalogues partagés personnalisés
   * _Remarque de correction_ : les utilisateurs administrateurs restreints peuvent désormais afficher et gérer de manière cohérente les clients et tous les catalogues partagés auxquels les produits sont affectés, à condition qu’ils aient accès à la boutique spécifique. Auparavant, un utilisateur administrateur restreint ayant accès à une boutique particulière ne pouvait pas toujours voir tous les catalogues partagés auxquels les produits étaient affectés ou pouvait voir les clients qui ne pouvaient pas effectuer d’enregistrement, ce qui entraînait des incohérences dans le système.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/7377de59>

### Compte, panier et passage en caisse

* _AC-2341_ : l’attribut d’adresse client personnalisé « sélectionner » n’est pas rendu pour la nouvelle adresse client
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/34950>

### Interface utilisateur d’administration

* _AC-10705_ : [Problème] ajoutez une vérification des autorisations pour le bouton de données « recharger les données »
   * _Remarque sur la correction_ : le système inclut désormais une vérification des autorisations pour le bouton « Recharger les données », afin de s’assurer qu’elles ne s’affichent et ne sont accessibles qu’aux utilisateurs disposant des autorisations appropriées. Auparavant, le bouton « Recharger les données » était visible et cliquable par tous les utilisateurs et utilisatrices, ce qui entraînait l’affichage d’une page « non autorisée » lorsque les utilisateurs et utilisatrices cliquaient dessus sans les autorisations nécessaires.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38283>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38279>
* _AC-11427_ : [problème] libellés incohérents pour les attributs dans les règles marketing
   * _Correction de la note_ : le système remplit désormais correctement les libellés de manière cohérente pour les options de catégorie et d’attribut dans la règle de prix du panier
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/31232>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/31231>
* _AC-11588_ : la validation des données a réussi et le bouton Importer est présent lors de l’importation de produits avec le comportement Remplacer
   * _Remarque sur la correction_ : le système valide désormais correctement les données et masque le bouton « Importer » pendant le processus d’importation du produit avec le comportement « Remplacer », empêchant tout remplacement involontaire des données. Auparavant, le système ne validait pas correctement les données et affichait le bouton « Importer », ce qui entraînait des incohérences potentielles des données.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/0574ac23>
* _AC-12167_ : [Bug] Magento 2.4.7 n’autorise pas les photos de produit avec extension de fichier majuscule.
   * _Remarque de correction_ : le système accepte désormais les chargements d’images de produit avec des extensions de fichier de lettre majuscule, assurant ainsi un processus de création de produit fluide. Auparavant, les chargements d’images avec des extensions de fichier en majuscules étaient refusés, ce qui forçait les utilisateurs à modifier l’extension de fichier en minuscules.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38831>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-12319_ : liste déroulante masquée dans les grilles avec l’action de sélection (par exemple, Contenu > Éléments > Pages)
   * _Correction de la note_ : désormais, le système a été corrigé dans toutes les listes déroulantes similaires pour toutes les grilles.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38891>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/39371>
* _AC-13131_ : [Problème] Avertissement de correctif : clé de tableau non définie « filtres »
   * _Remarque à propos de la correction_ : le système gère désormais les scénarios dans lesquels un nouvel utilisateur n’a pas encore interagi avec les signets, empêchant la journalisation d’un avertissement de « filtres » de clé de tableau non défini. Auparavant, cet avertissement était consigné lorsqu’un nouvel utilisateur n’avait pas interagi avec des signets.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39013>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38996>
* _AC-13529_ : Le fichier CSV d&#39;importation de produit avec des caractères spéciaux échoue en raison de changements de code dans le fichier Validate.php
   * _Remarque de correction_ : le système valide et importe désormais correctement les fichiers CSV de produit contenant des caractères spéciaux, ce qui permet de réussir le transfert des données. Auparavant, toute tentative d’importation d’un fichier CSV de produit avec des caractères spéciaux entraînait une erreur, empêchant le processus d’importation.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-13767_ : lorsque le nombre maximal de demandes de réinitialisation de mot de passe est supérieur à 0, par exemple : 3 , les messages d’erreur « Dépassement de limite » sont envoyés avant d’atteindre la limite, c’est-à-dire à partir de la deuxième fois
* _AC-13768_ : bien que le nombre maximal de demandes de réinitialisation de mot de passe soit défini sur 0 ( désactivé) , « Les messages d’erreur de dépassement de limite sont envoyés à partir de la 2e fois »
* _AC-13850_ : il n’y a pas d’astérisque rouge pour le champ du numéro de téléphone obligatoire
   * _Correction de la note_ : l’astérisque rouge précédent ne s’affichait pas pour le numéro de téléphone, mais  le numéro de téléphone était obligatoire. Qui est maintenant fixe astérisque rouge peut être vu sur le numéro de téléphone comme un champ obligatoire.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c699c206>
* _AC-14300_ : dans l’administration, il n’est pas possible de cliquer sur le bouton Envoyer la commande lorsque nous tentons de le réorganiser. (par intermittence)
* _AC-6975_ : [Problème] Définissez le mode d’indexeur par défaut sur « schedule »
   * _Remarque sur la correction_ : tous les nouveaux indexeurs sont configurés par défaut en mode **[!UICONTROL Update by Schedule]**.  Auparavant, le mode par défaut était **[!UICONTROL Update on Save]**. Les indexeurs existants ne sont pas affectés. [GitHub-36419](https://github.com/magento/magento2/issues/36419)
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/36419>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/0b410856>
* _AC-7700_ : [Problème] Déposez les tables de journal des modifications de l&#39;indexeur sur le désabonnement mview
   * _Remarque de correction_ : le système supprime désormais automatiquement les tables de journaux des modifications inutilisées lorsqu&#39;un index passe de « mise à jour selon le calendrier » à « mise à jour selon l&#39;enregistrement », marquant l&#39;index comme non valide pour s&#39;assurer qu&#39;aucune entrée n&#39;est manquée. Auparavant, le fait de passer un index à « mettre à jour lors de l&#39;enregistrement » laissait des tables de journaux des modifications inutilisées dans le système et marquait tous les index modifiés comme « valides ».
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/29789>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/25859>
* _AC-7962_ : Aucun lien vers l&#39;expédition lors des paiements en caisse en vue téléphone mobile
   * _Correction de la note_ : le système garantit désormais que les titres/liens de passage en caisse « Expédition » et « Révision et paiements » sont toujours visibles en haut de la page en mode mobile, ce qui permet aux utilisateurs de naviguer facilement entre les étapes et d’effectuer les corrections nécessaires. Auparavant, ces titres/liens étaient masqués en mode mobile, ce qui rendait difficile pour les utilisateurs de connaître l’étape en cours ou de revenir aux étapes précédentes.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/36856>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/36982>
* _AC-8109_ : les commentaires d&#39;expédition de requête de commandes client created_at sont renvoyés dans un fuseau horaire +0 qui n&#39;est pas dans le fuseau horaire configuré du magasin
   * _Correction de note_ : le système affiche désormais correctement le champ &#39;created_at&#39; à partir des commentaires d&#39;expédition dans le fuseau horaire configuré du client lors de l&#39;utilisation de la requête Commandes client. Auparavant, le champ « created_at » s’affichait dans le fuseau horaire +0, quel que soit le fuseau horaire configuré du client.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/36947>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37642>
* _AC-9843_ : i18n:collect-phrases rompt l’intégrité des traductions
   * _Correction de la remarque_ : la commande `bin/magento i18n:collect-phrases -o` collecte et ajoute désormais correctement les nouvelles expressions des fichiers JavaScript et .phtml, en veillant à ce que les traductions soient reflétées avec précision dans le fichier de traduction. Auparavant, le système n’incluait pas les expressions de traduction multiligne des fichiers JavaScript et les expressions des fichiers .phtml dans le fichier de traduction, ce qui entraînait des traductions incomplètes ou incorrectes.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2687_ : problème d&#39;autorisation d&#39;accès au bloc dynamique
   * _Remarque de correction_ : auparavant, pour l’administration restreinte, l’ajout d’un nouveau bloc dynamique générait une erreur. Après l’implémentation de ce correctif, l’administrateur restreint peut ajouter le bloc dynamique et le modifier sans erreur
* _ACP2E-2787_ : l&#39;apostrophe dans le nom d&#39;affichage du magasin est remplacée par &#39;
   * _Correction d’une note_ : les filtres de vue de magasin de la grille affichent désormais correctement les apostrophes
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38395>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2847_ : le chargement de Favicon ne parvient pas à valider les fichiers .ico
   * _Remarque sur la correction_ : l’erreur de validation du fichier a été mise à jour sur « Échec de la validation du fichier ». Vérifiez les paramètres de traitement des images dans la configuration de la boutique. » Auparavant, il s’agissait simplement de « Échec de la validation du fichier ».
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2957_ : la galerie dans PageBuilder affiche l’ancienne miniature d’image au lieu de l’image nouvellement chargée
   * _Remarque de correction_ : régénérez les aperçus d’image pour les images supprimées et rechargées avec le même nom via la galerie multimédia dans le contenu du générateur de page.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2-page-builder/commit/60140cd2>, <https://github.com/magento/magento2/commit/001e5188>
* _ACP2E-2978_ : l&#39;enregistrement d&#39;un produit par un utilisateur administrateur avec une étendue de rôle différente remplace/supprime les informations existantes sur les produits associés dans le produit
   * _Remarque sur la correction_ : auparavant, avant la correction, les produits associés étaient réinitialisés et étaient vides lorsque l’utilisateur secondaire en charge de l’administration cliquait sur le bouton d’enregistrement sans modifier les produits associés. Après ce correctif, l’utilisateur administrateur secondaire clique sur le bouton d’enregistrement et le produit ne se réinitialise pas et est enregistré avec succès.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3033_ : impossible d&#39;exporter plus de 200 commandes
   * _Remarque de correction_ : les limites du serveur pour la taille de requête des identifiants sélectionnés précédemment envoyés ont été négligées en modifiant la requête HTTP de GET à POST afin de résoudre le problème. Auparavant, en raison des limitations du serveur pour la taille de requête GET, le problème était rencontré.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3037_ : message de validation de la page de passage en caisse incorrect.
   * _Correction de la note_ : si un champ obligatoire reste vide, tel que « adresse », la validation côté serveur n’affichera pas le message. La validation côté client garantit que la notification d’erreur de champ obligatoire s’affiche, indiquant « Ceci est un champ obligatoire ». Auparavant, le message « adresse requise » s’affichait si un champ obligatoire était laissé vide, en plus du message de validation côté client.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3125_ : problème de modèle de réinitialisation de mot de passe avec l’utilisateur administrateur
   * _Remarque corrective_ : Le problème a été résolu en utilisant la clé correcte, qui inclut maintenant le nom d’utilisateur admin dans le modèle d’e-mail et complète correctement l’objet. Auparavant, le problème provenait d’une clé obsolète qui était utilisée.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3149_ : URL du segment de clients avec double barre oblique
   * _Remarque correctif_ : Les barres obliques doubles n’apparaissent pas dans l’URL lorsque l’utilisateur clique sur « Réinitialiser le filtre » dans la grille.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3171_ : COD n’est pas disponible pour les pays spécifiques autorisés
   * _Note de correctif_ : Maintenant, le paiement à la livraison est disponible pour les pays spécifiques autorisés chaque fois que cela est nécessaire et AC-3216 fonctionne comme prévu.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3178_ : impossible de mettre à jour le statut de la commande créée personnalisée
   * _Corriger la note_ : &#39;
Nous pouvons désormais mettre à jour les statuts de commande personnalisés, alors qu’auparavant le statut ne pouvait être modifié que si le statut actuel était soit « traitement » soit « fraude ».
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38659>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3294_ : l&#39;état de l&#39;adresse de livraison n&#39;est pas mis à jour automatiquement
   * _Remarque sur la correction_ : avant la correction, la région de l’adresse d’expédition (ou l’ID de région) n’était pas synchronisée avec les informations de facturation de l’adresse. Désormais, l’adresse de livraison région et l’identifiant de région sont correctement mis à jour lorsque les informations d’adresse de facturation sont modifiées.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3364_ : le bouton Réinitialiser ne fonctionne pas sur Ajouter/Modifier l’utilisateur administrateur
   * _Correction de la note_ : auparavant, le bouton Réinitialiser ne fonctionnait pas sur la page Ajouter/modifier un utilisateur administrateur. Désormais, dans le panneau d’administration sous Système -> Autorisations -> Tous les utilisateurs, le bouton Réinitialiser fonctionnera correctement sur la page Ajouter/modifier un utilisateur administrateur .
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3373_ : détection incorrecte du routage de l’URL d’administration Magento et erreurs CORS
   * _Remarque sur la correction_ : après la correction, si le domaine d’administration personnalisé est un sous-domaine du domaine principal, l’administrateur est accessible uniquement à partir du sous-domaine configuré.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37663>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3392_ : validation non effectuée de la « quantité maximale autorisée dans le panier »
   * _Correction de note_ : auparavant, lorsque nous mettions `Maximum Qty Allowed in Shopping Cart` vide, aucune exception n’était générée, bien qu’une valeur vide ne soit pas acceptée ici. Une fois que ce correctif est appliqué, le fait de placer une chaîne vide génère des exceptions et ne permet pas d’enregistrer le produit.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3408_ : [problème d’interface utilisateur de l’aperçu de Pagebuilder] les boutons de la colonne Page Builder ne s’alignent pas correctement
   * _Correction de la note_ : les boutons des colonnes du Générateur de page sont désormais correctement alignés. Auparavant, ils n’étaient pas alignés correctement dans les colonnes du Page Builder.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2-page-builder/commit/1a52ef4c>
* _ACP2E-3431_ : le rapport Produits commandés n&#39;est pas exporté. Erreur 404 à la place.
   * _Remarque sur la correction_ : l’exportation du rapport Produits commandés au format CSV et XML fonctionne désormais comme prévu
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3457_ : erreur JS TinyMCE dans la console après l’activation de la minification JS avec le mode de production
   * _Remarque de correction_ : auparavant, l’activation de la minimisation JavaScript en mode production dans le panneau d’administration entraînait l’affichage d’erreurs JavaScript liées à TinyMCE 6 dans la console du navigateur, ce qui affectait les fonctionnalités et l’expérience utilisateur. Maintenant, ce problème a été résolu, en veillant à ce que TinyMCE 6 fonctionne correctement sans générer d’erreurs, même lorsque la minimisation JS est activée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3459_ : demande de modifications supplémentaires pour terminer le correctif ACP2E-3375
   * _Corriger la note_ : &#39;-
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3503_ : activation automatique des nouvelles autorisations ACL
   * _Remarque de correction_ : les nouvelles autorisations ajoutées aux modules personnalisés n’accorderont plus automatiquement l’accès à tous les rôles utilisateur existants, sauf si elles sont configurées explicitement.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3509_ : le rapport d&#39;utilisateur du journal des actions d&#39;administration n&#39;affiche pas les détails de adminhtml_user_delete
   * _Remarque de correction_ : l’adminhtml_user_delete consigne désormais correctement les détails importants. Auparavant, les journaux n’étaient pas générés pour les suppressions d’utilisateurs.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/4de008a9>
* _ACP2E-3536_ : Règle de panier avec condition d’expédition ne s’appliquant pas lors de la passation d’une commande auprès de l’administrateur
   * _Remarque correctif_ : Auparavant, si la règle de prix du panier avait une remise sur le mode d’expédition avec le coupon, elle ne pouvait pas être appliquée via l’interface utilisateur d’administration. Une fois ce correctif appliqué, la remise de la règle de prix du panier avec un coupon pour une méthode d’expédition spécifique sera appliquée correctement à partir de l’interface utilisateur d’administration.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a52ff98f>, <https://github.com/magento/inventory/commit/11ce816b>
* _ACP2E-3559_ : le code HEX [FRESH] ne se met pas correctement à jour dans l’échantillon
   * _Remarque de correction_ : le code HEX saisi manuellement par l’utilisateur dans le sélecteur de couleurs de l’échantillon visuel n’est plus modifié par le système. Auparavant, certains codes HEX subissaient de légers ajustements en raison d’erreurs de conversion entre les modèles de couleurs.
   * _Contribution_ au code GitHub : <https://github.com/magento/magento2/commit/344fce23>, <https://github.com/magento/inventory/commit/1ef984c0>

### Interface utilisateur d’administration, B2B

* _AC-13628_ : L’en-tête de connexion B2B en tant que client a toujours Magento de marque
   * _Remarque correctif_ : plus tôt, l’en-tête de la vitrine affiche « Vous êtes maintenant connecté comme &lt;customer name=&quot;&quot;> sur &lt;store name=&quot;&quot;>» avec Magento marque. &lt;/store>&lt;/customer> Ce qui est maintenant corrigé et l’en-tête s’affiche avec la marque ADOBE.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/96dec499>

### IU d’administration, catalogue

* _ACP2E-2708_ : impossible de modifier les positions de la catégorie produits sur le site Web autorisé en tant qu’utilisateur administrateur restreint
   * _Remarque de correction_ : permet à un utilisateur administrateur restreint d’ajouter et de trier des produits sous une catégorie contenue dans la catégorie racine affectée sous un site web restreint.

### Interface utilisateur d’administration, Modes de paiement, Commande

* _AC-13520_ : Autorisation de transaction non affichée dans l&#39;onglet Transaction après la commande du bouton intelligent PayPal
   * _Corriger la note_ : Le système affiche désormais correctement l&#39;autorisation de transaction dans l&#39;onglet Transaction après qu&#39;une commande a été passée à l&#39;aide du bouton intelligent PayPal. Auparavant, la transaction d’autorisation n’apparaissait pas dans l’onglet Transaction après avoir cliqué sur le bouton « Autoriser », et aucune nouvelle transaction de type « Autorisation » n’a été créée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/6cfb9b6b>

### IU d’administration, performances

* _ACP2E-3169_ : après la mise à jour vers la version 2.4.5-p8, des erreurs 500 se produisent lors de la création de la commande depuis l’administrateur
   * _Remarque correctif_ : Auparavant, lors de l’activation de la minification HTML, une commande de l’administrateur ne pouvait pas être passée. Désormais, lorsque la minification HTML est activée, la commande de l’administrateur peut être passée avec succès.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/b21e5d91>

### Interface utilisateur d’administration, Expédition

* _ACP2E-2519_ : le nombre de codes coupon n’est pas mis à jour dans le   Colonne « Temps utilisé » de l’onglet Gérer les codes coupon si une commande est passée avec une expédition multiple.
   * _Corriger la note_ : Auparavant, lorsqu&#39;une commande était passée avec une expédition multiple, le nombre de codes de coupon n&#39;était pas mis à jour dans la colonne « Temps utilisé » de l&#39;onglet Gérer les codes de coupon. Désormais, le nombre correct s’affiche à la fois dans le « Temps utilisé », reflétant les valeurs souhaitées avec une expédition multiple.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/4745100c>

### Interface utilisateur d’administration, évaluation et prévisualisation

* _ACP2E-3424_ : [Cloud] la suppression d’un modèle avec des images manquantes entraîne la suppression de médias/pubs
   * _Remarque sur la correction_ : auparavant, si le nom de l’image d’aperçu était manquant pour un modèle pagebuilder, le dossier pub/media était supprimé. Après la correction, seul le modèle est supprimé et l’image d’aperçu, si elle est trouvée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2-page-builder/commit/0986853b>

### Analyses / Rapports

* _AC-9922_ : erreur Google Analytics CSP https://region1.analytics.google.com
   * _Remarque de correction_ : le système autorise désormais correctement les connexions à « https://region1.analytics.google.com&#39; » lorsque Google Analytics est activé, ce qui empêche les erreurs de politique de sécurité du contenu (CSP). Auparavant, l’activation de Google Analytics et l’affichage du site web depuis l’UE entraînaient des erreurs de console CSP en raison d’un refus de connexion à « https://region1.analytics.google.com&#39; ».
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37750>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38991>
* _ACP2E-2570_ : le rapport avancé ne fonctionne pas
   * _Remarque de correction_ : le système prend désormais en charge la génération de fichiers de données de rapports avancés pour les jeux de données très volumineux en chargeant et en écrivant des rapports par lots de 10 000. Auparavant, le module de création de rapports avancés ne pouvait pas générer de fichiers de données pour les jeux de données très volumineux, ce qui provoquait des erreurs « MySQL Server has gone away » lors de l’exécution de la tâche analytics_collect_data cron.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-3080_ : problème de visibilité de la période du rapport Produits commandés par l&#39;administrateur.
   * _Corriger la note_ : l’utilisateur pourra sélectionner n’importe quelle date dans le rapport des produits commandés. Auparavant, après une actualisation du tableau, la sélection de la date « DE » réinitialisait la date « À ».
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3096_ : en-têtes de curl incorrects, newrelic:create:deploy-marker ne fonctionne pas
   * _Remarque de correction_ : le système formate désormais correctement les en-têtes curl, ce qui permet à la commande newrelic:create:deploy-marker de créer un marqueur de déploiement dans New Relic. Auparavant, des en-têtes curl incorrects empêchaient la création d’un marqueur de déploiement dans New Relic.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37641>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3146_ : événement addToCart manquant dans la couche de données pour le produit configurable avec option personnalisée
   * _Remarque de correction_ : auparavant, l’événement addToCart n’était pas déclenché pour les produits configurables. Désormais, l’événement est correctement ajouté à la variable dataLayer de GMT.
* _ACP2E-3183_ : la surveillance du navigateur NewRelic par le script inlineJS provoque des erreurs CSP
   * _Remarque sur la correction_ : les scripts de surveillance du navigateur NewRelic sont désormais injectés par l’application au lieu de l’agent APM pour assurer la conformité avec la CSP (Content Security Policy, politique de sécurité du contenu). Auparavant, les scripts de surveillance du navigateur NewRelic injectés par l’agent APM n’étaient pas conformes à la CSP et empêchaient leur exécution.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3189_ : les requêtes INSERT à la table sales_bestsellers_aggregated_daily deviennent lentes sur les projets avec un volume de commandes client important
   * _Correction de note_ : auparavant, le rapport quotidien agrégé des meilleures ventes prenait beaucoup de temps à générer pour un grand volume de commandes passées. Le rapport est maintenant généré en temps voulu.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3276_ : rapports de commande affichant le mauvais symbole de devise
   * _Corriger la note_ : Le symbole de devise pour les montants de commande dans l&#39;état des commandes a été extrait de manière incorrecte de la devise/des options/de la base. Correction de l’utilisation de la devise, des options et de la valeur par défaut pour un compte rendu des performances précis.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3302_ : [Cloud] calculs incorrects dans le rapport d’utilisation des coupons
   * _Corriger la note_ : Le total des ventes dans la grille d&#39;état des coupons est désormais calculé avec précision en incorporant le « Montant de la remise de taxe » et le « Montant de la remise de taxe d&#39;expédition ». Auparavant, ces montants étaient absents du calcul, ce qui entraînait des écarts entre le total des ventes et les données des commandes client.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3339_ : problèmes liés au partage de « &lt;project_id>/var/tmp »
   * _Remarque à propos de la correction_ : les fichiers temporaires Analytics DataExport utiliseront le répertoire tmp du système, qui est plus adapté aux accès fréquents et aux modifications. Pour éviter les collisions si plusieurs instances sont exécutées sur le même serveur, le chemin tmp a été mis à jour pour utiliser l’ID unique d’une instance
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a4cf5e62>

### Analytics/Reporting, B2B

* _ACP2E-2300_ : B2B - le plan du site inclut des produits/catégories non affectés au catalogue partagé
   * _Remarque de correction_ : limitez les catégories et produits générés par le plan de site aux catégories et produits affectés uniquement au catalogue public partagé et/ou à la configuration des autorisations de catégorie de catalogue.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ea79f7dd>

### Analytics/Création de rapports, Cloud

* _ACP2E-3067_ : Magento ignore la plupart des transactions New Relic cron #34108
   * _Correction de la note_ : AC signale correctement les transactions liées aux tâches cron à NewRelic. Auparavant, certaines transactions liées à la tâche cron s’affichaient sous la forme « Autre transaction/Action/inconnu » dans NR
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3187_ : La mesure dans NR peut être trompeuse pour les transactions en arrière-plan - Suivi de ACP2E-3067
   * _Remarque de correction_ : les transactions en arrière-plan (cron) utiliseront le nom de l’application New Relic défini dans les paramètres de configuration
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ec7e32a9>

### B2B

* _AC-13501_ : le package 2.4.8-beta102 Enterprise Edition échoue avec des exceptions d’application.
* _ACP2E-2139_ : les produits affectés au catalogue partagé ne sont pas reflétés sur le front-end lors de l’exécution de l’index partiel
   * _Remarque de correction_ : les produits affectés au catalogue partagé via l’API REST sont désormais immédiatement visibles sur storefront une fois l’indexation partielle terminée. Auparavant, les produits n’étaient visibles qu’après une réindexation complète.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-2873_ : [Cloud] L’affichage des prix dans la version pour mobiles et pour ordinateurs de bureau n’est pas le même que dans « Mes devis »
   * _Corriger la note_ : La ligne Inclure la taxe superflue n&#39;apparaît plus dans le devis négociable lorsque la section du prix total du catalogue est dépensée.
* _ACP2E-3044_ : bordures inutiles sur la section Mes commandes
   * _Remarque sur la correction_ : Auparavant, un conteneur supplémentaire (références de commande) était créé pour appliquer des classes CSS supplémentaires, ce qui entraînait l’apparition de lignes de bordure inutiles sous le numéro de commande dans la section Mes commandes , qui n’est pas visible actuellement.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3247_ : sales_clean_quotes cron supprime les devis de vers commandes fournisseur encore approuvées
   * _Corriger la note_ : les devis utilisés dans les commandes fournisseur ne seront pas supprimés par le traitement cron sales_clean_quotes
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3465_ : le bouton Passer une commande disparaît dans les détails du bon de commande
   * _Corriger la note_ : correction d’un problème en raison duquel le bouton Passer une commande était masqué pour les commandes fournisseur approuvées lorsqu’une variation de produit avait le nombre minimum spécifié dans la carte
* _ACP2E-3474_ : [CLOUD] Aucune entité de ce type avec id = 0 avec le module b2b
   * _Remarque de correction_ : l’utilisateur connecté peut ajouter un produit au panier lorsque les fonctionnalités de catalogue partagé sont activées.
L’ajout précédent du produit au panier entraînait l’erreur « aucune entité de ce type avec l’id = 0 »
* _ACP2E-3562_ : aucun message d&#39;erreur n&#39;est affiché pour nos produits en stock lors de l&#39;ajout en bloc à partir de la liste des demandes d&#39;approvisionnement
   * _Remarque sur la correction_ : avant la correction, un message de réussite s’affichait, quel que soit le nombre de produits qui n’ont pas été ajoutés au panier. Désormais, des messages distincts s’affichent pour les produits qui ont été ajoutés avec succès au panier et pour les produits qui ont échoué.
* _ACP2E-3628_ : problème lié aux mises à jour de SKU après les mises à jour planifiées, entraînant des autorisations de produit incorrectes (-2 Refuser)
   * _Remarque de correction_ : la modification du SKU d’un produit avec les mises à jour planifiées antérieures n’entraîne plus l’inaccessibilité du produit pour les clients du catalogue partagé autorisés à voir le produit.

### B2B, Catalogue

* _ACP2E-2860_ : produits/catégories visibles lors de la réindexation lors de l’utilisation de NoDDL et des autorisations de catégorie
   * _Remarque de correction_ : évitez d’afficher sur les catégories restreintes du storefront et leur contenu lorsque l’indexation des autorisations de catalogue est en cours.

### B2B, Framework

* _AC-9607_ : échec du filtrage de la grille de l’entreprise, puis de la tentative d’exportation CSV de la grille et exception
   * _Remarque de correction_ : le système permet désormais d’exporter au format CSV les données de la grille Entreprises dans le panneau d’administration, même lorsque des filtres tels que « Solde restant à payer » et « Type d’entreprise » sont appliqués. Auparavant, l’application de certains filtres et la tentative d’exportation des données de la grille entraînaient un échec et une exception.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/44cef3a9>

### B2B, GraphQL

* _ACP2E-3391_ : [Cloud] impossible de définir custom_attributes lors de la création de la société via l’appel GraphQL
   * _Remarque sur la correction_ : après la correction, il est possible de définir l’attribut « custom_attributes » pour l’administrateur de la société lors de la création de la société à l’aide d’une requête GraphQL.

### Braintree

* _AC-14293_ : le bouton Passage en caisse express de l’administrateur est désactivé.
* _BUNDLE-3367_ : Payer via LPM
   * _Remarque de correction_ : le système effectue désormais correctement le rendu des modes de paiement locaux (LPM) lors du chargement initial, même lorsque les adresses d’expédition et de facturation d’un client connecté ne correspondent pas, ce qui garantit un processus de paiement fluide. Auparavant, une incohérence entre les adresses d’expédition et de facturation d’un client empêchait le rendu du LPM, ce qui entraînait des perturbations potentielles lors du passage en caisse.
* _BUNDLE-3368_ : configurable avec Virtual comme produit enfant
   * _Correction de note_ : Le système permet désormais des modes de paiement express pour les produits configurables qui ont un produit enfant virtuel, assurant ainsi un processus de paiement fluide. Auparavant, les modes de paiement express n’étaient pas disponibles lorsqu’un produit configurable avec un produit enfant virtuel était ajouté au panier.
* _BUNDLE-3369_ : erreur d’échec de la vérification du CVV
* _BUNDLE-3370_ : Mise en chambre forte via le compte Area Issues 247
   * _Correction de note_ : le système permet désormais aux clients d’enregistrer les informations de leur nouvelle carte ou de leur compte PayPal sur plusieurs sites web sans rencontrer d’erreurs d’autorisation. Auparavant, les clients ne pouvaient pas enregistrer les nouveaux modes de paiement sur différents sites web et un message d’erreur d’autorisation leur était présenté.
* _BUNDLE-3371_ : expédier à une adresse d&#39;un autre pays
   * _Remarque correctif_ : Le système permet désormais de traiter les transactions sans erreur lors de l’expédition à une adresse d’un autre pays, assurant ainsi un processus de paiement fluide. Auparavant, toute tentative d’expédition vers une adresse provenant d’un autre pays entraînait des erreurs de console, même si aucune erreur visible n’était générée sur le serveur frontal.
* _BUNDLE-3372_ : Carte de crédit - Démontage
   * _Remarque sur la correction_ : le système gère désormais correctement la désactivation des composants PayPal Braintree lorsqu’un client revient de la page de paiement à la page d’expédition, ce qui évite les erreurs et garantit que les boutons PayPal Express s’affichent correctement. Auparavant, le fait de revenir à la page d’expédition à partir de la page de paiement entraînait parfois une erreur lors de la tentative de démontage des composants PayPal Braintree.
* _BUNDLE-3373_ : Rappel d&#39;expédition pour PayPal Express
   * _Correction de note_ : le système affiche désormais correctement les modes d’expédition disponibles dans la fenêtre modale PayPal Express, ce qui permet aux clients de sélectionner leur mode d’expédition préféré avant de passer à la page de révision ou de terminer leur transaction. Auparavant, aucune méthode d&#39;expédition n&#39;était disponible dans la fenêtre modale PayPal Express, ce qui obligeait les clients à sélectionner une méthode d&#39;expédition sur une page de révision distincte avant de pouvoir terminer leur transaction.

### Bundle

* _AC-10826_ : le nombre de messages d&#39;erreur de validation de la case à cocher du lot Storefront est supérieur à 1
   * _Correction de la note_ : le système n’affiche désormais qu’un seul message d’erreur de validation lorsque l’utilisateur clique sur le bouton « Ajouter au panier » sans cocher d’option pour un produit groupé. Auparavant, le système affichait plusieurs messages d’erreur de validation pour chaque case à cocher désélectionnée.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/3ea26621>
* _AC-13321_ : Magento Exception levée dans certains cas de test liés à l’ordre
   * _Remarque correctif_ : Le système gère désormais correctement l’étape « sendGuestPaymentInformation » dans divers cas de test, empêchant ainsi Magento exceptions d’être levées. Auparavant, ces exceptions se produisaient en raison d’un mode de paiement nul, ce qui entraînait des échecs dans plusieurs cas de test.

### Panier et passage en caisse

* _AC-10660_ : l’exception n’est pas gérée correctement lors de l’ajout d’un produit au panier dans la page comparer des produits
   * _Remarque de correction_ : le système gère désormais correctement les exceptions lors de l’ajout d’un produit au panier à partir de la page Comparer les produits , affichant un message du gestionnaire de messages dans le contrôleur. Auparavant, une exception entraînait le renvoi d’une page codée en JSON au lieu d’être correctement capturée et gérée.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38200>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38257>, <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10698_ : GTag n&#39;envoie pas les prix et totaux des transactions.
   * _Correction de note_ : le système envoie désormais correctement les prix et totaux des transactions à Google Tag lorsque GTag est activé, assurant ainsi un suivi précis des données d’e-commerce. Auparavant, la devise était incorrectement envoyée dans le cadre des commandes « all », plutôt que d’être associée à la commande individuelle.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37348>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37504>, <https://github.com/magento/magento2/pull/37349>
* _AC-11641_ : [Problème] [Passage en caisse] directives dépendantes mises à jour dans le modèle d’e-mail de paiement ayant échoué
   * _Remarque correctif_ : Le système omet désormais correctement l’adresse de livraison et le mode d’expédition du modèle d’e-mail de paiement échoué pour les produits virtuels, garantissant que seules les informations pertinentes sont incluses dans l’e-mail. Auparavant, l’e-mail de paiement échoué pour les produits virtuels incluait incorrectement l’adresse de livraison et le mode d’expédition.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/32781>
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/pull/32511>
* _AC-11717_ : Magento 2 connexion dans le passage en caisse avec un client existant donne une erreur de console dans le navigateur Firefox
   * _Note corrective_ : Le système permet maintenant aux utilisateurs de se connecter pendant le processus de paiement sans rencontrer d’erreurs de console dans le navigateur Firefox. Auparavant, toute tentative de connexion en tant que client existant lors du passage en caisse entraînait une erreur de console dans Firefox.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38557>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/39509>
* _AC-11876_ : [Problème] régression des règles de vente dans 2.4.7
   * _Remarque correctif_ : Le système valide désormais correctement les règles de vente, empêchant l’application d’un code de coupon à un panier lorsque l’état du produit ne correspond à aucun nom de produit. Auparavant, une règle de vente pouvait être appliquée et une remise était accordée sur le montant des frais d’expédition, même lorsque l’état du produit ne correspondait à aucun nom de produit.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38671>
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/0574ac23>
* _AC-11914_ : [Problème] Règle de vente Calcul fixe du panier : montant de remise incorrect
   * _Remarque correctif_ : Le système calcule désormais correctement le montant de la remise pour les règles de vente avec des montants fixes de panier, garantissant ainsi que des remises précises sont appliquées indépendamment des modifications apportées aux articles du panier. Auparavant, le montant de la remise pouvait varier de manière incorrecte lorsque les articles du panier changeaient, ce qui entraînait parfois des remises beaucoup plus importantes que prévu.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38694>
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/581b7ef1>
* _AC-11993_ : [Problème] Le chargeur bloque les modes d’expédition après modification du code postal, règles de validation des tarifs d’expédition
   * _Remarque corrective_ : Le système gère désormais correctement les méthodes d’expédition personnalisées sans règles de validation des tarifs d’expédition, garantissant que le chargeur ne bloque pas les méthodes d’expédition après que le code postal est modifié dans l’adresse de livraison lors du paiement. Auparavant, la modification du code postal dans l’adresse de livraison lors du paiement entraînait le blocage des méthodes d’expédition par le chargeur et ne disparaissait pas lorsque des méthodes d’expédition personnalisées sans règles de validation des frais d’expédition étaient utilisées.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38742>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1bafc571>
* _AC-12170_ : la fonctionnalité de code promotionnel ne fonctionne pas correctement dans la page de passage en caisse de Magento 2.4.7.
   * _Correction de la note_ : le système active désormais le champ d’entrée code de remise/coupon sur la page de passage en caisse pour les produits virtuels et téléchargeables, ce qui permet aux utilisateurs d’appliquer les codes de remise comme prévu. Auparavant, la saisie du code de remise/coupon était désactivée et le texte du titre du bouton affichait « Annuler le coupon », ce qui empêchait les utilisateurs d’appliquer des codes de remise.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38826>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1bafc571>
* _AC-12479_ : la case Termes et conditions n’autorise pas HTML sur storefront
   * _Remarque à propos de la correction_ : le système prend désormais en charge le formatage d’HTML dans la case à cocher « Termes et conditions » du storefront, ce qui permet une personnalisation et une lisibilité améliorées. Auparavant, le texte de la case à cocher s’affichait au format texte brut, ignorant les balises HTML utilisées.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-12541_ : la règle de prix de panier créée pour l’utilisateur connecté est incorrectement appliquée pour l’utilisateur non connecté
   * _Remarque correctif_ : Le système supprime désormais correctement la règle de prix du panier pour les utilisateurs connectés lorsqu’ils sont automatiquement déconnectés en raison de l’expiration du cookie, garantissant ainsi que la remise n’est pas appliquée aux utilisateurs non connectés. Auparavant, la règle du prix du panier était toujours appliquée même lorsque l’utilisateur était déconnecté, ce qui entraînait l’application d’une remise incorrecte aux utilisateurs non connectés.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38944>
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13302_ : [Problème] [FONCTIONNALITÉ Optimisation] des performances Les grands paniers d’achat en empêchant...
   * _Remarque correctif_ : Le système optimise désormais les performances des paniers d’achats volumineux en empêchant les appels getActions en double, améliorant ainsi la vitesse et l’efficacité des opérations des paniers. Auparavant, pour un panier avec plusieurs articles, la fonction getActions était appelée plusieurs fois, ce qui ralentissait les performances du système.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39292>
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/pull/39290>
* _AC-13797_ : Registre de cadeaux Le produit ne s’affiche pas correctement
* _AC-13841_ : Registre de cadeaux Le produit ne s’affiche pas correctement
* _AC-8103_ : TVA de traduction dans le moteur de rendu d’adresses
   * _Correction de note_ : le système permet désormais la traduction du texte « VAT », « T », « F » dans les rendus d’adresse, ce qui permet aux utilisateurs de traduire ces termes dans la langue spécifique du magasin. Auparavant, ces termes n’étaient pas traduisibles, ce qui obligeait les utilisateurs à recourir à une solution de contournement.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/36942>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/36943>
* _ACP2E-2055_ : commandes en double avec le même ID de devis en même temps avec un décalage horaire réduit
   * _Correction de la note_ : correction du problème lorsque les clients Adobe Commerce rencontraient des commandes en double placées avec le même QuoteID
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2470_ : panier persistant effacé lors de l’étape de passage en caisse
   * _Correction de la note_ : après la correction, la sélection du mode de paiement lors du passage en caisse sans être connecté ne met pas fin à la session persistante.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2518_ : la commande à nouveau ajoute le produit non affecté au panier
   * _Remarque sur la correction_ : auparavant, pour les différents magasins, les produits pouvaient être commandés à partir de l’autre magasin. Une fois ce correctif appliqué, seul le même magasin , le même produit de la portée peut être réorganisé lorsque le partage du compte client est activé
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2620_ : dans l&#39;administration, le « Panier » sur le côté gauche n&#39;est pas mis à jour lors de la sélection des articles et « Déplacer vers le panier » sur le côté droit
   * _Remarque de correction_ : le « Panier » sur le côté gauche est mis à jour lors de la sélection des articles et « Déplacer vers le panier » sur le côté droit dans le côté administrateur. Auparavant, cette fonctionnalité ne fonctionnait pas, car les éléments de panier transformés ne devenaient pas vides à partir de la session.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2646_ : règle de vente [Cloud] non appliquée à la première commande d&#39;expédition multiple
   * _Note de correction_ : une fois la correction effectuée, la remise s&#39;affiche correctement pour chaque commande du même devis multilivraison.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2664_ : les requêtes [Cloud] en parallèle de production pour ajouter le même produit au panier entraînent deux éléments distincts dans l’API Cart rest
   * _Remarque de correction_ : le système traite désormais correctement plusieurs demandes parallèles pour ajouter le même produit au panier dans un seul élément de ligne, ce qui empêche la création d’éléments de ligne distincts pour le même SKU. Auparavant, la réalisation de requêtes parallèles pour ajouter le même produit au panier via l’API REST entraînait plusieurs éléments de ligne pour le même SKU.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2676_ : problème de commande depuis le registre des cadeaux Magento 2.4.4 Enterprise/Commerce
   * _Correction de la note_ : le problème empêchant l’achat réussi d’un produit dans un registre des cadeaux a été résolu, ce qui permet de passer des commandes et de mettre à jour le registre des cadeaux de manière appropriée. Auparavant, une erreur se produisait lorsque vous tentiez de passer une commande dans un registre des cadeaux, ce qui empêchait la conclusion de l’achat.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/35432>
* _ACP2E-2704_ : impossible d’envoyer le cookie. Taille des &#39;messages-image&#39; lors de la tentative de réorganisation
   * _Correction de la note_ : le processus de réorganisation ne générera pas ses propres erreurs maintenant. Elle s’appuie sur les vérifications d’articles intégrées de la liste du panier.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2798_ : l&#39;adresse de livraison par défaut n&#39;est pas sélectionnée lors du passage en caisse
   * _Correction de note_ : l’adresse d’expédition par défaut est désormais sélectionnée comme événement dans le contexte de l’activation de la recherche d’adresses.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2897_ : problème d’api [CLOUD] graphql addProductsToCart avec l’option personnalisée
   * _Remarque à propos de la correction_ : GraphQL ajoute correctement au panier le même produit avec différentes options personnalisées
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2917_ : [Cloud] les règles relatives aux produits associés ne fonctionnent pas lors du changement d’affichage de la boutique
   * _Remarque à propos de la correction_ : le problème a été résolu en confirmant que la valeur de la propriété personnalisée est reçue avec succès sur la page du panier. Auparavant, elle n’était pas récupérée correctement lors du changement entre les magasins sur la page du panier de storefront.
* _ACP2E-2923_ : plusieurs adresses ajoutées au compte lors du passage en caisse en tant que nouveau client
   * _Remarque correctif_ : Le système n’enregistre désormais une nouvelle adresse client qu’une seule fois si la commande n’a pas pu être créée, ce qui empêche la création de plusieurs adresses identiques en cas d’erreurs de passation de commande. Auparavant, le système enregistrait une nouvelle adresse chaque fois qu’une tentative de commande était effectuée, que la commande ait été créée avec succès ou non.
   * _Contribution_ au code GitHub : <https://github.com/magento/magento2/commit/001e5188>, <https://github.com/magento/inventory/commit/2ebcef39>
* _ACP2E-3004_ : la commande client à nouveau via le formulaire de commande invité entraîne un panier vide
   * _Correction de note_ : auparavant, lorsque le client passait une nouvelle commande sur la page Commandes et retours, il était redirigé vers la page de connexion. Une fois ce correctif appliqué, le client enregistré est correctement redirigé vers la page Afficher le panier lors d’une nouvelle commande. Le flux fonctionne de la même manière que pour les clients invités.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3025_ : l’utilisateur administrateur avec des ressources de rôle limitées ne peut pas afficher les paniers
   * _Remarque de correction_ : auparavant, l’administrateur restreint ne pouvait pas voir le panier abandonné du panneau d’administration pour un site web associé. Une fois ce correctif appliqué, l’administrateur restreint peut voir le panier abandonné dans le panneau d’administration.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3176_ : [Cloud] commande rapide grande quantité de performances de SKU
   * _Remarque de correction_ : les performances de passage en caisse ont été améliorées lorsque les attributs utilisés dans les conditions des règles de prix de panier ne sont pas présents pour tous les produits et lorsque la fonctionnalité MAP (Prix minimum annoncé) est activée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3211_ : objets dupliqués dans le panier
   * _Remarque de correction_ : le système traite désormais correctement plusieurs demandes parallèles pour ajouter le même produit au panier dans un seul élément de ligne, ce qui empêche la création d’éléments de ligne distincts pour le même SKU. Auparavant, la réalisation de requêtes parallèles pour ajouter le même produit au panier sur Storefront entraînait plusieurs éléments de ligne pour le même SKU.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3296_ : l’e-mail de confirmation de commande de passage en caisse est envoyé aux e-mails saisis dans Prénom/Nom
   * _Remarque corrigée_ : L’e-mail de confirmation de commande de paiement, qui était précédemment envoyé lorsqu’un modèle de type e-mail était entré dans les champs Prénom et Nom, n’est plus envoyé.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3402_ : Formulaire d’adresse de livraison de paiement obtenir une mise à jour avec une adresse incorrecte
   * _Remarque correctif_ : shippingAddressFromData est maintenant enregistré dans le stockage local par site Web. Auparavant, une adresse du mauvais site web pouvait être automatiquement renseignée dans le formulaire d’adresse d’expédition lors du passage en caisse si un code de magasin était utilisé dans l’URL et que le passage en caisse était initié à partir de plusieurs sites web au cours de la même session de personne invitée.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3405_ : [CLOUD] Checkout ne conserve pas l’adresse de facturation sélectionnée lorsque le Search d’adresse est activé
   * _Remarque corrigée_ : La page de paiement du paiement conservera désormais l’adresse de facturation sélectionnée lorsque la recherche d’adresse est activée. Auparavant, si « Nombre d’adresses client limite » est configuré sur 1 et que le client a plusieurs adresses, l’adresse de facturation sélectionnée disparaissait après le rechargement de la page.
* _ACP2E-3407_ : Carte-cadeau | La fusion de panier fusionne les cartes-cadeaux
   * _Correction de la note_ : les produits de carte cadeau sont désormais correctement fusionnés dans le panier
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3415_ : la persistance du panier n’est pas respectée lors de la déconnexion
   * _Correction de la remarque_ : ajout de la fonctionnalité « Mémoriser mon identité » manquante dans la fenêtre contextuelle d’authentification et les connexions de passage en caisse.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/344fce23>
* _ACP2E-3488_ : les données de devis existantes ne sont pas mises à jour/invisibles, mais créent un nouvel enregistrement de devis lorsque trigger_recollect = 1
   * _Remarque correctif_ : les articles du panier du client ne disparaissent plus à la suite de la suppression d’un produit après son ajout au panier.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3495_ : lorsqu’un élément du registre des cadeaux est acheté, le client voit des éléments qui ne figurent pas dans son registre
   * _Remarque correctif_ : la mise à jour du registre de cadeaux n’inclut plus les articles qui n’appartiennent pas au registre de cadeaux.
* _ACP2E-3510_ : [problème de cloud] avec la fenêtre contextuelle de confirmation « Tout supprimer » Suppression des articles du panier sans confirmation
   * _Correction de la remarque_ : désormais, cliquer sur le bouton « Tout supprimer » pour les produits nécessitant de l’attention invite une fenêtre contextuelle de confirmation à s’assurer que les articles ne sont supprimés qu’avec votre confirmation. Auparavant, les éléments étaient supprimés immédiatement sans confirmation
* _ACP2E-3618_ : [CLOUD] fonctionnalité du bouton de réorganisation
   * _Corriger la note_ : la réorganisation d’une commande de la zone d’administration ajoute désormais les produits en stock au devis, même si certains produits de la commande d’origine ne sont plus en stock. Avant la correction, aucun produit n’était ajouté au nouveau devis si le produit sans stock se trouvait dans la commande d’origine.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a52ff98f>
* _ACP2E-3622_ : les magasins de recherche ne fonctionnent pas par code postal
   * _Remarque de correction_ : la recherche d&#39;emplacements de retrait par code postal ne fonctionnait pas correctement pour les localisations en néerlandais. Après la correction, la recherche de l’emplacement de retrait fournit des résultats en fonction du code postal.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/344fce23>

### Panier et passer en caisse, passage en caisse/passage en caisse d’une page

* _AC-9386_ : [bogue aléatoire] le champ E-mail n’est pas rendu ou prend beaucoup de temps s’afficher dans la page Expédition ou paiement du paiement du paiement
   * _Correction de la note_ : Commerce effectue désormais le rendu attendu du champ **[!UICONTROL Email]** sur les pages d’expédition et de paiement du paiement. Auparavant, ce champ était absent ou son rendu était lent.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/e1babcfd>

### Panier et passer en caisse, commander

* _ACP2E-3097_ : le sélecteur de date pour le produit avec plusieurs options personnalisables avec des champs de date ne fonctionne pas lors de la commande auprès de l’administrateur
   * _Remarque de correction_ : le système affiche désormais correctement le sélecteur de date pour tous les champs de date lors de la configuration d’un produit avec plusieurs options de date personnalisables dans le processus de création de commande d’administration. Auparavant, le sélecteur de date s’affichait uniquement pour le premier champ de date, laissant les champs restants sans sélecteur de date.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b21e5d91>

### Panier et passer en caisse, expédition

* _AC-12119_ : Achat instantané « livraison la moins chère » cassé pour les produits configurables
   * _Correction de note_ : la fonction Achat instantané a incorrectement sélectionné l’option de livraison en magasin la plus coûteuse pour les produits configurables au lieu de la méthode de taux forfaitaire la moins chère. Ce correctif garantit que la méthode d’expédition correcte est choisie en fonction du prix réel. »
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38811>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38819>, <https://github.com/magento/magento2/commit/29fe9097>

### Catalogue

* _AC-10910_ : le nettoyage de la table de base de données cron_schedule ne nettoie pas les tâches non existantes
   * _Remarque sur la correction_ : le système nettoie désormais automatiquement la table de base de données cron_schedule, supprimant les entrées des tâches qui n&#39;existent plus dans le système. Vous obtiendrez ainsi des performances optimales en conservant un nombre minimal de lignes dans le tableau. Auparavant, les entrées des tâches des modules inactifs ou supprimés n’étaient pas nettoyées, ce qui entraînait une accumulation de données inutile dans le tableau cron_schedule.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38217>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38693>
* _AC-10953_ : le niveau de prix n&#39;est pas supprimé du produit configurable
   * _Remarque de correction_ : le système supprime désormais correctement le prix de niveau d’un produit lorsqu’il est converti d’un produit simple en un produit configurable, assurant ainsi un affichage précis des prix sur le serveur frontal. Auparavant, le prix de niveau d’un produit configurable n’était pas supprimé lorsqu’un produit était converti d’un produit simple en produit configurable, ce qui entraînait une incohérence du prix affiché.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38390>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38427>
* _AC-11804_ : le WYSIWYG de description de catégorie est vide dans un magasin autre que le magasin par défaut
   * _Remarque de correction_ : le système enregistre et affiche désormais correctement la description de la catégorie dans l’éditeur WYSIWYG lors de la modification d’une catégorie au niveau de l’affichage du magasin. Auparavant, l’éditeur WYSIWYG s’affichait vide après l’enregistrement d’une description de catégorie au niveau de l’affichage du magasin.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38622>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38623>
* _AC-11970_ : impossible de réorganiser les produits configurables avec une case à cocher sélectionnée pour l’option personnalisée
   * _Note de correction_ : le système traite désormais correctement la réorganisation des produits configurables avec une seule case à cocher sélectionnée option personnalisée, ce qui permet de créer un panier avec succès. Auparavant, toute tentative de réorganisation de ces produits entraînait une erreur et empêchait l’ajout d’articles dans le panier.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38736>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1d144bce>
* _AC-12076_ : [Problème] Corrigez le libellé de l’élément de filtre sur la navigation superposée.
   * _Remarque de correction_ : le système utilise désormais correctement les mots « élément » et « éléments » dans l’élément de filtre de navigation superposé, ce qui améliore la clarté et la précision des descriptions des filtres. Auparavant, ces mots n’étaient pas utilisés correctement, ce qui pouvait prêter à confusion pour les utilisateurs et utilisatrices qui parcouraient les options de filtre.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38789>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37852>
* _AC-12164_ : le format de date et d&#39;heure de l&#39;option personnalisée ne fonctionne pas
   * _Remarque de correction_ : le système applique désormais correctement le format de date configuré aux options personnalisées de produit de type Date, en s’assurant que le format de date s’affiche correctement sur le front-end. Auparavant, les modifications apportées à la configuration du format de date n’étaient pas répercutées sur le front-end pour les options personnalisées de produit de type Date.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/32990>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38925>
* _AC-13068_ : options de liste déroulante manquantes
   * _Remarque de correction_ : le système affiche désormais correctement toutes les valeurs dans la liste déroulante lors de la création d’un nouvel attribut avec plus de 20 valeurs. Auparavant, seules les 20 premières valeurs ou une autre valeur de page sélectionnée s’affichait, ce qui entraînait l’absence des valeurs restantes.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13296_ : [Problème] Utilisez l’ID de magasin actuel pour le cache d’exécution de catégorie.
   * _Remarque de correction_ : le système utilise désormais correctement l’ID de magasin actuel pour le cache d’exécution de catégorie, ce qui empêche le remplacement des données lorsque l’émulation est utilisée ou que le code personnalisé enregistre la catégorie dans différents magasins. Auparavant, l’objet stocké dans l’exécution pouvait provenir d’un magasin incorrect, ce qui entraînait le remplacement des données.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39310>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/36394>
* _AC-13324_ : bin/magento sampledata:deploy —no-update renvoie une exception
   * _Remarque de correction_ : le système accepte désormais correctement une valeur booléenne lors de l’utilisation de l’option —no-update dans la commande sampledata:deploy, ce qui empêche toute erreur lors du déploiement des données d’exemple. Auparavant, une erreur était générée lors de l’utilisation de cette commande, car le système s’attendait incorrectement à une valeur entière.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39344>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/39345>
* _AC-13355_ : [Problème] Corrigez l’utilisation du type de cache EAV
   * _Remarque à propos de la correction_ : le système utilise désormais correctement le type de cache EAV à tous les emplacements pertinents, ce qui garantit une mise en cache des données cohérente et efficace. Auparavant, le type de cache EAV n’était pas utilisé de manière cohérente, ce qui entraînait des inefficacités et des incohérences potentielles dans la mise en cache des données.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/32322>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/31264>
* _AC-13596_ : la recherche avancée de catalogue avec des données vides accède à la page de résultats de recherche[branche 2.4.dev]
   * _Remarque de correction_ : le système conserve désormais correctement les utilisateurs sur la page Recherche avancée et affiche un message d’erreur lorsqu’ils tentent d’effectuer une recherche sans saisir de données. Auparavant, l’exécution d’une recherche vide redirigeait les utilisateurs vers la page de recherche avancée du catalogue avec un message les invitant à modifier leur recherche.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-13622_ : [Problème] Mise en page du produit en fonction de attribute_set
   * _Remarque à propos de la correction_ : le système permet désormais d’ajuster la mise en page du produit en fonction du jeu d’attributs, offrant ainsi un moyen plus pratique et plus efficace de gérer l’affichage du produit dans le magasin frontal. Auparavant, la mise en page ne pouvait être ajustée que par SKU ou par type de produit, ce qui n’était pas toujours pratique pour de nombreux produits ou articles spécifiques.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38790>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/36244>
* _AC-6738_ : clé unique manquante dans la table eav_attribute_option_value
   * _Remarque de correction_ : le système inclut désormais une clé unique sur les colonnes &#39;option_id&#39; et &#39;store_id&#39; dans la table &#39;eav_attribute_option_value&#39;, ce qui empêche qu&#39;une option ait plusieurs valeurs pour la même vue de magasin. Auparavant, un code incorrect pouvait entraîner l’affichage de plusieurs valeurs pour une même vue de magasin, ce qui provoquait des problèmes lors de la modification de produits ou d’attributs.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/24718>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/28796>
* _AC-8297_ : [Problème] utilisez la classe de visibilité pour l’indexeur de produits de catégorie, au lieu des valeurs codées en dur
   * _Remarque de correction_ : le système utilise désormais la classe de visibilité pour l’indexeur de produit de catégorie au lieu des valeurs codées en dur, ce qui améliore la modularité. Auparavant, les valeurs codées en dur étaient utilisées dans l’indexeur de produits de catégorie, ce qui limitait la flexibilité et l’adaptabilité.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37200>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37199>
* _AC-9375_ : code de devise non modifié dans le widget Nouveau produit
   * _Correction de la note_ : le système met désormais correctement à jour le code de devise dans le widget Nouveau produit lorsque la devise est modifiée dans le serveur frontal, assurant ainsi la cohérence de l’affichage de la devise sur le site. Auparavant, la modification de la devise dans le front-end n’affectait pas le code de devise affiché dans le widget Nouveau produit.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37898>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37899>
* _ACP2E-2224_ : le prix normal ne s&#39;affiche pas sur le PLP pour le produit configurable
   * _Correction de note_ : le prix normal est désormais affiché sur les pages de liste des produits pour les produits configurables qui ont des produits enfants avec un prix spécial.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2478_ : les informations sur les stocks ne s’affichent pas correctement sur la grille de marchandisage visuelle.
   * _Remarque correctif_ : Stock s’affiche désormais en fonction du magasin sélectionné.
   * _Contribution_ du code GitHub : <https://github.com/magento/inventory/commit/bdbf97ea>
* _ACP2E-2621_ : le contenu du widget n’est pas mis à jour sur la page cms
   * _Remarque correctif_ : Le système met désormais à jour le contenu du widget sur une page CMS lorsqu’un produit est défini comme nouveau et enregistré, en veillant à ce que la page affiche la collection de produits mise à jour. Auparavant, la page n’était pas mise à jour pour afficher le nouveau produit en raison des identités de cache incorrectes utilisées pour le widget dans le cache.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2630_ : problèmes d&#39;enregistrement de la tarification avancée sur les produits groupés
   * _Remarque sur la correction_ : amélioration des performances d’économie de produit groupé.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2652_ : [On-Premise] Le processus de réindexation est inefficace lors de la création de règles de prix de catalogue
   * _Remarque de correction_ : désormais, l’enregistrement de la règle de prix de catalogue n’invalide pas les indexeurs, mais réindexe uniquement les produits affectés
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2679_ : mise à jour de l’heure des attributs de produit de type Date et Heure via l’importation d’un fichier CSV
   * _Remarque de correction_ : désormais, les attributs datetime auront une partie temporelle dans les données exportées. Il sera également possible de mettre à jour l’heure de ces attributs à l’aide de l’importation. De même, si l’option « Enceinte de champs » est activée, les valeurs d’attribut dans la colonne « additional_attributes » sont placées entre guillemets doubles.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38306>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2689_ : aucun message d’erreur approprié lorsque l’ID de site web est incorrect dans la requête
   * _Remarque de correction_ : Maintenant, le message d’erreur approprié a été ajouté pour afficher lorsque l’ID de site Web est incorrect dans la demande. Auparavant, il n’y avait aucune validation lorsque l’identifiant du site Web était incorrect dans la demande.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2785_ : l’image du produit est perdue après la suppression d’une mise à jour planifiée existante qui n’affecte pas l’image
   * _Remarque corrigée : les_ images des produits ne sont pas supprimées lors de la suppression de la mise à jour intermédiaire.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-2799_ : [Cloud] Prix de produit groupé incorrect lorsqu’il est utilisé avec des prix de niveau
   * _Corriger la note_ : précédemment, lors du calcul de certaines remises en pourcentage arrondies à 2 décimales maximum, générait différents prix finaux pour le panier et la page de liste de produits/page de détails des produits. Une fois ce correctif appliqué, le prix final du bundle du produit est le même que dans les pages de détails du produit, de liste des produits et de panier.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38091>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2805_ : la règle de promotions de catalogue ne fonctionne pas avec quantity_and_stock_status attribut
   * _Correction de note_ : l&#39;attribut quantity_and_stock_status sera désormais pris en compte par la règle de promotion du catalogue, qui n&#39;était pas prise en compte auparavant lors de la génération de nouveaux produits du côté administrateur.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/35627>
   * _Contribution du code GitHub_ : <https://github.com/magento/inventory/commit/cf34971d>
* _ACP2E-2837_ : les valeurs de colonne updated_at de l’entité produit ne sont pas mises à jour lors de la mise à jour du prix via l’API REST
   * _Remarque de correction_ : la colonne « Dernière mise à jour à » du produit depuis l’administration est mise à jour à la date et à l’heure correctes lors de la mise à jour des produits existants via l’API REST. Auparavant, la colonne « Dernière mise à jour à » n’était pas mise à jour correctement.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2840_ : il est possible de définir des valeurs non uniques via l&#39;importation de produits
   * _Correction de la note_ : le système applique désormais correctement la contrainte de valeur unique pour les attributs de produit uniques lors de l’importation du produit, ce qui empêche d’avoir des valeurs en double pour cet attribut. Auparavant, il était possible de définir des valeurs non uniques pour les attributs de produit configurés pour avoir des valeurs uniques via l’importation du produit.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38445>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2843_ : les produits sur le serveur frontal utilisent des données spécifiques au magasin lorsque le mode de magasin unique est activé
   * _Remarque de correction_ : auparavant, lorsque nous activions le mode Boutique unique pour l’affichage par défaut de la boutique, les modifications n’étaient pas migrées vers la portée au niveau du site web. Une fois ce correctif appliqué, lorsque nous activons le mode de magasin unique, les données par défaut spécifiques à la vue du magasin sont synchronisées avec les données spécifiques au niveau du site web et résolvent les conflits possibles pour les produits et les catégories.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-2857_ : impossible de définir « Tri par défaut » dans une catégorie à l’aide de l’API REST
   * _Remarque de correction_ : mettez correctement à jour default_sort_by sur une catégorie via une requête API REST/SOAP
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2871_ : [Cloud] Le commerçant est confronté à des problèmes liés au nombre de listes de souhaits
   * _Remarque de correction_ : l’ajout d’un produit à la liste de souhaits d’un magasin n’augmente plus le nombre de listes de souhaits des autres magasins ouverts dans le même navigateur. Auparavant, si les deux magasins étaient chargés dans le même navigateur, le nombre de listes de souhaits augmentait également dans l’autre magasin.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2874_ : la page de catégorie au niveau du serveur frontal affiche des emplacements vides lors de l’utilisation du produit groupé
   * _Remarque de correction_ : les produits groupés qui ne sont pas commercialisables dans le contexte actuel du magasin ne sont plus indexés.
   * _Contribution du code GitHub_ : <https://github.com/magento/inventory/commit/bc37ec76>
* _ACP2E-2888_ : [CLARIFICATION] problèmes de table de séquence de produits groupés
   * _Note de correction_ : Les enregistrements des tables de séquence de produits groupés (sequence_product_bundle_option, sequence_product_bundle_selection) sont désormais supprimés lorsque le produit groupé est supprimé ou que les options du produit groupé sont supprimées.
Auparavant, les enregistrements des tables de séquences de produits groupées n’étaient pas supprimés.
* _ACP2E-2905_ : [Cloud] Émission d&#39;un devis dans l&#39;architecture multi-sites web
   * _Remarque de correction_ : auparavant, l’architecture multi-sites web avec différentes devises et groupes de clients ne pouvait pas appliquer correctement les remises au magasin. Une fois ce correctif implémenté, une architecture multi-sites web avec des remises sur les prix de différents groupes de clients s’appliquera correctement à différents magasins.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38506>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2909_: dynamic-rows.js:658 Uncaught TypeError: dataRecord.slice while editing bundle products
   * _Remarque de correction_ : il n’y a aucune erreur JavaScript dans la console du navigateur lors de la suppression de l’option du produit groupé.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38505>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-2950_ : [Cloud] offre groupée avec un prix incorrect dans la confirmation de commande
   * _Corriger la note_ : le montant correct s’affiche pour les options de lot dans l’ordre sur Storefront lorsque une devise autre que la base a été utilisée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2956_ : bogue d’ajout de vidéo YouTube
   * _Remarque pour le correctif : les_ images et les vidéos des produits sont configurées dans une portée globale. Étant donné que vous ne pouvez pas avoir une vidéo de produit dans une portée et pas dans une autre, le paramètre de clé API Youtube a été défini sur une portée globale.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2964_ : [mise à jour de l’URL cloud] uniquement pour store_id=0
   * _Remarque correctif_ : le « chemin URL » est désormais stocké avec l’ID de magasin correct. Auparavant, l’ID de magasin était incorrect, ce qui entraînait des chemins d’URL incorrects restant dans la base de données lors du déplacement des catégories.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3009_ : async.operations.all a exécuté et créé une erreur.
   * _Remarque sur la correction_ : les données de lien de produit incorrectes dans les appels API REST ne provoquent plus d’erreurs critiques.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-3029_ : [Cloud] Problème mobile : impossible de pincer l’image du PDP uniquement
   * _Remarque à propos de la correction_ : le système prend désormais en charge la fonctionnalité de pincement pour zoomer sur les images de la page des détails du produit dans la vue mobile de Chrome, ce qui améliore l’expérience de l’utilisateur mobile. Auparavant, le double-appui sur l’image en mode mobile dans Chrome n’effectuait pas un zoom avant sur l’image comme prévu.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3058_ : libellé manquant dans LayeredNavigation avec le nom d’option 0
   * _Remarque correctif_ : le problème a été résolu en ignorant un vérificateur de valeur vide pour la valeur d’attribut 0. Auparavant, il était considéré comme vide et était à l’origine du problème.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-3069_ : les clients voient les prix d’autres groupes de clients
   * _Remarque corrigée_ : correction d’un problème en raison duquel les informations relatives au groupe de clients étaient enregistrées dans un segment incorrect en raison de l’ancienne valeur de X-Magento-Vary dans la demande.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3076_ : erreur lors de la suppression des options de lot
   * _Remarque de correction_ : le système supprime désormais correctement les options de lot sans déclencher d’erreur ni empêcher la page de répondre. Auparavant, toute tentative de suppression des options de lot entraînait une erreur « La page ne répondait pas » et empêchait l’enregistrement du produit.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3094_ : problème de navigateur d&#39;autorisations de catégorie sans mémoire
   * _Remarque correctif_ : L’interface utilisateur des autorisations de catégorie a été repensée pour permettre le rendu d’un grand nombre d’autorisations à l’aide du composant et de la pagination prêts à l’emploi. Auparavant, les autorisations de catégorie provoquaient le blocage du navigateur avec un grand nombre d’autorisations attribuées à la catégorie.
* _ACP2E-3100_ : [Le fichier image cloud] n’existe pas dans le journal d’erreurs New Relic
   * _Remarque de correction_ : le système synchronise désormais les images d’espace réservé personnalisées avec le stockage local, en s’assurant qu’elles s’affichent correctement lors de l’utilisation du stockage distant tel qu’AWS S3. Auparavant, les images d’espace réservé personnalisées ne s’affichaient pas lors de l’utilisation du stockage distant, ce qui entraînait un affichage d’image rompu et des journaux d’erreurs.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3103_ : le flux RSS des nouveaux produits n&#39;est pas mis à jour avec les nouveaux produits en raison du cache
   * _Remarque de correction_ : le flux Rss pour les nouveaux produits est désormais mis à jour lorsqu’un produit est défini comme nouveau et enregistré
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3126_ : [Galerie multimédia de produits cloud] La réponse GQL n’est pas triée par position de l’image
   * _Remarque corrigée_ : Le système trie désormais correctement les éléments de la galerie multimédia par position dans la réponse GraphQL, garantissant ainsi un ordre d’affichage précis. Auparavant, les éléments de la galerie de médias n’étaient pas triés par position, ce qui entraînait un ordre d’affichage incorrect.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37671>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3136_ : les éléments de sous-catégorie [Cloud] ne s’affichent pas lors de la modification des widgets sur le serveur principal de l’administrateur
   * _Remarque sur la correction_ : l’arborescence de catégories sur la nouvelle page de widget ne devrait plus rencontrer de problèmes lors du chargement des catégories de niveau 5 et ultérieure. Auparavant, certaines catégories étaient manquantes lors du chargement de l’arborescence au-delà des catégories de niveau 5.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3198_ : [cloud] problème de zoom avec deux doigts et de déplacement sur l’appareil mobile réel
   * _Remarque sur les correctifs_ : le système assure désormais une fonctionnalité de zoom d’image cohérente sur les appareils mobiles, offrant ainsi une expérience utilisateur fluide et prévisible. Auparavant, la fonction de zoom d’image était incohérente et faisait soudainement un zoom arrière après un certain point lorsqu’elle était affichée sur un appareil mobile.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3282_ : lorsque nous annulons l’attribution de produits du catalogue partagé, les produits de la liste de souhaits ne sont pas effacés
   * _Note corrective_ : Maintenant, aucun article n’est visible dans la liste de souhaits si un produit n’est pas disponible dans le catalogue partagé. Auparavant, la page de la liste de souhaits affichait de manière incorrecte un nombre de « 1 élément » même lorsqu’aucun élément n’était réellement disponible dans la liste de souhaits.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3286_ : Produits associés Sélectionner tout/Désélectionner tout Événement
   * _Correction de la remarque_ : auparavant, les boutons « Tout sélectionner »/« Tout désélectionner » pour les produits associés ne fonctionnaient pas correctement si un produit était sélectionné manuellement. Après la correction, ces boutons fonctionnent désormais de manière cohérente, même après une sélection manuelle, garantissant que tous les produits sont correctement sélectionnés ou non sélectionnés.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3336_ : [Cloud] la traduction de l’e-mail d’alerte Stock est incorrecte
   * _Remarque sur la correction_ : lors de l’envoi d’alertes de stock/prix pour un site web comportant plusieurs vues de magasin utilisant différentes langues, la langue de la vue de magasin dans laquelle l’alerte a été créée est utilisée dans l’e-mail.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a4cf5e62>, <https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3350_ : les noms des catégories désactivées ne sont plus grisés dans l&#39;arborescence des catégories
   * _Remarque de correction_ : auparavant, les catégories désactivées n’étaient pas grisées dans l’arborescence des catégories. Désormais, elles s’affichent avec un effet de gris.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3410_ : le chargement configurable du formulaire de modification du produit entraîne un délai d’expiration et un épuisement de la mémoire
   * _Remarque sur la correction_ : avant la correction, les variations de produit configurables étaient créées en fonction de toutes les combinaisons d’options d’attribut possibles. Dans les cas où les attributs disposaient de nombreuses options, une opération longue et gourmande en ressources s’est produite. Désormais, les variations de produit configurables sont construites en fonction des attributs de produit enfant existants. Il en résulte beaucoup moins de calculs, ce qui améliore l’utilisation des ressources.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3454_ : Fotorama ne charge pas correctement la vidéo lors de l’utilisation des nuanciers et l’option est présélectionnée via l’URL
   * _Remarque de correction_ : les vidéos de produit s’affichent désormais correctement sur la page des détails du produit configurable, si l’URL contient les options sélectionnées.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3461_ : le widget de carrousel PageBuilder affiche les produits qui ne correspondent pas aux conditions
   * _Remarque sur la correction_ : la liste de produits utilisée dans les widgets respecte désormais la condition de catégorie
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3469_ : une erreur de validation se déclenche pour tous les produits du groupe lorsque la quantité d&#39;un produit n&#39;est pas valide
   * _Correction de la note_ : désormais, l’erreur de validation est correctement déclenchée pour tous les produits du groupe lorsqu’un produit présente une quantité non valide, ce qui ne se produisait pas auparavant.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3513_ : [CLOUD] Prix spécial non affiché dans le produit configurable
   * _Note de correction_ : après la correction, la modification de la valeur « Utilisé dans la liste de produits » pour l&#39;attribut de prix spécial n&#39;affectera pas l&#39;affichage du prix spécial pour les produits configurables.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3516_ : les tables temporaires des indexeurs ne sont pas nettoyées si le processus est arrêté
   * _Remarque sur la correction_ : les tables temporaires de l’indexeur CatalogRule sont désormais nettoyées si le processus de l’indexeur est arrêté
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3520_ : [QUANS] échecs des tests unitaires principaux dans 2.4.7-p3
   * _Note de correction_ : les notes de mise à jour de ce test ne sont pas nécessaires, car il s’agit d’une amélioration du test unitaire.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3533_ : problème de performance lors de la récupération de la quantité de stock pour les produits groupés avec plusieurs sources
   * _Remarque de correction_ : la page de modification des produits groupés et des produits groupés est désormais optimisée lorsque les produits affectés ont un grand nombre de sources de stock.
   * _Contribution du code GitHub_ : <https://github.com/magento/inventory/commit/0208e433>
* _ACP2E-3641_ : Réparer https://jira.corp.adobe.com/browse/ACP2E-3389
   * _Remarque sur la correction_ : amélioration des performances de la page de catégorie d’administration en cas de grand nombre de catégories d’ancrage
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/982b1c42>

### Catalogue, Contenu

* _ACP2E-3063_ : le cache [Cloud] n’est pas invalidé.
   * _Remarque de correction_ : auparavant, lors de l’enregistrement d’une page CMS avec une mise en page de conception mise à jour, la représentation n’était pas appropriée sur le front-end. Une fois ce correctif appliqué, la mise en page de conception appropriée est visible sur le front-end lorsque nous modifions la mise en page de conception et enregistrons la page CMS.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3131_ : [cloud] catégories ancre/non ancre inversées dans le widget de contenu
   * _Corriger la note_ : précédemment, lorsque nous avons sélectionné Afficher sur -> Catégories d&#39;ancrage, toutes les catégories qui ne reflétaient pas la relation parent-enfant entre l&#39;ancre et la non-ancre étaient affichées. Une fois ce correctif appliqué, l’option Afficher sur -> Catégories d’ancrage affiche uniquement les catégories d’ancrage (sélectionnables) et l’option Afficher sur -> Catégories non ancrées affiche les catégories non ancrées (sélectionnables)
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3152_ : catégories ne fonctionnant pas avec les widgets
   * _Correction de la note_ : auparavant, si nous avions enregistré le bloc CMS pour différentes catégories d’ancrage/non-ancrage, il ne fonctionnait pas pour les catégories enfants lorsqu’il s’affichait sur le front-end. Une fois ce correctif appliqué, le bloc s’affiche en front-end pour différentes catégories.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d01ee51e>

### Catalogue, Framework

* _AC-9111_ : La commande get(Shipments|Creditmemos|Invoice)Collection - Collection ne doit pas être chargée
   * _Correction de note_ : le système garantit désormais que les recouvrements pour les expéditions et les avoirs ne sont pas préchargés lors de leur récupération à partir d&#39;une commande, ce qui permet d&#39;appliquer des filtres ou des commandes supplémentaires à ces recouvrements. Auparavant, ces collections étaient automatiquement chargées, ce qui empêchait toute modification ultérieure.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37561>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37562>
* _ACP2E-2949_ : [Cloud]Suivi : incohérence dans la comparaison des données lors de la vérification des modifications apportées aux données
   * _Remarque sur la correction_ : Auparavant, l’objet d’enregistrement était appelé à chaque fois sans modification des données (pour tout champ de données numérique, comme int/float/double). Cela déclenche l’indicateur _hasDataChanges sur true et appelle la fonction d’enregistrement. Il ne vérifie pas non plus les nombres flottants encapsulés par une chaîne. Une fois que ce correctif est appliqué, la fonction d’enregistrement n’appelle que si les données sont modifiées. La valeur de données pour int/float/double-check avec la valeur transmise à la fonction et effectue une correspondance de type stricte
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c8931218>

### Catalogue, GraphQL

* _ACP2E-3090_ : gestion des filtres de catégorie dans GraphQL : includeDirectChildrenOnly et category_uid
   * _Remarque de correction_ : seules les catégories enfants directes sont récupérées lors du filtrage par category_uid.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3166_ : le tri des produits Graphql [Cloud] ne fonctionne pas
   * _Remarque sur la correction_ : le tri des produits GraphQl par plusieurs champs lorsque les champs sont transmis dans des variables fonctionne désormais comme prévu.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3312_ : les prix de niveau renvoient une valeur incorrecte dans les produits GraphQL (par rapport à Storefront)
   * _Remarque sur la correction_ : après la correction, les prix de niveau du produit renvoyés pour les requêtes GraphQL ont un prix par article.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3385_ : [CLOUD] B2B : problème de catégorie via GraphQL
   * _Remarque sur la correction_ : après la correction, la requête GraphQL sur les catégories renvoie les catégories avec une autorisation Autoriser même si la catégorie racine ne dispose pas d’une autorisation Autoriser.

### Catalogue, tarification, évaluation et prévisualisation

* _ACP2E-2672_ : le point d’entrée de l’API Prix spécial [Cloud] renvoie une erreur lors de la mise à jour simultanée d’un grand nombre de produits
   * _Remarque de correction_ : désormais, l’API de mise à jour en bloc Prix spéciaux crée une seule campagne pour chaque période au lieu de plusieurs mises à jour planifiées pour chaque produit et période. En outre, il prend en charge les requêtes d’API simultanées pour accélérer le traitement d’un grand nombre de SKU.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/f89a447e>

### Catalogue, produit

* _AC-7050_ : l&#39;arborescence de sélection de catégorie dans l&#39;édition du produit n&#39;est pas dans le même ordre que celui défini dans Catalogue->Catégories
   * _Remarque de correction_ : le système affiche désormais correctement l’arborescence de sélection des catégories dans la section d’édition du produit, dans l’ordre défini dans Catalogue->Catégories, ce qui facilite l’administration des produits dans les catalogues volumineux. Auparavant, l’arborescence de catégories de la section de modification de produits s’affichait dans l’ordre de création des catégories, quel que soit l’ordre d’affichage défini dans Catalogue->Catégories.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/36101>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/36104>

### Catalogue, SEO

* _ACP2E-3653_ : URL canonique incorrecte pour la catégorie lorsque la page > 1
   * _Remarque de correction_ : auparavant, l’URL canonique pour le contenu multi-pages ne fonctionnait pas correctement, affichant systématiquement l’URL de base. Cependant, une fois le correctif implémenté, l’URL canonique pour le contenu multi-pages affiche désormais correctement l’URL avec l’ID de page.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/982b1c42>

### Catalogue, recherche

* _ACP2E-2757_ : les produits ne s’affichent pas dans la catégorie et la recherche, mais les liens directs fonctionnent
   * _Remarque sur la correction_ : auparavant, l’attribut personnalisé Oui/Non avec price_* attribute_code ne fonctionnait pas avec l’indexation. Après ce correctif, l’attribut personnalisé Oui/Non fonctionne comme prévu.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-3053_ : [Cloud] Erreur de recherche élastique sur certaines pages de catégorie
   * _Correction de la note_ : précédemment, avec le ticket de configuration mentionné, lorsque nous fixons le prix 0 pour plusieurs produits, une exception est générée sur la page de catégorie front-end. Une fois ce correctif appliqué lorsque le prix de plusieurs produits est égal à 0 et que nous chargeons la page de catégorie sur le front-end, aucune exception ne sera générée et la page de catégorie sera chargée correctement.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-3345_ : erreur de type lors de la création de l&#39;objet : Magento\CatalogSearch\Model\Indexer\Fulltext\Interceptor Exception
   * _Remarque sur la correction_ : après la correction, une instance de la classe Magento\CatalogSearch\Model\Indexer\Fulltext peut être créée sans spécifier $data.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3521_ : [CLOUD] le problème lié aux produits n’est pas visible dans le front-end après l’enregistrement dans Magento Admin
   * _Remarque sur la correction_ : après la correction, les produits configurables qui ont des produits enfants avec des noms longs ne seront pas manqués dans le storefront.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1984c61c>

### Catalogue, Livraison

* _ACP2E-3195_ : adresse d&#39;expédition vide lors de la commande d&#39;un article de registre cadeau
   * _Remarque corrective_ : Auparavant, pour les articles du registre des cadeaux des utilisateurs invités, lorsqu’ils étaient renvoyés par la fonction de messagerie, générait une adresse vide vide, incorrecte pour passer une commande. Une fois ce correctif appliqué, le registre des cadeaux vérifie les utilisateurs connectés/invités et les adresses attribuées s&#39;ils existent.

### Nuage

* _ACP2E-3010_ : [PHPSESSID] cloud modifie chaque demande POST
   * _Remarque correctif_ : PHPSESSID ne se régénère plus sur POST requêtes sur la zone front-end pour un client connecté si le cache L2 Redis est activé et que le client a été mis à jour à partir du backend
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3532_ : avertissements de génération de plan de site
   * _Remarque correctif_ : Après la correction, le sitemap est généré dans le répertoire tmp du système et copié vers la destination finale.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/d4de4726>

### Contenu

* _AC-10539_ : [Problème]  avec l’affichage des prix dans le widget Récemment consultés
   * _Remarque correctif_ : Le système affiche désormais correctement le prix des produits simples en rupture de stock dans le widget « Produit récemment consulté », ce qui garantit la cohérence de tous les widgets et pages de liste de produits. Auparavant, le prix des produits simples en rupture de stock n’était pas affiché dans le widget « Produit récemment consulté » en raison d’une condition dans les modèles de chargement des prix.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38167>
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/pull/38159>
* _AC-10596_ : [Problème] Corriger la faute de frappe et la grammaire dans le fichier acl.xsd
   * _Remarque de correction_ : le système corrige désormais une erreur de frappe et de grammaire dans le fichier acl.xsd, ce qui améliore la clarté et la précision de la documentation. Auparavant, le fichier acl.xsd contenait une faute de frappe et une grammaire incorrecte, ce qui pouvait prêter à confusion.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38061>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38046>
* _AC-10845_ : image de bannière Pagebuilder non visible dans la galerie
   * _Remarque de correction_ : le système affiche désormais correctement les images de bannière chargées dans les dossiers nouvellement créés dans la galerie Pagebuilder, ce qui élimine les erreurs de console précédentes. Avant cette correction, les images de bannière n’étaient pas visibles dans la galerie si elles étaient chargées dans un nouveau dossier, provoquant une erreur de console.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-12283_ : « Indicatif régional non défini » après la mise à jour vers la version 2.4.5-p8
   * _Remarque de correction_ : le système termine désormais avec succès le processus de déploiement de contenu statique lorsque le module Magento_CSP est activé et que « dev/js/translate_strategy » est défini sur « bedded », sans déclencher l’erreur « Indicatif régional non défini ». Auparavant, dans ces conditions, le processus de déploiement de contenu statique échouait avec une erreur « Code zone non défini ».
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38845>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38922>
* _AC-12692_ : l’arborescence de catégorie du widget n’est pas rendue correctement
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39008>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/58e40ceb>
* _AC-13054_ : impossible de voir le message « Utilisation de la valeur par défaut » lors de la modification du thème dans la page de configuration de la conception
   * _Correction de la note_ : le système inclut désormais une colonne distincte pour afficher le message « Utilisation de la valeur par défaut » en fonction du thème sélectionné dans la page de configuration de la conception. Cela garantit la clarté et la visibilité du statut de la valeur par défaut. Auparavant, le message « Utiliser la valeur par défaut » ne s’affichait pas, ce qui entraînait une confusion sur le statut du thème sélectionné.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13569_ : [Problème] Restaure à nouveau la compatibilité descendante avec les plug-ins TinyMCE (après cela...
   * _Remarque de correction_ : le système restaure désormais la rétrocompatibilité avec les modules externes TinyMCE, ce qui permet d’appeler les fonctions définies dans le module externe lors de l’utilisation du widget à partir d’un autre emplacement. Auparavant, en raison d’une modification de la version de TinyMCE, les modules externes ne renvoyaient pas les widgets en tant qu’objet, ce qui entraînait une erreur lors de la tentative d’appel de certaines fonctions sur l’instance de widget.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39262>
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/pull/39258>
* _AC-9638_ : [Problème] de téléchargement de fichier dans l’éditeur WYSIWYG sur la page produit
   * _Remarque correctif_ : Le système affiche désormais correctement l’arborescence des dossiers et autorise les téléchargements d’images dans l’éditeur WYSIWYG sur la page du produit, même après avoir développé l’onglet « Image et vidéos ». Auparavant, l’expansion de l’onglet « Image et vidéos » entraînait d’abord l’affichage de l’arborescence des dossiers et un message d’erreur lors de la tentative de téléchargement d’une image dans l’éditeur WYSIWYG.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38026>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38025>
* _ACP2E-2392_ : [problème de bloc dynamique On-PREM]
   * _Note correctif_ : les wdigets sont maintenant correctement rendus dans des blocs dynamiques.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2606_ : l’URL de YouTube nocookie ne fonctionne pas dans Page Builder
   * _Remarque de correction_ : le générateur de pages autorise désormais l’URL de non-cookie Youtube dans les paramètres d’élément de formulaire des règles de validation. Auparavant, l’URL de non-cookie Youtube ne fonctionnait pas dans le générateur de page.
* _ACP2E-2693_ : [Cloud] le serveur frontal ne se charge pas en raison d’un problème dans le modèle de newsletter
   * _Remarque sur la correction_ : l’ajout de blocs via la section de contenu de page CMS ne génère plus d’exception
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2836_: ACP2E-2836: [Cloud] Exception d’investigation trouvée dans le journal : InvalidArgumentException: La classe n’existe pas dans vendor/magento/module-rule/Model/ConditionFactory.php
   * _Remarque de correction_ : la suppression d’une condition sur les paramètres de contenu des produits PageBuilder n’entraîne plus l’enregistrement d’une exception dans les fichiers journaux. Auparavant, la suppression d’une condition sur les paramètres de contenu des produits PageBuilder entraînait l’enregistrement d’une exception critique dans les journaux, même si elle ne provoquait aucun problème sur le serveur frontal.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2-page-builder/commit/36c0f5df>
* _ACP2E-2842_ : basculement vers le mode magasin unique - le contenu global n’apparaît plus
   * _Remarque de correction_ : le système synchronise désormais les configurations de conception d’affichage du magasin avec les configurations de conception de site web lors de l’activation du mode magasin unique, en s’assurant que les mises à jour de contenu sont visibles sur le front-end. Auparavant, le passage en mode boutique unique empêchait la répercussion des mises à jour de contenu sur le storefront.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2903_ : Page Builder remplace l’image lors de la tentative d’ajout d’un lien et d’autres problèmes d’utilisation.
   * _Remarque de correction_ : si vous cliquez maintenant sur une image, les liens dans l’éditeur wysiwyg de l’élément de texte Page Builder chargent les données appropriées dans l’image, la boîte de dialogue de configuration des liens. L’ajout d’un lien vers une image dans l’éditeur fonctionne désormais correctement. Auparavant, l’image était remplacée par un lien.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-2970_ : l’ancienne galerie de médias ne parvient pas à rendre les images lorsqu’une image de 0 octet est placée dans le répertoire
   * _Remarque de correction_ : le système gère désormais les images de 0 octet dans la galerie de médias sans perturber le fonctionnement, ce qui permet d’afficher et de sélectionner d’autres images du répertoire comme prévu. Auparavant, la présence d’une image de 0 octet dans la galerie de médias empêchait l’affichage ou la sélection de toutes les images du répertoire.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3064_ : erreur Page Builder lors de la modification du bloc CMS
   * _Remarque de correction_ : le système enregistre désormais correctement les modifications apportées à la zone d’administration à l’aide de Page Builder, sans générer l’erreur « Page Builder affichait pendant 5 secondes sans libérer les verrous ». dans la console du navigateur. Auparavant, cette erreur se produisait lors de la tentative d’enregistrement des modifications, empêchant la mise à jour réussie du contenu.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/35b1b1da>, <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-3092_ : [CLOUD] aucun bouton de passage en caisse ou de modification de panier dans la section Panier
   * _Remarque sur la correction_ : le produit groupé est désormais ajouté au panier via des widgets sans erreur.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b21e5d91>, <https://github.com/magento/magento2-page-builder/commit/4ebe3f1d>
* _ACP2E-3113_ : l’aperçu de l’évaluation du contenu sur les pages de catégorie n’affiche pas les widgets de produit
   * _Remarque à propos de la correction_ : le problème a été résolu en s’assurant que les entrées de produits de la catégorie supplémentaire liée au bloc CMS ont été enregistrées avec précision dans la base de données. Auparavant, il renvoyait un jeu de résultats vide lorsque la page d’aperçu de catégorie était demandée.
* _ACP2E-3122_ : le bouton [CLOUD] Charger l’image ne fonctionne pas
   * _Remarque de correction_ : avant que le bouton Charger l’image pour la bannière et le curseur de PageBuilder ne fonctionne pas comme prévu, et maintenant, lorsque vous appuyez dessus, le gestionnaire de fichiers local s’ouvre pour sélectionner l’image à charger.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2-page-builder/commit/476ef8ea>
* _ACP2E-3127_ : imagecreatetruecolor() : la #2 de l’argument ($height) doit être supérieure à 0. Impossible de charger une image spécifique
   * _Remarque de correction_ : résolution du problème provoquant des erreurs dans l’administration lors du chargement d’images d’une hauteur de 0 via la galerie de médias, et réussite de la synchronisation des ressources à l’aide de la commande de synchronisation. Auparavant, ne pouvait pas charger l’image via la galerie de médias et la commande de synchronisation échouait également lorsqu’une image spécifique se trouvait dans la galerie.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3154_ : Prototype.js Array.from en conflit avec l’API Google Maps
   * _Correction d’une remarque_ : les cartes Google sont désormais correctement rendues dans l’éditeur PageBuilder. Auparavant, une erreur Javascript empêchait le rendu correct des cartes Google.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3275_ : [Cloud - Le] curseur CMS ne reflète pas les dernières modifications
   * _Correction d’une remarque_ : le problème a été résolu en veillant à ce que la liste des curseurs soit actualisée tandis que l’événement d’enregistrement est déclenché sur l’écran de modification de la diapositive. Auparavant, cela se déclenchait et provoquait le problème.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3326_ : une erreur se produit dans la page CSM lorsque des blocs CMS sont insérés à l’aide du générateur de page dans un certain ordre
   * _Remarque sur la correction_ : Auparavant, sur certaines versions de PHP et OS (Linux), le rendu des blocs qui référençaient d’autres blocs cms via PageBuilder aurait échoué avec une erreur « Une erreur inconnue s’est produite. Veuillez réessayer.&quot;. Désormais, le contenu des blocs cms est correctement rendu dans un contenu contrôlé par PageBuilder.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3388_ : [les blocs dynamiques Cloud] ne fonctionneront pas correctement
   * _Remarque correctif_ : les segments de clients connectés sont désormais effacés après la déconnexion, ce qui empêche la session d’invité d’hériter des segments précédemment connectés
* _ACP2E-3428_ : échec de l’aperçu du modèle Pagebuilder pour le contenu volumineux
   * _Remarque correctif_ : Un contenu volumineux entraînait un élément de canevas dépassant les limites du navigateur et renvoyait une valeur incorrecte, ce qui cassait le code principal (impossible de décoder correctement l’image). Ce problème a été corrigé en limitant la taille de la zone de travail à la limite du navigateur universel.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2-page-builder/commit/adfb1747>
* _ACP2E-3430_ : Dernières mises à jour de sécurité avec TinyMCE 7 taille de police manquante
   * _Correction d’une remarque_ : la taille de police et les sélecteurs de famille de polices sont désormais disponibles dans l’éditeur de WYSIWYG. Avant ce correctif, avec TinyMCE 7, ils n’étaient pas disponibles dans l’interface de l’éditeur.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d50f6b5d>, <https://github.com/magento/magento2-page-builder/commit/2c2f7a0e>
* _ACP2E-3483_ : taille de police de l&#39;éditeur TinyMCE 7 dans l&#39;administrateur en PT et non en PX. Veuillez clarifier
   * _Remarque sur la correction_ : avant la correction, vous ne pouviez pas spécifier la taille de police en px dans les zones WYSIWYG. Vous pouvez maintenant définir la taille de la police en px au lieu de pt.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/3f12d152>, <https://github.com/magento/magento2-page-builder/commit/20aa5d7a>
* _ACP2E-3490_ : le type de contenu du produit dans Page Builder est réduit sans messages corrects
   * _Remarque sur la correction_ : avant la correction, le code HTML de l’aperçu n’était pas généré correctement lorsqu’il n’y avait aucun produit dans le widget. Désormais, la réponse vide est correctement générée et le widget Products s’affiche correctement dans l’aperçu.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/3f12d152>, <https://github.com/magento/magento2-page-builder/commit/20aa5d7a>
* _ACP2E-3534_ : [page builder]l’ajout de la liste de produits au bloc génère des erreurs
   * _Remarque de correction_ : l’ajout actuel d’une liste de produits groupée au bloc via le générateur de page ne génère pas d’erreurs
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/344fce23>

### Contenu, SEO

* _ACP2E-2870_ : la hiérarchie de page CMS peut entraîner des problèmes de réécriture d’URL
   * _Remarque de correction_ : auparavant, pour la réécriture d’URL permanente personnalisée pour les pages racine autres que le site web, la redirection à l’infini et la page n’était jamais chargée. Une fois ce correctif appliqué, la réécriture d’URL personnalisée pour la page racine non site web fonctionne comme prévu et aucune boucle de redirection ne se produit.

### Contenu, évaluation et aperçu

* _ACP2E-2979_ : la règle de prix de catalogue ne s’affiche pas lorsqu’elle est définie pour la planification avec des blocs dynamiques
   * _Remarque de correction_ : le système affiche désormais correctement le contenu dynamique associé aux règles de prix de catalogue planifiées sur la page des détails du produit. Auparavant, le chargement du contenu dynamique échouait lorsque les règles de prix de catalogue étaient planifiées.

### Client/Clients

* _AC-12162_ : front-end - la validation de la date de naissance échoue dans la page de création du client
   * _Remarque à propos de la correction_ : assurez-vous que toute validation fonctionne après la mise à niveau de la dépendance du système moment.js vers la dernière version mineure
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-13060_ : Segment client > Condition > Historique des produits* > « Le produit a été consulté » ne fonctionne pas
   * _Remarque de correction_ : le système affiche désormais correctement les clients enregistrés correspondants dans la condition « Le produit a été consulté » sous Segments client, lorsque la condition est remplie. Auparavant, même lorsque la condition était remplie, le nombre de clients enregistrés appariés restait à zéro.
* _AC-8499_ : le champ de texte Région n’est pas réinitialisé lorsque la liste déroulante Pays est modifiée
   * _Correction de la note_ : le système réinitialise désormais le champ de texte Région lorsque le pays est modifié dans le menu déroulant, en s’assurant que les valeurs précédentes ne persistent pas. Auparavant, la modification du pays de la liste déroulante ne réinitialisait pas le champ Région, ce qui entraînait la conservation de la dernière valeur enregistrée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/3ea26621>
* _AC-9240_ : la suppression d’un client ne nettoie pas toutes les données de session du navigateur sur Storefront pour le client connecté et supprimé
   * _Remarque de correction_ : la suppression d’un client nettoie désormais toutes les données de session du navigateur du storefront pour les clients connectés et supprimés comme prévu. L’acheteur peut continuer à faire des achats et son navigateur traite sa session comme une session d’invité. Auparavant, lorsque le compte client d’un acheteur connecté était supprimé de l’administration, le navigateur de l’acheteur générait des erreurs JavaScript.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/7d5e3906>

### Framework

* _AC-10037_ : [Question]Configuration de type non utilisée dans `app/code/Magento/Translation/etc/di.xml`
   * _Remarque de correction_ : le système supprime désormais les dépendances inutilisées dans la configuration, améliorant ainsi la propreté et l’efficacité globales du code. Auparavant, il y avait des dépendances inutilisées dans la configuration qui ne contribuaient à aucune fonctionnalité.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38030>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38064>
* _AC-10654_ : V1/customers/password endpoint question/problème
   * _Remarque de correction_ : le système respecte désormais les contraintes définies dans l’interface utilisateur graphique de gestion lors du traitement des demandes de changement de mot de passe via l’API, empêchant tout abus potentiel de la fonction de réinitialisation du mot de passe. Auparavant, l’API pouvait traiter les demandes de changement de mot de passe en dehors des règles définies dans l’interface utilisateur graphique de gestion, ce qui pouvait permettre de disposer d’un flux constant d’e-mails de réinitialisation si des e-mails valides étaient connus.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38238>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10738_ : la configuration du vernis n’exclut pas tous les paramètres marketing
   * _Remarque de correction_ : le système exclut désormais correctement tous les paramètres marketing courants dans la configuration de Varnish, ce qui garantit un suivi et des analyses précis. Auparavant, certains paramètres marketing tels que gad_source, srsltid et msclkid n’étaient pas exclus, ce qui entraînait des inexactitudes potentielles dans la collecte des données.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38298>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/39188>
* _AC-10838_ : processus d’indexation des erreurs du processus d’index de recherche catalogue
   * _Note de correction_ : Le système exécute maintenant correctement la commande de réindexation sans rencontrer d&#39;erreur, quelle que soit la version libxml compilée avec PHP. Auparavant, l&#39;exécution de la commande re-index provoquait une erreur de type « Erreur de processus d&#39;index de recherche de catalogue pendant le processus d&#39;indexation » lorsque PHP était compilé avec certaines versions de libxml.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38254>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38553>, <https://github.com/magento/magento2/commit/0574ac23>
* _AC-10941_ : ajout de filtres created_at, status et grand_total à la requête Commandes client et correction de plusieurs échecs de filtres
   * _Remarque sur la correction_ : le système prend désormais en charge l’utilisation des filtres created_at, status et grand_total dans les requêtes Commandes client et a résolu un problème en raison duquel plusieurs filtres n’étaient pas appliqués correctement. Auparavant, le système ne prenait pas en charge ces filtres et ne pouvait pas les appliquer tous lorsque plusieurs d’entre eux étaient utilisés dans une requête.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38392>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/36949>
* _AC-10991_ : inondation aléatoire de requêtes provenant de blocs de ventes croisées / de ventes incitatives et d’indexation des prix
   * _Remarque à propos de la correction_ : le système optimise désormais les requêtes provenant des blocs de ventes croisées, de montée en gamme et connexes, ce qui améliore les performances et empêche le site de tomber en panne en raison de requêtes excessives. Auparavant, le système pouvait être surchargé de requêtes provenant de ces blocs, ce qui provoquait des ralentissements importants et pouvait entraîner l’arrêt du site.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/36667>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38050>
* _AC-11423_ : Exception : Avertissement : Tentative d&#39;accès au décalage de tableau en... -> Calendar.php depuis la mise à niveau vers ICU 74.1 (PHP Intl)
   * _Remarque de correction_ : Commerce ne consigne plus l’exception suivante dans le fichier exception.log chaque fois qu’un acheteur ou un commerçant visite le storefront ou l’administrateur : `main.CRITICAL: Exception: Warning: Trying to access array offset on value of type null in /vendor/magento/framework/View/Element/Html/Calendar.php on line 114 in /vendor/magento/framework/App/ErrorHandler.php:62`. [GitHub-38214](https://github.com/magento/magento2/issues/38214)
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38214>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38364>
* _AC-11476_ : [Problème] résoudre les problèmes liés aux données client lorsque le formulaire contient un élément nommé `method`
   * _Remarque de correction_ : le système identifie désormais correctement l’attribut « method » dans les envois de formulaire, même lorsqu’un élément nommé « method » est présent dans le formulaire. Cela garantit un traitement précis des données client. Auparavant, si un élément de formulaire était nommé « méthode », cela interférait avec l’identification de l’attribut « méthode » dans les envois de formulaire, ce qui entraînait des problèmes potentiels avec la gestion des données client.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38484>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38449>
* _AC-11489_ : [Problème] Corrigez PHPDocs pour \Magento\Framework\Data\Collection::getItemById
   * _Remarque de correction_ : les PHPDocs de la méthode \Magento\Framework\Data\Collection::getItemById ont été mis à jour afin d’inclure la valeur null comme type de retour possible, ce qui résout les problèmes liés aux outils d’analyse statique. Auparavant, les PHPDocs de la méthode ne spécifiaient pas la valeur null comme type de retour possible, ce qui entraînait des avertissements ou des erreurs dans l’analyse statique lorsque la méthode était utilisée dans des instructions conditionnelles.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38485>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38439>
* _AC-11592_ : [Problème] Autoriser uniquement les préférences valides pendant la configuration:di:la compilation
   * _Remarque de correction_ : le système renvoie désormais une erreur lors de la commande setup:di:compile si une préférence est créée pour une classe qui n’existe pas ou qui est spécifiquement exclue, en s’assurant que seules des préférences valides sont autorisées. Auparavant, ces scénarios échouaient en silence, ce qui rendait inutiles les modules externes associés aux classes d’origine.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38517>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/33161>
* _AC-11651_ : Magento tente de modifier la propriété en lecture seule dans la méthode __wakeup de LoggerProxy
   * _Remarque de correction_ : le système permet désormais de modifier les propriétés précédemment en lecture seule dans la méthode de réveil __wakeup de LoggerProxy, assurant ainsi un fonctionnement fluide sans forcer les utilisateurs à employer une solution de contournement. Auparavant, une tentative de réaffectation de la valeur d’une propriété en lecture seule dans la méthode __wakeup de LoggerProxy provoquait des problèmes.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38526>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-11681_ : [Numéro] AC-2039 AC-1667 Mise à niveau TinyMCE références
   * _Correction de la remarque_ : mise à jour de la dernière version de tinymce dans composer.json
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38533>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/36543>, <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-11696_ : ChangelogBatchWalker ne fonctionne pas dans plusieurs threads
   * _Remarque de correction_ : le système prend désormais en charge le branchement de processus pour l’indexation MView, ce qui évite les erreurs lors de l’exécution de l’indexeur lorsque le système fonctionne sur plusieurs threads. Auparavant, l’exécution du ChangelogBatchWalker sur plusieurs threads entraînait la suppression des tables utilisées par d’autres threads, provoquant une erreur lors de l’exécution de l’indexeur.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38246>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38248>
* _AC-11781_ : [Problème] Renommez une variable nommée de manière incorrecte
   * _Remarque de correction_ : le système nomme désormais correctement la variable contenant le montant qui peut toujours être remboursé, ce qui évite toute confusion lors du débogage. Auparavant, cette variable était incorrectement nommée totalRefund, ce qui pouvait entraîner des malentendus pour les développeurs.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38609>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/36205>
* _AC-11809_ : [Problème] Transmettez les attributs personnalisés au lien actuel via XML
   * _Remarque de correction_ : le système permet désormais de transmettre des attributs personnalisés au lien actif via XML, en veillant à ce que ces attributs s’affichent correctement même lorsque le lien est la page active. Auparavant, les attributs personnalisés n’étaient pas affichés pour le lien de la page en cours, car la méthode getAttributesHtml() n’était pas utilisée pour le lien en cours.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38500>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/30070>
* _AC-11819_ : le cache FPC intégré est rompu dans la version 2.4.7 pour certaines configurations
   * _Remarque de correction_ : le système met désormais correctement en cache les pages lorsque le paramètre MAGE_RUN_CODE est défini, garantissant ainsi des performances optimales. Auparavant, les pages n’étaient pas mises en cache dans ces conditions, ce qui entraînait des problèmes de performances potentiels.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38626>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38646>, <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-11829_ : [Problème] Correction des incohérences de gestion des exceptions entre les modes développeur et production
   * _Remarque corrigée_ : Le système gère désormais systématiquement les exceptions entre les modes développeur et production, empêchant ainsi une redirection inattendue vers la page de connexion lorsqu’une exception est générée. Auparavant, une incohérence dans la gestion des exceptions pouvait provoquer une redirection vers la page de connexion en mode de production au lieu d’afficher le message d’exception.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38639>
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/pull/37712>
* _AC-11852_ : Remplacer la traduction &#39;PayPal compte&#39; dans token_list.phtml
   * _Correction de note_ : le système désigne désormais la section pour les méthodes de paiement de compte pouvant être segmentées en unités lexicales comme étant « Compte » au lieu de « Compte PayPal » sur la page Modes de paiement stockés , ce qui le rend plus représentatif de sa fonction. Auparavant, cette section était spécifiquement étiquetée comme « Compte PayPal », ce qui était trompeur lorsque d&#39;autres méthodes de paiement de compte jetable ont été ajoutées.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/35622>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37959>
* _AC-11874_ : la rétrocompatibilité a été perdue sur la classe Magento\Catalog\Model\ProductRepository
   * _Remarque de correction_ : la classe ProductRepository conserve désormais la rétrocompatibilité en restaurant la classe Initialization Helper en tant que deuxième paramètre, en veillant à ce que les modules s’étendant à partir de cette classe fonctionnent comme prévu. Auparavant, la suppression de l&#39;Assistant d&#39;initialisation du constructeur dans la classe ProductRepository entraînait une perte de rétrocompatibilité, forçant les utilisateurs à employer une solution de contournement.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38669>
* _AC-11905_ : [Problème] Déploiement de contenu statique - Erreur de type
   * _Remarque de correction_ : le système gère désormais correctement les fichiers LESS vides lors du déploiement du contenu statique, affichant un message d’erreur « Le fichier LESS est vide ». Auparavant, une erreur de type incorrect était générée lors de la détection d’un fichier LESS vide lors du déploiement.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38682>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38683>
* _AC-12002_ : [Problème] [Affichage] Suppression de l’espace supplémentaire dans le lien et la balise du script
   * _Remarque à propos de la correction_ : le système s’assure désormais qu’il n’y a pas d’espace supplémentaire dans les balises de lien et de script, fournissant ainsi un code plus propre et plus efficace. Auparavant, il était possible de trouver des espaces doubles entre les attributs dans les balises de lien et de script.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/32920>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/32919>
* _AC-12127_ : [Problème] éviter une boucle infinie de mauvaise configuration
   * _Remarque de correction_ : le système évite désormais une boucle infinie en empêchant le mappage autoréférentiel dans les configurations de type virtuel. Cela permet de s’assurer que l’application n’est pas bloquée dans une boucle sans fin lors de la tentative de déréférencement d’un nœud autoréférentiel. Auparavant, si une configuration de type virtuel était auto-référentielle, l’application tournait indéfiniment.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38822>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38794>
* _AC-12299_ : gestionnaire d’objets non utilisé pour Magento\Csp\Model\Mode\Data\ModeConfigured
   * _Remarque de correction_ : le système utilise désormais correctement le Gestionnaire d’objets lors de la création de l’objet ModeConfigured, ce qui permet d’utiliser des modules externes sur cet objet. Auparavant, le Gestionnaire d&#39;objets n&#39;était pas utilisé, empêchant l&#39;application de modules externes à l&#39;objet ModeConfigured.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38875>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38886>
* _AC-12540_ : commentaire de bloc de document inexact dans les alertes de stock de produits et de prix
   * _Corriger la note_ : le commentaire du bloc doc pour la méthode deleteCustomer dans les alertes de stock de produits et de prix a été corrigé afin de refléter précisément le fait que la méthode supprime du site web toutes les alertes de produit ou de prix de stock associées à un client et à un site web donnés, et non au client. Auparavant, le commentaire indiquait à tort que la méthode était destinée à supprimer un client du site web.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38939>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/39001>
* _AC-12594_ : [Problème] utilisez la configuration compilée pour les données générées au lieu de la configuration générale.
   * _Remarque de correction_ : le système utilise désormais la configuration compilée pour les données générées au lieu de la configuration générale, ce qui réduit le transfert réseau et la surcharge des données qui dépendent d’une certaine version du code. Cette modification empêche le remplacement du cache dans les instances partagées lors de la permutation de conteneur, ce qui améliore la stabilité et réduit les temps d’arrêt. Auparavant, certaines classes principales utilisaient le type de configuration partagé, ce qui pouvait entraîner le remplacement du cache ou des temps d’arrêt de l’application en raison de différences dans les versions de code sur plusieurs serveurs.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38785>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/29954>
* _AC-12597_ : [Problème] Supprimez les références aux fichiers d’extjs qui ont été supprimés dans e1ccdb...
   * _Remarque de correction_ : le système supprime désormais les références aux fichiers d’extjs qui ont été supprimés, éliminant ainsi les erreurs dans la console du navigateur et le fichier journal du système. Auparavant, ces références provoquaient des erreurs en raison de l’absence des fichiers référencés.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38960>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38951>
* _AC-12778_ : [Problème] Nettoyage mineur : correction d’une mauvaise utilisation de sprintf, il ne prend que 2 espaces réservés ici et w...
   * _Correction de la remarque_ : le système utilise désormais correctement la fonction sprintf avec le nombre approprié d’espaces réservés, ce qui améliore la propreté et la cohérence du code. Auparavant, la fonction sprintf était incorrectement utilisée avec un argument supplémentaire, ce qui ne provoquait aucun problème majeur, mais n’était pas l’utilisation correcte.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39062>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38628>
* _AC-12857_ : PHP 8.2.15 a supprimé l&#39;extension FTP
   * _Remarque de correction_ : le système inclut désormais l’extension FTP en tant que dépendance dans le fichier composer.json, ce qui garantit la réussite de la configuration des importations de fichiers CSV par FTP. Auparavant, une erreur était générée lors de la tentative de configuration des imports de fichiers CSV via FTP en raison de l’absence de l’extension FTP dans le package PHP.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39083>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/47b448e2>
* _AC-12869_ : [Problème] corrige les classes incorrectes référencées dans les modules Magento.
   * _Remarque de correction_ : le système référence désormais correctement les classes dans les modules, ce qui garantit un fonctionnement plus fluide et empêche les blocages dus à des classes inexistantes. Cela inclut un correctif de bugs dans les modules Indexer et Creditmemo, ainsi que l’implémentation de HttpGetActionInterface dans la classe PrintAction. Auparavant, des références de classe incorrectes entraînaient des erreurs et des blocages système potentiels, et certaines fonctionnalités, telles que le nom de fichier pour les fichiers PDF creditmemo et la réindexation des stocks, ne fonctionnaient pas comme prévu.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39126>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37784>
* _AC-12964_ : possibilité de définir la zone pour la commande de ligne de commande dev:di:info
   * _Remarque sur la correction_ : le système permet désormais aux développeurs de définir une zone pour la commande dev:di:info CLI, ce qui améliore le processus de développement et de débogage. Auparavant, cette commande ne pouvait afficher que les informations relatives à la zone GLOBAL.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38758>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38759>
* _AC-13149_ : [Problème] ajoutez la propriété isMultipleFiles au modèle d’élément de formulaire d’image
   * _Remarque sur la correction_ : ce correctif empêche le bouton « Parcourir pour trouver ou faire glisser l’image ici » de disparaître lorsqu’une image est ajoutée à un élément de formulaire d’image à plusieurs fichiers.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39219>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/36325>
* _AC-13247_ : setup:upgrade échoue avec la version 11.4 de MariaDB en raison de changements de jeu de caractères et de classement
* _AC-13279_ : [Problème] supprimez tous les paramètres marketing get pour réduire le cache
   * _Remarque à propos de la correction_ : le système supprime désormais tous les paramètres marketing get pour optimiser l’utilisation du cache, reflétant la logique utilisée lorsque le vernis est utilisé. Auparavant, ces paramètres pouvaient entraîner un gonflement du cache et une réduction des performances.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39266>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/39099>
* _AC-13345_ : [Problème] [PHPDOC] Correction d’un phpdoc incorrect Magento\Directory\Model\AllowedCountries::getAllowedCountries()
   * _Remarque à propos de la correction_ : la PHPDoc pour la méthode AllowedCountries::getAllowedCountries() a été corrigée afin de fournir des informations précises, ce qui améliore la clarté et l’utilité de la documentation. Auparavant, la PHPDoc de cette méthode contenait des informations incorrectes, ce qui pouvait entraîner une confusion ou une mauvaise utilisation de la méthode.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39246>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/39241>
* _AC-13348_ : [Problème] Supprime du code pour les versions PHP que nous ne prenons plus en charge.
   * _Correction de note_ : suppression du code des versions PHP qui ne sont plus prises en charge dans Magento
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39361>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/39202>
* _AC-13417_ : [Problème] Rendre l&#39;adaptateur ImageMagick compatible avec php8 (Conversion implicite de float en int)
   * _Note de correction_ : Le système assure maintenant la compatibilité avec PHP8 en gérant correctement les nombres flottants lors du calcul des dimensions de l’image, évitant ainsi toute erreur due à la conversion implicite du float en int. Auparavant, le calcul des dimensions de l’image pouvait entraîner des nombres flottants qui, lorsqu’ils étaient implicitement arrondis, provoquaient une erreur.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39402>
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/pull/37362>
* _AC-13537_ : [Problème] [PHPDOC] Correction incorrecte phpdoc Magento\Framework\App\Config\ScopeConfigInterface
   * _Remarque de correctif_ : Cette mise à jour corrige les annotations PHPDoc dans le Magento\Framework\App\Config\ScopeConfigInterface pour refléter avec précision le type de l’argument $scopeCode pour les méthodes getValue et isSetFlag.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39492>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/39199>
* _AC-13725_ : Magento\Framework\Filesystem\Driver\Http dépend de l’expression de raison OK
   * _Correction de la note_ : suppression de la vérification de l’expression « OK » de Magento\Framework\Filesystem\Driver\Http::isExists
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39546>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/39558>
* _AC-13810_ : l’indexeur de grille client ne fonctionne pas correctement en mode Mise à jour par planification .
   * _Remarque sur la correction_ : la grille cliente précédente était mise à jour instantanément, mais après la correction, la grille cliente est mise à jour après l’exécution de cron, mais elle n’est pas répercutée instantanément.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1da9ba6f>
* _AC-6754_ : erreur de frappe sur un fichier js.
   * _Remarque sur la correction_ : le système utilise désormais correctement le terme « abonnés » dans le fichier JavaScript, assurant ainsi le bon fonctionnement des fonctions associées. Auparavant, une erreur typographique dans le fichier JavaScript entraînait l’utilisation incorrecte du terme « abonnés ».
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/36163>
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/pull/36171>
* _AC-8353_ : [Problème] Supprimer la balise `@author` interdite
   * _Remarque à propos de la correction_ : le système respecte désormais les normes de codage en supprimant la balise `@author` interdite de certains modules, ce qui garantit un code plus propre et plus normalisé. Auparavant, la balise `@author` était présente dans certains modules, ce qui était contraire aux normes de codage établies.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37253>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37003>
* _AC-8356_ : [Problème] Supprimez la balise `@author` interdite du `Magento_Customer` (partie 2)
   * _Remarque à propos de la correction_ : le système respecte désormais la norme de codage en supprimant la balise `@author` interdite de certains modules, ce qui garantit un code plus propre et plus normalisé. Auparavant, la balise `@author` était présente dans certains modules, ce qui était contraire aux normes de codage établies.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37250>
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/pull/37000>
* _AC-8659_ : L’espace dans la syntaxe editorconfig enfreint la règle pour [{composer,auth}.json]
   * _Remarque du correctif_ : Le système applique maintenant correctement un retrait de 4 espaces au compositeur et aux fichiers auth.json, à la suite d’une correction d’une erreur de syntaxe dans editorconfig. Auparavant, en raison d’un espace dans la syntaxe editorconfig, ces fichiers étaient incorrectement formatés avec un retrait de 2 espaces.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37394>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37395>
* _AC-8662_ : [Problème] d’amélioration de la journalisation des erreurs cron
   * _Remarque de correction_ : le système capture et consigne désormais à la fois STDERR et STDOUT pour les processus cron, fournissant ainsi des informations de diagnostic précieuses dans les cas où les processus cron échouent. Auparavant, tous les messages d’erreur des processus cron n’étaient pas enregistrés et STDERR et STDOUT pour les groupes cron s’exécutant dans des processus distincts étaient perdus.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37453>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/32690>
* _AC-8984_ : [Problème] ajoute quelques couleurs supplémentaires à la sortie de certaines commandes de l’interface de ligne de commande de configuration
   * _Remarque de correction_ : le système ajoute désormais plus de couleurs à la sortie de certaines commandes de l’interface de ligne de commande (CLI) de la configuration, améliorant ainsi la lisibilité et l’expérience utilisateur. Auparavant, la sortie de ces commandes était plus difficile à lire en raison de l’absence de différenciation des couleurs.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/29335>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/29298>
* _AC-9630_ : la mise à niveau de Magento réinitialise general/region/state_required lorsqu’un nouveau pays avec l’état/région requis est ajouté.
   * _Remarque de correction_ : le système ajoute désormais uniquement le pays modifié à la configuration « general/region/state_required » lorsqu’un nouveau pays avec les états obligatoires est ajouté, ce qui empêche toute interruption du code personnalisé qui suppose que la région est désactivée. Auparavant, l’ajout d’un nouveau pays avec les états obligatoires réinitialisait la configuration « general/region/state_required » aux pays par défaut avec l’état obligatoire, ce qui pouvait entraîner l’interruption de l’activité.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37796>
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/pull/38076>
* _AC-9712_ : Différence de moins de compilation entre php et la bibliothèque nodejs (grunt) avec des expressions compliquées `calc`
   * _Note de correction_ : Correction de la différence en moins de compilation entre php et la bibliothèque nodejs (grunt) après la mise à jour wikimedia / less.php :^5.x
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37841>
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/b34c0a75>
* _ACP2E-2692_ : l’erreur « Table de base ou vue introuvable » se produit lorsque l’indexation partielle est exécutée
   * _Remarque de correction_ : la réindexation partielle fonctionne désormais correctement avec le journal des modifications volumineux en cas de connexion à la base de données secondaire
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2844_ : Problèmes après la mise à niveau de MariaDB vers la version 10.5.1 ou ultérieure
   * _Remarque correctif_ : correction du problème lorsque les valeurs datetime d’une base de données étaient converties en 0000-00-00 00 00:00:après la mise à niveau de Mysql
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2855_ : non-correspondance des types dans la comparaison des données lors de la vérification des modifications apportées aux données
   * _Remarque sur la correction_ : Auparavant, l’objet d’enregistrement était appelé à chaque fois sans modification des données (pour tout champ de données numérique, comme int/float/double). Cela déclenche l’indicateur _hasDataChanges sur true et appelle la fonction d’enregistrement. Une fois que ce correctif est appliqué, la fonction d’enregistrement n’appelle que si les données sont modifiées. La valeur des données pour int/float/double-check avec la valeur transmise à la fonction et effectue une correspondance de type stricte.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2959_ : [l’importation dans le cloud] ne peut pas être utilisée avec le répertoire var
   * _Remarque sur la correction_ : le produit peut être importé avec succès, quel que soit le nom du fichier.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2966_ : dans ipad mini, le menu et l’en-tête se chargent comme des appareils mobiles, mais plutôt comme des ordinateurs de bureau.
   * _Remarque de correction_ : le système traite désormais les appareils d’une largeur de 768 px comme des ordinateurs de bureau, en s’assurant que le menu et l’en-tête se chargent correctement. Auparavant, les appareils d’une largeur de 768 pixels étaient traités comme des appareils mobiles, ce qui entraînait le chargement du menu et de l’en-tête dans une vue mobile.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/35b1b1da>, <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-3046_ : erreur de table ou d&#39;affichage de base introuvable lors de l&#39;exécution de mview cron lors d&#39;une opération DDL
   * _Remarque de correction_ : le système gère désormais correctement les opérations de mise à jour de la base de données pendant que la mise à jour mview s&#39;exécute en arrière-plan, ce qui empêche l&#39;apparition d&#39;erreurs « Table de base ou vue introuvable ». Auparavant, certaines opérations de mise à jour de la base de données pouvaient entraîner l’erreur « Table de base ou vue introuvable » si la mise à jour de la mview était exécutée en même temps.
* _ACP2E-3230_ : la modification de la longueur des colonnes via db_schema.xml ne fonctionne pas en cas de clés étrangères
   * _Remarque de correction_ : la modification d’une colonne avec une clé étrangère via un schéma déclaratif ne génère désormais pas d’erreurs avec MariaDB
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3361_ : certains enregistrements de relations sont enregistrés dans la base de données lorsque l&#39;enregistrement de commande est enregistré
   * _Remarque sur la correction_ : avant la correction, les requêtes UPDATE inutiles étaient déclenchées, ce qui peut avoir un impact sur les performances. Après le correctif, les requêtes UPDATE inutiles ont été éliminées.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3375_: [CLOUD] L’administration rencontre de nombreuses erreurs JavaScript dans la console
   * _Remarque de correction_ : auparavant, dans le panneau d’administration, il y avait de nombreuses erreurs JavaScript dans la console. Désormais, dans le panneau d’administration, il n’y aura aucune erreur JavaScript dans la console et toutes les fonctions JavaScript par défaut s’exécuteront correctement sans problème.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3387_ : [Cloud] Magento : le message de file d’attente a été supprimé
   * _Remarque de correction_ : les messages de la file d’attente sont désormais correctement effacés. Avant la correction, étant donné que le système de file d’attente SQL était utilisé, les nouveaux messages pouvaient être supprimés si le message de la file d’attente de nettoyage était en cours d’exécution au même moment.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3537_ : les entrées de clé de cache correspondantes ne sont pas disponibles dans les balises de cache, donc le nettoyage du cache ne fonctionne pas correctement
   * _Remarque de correction_ : le mode LUA est désormais activé par défaut pour le nettoyeur de la mémoire cache Redis afin d’empêcher les conditions de concurrence.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a52ff98f>
* _ACP2E-3681_ : la valeur MAGENTO_DC_INDEXER__USE_APPLICATION_LOCK est ignorée
   * _Remarque sur la correction_ : après la correction, une variable ENV définie sur « false » sera traitée comme booléenne false, et non comme chaîne « false ».
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/982b1c42>

### Framework, GraphQL

* _AC-7976_ : [problème] prise en charge des types scalaires personnalisés pour le schéma GraphQL
   * _Remarque de correction_ : le système prend désormais en charge les types scalaires personnalisés pour le schéma GraphQL, ce qui permet aux développeurs et développeuses de définir des types scalaires personnalisés et des implémentations. Cette fonction peut s’avérer particulièrement utile pour exprimer des valeurs qui peuvent nécessiter une validation, telles qu’HTML, les e-mails, les URL, les dates, etc., ainsi que pour les cas plus avancés tels que les attributs EAV. Auparavant, le système ne prenait pas en charge le traitement des types scalaires personnalisés dans GraphQL.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/36877>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/34651>, <https://github.com/magento/magento2/commit/0574ac23>

### Framework, Produit

* _AC-13011_ : les rapports EE 2.4.8-beta1 ne sont pas générés en raison d’une exception magento

### Framework, framework d’interface utilisateur

* _ACP2E-3324_ : possibilité de remplacer la valeur de configuration même si elle est verrouillée
   * _Remarque sur la correction_ : auparavant, la configuration de conception ne pouvait pas être définie via la commande bin/magento config:set et les valeurs verrouillées pouvaient être modifiées en manipulant le formulaire qui les affichait. Après la correction, les valeurs verrouillées définies depuis l’interface en ligne de commande avec —lock-env ou —lock-conf ne peuvent plus être mises à jour.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/55615e61>

### GraphQL

* _AC-11729_ : Magento_GraphQl exécute le traitement des en-têtes même si la valeur de l’en-tête n’est pas validée
   * _Remarque de correction_ : le système garantit désormais que le traitement de l’en-tête n’est exécuté qu’une seule fois et uniquement si la valeur de l’en-tête est validée, ce qui renforce la sécurité et empêche les vulnérabilités potentielles. Auparavant, le traitement de l’en-tête était exécuté même si la valeur de l’en-tête n’était pas validée, ce qui entraînait des vulnérabilités potentielles et un comportement inattendu en raison du double traitement des valeurs d’en-tête.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-8951_ : Les options de la carte cadeau physique n&#39;ont pas le bon ordre de tri
   * _Correction de la remarque_ : le système trie désormais correctement les options des produits de carte cadeau physique lors de l’interrogation via GraphQL, en assurant un rendu cohérent avec le thème Luma. Auparavant, l’ordre de tri était incorrect en fonction du thème Luma, ce qui entraînait un affichage et un ordre incorrects des options telles que le nom de l’expéditeur, le nom du destinataire et le montant.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1bafc571>
* _AC-9157_ : [GraphQL] le cache du résolveur est invalidé lors de la création/modification/déplacement/suppression d’une mise à jour d’évaluation
   * _Remarque de correction_ : le système s’assure désormais que le cache du résolveur n’est pas invalidé lors de la création, de la modification, du déplacement ou de la suppression d’une mise à jour d’évaluation, mais uniquement lorsque la mise à jour d’évaluation est appliquée à l’entité. Auparavant, le cache du résolveur était invalidé prématurément, avant même l’application de la mise à jour de l’évaluation, ce qui entraînait des invalidations inutiles du cache.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2642_ : cache rapide non effacé pour la mise à jour de l&#39;évaluation du contenu
   * _Remarque de correction_ : désormais, GraphQL avec le cache de réponse de contenu PageBuilder est invalidé lorsque les entités liées au contenu PageBuilder sont mises à jour.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2653_ : désactivation de Layered Navetion - ne supprime pas l’agrégation de Graphql
   * _Remarque à propos de la correction_ : le problème a été corrigé après l’application de la vérification lors de la demande d’une recherche de produit avec des agrégations de catégories par le biais d’une requête GraphQL lorsque le paramètre de configuration d’administration de « Catalogue > Navigation superposée > Afficher le filtre de catégorie » est activé.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2928_ : l’appel de produits GraphQL contenant le filtre de prix {from:« 0 »} ne renvoie aucun résultat
   * _Remarque sur la correction_ : auparavant, la recherche de produits GraphQL avec un filtre de prix nuls ne renvoyait aucun résultat en raison d’une exception renvoyée. Désormais, la recherche renvoie les résultats attendus.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2974_ : les traductions des attributs de retour client ne sont pas reflétées dans l’API GraphQL pour StoreView respectif
   * _Remarque de correction_ : les traductions des attributs de retour client sont reflétées dans l’API GraphQL pour l’affichage de magasin correspondant.
Auparavant, les attributs de retour client pour les StoreView respectifs n’étaient pas reflétés dans l’API GraphQL.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3128_ : appel GraphQL [Cloud] rompu pour getPurchaseOrder avec devis de nœud
   * _Remarque de correction_ : l’appel GraphQL de bon de commande pourra exécuter la tâche sans rencontrer d’erreur de serveur interne.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3184_ : [Cloud] produits configurables non affichés sur le site de production si le produit n’est pas activé dans « Toutes les vues de la boutique »
   * _Remarque de correction_ : le système affiche désormais correctement les produits configurables sur le site même si le produit n’est pas activé dans « Toutes les vues de la boutique », mais est activé dans des portées d’affichage de boutique spécifiques.
Auparavant, si un produit était désactivé dans « Toutes les vues de la boutique » et activé uniquement dans des portées d’affichage de boutique spécifiques, les attributs de produit ne s’affichaient pas correctement dans la réponse GraphQL, ce qui entraînait un affichage incorrect du produit.
   * _Contribution du code GitHub_ : <https://github.com/magento/inventory/commit/3f300077>
* _ACP2E-3190_ : [Cloud] Produits Graphql présentant une erreur lorsque le même produit simple a été affecté à plusieurs produits configurables
   * _Remarque de correction_ : auparavant, avec des produits configurables distincts utilisant le même produit simple, grapQL renvoyait une erreur. Après application de ce correctif, différents produits configurables avec le même produit simple, grapQL renvoie le résultat sans erreur.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3215_ : [Cloud] problème d’authentification des utilisateurs et d’accès aux jetons intersites dans la configuration multisite
   * _Remarque à propos de la correction_ : les requêtes Informations du client et Panier GraphQl dans la configuration multisite vérifient si le client se trouve sur un site web autre que celui par défaut.
La requête précédente fonctionnait sans s’assurer que le client existe sur un site web autre que celui par défaut dans la configuration multisite.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3253_ : la pagination des éléments du panier GraphQL V2 ne fonctionne pas correctement
   * _Remarque à propos de la correction_ : le problème a été résolu en transmettant la valeur correcte de l’argument de page actuel dans la requête de collection. Auparavant, une valeur incorrecte était transmise pour définir la page active, ce qui provoquait le problème.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3255_ : la valeur du modèle [GRAPHQL] doit être spécifiée lors de l’obtention du panier client
   * _Remarque sur la correction_ : la requête « customerCart » de GraphQL peut désormais créer un panier vide même si le devis n’est pas disponible dans la base de données. Auparavant, cette opération échouait en raison de problèmes de validation du pays lors de la création du panier vide.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3380_ : les éléments de liste de souhaits [GraphQl] sont visibles via GraphQl, mais pas sur storefront
   * _Remarque sur la correction_ : les produits de liste de souhaits n’étaient pas correctement répertoriés lorsqu’ils étaient demandés via GraphQL. Désormais, les produits de la liste de souhaits sont filtrés en fonction du contexte de magasin fourni.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/55615e61>
* _ACP2E-3404_ : [GraphQL] Réinitialiser l&#39;incohérence de l&#39;e-mail de mot de passe entre le contenu et l&#39;objet/lien
   * _Remarque à propos de la correction_ : le problème a été résolu en simulant le magasin correct où le compte du client est enregistré lors de l’envoi de la demande de réinitialisation de mot de passe, quel que soit le magasin du site web.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3419_ : la requête GraphQL de produits [Cloud] renvoie les produits associés non affectés au site web actuel
   * _Remarque sur la correction_ : auparavant, pour les requêtes GraphQL, les produits associés à plusieurs magasins ne s’affichaient pas correctement pour les requêtes de produit. Une fois ce correctif appliqué, pour les produits , graphQL interroge les produits associés à plusieurs magasins et les affiche en conséquence.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3447_ : l’utilisation d’un ID de magasin incorrect dans l’en-tête GraphQL entraîne une erreur de mémoire fatale
   * _Remarque de correctif_ : l’envoi d’un code de magasin incorrect dans la requête GraphQL n’entraîne plus une consommation excessive de mémoire.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3467_ : [réponse Cloud] 500 à la réponse Graphql vide sur 2.4.7
   * _Remarque correctif_ : Après la correction, les demandes graphql non valides ne seront pas enregistrées dans le fichier exception.log.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3492_ : [Cloud] problèmes liés à l’API Graphql
   * _Remarque sur la correction_ : avant la correction à l’aide du serveur d’applications Graphql, la demande d’adresse du client ne renvoyait pas les données les plus récentes.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3505_ : le produit désactivé apparaît toujours dans les articles liés, de montée en gamme et de vente croisée dans la requête grpahQL
   * _Remarque à propos de la correction_ : Graphql fournit désormais une réponse correcte pour les produits connexes, de montée en gamme et de vente croisée désactivés
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3647_ : [CLOUD] : erreur GraphQl Erreur de serveur interne placeOrder mutation
   * _Correction de la note_ : la mutation « placeOrder » avec les informations de code de coupon dans la requête ne renvoie plus d’erreur interne. La commande a été passée avec succès. Auparavant, il échouait avec « Erreur de serveur interne ».
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/982b1c42>
* _LYNX-426_ : Le discount_percentage n’est pas calculé pour les produits groupés à prix dynamique
   * _Remarque correctif_ : correction ajoutée pour discount_percentage de product.price_details n’affichant pas la valeur correcte pour les produits groupés avec prix dynamique activé et coupon de réduction appliqué.
* _LYNX-485_ : les produits groupés affichent toujours « IN_STOCK » lorsque l’un de ses produits groupés est en rupture de stock
   * _Remarque correctif_ : Résolution du problème où les produits groupés affichaient toujours « IN_STOCK » même lorsque l’un de leurs produits groupés était en rupture de stock.
* _LYNX-486_ : not_available_message et only_x_left_in_stock n’affiche pas le même stock disponible
   * _Remarque correctif_ : Résolution du problème en raison duquel la disponibilité des stocks des not_available_message et des only_x_left_in_stock n’était pas cohérente.
* _LYNX-488_ : champ original_row_total renvoi d’une valeur incorrecte
   * _Remarque correctif_ : Résolution du problème lié au champ original_row_total, qui renvoyait des valeurs incorrectes lorsque des options personnalisées étaient sélectionnées.
* _LYNX-503_ : la vignette groupée du produit doit s’afficher en fonction de la configuration.
   * _Remarque correctif_ : Résolution du problème pour s’assurer que la miniature du produit groupé est affichée en fonction des paramètres de configuration
* _LYNX-510_ : erreur lors de l’interrogation de selected_options dans OrderAddress
   * _Remarque de correction_ : AttributeSelectedOptions mis à jour sur custom_attributesV2 dans la réponse GraphQL d’adresse de commande.
* _LYNX-512_ : original_item_price n&#39;inclut pas les remises
   * _Corriger la note_ : a mis à jour original_item_price pour inclure les remises.
* _LYNX-530_ : le message Non disponible n&#39;indique pas la quantité en stock disponible
   * _Correction de la note_ : résolution du message d’erreur et du code d’erreur de la mutation AddProductsToCart pour s’aligner sur la configuration du message « non disponible »
* _LYNX-532_ : le statut « OUT_OF_STOCK » revient sur Simple avec des options personnalisées produits avec options à sélection multiple
   * _Remarque de correction_ : mise à jour du résolveur StockStatusProvider dans le package d’inventaire pour corriger le stock_status pour les produits simples avec des options personnalisées.
* _LYNX-533_ : erreur (GQL) : cart.itemsV2.items.product.custom_attributesV2 renvoie une erreur de serveur
   * _Remarque de correction_ : résolution de l’erreur de serveur qui se produisait lorsqu’une requête de panier incluait les attributs personnalisés d’un produit en ajoutant un produit sans attribut personnalisé.
* _LYNX-536_ : commandes/date_of_first_order renvoyant toujours la valeur null
   * _Correction de la note_ : correction du problème en raison duquel commandes > date_of_first_order renvoyait toujours la valeur null.
* _LYNX-544_ : le client ne doit pas pouvoir annuler une commande partiellement expédiée
   * _Corriger la note_ : une validation a été ajoutée pour empêcher les clients d&#39;annuler une commande partiellement expédiée.
* _LYNX-548_ : codes d&#39;erreur pour l&#39;annulation de la commande en fonction du message d&#39;erreur
   * _Corriger la note_ : les codes d’erreur pour l’annulation de la commande sont désormais basés sur le message d’erreur spécifique.
* _LYNX-581_ : revenez aux propriétés liées aux cookies du privé au protégé.
   * _Correction d’une note_ : rétablit la visibilité des propriétés du constructeur de la classe Magento\Framework\App\PageCache\Version de privée à protégée
* _LYNX-600_ : augmentez la complexité maximale de requête GraphQL par défaut à 1 000.
   * _Remarque de correctif_ : augmentation de la complexité maximale par défaut des requêtes GraphQL de 300 à 1 000.
* _LYNX-620_ : GQL - itemsV2 > Total de la ligne d’origine, les prix des plages de prix sont renvoyés sous la forme de 0,00 $ pour les produits téléchargeables avec des options de fichier dont les prix sont distincts.
   * _Correction de la note_ : correction d’un problème en raison duquel les produits téléchargeables avec des options d’achat de lien distinctes activées renvoyaient 0 $ pour les articlesV2 > Total de la ligne d’origine, la plage de prix renvoyée était de 0,00 $ pour les produits avec des options de fichier ayant des prix distincts.
* _LYNX-711_ : schéma d’une table lors de la création d’une toute nouvelle version et lors de la mise à niveau
   * _Remarque de correction_ : correction d’un problème en raison duquel l’ajout d’une nouvelle colonne VARCHAR à une table existante provoquait des échecs de test en raison de différences de schéma entre les nouvelles installations et les mises à niveau. La méthode modifyColumn() gère désormais correctement les colonnes VARCHAR en définissant le jeu de caractères et le classement par défaut.
* _LYNX-772_ : Compatibilité GraphQl pour la version PHP-8.4
   * _Correction d’une note_ : correction des problèmes de compatibilité de GraphQL avec PHP 8.4 dans plusieurs programmes de résolution, assurant ainsi un fonctionnement fluide. Mise à jour des fichiers concernés dans les modules CatalogRule, Customer, GiftMessage, GiftCard et GiftWrapping.

### GraphQL, Inventaire / MSI

* _ACP2E-2607_ : la mutation MergeCart renvoie une exception lorsque les paniers source et de destination ont les mêmes éléments de lot
   * _Corriger la note_ : &#39;-
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c971859e>, <https://github.com/magento/inventory/commit/db0620da>

### GraphQL, Inventaire / MSI, Performances

* _ACP2E-1716_ : site arrêté après la mise à niveau
   * _Remarque de correctif_ : les performances de récupération des produits groupés via GraphQl sont améliorées.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ba25af8a>, <https://github.com/magento/inventory/commit/bdbf97ea>

### GraphQL, Performances

* _AC-9569_ : [Résolveur GraphQL] les données du résolveur client ne sont pas invalidées de l’importation
   * _Remarque de correction_ : le cache du résolveur client de GraphQL est désormais invalidé comme prévu lorsqu’un client est modifié ou supprimé lors des importations. Auparavant, le cache n’était pas invalidé et les données client pouvaient être modifiées ou supprimées lors de l’importation.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/0574ac23>

### GraphQL, Recherche

* _ACP2E-2809_ : le tri des listes de produits GraphQL par plusieurs paramètres ne fonctionne pas
   * _Remarque de correction_ : le tri des produits par plusieurs champs dans GraphQl fonctionne désormais comme décrit dans la documentation
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-948_ : requête GraphQL de liste de produits limitée à total_count 10 000 produits uniquement
   * _Note de correction_ : une fois la correction effectuée, le résultat de la recherche ne se limite pas à 10000 produits. Il devient alors possible d’obtenir tous les produits correspondant aux critères de recherche, même si le nombre est supérieur à 10000.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/a4cf5e62>

### GraphQL, Cadre de test

* _ACP2E-3363_ : échec du test d’intégration Magento\GraphQl\App\GraphQlCustomerMutationsTest.php
   * _Remarque correctif_ : &#39;-
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/a4cf5e62>

### Import/export

* _AC-12172_ : problème lors de l’importation du produit lorsqu’il est fourni avec le type d’options personnalisé : fichier (le produit créé ne contient pas le prix du type d’option personnalisé et affiche uniquement la première extension de type de fichier fournie)
   * _Remarque correctif_ : Le système importe désormais correctement les données du produit avec des options personnalisées de type &#39;fichier&#39;, garantissant que toutes les extensions de fichier fournies sont affichées et que le prix de l’option personnalisée est inclus. Auparavant, lors de l’importation du produit, si une option personnalisée de type « fichier » était fournie avec plusieurs extensions de fichier, seule la première extension s’affichait et le prix de l’option personnalisée était manquant.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38805>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38926>
* _ACP2E-2710_ : temps d&#39;exécution incorrect pour l&#39;opération d&#39;importation dans la grille de l&#39;historique d&#39;importation
   * _Remarque correctif_ : le temps d’exécution du rapport d’importation s’affiche correctement, indépendamment des paramètres régionaux de l’administrateur.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2737_ : clients en double créés avec la même adresse électronique à l’aide de l’importation
   * _Remarque correctif_ : L’importation du client alors que le partage de compte est défini sur Global, client importé qui existe dans le système est mis à jour.
Le client précédemment importé était dupliqué.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2902_ : ajout/mise à jour d&#39;un import sur les produits dupliquant des options personnalisables
   * _Correction de la note_ : le problème a été résolu en attribuant le magasin approprié aux options de produit lors des importations d’options de produit au format CSV.
Auparavant, affecté à l’admin store au lieu de leur magasin respectif.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2990_ : date « created_at » du client non convertie en fuseau horaire du magasin lors de l’exportation
   * _Correction de la note_ : une valeur de date de colonne « created_at » est convertie au format de date approprié en fonction du fuseau horaire du magasin dans la section CSV d’exportation du client.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3165_ : [Cloud] erreur lors de la vérification des données dans les données d’importation à l’aide de CSV
   * _Remarque correctif_ : Il n’y a aucune erreur lors de la vérification des données lors de l’importation CSV. Auparavant, le message d’erreur affiché était : « Nous ne pouvons pas trouver un client qui correspond à cet e-mail et code de site Web dans la (les) ligne(s) : 1 » lors de la vérification des données dans la section d’importation à l’aide d’un fichier CSV à partir de l’administrateur.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3172_ : bouton Importer manquant
   * _Correction de la remarque_ : résolvez le problème manquant du bouton Importer après la vérification des données avec des enregistrements corrects et incorrects dans le fichier CSV. Auparavant, le bouton d’importation ne s’affichait pas après la vérification des données avec des enregistrements corrects et incorrects dans le fichier CSV.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1819fe73>
* _ACP2E-3382_ : impossible d&#39;importer l&#39;adresse du client exportée
   * _Remarque du correctif_ : L’importation de l’adresse du client se poursuivra comme prévu. Auparavant, un fichier d’importation d’adresse client ne passait pas la validation si Partager les comptes clients = Global, et il existe deux sites Web où le site Web par défaut a une liste restreinte de pays, et l’adresse qui est importée est pour un autre site Web où les pays autorisés sont différents
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3448_ : [Cloud] Une quantité incorrecte dans le fichier CSV n&#39;a pas donné d&#39;erreur
   * _Corriger la note_ : Désormais, l&#39;importation des origines de stock générera une erreur de validation pour les valeurs non numériques dans la colonne de quantité. Auparavant, l&#39;importation d&#39;origines de stock avec une valeur non numérique dans la colonne Quantité entraînait la définition de la quantité sur 0.
   * _Contribution du code GitHub_ : <https://github.com/magento/inventory/commit/5b21b7af>
* _ACP2E-3455_ : le message d&#39;erreur de clé d&#39;URL dupliquée généré lors de l&#39;importation d&#39;un produit est incorrect lorsque la clé d&#39;URL appartient déjà à une catégorie
   * _Remarque de correction_ : affichage du message d’erreur correct lors de la vérification de l’importation du produit, lorsque le client a tenté d’importer le produit alors que la clé URL du produit appartient déjà à une catégorie.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3475_ : l&#39;exportation du produit entraîne un OOM même avec une limite de mémoire 4G
   * _Remarque sur la correction_ : avant ce correctif, l’exportation du produit échouait si les attributs de produit avaient des milliers de valeurs d’option même avec la mémoire disponible 4G. Après ce correctif, l’exportation du produit doit terminer l’exportation du fichier CSV.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3527_ : processus d&#39;importation [Cloud] interférant les uns avec les autres
   * _Remarque sur la correction_ : des messages corrects s’affichent si le même utilisateur administrateur effectue plusieurs opérations d’importation à l’aide de la même session utilisateur.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d4de4726>

### Importation/exportation, Performances

* _ACP2E-3476_ : [Cloud] Le temps d’importation des produits a considérablement augmenté
   * _Remarque sur la correction_ : avant la correction, l’importation de produits de catalogue avec plus de 10 000 entrées présentait une dégradation temporelle significative. Après le correctif, l’importation des produits du catalogue s’exécute dans les délais impartis.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/87d012e5>

### Installer et administrer

* _AC-13242_ : la mise à niveau de Magento échoue sur MariaDB 11.4 + 2.4.8-beta1
   * _Remarque sur la correction_ : la mise à niveau doit s’être effectuée sans erreur.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/7b336d0a>
* _ACP2E-2102_ : pas de VCL d&#39;exportation pour le bouton Vernis 7 dans le panneau d&#39;administration
   * _Correction de la remarque_ : le bouton « Exporter VCL pour vernis 7 » a été ajouté au panneau d’administration.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a4fbf702>

### Inventaire / MSI

* _AC-10750_ : la mise à jour de l&#39;inventaire des produits configurables échoue lorsque la base de données utilise des préfixes
   * _Remarque sur les correctifs_ : le système met désormais correctement à jour l&#39;inventaire des produits configurables lorsque la base de données utilise des préfixes, ce qui empêche tout message d&#39;erreur et garantit que la quantité correcte est enregistrée. Auparavant, une erreur se produisait lors de la tentative d&#39;enregistrement de la quantité en stock de produits simples dans un produit configurable si la base de données utilisait des préfixes.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38045>
* _AC-11593_ : la clé API Google Google ne fonctionne pas lors de l’ajout d’une carte avec des attributs
   * _Remarque de correction_ : le système prend désormais en charge la dernière version de l’API Google Maps 3.56, ce qui permet aux utilisateurs d’ajouter un bloc de contenu Map du menu PageBuilder à l’étape sans rencontrer d’erreurs. Auparavant, les utilisateurs ne pouvaient pas ajouter de bloc de contenu Map en raison de problèmes de compatibilité avec la version de l’API Google Maps, ce qui entraînait un message d’erreur « une erreur s’est produite ».
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/0574ac23>
* _AC-13922_ : impossible de créer une expédition pour l&#39;article de commande avec plusieurs sources et un SKU corrompu
   * _Correction de la note_ : Auparavant, lorsque des espaces étaient ajoutés par erreur dans le SKU par le biais de la base de données, une erreur se produisait dans la page d&#39;expédition, qui est maintenant corrigée et la correction automatique est considérée comme une erreur conviviale pour l&#39;homme, sans aucun impact. Par conséquent, l&#39;expédition a été créée avec succès.
   * _Contribution du code GitHub_ : <https://github.com/magento/inventory/commit/c18eb5fa>
* _ACP2E-1411_ : [Test] Offrez des produits groupés avec 0 inventaire affiché sur la vitrine
   * _Remarque sur la correction_ : le produit groupé ne s’affiche pas sur les sites Web supplémentaires utilisant un stock supplémentaire.
* _ACP2E-2794_ : [Cloud] problème critique lié à la liste des produits avec des espaces vides
   * _Remarque sur la correction_ : le système affiche désormais correctement les listes de produits sans espaces vides lorsque les produits sont définis sur « En rupture de stock », ce qui garantit un affichage cohérent et précis des produits disponibles. Auparavant, la définition d’un produit sur « En rupture de stock » entraînait l’affichage d’un espace vide dans la liste des produits, ce qui perturbait la mise en page et pouvait dérouter les clients.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ea79f7dd>, <https://github.com/magento/inventory/commit/b59e48ca>
* _ACP2E-3335_ : impossible d&#39;expédier la commande lorsque le magasin de prélèvement MSI est activé
   * _Remarque sur la correction_ : amélioration des performances d’inventaire de la création d’expédition pour de nombreuses sources avec retrait en magasin
   * _Contribution du code GitHub_ : <https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3355_ : la réindexation Cron ne parvient pas à mettre à jour la disponibilité du produit sur le serveur frontal
   * _Remarque de correction_ : auparavant, les produits restaient en rupture de stock sur le serveur frontal après la mise à jour du statut de la commande en attente via l’API REST. Désormais, après la mise à jour du statut de la commande en attente via l’API REST, les produits s’affichent comme en stock.
   * _Contribution du code GitHub_ : <https://github.com/magento/inventory/commit/e6fe0aa7>
* _ACP2E-3357_ : échec de l&#39;ajout d&#39;images à configurable lorsque MSI est activé.
   * _Remarque sur la correction_ : le chargement des images pour les produits configurables fonctionne désormais comme prévu lorsque le module d’inventaire est utilisé. Auparavant, le chargement de l’image ne fonctionnait pas
   * _Contribution du code GitHub_ : <https://github.com/magento/inventory/commit/fdf409aa>
* _ACP2E-3470_ : problème lié au produit groupé + MSI dans Clean M2.4.7-p3
   * _Remarque de correction_ : auparavant, pour les produits groupés en stock après duplication avec le même produit simple, le produit simple ne peut pas être enregistré. Une fois ce correctif appliqué, le produit simple peut être enregistré sans aucune exception.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39358>
   * _Contribution du code GitHub_ : <https://github.com/magento/inventory/commit/0208e433>

### Inventaire / MSI, Recherche

* _ACP2E-3413_ : tous les produits sont indexés avec [is_out_of_stock] = 1 lorsque le SKU n’est pas défini comme attribut consultable
   * _Remarque de correction_ : après la correction, le paramètre « is_out_of_stock » dans l’index de recherche catalogue est correct, même lorsque le SKU ne peut pas faire l’objet de recherches.
   * _Contribution du code GitHub_ : <https://github.com/magento/inventory/commit/5b21b7af>

### Ordre

* _AC-10828_ : Écran d&#39;aperçu de commande du serveur principal : Quantité en reliquat non visible au niveau de l&#39;article de commande
   * _Corriger la note_ : Le système affiche désormais le nombre d&#39;articles en reliquat dans la colonne Quantité de l&#39;écran d&#39;aperçu de commande du serveur principal. Cela permet aux utilisateurs et utilisatrices de suivre avec précision le statut de tous les éléments d’une commande. Auparavant, la colonne Quantité affichait uniquement le nombre d’articles commandés, facturés et expédiés, mais n’affichait pas le nombre d’articles en reliquat.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38252>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38320>
* _AC-10994_ : [Problème] ID de magasin incorrect utilisé dans le moteur de rendu d’adresse de commande
   * _Remarque de correction_ : le système utilise désormais correctement l’ID de magasin associé à une commande lors du rendu de l’adresse de commande, en s’assurant que les adresses sont formatées correctement en fonction de leur ID de magasin respectif. Auparavant, le système utilisait incorrectement l’ID de magasin actuel, ce qui pouvait entraîner un formatage incorrect de l’adresse dans les cas où plusieurs e-mails de commande provenant de différents magasins devaient être envoyés.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38412>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37932>
* _AC-11690_ : problème de mise en cache de JoinProcessor
   * _Remarque de correction_ : le système applique désormais correctement le JoinProcessor pour chaque itération, même avec des appels consécutifs, ce qui garantit une récupération précise des données. Auparavant, JoinProcessor était incorrectement marqué comme étant déjà appliqué dans des itérations consécutives, ce qui entraînait des erreurs dans la récupération des données.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/27504>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37550>
* _AC-11798_ : [Problème] Le prix d’expédition s’affiche différemment dans le pdf imprimé
   * _Corriger la note_ : le système affiche désormais correctement les prix d&#39;expédition dans les fichiers PDF imprimés en fonction des paramètres de configuration de taxe, ce qui garantit la cohérence entre la page de vue de la facture de commande client et la facture imprimée. Auparavant, le prix d’expédition affiché dans le PDF imprimé excluait la taxe, quels que soient les paramètres de configuration de la taxe.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38608>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38595>, <https://github.com/magento/magento2/commit/1bafc571>
* _AC-13839_ : réorganiser avec un produit configurable parent supprimé
   * _Correction de note_ : Désormais, lors de la réorganisation avec le produit supprimé, le système n&#39;affichera pas le bouton de réorganisation pour réorganiser
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39568>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/39601>
* _AC-13924_ : [Problème] Correction d’une propriété incorrecte \Magento\Sales\Model\Order\Email\Container\Template::$id
   * _Correction de la note_ : cela corrige le mauvais phpdoc pour \Magento\Sales\Model\Order\Email\Container\Template::$id, en fait $id est de type int mais en réalité est string.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39151>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/39150>
* _ACP2E-2622_ : impossible d&#39;enregistrer les modifications apportées au numéro de téléphone dans les détails de la commande existante
   * _Note de correction_ : Désormais, l&#39;utilisateur peut ajouter le préfixe international 00 dans le champ téléphonique de l&#39;adresse de commande
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38201>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2734_ : échec de l&#39;envoi des e-mails
   * _Remarque de correction_ : le système comprend désormais une option de configuration async_sending_attempts pour spécifier le nombre de tentatives d’envoi d’un e-mail avant l’arrêt, ce qui améliore la gestion des envois d’e-mail ayant échoué lorsque l’option « Envoi asynchrone » est activée. Auparavant, si l’envoi d’un e-mail échouait, le système tentait continuellement de le renvoyer, ce qui entraînait une boucle sans fin de messages d’erreur dans le journal système.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2756_ : [Cloud] le statut de la commande a été remplacé par terminé lors du remboursement partiel d&#39;une commande partiellement expédiée
   * _Corriger note_ : Lors de l&#39;émission d&#39;un avoir, le statut de la commande n&#39;est plus « terminé » si des articles n&#39;ont pas encore été expédiés.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-3002_ : [CLOUD] impossible de désactiver l’envoi d’e-mails depuis l’interface utilisateur d’administration comme indiqué dans la documentation de développement
   * _Remarque de correction_ : le système empêche désormais correctement l’envoi d’e-mails de vente lorsque la communication par e-mail est désactivée. Ces e-mails ne seront plus envoyés lorsque la communication par e-mail sera réactivée. Auparavant, les e-mails de vente initiés alors que la communication par e-mail était désactivée étaient toujours envoyés une fois la communication par e-mail réactivée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-3045_ : commande clôturée sans remboursement intégral
   * _Corriger la note_ : Le système conserve désormais correctement le statut de la commande comme &#39;Traitement&#39; et le statut de la facture comme &#39;En attente&#39; lorsqu&#39;une commande avec un paiement non saisi fait l&#39;objet d&#39;une expédition. Cela garantit que les commandes ne sont marquées comme « Fermées » qu&#39;après avoir été entièrement remboursées. Auparavant, la création d&#39;une livraison pour une commande avec une facture en attente modifiait incorrectement le statut de la commande en « Fermée ».
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3311_: [Cloud] Impossible de créer une commande dans l’administration sur un magasin si seule l’adresse de facturation par défaut n’a pas été configurée
   * _Correction de la note_ : désormais, le message d’erreur approprié « Un client ou une cliente avec la même adresse e-mail existe déjà dans un site web associé ». s’affiche si un client ne dispose pas d’une adresse de facturation par défaut et tente de créer une commande dans un autre magasin.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3416_ : l&#39;administrateur a dupliqué les demandes de commande envoyées
   * _Correction de la note_ : auparavant, il était possible de cliquer plusieurs fois sur le bouton « Envoyer la commande » du panneau d’administration ou de l’activer en appuyant de manière répétée sur la touche « Entrée », ce qui entraînait des envois en double ou des commandes avec une erreur. Vous pouvez désormais empêcher d’autres actions tant que la commande n’est pas entièrement traitée, en veillant à ce qu’une seule commande soit envoyée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3425_ : l&#39;administrateur peut toujours passer commande même sans mode de paiement
   * _Corriger note_ : Le mode de paiement précédemment sélectionné est désormais conservé lorsque le mode de paiement réapparaît dans la liste des paiements disponibles.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3518_ : les éléments sont dupliqués après la création d’une commande auprès de l’administrateur sur le navigateur Mozilla Firefox
   * _Remarque de correction_ : les produits ajoutés à l’aide de « Ajouter des produits par SKU » ne sont plus dupliqués dans Firefox lors de la création d’une commande dans l’administration.

### Commande, Paiements

* _ACP2E-3233_ : l&#39;administrateur peut toujours passer commande même sans mode de paiement
   * _Corriger la note_ : Auparavant, le commerçant pouvait passer des commandes à partir du panneau d&#39;administration sans sélectionner de mode de paiement. Maintenant, le commerçant doit utiliser un mode de paiement pour passer une commande.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/fd5cf3af>

### Commande, Retours

* _ACP2E-2982_ : le remboursement de la commande génère un avoir en double
   * _Remarque de correction_ : l&#39;émission du remboursement via l&#39;API REST lorsque deux demandes identiques ont été exécutées simultanément ne crée plus d&#39;avoirs en double.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a4fbf702>

### Commande, Taxe

* _ACP2E-3003_ : [CLOUD] Base_row_total incorrect dans l’API de commande RESTFUL lors de l’activation des transactions transfrontalières et de l’application des remises sur coupon
   * _Correction de la note_ : Désormais, un montant base_row_total correct est renvoyé par l’API de commande RESTFUL lorsque la transaction transfrontalière est activée et que la remise de coupon est appliquée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/9af794a4>

### Autres frais

* _BUNDLE-3394_ : [Braintree] Remboursez la transaction de stockage en ligne en tant que transactionid-remboursement
* _BUNDLE-3421_ : [Braintree] + [CLOUD] Braintree (carte de crédit) ne peut pas fractionner les frais
* _BUNDLE-3422_ : le certificat SSL [Braintree] [Cloud]Braintree expire le 30 juin
* _LYNX-339_ : cookie private_content_version renvoyé dans les requêtes GQL.
   * _Remarque de correction_ : correction d’un problème en raison duquel le cookie private_content_version était renvoyé dans les requêtes GraphQL, même lorsque le cookie de session était désactivé. Le cookie n’est plus inclus dans les réponses de GraphQL lorsque la session est désactivée, comme prévu.
* _LYNX-366_ : erreur du serveur sur les props d&#39;e-mail dans les requêtes de carte cadeau physique
   * _Correction d’une note_ : correction d’un problème en raison duquel les requêtes pour sender_email et recipient_email sur les cartes-cadeaux physiques généraient une erreur de serveur. Ces props sont désormais correctement renvoyées pour les cartes-cadeaux virtuelles et le comportement de la requête est cohérent.
* _LYNX-380_ : l’attribut is_available dans CartItemInterface renvoie toujours false pour les produits configurables
   * _Correction de la note_ : correction d’un problème en raison duquel l’attribut is_available dans CartItemInterface renvoyait toujours la valeur false pour les produits configurables en stock. Désormais, elle reflète correctement la disponibilité comme vraie, le cas échéant.
* _LYNX-382_ : l&#39;attribut is_available dans CartItemInterface renvoie la valeur true même lorsque le stock vendable est inférieur à la quantité du produit
   * _Correction de la note_ : correction d’un problème en raison duquel l’attribut is_available dans CartItemInterface renvoyait incorrectement la valeur true même lorsque la quantité d’articles du panier dépassait le stock vendable.
* _LYNX-395_ : l’attribut only_x_left_in_stock dans ProductInterface n’est pas précis sur les produits configurables
   * _Correction d’une note_ : correction d’un problème en raison duquel l’attribut only_x_left_in_stock dans ProductInterface ne reflétait pas précisément le stock disponible pour les variantes de produit configurables dans le panier. Désormais, la valeur only_x_left_in_stock correspond correctement aux niveaux de stock réels de la variante, ce qui garantit que des données d’inventaire précises sont renvoyées dans la requête Cart GQL.
* _LYNX-399_ : La miniature d’espace réservé apparaît lorsqu’un produit simple est ajouté au panier au sein d’un produit groupé
   * _Remarque de correction_ : correction d’un problème en raison duquel l’ajout d’un produit simple (partie d’un produit regroupé) au panier renvoyait une image miniature d’espace réservé, même lorsque le produit avait une image affectée.
Détails du correctif :
• La vignette du produit affiche désormais correctement l’image attribuée si disponible.
• La sélection des miniatures respecte la configuration admin sous :
Stocke > configuration > les ventes > le passage en caisse > le panier >image groupée du produit.
Cela garantit un comportement cohérent des miniatures pour les produits regroupés en fonction des paramètres du magasin.
* _LYNX-400_ : les attributs d’option personnalisés du client ne fonctionnent pas avec des valeurs entières
   * _Correction de la note_ : correction d’un problème en raison duquel les attributs d’option personnalisés du client ne fonctionnaient pas lorsque la valeur renvoyée était un entier. Les options personnalisées gèrent et renvoient désormais correctement les valeurs entières comme prévu.
* _LYNX-402_ : erreur de serveur interne lors de la tentative d’obtention de priceDetails pour les produits groupés avec un prix dynamique
   * _Correction de la note_ : correction d’un problème en raison duquel l’interrogation de price_details pour les produits groupés avec une tarification dynamique via GraphQL entraînait une erreur de serveur interne. Cette amélioration garantit la stabilité des requêtes de panier lors de l’utilisation de produits groupés configurés avec une tarification dynamique.
* _LYNX-403_ : only_x_left_in_stock renvoie toujours 0 pour les produits configurables
   * _Correction de la note_ : correction d’un problème en raison duquel l’attribut only_x_left_in_stock renvoyait toujours 0 pour les produits configurables lorsqu’il était ajouté à l’aide du SKU parent avec des options.
Détails du correctif :
· La valeur only_x_left_in_stock reflète désormais précisément le stock de la variante enfant sélectionnée au lieu du SKU parent.
· Cela permet de s’assurer que les niveaux de stock sont correctement affichés pour les variations de produit configurables dans le panier et les pages de produit.
* _LYNX-405_ : erreur GraphQL : type &#39;fichier&#39; non pris en charge dans la requête des options personnalisables
   * _Remarque de correction_ : correction d’un problème en raison duquel GraphQL renvoyait une erreur pour les options personnalisables de type « fichier » dans les éléments de panier. La requête renvoie désormais correctement les détails de tous les types d’options personnalisables, y compris les options basées sur des fichiers, sans causer d’erreurs.
* _LYNX-411_ : la requête GraphQL ne renvoie pas le prix normal calculé correct pour les produits personnalisables
   * _Correction de la note_ : correction d’un problème en raison duquel GraphQL ne renvoyait pas le prix normal calculé correct pour les produits personnalisables. La requête inclut désormais correctement le prix normal calculé avec des valeurs personnalisables appliquées (par exemple, 125 $) dans la propriété de prix, reflétant à la fois le prix de base et tous les coûts de personnalisation supplémentaires.
* _LYNX-412_ : AppliedTaxes via EstimatedTotals persiste avec des mutations mises à jour
   * _Remarque corrigée_ : correction d’un problème lié à la mutation EstimatedTotals en raison de laquelle les taxes appliquées persistaient sur un panier même après la mise à jour de la région ou du code postal. La mutation met désormais correctement à jour les taxes appliquées lors du changement entre les valeurs de région et de code postal, garantissant que seule la règle fiscale correcte est appliquée en fonction des données du panier actuel.
* _LYNX-420_ : is_available attribut dans CartItemInterface renvoie true même lorsque le stock commercialisable est inférieur à la quantité du produit
   * _Remarque de correctif_ : correction d’un problème en raison duquel l’attribut is_available dans CartItemInterface retournait incorrectement true même lorsque le stock commercialisable était inférieur à la quantité de produit demandée. Le champ is_available renvoie désormais correctement false lorsque la quantité du produit dépasse le stock disponible.
* _LYNX-421_ : impossible d’ajouter un coupon au panier pour l’expédition uniquement
   * _Correction d’une note_ : correction d’un problème en raison duquel un coupon ne pouvait pas être appliqué à un panier pour les remises sur les frais d’expédition uniquement. Le coupon est désormais correctement appliqué au montant de l’expédition lors de l’utilisation d’une règle de vente sans conditions de produit, ce qui garantit que la remise attendue est appliquée aux frais d’expédition.
* _LYNX-425_ : Prix normal du produit avec 12 décimales et une valeur incorrecte
   * _Corriger la note_ : correction d’un problème en raison duquel la valeur du prix normal dans les chemins GraphQL product.price_range.maximum_price et minimum_price ne correspondait pas au prix du catalogue lorsque plusieurs taux de taxe étaient appliqués. Le prix normal reflète désormais de manière cohérente le prix catalogue dans toutes les configurations de taxe, ce qui garantit une tarification unitaire précise, des calculs de coût total des lignes et des contrôles de remise dans le résumé du panier.
* _LYNX-430_ : erreur de serveur GraphQL sur le panier avec produit en rupture de stock groupé
   * _Correction d’une note_ : correction d’un problème en raison duquel GraphQL renvoyait une erreur de serveur interne lors de la récupération d’un panier contenant un produit groupé avec un article en rupture de stock, en particulier lorsque la requête incluait la propriété itemsV2. GraphQL renvoie désormais correctement une liste d’éléments avec des messages d’erreur pertinents joints à l’entrée d’élément de produit groupé, comme prévu.
* _LYNX-441_ : impossible de créer une adresse avec des attributs personnalisés
   * _Correction d’une note_ : correction d’un problème lié à la mutation createCustomerAddress qui empêchait la création d’adresses avec les attributs personnalisés obligatoires. La mutation gère désormais correctement les attributs d’adresse personnalisés lorsque la payload appropriée est fournie.
* _LYNX-447_ : erreur de serveur GraphQL sur le panier avec only_x_left_in_stock sur le produit groupé
   * _Correction d’une note_ : correction d’un problème en raison duquel la récupération d’un panier contenant un produit groupé avec le champ only_x_left_in_stock dans la requête GraphQL entraînait une erreur de serveur interne. GraphQL renvoie désormais correctement un flottant ou une valeur null pour le champ only_x_left_in_stock sans erreurs.
* _LYNX-464_ : erreur GraphQL lors de la suppression d’autres produits avec un produit configurable insuffisant dans le panier
   * _Correction de la note_ : correction d’un problème en raison duquel la tentative de suppression des produits en stock du panier entraînait une erreur GraphQL « La quantité demandée n’est pas disponible » si le panier contenait également des produits configurables avec un stock insuffisant. La suppression fonctionne désormais comme prévu sans déclencher d’erreurs.
* _LYNX-469_ : Impossible d’ajouter des produits en raison du SKU en mutation étant sensible à la casse
   * _Remarque de correction_ : correction d’un problème en raison duquel la mutation addProductsToCart renvoyait une erreur « PRODUCT_NOT_FOUND » lors de l’utilisation de SKU avec une casse différente. La mutation gère désormais les SKU sans respect de la casse, ce qui garantit la cohérence avec les requêtes du service de catalogue et le comportement du PDP.
* _LYNX-603_ : attribut de produit > ™ abrégée de marque renvoyée sous la forme ™
   * _Remarque à propos de la correction_ : problème de codage des caractères résolu avec le nom du produit pour l’API GraphQL
* _LYNX-619_ : problème de mutation updateCustomerEmail
   * _Correction d’une note_ : correction d’un problème lié à la mutation updateCustomerEmail en raison duquel les clients sans attributs personnalisés obligatoires (ajoutés après la création du compte) ne pouvaient pas mettre à jour leur e-mail.
* _LYNX-626_ : la mutation setShippingAddressesOnCart renvoie une erreur lors de l’utilisation de pickup_location_code
   * _Remarque sur le correctif_ : correction d’un problème en raison duquel la mutation setShippingAddressesOnCart retournait une erreur lors de l’utilisation de pickup_location_code sans spécifier customer_address_id ou adresse. La mutation permet désormais de définir correctement une adresse de livraison avec seulement le pickup_location_code.
* _LYNX-627_ : CustomerOrder.items_eligible_for_return liste doit être cohérente avec les articles commandés
   * _Remarque_ pour le correctif : Résolution d’incohérences avec l’éligibilité des retours dans les commandes :
1. La liste CustomerOrder.items_eligible_for_return correspond désormais aux articles de commande réels.
2. Le champ OrderItemInterface.eligible_for_return renvoie correctement false lorsque la quantité complète a déjà été renvoyée.
3. CustomerOrder.items_eligible_for_return n’inclut plus que les articles qui ne sont pas déjà en cours de retour.
* _LYNX-628_ : Ajouter quantity_return_requested champ
   * _Remarque correctif_ : ajout du champ quantity_return_requested à OrderItemInterface, ce qui vous permet d’identifier la quantité d’articles pour lesquels un retour a été envoyé. Ceci améliore le suivi des retours en plus du champ de quantity_returned existant.
* _LYNX-634_ : Les actions de commande disponibles ne doivent pas contenir de RETOUR après les retours créés pour tous les articles en quantité complète
   * _Correction de la note_ : correction d’un problème en raison duquel le champ available_actions de la requête customer.orders de GraphQL incluait incorrectement RETURN après la création d’un retour complet pour tous les articles. L’action RETOUR est désormais correctement supprimée une fois le processus de retour terminé.
* _LYNX-637_ : compatibilité Storefront - mettez à jour la logique pour obtenir le nom de la table avec le préfixe et d’autres améliorations mineures
   * _Note de correction_ : Mise à jour de la logique pour récupérer le nom de la table avec le préfixe (lié aux modifications SCP).
* _LYNX-643_ : l’enregistrement dans le carnet d’adresses ne fonctionne pas lors de l’utilisation du champ same_as_shipping de setBillingAddressOnCart GQL
   * _Correction d’une note_ : correction d’un problème en raison duquel l’adresse d’expédition n’était pas enregistrée dans le carnet d’adresses du client lors de l’utilisation de la mutation de GraphQL setBillingAddressOnCart avec le champ same_as_shipping défini sur true. Désormais, l’adresse de livraison est correctement stockée comme prévu.
* _LYNX-650_ : Standariser le order_id dans les mutations
   * _Remarque de correctif_ : Normalisation de l’entrée de order_id dans les mutations et mise à jour du modèle d’e-mail de confirmation d’annulation de commande afin d’exposer l’ID d’incrémentation au lieu de l’ID de commande.
* _LYNX-651_ : CustomerOrder n’affiche pas les commentaires de commande
   * _Remarque correctif_ : Résolution d’un problème avec CustomerOrder pour inclure les commentaires de commande dans les requêtes GraphQL de commande des invités et des clients.
* _LYNX-652_ : original_item_price ne doit inclure aucune remise
   * _Remarque correctif_ : Mise à jour de la logique pour l’original_item_price dans les prix des articles du panier GraphQL afin d’exclure les remises.
* _LYNX-681_ : les produits groupés affichent toujours « IN_STOCK » lorsque l’un de ses produits groupés est en rupture de stock
   * _Correction de la note_ : correction d’un problème en raison duquel product.stock_status pour les produits groupés affichait toujours « IN_STOCK » même si l’un des éléments groupés était en rupture de stock.
* _LYNX-686_ : la requête client renvoie Erreur interne du serveur si la valeur de l’attribut personnalisé supprimé existe pour un client
   * _Remarque correctif_ : correction du problème où la requête client renvoyait une erreur de serveur interne lorsqu’un attribut personnalisé supprimé avait toujours une valeur stockée. Désormais, un message d’erreur correct est renvoyé si un attribut non existant est demandé. Le cache nécessaire est invalidé lors de la suppression de l’attribut personnalisé du client.
* _LYNX-687_ : Paramètre d’action pour le renvoi et l’annulation des liens de confirmation
   * _Correction de la note_ : paramètre d’action ajouté pour le retour et l’annulation des liens liés aux e-mails de confirmation
* _LYNX-688_ : l&#39;URL de confirmation de l&#39;utilisateur invité est redirigée vers la page de statut de la commande, car il lui manque orderRef (pour GuestRMA)
   * _Correction de la note_ : ajout du paramètre orderRef au lien dans l&#39;e-mail de confirmation RMA invité
* _LYNX-689_ : l’URL de confirmation de l’utilisateur invité est redirigée vers la page de statut de la commande, car il manque orderRef
   * _Correction de la note_ : ajout du paramètre orderRef au lien dans l’e-mail de confirmation d’annulation de commande du client
* _LYNX-690_ : Problèmes liés aux requêtes client lorsque RMA est désactivé
   * _Remarque de correctif_ : Mise à jour de la logique GraphQL pour s’assurer que les retours précédemment créés restent accessibles même lorsque RMA est désactivé globalement. Le message d’erreur a été supprimé pour améliorer l’expérience utilisateur de la vitrine, garantissant ainsi que les clients peuvent toujours voir leurs retours passés.
* _LYNX-696_ : GraphQL ne renvoie pas les données de panier mises à jour lorsque des coupons en conflit sont appliqués
   * _Correction de la note_ : correction d’un problème en raison duquel l’application d’un coupon en conflit avec une priorité plus élevée générait un message d’erreur sans renvoyer les données de panier mises à jour. Maintenant, lorsqu’un nouveau coupon invalide le coupon existant, la mutation retourne correctement le panier avec le coupon valide appliqué.
* _LYNX-699_ : impossible de renvoyer la valeur null pour le champ « TaxItem.title » non nullable sur placeOrder GQL
   * _Correction de la note_ : correction d’un problème en raison duquel la mutation placeOrder échouait avec une erreur de serveur interne en raison d’une valeur nulle pour le champ TaxItem.title non nullable. Désormais, le champ renvoie toujours une valeur valide, ce qui garantit la réussite du placement de la commande.
* _LYNX-702_ : EstimateTotals : les remises sont nulles pour les types de produits virtuels
   * _Correction de la note_ : correction du problème en raison duquel la mutation estimateTotals renvoyait une valeur nulle pour les remises lorsqu’un code de remise est appliqué à un panier contenant des produits virtuels.
* _LYNX-703_ : le produit groupé ne renvoie pas le pourcentage et le montant de remise corrects
   * _Corriger la note_ : De nouvelles propriétés « catalog_discount » et « row_catalog_discount » ont été introduites pour les prix d&#39;article de catalogue afin d&#39;afficher les montants et pourcentages de remise corrects aux niveaux ligne et article unique.
* _LYNX-714_ : configuration du message cadeau au niveau du produit
   * _Correction d’une note_ : correction d’un problème en raison duquel les messages cadeau n’étaient pas appliqués au niveau du produit lorsqu’ils étaient désactivés globalement. Désormais, si les messages cadeau sont activés pour un produit spécifique, ils peuvent être ajoutés à l’aide de la mutation updateCartItems et seront correctement enregistrés et reflétés.
* _LYNX-717_ : Problème lié au retrait de l’emballage-cadeau du panier
   * _Correction d’une note_ : correction d’un problème en raison duquel la suppression de l’emballage-cadeau d’un article de panier à l’aide de la mutation updateCartItems ne fonctionnait pas comme prévu. Désormais, l&#39;application et la suppression de l&#39;emballage cadeau fonctionnent correctement sans erreurs.
* _LYNX-751_ : la fonctionnalité de client enregistré correspondant ne fonctionne pas dans Boilerplate et la mutation trackViewedProduct doit être activée pour les invités.
   * _Remarque de correctif_ : mutation trackViewedProduct exposée permettant de suivre l’événement d’affichage de produit pour les clients et les invités
* _LYNX-757_ : erreur de retour de requête cart.rules au lieu d’un tableau vide au cas où aucune règle de panier active n’est appliquée
   * _Remarque correctif_ : correction de la requête cart.rules pour renvoyer un tableau vide au lieu d’une erreur lorsqu’aucune règle de panier active n’est appliquée.
* _LYNX-758_ : Problème lors de la récupération des emballages cadeaux pour les articles de panier
   * _Remarque corrigée_ : mise à jour de la logique de récupération pour renvoyer les options d’emballage cadeau pour les articles du panier lorsqu’elles sont globalement désactivées mais activées au niveau du produit
* _LYNX-778_ : Les appels GraphQL avec OPTIONS méthode renvoient le code de réponse 500 lorsque le package adobe-commerce/storefront-compatibility est installé
   * _Remarque correctif_ : correction d’un problème où les appels GraphQL à l’aide de la méthode OPTIONS renvoyaient une erreur de serveur interne 500 lorsque le package adobe-commerce/storefront-compatibility était installé. Le point de terminaison renvoie désormais correctement une réponse 200/204, comme prévu.

### Autres outils de développement

* _AC-10658_ : [Problème] de correction d’une erreur de syntaxe HTML dans visual.phtml
   * _Remarque de correction_ : le système ferme désormais correctement la balise de début dans le fichier visual.phtml, en veillant à ce que la syntaxe HTML soit correcte. Auparavant, la balise de début n’était pas fermée correctement, ce qui provoquait une erreur de syntaxe HTML.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38247>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37457>
* _AC-11474_ : [Problème] Modification de « actif » en « activé » dans la commande bin/magento maintenance:status
   * _Remarque de correction_ : le système fournit désormais des messages d’état plus précis pour la commande du mode de maintenance, changeant l’état de « actif » en « activé » et de « non actif » en « désactivé ». Auparavant, le message d’état de la commande du mode de maintenance s’affichait comme « actif » ou « non actif », ce qui pouvait prêter à confusion.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38486>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38410>
* _AC-12571_ : la navigation dans l’arborescence des catégories entraîne des erreurs dans Redis : « La session Redis a dépassé les connexions simultanées »
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38851>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/0611e750>
* _AC-12731_ : problèmes de CSP combinés avec dev/css/use_css_critical_path
   * _Remarque à propos de la correction_ : le système charge désormais correctement les fichiers CSS de manière asynchrone sur les pages de passage en caisse, même lorsque le paramètre « dev/css/use_css_critical_path » est activé, ce qui garantit que ces pages sont rendues avec les styles CSS appropriés. Auparavant, une politique de sécurité du contenu (CSP) restreinte empêchait l’exécution du JavaScript intégré, ce qui entraînait le chargement inattendu des fichiers CSS.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39020>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/39040>
* _AC-13398_ : en utilisant le type virtuel pour configurer le plug-in, la méthode d&#39;intercepteur ne peut pas être générée correctement dans la commande setup:di:compile
   * _Remarque de correction_ : le système génère désormais correctement des méthodes d’intercepteur lors de l’utilisation d’un type virtuel pour configurer un plug-in, ce qui garantit des résultats cohérents, qu’ils soient précompilés ou compilés lors de l’exécution. Auparavant, le système générait des résultats incorrects lors de la précompilation par rapport à la compilation à l’exécution.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/33980>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38141>
* _ACP2E-3441_ : impossible de télécharger les fichiers du collecteur de données
   * _Remarque de correction_ : le téléchargement de la sauvegarde n’affiche plus une page vierge au lieu de télécharger le fichier.
* _ACP2E-3631_ : les tests unitaires Adobe Commerce 2.4.7-p3 échouent
   * _Note de correction_ : aucune note de mise à jour n’est requise.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/982b1c42>

### Paiement / Modes de paiement, Commande

* _AC-13699_ : Les détails de carte de crédit de payflow papal enregistrés pour une utilisation ultérieure ne s’affichent pas sur la page du mode de paiement stocké
   * _Corriger la note_ : les détails de carte de crédit de payflow papal antérieurs enregistrés pour une utilisation ultérieure ne s&#39;affichaient pas sur la page de mode de paiement stockée qui est maintenant fixe les détails de carte de crédit s&#39;affichent sur la page de mode de paiement stockée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/96dec499>

### Paiements

* _AC-13414_ : le paiement par carte de crédit (lien de flux de paiement) ne fonctionne pas
   * _Correction de note_ : erreur d&#39;obtention précédente (le paiement a été refusé) lors de la commande avec carte de crédit après la correction Commande passée avec succès.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a68324bc>
* _ACP2E-2841_ : Le flux de paie crée une transaction chaque fois que nous cliquons sur le bouton de récupération sur l&#39;écran d&#39;affichage des transactions
   * _Correction de note_ : le système récupère désormais correctement les informations de transaction sans créer de transaction de paiement chaque fois que l&#39;utilisateur clique sur le bouton de récupération sur l&#39;écran d&#39;affichage des transactions. Auparavant, cliquer sur le bouton de récupération créait incorrectement une nouvelle transaction de paiement pour une commande qui avait déjà été payée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3028_ : le message Paylater ne s&#39;affiche pas dans le PDP pour le compte marchand paypal canadien
   * _Correction de note_ : Le système affiche désormais correctement le message PayLater pour les comptes marchands PayPal canadiens sur la page des détails du produit (PDP) lorsque le pays de l&#39;acheteur peut être déterminé à partir de l&#39;adresse de facturation du compte ou de l&#39;expédition. Auparavant, le message PayLater ne s’affichait pas en raison d’un paramètre manquant, ce qui entraînait une erreur dans la console du navigateur.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3143_ : le remboursement d&#39;une commande PayPal génère un avoir en double
   * _Correction de note_ : correction d&#39;un problème de simultanéité des avoirs créés par IPN pour le service de paiement PayPal.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3163_ : la règle de prix du panier ne fonctionne pas pour Paypal
   * _Corriger la note_ : le montant correct s&#39;affiche du côté de PayPal lorsque la remise est appliquée par le mode de paiement
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3208_ : [Cloud] les utilisateurs dotés d’un rôle spécifique ne peuvent pas se connecter
   * _Remarque sur la correction_ : l&#39;utilisateur administrateur dont le rôle contient uniquement un accès à la section PayPal peut désormais se connecter sans erreur
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/66dea0de>

### Performances

* _AC-11932_ : problème de paramètres d’attribut de produit par défaut
   * _Remarque sur la correction_ : le système permet désormais aux utilisateurs de désélectionner une option par défaut pour un attribut de produit, en s’assurant que l’attribut n’a pas toujours de valeur par défaut définie. Auparavant, une fois qu’une valeur par défaut était définie pour un attribut de produit, il n’était pas possible de la désélectionner, ce qui définissait toujours une valeur par défaut pour l’attribut.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38703>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-12000_ : [problème] nettoyage du code et ajout d’un nouveau bloc principal critique, puis déplacement du code CSS critique avant les ressources
   * _Remarque de correction_ : le système comprend désormais un nouveau bloc HEAD critique et déplace les feuilles CSS critiques avant les ressources, ce qui permet une personnalisation et une optimisation des performances supplémentaires dans le front-end. Auparavant, le CSS critique n’était pas positionné avant les ressources, ce qui limitait les opportunités de personnalisation et d’optimisation.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38748>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/35580>
* _AC-12176_ : la compilation du thème s’interrompt lorsque l’hôte mysql contient des informations sur le port
   * _Remarque de correction_ : le système gère désormais correctement la configuration de l’hôte MySQL qui inclut les informations de port, assurant ainsi la réussite de la compilation du thème. Auparavant, la compilation du thème échouait si la configuration de l’hôte MySQL dans la connexion à la base de données incluait des informations sur le port.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38799>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38842>
* _AC-13471_ : prise en charge de l’interface CommandLoaderInterface de Symfony dans l’interface de ligne de commande Magento
   * _Remarque de correction_ : cette modification réduit le temps d’initialisation de l’application de ligne de commande Magento en permettant l’initialisation différée des commandes jusqu’à ce qu’elles soient nécessaires.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/29266>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/29355>
* _ACP2E-2494_ : Problème de performances lors du chargement d’attributs de produit dans les règles de panier
   * _Remarque sur la correction_ : amélioration des performances des requêtes pour les règles de vente, d’environ 150 ms à un seul chiffre ms.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2673_ : performances d’indexation partielle du prix
   * _Remarque correctif_ : Les performances d’indexation partielle du prix ont été améliorées en optimisant certaines des requêtes de suppression utilisées dans le processus d’indexation.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2850_ : la commande est rejetée sur la configuration multi-magasins lors de l’utilisation du traitement des commandes asynchrones + Conditions générales
   * _Remarque correctif_ : Les commandes passées à partir de sites Web autres que ceux par défaut avec les termes et conditions activés sont maintenant traitées.
Avant d’être automatiquement rejetées.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2910_ : l&#39;exécution de l&#39;appel API Order Rest prend beaucoup de temps
   * _Remarque de correction_ : le système exécute désormais l’appel API Order Rest dans un délai raisonnable, ce qui améliore les performances lors de la récupération d’un grand nombre de commandes. Auparavant, l’exécution de l’appel de l’API REST Order prenait beaucoup de temps, ce qui entraînait des retards lors de la récupération d’un grand nombre de commandes.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/001e5188>

### Performances, promotion

* _ACP2E-2617_ : l&#39;indexeur de règles de vente a cessé de fonctionner
   * _Remarque à propos de la correction_ : le système termine désormais avec succès l’indexeur de règles de vente même avec un grand nombre de groupes de filtres combinés, en s’assurant que les conditions des règles du panier sont appliquées au panier comme prévu. Auparavant, l’indexeur de règles de vente ne se terminait pas lorsqu’il y avait un grand nombre de groupes de filtres combinés, ce qui entraînait un message d’erreur et empêchait l’application des conditions des règles du panier.

### Tarification

* _AC-11810_ : Magento2.4.6-p4 Order API Simple Item Prix manquant
   * _Remarque sur la correction_ : le système affiche désormais correctement le prix des produits simples lorsqu’ils sont interrogés via l’API de commande, garantissant ainsi une représentation précise des données. Auparavant, le prix de produits simples s’affichait incorrectement comme zéro dans la réponse de l’API.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38603>
* _AC-13855_ : erreur d’arrondi de centime dans la règle de catalogue
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/276e0acd>

### Produit

* _AC-10535_ : des caractères spéciaux dans le nom de produit associé configurable sont en cours de conversion en entités HTML.
   * _Remarque de correction_ : le système conserve désormais correctement les caractères spéciaux dans les noms des produits associés lors de la modification d’un produit configurable, ce qui empêche leur conversion en entités HTML. Auparavant, les caractères spéciaux dans les noms de produits associés étaient convertis en entités HTML lorsque le produit configurable était modifié.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38146>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38447>
* _AC-10947_ : la fonction ProductRepository GetById ne crée pas la clé de cache correcte
   * _Remarque de correction_ : le système crée désormais correctement une clé de cache dans la fonction GetById du référentiel de produits, que l’ID de magasin soit transmis sous la forme d’une chaîne ou d’un entier. Cela garantit que le produit est récupéré de la mémoire lors des appels suivants, ce qui améliore les performances. Auparavant, le système récupérait le produit de la base de données chaque fois que la fonction était appelée, même avec les mêmes paramètres, en raison d’une création de clé de cache incorrecte.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38384>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38433>
* _AC-11992_ : [Problème] [MFTF] ajoutée à AdminClickAddOptionForBundleItemsActionGroup
   * _Remarque de correction_ : le système inclut désormais l’AdminClickAddOptionForBundleItemsActionGroup, ce qui améliore les fonctionnalités du panneau d’administration. Auparavant, ce groupe d’actions n’était pas disponible.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/30857>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/30838>
* _AC-13173_ : [Problème] Corriger la faute de frappe dans le bloc PHPDoc
   * _Remarque de correction_ : le système supprime désormais correctement une variable référencée inconnue dans PHPDoc pour la déclaration de variable $helper, ce qui améliore la clarté et la précision du code. Auparavant, cette variable référencée inconnue dans PHPDoc provoquait une confusion et des inexactitudes potentielles dans le code.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38961>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38940>
* _AC-13423_ : [Problème] Correction d’un lot rompu et de la disposition des pages de produits téléchargeables dans Magento >= 2.4.7
   * _Remarque sur la correction_ : la mise en page du lot et des pages de produits téléchargeables a été corrigée, assurant ainsi un affichage cohérent et correct sur tous les appareils. Auparavant, ces pages rencontraient des problèmes de mise en page en raison d’une réorganisation du bloc de médias d’informations sur le produit.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39403>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-5969_ : AlertProcessor - L’argument #2 ($storeId) doit être de type int, chaîne donnée.
   * _Remarque de correction_ : le système déclenche désormais correctement les e-mails d’alerte de produit en s’assurant que l’identifiant du magasin est du type de données correct. Auparavant, les e-mails d’alerte de produit n’étaient pas envoyés en raison d’une incohérence de type dans l’identifiant du magasin.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/35602>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/0574ac23>
* _ACP2E-2944_ : la fonction [Cloud] addFilterToMap ne fonctionne pas pour certaines colonnes
   * _Note de correction_ : désormais, le module personnalisé peut être utilisé dans la grille de commande. Des erreurs se produisaient précédemment lors de l’utilisation d’un module personnalisé.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-3471_ : [Cloud] Produits dans la catégorie - Ajouter des produits - Attribuer - Tout sélectionner
   * _Correction d’une remarque_ : les utilisateurs peuvent désormais sélectionner ou désélectionner des produits à l’aide du bouton (bascule).

### Promotion

* _ACP2E-2602_ : attribut du client non visible lors de la création d’un compte à partir d’une invitation
   * _Remarque sur la correction_ : les attributs du client sont disponibles lors de la création du compte à partir de l’invitation.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2627_ : le code de coupon avec la limite Utilisations par coupon n&#39;est pas libéré pour paiement a échoué avec l&#39;annulation de la commande
   * _Correction de note_ : le système met désormais immédiatement à jour les utilisations des coupons lorsqu’une commande est créée ou annulée, et ajoute les utilisations des règles à une file d’attente pour éviter les blocages potentiels. Cela permet de libérer un code de coupon avec une limite « Utilisations par coupon » et de le réutiliser si une commande est annulée en raison d’un échec de paiement. Auparavant, le système ne libérait pas le code de coupon pour le réutiliser dans de tels cas, ce qui entraînait un message d’erreur indiquant que le code de coupon n’était pas valide.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2811_ : [Cloud] réindexation de la règle de catalogue L’indexeur de produit lance SQLSTATE[HY000] : Erreur générale : le serveur MySQL 2006 est parti.
   * _Remarque de correction_ : le système gère désormais correctement la valeur « batchCount » personnalisée dans le fichier di.xml pour « Magento\CatalogRule\Model\Indexer\IndexBuilder », ce qui empêche les erreurs SQL telles que « Erreur générale : 2006 le serveur MySQL a disparu » lors de la réindexation de l’indexeur de produit de la règle de catalogue en raison d’une taille de lot incorrecte sur les catalogues volumineux
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2926_ : [CLOUD]Règle de prix du panier pour le segment client des visiteurs n’appliquant pas de remise au panier
   * _Correction d’une remarque_ : le système applique désormais correctement les règles de prix du panier pour les segments de clientèle des visiteurs, même si la règle n’utilise pas de coupon, en s’assurant que les remises appropriées sont appliquées au panier. Auparavant, les remises n’étaient pas appliquées au panier pour les segments de clientèle des visiteurs, sauf si la règle de prix du panier utilisait un coupon.
* _ACP2E-3024_ : attribut « Type » manquant dans l’onglet « Produits à faire correspondre » des règles de produits associés
   * _Remarque sur la correction_ : l’attribut « Type » est désormais disponible sous la forme d’une option de filtre dans l’onglet « Produits à faire correspondre » du module « Règles de produits associées », ce qui permet de définir des règles plus précises. Auparavant, cet attribut était absent de l’onglet « Produits à faire correspondre », ce qui limitait la possibilité de créer des critères de correspondance précis.
* _ACP2E-3139_ : si la règle de vente comporte l&#39;attribut Etape de quantité de remise (Acheter X), les autres règles ne sont pas appliquées
   * _Corriger la note_ : la règle de prix du panier n’annule pas les règles précédemment appliquées si la quantité du produit dans le panier est insuffisante pour que la règle soit appliquée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3331_ : problème de performance sur la règle de prix de panier - module Règle de vente anticipée
   * _Remarque de correction_ : des index de base de données manquants ont été ajoutés pour les filtres AdvancedSalesRule.
* _ACP2E-3332_ : émettre des règles de vente avec une remise de montant fixe et une « remise de quantité maximale est appliquée à »
   * _Corriger la note_ : problème résolu avec la remise des règles du panier, lorsque la remise de montant fixe est configurée pour être appliquée à une quantité limitée de produits est le panier. Auparavant, la valeur « Remise Qté maximale appliquée à » était utilisée pour calculer le prix de l’article actuel dans le panier, et pas seulement pour calculer la remise de la règle.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3342_ : la mise à niveau de Magento [CLOUD] a rendu les coupons sensibles à la casse
   * _Remarque sur la correction_ : avant la correction, vous deviez saisir le code de coupon tel qu’il était configuré en tenant compte des majuscules et des minuscules. Désormais, le coupon sera validé dans le backend, quelle que soit la configuration du code en majuscules ou minuscules.
* _ACP2E-3349_ : règles de panier « Remise de montant fixe pour le panier entier »  L’action applique incorrectement les remises
   * _Note de correction_ : Les codes de coupon seront validés correctement, indépendamment des majuscules ou des minuscules, lorsqu’ils sont utilisés dans la création de commande à partir de la zone d’administration. Auparavant, le code de coupon n’était pas validé s’il ne correspondait pas à la casse exacte du code de règle de panier configuré.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3374_ : en arrière-plan, valeurs de magasin par défaut pour les attributs de produit (au lieu des valeurs d’administration attendues)
   * _Remarque à propos de la correction_ : désormais, dans le serveur principal, les valeurs d’administration sont utilisées au lieu des valeurs de magasin par défaut pour les attributs de produit.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3377_ : l’action « Remise de montant fixe pour l’ensemble du panier » applique incorrectement les remises lors de l’ajout de produits groupés
   * _Remarque sur la correction_ : les règles de panier à montant fixe n’étaient pas correctement appliquées pour les produits groupés. Désormais, lors du calcul du montant de la remise totale, les produits enfants groupés sont pris en compte, ce qui permet d’obtenir un calcul de remise correct.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3403_ : Règles de prix du panier Calcul erroné de la remise
   * _Correction de note_ : les remises sur montant fixe sont désormais correctement calculées. Avant le correctif, les remises à montant fixe n’étaient pas totalisées correctement pour les produits groupés.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/0b488dd1>
* _ACP2E-3406_ : les catégories imbriquées dans les conditions de règle ne s’affichent pas
   * _Corriger la note_ : problème résolu lorsque les catégories imbriquées sous la catégorie de niveau 3 ne sont pas affichées dans les règles marketing pour la condition de catégorie
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3432_ : usage_limit et uses_per_customer ne sont pas mis à jour dans la table salesrule_coupon.
   * _Remarque de correction_ : la mise à jour des Utilisations par coupon et des Utilisations par client dans la règle de prix du panier affecte désormais les coupons générés automatiquement existants. Auparavant, les nouvelles valeurs affectaient uniquement les nouveaux coupons
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3456_ : la règle de prix du panier ne prend pas en compte la catégorie parent lorsqu’elle utilise la condition « est égale ou supérieure à ».
   * _Corriger la note_ : les règles de prix du panier considèrent désormais correctement la catégorie parent lorsqu’elle est utilisée dans des conditions avancées
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/93359343>
* _ACP2E-3463_ : calcul de remise non valide avec priorité
   * _Corriger la note_ : dans le cas d&#39;un montant fixe appliqué pour le type de remise Panier entier, le montant n&#39;était pas calculé correctement pour les articles du panier qui étaient déjà remis par une promotion précédente. Désormais, les remises sont correctement résumées.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3472_ : [CLOUD] le calcul de l’expédition ne prend pas en compte la règle du panier
   * _Remarque sur la correction_ : avant la correction, une règle de panier avec une condition de région n’était pas appliquée de manière cohérente. Après le correctif, les règles de panier avec des conditions de région sont correctement appliquées.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3491_ : la condition de SKU de règle de panier échoue pour la facture.
   * _Corriger la note_ : la remise sur le produit groupé avec prix dynamique est désormais correctement reflétée dans la facture. Auparavant, la remise n’était pas répercutée sur la facture.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3498_ : valeur de remise incorrecte lorsque plusieurs règles de prix de panier sont appliquées simultanément à des produits à prix réduit/spéciaux
   * _Remarque du correctif_ : Avant le correctif, les règles de montant fixe pour l’ensemble du panier n’étaient pas appliquées correctement si plus d’une était appliquée. Maintenant, les règles du panier de réduction à montant fixe sont appliquées correctement.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1984c61c>

### Renvoie

* _ACP2E-3330_: [CLOUD] Les utilisateurs administrateurs restreints peuvent voir le menu et les boutons de retour
   * _Remarque sur la correction_ : les utilisateurs administrateurs restreints n&#39;ont désormais pas accès aux contrôles liés à RMA (menus et boutons).
Les utilisateurs administrateurs précédemment restreints pouvaient voir le menu et les boutons de retour.
* _ACP2E-3443_ : l&#39;écran de retour est en panne lors de l&#39;actualisation de l&#39;écran
   * _Correction d’une remarque_ : l’utilisateur ou l’utilisatrice peut actualiser la page sans distorsion d’écran.

### SEO

* _AC-11907_ : l’ajout de réécritures d’URL avec un accent entraîne un chargement infini
   * _Remarque de correction_ : le système crée et exécute désormais correctement les réécritures d’URL avec des accents, ce qui empêche le chargement infini pendant le processus d’enregistrement. Auparavant, l’ajout d’une réécriture d’URL avec un accent provoquait un problème de chargement infini.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38692>
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/44cef3a9>
* _ACP2E-2641_ : Réécriture d’URL de catégorie incorrecte pour la catégorie de troisième niveau
   * _Remarque de correction_ : générez des réécritures d’URL correctes pour les enfants avec le parent avec la clé d’URL étendue personnalisée
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2770_ : les caractères à deux octets (caractères spéciaux) dans le champ Nom du produit bloquent la création du produit dans le serveur principal
   * _Remarque de correction_ : un nouveau paramètre a été ajouté pour vous permettre ou non d’appliquer une translittération à l’URL du produit. Le paramètre est disponible ici : Magasins > Configuration > Catalogue > Catalogue > Optimisation du moteur de recherche : « Appliquer la translittération à l’URL du produit »
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3383_ : création d’entrées url_rewrite incorrecte avec plusieurs magasins dans un groupe de magasins
   * _Remarque sur la correction_ : avant la correction, vous ne pouviez générer des réécritures d’URL qu’au niveau d’un site web lors de la modification d’un produit. Avec le correctif, un nouveau paramètre a été introduit (Magasins > Configuration > Catalogue > Catalogue > Optimisation du moteur de recherche, « Portée de la réécriture des URL de produit » avec les options « Vue du magasin », « Site Web ») qui vous permet de générer des réécritures d’URL au niveau du magasin ou du site Web.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/2d627301>

### Ventes

* _AC-13751_ : la règle de prix du deuxième panier n’est pas appliquée si la règle du premier panier est déjà appliquée.

### Rechercher

* _AC-13053_ : obtention de « Saisissez un terme de recherche et réessayez ». erreur sur la page de recherche avancée dans storefront dans 2.4.8-beta1
   * _Remarque de correction_ : le système affiche désormais correctement les résultats de la recherche sur la page Recherche avancée lorsqu’un attribut de produit est défini sur « Non ». Auparavant, la définition d’un attribut de produit sur « Non » et l’exécution d’une recherche entraînait un message d’erreur « Saisissez un terme de recherche et réessayez ».
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/3ea26621>
* _AC-13721_ : magento/module-open-search dépend d&#39;une branche opensearch-php inexistante
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/05dc0bbf>
* _ACP2E-3362_ : la table search_query, lorsqu’elle est de taille importante, a un impact important sur le temps de chargement frontal
   * _Remarque sur la correction_ : amélioration du temps de chargement de la page de liste de recherche. Avant la correction, la page de liste de recherche était retardée en raison d’une requête non optimisée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/55615e61>

### Sécurité

* _AC-11855_ : [Problème] Menu contextuel Paylater de police manquant
   * _Remarque de correction_ : le système permet désormais de charger la police « https://www.paypalobjects.com/webstatic/mktg/2014design/font/PP-Sans/PayPalSansBig-Medium.woff&#39; » sans enfreindre la directive de la politique de sécurité du contenu, ce qui garantit l’affichage correct de la fenêtre contextuelle Paylater. Auparavant, le chargement de la police était refusé en raison d’une violation de la directive de la politique de sécurité du contenu, ce qui provoquait des problèmes d’affichage avec la fenêtre contextuelle Paylater.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38624>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37401>
* _AC-12035_ : [Problème] mettez à jour le texte DOM js.js réinterprété comme HTML.
   * _Remarque à propos de la correction_ : en utilisant innerText, vous éviterez le risque d’injection d’HTML, car ces propriétés s’affichent automatiquement dans le texte fourni à l’aide des caractères spéciaux HTML. Ce correctif permet d’éviter les vulnérabilités de type cross-site scripting (XSS) en traitant l’entrée comme du texte brut plutôt que comme une interprétation d’HTML.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38767>
* _ACP2E-3273_ : ReCaptcha V2 s’affiche incorrectement lors du passage en caisse en allemand
   * _Correction de la note_ : auparavant, le recaptcha de sous l’adresse e-mail de l’extraction semblait sans style pour les langues comportant des mots longs, comme l’allemand. Ensuite, le recaptcha sera identique à tous les éléments recaptcha du reste des zones.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3300_ : Captcha lors de la connexion de l’administrateur ne nécessite pas d’interaction pour certains utilisateurs
   * _Remarque sur la correction_ : ReCaptcha pour la connexion administrateur est validé comme prévu
   * _Contribution du code GitHub_ : <https://github.com/magento/security-package/commit/8f64ab3c>

### Expédition

* _AC-10757_ : [Problème] Correction d’une faute de frappe dans tracking.phtml - les fonctions JS « currier » ont été renommées « carrier » (transporteur)
   * _Remarque de correction_ : le système utilise désormais correctement le terme « carrier » au lieu du « currier » mal orthographié dans les fonctions de gestionnaire JavaScript utilisées dans le modèle de suivi des commandes, ce qui permet d’assurer un nom de fonction et une clarté de code corrects. Auparavant, le terme mal orthographié « currier » était utilisé, ce qui entraînait une confusion et une incohérence potentielles dans la base de code.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/34523>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/33414>
* _AC-11938_ : REPOS UPS « Un envoi ne peut pas avoir un KGS/IN ou un LBS/CM ou un OZS/CM comme unité de mesure »
   * _Correction de la remarque_ : assurez-vous que les taux UPS doivent être visibles dans le passage en caisse et le panier.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38618>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/493e01f5>
* _AC-12938_ : Mises à jour des instructions de configuration « sandbox » et « prod » du REST UPS dans devdoc
* _AC-13172_ : [Problème] Orthographe correcte des variables pour l’adresse du client
   * _Remarque de correction_ : le système épelle désormais correctement les variables pour les adresses des clients, ce qui garantit un affichage précis dans la zone de compte du front-end. Auparavant, une orthographe incorrecte de ces variables pouvait entraîner des erreurs lors des révisions du code local.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/32817>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/32815>
* _ACP2E-2738_ : la fenêtre de suivi indique une date de livraison prévue incorrecte
   * _Corriger la note_ : afficher la date de livraison correcte pour l’opérateur Fedex.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2763_ : Les Taux Du Tableau S&#39;Affichent Toujours Même Si La Livraison Gratuite Est Appliquée
   * _Corriger la note_ : la méthode d&#39;expédition au tarif du tableau s&#39;affiche maintenant même si l&#39;expédition gratuite devient disponible après l&#39;application du coupon
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2765_ : échec du test MFTF AdminCreateShippingLabelTest en raison d&#39;informations d&#39;identification non ajoutées dans l&#39;environnement Jenkins
   * _Remarque sur la correction_ : correctif de test mftf
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-3340_ : l’API de suivi FedEx ne fonctionne pas avec les informations d’identification REST
   * _Remarque sur la correction_ : auparavant, l’intégration de FedEx ne nécessitait pas de clés API supplémentaires pour l’API de suivi. Une nouvelle configuration a été ajoutée pour prendre en charge les clés d’API de suivi.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3354_ : [Cloud] FedEx n&#39;a pas renvoyé les taux négociés sur REST
   * _Note de correction_ : avant la correction, les taux spécifiques au compte FedEx n&#39;étaient pas envoyés sur la réponse, même si selon la documentation de FedEx, ils auraient dû être envoyés. Après la correction, les taux spécifiques au compte sont envoyés sur la réponse en modifiant la requête de notre côté.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/55615e61>

### Évaluation et prévisualisation

* _ACP2E-2901_ : les paramètres de mise à jour planifiée ne sont pas enregistrés s’ils ont été ajoutés lors de la mise à jour
   * _Remarque de correction_ : le système efface désormais correctement les valeurs des attributs de produit dans les mises à jour planifiées suivantes lorsque ces attributs sont modifiés dans la mise à jour en cours d’exécution. Auparavant, lorsqu’un attribut de produit était modifié par une mise à jour planifiée en cours d’exécution, il était impossible d’effacer ces valeurs d’attribut lors de la création d’une mise à jour planifiée, ce qui nécessitait que l’utilisateur les modifie après la création.
* _ACP2E-2999_ : problème de date de début et de fin de la règle de prix du panier non synchronisé avec la mise à jour d’évaluation
   * _Correction de note_ : les dates sont enregistrées en fonction des mises à jour de l’évaluation des règles de prix de panier.
* _ACP2E-3104_ : erreur JS dans l&#39;aperçu intermédiaire
   * _Remarque de correction_ : le fichier form-mini-stub.js se charge maintenant sans erreur de syntaxe Js dans les outils de développement.
* _ACP2E-3162_ : impossible de mettre à jour le contenu échelonné du prix spécial du produit
   * _Correction de note_ : le système permet désormais de modifier la date de fin d’une campagne de mise à jour des prix après son lancement, afin que les utilisateurs puissent apporter les ajustements nécessaires à leurs campagnes. Auparavant, une erreur était générée lors de la tentative de mise à jour de la date de fin d’une campagne active, empêchant les utilisateurs d’apporter des modifications.
* _ACP2E-3453_ : impossible de mettre à jour la mise à jour planifiée lors de l&#39;utilisation d&#39;un attribut de catégorie personnalisée unique
   * _Correction d’une note_ : correction d’un problème en raison duquel la mise à jour d’une mise à jour planifiée pour une catégorie n’était pas possible si la catégorie avait un attribut unique
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/078c387e>

### Ciblage

* _AC-9432_ : [problème] autoriser l’utilisation de plages CIDR dans la liste autorisée de maintenance
   * _Remarque de correction_ : le système prend désormais en charge l’utilisation des plages CIDR dans la liste d’adresses IP autorisées du mode de maintenance, ce qui permet à une plage d’adresses IP de contourner le mode de maintenance. Auparavant, la liste autorisée d’adresses IP du mode de maintenance autorisait uniquement les adresses IP individuelles à contourner le mode de maintenance.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37943>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/30699>

### Taxe

* _AC-13295_ : [Problème] promotion de propriété de constructeur Feature/php8.1 wee graph ql
   * _Correction de la remarque_ : remplacez presque toutes les propriétés par la promotion de propriété du constructeur dans le module aem graph ql :
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39309>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/36975>
* _ACP2E-3193_ : la taxe sur les produits fixes (FPT) ne fonctionne pas avec les produits configurables
   * _Remarque sur la correction_ : FPT pour que les variations de produit configurables fonctionnent correctement.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ec7e32a9>

### Framework de test

* _AC-11654_ : échec du test d’intégration testDbSchemaUpToDate en raison du type de colonne JSON
   * _Remarque de correction_ : le système reconnaît désormais correctement les types de colonnes JSON dans le schéma de base de données lors des tests d’intégration, ce qui empêche les échecs de test en raison d’une incohérence entre le schéma de base de données et le schéma déclaratif. Auparavant, le système identifiait incorrectement les types de colonnes JSON en tant que LONGTEXT dans MariaDB, ce qui entraînait l’échec des tests d’intégration.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ef81f5a2>
* _AC-13362_ : [Problème] Orthographe de correction PHPDoc
   * _Remarque correctif_ : Le système reconnaît désormais correctement les méthodes obsolètes dans les IDE en raison d’une correction orthographique dans PHPDoc. Auparavant, une faute d’orthographe dans PHPDoc empêchait les IDE de reconnaître certaines méthodes comme obsolètes.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/31399>
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/pull/31398>
* _AC-13478_ : MAGETWO-95118 : Vérification du comportement avec le panier persistant après l’expiration de la session
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13716_ : échec des tests d’intégration Magento\NegotiableQuote\Controller\Quote\DownloadTest::testCompanyManagerDownloadWithNQSubPermission
* _AC-13722_ : [Comparaison de base de données] Erreur fatale si la base de données contient un enregistrement sur la règle cible sans condition
   * _Remarque sur la correction_ : plus tôt si la base de données contenait un enregistrement sur la règle cible sans qu&#39;aucune condition ne génère d&#39;erreurs fatales, mais après que l&#39;outil de comparaison de base de données de correction réussisse sans erreurs fatales.
* _AC-13848_ : correction des tests statiques pour permettre leur utilisation par des extensions tierces
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/9e383b4d>
* _ACP2E-3334_ : [interne] l’échec de l’application de la correction n’est pas affiché pendant l’exécution ou dans les journaux
   * _Corriger la note_ : &#39;-
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3458_ : [MFTF] StorefrontCheckoutProcessForQuoteWithoutNegotiatedPriceTest
   * _Remarque sur la correction_ : Mftfs fixes
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/078c387e>

### Framework de l’interface utilisateur

* _AC-12128_ : correctif de vulnérabilité de sécurité Prototype.js CVE-2020-27511
   * _Remarque de correction_ : le système a été mis à jour pour résoudre la vulnérabilité de sécurité CVE-2020-27511 dans Prototype.js 1.7.3, ce qui améliore la sécurité globale du système. Avant cette mise à jour, le système était susceptible de subir un déni de service d’expression régulière (ReDOS) par le biais de la suppression des balises HTML conçues.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12189_ : Grunt Less utilise pub/ préfixe pour les plans source
   * _Remarque concernant la correction_ : le système génère désormais des mappages source less/css sans le préfixe /pub pour les chemins d’accès lors de l’utilisation de grunt, ce qui élimine la nécessité d’une solution de contournement dans la configuration du serveur web. Auparavant, l’utilisation du préfixe /pub dans les chemins d’accès des plans de source nécessitait une configuration spécifique dans le serveur web pour fonctionner correctement.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38837>
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/pull/38840>
* _AC-12432_ : champ de fichier de composant d’IU
   * _Remarque correctif_ : Le système valide désormais correctement le champ de fichier dans un formulaire de composant d’interface utilisateur, ce qui permet au formulaire d’être soumis sans erreur lorsqu’un fichier est sélectionné. Auparavant, la validation échouait même lorsqu’un fichier était sélectionné, ce qui empêchait l’envoi du formulaire.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38908>
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/pull/39004>
* _AC-12645_ : [Problème] Amélioration du format de date dans la console js : passer de 12 heures à 24 heures pour...
   * _Remarque correctif_ : Amélioration du format de date dans la console JS : passer de 12 heures à 24 heures.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38983>
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/pull/38972>
* _AC-12650_ : Problème] ajouter [la génération sourceMap pour moins de fichiers en mode développeur
   * _Remarque de correction_ : le système génère désormais des mappages source pour moins de fichiers en mode Développeur, ce qui facilite l’identification de la source d’un style. Auparavant, l’identification de la source d’un style était difficile lors de l’exécution du système en mode développeur avec une compilation côté serveur moins .
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38982>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38977>
* _AC-1306_ : du contenu statique est déployé pour les modules désactivés
   * _Remarque de correction_ : le système exclut désormais le CSS relatif aux modules désactivés des fichiers de sortie CSS finaux, en veillant à ce que les styles inutiles ne soient pas chargés. Auparavant, le code CSS relatif aux modules désactivés était inclus dans les fichiers de sortie CSS finaux, ce qui entraînait le chargement de styles supplémentaires et inutiles.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/24666>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/32922>
* _AC-13459_ : comportement incohérent dans le tri « en rupture de stock » avec le seuil minimum de stock
   * _Correction de la note_ : le système trie désormais correctement les produits du catalogue en fonction des niveaux de stock, en respectant le seuil minimal de stock défini et en déplaçant régulièrement les articles en rupture de stock au bas de la liste. Auparavant, le comportement du tri était incohérent, les articles n’apparaissant pas toujours dans le bon ordre en fonction de leur niveau de stock, et les modifications du tri pouvaient se produire de manière imprévisible après l’enregistrement, l’actualisation ou la modification de la hiérarchie des catégories.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13472_ : suggestion pour améliorer les rapports d’erreur en cas de problèmes de chargement de required.js.
   * _Remarque de correction_ : cette requête de résolution améliore le message d’erreur lorsque requirejs ne parvient pas à charger un composant.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/36761>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38971>
* _AC-14004_ : les erreurs d&#39;obsolescence de PHP 8.4 provoquent des échecs de build dans 2.4-development
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1da9ba6f>
* _AC-9007_ : [problème] ne chargez pas le contexte du bloc principal sur le front-end
   * _Remarque à propos de la correction_ : le système s’assure désormais que le contexte du bloc principal n’est pas chargé sur le front-end, évitant la création de sessions principales inutiles et de verrous de session potentiels. Auparavant, le système chargeait incorrectement le contexte du bloc principal sur le front-end, ce qui entraînait la création de sessions principales et de verrous de session potentiels.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37617>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/36368>
* _AC-9168_ : [Problème] Supprimer les scripts inutiles
   * _Remarque à propos de la correction_ : le système optimise désormais le temps de chargement des pages en supprimant les scripts JavaScript inutiles de la section d’évaluation, au lieu d’utiliser des styles CSS intégrés pour un code plus efficace et plus lisible. Auparavant, l’utilisation de scripts JavaScript pour la section d’évaluation pouvait potentiellement ralentir le temps de chargement des pages.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37776>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/34643>
* _ACP2E-2529_ : exception lors de la vérification du solde d&#39;une carte cadeau lorsque Recaptcha est activé
   * _Remarque correctif_ : Les utilisateurs pourront récupérer le solde de la carte-cadeau dans l’écran Afficher et modifier le panier. Auparavant, ces détails n’étaient pas affichés lorsque reCAPTCHA était activé.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2-page-builder/commit/4a2795ea>
* _ACP2E-2729_ : [demande de fonctionnalité de clarification] Conformité ADA
   * _Remarque correctif_ : Le système assure désormais la conformité ADA en supprimant les propriétés CSS non prises en charge et en les remplaçant par celles prises en charge dans le fichier print.css. Auparavant, l’utilisation de propriétés CSS non prises en charge entraînait des problèmes de compatibilité du navigateur.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-3061_ : [] code de bibliothèque Cloud Confusion dans effect-drop.js d’AC 2.4.4-p8
   * _Remarque correctif_ : Le système implémente désormais correctement la bibliothèque effect-drop.js, garantissant ainsi le bon fonctionnement des effets de l’interface utilisateur jQuery. Auparavant, la bibliothèque effect-drop.js était écrasée par erreur par la bibliothèque effect-clip.js, ce qui entraînait des problèmes potentiels avec les effets d’interface utilisateur jQuery.
   * _Contribution_ du code GitHub : <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3367_ : en-tête de site | Caractères spéciaux Rupture de la section d’accueil des clients
   * _Remarque du correctif_ : Après la correction, les caractères spéciaux s’affichent correctement dans la section d’accueil des clients.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3561_ : échec de la modification du segment client avec daterange
   * _Remarque à propos de la correction_ : il est possible d’enregistrer le segment client avec la condition de période, lorsqu’une seule des dates a été modifiée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a52ff98f>
