---
source-git-commit: b3059a262fe6144bca47fc9fb1b4d201b38af3ba
workflow-type: tm+mt
source-wordcount: '15251'
ht-degree: 0%

---
# Adobe Commerce a résolu les problèmes (v2.4.8-beta1)

## Correction de problèmes dans la version v2.4.8-beta1

Nous avons corrigé 308 problèmes dans le code principal d’Adobe Commerce 2.4.8. Un sous-ensemble des problèmes résolus inclus dans cette version est décrit ci-dessous.

### API

* _AC-10042_ : l’API REST /V1/transactions renvoie une erreur lorsque parent_txn_id = txn_id
   * _Remarque de correction_ : le système gère désormais correctement les transactions de concept parent et enfant où l’ID de transaction parent est identique à l’ID de transaction, ce qui empêche une boucle infinie lors de l’interrogation du point d’entrée /V1/transactions de l’API REST. Auparavant, ce scénario entraînait une erreur fatale en raison du dépassement du temps d’exécution maximal.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1bafc571>
* _AC-11878_ : problème de type [Graphql] dans 2.4.7
   * _Remarque de correction_ : le système gère désormais correctement les valeurs entières dans la fonction GetCustomSelectedOptionAttributes lors de l’exécution d’une requête GraphQL, ce qui empêche toute erreur liée au type. Auparavant, le lancement d’une requête GraphQL qui utilisait GetCustomSelectedOptionAttributes avec un argument entier entraînait une erreur de type.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38662>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38663>
* _ACP2E-2703_ : API REST affichant les commandes provenant d’un autre site web. 
   * _Remarque de correction_ : le système prend désormais en charge l’accès autorisé de la portée pour les jetons d’administration de l’API REST et les points d’entrée Magento_Sales, en veillant à ce que l’API REST affiche uniquement les commandes auxquelles l’administrateur a accès. Auparavant, l’API REST affichait les commandes de tous les sites web, quel que soit le site web affecté à l’utilisateur administrateur.
* _ACP2E-2755_ : problème avec l’api rest après l’activation de 2FA Duo
   * _Remarque de correction_ : 2FA avec option de sécurité Duo génère désormais la signature correcte pour l’API Rest
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

### API, GraphQL, taxe

* _AC-12060_ : Luma (API REST) et Graphql ne calculent pas les taxes lorsque seul le code postal est fourni.
   * _Remarque sur la correction_ : le système calcule désormais correctement les taxes lorsqu’un seul code postal est fourni, ce qui permet d’obtenir des estimations de taxe précises pour Luma (API REST) et GraphQL. Auparavant, seules les estimations d’expédition étaient calculées et les taxes n’étaient pas incluses lorsqu’un code postal était fourni.

### Compte

* _AC-10782_ : le formulaire d’adresse du client autorise le code aléatoire dans les champs de nom
   * _Remarque de correction_ : le système valide désormais l’entrée dans les champs Prénom et Nom du formulaire d’adresse du client, empêchant l’utilisation de code aléatoire. Auparavant, le système permettait d’utiliser du code aléatoire dans ces champs sans générer d’erreur.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38331>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38345>
* _AC-10990_ : plantage de l’ajout d’adresse à mon compte lors de l’enregistrement
   * _Correction de la remarque_ : le système enregistre désormais correctement les adresses client même lorsque le champ Région n’est pas affiché, ce qui empêche un blocage pendant le processus d’enregistrement. Auparavant, toute tentative d’ajout ou de modification d’une adresse sans champ de région affiché entraînait une erreur d’exception.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38406>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38407>
* _AC-11919_ : administrateur : boutons d’actions de page flottant à gauche et non à droite
   * _Remarque à propos de la correction_ : le système aligne désormais correctement les boutons d’actions de page sur le côté droit de l’en-tête autocollant dans le panneau d’administration, ce qui améliore l’aspect professionnel. Auparavant, ces boutons flottaient incorrectement sur le côté gauche de l’en-tête persistant.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38701>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/44cef3a9>
* _AC-11999_ : erreur dev:di:info dans magento 2.4.7
   * _Remarque de correction_ : le système affiche désormais correctement les paramètres du constructeur lors de l’exécution de la commande dev:di:info, ce qui empêche toute erreur. Auparavant, l’exécution de cette commande entraînait une erreur en raison d’une incohérence de type dans l’argument .
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38740>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-6071_ : le client est connecté mais affiche une erreur 404 en mode frontal.
   * _Remarque à propos de la correction_ : la page du tableau de bord client du storefront se charge désormais comme prévu lorsqu’un client se connecte. Auparavant, les clients pouvaient se connecter, mais cette page affichait une erreur 404. [GitHub-35838](https://github.com/magento/magento2/issues/35838)
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/35838>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/36263>
* _ACP2E-2791_ : impossible d’enregistrer les informations d’attribut du client dans la section Modifier le client d’administration ;
   * _Remarque à propos de la correction_ : l’ID de magasin du client est désormais correctement implémenté par portée de site web pour le formulaire de modification du client administrateur.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/488c1034>
* _ACP2E-3115_ : [Cloud] Impossible de créer un client via l’API lorsque la vente privée est activée
   * _Remarque de correction_ : désormais, le client peut être créé par un utilisateur administrateur authentifié, ainsi qu’avec un jeton d’intégration authentifié via l’api REST lorsque la restriction de site web est activée.

### Interface utilisateur d’administration

* _AC-11588_ : la validation des données a réussi et le bouton Importer est présent lors de l’importation de produits avec le comportement Remplacer
   * _Remarque sur la correction_ : le système valide désormais correctement les données et masque le bouton « Importer » pendant le processus d’importation du produit avec le comportement « Remplacer », empêchant tout remplacement involontaire des données. Auparavant, le système ne validait pas correctement les données et affichait le bouton « Importer », ce qui entraînait des incohérences potentielles des données.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/0574ac23>
* _AC-12167_ : [Bug] Magento 2.4.7 n’autorise pas les photos de produit avec extension de fichier majuscule.
   * _Remarque de correction_ : le système accepte désormais les chargements d’images de produit avec des extensions de fichier de lettre majuscule, assurant ainsi un processus de création de produit fluide. Auparavant, les chargements d’images avec des extensions de fichier en majuscules étaient refusés, ce qui forçait les utilisateurs à modifier l’extension de fichier en minuscules.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38831>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-6975_ : [Problème] Définissez le mode d’indexeur par défaut sur « schedule »
   * _Remarque sur la correction_ : tous les nouveaux indexeurs sont configurés par défaut en mode **[!UICONTROL Update by Schedule]**.  Auparavant, le mode par défaut était **[!UICONTROL Update on Save]**. Les indexeurs existants ne sont pas affectés. [GitHub-36419](https://github.com/magento/magento2/issues/36419)
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/36419>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/0b410856>
* _AC-7700_ : [Problème] Déposez les tables de journal des modifications de l&#39;indexeur sur le désabonnement mview
   * _Remarque de correction_ : le système supprime désormais automatiquement les tables de journaux des modifications inutilisées lorsqu&#39;un index passe de « mise à jour selon le calendrier » à « mise à jour selon l&#39;enregistrement », marquant l&#39;index comme non valide pour s&#39;assurer qu&#39;aucune entrée n&#39;est manquée. Auparavant, le fait de passer un index à « mettre à jour lors de l&#39;enregistrement » laissait des tables de journaux des modifications inutilisées dans le système et marquait tous les index modifiés comme « valides ».
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/29789>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/25859>
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
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/001e5188>, <https://github.com/magento/magento2-page-builder/commit/60140cd2>
* _ACP2E-2978_ : l&#39;enregistrement d&#39;un produit par un utilisateur administrateur avec une étendue de rôle différente remplace/supprime les informations existantes sur les produits associés dans le produit
   * _Remarque sur la correction_ : auparavant, avant la correction, les produits associés étaient réinitialisés et étaient vides lorsque l’utilisateur secondaire en charge de l’administration cliquait sur le bouton d’enregistrement sans modifier les produits associés. Après ce correctif, l’utilisateur administrateur secondaire clique sur le bouton d’enregistrement et le produit ne se réinitialise pas et est enregistré avec succès.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3033_ : impossible d&#39;exporter plus de 200 commandes
   * _Remarque de correction_ : les limites du serveur pour la taille de requête des identifiants sélectionnés précédemment envoyés ont été négligées en modifiant la requête HTTP de GET à POST afin de résoudre le problème. Auparavant, en raison des limitations du serveur pour la taille de requête GET, le problème était rencontré.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3037_ : message de validation de la page de passage en caisse incorrect.
   * _Correction de la note_ : si un champ obligatoire reste vide, tel que « adresse », la validation côté serveur n’affichera pas le message. La validation côté client garantit que la notification d’erreur de champ obligatoire s’affiche, indiquant « Ceci est un champ obligatoire ». Auparavant, le message « l’adresse est requise » s’affichait si un champ obligatoire restait vide, en plus du message de validation côté client.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3125_ : problème de modèle de réinitialisation du mot de passe avec l’utilisateur administrateur
   * _Remarque à propos de la correction_ : le problème a été résolu avec la clé appropriée, qui inclut désormais le nom d’utilisateur de l’administrateur dans le modèle d’e-mail et renseigne correctement l’objet. Auparavant, le problème provenait d’une clé obsolète utilisée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3149_ : barres obliques doubles dans l’URL du segment client
   * _Remarque de correction_ : les barres obliques doubles n’apparaissent pas dans l’URL lorsque l’utilisateur clique sur « Réinitialiser le filtre » dans la grille.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3171_ : la DCO n&#39;est pas disponible pour les pays spécifiques autorisés
   * _Corriger la note_ : désormais, le paiement à la livraison est disponible pour les pays spécifiques autorisés dès que cela est nécessaire et   AC-3216 fonctionne comme prévu.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3178_ : impossible de mettre à jour le statut de la commande créée personnalisée
   * _Corriger la note_ : &#39;
Nous pouvons désormais mettre à jour les statuts de commande personnalisés, alors qu’auparavant le statut ne pouvait être modifié que si le statut actuel était soit « traitement » soit « fraude ».
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38659>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/8459b17d>

### Interface utilisateur d’administration, catalogue

* _ACP2E-2708_ : impossible de modifier les positions pour les produits de la catégorie dans le site web autorisé en tant qu’utilisateur administrateur restreint
   * _Remarque de correction_ : permet à un utilisateur administrateur restreint d’ajouter et de trier des produits sous une catégorie contenue dans la catégorie racine affectée sous un site web restreint.

### Interface utilisateur d’administration, Performances

* _ACP2E-3169_ : après la mise à jour vers la version 2.4.5-p8, 500 erreurs se produisent lors de la création d’une commande à partir de l’administrateur
   * _Remarque de correction_ : auparavant, lors de l’activation de la minimisation HTML, une commande de l’administrateur ne pouvait pas être passée. Désormais, lorsque la minimisation HTML est activée, la commande auprès de l’administrateur peut être passée avec succès.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b21e5d91>

### Interface utilisateur d’administration, Expédition

* _ACP2E-2519_ : le nombre de codes coupon n’est pas mis à jour dans le   Colonne « Temps utilisé » de l’onglet Gérer les codes coupon si une commande est passée avec une expédition multiple.
   * _Corriger la note_ : Auparavant, lorsqu&#39;une commande était passée avec une expédition multiple, le nombre de codes de coupon n&#39;était pas mis à jour dans la colonne « Temps utilisé » de l&#39;onglet Gérer les codes de coupon. Désormais, le nombre correct s’affiche à la fois dans le « Temps utilisé », reflétant les valeurs souhaitées avec une expédition multiple.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/4745100c>

### Analyses / Rapports

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

### Analytics/Reporting, B2B

* _ACP2E-2300_ : B2B - le plan du site inclut des produits/catégories non affectés au catalogue partagé
   * _Remarque de correction_ : limitez les catégories et produits générés par le plan de site aux catégories et produits affectés uniquement au catalogue public partagé et/ou à la configuration des autorisations de catégorie de catalogue.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ea79f7dd>

### Analytics/Création de rapports, Cloud

* _ACP2E-3067_ : Magento ignore la plupart des transactions New Relic cron #34108
   * _Correction de la note_ : AC signale correctement les transactions liées aux tâches cron à NewRelic. Auparavant, certaines transactions liées à la tâche cron s’affichaient sous la forme « Autre transaction/Action/inconnu » dans NR
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/35b1b1da>

### B2B

* _ACP2E-2873_ : [Cloud] L’affichage des prix dans la version pour mobiles et pour ordinateurs de bureau n’est pas le même que dans « Mes devis »
   * _Corriger la note_ : La ligne Inclure la taxe superflue n&#39;apparaît plus dans le devis négociable lorsque la section du prix total du catalogue est dépensée.
* _ACP2E-3044_ : bordures inutiles sur la section Mes commandes
   * _Remarque sur la correction_ : Auparavant, un conteneur supplémentaire (références de commande) était créé pour appliquer des classes CSS supplémentaires, ce qui entraînait l’apparition de lignes de bordure inutiles sous le numéro de commande dans la section Mes commandes , qui n’est pas visible actuellement.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/9af794a4>

### B2B, Catalogue

* _ACP2E-2860_ : produits/catégories visibles lors de la réindexation lors de l’utilisation de NoDDL et des autorisations de catégorie
   * _Remarque de correction_ : évitez d’afficher sur les catégories restreintes du storefront et leur contenu lorsque l’indexation des autorisations de catalogue est en cours.

### B2B, Framework

* _AC-9607_ : échec du filtrage de la grille de l’entreprise, puis de la tentative d’exportation CSV de la grille et exception
   * _Remarque de correction_ : le système permet désormais d’exporter au format CSV les données de la grille Entreprises dans le panneau d’administration, même lorsque des filtres tels que « Solde restant à payer » et « Type d’entreprise » sont appliqués. Auparavant, l’application de certains filtres et la tentative d’exportation des données de la grille entraînaient un échec et une exception.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/44cef3a9>

### Braintree

* _BUNDLE-3367_ : Payer via LPM
   * _Remarque de correction_ : le système effectue désormais correctement le rendu des modes de paiement locaux (LPM) lors du chargement initial, même lorsque les adresses d’expédition et de facturation d’un client connecté ne correspondent pas, ce qui garantit un processus de paiement fluide. Auparavant, une incohérence entre les adresses d’expédition et de facturation d’un client empêchait le rendu du LPM, ce qui entraînait des perturbations potentielles lors du passage en caisse.
   * _Contribution du code GitHub_ : <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3368_ : configurable avec Virtual comme produit enfant
   * _Correction de note_ : Le système permet désormais des modes de paiement express pour les produits configurables qui ont un produit enfant virtuel, assurant ainsi un processus de paiement fluide. Auparavant, les modes de paiement express n’étaient pas disponibles lorsqu’un produit configurable avec un produit enfant virtuel était ajouté au panier.
   * _Contribution du code GitHub_ : <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3369_ : erreur d’échec de la vérification du CVV
   * _Contribution du code GitHub_ : <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3370_ : Mise en chambre forte via le compte Area Issues 247
   * _Correction de note_ : le système permet désormais aux clients d’enregistrer les informations de leur nouvelle carte ou de leur compte PayPal sur plusieurs sites web sans rencontrer d’erreurs d’autorisation. Auparavant, les clients ne pouvaient pas enregistrer les nouveaux modes de paiement sur différents sites web et un message d’erreur d’autorisation leur était présenté.
   * _Contribution du code GitHub_ : <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3371_ : expédier à une adresse d&#39;un autre pays
   * _Correction de note_ : le système permet désormais de traiter les transactions sans erreur lors de l’expédition vers une adresse d’un autre pays, ce qui garantit un processus de passage en caisse fluide. Auparavant, toute tentative d’expédition vers une adresse provenant d’un autre pays entraînait des erreurs de console, même si aucune erreur visible n’était générée sur le serveur frontal.
   * _Contribution du code GitHub_ : <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3372_ : Carte de crédit - Démontage
   * _Remarque sur la correction_ : le système gère désormais correctement la désactivation des composants PayPal Braintree lorsqu’un client revient de la page de paiement à la page d’expédition, ce qui évite les erreurs et garantit que les boutons PayPal Express s’affichent correctement. Auparavant, le fait de revenir à la page d’expédition à partir de la page de paiement entraînait parfois une erreur lors de la tentative de démontage des composants PayPal Braintree.
   * _Contribution du code GitHub_ : <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3373_ : Rappel d&#39;expédition pour PayPal Express
   * _Correction de note_ : le système affiche désormais correctement les modes d’expédition disponibles dans la fenêtre modale PayPal Express, ce qui permet aux clients de sélectionner leur mode d’expédition préféré avant de passer à la page de révision ou de terminer leur transaction. Auparavant, aucune méthode d&#39;expédition n&#39;était disponible dans la fenêtre modale PayPal Express, ce qui obligeait les clients à sélectionner une méthode d&#39;expédition sur une page de révision distincte avant de pouvoir terminer leur transaction.
   * _Contribution du code GitHub_ : <https://github.com/magento/ext-braintree/pull/204>

### Panier et passer en caisse

* _AC-10660_ : l’exception n’est pas gérée correctement lors de l’ajout d’un produit au panier dans la page comparer des produits
   * _Remarque de correction_ : le système gère désormais correctement les exceptions lors de l’ajout d’un produit au panier à partir de la page Comparer les produits , affichant un message du gestionnaire de messages dans le contrôleur. Auparavant, une exception entraînait le renvoi d’une page codée en JSON au lieu d’être correctement capturée et gérée.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38200>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38257>, <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10698_ : GTag n&#39;envoie pas les prix et totaux des transactions.
   * _Correction de note_ : le système envoie désormais correctement les prix et totaux des transactions à Google Tag lorsque GTag est activé, assurant ainsi un suivi précis des données d’e-commerce. Auparavant, la devise était incorrectement envoyée dans le cadre des commandes « all », plutôt que d’être associée à la commande individuelle.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37348>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37504>, <https://github.com/magento/magento2/pull/37349>
* _AC-11641_ : [Problème] [Passage en caisse] directives dépendantes mises à jour dans le modèle d’e-mail de paiement ayant échoué
   * _Correction de la note_ : le système omet désormais correctement l’adresse et le mode d’expédition du modèle d’e-mail de paiement en échec pour les produits virtuels, en s’assurant que seules les informations pertinentes sont incluses dans l’e-mail. Auparavant, l’e-mail de paiement ayant échoué pour les produits virtuels incluait incorrectement l’adresse et le mode d’expédition.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/32781>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/32511>
* _AC-11876_ : [Problème] régression des règles de vente dans 2.4.7
   * _Correction de la note_ : le système valide désormais correctement les règles de vente, ce qui empêche l’application d’un code de coupon à un panier lorsque la condition du produit ne correspond à aucun nom de produit. Auparavant, une règle de vente pouvait être appliquée et une remise accordée sur le montant de l’expédition, même si la condition du produit ne correspondait à aucun nom de produit.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38671>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/0574ac23>
* _AC-11993_ : [Problème] Le chargeur bloque les méthodes d’expédition après la modification du code postal et les règles de validation des taux d’expédition
   * _Correction de note_ : le système gère désormais correctement les méthodes d’expédition personnalisées sans règles de validation des taux d’expédition, en veillant à ce que le chargeur ne bloque pas les méthodes d’expédition après le changement du code postal dans l’adresse d’expédition lors du passage en caisse. Auparavant, la modification du code postal dans l’adresse d’expédition lors du passage en caisse entraînait le blocage du chargeur des méthodes d’expédition et ne disparaissait pas lorsque des méthodes d’expédition personnalisées sans règles de validation des taux d’expédition étaient utilisées.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38742>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1bafc571>
* _AC-12170_ : la fonctionnalité de code promotionnel ne fonctionne pas correctement dans la page de passage en caisse de Magento 2.4.7.
   * _Correction de la note_ : le système active désormais le champ d’entrée code de remise/coupon sur la page de passage en caisse pour les produits virtuels et téléchargeables, ce qui permet aux utilisateurs d’appliquer les codes de remise comme prévu. Auparavant, la saisie du code de remise/coupon était désactivée et le texte du titre du bouton affichait « Annuler le coupon », ce qui empêchait les utilisateurs d’appliquer des codes de remise.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38826>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1bafc571>
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
   * _Correction de note_ : le système n’enregistre désormais qu’une seule fois une nouvelle adresse client si la création de la commande a échoué, ce qui empêche la création de plusieurs adresses identiques en cas d’erreurs de placement de commande. Auparavant, le système enregistrait une nouvelle adresse chaque fois qu’une tentative de placement de commande était effectuée, que la commande ait été créée avec succès ou non.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/001e5188>, <https://github.com/magento/inventory/commit/2ebcef39>
* _ACP2E-3004_ : la réorganisation d’une commande client via un formulaire de commande invité génère un panier vide
   * _Correction de note_ : auparavant, lorsque le client passait une nouvelle commande sur la page Commandes et retours, il était redirigé vers la page de connexion. Une fois ce correctif appliqué, le client enregistré est correctement redirigé vers la page Afficher le panier lors d’une nouvelle commande. Le flux fonctionne de la même manière que pour les clients invités.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3025_ : l’utilisateur administrateur avec des ressources de rôle limitées ne peut pas afficher les paniers
   * _Remarque de correction_ : auparavant, l’administrateur restreint ne pouvait pas voir le panier abandonné du panneau d’administration pour un site web associé. Une fois ce correctif appliqué, l’administrateur restreint peut voir le panier abandonné dans le panneau d’administration.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d1f7dc95>

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
* _AC-12076_ : [Problème] Corrigez le libellé de l’élément de filtre sur la navigation superposée.
   * _Remarque de correction_ : le système utilise désormais correctement les mots « élément » et « éléments » dans l’élément de filtre de navigation superposé, ce qui améliore la clarté et la précision des descriptions des filtres. Auparavant, ces mots n’étaient pas utilisés correctement, ce qui pouvait prêter à confusion pour les utilisateurs et utilisatrices qui parcouraient les options de filtre.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38789>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37852>
* _AC-12164_ : le format de date et d&#39;heure de l&#39;option personnalisée ne fonctionne pas
   * _Remarque de correction_ : le système applique désormais correctement le format de date configuré aux options personnalisées de produit de type Date, en s’assurant que le format de date s’affiche correctement sur le front-end. Auparavant, les modifications apportées à la configuration du format de date n’étaient pas répercutées sur le front-end pour les options personnalisées de produit de type Date.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/32990>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38925>
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
   * _Corriger la note_ : le stock s’affiche désormais en fonction du magasin sélectionné.
   * _Contribution du code GitHub_ : <https://github.com/magento/inventory/commit/bdbf97ea>
* _ACP2E-2621_ : le contenu du widget n’est pas mis à jour sur la page cms
   * _Remarque de correction_ : le système met désormais à jour le contenu du widget sur une page CMS lorsqu’un produit est défini comme nouveau et enregistré, en s’assurant que la page affiche la collection de produits mise à jour. Auparavant, la page n’était pas mise à jour pour afficher le nouveau produit en raison d’identités de cache incorrectes utilisées pour le widget dans le cache.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/f89a447e>
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
   * _Remarque de correction_ : le message d’erreur approprié a été ajouté pour s’afficher lorsque l’identifiant du site web est incorrect dans la requête. Auparavant, il n’existait aucune validation lorsque l’ID de site web était incorrect dans la requête.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2785_ : l&#39;image du produit est perdue après la suppression d&#39;une mise à jour planifiée existante qui n&#39;affecte pas l&#39;image
   * _Remarque de correction_ : les images du produit ne sont pas supprimées lors de la suppression de la mise à jour de l’évaluation.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-2799_ : [Cloud] Prix de produit groupé incorrect lorsqu’il est utilisé avec des prix de niveau
   * _Corriger la note_ : précédemment, lors du calcul de certaines remises en pourcentage arrondies à 2 décimales maximum, générait différents prix finaux pour le panier et la page de liste de produits/page de détails des produits. Une fois ce correctif appliqué, le prix final du bundle du produit est le même que dans les pages de détails du produit, de liste des produits et de panier.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38091>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2805_ : la règle des promotions de catalogue ne fonctionne pas avec l&#39;attribut quantity_and_stock_status
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
   * _Remarque sur la correction_ : les images et les vidéos du produit sont configurées dans la portée globale. Étant donné que vous ne pouvez pas avoir une vidéo de produit dans une portée et pas dans une autre, le paramètre de clé API Youtube a été défini sur une portée globale.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2964_ : mise à jour de l’URL [Cloud] uniquement pour store_id=0
   * _Remarque de correction_ : le « chemin URL » est désormais stocké avec l’identifiant de magasin correct. Auparavant, l’ID de magasin était incorrect, ce qui entraînait le maintien de chemins d’URL incorrects dans la base de données lors du déplacement de catégories.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3009_ : async.operations.all s’est exécuté et a créé une erreur.
   * _Remarque sur la correction_ : les données de lien de produit incorrectes dans les appels API REST ne provoquent plus d’erreurs critiques.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-3029_ : [Cloud] Problème mobile : impossible de pincer l’image du PDP uniquement
   * _Remarque à propos de la correction_ : le système prend désormais en charge la fonctionnalité de pincement pour zoomer sur les images de la page des détails du produit dans la vue mobile de Chrome, ce qui améliore l’expérience de l’utilisateur mobile. Auparavant, le double-appui sur l’image en mode mobile dans Chrome n’effectuait pas un zoom avant sur l’image comme prévu.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3058_ : libellé manquant dans LayeredNavigation avec le nom d&#39;option 0
   * _Correction de la note_ : le problème a été résolu en ignorant un vérificateur de valeur vide pour la valeur d’attribut 0. Auparavant, il était considéré comme vide et provoquait le problème.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-3069_ : les clients voient les prix d&#39;autres groupes de clients
   * _Correction de la note_ : correction d’un problème en raison duquel les informations liées au groupe de clients étaient enregistrées dans un segment incorrect en raison de l’ancienne valeur de X-Magento-Vary dans la requête.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3076_ : erreur lors de la suppression des options de lot
   * _Remarque de correction_ : le système supprime désormais correctement les options de lot sans déclencher d’erreur ni empêcher la page de répondre. Auparavant, toute tentative de suppression des options de lot entraînait une erreur « La page ne répondait pas » et empêchait l’enregistrement du produit.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3094_ : problème de navigateur d&#39;autorisations de catégorie sans mémoire
   * _Remarque de correction_ : l’interface utilisateur des autorisations de catégorie a été repensée pour permettre le rendu d’un grand nombre d’autorisations à l’aide du composant d’interface utilisateur prêt à l’emploi et de la pagination. Auparavant, les autorisations de catégorie entraînaient le blocage du navigateur avec une grande quantité d’autorisations attribuées à la catégorie.
* _ACP2E-3100_ : le fichier image [Cloud] n’existe pas dans le journal d’erreurs New Relic
   * _Remarque de correction_ : le système synchronise désormais les images d’espace réservé personnalisées avec le stockage local, en s’assurant qu’elles s’affichent correctement lors de l’utilisation du stockage distant tel qu’AWS S3. Auparavant, les images d’espace réservé personnalisées ne s’affichaient pas lors de l’utilisation du stockage distant, ce qui entraînait un affichage d’image rompu et des journaux d’erreurs.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3126_ : la réponse GQL de la Galerie de médias du produit [Cloud] n’est pas triée par position de l’image
   * _Remarque de correction_ : le système trie désormais correctement les éléments de la galerie de médias par position dans la réponse GraphQL, en veillant à l’ordre d’affichage précis. Auparavant, les éléments de la galerie de médias n’étaient pas triés par position, ce qui entraînait un ordre d’affichage incorrect.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37671>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3136_ : les éléments de sous-catégorie [Cloud] ne s’affichent pas lors de la modification des widgets sur le serveur principal de l’administrateur
   * _Remarque sur la correction_ : l’arborescence de catégories sur la nouvelle page de widget ne devrait plus rencontrer de problèmes lors du chargement des catégories de niveau 5 et ultérieure. Auparavant, certaines catégories étaient manquantes lors du chargement de l’arborescence au-delà des catégories de niveau 5.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/148c3ead>

### Catalogue, Framework

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

### Catalogue, tarification, évaluation et prévisualisation

* _ACP2E-2672_ : le point d’entrée de l’API Prix spécial [Cloud] renvoie une erreur lors de la mise à jour simultanée d’un grand nombre de produits
   * _Remarque de correction_ : désormais, l’API de mise à jour en bloc Prix spéciaux crée une seule campagne pour chaque période au lieu de plusieurs mises à jour planifiées pour chaque produit et période. En outre, il prend en charge les requêtes d’API simultanées pour accélérer le traitement d’un grand nombre de SKU.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/f89a447e>

### Catalogue, produit

* _AC-7050_ : l&#39;arborescence de sélection de catégorie dans l&#39;édition du produit n&#39;est pas dans le même ordre que celui défini dans Catalogue->Catégories
   * _Remarque de correction_ : le système affiche désormais correctement l’arborescence de sélection des catégories dans la section d’édition du produit, dans l’ordre défini dans Catalogue->Catégories, ce qui facilite l’administration des produits dans les catalogues volumineux. Auparavant, l’arborescence de catégories de la section de modification de produits s’affichait dans l’ordre de création des catégories, quel que soit l’ordre d’affichage défini dans Catalogue->Catégories.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/36101>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/36104>

### Catalogue, recherche

* _ACP2E-2757_ : les produits ne s’affichent pas dans la catégorie et la recherche, mais les liens directs fonctionnent
   * _Remarque sur la correction_ : auparavant, l’attribut personnalisé Oui/Non avec price_* attribute_code ne fonctionnait pas avec l’indexation. Après ce correctif, l’attribut personnalisé Oui/Non fonctionne comme prévu.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-3053_ : [Cloud] Erreur de recherche élastique sur certaines pages de catégorie
   * _Correction de la note_ : précédemment, avec le ticket de configuration mentionné, lorsque nous fixons le prix 0 pour plusieurs produits, une exception est générée sur la page de catégorie front-end. Une fois ce correctif appliqué lorsque le prix de plusieurs produits est égal à 0 et que nous chargeons la page de catégorie sur le front-end, aucune exception ne sera générée et la page de catégorie sera chargée correctement.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c8931218>

### Cloud

* _ACP2E-3010_ : [Cloud] PHPSESSID modifie chaque requête POST
   * _Remarque de correction_ : PHPSESSID ne se régénère plus sur les requêtes POST sur la zone frontale pour un client connecté si le cache L2 Redis est activé et que le client a été mis à jour à partir du serveur principal
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/6a185204>

### Contenu

* _AC-10539_ : [problème] lié à l’affichage des prix dans le widget Récemment consultés
   * _Remarque à propos de la correction_ : le système affiche désormais correctement le prix des produits simples en rupture de stock dans le widget « Produit récemment consulté », ce qui garantit la cohérence entre tous les widgets et toutes les pages de liste de produits. Auparavant, le prix des produits simples en rupture de stock n’était pas affiché dans le widget « Produit récemment consulté » en raison d’une condition dans les modèles de chargement de prix.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38167>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38159>
* _AC-10596_ : [Problème] Corrigez la faute de frappe et la grammaire dans le fichier acl.xsd.
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
* _AC-9638_ : [problème] problème de chargement de fichier dans l’éditeur WYSIWYG sur la page du produit
   * _Remarque sur la correction_ : le système affiche désormais correctement l’arborescence de dossiers et permet les chargements d’images dans l’éditeur WYSIWYG sur la page du produit, même après avoir développé l’onglet « Image et vidéos » en premier. Auparavant, le développement de l’onglet « Image et vidéos » entraînait d’abord l’affichage de l’arborescence de dossiers et un message d’erreur lors de la tentative de chargement d’une image dans l’éditeur de WYSIWYG.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38026>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38025>
* _ACP2E-2392_ : problème de bloc dynamique [On-PREM]
   * _Remarque sur la correction_ : les widgets sont désormais correctement rendus dans les blocs dynamiques.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2606_ : l’URL du cookie YouTube ne fonctionne pas dans Page Builder
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
* _ACP2E-3127_ : imagecreatetruecolor() : la #2 de l’argument ($height) doit être supérieure à 0. Impossible de charger une image spécifique
   * _Remarque de correction_ : résolution du problème provoquant des erreurs dans l’administration lors du chargement d’images d’une hauteur de 0 via la galerie de médias, et réussite de la synchronisation des ressources à l’aide de la commande de synchronisation. Auparavant, ne pouvait pas charger l’image via la galerie de médias et la commande de synchronisation échouait également lorsqu’une image spécifique se trouvait dans la galerie.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3154_ : Prototype.js Array.from en conflit avec l’API Google Maps
   * _Correction d’une remarque_ : les cartes Google sont désormais correctement rendues dans l’éditeur PageBuilder. Auparavant, une erreur Javascript empêchait le rendu correct des cartes Google.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/148c3ead>

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

### Framework

* _AC-10654_ : V1/customers/password endpoint question/problème
   * _Remarque de correction_ : le système respecte désormais les contraintes définies dans l’interface utilisateur graphique de gestion lors du traitement des demandes de changement de mot de passe via l’API, empêchant tout abus potentiel de la fonction de réinitialisation du mot de passe. Auparavant, l’API pouvait traiter les demandes de changement de mot de passe en dehors des règles définies dans l’interface utilisateur graphique de gestion, ce qui pouvait permettre de disposer d’un flux constant d’e-mails de réinitialisation si des e-mails valides étaient connus.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38238>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10721_ :
   * _Remarque de correction_ : mettez à niveau les dépendances du compositeur league/flysystem vers la dernière version
   * _Problème GitHub_ : &lt;<https://github.com/magento/magento2/commit/91cb4d46>>
   * _Contribution du code GitHub_ : mettez à niveau les dépendances du compositeur 2.x league/flysystem vers la dernière version 3.x
* _AC-10838_ : processus d’indexation des erreurs du processus d’index de recherche catalogue
   * _Note de correction_ : Le système exécute maintenant correctement la commande de réindexation sans rencontrer d&#39;erreur, quelle que soit la version libxml compilée avec PHP. Auparavant, l&#39;exécution de la commande re-index provoquait une erreur de type « Erreur de processus d&#39;index de recherche de catalogue pendant le processus d&#39;indexation » lorsque PHP était compilé avec certaines versions de libxml.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38254>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38553>, <https://github.com/magento/magento2/commit/0574ac23>
* _AC-10941_ : ajout de filtres created_at, status et grand_total à la requête Commandes client et correction de plusieurs échecs de filtres
   * _Remarque sur la correction_ : le système prend désormais en charge l’utilisation des filtres created_at, status et grand_total dans les requêtes Commandes client et a résolu un problème en raison duquel plusieurs filtres n’étaient pas appliqués correctement. Auparavant, le système ne prenait pas en charge ces filtres et ne pouvait pas les appliquer tous lorsque plusieurs d’entre eux étaient utilisés dans une requête.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38392>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/36949>
* _AC-10971_ : https://github.com/magento/magento2/issues/38415
   * _Note de correction_ : PHP 8.2/8.3, une seule dépendance échoue le php linter en ce moment : league/flysystem
   * _Problème GitHub_ : &lt;<https://github.com/magento/magento2/commit/672a2e61>>
   * _Contribution du code GitHub_ : le système prend désormais en charge PHP 8.2/8.3 en mettant à jour le package league/flysystem vers la version 3.0.20, en veillant à ce qu’aucune erreur de linting PHP ne se produise. Auparavant, l&#39;exécution de fichiers PHP via le linter PHP avec PHP 8.3 entraînait des erreurs de linting dans le package league/flysystem.
* _AC-10991_ : inondation aléatoire de requêtes provenant de blocs de ventes croisées / de ventes incitatives et d’indexation des prix
   * _Remarque à propos de la correction_ : le système optimise désormais les requêtes provenant des blocs de ventes croisées, de montée en gamme et connexes, ce qui améliore les performances et empêche le site de tomber en panne en raison de requêtes excessives. Auparavant, le système pouvait être surchargé de requêtes provenant de ces blocs, ce qui provoquait des ralentissements importants et pouvait entraîner l’arrêt du site.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/36667>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38050>
* _AC-11388_ :
   * _Remarque sur la correction_ : vérifiez que la suppression du dossier supprime S3 et les répertoires de stockage de fichiers locaux
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
* _AC-11651_ : Magento tente de modifier la propriété en lecture seule dans la méthode __wakeup de LoggerProxy
   * _Remarque de correction_ : le système permet désormais de modifier les propriétés précédemment en lecture seule dans la méthode de réveil __wakeup de LoggerProxy, assurant ainsi un fonctionnement fluide sans forcer les utilisateurs à employer une solution de contournement. Auparavant, une tentative de réaffectation de la valeur d’une propriété en lecture seule dans la méthode __wakeup de LoggerProxy provoquait des problèmes.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38526>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-11673_ :
   * _Remarque sur la correction_ : examiner les dernières versions de php-amqplib/php-amqplib
   * _Problème GitHub_ : &lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _Contribution du code GitHub_ : mise à jour de la dernière version de php-amqplib/php-amqplib :^3.x
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
* _AC-11808_ :
   * _Remarque sur la correction_ : examiner et mettre à niveau la liste des dépendances principales d’Adobe Commerce
   * _Contribution du code GitHub_ : mise à niveau de la liste des dépendances principales d’Adobe Commerce nécessaire 
* _AC-11819_ : le cache FPC intégré est endommagé dans la version 2.4.7 pour certaines configurations
   * _Remarque de correction_ : le système met désormais correctement en cache les pages lorsque le paramètre MAGE_RUN_CODE est défini, garantissant ainsi des performances optimales. Auparavant, les pages n’étaient pas mises en cache dans ces conditions, ce qui entraînait des problèmes de performances potentiels.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38626>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38646>, <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-11829_ : [Problème] Correction de l’incohérence dans la gestion des exceptions entre les modes de développement et de production
   * _Remarque de correction_ : le système gère désormais de manière cohérente les exceptions entre les modes de développement et de production, ce qui empêche toute redirection inattendue vers la page de connexion lorsqu’une exception est générée. Auparavant, une incohérence dans la gestion des exceptions pouvait entraîner une redirection vers la page de connexion en mode de production au lieu d’afficher le message d’exception.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38639>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37712>
* _AC-11852_ : remplacer la traduction « Compte PayPal » dans token_list.phtml
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
* _AC-11911_ :
   * _Remarque de correction_ : nettoyage css jQuery/fileuploader après la migration vers la bibliothèque uppy
   * _Problème GitHub_ : &lt;<https://github.com/magento/magento2/commit/7cabfb46>>
   * _Contribution du code GitHub_ : bibliothèque jQuery/fileUploader supprimée, car elle a été migrée vers la bibliothèque Uppy.
* _AC-12002_ : [Problème] [Affichage] Suppression de l’espace supplémentaire dans le lien et la balise du script
   * _Remarque à propos de la correction_ : le système s’assure désormais qu’il n’y a pas d’espace supplémentaire dans les balises de lien et de script, fournissant ainsi un code plus propre et plus efficace. Auparavant, il était possible de trouver des espaces doubles entre les attributs dans les balises de lien et de script.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/32920>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/32919>
* _AC-12015_ :
   * _Remarque de correction_ : nettoyage du dossier ExtJs après la migration vers la bibliothèque jsTree.
   * _Problème GitHub_ : &lt;<https://github.com/magento/magento2/commit/7cabfb46>>
   * _Contribution du code GitHub_ : dossier extJs supprimé, car la fonctionnalité associée a été migrée vers jsTree.
* _AC-12022_ :
   * _Remarque de correction_ : mettez à niveau la dépendance du système monologue/monologue vers la dernière version majeure.
   * _Problème GitHub_ : &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _Contribution du code GitHub_ : le système a été mis à jour pour utiliser la dernière version majeure de la bibliothèque « monolog/monolog:^3.x », ce qui garantit la compatibilité et de meilleures performances. Auparavant, le système utilisait une version obsolète de la bibliothèque « monologue/monologue », ce qui pouvait entraîner des problèmes et des limitations potentiels.
* _AC-12023_ :
   * _Remarque de correctif_ : mettez à niveau la dépendance wikimedia/less.php vers la dernière version majeure.
   * _Problème GitHub_ : &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _Contribution du code GitHub_ : le système a été mis à jour afin d’utiliser la dernière version majeure 5.x de la bibliothèque « wikimedia/less.php », assurant ainsi la compatibilité et des fonctionnalités à jour. Auparavant, le système utilisait une version obsolète de la bibliothèque, ce qui pouvait entraîner des problèmes de sécurité.
* _AC-12024_ :
   * _Remarque de correction_ : mettez à niveau la dépendance de la bibliothèque jquery/validate vers la dernière version mineure.
   * _Problème GitHub_ : &lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _Contribution du code GitHub_ : mettez à niveau la dépendance de bibliothèque jquery/validate vers la dernière version mineure 1.20.0
* _AC-12025_ :
   * _Remarque de correctif_ : mettez à niveau la dépendance du système moment.js vers la dernière version mineure.
   * _Problème GitHub_ : &lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _Contribution du code GitHub_ : mettez à niveau la dépendance du système moment.js vers la dernière version mineure, la version 2.30.1
* _AC-12267_ :
   * _Remarque de correction_ : prend en charge les reprises de connexion pour la session Redis et compatible avec colinmollenhour/php-redis-session-abstract v2.0.0
   * _Problème GitHub_ : &lt;<https://github.com/magento/magento2/commit/672a2e61>>
   * _Contribution du code GitHub_ : mise à jour de la dernière version de colinmollenhour/php-redis-session-abstract v2.0.0 compatible avec adobe commerce
* _AC-12268_ :
   * _Correction de la remarque_ : mettez à niveau les dépendances du compositeur league/flysystem vers la dernière version.
   * _Contribution du code GitHub_ : mettez à niveau les dépendances du compositeur 2.x league/flysystem vers la dernière version 3.x
* _AC-12594_ : [Problème] utilisez la configuration compilée pour les données générées au lieu de la configuration générale.
   * _Remarque de correction_ : le système utilise désormais la configuration compilée pour les données générées au lieu de la configuration générale, ce qui réduit le transfert réseau et la surcharge des données qui dépendent d’une certaine version du code. Cette modification empêche le remplacement du cache dans les instances partagées lors de la permutation de conteneur, ce qui améliore la stabilité et réduit les temps d’arrêt. Auparavant, certaines classes principales utilisaient le type de configuration partagé, ce qui pouvait entraîner le remplacement du cache ou des temps d’arrêt de l’application en raison de différences dans les versions de code sur plusieurs serveurs.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38785>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/29954>
* _AC-12597_ : [Problème] Supprimez les références aux fichiers d’extjs qui ont été supprimés dans e1ccdb...
   * _Remarque de correction_ : le système supprime désormais les références aux fichiers d’extjs qui ont été supprimés, éliminant ainsi les erreurs dans la console du navigateur et le fichier journal du système. Auparavant, ces références provoquaient des erreurs en raison de l’absence des fichiers référencés.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38960>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38951>
* _AC-12715_ :
   * _Remarque sur la correction_ : mettez à jour les dépendances du compositeur de laminas vers la dernière version
   * _Problème GitHub_ : &lt;<https://github.com/magento/magento2/commit/b34c0a75>>
   * _Contribution du code GitHub_ : le système prend désormais en charge les dernières versions des dépendances du compositeur de laminas :
laminas/laminas-servicemanager
laminas/laminas-server
laminas/laminas-stdlib
laminas/validator
garantir la compatibilité et la mise à jour des fonctionnalités. Auparavant, la mise à jour vers les dernières versions de ces dépendances pouvait entraîner des problèmes d’incompatibilité descendante et des échecs de test.
* _AC-12750_ :
   * _Remarque de correction_ : la suppression d’ExtJs consigne une erreur dans le journal de la console du navigateur et dans le journal Magento
* _AC-12778_ : [Problème] Nettoyage mineur : correction d’une mauvaise utilisation de sprintf, il ne prend que 2 espaces réservés ici et w...
   * _Correction de la remarque_ : le système utilise désormais correctement la fonction sprintf avec le nombre approprié d’espaces réservés, ce qui améliore la propreté et la cohérence du code. Auparavant, la fonction sprintf était incorrectement utilisée avec un argument supplémentaire, ce qui ne provoquait aucun problème majeur, mais n’était pas l’utilisation correcte.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39062>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38628>
* _AC-12823_ :
   * _Remarque sur la correction_ : vérifiez l’échec du test unitaire en raison de la mise à jour du correctif phpunit lors de la mise à niveau des composants
   * _Problème GitHub_ : &lt;<https://github.com/magento/magento2/commit/b34c0a75>>
* _AC-12866_ :
   * _Remarque sur la correction_ : supprimer les abandons - Tests d’intégration PhpUnit10
   * _Problème GitHub_ : &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _contribution du code GitHub_ : résoudre les problèmes liés à PHPUnit
* _AC-12868_ :
   * _Remarque sur la correction_ : supprimer les abandons - Tests PhpUnit10 WebApi
   * _Problème GitHub_ : &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _contribution du code GitHub_ : résoudre les problèmes liés à PHPUnit
* _AC-12869_ : [Problème] corrige les classes incorrectes référencées dans les modules Magento.
   * _Remarque de correction_ : le système référence désormais correctement les classes dans les modules, ce qui garantit un fonctionnement plus fluide et empêche les blocages dus à des classes inexistantes. Cela inclut un correctif de bugs dans les modules Indexer et Creditmemo, ainsi que l’implémentation de HttpGetActionInterface dans la classe PrintAction. Auparavant, des références de classe incorrectes entraînaient des erreurs et des blocages système potentiels, et certaines fonctionnalités, telles que le nom de fichier pour les fichiers PDF creditmemo et la réindexation des stocks, ne fonctionnaient pas comme prévu.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39126>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37784>
* _AC-12882_ :
   * _Remarque sur la correction_ : vérifiez la version d’intégration après la mise à niveau des composants
   * _Problème GitHub_ : &lt;<https://github.com/magento/magento2/commit/b34c0a75>>
* _AC-6754_ : erreur de frappe sur un fichier js.
   * _Remarque sur la correction_ : le système utilise désormais correctement le terme « abonnés » dans le fichier JavaScript, assurant ainsi le bon fonctionnement des fonctions associées. Auparavant, une erreur typographique dans le fichier JavaScript entraînait l’utilisation incorrecte du terme « abonnés ».
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/36163>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/36171>
* _AC-8089_ :
   * _Correction de la note_ : examiner les dépendances du compositeur league/flysystem lors de la mise à niveau vers la dernière version
* _AC-8353_ : [Problème] Supprimer la balise `@author` interdite
   * _Remarque à propos de la correction_ : le système respecte désormais les normes de codage en supprimant la balise `@author` interdite de certains modules, ce qui garantit un code plus propre et plus normalisé. Auparavant, la balise `@author` était présente dans certains modules, ce qui était contraire aux normes de codage établies.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37253>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37003>
* _AC-8356_ : [Problème] Supprimez la balise `@author` interdite du `Magento_Customer` (partie 2)
   * _Remarque à propos de la correction_ : le système respecte désormais la norme de codage en supprimant la balise `@author` interdite de certains modules, ce qui garantit un code plus propre et plus normalisé. Auparavant, la balise `@author` était présente dans certains modules, ce qui était contraire aux normes de codage établies.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37250>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37000>
* _AC-8659_ : espace dans la syntaxe editorconfig qui rompt la règle pour [{composer,auth}.json]
   * _Remarque sur la correction_ : le système applique désormais correctement un retrait de 4 espaces aux fichiers composer et auth.json, suite à un correctif apporté à une erreur de syntaxe dans editorconfig. Auparavant, en raison d’un espace dans la syntaxe editorconfig, ces fichiers étaient incorrectement formatés avec un retrait de 2 espaces.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37394>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37395>
* _AC-8984_ : [Problème] ajoute quelques couleurs supplémentaires à la sortie de certaines commandes de l’interface de ligne de commande de configuration
   * _Remarque de correction_ : le système ajoute désormais plus de couleurs à la sortie de certaines commandes de l’interface de ligne de commande (CLI) de la configuration, améliorant ainsi la lisibilité et l’expérience utilisateur. Auparavant, la sortie de ces commandes était plus difficile à lire en raison de l’absence de différenciation des couleurs.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/29335>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/29298>
* _AC-9630_ : la mise à niveau de Magento réinitialise general/region/state_required lorsqu’un nouveau pays avec l’état/région requis est ajouté.
   * _Remarque de correction_ : le système ajoute désormais uniquement le pays modifié à la configuration « general/region/state_required » lorsqu’un nouveau pays avec les états obligatoires est ajouté, ce qui empêche toute interruption du code personnalisé qui suppose que la région est désactivée. Auparavant, l’ajout d’un nouveau pays avec les états obligatoires réinitialisait la configuration « general/region/state_required » aux pays par défaut avec l’état obligatoire, ce qui pouvait entraîner l’interruption de l’activité.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37796>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38076>
* _AC-9712_ : Différence dans la compilation moindre entre la bibliothèque php &amp; nodejs (grunt) avec des expressions `calc` compliquées
   * _Note de correction_ : correction de la différence de compilation entre la bibliothèque php &amp; nodejs (grunt) après la mise à jour wikimedia/less.php:^5.x
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37841>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b34c0a75>
* _ACP2E-2692_ : l&#39;erreur « Table ou vue de base introuvable » se produit lors de l&#39;exécution de l&#39;indexation partielle
   * _Remarque de correction_ : la réindexation partielle fonctionne désormais correctement avec le journal des modifications volumineux en cas de connexion à la base de données secondaire
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2844_ : problèmes après la mise à niveau de MariaDB vers 10.5.1 ou une version ultérieure
   * _Remarque de correction_ : correction du problème lorsque les valeurs datetime dans une base de données étaient converties en 0000-00-00 00:00:00 après la mise à niveau de Mysql
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2855_ : non-correspondance des types dans la comparaison des données lors de la vérification des modifications apportées aux données
   * _Remarque sur la correction_ : Auparavant, l’objet d’enregistrement était appelé à chaque fois sans modification des données (pour tout champ de données numérique, comme int/float/double). Cela déclenche l’indicateur _hasDataChanges sur true et appelle la fonction d’enregistrement. Une fois que ce correctif est appliqué, la fonction d’enregistrement n’appelle que si les données sont modifiées. La valeur des données pour int/float/double-check avec la valeur transmise à la fonction et effectue une correspondance de type stricte.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2959_ : l&#39;importation [Cloud] ne peut pas être utilisée avec la variable de répertoire
   * _Remarque sur la correction_ : le produit peut être importé avec succès, quel que soit le nom du fichier.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2966_ : dans ipad mini, le menu et l’en-tête se chargent comme des appareils mobiles, mais plutôt comme des ordinateurs de bureau.
   * _Remarque de correction_ : le système traite désormais les appareils d’une largeur de 768 px comme des ordinateurs de bureau, en s’assurant que le menu et l’en-tête se chargent correctement. Auparavant, les appareils d’une largeur de 768 pixels étaient traités comme des appareils mobiles, ce qui entraînait le chargement du menu et de l’en-tête dans une vue mobile.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/35b1b1da>, <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-3046_ : erreur de table ou d&#39;affichage de base introuvable lors de l&#39;exécution de mview cron lors d&#39;une opération DDL
   * _Remarque de correction_ : le système gère désormais correctement les opérations de mise à jour de la base de données pendant que la mise à jour mview s&#39;exécute en arrière-plan, ce qui empêche l&#39;apparition d&#39;erreurs « Table de base ou vue introuvable ». Auparavant, certaines opérations de mise à jour de la base de données pouvaient entraîner l’erreur « Table de base ou vue introuvable » si la mise à jour de la mview était exécutée en même temps.

### Framework, GraphQL

* _AC-7976_ : [problème] prise en charge des types scalaires personnalisés pour le schéma GraphQL
   * _Remarque de correction_ : le système prend désormais en charge les types scalaires personnalisés pour le schéma GraphQL, ce qui permet aux développeurs et développeuses de définir des types scalaires personnalisés et des implémentations. Cette fonction peut s’avérer particulièrement utile pour exprimer des valeurs qui peuvent nécessiter une validation, telles qu’HTML, les e-mails, les URL, les dates, etc., ainsi que pour les cas plus avancés tels que les attributs EAV. Auparavant, le système ne prenait pas en charge le traitement des types scalaires personnalisés dans GraphQL.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/36877>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/34651>, <https://github.com/magento/magento2/commit/0574ac23>

### Framework, Produit

* _AC-13011_ : les rapports EE 2.4.8-beta1 ne sont pas générés en raison d’une exception magento

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
* _ACP2E-3253_ : la pagination des éléments du panier GraphQL V2 ne fonctionne pas correctement
   * _Remarque à propos de la correction_ : le problème a été résolu en transmettant la valeur correcte de l’argument de page actuel dans la requête de collection. Auparavant, une valeur incorrecte était transmise pour définir la page active, ce qui provoquait le problème.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/8459b17d>

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

### Importer/exporter

* _AC-12172_ : problème lors de l’importation du produit lorsqu’il est fourni avec le type d’options personnalisé : fichier (le produit créé ne contient pas le prix du type d’option personnalisé et affiche uniquement la première extension de type de fichier fournie)
   * _Remarque sur la correction_ : le système importe désormais correctement les données de produit avec les options personnalisées de type &#39;fichier&#39;, en s&#39;assurant que toutes les extensions de fichier fournies sont affichées et que le prix de l&#39;option personnalisée est inclus. Auparavant, lors de l’importation du produit, si une option personnalisée de type « fichier » était fournie avec plusieurs extensions de fichier, seule la première extension s’affichait et le prix de l’option personnalisée était manquant.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38805>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38926>
* _ACP2E-2710_ : temps d&#39;exécution incorrect pour l&#39;opération d&#39;importation dans la grille de l&#39;historique d&#39;importation
   * _Remarque de correction_ : le temps d’exécution du rapport d’importation s’affiche correctement indépendamment des paramètres régionaux d’administration.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2737_ : des clients en double sont créés avec la même adresse électronique à l’aide de l’importation
   * _Remarque de correction_ : import du client tandis que le partage de compte défini sur Global, le client importé qui existe dans le système est mis à jour.
Le client précédemment importé a été dupliqué.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2902_ : ajout/mise à jour d&#39;un import sur les produits dupliquant des options personnalisables
   * _Correction de la note_ : le problème a été résolu en attribuant le magasin approprié aux options de produit lors des importations d’options de produit au format CSV.
Auparavant, affecté à l’admin store au lieu de leur magasin respectif.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2990_ : date « created_at » du client non convertie en fuseau horaire du magasin lors de l’exportation
   * _Correction de la note_ : une valeur de date de colonne « created_at » est convertie au format de date approprié en fonction du fuseau horaire du magasin dans la section CSV d’exportation du client.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3165_ : [Cloud] erreur lors de la vérification des données dans les données d’importation à l’aide de CSV
   * _Remarque sur la correction_ : aucune erreur ne se produit lors de la vérification des données lors de l’importation du fichier CSV. Auparavant, le message d’erreur affiché était le suivant : « Nous ne parvenons pas à trouver un client qui correspond à cet e-mail et au code de site web dans ligne(s) : 1 » lors de la vérification des données dans la section d’importation à l’aide du fichier CSV de l’administrateur.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/8459b17d>

### Installer et administrer

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
* _ACP2E-1411_ : [Test] Offrez des produits groupés avec 0 inventaire affiché sur la vitrine
   * _Remarque sur la correction_ : le produit groupé ne s’affiche pas sur les sites Web supplémentaires utilisant un stock supplémentaire.
* _ACP2E-2794_ : [Cloud] problème critique lié à la liste des produits avec des espaces vides
   * _Remarque sur la correction_ : le système affiche désormais correctement les listes de produits sans espaces vides lorsque les produits sont définis sur « En rupture de stock », ce qui garantit un affichage cohérent et précis des produits disponibles. Auparavant, la définition d’un produit sur « En rupture de stock » entraînait l’affichage d’un espace vide dans la liste des produits, ce qui perturbait la mise en page et pouvait dérouter les clients.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ea79f7dd>, <https://github.com/magento/inventory/commit/b59e48ca>

### Ordre

* _AC-10828_ : Écran d&#39;aperçu de commande du serveur principal : Quantité en reliquat non visible au niveau de l&#39;article de commande
   * _Corriger la note_ : Le système affiche désormais le nombre d&#39;articles en reliquat dans la colonne Quantité de l&#39;écran d&#39;aperçu de commande du serveur principal. Cela permet aux utilisateurs et utilisatrices de suivre avec précision le statut de tous les éléments d’une commande. Auparavant, la colonne Quantité affichait uniquement le nombre d’articles commandés, facturés et expédiés, mais n’affichait pas le nombre d’articles en reliquat.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38252>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38320>
* _AC-10994_ : [Problème] ID de magasin incorrect utilisé dans le moteur de rendu d’adresse de commande
   * _Remarque de correction_ : le système utilise désormais correctement l’ID de magasin associé à une commande lors du rendu de l’adresse de commande, en s’assurant que les adresses sont formatées correctement en fonction de leur ID de magasin respectif. Auparavant, le système utilisait incorrectement l’ID de magasin actuel, ce qui pouvait entraîner un formatage incorrect de l’adresse dans les cas où plusieurs e-mails de commande provenant de différents magasins devaient être envoyés.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38412>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37932>
* _AC-11798_ : [Problème] Le prix d’expédition s’affiche différemment dans le pdf imprimé
   * _Corriger la note_ : le système affiche désormais correctement les prix d&#39;expédition dans les fichiers PDF imprimés en fonction des paramètres de configuration de taxe, ce qui garantit la cohérence entre la page de vue de la facture de commande client et la facture imprimée. Auparavant, le prix d’expédition affiché dans le PDF imprimé excluait la taxe, quels que soient les paramètres de configuration de la taxe.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38608>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38595>, <https://github.com/magento/magento2/commit/1bafc571>
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

### Commande, Retours

* _ACP2E-2982_ : le remboursement de la commande génère un avoir en double
   * _Remarque de correction_ : l&#39;émission du remboursement via l&#39;API REST lorsque deux demandes identiques ont été exécutées simultanément ne crée plus d&#39;avoirs en double.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a4fbf702>

### Commande, Taxe

* _ACP2E-3003_ : [CLOUD] Base_row_total incorrect dans l’API de commande RESTFUL lors de l’activation des transactions transfrontalières et de l’application des remises sur coupon
   * _Correction de la note_ : Désormais, un montant base_row_total correct est renvoyé par l’API de commande RESTFUL lorsque la transaction transfrontalière est activée et que la remise de coupon est appliquée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/9af794a4>

### Autres frais

* _LYNX-339_ : cookie private_content_version renvoyé dans les requêtes GQL.
* _LYNX-366_ : erreur du serveur sur les props d&#39;e-mail dans les requêtes de carte cadeau physique
* _LYNX-380_ : l’attribut is_available dans CartItemInterface renvoie toujours false pour les produits configurables
* _LYNX-382_ : l&#39;attribut is_available dans CartItemInterface renvoie la valeur true même lorsque le stock vendable est inférieur à la quantité du produit
* _LYNX-395_ : l’attribut only_x_left_in_stock dans ProductInterface n’est pas précis sur les produits configurables
* _LYNX-399_ : la miniature de l’espace réservé est renvoyée lorsqu’un produit simple est ajouté au panier dans un produit groupé
* _LYNX-400_ : les attributs d’option personnalisés du client ne fonctionnent pas avec des valeurs entières
* _LYNX-402_ : erreur de serveur interne lors de la tentative d’obtention de priceDetails pour les produits groupés avec un prix dynamique
* _LYNX-403_ : only_x_left_in_stock renvoie toujours 0 pour les produits configurables
* _LYNX-405_ : erreur GraphQL : type &#39;fichier&#39; non pris en charge dans la requête des options personnalisables
* _LYNX-411_ : la requête GraphQL ne renvoie pas le prix normal calculé correct pour les produits personnalisables
* _LYNX-412_ : les taxes appliquées via EstimatedTotals persistent avec des mutations mises à jour
* _LYNX-420_ : l&#39;attribut is_available dans CartItemInterface renvoie la valeur true même lorsque le stock vendable est inférieur à la quantité du produit
* _LYNX-421_ : impossible d’ajouter un coupon au panier pour l’expédition uniquement
* _LYNX-425_ : Prix normal du produit avec 12 décimales et une valeur incorrecte
* _LYNX-430_ : erreur de serveur GraphQL sur le panier avec produit en rupture de stock groupé
* _LYNX-441_ : impossible de créer une adresse avec des attributs personnalisés
* _LYNX-447_ : erreur de serveur GraphQL sur le panier avec only_x_left_in_stock sur le produit groupé
* _LYNX-464_ : erreur GraphQL lors de la suppression d’autres produits avec un produit configurable insuffisant dans le panier
* _LYNX-469_ : impossible d’ajouter des produits en raison de la sensibilité à la casse du SKU dans la mutation
* _LYNX-526_ : GraphQL. La configuration n’est pas respectée pour ANNULER la commande available_actions

### Autres outils de développement

* _AC-10658_ : [Problème] Correction de l’erreur de syntaxe HTML dans visual.phtml
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

### Paiements

* _ACP2E-2841_ : Le flux de paie crée une transaction chaque fois que nous cliquons sur le bouton de récupération sur l&#39;écran d&#39;affichage des transactions
   * _Correction de note_ : le système récupère désormais correctement les informations de transaction sans créer de transaction de paiement chaque fois que l&#39;utilisateur clique sur le bouton de récupération sur l&#39;écran d&#39;affichage des transactions. Auparavant, cliquer sur le bouton de récupération créait incorrectement une nouvelle transaction de paiement pour une commande qui avait déjà été payée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3028_ : le message Paylater ne s&#39;affiche pas dans le PDP pour le compte marchand paypal canadien
   * _Correction de note_ : Le système affiche désormais correctement le message PayLater pour les comptes marchands PayPal canadiens sur la page des détails du produit (PDP) lorsque le pays de l&#39;acheteur peut être déterminé à partir de l&#39;adresse de facturation du compte ou de l&#39;expédition. Auparavant, le message PayLater ne s’affichait pas en raison d’un paramètre manquant, ce qui entraînait une erreur dans la console du navigateur.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/6a185204>

### Performances

* _AC-12000_ : [problème] nettoyage du code et ajout d’un nouveau bloc principal critique, puis déplacement du code CSS critique avant les ressources
   * _Remarque de correction_ : le système comprend désormais un nouveau bloc HEAD critique et déplace les feuilles CSS critiques avant les ressources, ce qui permet une personnalisation et une optimisation des performances supplémentaires dans le front-end. Auparavant, le CSS critique n’était pas positionné avant les ressources, ce qui limitait les opportunités de personnalisation et d’optimisation.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38748>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/35580>
* _AC-12176_ : la compilation du thème s’interrompt lorsque l’hôte mysql contient des informations sur le port
   * _Remarque de correction_ : le système gère désormais correctement la configuration de l’hôte MySQL qui inclut les informations de port, assurant ainsi la réussite de la compilation du thème. Auparavant, la compilation du thème échouait si la configuration de l’hôte MySQL dans la connexion à la base de données incluait des informations sur le port.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38799>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38842>
* _ACP2E-2494_ : problème de performance lors du chargement des attributs de produit dans les règles de panier
   * _Remarque sur la correction_ : amélioration des performances des requêtes pour les règles de vente, d’environ 150 ms à un seul chiffre ms.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2673_ : performances d’indexation partielle du prix
   * _Remarque à propos de la correction_ : les performances d’indexation partielle du prix ont été améliorées en optimisant certaines des requêtes de suppression utilisées dans le processus d’indexation.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2850_ : la commande est refusée lors de la configuration multi-magasin lors de l’utilisation du traitement asynchrone des commandes + conditions générales
   * _Correction de note_ : les commandes passées à partir de sites web autres que ceux par défaut dont les conditions générales sont activées sont désormais traitées.
Avant qu&#39;ils ne soient automatiquement rejetés.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/57a32313>
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
* _AC-5969_ : AlertProcessor - L’argument #2 ($storeId) doit être de type int, chaîne donnée.
   * _Remarque de correction_ : le système déclenche désormais correctement les e-mails d’alerte de produit en s’assurant que l’identifiant du magasin est du type de données correct. Auparavant, les e-mails d’alerte de produit n’étaient pas envoyés en raison d’une incohérence de type dans l’identifiant du magasin.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/35602>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/0574ac23>
* _ACP2E-2944_ : la fonction [Cloud] addFilterToMap ne fonctionne pas pour certaines colonnes
   * _Note de correction_ : désormais, le module personnalisé peut être utilisé dans la grille de commande. Des erreurs se produisaient précédemment lors de l’utilisation d’un module personnalisé.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/3a7c4d17>

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

### SEO

* _AC-11907_ : l’ajout de réécritures d’URL avec un accent entraîne un chargement infini
   * _Remarque de correction_ : le système crée et exécute désormais correctement les réécritures d’URL avec des accents, ce qui empêche le chargement infini pendant le processus d’enregistrement. Auparavant, l’ajout d’une réécriture d’URL avec un accent provoquait un problème de chargement infini.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38692>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/44cef3a9>
* _ACP2E-2641_ : réécriture d&#39;URL de catégorie multi-magasin incorrecte pour la catégorie de troisième niveau
   * _Remarque de correction_ : générez des réécritures d’URL correctes pour les enfants avec le parent avec la clé d’URL étendue personnalisée
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2770_ : les caractères à deux octets (caractères spéciaux) dans le champ Nom du produit bloquent la création du produit dans le serveur principal
   * _Remarque de correction_ : un nouveau paramètre a été ajouté pour vous permettre ou non d’appliquer une translittération à l’URL du produit. Le paramètre est disponible ici : Magasins > Configuration > Catalogue > Catalogue > Optimisation du moteur de recherche : « Appliquer la translittération à l’URL du produit »
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b2286ecf>

### Sécurité

* _AC-11762_ :
   * _Corriger la note_ : mettez à jour le champ de fenêtre OTP 2FA avec la description correcte et la valeur par défaut après le changement BiC
   * _Contribution du code GitHub_ : commande mise à jour pour la façon dont la période otp_window sera saisie à partir de maintenant bin/magento config:set twofactorauth/google/otp_window VALUE
vers bin/magento config:set twofactorauth/google/leeway VALUE
* _AC-11855_ : [Problème] Menu contextuel Paylater de police manquant
   * _Remarque de correction_ : le système permet désormais de charger la police « https://www.paypalobjects.com/webstatic/mktg/2014design/font/PP-Sans/PayPalSansBig-Medium.woff&#39; » sans enfreindre la directive de la politique de sécurité du contenu, ce qui garantit l’affichage correct de la fenêtre contextuelle Paylater. Auparavant, le chargement de la police était refusé en raison d’une violation de la directive de la politique de sécurité du contenu, ce qui provoquait des problèmes d’affichage avec la fenêtre contextuelle Paylater.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38624>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37401>
* _AC-11937_ :
   * _Corriger la note_ : mettez à jour le champ de fenêtre OTP 2FA avec la description correcte et la valeur par défaut après le changement BiC
   * _Contribution du code GitHub_ : commande mise à jour pour la façon dont la période otp_window sera saisie à partir de maintenant bin/magento config:set twofactorauth/google/otp_window VALUE
vers bin/magento config:set twofactorauth/google/leeway VALUE
* _AC-12309_ :
   * _Remarque sur la correction_ : mettez à jour la documentation utilisateur pour l’authentification à deux facteurs (2FA) afin de modifier la commande otp_window
   * _Contribution du code GitHub_ : mettez à jour la documentation utilisateur pour l’authentification à deux facteurs (2FA) afin de modifier la commande des paramètres OTP_WINDOW comme indiqué à l’adresse : https://jira.corp.adobe.com/browse/AC-11762

### Expédition

* _AC-10757_ : [Problème] Correction d’une faute de frappe dans tracking.phtml - les fonctions JS « currier » ont été renommées « carrier » (transporteur)
   * _Remarque de correction_ : le système utilise désormais correctement le terme « carrier » au lieu du « currier » mal orthographié dans les fonctions de gestionnaire JavaScript utilisées dans le modèle de suivi des commandes, ce qui permet d’assurer un nom de fonction et une clarté de code corrects. Auparavant, le terme mal orthographié « currier » était utilisé, ce qui entraînait une confusion et une incohérence potentielles dans la base de code.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/34523>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/33414>
* _AC-11811_ :
   * _Note de correction_ : REPOS UPS « Un envoi ne peut pas avoir un KGS/IN ou un LBS/CM ou un OZS/CM comme unité de mesure »
   * _Problème GitHub_ : &lt;<https://github.com/magento/magento2/commit/9b1713d8>>
   * _Contribution du code GitHub_ : les taux d’UPS sont visibles dans le passage en caisse et le panier.
* _AC-11916_ :
   * _Note de correction_ : [QPT] REPOS UPS « Une expédition ne peut pas avoir un KGS/IN ou un LBS/CM ou un OZS/CM comme unité de mesure »
   * _Contribution du code GitHub_ : les taux d’UPS sont visibles dans le passage en caisse et le panier.
* _AC-11938_ : REPOS UPS « Un envoi ne peut pas avoir un KGS/IN ou un LBS/CM ou un OZS/CM comme unité de mesure »
   * _Correction de la remarque_ : assurez-vous que les taux UPS doivent être visibles dans le passage en caisse et le panier.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38618>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/493e01f5>
* _AC-11983_ :
   * _Note de correction_ : [QPT] REPOS UPS « Une expédition ne peut pas avoir un KGS/IN ou un LBS/CM ou un OZS/CM comme unité de mesure »
   * _Contribution du code GitHub_ : les taux d’UPS sont visibles dans le passage en caisse et le panier.
* _AC-11984_ :
   * _Note de correction_ : [QPT] REPOS UPS « Une expédition ne peut pas avoir un KGS/IN ou un LBS/CM ou un OZS/CM comme unité de mesure »
   * _Contribution du code GitHub_ : les taux d’UPS sont visibles dans le passage en caisse et le panier.
* _ACP2E-2738_ : la fenêtre de suivi indique une date de livraison prévue incorrecte
   * _Corriger la note_ : afficher la date de livraison correcte pour l’opérateur Fedex.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2763_ : Les Taux Du Tableau S&#39;Affichent Toujours Même Si La Livraison Gratuite Est Appliquée
   * _Corriger la note_ : la méthode d&#39;expédition au tarif du tableau s&#39;affiche maintenant même si l&#39;expédition gratuite devient disponible après l&#39;application du coupon
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2765_ : échec du test MFTF AdminCreateShippingLabelTest en raison d&#39;informations d&#39;identification non ajoutées dans l&#39;environnement Jenkins
   * _Remarque sur la correction_ : correctif de test mftf
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ea79f7dd>

### Évaluation et prévisualisation

* _ACP2E-2901_ : les paramètres de mise à jour planifiée ne sont pas enregistrés s’ils ont été ajoutés lors de la mise à jour
   * _Remarque de correction_ : le système efface désormais correctement les valeurs des attributs de produit dans les mises à jour planifiées suivantes lorsque ces attributs sont modifiés dans la mise à jour en cours d’exécution. Auparavant, lorsqu’un attribut de produit était modifié par une mise à jour planifiée en cours d’exécution, il était impossible d’effacer ces valeurs d’attribut lors de la création d’une mise à jour planifiée, ce qui nécessitait que l’utilisateur les modifie après la création.
* _ACP2E-2999_ : problème de date de début et de fin de la règle de prix du panier non synchronisé avec la mise à jour d’évaluation
   * _Correction de note_ : les dates sont enregistrées en fonction des mises à jour de l’évaluation des règles de prix de panier.
* _ACP2E-3104_ : erreur JS dans l&#39;aperçu intermédiaire
   * _Remarque de correction_ : le fichier form-mini-stub.js se charge maintenant sans erreur de syntaxe Js dans les outils de développement.
* _ACP2E-3162_ : impossible de mettre à jour le contenu échelonné du prix spécial du produit
   * _Correction de note_ : le système permet désormais de modifier la date de fin d’une campagne de mise à jour des prix après son lancement, afin que les utilisateurs puissent apporter les ajustements nécessaires à leurs campagnes. Auparavant, une erreur était générée lors de la tentative de mise à jour de la date de fin d’une campagne active, empêchant les utilisateurs d’apporter des modifications.

### Ciblage

* _AC-9432_ : [problème] autoriser l’utilisation de plages CIDR dans la liste autorisée de maintenance
   * _Remarque de correction_ : le système prend désormais en charge l’utilisation des plages CIDR dans la liste d’adresses IP autorisées du mode de maintenance, ce qui permet à une plage d’adresses IP de contourner le mode de maintenance. Auparavant, la liste autorisée d’adresses IP du mode de maintenance autorisait uniquement les adresses IP individuelles à contourner le mode de maintenance.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37943>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/30699>

### Framework de test

* _AC-11491_ :
   * _Remarque sur la correction_ : [Ignorer] Doit être Annuler à nouveau le test d’intégration
   * _Problème GitHub_ : &lt;<https://github.com/magento/magento2/commit/493e01f5>>
   * _Contribution du code GitHub_ : annulez tous les tests d’intégration qui sont ignorés dans ce PR - https://github.com/magento-commerce/magento2ce/pull/8811/
* _AC-11654_ : échec du test d’intégration testDbSchemaUpToDate en raison du type de colonne JSON
   * _Remarque de correction_ : le système reconnaît désormais correctement les types de colonnes JSON dans le schéma de base de données lors des tests d’intégration, ce qui empêche les échecs de test en raison d’une incohérence entre le schéma de base de données et le schéma déclaratif. Auparavant, le système identifiait incorrectement les types de colonnes JSON en tant que LONGTEXT dans MariaDB, ce qui entraînait l’échec des tests d’intégration.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ef81f5a2>

### Framework de l’interface utilisateur

* _AC-12128_ : correctif de vulnérabilité de sécurité Prototype.js CVE-2020-27511
   * _Remarque de correction_ : le système a été mis à jour pour résoudre la vulnérabilité de sécurité CVE-2020-27511 dans Prototype.js 1.7.3, ce qui améliore la sécurité globale du système. Avant cette mise à jour, le système était susceptible de subir un déni de service d’expression régulière (ReDOS) par le biais de la suppression des balises HTML conçues.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12189_ : Grunt Less utilise pub/ préfixe pour les plans source
   * _Remarque concernant la correction_ : le système génère désormais des mappages source less/css sans le préfixe /pub pour les chemins d’accès lors de l’utilisation de grunt, ce qui élimine la nécessité d’une solution de contournement dans la configuration du serveur web. Auparavant, l’utilisation du préfixe /pub dans les chemins d’accès des plans de source nécessitait une configuration spécifique dans le serveur web pour fonctionner correctement.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38837>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38840>
* _AC-1306_ : du contenu statique est déployé pour les modules désactivés
   * _Remarque de correction_ : le système exclut désormais le CSS relatif aux modules désactivés des fichiers de sortie CSS finaux, en veillant à ce que les styles inutiles ne soient pas chargés. Auparavant, le code CSS relatif aux modules désactivés était inclus dans les fichiers de sortie CSS finaux, ce qui entraînait le chargement de styles supplémentaires et inutiles.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/24666>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/32922>
* _AC-9007_ : [problème] ne chargez pas le contexte du bloc principal sur le front-end
   * _Remarque à propos de la correction_ : le système s’assure désormais que le contexte du bloc principal n’est pas chargé sur le front-end, évitant la création de sessions principales inutiles et de verrous de session potentiels. Auparavant, le système chargeait incorrectement le contexte du bloc principal sur le front-end, ce qui entraînait la création de sessions principales et de verrous de session potentiels.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37617>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/36368>
* _ACP2E-2529_ : exception lors de la vérification du solde d&#39;une carte cadeau lorsque Recaptcha est activé
   * _Correction de note_ : les utilisateurs pourront récupérer le solde de la carte cadeau dans l’écran d’affichage et de modification du panier. Auparavant, ces détails n’étaient pas affichés lorsque reCAPTCHA était activé.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2-page-builder/commit/4a2795ea>
* _ACP2E-2729_ : [CLARIFICATION] demande de fonctionnalité conforme ADA
   * _Remarque de correction_ : le système assure désormais la conformité ADA en supprimant les propriétés CSS non prises en charge et en les remplaçant par des propriétés prises en charge dans le fichier print.css. Auparavant, l’utilisation de propriétés CSS non prises en charge entraînait des problèmes de compatibilité avec les navigateurs.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-3061_ : code de bibliothèque de confusion [Cloud] dans effect-drop.js d’AC 2.4.4-p8
   * _Remarque à propos de la correction_ : le système implémente désormais correctement la bibliothèque effect-drop.js, assurant ainsi le bon fonctionnement des effets de l’interface utilisateur jQuery. Auparavant, la bibliothèque effect-drop.js était remplacée par erreur par la bibliothèque effect-clip.js, ce qui entraînait des problèmes potentiels avec les effets de l’interface utilisateur jQuery.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/35b1b1da>
