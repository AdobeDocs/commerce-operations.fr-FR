---
source-git-commit: e05e4e4ef547bfb95fdcc53c2095ef0725b0a6e1
workflow-type: tm+mt
source-wordcount: '14731'
ht-degree: 0%

---
# Notes de mise à jour du Magento Open Source (v2.4.8-beta1)

## Tons clairs

Les 49 mises en évidence suivantes s’appliquent à la version 2.4.8 de Magento Open Source.

### Framework

* _AC-10721_ : mettez à niveau les dépendances du compositeur de ligue/système de vol vers la dernière version
   * _Remarque de correctif_ : mettez à niveau les dépendances du compositeur de classe/système de vol 2.x vers la dernière version 3.x.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/91cb4d46>
* _AC-11495_ : mise à niveau des composants de la plateforme 2.4.8-beta1
* _AC-11673_ : recherchez les dernières versions de php-amqplib/php-amqplib
   * _Note de correctif_ : mise à jour de la dernière version php-amqplib/php-amqplib :^3.x
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-11723_ : restructuration de la structure de test d’intégration pour la compatibilité phpunit 10 - IntegrationTest.php introuvable
   * _Remarque de correctif_ : PHPUnit 9 est mis à niveau vers PHPUnit 10 avec les modifications de la structure Intégration et Test WebAPI d’Adobe Commerce. Les modifications de PHPUnit 10 sont rétrocompatibles.
   * _Contribution du code GitHub_ : &lt;https://github.com/magento/magento2/ (interne, non fusionné)>
* _AC-11813_ : structure de test WebApi pour la compatibilité phpunit 10 - problème lié à la connectivité RabbitMQ avec les modules SOAP et B2B
   * _Remarque de correctif_ : PHPUnit 9 est mis à niveau vers PHPUnit 10 avec les modifications de la structure Intégration et Test WebAPI d’Adobe Commerce. Les modifications de PHPUnit 10 sont rétrocompatibles.
   * _Contribution du code GitHub_ : &lt;https://github.com/magento/magento2/ (interne, non fusionné)>
* _AC-11816_ : Ajouter une compatibilité avec MySQL 8.4 LTS
* _AC-11911_ : nettoyage CSS de jQuery/fileuploader après la migration vers la bibliothèque de disponibilité
   * _Remarque : correction_ : suppression de la bibliothèque jQuery/fileUploader car elle a été migrée vers la bibliothèque Uppy.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/7cabfb46>
* _AC-11995_ : Ajouter une compatibilité avec MySQL 8.4 LTS pour Magento CE
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12014_ : le module Mark élasticsearch 8 comme obsolète
* _AC-12015_ : nettoyage du dossier ExtJs après la migration vers la bibliothèque jsTree
   * _Remarque : correction_ : suppression du dossier extJs car la fonctionnalité associée a été migrée vers jsTree
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/7cabfb46>
* _AC-12022_ : mise à niveau de la dépendance système monolog/monolog vers la dernière version majeure
   * _Remarque de correctif_ : le système a été mis à jour pour utiliser la dernière version majeure de la bibliothèque &quot;monolog/monolog:^3.x&quot;, assurant ainsi la compatibilité et de meilleures performances. Auparavant, le système utilisait une version obsolète de la bibliothèque &quot;monolog/monolog&quot;, ce qui aurait pu entraîner des problèmes et des limitations potentiels.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12023_ : Mettre à niveau wikimedia/less.php la dépendance vers la dernière version majeure
   * _Remarque de correctif_ : le système a été mis à jour afin d’utiliser la dernière version majeure 5.x de la bibliothèque &quot;wikimedia/less.php&quot;, assurant ainsi la compatibilité et des fonctionnalités à jour. Auparavant, le système utilisait une version obsolète de la bibliothèque, ce qui pouvait entraîner des problèmes de sécurité.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12024_ : mise à niveau de la dépendance de bibliothèque jquery/validate vers la dernière version mineure
   * _Remarque : Mettez à niveau la dépendance de bibliothèque jquery/validate vers la dernière version mineure 1.20.0_
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12025_ : mise à niveau de la dépendance système du moment.js vers la dernière version mineure
   * _Remarque de correctif_ : Mettez à niveau la dépendance du système moment.js vers la dernière version mineure 2.30.1
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12032_ : Ajouter une compatibilité avec MySQL 8.4 LTS pour EE
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12034_ : Ajouter une compatibilité avec MySQL 8.4 LTS pour B2B
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12074_ : Ajouter une compatibilité avec MySQL 8.4 LTS pour les extensions de lot
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12085_ : ajouter une compatibilité avec MariaDB 11.4 LTS pour CE
   * _Remarque : correction_ : ajout de la prise en charge de MariaDB 11.4 avec Adobe Commerce et les extensions
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12165_ : Optimisation des abonnés - PhpUnit10
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/90e25b6b>
* _AC-12267_ : prise en charge des reprises de connexion pour la session Redis et compatible avec colinmollenhour/php-redis-session-abstract v2.0.0
   * _Remarque : mise à jour de la dernière version de colinmollenhour/php-redis-session-abstract v2.0.0 compatible avec adobe commerce_
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12268_ : mettez à niveau les dépendances du compositeur de ligue/système de vol vers la dernière version
   * _Remarque de correctif_ : mettez à niveau les dépendances du compositeur de classe/système de vol 2.x vers la dernière version 3.x.
* _AC-12576_ : étudiez les échecs des tests d’automatisation avec MySQL 8.4 LTS
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12595_ : Ajouter une compatibilité avec MariaDB 11.4 LTS For EE
   * _Remarque : correction_ : ajout de la prise en charge de MariaDB 11.4 avec Adobe Commerce et les extensions
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12693_ : Recherche sur l’outil de migration de données (DMT) avec MySQL 8.4 LTS
* _AC-12715_ : mise à jour des dépendances du compositeur laminas à l’aide de la dernière version
   * _Fix note_ : le système prend désormais en charge les dernières versions des dépendances des compositeurs laminas :
laminas/laminas-servicemanager
laminas/laminas-server
laminas/laminas-stdlib
laminas/laminas-validator
assurer la compatibilité et les fonctionnalités à jour. Auparavant, la mise à jour vers les dernières versions de ces dépendances pouvait entraîner des problèmes d’incompatibilité ascendante et des échecs de test.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12752_ : Ajouter une compatibilité avec MariaDB 11.4 LTS pour l’outil de migration de données
   * _Remarque : correction_ : ajout de la prise en charge de MariaDB 11.4 avec Adobe Commerce et les extensions
* _AC-12823_ : étudiez l’échec du test unitaire en raison de la mise à jour du correctif phpunit au cours de la mise à niveau du composant.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12897_ : compatibilité des outils SVC et EAT avec MySQL 8.4
* _AC-12898_ : compatibilité des outils UCT avec MySQL 8.4
   * _Remarque de correctif_ : l’outil de compatibilité de mise à niveau (UCT) est désormais compatible avec MySQL 8.4, ce qui garantit un bon fonctionnement et des contrôles de compatibilité pour les instances s’exécutant sur cette version. Auparavant, l’outil UCT n’était pas testé et sa compatibilité avec MySQL 8.4 n’était pas vérifiée.
* _AC-9749_ : mise à niveau de PHPUnit 10
   * _Remarque de correctif_ : mise à jour des dépendances du compositeur phpunit/phpunit vers la version compatible - &quot;phpunit/phpunit&quot;:&quot;10.x&quot;

### Installation et administration

* _AC-6819_ : définissez les indexeurs sur &quot;Mise à jour par planification&quot; par défaut

### Commande

* _ACP2E-2709_ : [Demande de fonctionnalités] Le client suggère que le bouton Envoyer le commentaire sur la page Détails de la commande est déroutant et doit être remplacé par autre chose.
   * _Remarque_ : Afin de minimiser la confusion, le libellé du bouton &quot;Envoyer le commentaire&quot; a été remplacé par &quot;Mettre à jour&quot; dans la page des détails de la commande.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/488c1034>

### Autre

* _AC-11420_ : la définition des indexeurs s’affiche par défaut dans l’état Prêt lorsque la nouvelle version d’Adobe Commerce est installée
   * _Remarque de correctif_ : après le Magento d’installation, l’état de l’indexeur doit être *Ready* par défaut.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/71432aeb>
* _AC-11421_ : dans l’installation de Magento existante lors de l’installation du module d’indexation tiers, définissez les indexeurs par défaut lors de la mise à jour programmée.
   * _Remarque : tous les nouveaux indexeurs sont par défaut en mode [Mise à jour par planification] ._ Auparavant, le mode par défaut était [Mettre à jour sur Enregistrer]. Idem avec les indexeurs personnalisés également.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/71432aeb>
* _AC-12480_ : les options Elasticsearch 7 et 8 doivent être fournies avec Obsolète dans la configuration d’administration.
   * _Remarque : l’option Elasticsearch 8 de l’option Configuration d’administration s’affiche avec du texte obsolète pour informer les utilisateurs que l’option Elasticsearch 8 n’est plus recommandée pour l’utilisation._
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/0611e750>
* _AC-12481_ : ajouter une note lorsque l’option Elasticsearch est sélectionnée dans la configuration d’administration
   * _Remarque : correction_ : ajout d’une note textuelle pour informer les utilisateurs administrateurs d’Adobe Commerce que la recherche en élasticité n’est plus prise en charge par Adobe et est obsolète.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/0611e750>
* _AC-12870_ : compatibilité des outils SVC et EAT avec MariaDB 11.4
   * _Note de correctif_ : compatibilité des outils SVC et EAT avec MariaDB 11.4
* _AC-12876_ : compatibilité des outils UCT avec MariaDB 11.4
* _LYNX-374_ : Confirmation du courrier électronique du document via GraphQL
* _LYNX-376_ : document obtenant des configurations pour reCAPTCHA dans GraphQL
* _LYNX-409_ : optimisations des requêtes de base de données pour mettre à jour la mutation des éléments du panier

### Sécurité

* _AC-11041_ : améliorations de la sécurité pour la version 2.4.8-bêta1 de juin 2024
* _AC-11864_ : améliorations de la sécurité pour la version 2.4.8-bêta1 d’août 2024
* _AC-12346_ : améliorations de la sécurité pour la version 2.4.8-bêta1 à partir de la version d’octobre 2024
* _AC-12691_ : [2.4.8-beta1] Le point d’entrée de l’API REST de mise à jour client ne fonctionne pas
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a4102373>, <https://github.com/magento/magento2/commit/a4102373>

### Interface utilisateur

* _AC-12726_ : [2.4.8-beta1] Migration de TinyMCE 5 vers TinyMCE 7
   * _Remarque : migrée TinyMCE 5 vers TinyMCE 7.3.0 pour être une version prise en charge pour Adobe Commerce, le système utilisait auparavant la version 5.10.2 obsolète et signalait une vulnérabilité de sécurité._
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12825_ : [2.4.8-beta1] Migration de TinyMCE 5 vers TinyMCE 7 Page Builder
   * _Remarque : migrée TinyMCE 5 vers TinyMCE 7.3.0 pour être une version prise en charge pour Adobe Commerce, le système utilisait auparavant la version 5.10.2 obsolète et signalait une vulnérabilité de sécurité._
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12844_ : [2.4.8-beta1] Migration de TinyMCE 5 vers TinyMCE 7 - Magento2-infrara - mots interdits
   * _Remarque : migrée TinyMCE 5 vers TinyMCE 7.3.0 pour être une version prise en charge pour Adobe Commerce, le système utilisait auparavant la version 5.10.2 obsolète et signalait une vulnérabilité de sécurité._
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12901_ : mise à niveau de Require.js vers la dernière version 2.3.7 (vulnérabilité de sécurité CVE-2024-38999)
   * _Remarque : correction_ : mise à jour de require.js vers la dernière version 2.3.7. Dans la version précédente, une vulnérabilité de sécurité signalée
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b34c0a75>

## Problèmes résolus

Nous avons corrigé 253 problèmes dans le code principal Magento Open Source 2.4.8. Vous trouverez ci-dessous un sous-ensemble des problèmes résolus inclus dans cette version.

### API

* _AC-10042_ : l’API REST /V1/transactions renvoie une erreur lorsque parent_txn_id = txn_id
   * _Remarque de correctif_ : le système gère désormais correctement les transactions de concept parent et enfant lorsque l’ID de transaction parent est identique à l’ID de transaction, ce qui empêche une boucle infinie lors de l’interrogation du point de terminaison de l’API REST /V1/transactions. Auparavant, ce scénario entraînait une erreur fatale en raison du dépassement du temps d’exécution maximal.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1bafc571>
* _AC-11878_ : [Problème de type Graphql] dans la version 2.4.7
   * _Remarque de correctif_ : le système gère désormais correctement les valeurs entières dans la fonction GetCustomSelectedOptionAttributes lors de l’exécution d’une requête GraphQL, ce qui empêche toute erreur de type. Auparavant, le lancement d’une requête GraphQL qui utilisait GetCustomSelectedOptionAttributes avec un argument entier entraînait une erreur de type.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38662>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38663>
* _ACP2E-2927_ : [API REST] : Utiliser la valeur par défaut en mode magasin ne reste pas cochée après l’ajout de configurations pour un produit configurable
   * _Remarque : correction_ : le problème a été corrigé en s’assurant que les entrées de base de données correctes pour les options personnalisables d’un magasin autre que celui par défaut sont correctes. La case à cocher du magasin personnalisé dans la section &quot;admin > Catalogue > Edition du produit > Options personnalisables&quot; était auparavant décochée en raison d’entrées de base de données inexactes, même si le titre de l’option pour le magasin personnalisé restait identique à celui du magasin par défaut.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-2969_ : API REST incapable d’effectuer des requêtes avec barre oblique (/) dans le SKU lors de l’utilisation de Oauth1
   * _Remarque sur les correctifs_ : Avant le correctif, vous n’étiez pas en mesure d’effectuer un appel API réussi pour un produit dont le SKU contenait &quot;/&quot;. Désormais, vous pouvez émettre une requête d’obtention d’API réussie pour les détails du produit même si son SKU comporte une barre oblique.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3079_ : Échec de la mise à jour de l&#39;adresse client lors de la mise à jour via l&#39;API REST si &quot;validateDefaultAddress&quot; est activé
   * _Remarque : le point de terminaison de l’API fonctionne désormais comme prévu une fois le problème avec la clé d’ID manquante dans la charge utile de l’API résolu._
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3091_ : [Cloud] Création du groupe de prix de groupes de sites web dupliqués dans l’API des prix de niveau.
   * _Remarque :_ : l’API Repose sur le prix du niveau de maintenant ne permet pas de créer le groupe de prix de groupes de sites web en double.
Auparavant, il était possible de créer le groupe de prix du site web Dupliquer dans l’API de prix de niveau qui ne serait pas validé dans Admin lors de l’enregistrement du produit.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3130_ : impossible d’ajouter un commentaire de commande avec l’état via l’API REST
   * _Remarque : correction_ : le problème a été résolu en autorisant le changement d’état dans l’ordre s’il provient uniquement de l’état actuel. Auparavant, il ne respectait pas l’état de la commande et empêchait toute modification de l’état de la commande, même si elle venait du même état.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/93d50f8d>

### Compte

* _AC-10782_ : le formulaire d’adresse du client autorise le code aléatoire dans les champs de nom
   * _Remarque : le système valide désormais l’entrée dans les champs Prénom et Nom du formulaire d’adresse du client, ce qui empêche l’utilisation de code aléatoire._ Auparavant, le système autorisait l’utilisation de code aléatoire dans ces champs sans générer d’erreur.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38331>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38345>
* _AC-1090_ : mon compte ajoute un blocage de l’adresse lors de l’enregistrement
   * _Remarque :_ : le système enregistre désormais correctement les adresses client même lorsque le champ de région n’est pas affiché, ce qui empêche un blocage pendant le processus d’enregistrement. Auparavant, toute tentative d’ajout ou de modification d’une adresse sans champ de région affiché générait une erreur d’exception.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38406>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38407>
* _AC-11919_ : Admin : Boutons d’actions de page flottants à gauche et à droite
   * _Remarque : le système aligne désormais correctement les boutons d’actions de page sur le côté droit de l’en-tête bascule dans le panneau d’administration, améliorant ainsi l’aspect professionnel._ Auparavant, ces boutons flottaient incorrectement sur le côté gauche de l’en-tête bascule.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38701>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/44cef3a9>
* _AC-11999_ : dev:di:Erreur d’information dans magento 2.4.7
   * _Remarque de correctif_ : le système affiche désormais correctement les paramètres du constructeur lors de l’exécution de la commande dev:di:info, ce qui empêche toute erreur. Auparavant, l’exécution de cette commande entraînait une erreur en raison d’une incohérence de type dans l’argument .
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38740>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-6071_ : le client est connecté mais affiche une erreur 404 dans le serveur frontal.
   * _Remarque :_ : la page du tableau de bord client storefront se charge désormais comme prévu lorsqu’un client se connecte. Auparavant, les clients pouvaient se connecter, mais cette page affichait une erreur 404. [GitHub-35838](https://github.com/magento/magento2/issues/35838)
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/35838>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/36263>
* _ACP2E-2791_ : impossible d’enregistrer les informations d’attributs du client dans la section Admin Modifier le client ;
   * _Remarque : L’ID de magasin du client est désormais correctement mis en oeuvre par portée de site web pour le formulaire de modification du client administrateur._
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/488c1034>

### Interface utilisateur d’administration

* _AC-11588_ : La validation des données est un succès et un bouton Importer est présent pendant l’importation des produits avec le comportement Remplacer
   * _Remarque de correctif_ : le système valide désormais correctement les données et masque le bouton &quot;Importer&quot; pendant le processus d’importation du produit avec le comportement &quot;Remplacer&quot;, ce qui empêche tout remplacement inattendu des données. Auparavant, le système avait incorrectement validé les données et affiché le bouton &quot;Importer&quot;, ce qui pouvait entraîner des incohérences entre les données.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/0574ac23>
* _AC-12167_ : [Bug] Magento 2.4.7 n’autorise pas les photos de produit avec extension de fichier de lettre majuscule.
   * _Remarque : le système accepte désormais les téléchargements d’images de produits avec des extensions de fichier de lettres majuscules, ce qui garantit un processus de création de produits fluide._ Auparavant, les téléchargements d’images avec extensions de fichier de majuscules étaient refusés, ce qui forçait les utilisateurs à modifier l’extension de fichier en minuscules.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38831>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-6975_ : [Problème] Définissez le mode d’indexeur par défaut sur &quot;planning&quot;
   * _Remarque de correctif_ : tous les nouveaux indexeurs sont par défaut en mode **[!UICONTROL Update by Schedule]**.  Auparavant, le mode par défaut était **[!UICONTROL Update on Save]**. Les indexeurs existants ne sont pas affectés. [GitHub-36419](https://github.com/magento/magento2/issues/36419)
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/36419>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/0b410856>
* _AC-7700_ : [Problème] Déposer les tables de modification de l’indexeur sur le désabonnement de l’affichage
   * _Remarque_ : le système supprime désormais automatiquement les tables de logs de modifications inutilisées lorsqu’un index passe de &quot;mise à jour programmée&quot; à &quot;mise à jour à l’enregistrement&quot;, marquant l’index comme non valide afin de s’assurer qu’aucune entrée n’est manquée. Auparavant, le fait de basculer un index sur &quot;mettre à jour lors de l’enregistrement&quot; laissait les tables modifielog inutilisées dans le système et marquait tous les index modifiés comme étant &quot;valides&quot;.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/29789>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/25859>
* _AC-9843_ : l’i18n:collect-expressions rompt l’intégrité des traductions
   * _Remarque :_ : la commande `bin/magento i18n:collect-phrases -o` collecte désormais correctement les nouvelles expressions des fichiers JavaScript et .phtml, en veillant à ce que les traductions soient reflétées avec précision dans le fichier de traduction. Auparavant, le système n’incluait pas d’expressions de traduction multi-lignes des fichiers JavaScript et d’expressions des fichiers .phtml dans le fichier de traduction, ce qui entraînait des traductions incomplètes ou incorrectes.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2787_ : l’appostrophe dans le nom de la vue de magasin est remplacée par &#39;
   * _Remarque : les filtres de vue de magasin de la grille affichent désormais correctement les apostrophes._
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38395>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2847_ : le téléchargement de favicon ne parvient pas à valider les fichiers .ico
   * _Remarque : correction_ : l’erreur de validation du fichier a été mise à jour en &quot;Échec de la validation du fichier. Vérifiez les paramètres de traitement des images dans la configuration du magasin.&quot; Auparavant, il s’agissait simplement de &quot;Échec de la validation du fichier&quot;.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2957_ : la galerie dans PageBuilder affiche une ancienne miniature d’image au lieu d’une image nouvellement chargée
   * _Remarque : Régénérer les aperçus d’image pour les images supprimées et rechargées avec le même nom via la galerie multimédia dans le contenu du créateur de pages._
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/001e5188>, <https://github.com/magento/magento2-page-builder/commit/60140cd2>
* _ACP2E-2978_ : l’enregistrement d’un produit par un utilisateur administrateur avec une portée différente écrase/supprime les informations de produit connexes existantes dans le produit.
   * _Remarque :_ : auparavant, avant le correctif, les produits associés étaient réinitialisés et devenaient vides lorsque l’utilisateur administrateur secondaire cliquait sur le bouton d’enregistrement sans modifier le produit associé. Après ce correctif, l’administrateur secondaire clique sur le bouton d’enregistrement et le produit ne se réinitialise pas et est enregistré correctement.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3033_ : impossible d’exporter plus de 200 commandes
   * _Remarque :_ : les limites du serveur relatives à la taille de requête des ID sélectionnés précédemment envoyés ont été négligées en modifiant la requête HTTP de GET à POST afin de résoudre le problème. Auparavant, en raison des limitations de taille de demande de GET du serveur, le problème était rencontré.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3037_ : message Validation de la page de passage en caisse incorrect.
   * _Remarque : Si un champ obligatoire n’est pas renseigné (par exemple, &quot;adresse&quot;), la validation côté serveur n’affiche pas le message._ La validation côté client permet de s’assurer que la notification d’erreur de champ requise s’affiche, en indiquant &quot;Il s’agit d’un champ obligatoire&quot;. Auparavant, le message &quot;l’adresse est requise&quot; s’affichait si un champ obligatoire était vide, en plus du message de validation côté client.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3125_ : problème de modèle de réinitialisation de mot de passe avec l’utilisateur administrateur
   * _Remarque : correction_ : le problème a été résolu à l’aide de la clé correcte, qui inclut désormais le nom d’utilisateur administrateur dans le modèle de courrier électronique et termine correctement l’objet. Auparavant, le problème provenait d’une clé obsolète utilisée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3149_ : double barre oblique dans l’URL du segment client
   * _Remarque : correction_ : les barres obliques doubles n’apparaissent pas dans l’URL lorsque l’utilisateur clique sur &quot;Réinitialiser le filtre&quot; dans la grille.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3171_ : la DCO n&#39;est pas disponible pour les pays spécifiques autorisés
   * _Remarque : les espèces à la livraison sont désormais disponibles pour des pays spécifiques autorisés chaque fois qu’elles sont requises et   AC-3216 fonctionne comme prévu._
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3178_ : impossible de mettre à jour l’état de commande créé personnalisé
   * _Note de correctif_ : &#39;
Nous pouvons désormais mettre à jour les statuts de commande personnalisés, alors qu’auparavant, l’état ne pouvait être modifié que si l’état actuel était &quot;traitement&quot; ou &quot;fraude&quot;.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38659>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/8459b17d>

### Interface utilisateur d’administration, performances

* _ACP2E-3169_ : après la mise à jour vers la version 2.4.5-p8 500 des erreurs se produisent lors de la création de l’ordre à partir de l’administrateur
   * _Remarque : auparavant, lors de l’activation de la minimisation des HTMLS, une commande de l’administrateur n’était pas possible._ Désormais, une fois la minification d’HTML activée, la commande de l’administrateur peut être placée correctement.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b21e5d91>

### Interface utilisateur d’administration, Livraison

* _ACP2E-2519_ : le nombre de codes de coupon ne se met pas à jour dans la variable   La colonne &quot;Durée d’utilisation&quot; de l’onglet Gérer les codes de bon si une commande est passée avec des frais d’expédition multiples.
   * _Remarque : auparavant, lorsqu’une commande était passée avec plusieurs envois, le nombre de codes de coupon n’était pas mis à jour dans la colonne &quot;Durée d’utilisation&quot; de l’onglet Gérer les codes de bon._ Désormais, le nombre correct s’affiche dans les deux &quot;Temps utilisé&quot;, reflétant les valeurs souhaitées avec plusieurs envois.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/4745100c>

### Analytics / Création de rapports

* _ACP2E-2570_ : le rapport d’avancement ne fonctionne pas
   * _Remarque :_ : le système prend désormais en charge la génération de fichiers de données de rapports avancés pour les jeux de données extra-volumineux en chargeant et en écrivant des rapports par lots de 10 000. Auparavant, le module de reporting avancé ne pouvait pas générer de fichiers de données pour les jeux de données extra-volumineux, ce qui provoquait des erreurs &quot;MySQL Server a disparu&quot; lors de l’exécution de la tâche analytics_collect_data cron.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-3080_ : problème de visibilité de la plage de dates du rapport Produits commandés par l’administrateur.
   * _Remarque : correction_ : l’utilisateur pourra sélectionner n’importe quelle date dans le rapport des produits commandés. Auparavant, après une actualisation du tableau, la sélection de la date &quot;DE&quot; réinitialisait la date &quot;À&quot;.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3096_ : les en-têtes d’URL incorrects qui renouvellent l’étiquette:create:deploy-marquate ne fonctionnent pas
   * _Remarque de correctif_ : le système formate désormais correctement les en-têtes curl, ce qui permet à la nouvelle commande deploy-marqueur :create: de créer un marqueur de déploiement dans New Relic. Auparavant, des en-têtes curl incorrects empêchaient la création d’un marqueur de déploiement dans New Relic.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37641>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/6a185204>

### Analytics / Création de rapports, B2B

* _ACP2E-2300_ : B2B - le plan de site comprend des produits/catégories non affectés au catalogue partagé
   * _Remarque : limitez les catégories et les produits générés par le plan de site aux catégories et aux produits affectés uniquement au catalogue partagé public et/ou à la configuration de l’autorisation de catégorie de catalogue._
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ea79f7dd>

### Analytics / Création de rapports, Cloud

* _ACP2E-3067_ : le Magento ignore la plupart des transactions New Relic cron #34108
   * _Remarque de correctif_ : AC signale correctement les transactions liées à la tâche cron à NewRelic. Auparavant, certaines transactions liées aux tâches cron s’affichaient comme &quot;OtherTransaction/Action/unknown&quot; dans NR
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/35b1b1da>

### B2B

* _ACP2E-3044_ : bordures inutiles dans la section Mes commandes
   * _Remarque :_ : Auparavant, un conteneur supplémentaire (références de commande) était créé pour appliquer des classes CSS supplémentaires, ce qui provoquait l’affichage de lignes de bordure inutiles sous le numéro de commande dans la section Mes commandes, qui n’est pas visible à présent.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/9af794a4>

### B2B, structure

* _AC-9607_ : le filtrage de la grille d’entreprise, puis la tentative d’exportation de grille CSV échoueront et généreront une exception
   * _Remarque_ : le système permet désormais d’exporter avec succès les données de la grille Entreprises dans le panneau d’administration, même si des filtres tels que &quot;Solde en attente&quot; et &quot;Type d’entreprise&quot; sont appliqués. Auparavant, l’application de certains filtres et la tentative d’exportation des données de la grille entraînait l’échec et l’envoi d’une exception.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/44cef3a9>

### Braintree

* _BUNDLE-3367_ : Payer par LPM
   * _Remarque : le système effectue désormais correctement le rendu des méthodes de paiement locales (LPM) au chargement initial, même lorsque les adresses d’expédition et de facturation d’un client connecté ne correspondent pas, ce qui garantit un processus de passage en caisse fluide._ Auparavant, une incohérence entre les adresses d’expédition et de facturation d’un client empêchait le rendu de LPM, ce qui pouvait entraîner des perturbations lors du passage en caisse.
   * _Contribution du code GitHub_ : <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3368_ : configurable avec Virtual as Child Product
   * _Remarque_ : le système permet désormais des méthodes de paiement express pour les produits configurables ayant un produit enfant virtuel, assurant ainsi un processus de passage en caisse fluide. Auparavant, les méthodes de paiement express n’étaient pas disponibles lorsqu’un produit configurable avec un produit enfant virtuel était ajouté au panier.
   * _Contribution du code GitHub_ : <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3369_ : Erreur de vérification CVV échouée
   * _Contribution du code GitHub_ : <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3370_ : Résolution des problèmes liés aux zones du compte 247
   * _Remarque :_ : le système permet désormais aux clients d’enregistrer de nouvelles informations de carte ou de compte PayPal sur plusieurs sites web sans rencontrer d’erreurs d’autorisation. Auparavant, les clients ne pouvaient pas enregistrer de nouveaux modes de paiement sur différents sites web et un message d’erreur d’autorisation s’affichait.
   * _Contribution du code GitHub_ : <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3371_ : Expéditeur d’une adresse d’un autre pays
   * _Remarque_ : le système permet désormais de traiter les transactions sans erreur lors de l’expédition vers une adresse d’un autre pays, ce qui garantit un processus de passage en caisse fluide. Auparavant, toute tentative d’envoi vers une adresse d’un autre pays générait des erreurs de console, en dépit d’aucune erreur visible sur le serveur frontal.
   * _Contribution du code GitHub_ : <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3372_ : Carte de crédit - Fonction Teardown
   * _Remarque :_ : le système gère désormais correctement le démarrage des composants PayPal Braintree lorsqu’un client revient de la page de paiement à la page d’expédition, ce qui empêche toute erreur et garantit que les boutons PayPal Express s’affichent correctement. Auparavant, la navigation vers la page d’expédition à partir de la page de paiement entraînait parfois une erreur lors de la tentative de désactivation des composants PayPal du Braintree.
   * _Contribution du code GitHub_ : <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3373_ : Rappel d’expédition pour PayPal Express
   * _Remarque :_ : le système affiche désormais correctement les méthodes de livraison disponibles dans le modal PayPal Express, ce qui permet aux clients de sélectionner leur méthode de livraison préférée avant de passer à la page de révision ou de terminer leur transaction. Auparavant, aucune méthode d’expédition ne pouvait être sélectionnée dans le modal PayPal Express, ce qui obligeait les clients à sélectionner une méthode d’expédition sur une page de révision distincte avant de pouvoir terminer leur transaction.
   * _Contribution du code GitHub_ : <https://github.com/magento/ext-braintree/pull/204>

### Panier et passage en caisse

* _AC-10660_ : les exceptions ne sont pas gérées correctement lors de l’ajout d’un produit au panier dans la page de comparaison des produits.
   * _Remarque de correctif_ : le système gère désormais correctement les exceptions lors de l’ajout d’un produit au panier à partir de la page de comparaison des produits, affichant un message du gestionnaire de messages dans le contrôleur. Auparavant, une exception provoquait le renvoi d’une page codée JSON au lieu d’être correctement capturée et gérée.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38200>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38257>, <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10698_ : GTag n’envoie pas les prix et les totaux des transactions.
   * _Remarque : le système envoie désormais correctement les prix et les totaux des transactions à Google Tag lorsque GTag est activé, ce qui permet d’assurer un suivi précis des données de commerce électronique._ Auparavant, la devise était incorrectement envoyée dans le cadre des commandes &quot;all&quot;, plutôt que d’être associée à la commande individuelle.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37348>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37504>, <https://github.com/magento/magento2/pull/37349>
* _AC-11641_ : [Problème] [Passage en caisse] Directives mises à jour dans le modèle d’email de paiement en échec
   * _Remarque de correctif_ : le système omet désormais correctement l’adresse de livraison et le mode de livraison du modèle d’email de paiement en échec pour les produits virtuels, en s’assurant que seules les informations pertinentes sont incluses dans l’email. Auparavant, l’adresse électronique de paiement pour les produits virtuels ne comprenait pas correctement l’adresse de livraison et le mode de livraison.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/32781>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/32511>
* _AC-11876_ : [Problème] Régression des règles de vente dans la version 2.4.7
   * _Remarque :_ : le système valide désormais correctement les règles de vente, empêchant l’application d’un code de bon à un panier lorsque la condition de produit ne correspond à aucun nom de produit. Auparavant, une règle de vente pouvait être appliquée et une remise était accordée sur le montant de livraison, même si la condition de produit ne correspondait à aucun nom de produit.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38671>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/0574ac23>
* _AC-11993_ : [Problème] Le chargeur bloque les méthodes d’expédition une fois le code postal modifié, les règles de validation des taux d’expédition
   * _Remarque de correctif_ : le système gère désormais correctement les méthodes d’expédition personnalisées sans règles de validation des taux d’expédition, en s’assurant que le chargeur ne bloque pas les méthodes d’expédition une fois le code postal modifié dans l’adresse d’expédition lors du passage en caisse. Auparavant, la modification du code postal dans l’adresse d’expédition lors du passage en caisse provoquait le blocage par le chargeur des méthodes d’expédition et ne disparaissait pas lorsque des méthodes d’expédition personnalisées sans règles de validation des taux d’expédition étaient utilisées.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38742>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1bafc571>
* _AC-12170_ : La fonction Code coupon ne fonctionne pas correctement dans la page de passage en caisse de Magento 2.4.7
   * _Remarque :_ : le système active désormais le champ d’entrée Code de remise/coupon sur la page de passage en caisse pour les produits virtuels et téléchargeables, ce qui permet aux utilisateurs d’appliquer les codes de réduction comme prévu. Auparavant, la saisie du code de remise/coupon était désactivée et le texte du titre du bouton s’affichait comme &quot;Annuler le bon&quot;, ce qui empêchait les utilisateurs d’appliquer des codes de réduction.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38826>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1bafc571>
* _AC-8103_ : TVA de traduction dans le moteur de rendu d’adresse
   * _Remarque de correctif_ : le système permet désormais la traduction du texte &quot;TVA&quot;, &quot;T&quot;, &quot;F&quot; dans les moteurs de rendu d’adresse, ce qui permet aux utilisateurs de traduire ces termes dans la langue spécifique du magasin. Auparavant, ces termes n’étaient pas traduisibles, ce qui forçait les utilisateurs à utiliser une solution de contournement.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/36942>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/36943>
* _ACP2E-2055_ : dupliquer simultanément des commandes avec le même ID de devis avec peu de différence de temps
   * _Remarque : correction_ : correction d’un problème en raison duquel les clients Adobe Commerce rencontraient des commandes en double avec le même ID de devis.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2470_ : panier persistant effacé lors de l’étape de passage en caisse
   * _Remarque : après le correctif, la sélection du mode de paiement lors de l’extraction alors qu’elle n’est pas connectée ne met pas fin à la session persistante._
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2518_ : la réorganisation ajoute un produit non attribué au panier
   * _Remarque : auparavant, pour les différents magasins, les produits peuvent être réorganisés à partir de l’autre magasin._ Une fois ce correctif appliqué uniquement au même magasin , un même produit de portée peut être réorganisé lorsque le partage de compte client est activé.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2620_ : dans l’administration, le &quot;panier&quot; sur le côté gauche n’est pas mis à jour lors de la sélection des éléments et &quot;Déplacer vers le panier&quot; sur le côté droit.
   * _Remarque : correction_ : le &quot;panier&quot; sur le côté gauche est mis à jour lors de la sélection des éléments et &quot;Accéder au panier&quot; sur le côté droit dans le côté administrateur. Auparavant, cette fonctionnalité ne fonctionnait pas, car les éléments de panier transformés n’étaient pas vides de la session.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2646_ : [Cloud] Règle de vente non appliquée à la première commande de plusieurs envois
   * _Remarque : après le correctif, la remise s’affiche correctement pour chaque commande du même guillemet multi-expédition._
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2664_ : [Cloud] Demandes parallèles de production pour ajouter un même produit au panier génèrent deux articles distincts dans l’API de repos du panier
   * _Remarque :_ : le système traite désormais correctement plusieurs demandes parallèles pour ajouter le même produit au panier sur une seule ligne, ce qui empêche la création d’éléments de ligne distincts pour le même SKU. Auparavant, le fait d’effectuer des requêtes parallèles pour ajouter le même produit au panier via l’API REST générait plusieurs lignes pour le même SKU.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2704_ : impossible d’envoyer le cookie. Taille des &quot;messages-images&quot; lors de la tentative de réorganisation
   * _Remarque : le processus de réorganisation ne génère pas désormais ses propres erreurs._ Elle repose sur les vérifications d’articles intégrées au panier de la liste.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2798_ : l’adresse de livraison par défaut n’est pas sélectionnée lors du passage en caisse
   * _Remarque : correction_ : l’adresse de livraison par défaut est désormais sélectionnée dans le cadre de la recherche d’adresses activée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2897_ : [CLOUD] problème d’api graphql addProductsToCart avec option personnalisée
   * _Remarque : GraphQL ajoute correctement au panier le même produit avec différentes options personnalisées._
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2923_ : plusieurs adresses ajoutées au compte lors de l’extraction en tant que nouveau client
   * _Remarque :_ : le système n’enregistre désormais une nouvelle adresse client qu’une seule fois si la commande n’a pas été créée, ce qui empêche la création de plusieurs adresses identiques en cas d’erreur de placement de commande. Auparavant, le système enregistrait une nouvelle adresse à chaque tentative de placement de commande, que la commande ait été créée ou non.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/001e5188>, <https://github.com/magento/inventory/commit/2ebcef39>
* _ACP2E-3004_ : la réorganisation de la commande client par le biais d’un formulaire de commande d’invité entraîne un panier vide
   * _Remarque :_ : auparavant, lors d’une réorganisation dans la page Commandes et retours, le client était redirigé vers la page de connexion. Une fois ce correctif appliqué, le client enregistré est correctement redirigé vers la page Afficher le panier lors du placement d’une nouvelle commande. Le flux fonctionne de la même manière que les clients invités.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3025_ : utilisateur administrateur avec des ressources de rôle limité incapable d’afficher les paniers d’achat
   * _Remarque :_ : auparavant, les administrateurs à accès limité ne pouvaient pas voir le panier abandonné dans le panneau d’administration d’un site web associé. Une fois ce correctif appliqué, l’administrateur restreint peut voir le panier abandonné depuis le panneau d’administration.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d1f7dc95>

### Panier et passage en caisse, passage en caisse/passage en caisse d’une page

* _AC-9386_ : [BOGUE aléatoire] Le champ de l’e-mail n’est pas rendu ou prend beaucoup de temps à s’afficher dans la page Expédition du passage en caisse ou paiement
   * _Remarque : Commerce effectue désormais le rendu du champ **[!UICONTROL Email]**sur les pages d’expédition et de paiement de passage en caisse comme prévu._ Auparavant, ce champ était absent ou rendu lentement.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/e1babcfd>

### Panier et achat, commande

* _ACP2E-3097_ : sélecteur de date pour un produit avec plusieurs options personnalisables dont les champs de date ne fonctionnent pas lors du placement de la commande depuis l’administrateur
   * _Remarque : le système affiche désormais correctement le sélecteur de date pour tous les champs de date lors de la configuration d’un produit avec plusieurs options de date personnalisables dans le processus de création de commande de l’administrateur._ Auparavant, le sélecteur de date ne s’affichait que pour le premier champ de date, laissant les champs restants sans sélecteur de date.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b21e5d91>

### Panier et paiement, livraison

* _AC-12119_ : achat instantané de &quot;livraison la moins chère&quot; interrompue pour les produits configurables
   * _Remarque : La fonction Achat instantané a incorrectement sélectionné l’option de remise en magasin la plus chère pour les produits configurables au lieu de la méthode de taux plat la moins chère._ Ce correctif garantit que le bon mode de livraison est choisi en fonction du prix réel.&quot;
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38811>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38819>, <https://github.com/magento/magento2/commit/29fe9097>

### Catalogue

* _AC-10910_ : le nettoyage de la table de base de données cron_schedule ne nettoie pas les tâches non existantes
   * _Remarque de correctif_ : le système nettoie désormais automatiquement la table de base de données cron_schedule, supprimant ainsi les entrées pour les tâches qui n’existent plus dans le système. Cela garantit des performances optimales en conservant un nombre minimal de lignes dans le tableau. Auparavant, les entrées des tâches des modules inactifs ou supprimés n’étaient pas nettoyées, ce qui entraînait une accumulation inutile de données dans la table cron_schedule.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38217>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38693>
* _AC-10953_ : Le prix de niveau n’est pas supprimé des produits configurables.
   * _Remarque :_ : le système supprime désormais correctement le prix de niveau d’un produit lorsqu’il est converti d’un produit simple à un produit configurable, assurant ainsi un affichage précis des prix sur l’interface. Auparavant, le prix de niveau d’un produit configurable n’était pas supprimé lorsqu’un produit était converti d’un produit simple vers un produit configurable, ce qui entraînait une incohérence dans le prix affiché.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38390>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38427>
* _AC-11804_ : description de catégorie WYSIWYG est vide sur un storeview autre que le storeview par défaut
   * _Remarque : le système enregistre et affiche désormais correctement la description de la catégorie dans l’éditeur WYSIWYG lors de la modification d’une catégorie au niveau de la vue de magasin._ Auparavant, l’éditeur WYSIWYG apparaissait vide après l’enregistrement d’une description de catégorie au niveau de la vue de magasin.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38622>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38623>
* _AC-12076_ : [Problème] Correction de la formulation de l’élément de filtre sur la navigation par couches
   * _Remarque de correctif_ : le système utilise désormais correctement les mots &quot;item&quot; et &quot;items&quot; dans l’élément de filtre de navigation par couches, ce qui améliore la clarté et la précision des descriptions de filtre. Auparavant, ces mots étaient utilisés de manière incorrecte, ce qui pouvait prêter à confusion lorsque les utilisateurs naviguaient dans les options de filtrage.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38789>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37852>
* _AC-12164_ : Le format de date et d’heure pour l’option personnalisée ne fonctionne pas
   * _Remarque : le système applique désormais correctement le format de date configuré aux options personnalisées de type Date du produit, en s’assurant que le format de date s’affiche correctement sur le serveur frontal._ Auparavant, les modifications apportées à la configuration du format de date ne se répercutaient pas sur le serveur frontal pour les options personnalisées de produit de type Date.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/32990>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38925>
* _AC-6738_ : clé unique manquante sur la table eav_attribute_option_value
   * _Remarque :_ : le système inclut désormais une clé unique sur les colonnes &#39;option_id&#39; et &#39;store_id&#39; dans la table &#39;eav_attribute_option_value&#39;, ce qui empêche qu’une option ait plusieurs valeurs pour la même vue de magasin. Auparavant, un code incorrect pouvait entraîner la présence de plusieurs valeurs pour la même vue de magasin, ce qui provoquait des problèmes lors de la modification des produits ou des attributs.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/24718>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/28796>
* _AC-8297_ : [Problème] Utilisez la classe de visibilité pour l’indexeur de produits de catégorie, au lieu des valeurs codées en dur
   * _Remarque de correctif_ : le système utilise désormais la classe de visibilité pour l’indexeur de produits de catégorie plutôt que les valeurs codées en dur, ce qui améliore la modularité. Auparavant, les valeurs codées en dur étaient utilisées dans l’indexeur de produits de catégorie, ce qui limitait la flexibilité et l’adaptabilité.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37200>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37199>
* _AC-9375_ : le code de devise ne change pas dans le nouveau widget de produit
   * _Remarque : le système met désormais correctement à jour le code de devise dans le widget Nouveau produit lorsque la devise est modifiée dans l’interface utilisateur frontale, assurant ainsi la cohérence de l’affichage des devises sur l’ensemble du site._ Auparavant, la modification de la devise dans l’interface utilisateur frontale n’affectait pas le code de devise affiché dans le widget Nouveau produit.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37898>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37899>
* _ACP2E-2224_ : le prix normal ne s’affiche pas sur PLP pour un produit configurable
   * _Remarque : le prix normal s’affiche désormais sur les pages de liste de produits pour les produits configurables ayant des produits enfants avec des prix spéciaux._
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2478_ : les informations sur les stocks ne s’affichent pas correctement sur la grille de marchandisage visuel
   * _Remarque : correction_ : le stock s’affiche désormais en fonction de la boutique sélectionnée.
   * _Contribution du code GitHub_ : <https://github.com/magento/inventory/commit/bdbf97ea>
* _ACP2E-2621_ : le contenu du widget n’est pas mis à jour sur la page cms
   * _Remarque : le système met à jour le contenu du widget sur une page CMS lorsqu’un produit est défini comme nouveau et enregistré, en s’assurant que la page affiche la collection de produits mise à jour._ Auparavant, la page n’était pas mise à jour pour afficher le nouveau produit en raison des identités de cache incorrectes utilisées pour le widget dans le cache.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2630_ : problèmes d’enregistrement des tarifs avancés sur les produits en regroupement
   * _Remarque : correction_ : amélioration des performances de l’enregistrement des produits par lots.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2652_ : [Le processus de réindexation On-Premise] est inefficace lors de la création de règles de prix de catalogue
   * _Remarque_ : l’enregistrement de la règle de prix du catalogue n’invalidera pas les indexeurs, mais réindexera uniquement les produits affectés.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2679_ : mise à jour des attributs de produit de type Date et Heure via une importation CSV
   * _Remarque : correction_ : les attributs datetime disposent désormais d’un temps partiel dans les données exportées. Il sera également possible de mettre à jour l’heure de ces attributs à l’aide de l’import. En outre, si l’option &quot;Complément de champs&quot; est activée, les valeurs d’attribut de la colonne &quot;additional_attributes&quot; sont entourées de guillemets doubles.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38306>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2689_ : aucun message d’erreur approprié lorsque l’ID de site web est incorrect dans la requête
   * _Remarque : correction_ : le message d’erreur approprié a été ajouté pour s’afficher lorsque l’ID de site web est incorrect dans la requête. Auparavant, aucune validation n’était effectuée lorsque l’ID du site web était incorrect dans la requête.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2785_ : l’image du produit est perdue après la suppression d’une mise à jour planifiée existante qui n’affecte pas l’image.
   * _Remarque : les images de produit ne sont pas supprimées lors de la suppression de la mise à jour d’évaluation._
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-2799_ : [Cloud] Prix du produit groupé incorrect lorsqu’il est utilisé avec des prix de niveau
   * _Remarque : Auparavant, lors du calcul de certains pourcentage de remises arrondies à 2 décimales près, les prix finaux pour le panier et la page de détails des produits étaient différents._ Une fois ce correctif appliqué, le prix final du produit groupé est le même que dans la page des détails du produit, la page de liste des produits et la page du mini panier.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38091>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2805_ : la règle de promotions de catalogue ne fonctionne pas avec l’attribut quantity_and_stock_status
   * _Remarque sur les correctifs_ : l’attribut quantity_and_stock_status sera désormais pris en compte par la règle de promotion du catalogue, qui n’était pas auparavant prise en compte lors de la génération d’un nouveau produit du côté administrateur.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/35627>
   * _Contribution du code GitHub_ : <https://github.com/magento/inventory/commit/cf34971d>
* _ACP2E-2837_ : l’entité de produit a mis à jour les valeurs de colonne _at sans mise à jour lors de la mise à jour du prix via l’API REST
   * _Remarque : La colonne &quot;Dernière mise à jour à&quot; du produit de l’administrateur est mise à jour à la date correcte lors de la mise à jour des produits existants via l’API REST._ Auparavant, la colonne &quot;Dernière mise à jour à&quot; n’était pas correctement mise à jour.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2840_ : il est possible de définir des valeurs non uniques par le biais de l’importation de produits
   * _Remarque de correctif_ : le système applique désormais correctement la contrainte de valeur unique pour les attributs de produit uniques lors de l’importation du produit, empêchant la duplication de valeurs pour cet attribut. Auparavant, il était possible de définir des valeurs non uniques pour les attributs de produit qui étaient configurés pour avoir des valeurs uniques par le biais de l’importation de produit.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38445>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2843_ : les produits sur le front-end utilisent des données spécifiques au magasin lorsque le mode Boutique unique est activé
   * _Remarque : auparavant, lorsque nous activions le mode de magasin unique pour la vue de magasin par défaut, les modifications n’étaient pas migrées vers la portée au niveau du site web._ Une fois ce correctif appliqué, lorsque nous activons le mode de magasin unique, les données par défaut propres à l’affichage du magasin sont synchronisées avec les données spécifiques au niveau du site web et résolvent les conflits possibles pour les produits et les catégories.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-2857_ : impossible de définir &quot;Par défaut de tri&quot; dans une catégorie à l’aide de l’API REST
   * _Note de correctif_ : mettez à jour correctement default_sort_by sur une catégorie via une requête REST/SOAP APi
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2871_ : [Cloud] Le marchand rencontre des problèmes avec un nombre de listes de souhaits.
   * _Remarque : l’ajout d’un produit à la liste des souhaits dans un magasin n’augmente plus le nombre de listes souhaitées dans d’autres magasins ouverts dans le même navigateur._ Auparavant, si les deux magasins étaient chargés dans le même navigateur, le nombre de listes bloquées augmentait également dans l’autre magasin.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2874_ : la page de catégorie à l’interface affiche des emplacements vides lors de l’utilisation d’un produit groupé
   * _Remarque : les produits groupés qui ne sont pas vendables dans le contexte actuel du magasin ne sont plus indexés._
   * _Contribution du code GitHub_ : <https://github.com/magento/inventory/commit/bc37ec76>
* _ACP2E-2905_ : [Cloud] Problème de devis dans l’architecture multi-site
   * _Remarque : Auparavant, l’architecture multi-site avec des devises et des groupes de clients différents ne pouvait pas appliquer correctement les remises au magasin._ Une fois ce correctif mis en oeuvre, l’architecture multi-site avec des remises sur le prix de groupe de clients différentes s’applique correctement à différents magasins.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38506>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2909_ : dynamic-rows.js:658 Uncaught TypeError: dataRecord.slice lors de la modification de produits du lot
   * _Remarque : il n’y a pas d’erreur JavaScript dans la console du navigateur lors de la suppression d’une option du produit groupé._
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38505>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-2950_ : [Cloud] Mauvaise tarification du produit lors de la confirmation de commande
   * _Remarque : correction_ : le montant correct s’affiche pour les options de bundle dans l’ordre sur Storefront lorsque la devise autre que la base 1 a été utilisée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2956_ : bogue d’ajout de vidéos YouTube
   * _Remarque : les images et les vidéos des produits sont configurées dans la portée globale._ Étant donné que vous ne pouvez pas avoir de vidéo de produit dans une portée et non dans une autre, le paramètre de clé de l’API YouTube a été défini sur une portée globale.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2964_ : [Cloud] Mise à jour de l’URL uniquement pour store_id=0
   * _Remarque de correctif_ : Le &quot;chemin d’accès à l’URL&quot; est désormais stocké avec l’ID de magasin correct. Auparavant, l’ID de magasin était incorrect, ce qui entraînait des chemins d’URL incorrects restant dans la base de données lors du déplacement de catégories.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3009_ : async.operations.all exécuté et a créé une erreur.
   * _Remarque : correction_ : les données de lien de produit incorrectes dans les appels API REST ne provoquent plus d’erreurs critiques.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-3029_ : [Cloud] Problème mobile Impossible de pincer sur l’image PDP uniquement
   * _Remarque : le système prend désormais en charge la fonctionnalité de pincement pour zoomer sur les images de page des détails du produit dans la vue mobile sur Chrome, ce qui améliore l’expérience de l’utilisateur mobile._ Auparavant, le fait d’appuyer deux fois sur l’image dans la vue mobile sur Chrome n’effectuait pas de zoom avant comme prévu.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3058_ : libellé manquant dans LayeredNavigation avec le nom de l’option 0
   * _Remarque de correctif_ : le problème a été résolu en ignorant un vérificateur de valeur vide pour la valeur d’attribut 0. Auparavant, il était considéré comme vide et provoquait le problème.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-3069_ : les clients voient les prix d&#39;autres groupes de clients
   * _Remarque : correction_ : correction d’un problème en raison duquel les informations relatives aux groupes de clients étaient enregistrées dans un segment incorrect en raison de l’ancienne valeur de X-Magento-Vary dans la demande.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3076_ : erreur lors de la suppression des options de lot
   * _Remarque : le système supprime désormais correctement les options de lot sans déclencher d’erreur ni provoquer la perte de réponse de la page._ Auparavant, la tentative de suppression des options de lot entraînait une erreur &quot;Ne pas répondre à la page&quot; et empêchait l’enregistrement du produit.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3100_ : [Cloud] Le fichier image n’existe pas dans le journal des erreurs New Relic
   * _Remarque :_ : le système synchronise désormais les images d’espace réservé personnalisées dans le stockage local, en s’assurant qu’elles s’affichent correctement lors de l’utilisation d’un stockage distant tel qu’AWS S3. Auparavant, le rendu des images d’espace réservé personnalisé échouait lors de l’utilisation d’un stockage à distance, ce qui entraînait un affichage d’image rompu et des journaux d’erreurs.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3126_ : [Cloud] La réponse GQL de la galerie de médias de produits n’est pas triée par position d’image
   * _Remarque : correction_ : le système trie désormais correctement les éléments de la galerie multimédia par position dans la réponse GraphQL, assurant ainsi un ordre d’affichage précis. Auparavant, les éléments de la galerie multimédia n’étaient pas triés par position, ce qui entraînait un ordre d’affichage incorrect.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37671>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3136_ : [Cloud] Les éléments de sous-catégorie ne s’affichent pas sur les widgets modifiés sur le serveur principal d’administration
   * _Remarque : l’arborescence des catégories sur la nouvelle page du widget ne doit plus rencontrer de problèmes lors du chargement des catégories de niveau 5+._ Auparavant, certaines catégories manquaient lors du chargement de l’arborescence au-delà des catégories Niveau 5.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/148c3ead>

### Catalogue, structure

* _ACP2E-2949_ : [Cloud]Suite : incohérence dans la comparaison des données lors de la vérification que les données comportent des modifications
   * _Remarque :_ : auparavant, l’objet d’enregistrement était appelé à chaque fois sans modification de données (pour tout champ de données numérique, comme int/float/double). Elle déclenche l’indicateur _hasDataChanges sur true et appelle la fonction save . Il ne vérifie pas non plus les nombres flottants encapsulés par une chaîne. Une fois ce correctif appliqué, la fonction save n’appelle que si les données sont modifiées. La valeur de données pour int/float/double-check avec la valeur transmettant à la fonction et fait correspondre strictement le type
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c8931218>

### Catalogue, GraphQL

* _ACP2E-3090_ : gestion des filtres de catégorie dans GraphQL : includeDirectChildrenOnly et category_uid
   * _Remarque : seuls les types de catégories enfants directes sont récupérés lors du filtrage par catégorie_uid._
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3166_ : [Cloud] Le tri des produits Graphql ne fonctionne pas
   * _Remarque : correction_ : le tri des produits GraphQl par plusieurs champs lorsque les champs sont transmis dans les variables fonctionne désormais comme prévu.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/8459b17d>

### Catalogue, tarification, évaluation et aperçu

* _ACP2E-2672_ : [Cloud] Le point d’entrée API de prix spécial renvoie une erreur lors de la mise à jour simultanée d’un grand nombre de produits
   * _Remarque : maintenant l’API de mise à jour en masse des prix spéciaux crée une campagne unique pour chaque période au lieu de plusieurs mises à jour planifiées pour chaque produit et période._ En outre, elle prend en charge les demandes d’API simultanées pour un traitement plus rapide d’un grand nombre de SKU.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/f89a447e>

### Catalogue, produit

* _AC-7050_ : l’arborescence de sélection des catégories dans l’édition du produit n’est pas dans le même ordre que défini dans Catalogue->Catégories
   * _Remarque :_ : le système affiche désormais correctement l’arborescence de sélection de catégories dans la section d’édition du produit dans le même ordre que défini dans Catalogue ->Catégories, ce qui facilite l’administration des produits dans les catalogues volumineux. Auparavant, l’arborescence des catégories de la section d’édition du produit s’affichait dans l’ordre de création de la catégorie, quel que soit l’ordre d’affichage défini dans Catalogue -> Catégories.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/36101>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/36104>

### Catalogue, recherche

* _ACP2E-2757_ : les produits ne s’affichent pas sur la catégorie et la recherche, mais les liens directs fonctionnent
   * _Remarque de correctif_ : auparavant, l’attribut personnalisé Oui/Non avec price_* attribute_code ne fonctionnait pas avec l’indexation. Après ce correctif, l’attribut personnalisé Oui/Non fonctionne comme prévu.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-3053_ : [Cloud] Erreur de recherche élastique sur certaines pages de catégorie
   * _Remarque : auparavant, avec le ticket de configuration mentionné, lorsque nous mettions le prix 0 pour plusieurs produits, une exception était générée sur la page de catégorie frontale._ Une fois ce correctif appliqué lorsque plusieurs prix de produit 0 et que nous chargeons la page de catégorie au front, il ne renvoie aucune exception et charge la page de catégorie avec succès.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c8931218>

### Cloud

* _ACP2E-3010_ : [Cloud] PHPSESSID modifie chaque demande de POST
   * _Remarque de correctif_ : PHPSESSID ne se régénère plus sur les demandes de POST sur la zone frontale d’un client connecté si le cache de Redis L2 est activé et que le client a été mis à jour à partir du serveur principal.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/6a185204>

### Contenu

* _AC-10539_ : [Problème] lié à l’affichage du prix dans le widget Récemment consultés
   * _Remarque :_ : le système affiche désormais correctement le prix des produits simples en rupture de stock dans le widget &quot;Produit récemment consulté&quot;, assurant ainsi la cohérence entre tous les widgets et toutes les pages de liste de produits. Auparavant, le prix des produits simples en rupture de stock n’était pas affiché dans le widget &quot;Produit récemment consulté&quot; en raison d’une condition dans les modèles de chargement de prix.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38167>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38159>
* _AC-10596_ : [Problème] Correction de la faute de frappe et de la grammaire dans le fichier acl.xsd
   * _Remarque de correctif_ : le système corrige désormais une erreur de typo et de grammaire dans le fichier acl.xsd, ce qui améliore la clarté et la précision de la documentation. Auparavant, le fichier acl.xsd contenait une faute de frappe et une grammaire incorrecte, ce qui pouvait entraîner une confusion.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38061>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38046>
* _AC-10845_ : image de bannière du générateur de pages non visible dans la galerie
   * _Remarque : le système affiche désormais correctement les images de bannière téléchargées dans les dossiers nouvellement créés dans la galerie Pagebuilder, éliminant ainsi les erreurs de console précédentes._ Avant ce correctif, les images de bannière n’étaient pas visibles dans la galerie si elles étaient chargées dans un nouveau dossier, ce qui provoquait une erreur de console.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-12283_ : &quot;Code régional non défini&quot; après la mise à jour vers la version 2.4.5-p8
   * _Remarque de correctif_ : le système termine désormais avec succès le processus de déploiement de contenu statique lorsque le module Magento_CSP est activé et que &quot;dev/js/translate_strategy&quot; est défini sur &quot;incorporé&quot;, sans déclencher l’erreur &quot;Code régional non défini&quot;. Auparavant, dans ces conditions, le processus de déploiement de contenu statique échouait avec une erreur &quot;Code régional non défini&quot;.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38845>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38922>
* _AC-9638_ : [ problème de téléchargement de fichier dans l’éditeur WYSIWYG sur la page du produit]
   * _Remarque :_ : le système affiche désormais correctement l’arborescence de dossiers et permet les chargements d’images dans l’éditeur WYSIWYG sur la page du produit, même après avoir développé l’onglet &quot;Image et vidéos&quot; en premier. Auparavant, le fait de développer l’onglet &quot;Image et vidéos&quot; entraînait d’abord l’affichage de l’arborescence de dossiers et d’un message d’erreur lors du téléchargement d’une image dans l’éditeur WYSIWYG.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38026>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38025>
* _ACP2E-2392_ : [On-PREM] Problème de bloc dynamique
   * _Remarque : les widgets sont désormais correctement rendus dans les blocs dynamiques._
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2693_ : [Cloud] La frontière ne se charge pas en raison d’un problème dans le modèle de newsletter
   * _Remarque : l’ajout de blocs via la section de contenu Page CMS ne mène plus à l’exception_
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2836_ : ACP2E-2836 : [Cloud] Exception d&#39;investigation trouvée dans le journal : InvalidArgumentException : la classe n&#39;existe pas dans vendor/magento/module-rule/Model/ConditionFactory.php
   * _Remarque : la suppression d’une condition dans les paramètres de contenu des produits PageBuilder ne provoque plus l’enregistrement d’une exception dans les fichiers journaux._ Auparavant, la suppression d’une condition sur les paramètres de contenu des produits PageBuilder entraînait l’enregistrement d’une exception critique dans les journaux, bien qu’elle ne provoquait aucun problème sur le front-end.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2-page-builder/commit/36c0f5df>
* _ACP2E-2842_ : passage en mode de magasin unique - le contenu global n’apparaît plus
   * _Remarque : le système synchronise désormais les configurations de conception de vue de magasin avec les configurations de conception de site web lors de l’activation du mode de magasin unique, en s’assurant que les mises à jour de contenu sont visibles sur le serveur frontal._ Auparavant, le passage en mode de magasin unique empêchait la mise à jour du contenu de se répercuter sur le storefront.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2903_ : le générateur de pages remplace l’image en essayant d’ajouter un lien et d’autres problèmes d’utilisation.
   * _Remarque : correction_ : maintenant que vous cliquez sur une image, les liens dans l’éditeur de texte de l’outil de texte de Page Builder chargent les données appropriées dans l’image, dans la boîte de dialogue de configuration des liens. L’ajout d’un lien vers une image dans l’éditeur fonctionne désormais correctement. Auparavant, l’image était remplacée par un lien.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-2970_ : l’ancienne galerie multimédia ne parvient pas à effectuer le rendu des images lorsqu’une image de 0 octet est placée dans le répertoire
   * _Remarque de correctif_ : le système gère désormais les images de 0 octet dans la galerie multimédia sans perturber la fonctionnalité, ce qui permet à d’autres images du répertoire d’être affichées et sélectionnées comme prévu. Auparavant, la présence d’une image de 0 octet dans la galerie multimédia empêchait l’affichage ou la sélection de toutes les images du répertoire.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3064_ : Créateur de pages d’erreur lors de la modification du bloc CMS
   * _Remarque : le système enregistre désormais correctement les modifications apportées à la zone d’administration à l’aide du créateur de pages, sans générer l’erreur &quot;Le créateur de pages a effectué le rendu pendant 5 secondes sans déclencher de verrous&quot;._ dans la console du navigateur. Auparavant, cette erreur survenait lors de la tentative d’enregistrement des modifications, empêchant la mise à jour du contenu.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/35b1b1da>, <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-3092_ : [CLOUD] Aucun bouton de passage en caisse ou de modification du panier dans la section panier
   * _Remarque : Le produit par lots est maintenant ajouté au panier par le biais de widgets sans erreur._
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b21e5d91>, <https://github.com/magento/magento2-page-builder/commit/4ebe3f1d>
* _ACP2E-3127_ : imagecreatetruecolor() : l’argument #2 ($height) doit être supérieur à 0. Impossible de charger une image spécifique
   * _Remarque : correction_ : résolution du problème provoquant des erreurs dans l’administrateur lors du téléchargement d’images dont la hauteur est de 0 via la galerie multimédia et de la synchronisation des ressources à l’aide de la commande de synchronisation. Auparavant, il n’était pas possible de télécharger l’image par le biais de la galerie multimédia. De plus, la commande de synchronisation échouait lorsqu’une image spécifique se trouvait dans la galerie.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3154_ : Prototype.js Array.from en conflit avec l’API Google Maps
   * _Remarque : Google Maps s’affiche désormais correctement dans l’éditeur PageBuilder._ Auparavant, une erreur JavaScript empêchait le rendu correct des cartes Google.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/148c3ead>

### Client/Clients

* _AC-12162_ : front-end - La validation de la date de naissance échoue dans la page de création du client
   * _Remarque : Assurez-vous que toutes les validations fonctionnent après la mise à niveau de la dépendance du système moment.js vers la dernière version mineure._
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/de4dfb8e>

### Framework

* _AC-10654_ : question/problème de point de terminaison V1/customers/password
   * _Remarque de correctif_ : le système respecte désormais les contraintes définies dans l’interface utilisateur graphique de gestion lors du traitement des demandes de modification de mot de passe via l’API, ce qui empêche tout abus potentiel de la fonction de réinitialisation de mot de passe. Auparavant, l’API pouvait traiter les demandes de modification de mot de passe en dehors des règles définies dans l’interface utilisateur graphique de la gestion, ce qui pouvait permettre un flux constant de réinitialisation des emails si des emails valides étaient connus.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38238>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10721_ :
   * _Remarque de correctif_ : mettez à niveau les dépendances du compositeur de ligue/système de vol vers la dernière version.
   * _Problème GitHub_ : &lt;<https://github.com/magento/magento2/commit/91cb4d46>>
   * _Contribution du code GitHub_ : mettez à niveau les dépendances de la ligue 2.x/du compositeur de système de vol vers la dernière version 3.x
* _AC-10838_ : processus d’indexation des erreurs du processus d’index de recherche catalogue
   * _Remarque de correctif_ : le système termine désormais la commande de réindexation sans rencontrer d’erreur, quelle que soit la version de la bibliothèque compilée avec PHP. Auparavant, l’exécution de la commande de réindexation entraînait une erreur de &quot;processus d’index de recherche catalogue lors du processus d’indexation&quot; lorsque PHP était compilé avec certaines versions de libxml.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38254>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38553>, <https://github.com/magento/magento2/commit/0574ac23>
* _AC-10941_ : ajout de filtres created_at, status et grand_total à la requête Commandes du client et correction de plusieurs échecs de filtres
   * _Remarque :_ : le système prend désormais en charge l’utilisation des filtres created_at, status et grand_total dans les requêtes de commandes client. Il a résolu un problème en raison duquel plusieurs filtres n’étaient pas correctement appliqués. Auparavant, le système ne prenait pas en charge ces filtres et ne parvenait pas à appliquer tous les filtres lorsque plusieurs d’entre eux étaient utilisés dans une requête.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38392>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/36949>
* _AC-10971_ : https://github.com/magento/magento2/issues/38415
   * _Remarque de correctif_ : PHP 8.2/8.3, une seule dépendance échoue au php linter en ce moment : league/flysystem
   * _Problème GitHub_ : &lt;<https://github.com/magento/magento2/commit/672a2e61>>
   * _Contribution du code GitHub_ : le système prend désormais en charge PHP 8.2/8.3 en mettant à jour le package de la ligue/du système de vol vers la version 3.0.20, ce qui permet d’éviter toute erreur de liaison PHP. Auparavant, l’exécution de fichiers PHP via la ligne PHP avec PHP 8.3 entraînait des erreurs de liaison dans le package league/flysystem.
* _AC-10991_ : inondation aléatoire de requêtes provenant de blocs associés / upsell / crosssell et d’indexation de prix
   * _Remarque :_ : le système optimise désormais les requêtes des blocs associés, de vente incitative et de vente croisée, ce qui améliore les performances et empêche le site de s’arrêter en raison de requêtes excessives. Auparavant, le système pouvait devenir surchargé avec des requêtes de ces blocs, ce qui provoquait des ralentissements importants et pouvait entraîner la panne du site.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/36667>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38050>
* _AC-11423_ : Exception : Avertissement : tentative d’accès au décalage de tableau dans... -> Calendar.php depuis la mise à niveau vers l’ICU 74.1 (PHP Intl)
   * _Remarque :_ : Commerce ne consigne plus l’exception suivante dans le fichier exception.log chaque fois qu’un acheteur ou un commerçant visite le storefront ou l’administrateur : `main.CRITICAL: Exception: Warning: Trying to access array offset on value of type null in /vendor/magento/framework/View/Element/Html/Calendar.php on line 114 in /vendor/magento/framework/App/ErrorHandler.php:62`. [GitHub-38214](https://github.com/magento/magento2/issues/38214)
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38214>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38364>
* _AC-11476_ : [Problème] Correction de problèmes liés aux données client lorsque le formulaire contient un élément portant le nom `method`
   * _Remarque de correctif_ : le système identifie désormais correctement l’attribut &#39;method&#39; dans les envois de formulaire, même lorsqu’un élément nommé &#39;method&#39; est présent dans le formulaire. Cela garantit un traitement précis des données client. Auparavant, si un élément de formulaire était nommé &quot;method&quot;, il interférait avec l’identification de l’attribut &quot;method&quot; dans les envois de formulaire, ce qui pouvait entraîner des problèmes potentiels avec la gestion des données client.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38484>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38449>
* _AC-11489_ : [Problème] Correction des PHPDocs pour \Magento\Framework\Data\Collection::getItemById
   * _Remarque de correctif_ : les PHPDocs de la méthode \Magento\Framework\Data\Collection::getItemById ont été mis à jour afin d’inclure null comme type de retour possible, ce qui résout les problèmes liés aux outils d’analyse statique. Auparavant, les PHPDocs de la méthode ne spécifiaient pas null comme type de retour possible, ce qui entraînait des avertissements ou des erreurs dans l’analyse statique lorsque la méthode était utilisée dans des instructions conditionnelles.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38485>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38439>
* _AC-11651_ : Magento tentant de modifier la propriété en lecture seule dans la méthode __wakeup de LoggerProxy
   * _Remarque de correctif_ : le système permet désormais de modifier des propriétés précédemment en lecture seule dans la méthode de réveil __LoggerProxy, assurant un fonctionnement fluide sans obliger les utilisateurs à utiliser une solution de contournement. Auparavant, une tentative de réattribution de la valeur d’une propriété en lecture seule dans la méthode __wakeup de LoggerProxy provoquait des problèmes.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38526>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-11673_ :
   * _Note de correctif_ : recherchez les dernières versions de php-amqplib/php-amqplib
   * _Problème GitHub_ : &lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _Contribution du code GitHub_ : mise à jour de la dernière version php-amqplib/php-amqplib :^3.x
* _AC-11681_ : [Problème] AC-2039 AC-1667 Références TinyMCE de mise à niveau
   * _Note de correctif_ : mise à jour de la version la plus récente de tinymce dans composer.json
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38533>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/36543>, <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-11696_ : ChangelogBatchWalker ne fonctionne pas dans plusieurs threads
   * _Remarque de correctif_ : le système prend désormais en charge le branchement de processus pour l’indexation MView, ce qui empêche les erreurs lors de l’exécution de l’indexeur lors du fonctionnement sur plusieurs threads. Auparavant, l’exécution de ChangelogBatchWalker sur plusieurs threads entraînait la suppression des tables utilisées par d’autres threads, provoquant une erreur lors de l’exécution de l’indexeur.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38246>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38248>
* _AC-11781_ : [Problème] Changement du nom de variable incorrect
   * _Remarque de correctif_ : le système nomme désormais correctement la variable qui contient le montant d’argent qui peut encore être remboursé, ce qui évite toute confusion pendant le débogage. Auparavant, cette variable était incorrectement nommée totalRefund, ce qui pouvait entraîner des incompréhensions pour les développeurs.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38609>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/36205>
* _AC-11808_ :
   * _Note de correctif_ : recherchez et mettez à niveau la liste des dépendances Adobe Commerce Core
   * _Contribution du code GitHub_ : mise à niveau de la liste des dépendances principales Adobe Commerce 
* _AC-11819_ : le cache FPC intégré est rompu dans 2.4.7 pour certaines configurations
   * _Remarque : le système met désormais correctement en cache les pages lorsque le paramètre MAGE_RUN_CODE est défini, assurant ainsi des performances optimales._ Auparavant, les pages n’étaient pas mises en cache dans ces conditions, ce qui pouvait entraîner des problèmes de performances.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38626>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38646>, <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-11829_ : [Problème] Correction d’une incohérence de la gestion des exceptions entre les modes de développement et de production
   * _Remarque :_ : le système gère désormais de manière cohérente les exceptions entre les modes Développeur et Production, ce qui empêche une redirection inattendue vers la page de connexion lorsqu’une exception est générée. Auparavant, une incohérence dans la gestion des exceptions pouvait entraîner une redirection vers la page de connexion en mode de production au lieu d’afficher le message d’exception.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38639>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37712>
* _AC-11852_ : remplacez la traduction &#39;Compte PayPal&#39; dans token_list.phtml
   * _Remarque :_ : le système attribue désormais à la section les méthodes de paiement de compte jetable &quot;Compte&quot; au lieu de &quot;Compte PayPal&quot; dans la page des méthodes de paiement stockées, ce qui la rend plus représentative de sa fonction. Auparavant, cette section était spécifiquement étiquetée &quot;Compte PayPal&quot;, ce qui induisait en erreur lorsque d’autres méthodes de paiement de compte jetables étaient ajoutées.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/35622>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37959>
* _AC-11905_ : [Problème] Déploiement de contenu statique - Erreur de type
   * _Remarque de correctif_ : le système gère désormais correctement les fichiers LESS vides lors du déploiement de contenu statique, en affichant un message d’erreur &quot;Le fichier LESS est vide&quot;. Auparavant, une erreur de type incorrecte était générée lors de la rencontre d’un fichier LESS vide lors du déploiement.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38682>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38683>
* _AC-11911_ :
   * _Remarque de correctif_ : nettoyage CSS de jQuery/fileuploader après la migration vers la bibliothèque de modification
   * _Problème GitHub_ : &lt;<https://github.com/magento/magento2/commit/7cabfb46>>
   * _Contribution du code GitHub_ : suppression de la bibliothèque jQuery/fileUploader car elle a été migrée vers la bibliothèque Uppy.
* _AC-12002_ : [Problème] [Affichage] Suppression de l’espace supplémentaire dans la balise de lien et de script
   * _Remarque : le système s’assure désormais qu’il n’y a pas d’espaces supplémentaires dans les balises de lien et de script, ce qui fournit un code plus propre et plus efficace._ Auparavant, il était possible de trouver deux espaces entre les attributs dans les balises de lien et de script.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/32920>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/32919>
* _AC-12015_ :
   * _Remarque : correction_ : nettoyage du dossier ExtJs après la migration vers la bibliothèque jsTree
   * _Problème GitHub_ : &lt;<https://github.com/magento/magento2/commit/7cabfb46>>
   * _Contribution du code GitHub_ : suppression du dossier extJs car la fonctionnalité associée a été migrée vers jsTree
* _AC-12022_ :
   * _Remarque : effectuez la mise à niveau de la dépendance système monolog/monolog vers la dernière version majeure._
   * _Problème GitHub_ : &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _Contribution du code GitHub_ : le système a été mis à jour pour utiliser la dernière version majeure de la bibliothèque &quot;monolog/monolog:^3.x&quot;, assurant ainsi la compatibilité et de meilleures performances. Auparavant, le système utilisait une version obsolète de la bibliothèque &quot;monolog/monolog&quot;, ce qui aurait pu entraîner des problèmes et des limitations potentiels.
* _AC-12023_ :
   * _Remarque : Mettez à niveau wikimedia/less.php la dépendance vers la dernière version majeure_
   * _Problème GitHub_ : &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _Contribution du code GitHub_ : le système a été mis à jour afin d’utiliser la dernière version majeure 5.x de la bibliothèque &quot;wikimedia/less.php&quot;, assurant ainsi la compatibilité et des fonctionnalités à jour. Auparavant, le système utilisait une version obsolète de la bibliothèque, ce qui pouvait entraîner des problèmes de sécurité.
* _AC-12024_ :
   * _Remarque : Mettez à niveau la dépendance de bibliothèque jquery/validate vers la dernière version mineure._
   * _Problème GitHub_ : &lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _Contribution du code GitHub_ : mise à niveau de la dépendance de bibliothèque jquery/validate vers la dernière version mineure 1.20.0
* _AC-12025_ :
   * _Remarque : effectuez la mise à niveau de la dépendance du système moment.js vers la dernière version mineure._
   * _Problème GitHub_ : &lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _Contribution du code GitHub_ : mettez à niveau la dépendance du système moment.js vers la dernière version mineure 2.30.1
* _AC-12267_ :
   * __ : prend en charge les reprises de connexion pour la session Redis et compatibles avec colinmollenhour/php-redis-session-abstract v2.0.0
   * _Problème GitHub_ : &lt;<https://github.com/magento/magento2/commit/672a2e61>>
   * _Contribution du code GitHub_ : mise à jour de la dernière version de colinmollenhour/php-redis-session-abstract v2.0.0 compatible avec adobe commerce
* _AC-12268_ :
   * _Remarque de correctif_ : mettez à niveau les dépendances du compositeur de catégorie/système de vol vers la dernière version
   * _Contribution du code GitHub_ : mettez à niveau les dépendances de la ligue 2.x/du compositeur de système de vol vers la dernière version 3.x
* _AC-12594_ : [Problème] Utilisez la configuration compilée pour les données générées au lieu de la configuration générale
   * _Remarque :_ : le système utilise désormais la configuration compilée pour les données générées au lieu de la configuration générale, ce qui réduit le transfert réseau et la surcharge de données qui dépend d’une certaine version du code. Cette modification empêche le remplacement du cache dans les instances partagées lors de la permutation de conteneur, ce qui améliore la stabilité et réduit les temps d’arrêt. Auparavant, certaines classes principales utilisaient le type de configuration partagé, ce qui pouvait entraîner le remplacement du cache ou des temps d’arrêt de l’application en raison de différences de versions du code sur plusieurs serveurs.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38785>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/29954>
* _AC-12597_ : [Problème] Supprimez les références aux fichiers des fichiers extjs qui ont été supprimés dans e1cdb...
   * _Remarque de correctif_ : le système supprime désormais les références aux fichiers d’extensions qui ont été supprimés précédemment, ce qui élimine les erreurs dans la console du navigateur et dans le fichier journal du système. Auparavant, ces références provoquaient des erreurs en raison de l’absence des fichiers référencés.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38960>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38951>
* _AC-12715_ :
   * _: Mettre à jour les dépendances des compositeurs laminas à niveau vers la dernière version_
   * _Problème GitHub_ : &lt;<https://github.com/magento/magento2/commit/b34c0a75>>
   * _Contribution du code GitHub_ : le système prend désormais en charge les dernières versions des dépendances des compositeurs laminas :
laminas/laminas-servicemanager
laminas/laminas-server
laminas/laminas-stdlib
laminas/laminas-validator
assurer la compatibilité et les fonctionnalités à jour. Auparavant, la mise à jour vers les dernières versions de ces dépendances pouvait entraîner des problèmes d’incompatibilité ascendante et des échecs de test.
* _AC-12778_ : [Problème] Nettoyage mineur : correction d’une mauvaise utilisation du sprintf, il ne prend que 2 espaces réservés ici et w...
   * _Remarque de correctif_ : le système utilise désormais correctement la fonction sprintf avec le nombre approprié d’espaces réservés, ce qui améliore la propreté et la cohérence du code. Auparavant, la fonction sprintf était utilisée de manière incorrecte avec un argument supplémentaire, ce qui n’entraînait aucun problème majeur, mais n’était pas l’utilisation correcte.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39062>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38628>
* _AC-12866_ :
   * _Remarque : Supprimez les obsolescences- Tests d’intégration PhpUnit10_
   * _Problème GitHub_ : &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _Contribution du code GitHub_ : résolution des obsolescences de PHPUnit
* _AC-12868_ :
   * _Remarque de correctif_ : Suppression des obsolescences - Tests WebApi PhpUnit10
   * _Problème GitHub_ : &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _Contribution du code GitHub_ : résolution des obsolescences de PHPUnit
* _AC-12869_ : [Problème] Correction des classes incorrectes référencées dans les modules de Magento.
   * _Remarque : le système référence désormais correctement les classes dans les modules, ce qui garantit un fonctionnement plus fluide et évite les blocages en raison de classes non existantes._ Cela inclut un correctif dans les modules Indexer et Creditmemo et l’implémentation de HttpGetActionInterface dans la classe PrintAction. Auparavant, des références de classe incorrectes entraînaient des erreurs et des blocages système potentiels, et certaines fonctionnalités, telles que le nom de fichier des fichiers du PDF de crédit et la réindexation des stocks, ne fonctionnaient pas comme prévu.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39126>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37784>
* _AC-6754_ : erreur de typo sur un fichier js.
   * _Remarque :_ : le système utilise désormais correctement le terme &quot;abonnés&quot; dans le fichier JavaScript, assurant le bon fonctionnement des fonctionnalités associées. Auparavant, une erreur typographique du fichier JavaScript entraînait une utilisation incorrecte du terme &quot;subsctibers&quot;.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/36163>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/36171>
* _AC-8353_ : [Problème] Supprimer la balise `@author` interdite
   * _Remarque de correctif_ : le système respecte désormais les normes de codage en supprimant la balise `@author` interdite de certains modules, en assurant un code plus propre et plus normalisé. Auparavant, la balise `@author` était présente dans certains modules, ce qui était contraire aux normes de codage établies.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37253>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37003>
* _AC-8356_ : [Problème] Supprimer la balise `@author` interdite de `Magento_Customer` (partie 2)
   * _Remarque de correctif_ : le système respecte désormais la norme de codage en supprimant la balise `@author` interdite de certains modules, en assurant un code plus propre et plus normalisé. Auparavant, la balise `@author` était présente dans certains modules, ce qui était contraire aux normes de codage établies.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37250>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37000>
* _AC-8659_ : l’espace dans la syntaxe editorconfig rompt la règle pour [{compositeur,auth}.json]
   * _Remarque de correctif_ : le système applique désormais correctement un retrait de 4 espaces aux fichiers compositeur et auth.json, suite à un correctif d’une erreur de syntaxe dans l’editorconfig. Auparavant, en raison d’un espace dans la syntaxe editorconfig, ces fichiers étaient mal formatés avec un retrait de 2 espaces.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37394>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37395>
* _AC-8984_ : [Problème] Ajoute des couleurs supplémentaires à la sortie de certaines commandes de configuration cli
   * _Remarque de correctif_ : le système ajoute désormais plus de couleurs à la sortie de certaines commandes de ligne de commande de configuration, ce qui améliore la lisibilité et l’expérience utilisateur. Auparavant, la sortie de ces commandes était plus difficile à lire en raison de l’absence de différenciation des couleurs.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/29335>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/29298>
* _AC-9630_ : la mise à niveau du Magento réinitialise general/region/state_required lorsque le nouveau pays avec l’état/la région requis est ajouté.
   * _Remarque de correctif_ : le système ajoute désormais uniquement le pays modifié à la configuration &quot;general/region/state_required&quot; lorsqu’un nouveau pays avec les états requis est ajouté, ce qui empêche toute interruption du code personnalisé qui suppose que la région est désactivée. Auparavant, l’ajout d’un nouveau pays avec les états requis réinitialisait la configuration &quot;general/region/state_required&quot; sur les pays par défaut avec un état requis, ce qui risquait de rompre la boutique.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37796>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38076>
* _AC-9712_ : Différence en moins de compilation entre la bibliothèque php et nodejs (grunt) avec des expressions `calc` compliquées
   * _Note de correctif_ : corrigez la différence de compilation moindre entre la bibliothèque php et nodejs (grunt) après la mise à jour wikimedia/less.php:^5.x
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37841>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b34c0a75>
* _ACP2E-2692_ : l&#39;erreur &quot;Table ou vue de base introuvable&quot; se produit lors de l&#39;exécution de l&#39;indexation partielle
   * _Remarque de correctif_ : La réindexation partielle fonctionne désormais correctement avec les grands fichiers de modification en cas de connexion à la base de données secondaire.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2844_ : problèmes après la mise à niveau de MariaDB vers la version 10.5.1 ou ultérieure
   * _Remarque de correctif_ : correction d’un problème en raison duquel les valeurs datetime d’une base de données étaient converties en 0000-00-00 00:00:00 après la mise à niveau de Mysql.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2855_ : type Discordance dans la comparaison des données lors de la vérification de la modification des données
   * _Remarque :_ : auparavant, l’objet d’enregistrement était appelé à chaque fois sans modification de données (pour tout champ de données numérique, comme int/float/double). Elle déclenche l’indicateur _hasDataChanges sur true et appelle la fonction save . Une fois ce correctif appliqué, la fonction save n’appelle que si les données sont modifiées. La valeur de données pour int/float/double-check avec la valeur transmettant à la fonction et effectue une correspondance de type stricte.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2959_ : l’importation [Cloud] ne peut pas être utilisée avec la variable de répertoire
   * _Remarque sur les correctifs_ : le produit peut être importé avec succès quel que soit le nom de fichier.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2966_ : dans ipad mini, le menu et l’en-tête se chargent comme mobile, mais ils doivent se charger comme bureau.
   * _Remarque : le système traite désormais les périphériques d’une largeur de 768 pixels comme des ordinateurs de bureau, en s’assurant que le menu et l’en-tête se chargent correctement._ Auparavant, les appareils dont la largeur était de 768 px étaient traités comme mobiles, ce qui entraînait le chargement du menu et de l’en-tête dans une vue mobile.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/35b1b1da>, <https://github.com/magento/magento2-page-builder/commit/4d5db10a>

### Structure, GraphQL

* _AC-7976_ : [Problème] Prise en charge des types scalaires personnalisés pour le schéma GraphQL
   * _Remarque : le système prend désormais en charge les types scalaires personnalisés pour les schémas GraphQL, ce qui permet aux développeurs de définir des types scalaires et des implémentations personnalisés._ Cette fonctionnalité peut s’avérer particulièrement utile pour exprimer des valeurs qui peuvent nécessiter une validation, telles que l’HTML, les emails, les URL, les dates, etc., et pour des cas plus avancés tels que les attributs de valeur ajoutée (EAV). Auparavant, le système ne prenait pas en charge le traitement des types scalaires personnalisés dans GraphQL.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/36877>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/34651>, <https://github.com/magento/magento2/commit/0574ac23>

### GraphQL

* _AC-11729_ : Magento_GraphQl exécute le traitement des en-têtes même si la valeur d’en-tête ne passe pas la validation
   * _Remarque de correctif_ : le système s’assure désormais que le traitement des en-têtes n’est exécuté qu’une seule fois et uniquement si la valeur d’en-tête est validée, ce qui renforce la sécurité et évite des vulnérabilités potentielles. Auparavant, le traitement de l’en-tête était exécuté même si la valeur de l’en-tête n’était pas validée, ce qui entraînait des vulnérabilités potentielles et un comportement inattendu en raison du double traitement des valeurs d’en-tête.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-8951_ : les options de carte-cadeau physique n’ont pas l’ordre de tri correct
   * _Remarque :_ : le système trie désormais correctement les options des produits de carte-cadeau physiques lorsqu’ils sont interrogés via GraphQL, en assurant un rendu cohérent avec le thème Luma. Auparavant, l’ordre de tri était incorrect en fonction du thème luma, ce qui entraînait un affichage et un ordre incorrects des options telles que le nom de l’expéditeur, le nom du destinataire et le montant.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1bafc571>
* _AC-9157_ : [GraphQL] Le cache de résolveur est invalidé lors de la création/modification/déplacement/suppression d’une mise à jour intermédiaire
   * _Remarque de correctif_ : le système s’assure désormais que le cache du programme de résolution n’est pas invalidé lors de la création, de la modification, du déplacement ou de la suppression d’une mise à jour d’évaluation, mais uniquement lorsque la mise à jour d’évaluation est appliquée à l’entité. Auparavant, le cache du programme de résolution était invalidé prématurément, même avant l’application de la mise à jour intermédiaire, ce qui entraînait des invalidations inutiles du cache.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2642_ : mise en cache rapide non effacée pour la mise à jour de l’évaluation du contenu
   * _Remarque : Désormais, le cache de réponse du contenu GraphQL avec PageBuilder est invalidé lorsque les entités liées au contenu PageBuilder sont mises à jour._
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2653_ : désactivation de la navigation par couches - Ne supprime pas l’agrégation de Graphql
   * _Remarque : correction_ : le problème a été corrigé après l’application de la vérification lors de la demande d’une recherche de produits avec des agrégations de catégories par le biais d’une requête GraphQL lorsque le paramètre de configuration de l’administrateur de &quot;Catalogue > Navigation en couches > Filtre de catégorie d’affichage&quot;.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2928_ : l’appel de produits GraphQL contenant le filtre de prix {from:&quot;0&quot;} ne renvoie aucun résultat
   * _Remarque : Auparavant, la recherche de produits graphql avec un filtre de prix nul ne renvoyait aucun résultat en raison d’une exception générée._ Désormais, la recherche renvoie les résultats comme prévu.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-3128_ : [Cloud] Appel GraphQL endommagé pour getPurchaseOrder avec guillemet de noeud
   * _Remarque : L’appel GraphQL du bon de commande pourra exécuter la tâche sans rencontrer d’erreurs au niveau du serveur interne._
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3184_ : [Cloud] Produits configurables non affichés dans le site de production si le produit n’est pas activé dans &quot;Toutes les consultations de magasin&quot;
   * _Remarque : le système affiche désormais correctement les produits configurables sur le site même si le produit n’est pas activé dans &quot;Toutes les vues de magasin&quot;, mais est activé dans des portées d’affichage de magasin spécifiques._
Auparavant, si un produit était désactivé dans &quot;Toutes les vues de magasin&quot; et activé uniquement dans des portées d’affichage de magasin spécifiques, les attributs de produit ne s’affichaient pas correctement dans la réponse GraphQL, ce qui entraînait un affichage incorrect du produit.
   * _Contribution du code GitHub_ : <https://github.com/magento/inventory/commit/3f300077>
* _ACP2E-3190_ : [Cloud] Produits graphql ayant une erreur lorsqu’un même produit simple a affecté plusieurs produits configurables
   * _Remarque de correctif_ : auparavant, avec des produits configurables distincts avec le même produit simple, GraphQL renvoie une erreur. Une fois ce correctif appliqué, différents produits configurables avec le même produit simple, le graphiqueQL renvoie le résultat sans erreur.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3253_ : la pagination des éléments de panier GraphQL V2 ne fonctionne pas correctement
   * _Remarque : correction_ : le problème a été corrigé en transmettant la valeur correcte de l’argument de page en cours dans la requête de collection. Auparavant, la mauvaise valeur était transmise pour définir la page active, ce qui provoquait le problème.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/8459b17d>

### GraphQL, Inventaire/MSI

* _ACP2E-2607_ : la mutation MergeCart renvoie une exception lorsque les paniers source et de destination ont les mêmes éléments de lot
   * _Note de correctif_ : &#39;-
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c971859e>, <https://github.com/magento/inventory/commit/db0620da>

### GraphQL, Inventaire/MSI, Performances

* _ACP2E-1716_ : Site d&#39;arrêt après mise à niveau
   * _Remarque de correctif_ : les performances de récupération des produits de bundle via GraphQl sont améliorées.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ba25af8a>, <https://github.com/magento/inventory/commit/bdbf97ea>

### GraphQL, performances

* _AC-9569_ : [Résolveur GraphQL] Les données du résolveur client ne sont pas invalidées à partir de l’importation
   * _Remarque : le cache du résolveur client GraphQL est désormais invalidé comme prévu lorsqu’un client est modifié ou supprimé par le biais d’importations._ Auparavant, le cache n’était pas invalidé et les données client pouvaient être modifiées ou supprimées lors de l’importation.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/0574ac23>

### GraphQL, Recherche

* _ACP2E-2809_ : le tri des listes de produits GraphQL par plusieurs paramètres ne fonctionne pas
   * _Remarque : correction_ : le tri des produits par plusieurs champs dans GraphQl fonctionne désormais comme décrit dans la documentation.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c971859e>

### Importer/exporter

* _AC-12172_ : problème lors de l’importation d’un produit lorsqu’il est fourni avec options-type personnalisé : fichier (le produit créé ne contient pas de prix pour l’option personnalisée et n’affiche que la première extension de type de fichier fournie)
   * _Remarque : le système importe désormais correctement les données de produit avec des options personnalisées de type &quot;fichier&quot;, en s’assurant que toutes les extensions de fichier fournies sont affichées et que le prix de l’option personnalisée est inclus._ Auparavant, lors de l’importation du produit, si une option personnalisée de type &quot;fichier&quot; était fournie avec plusieurs extensions de fichier, seule la première extension était affichée et le prix de l’option personnalisée était manquant.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38805>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38926>
* _ACP2E-2710_ : temps d’exécution incorrect pour une opération d’importation dans la grille Import History
   * _Remarque : le temps d’exécution des rapports d’importation s’affiche correctement indépendamment du paramètre régional d’administration._
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2737_ : clients dupliqués en cours de création avec la même adresse email à l’aide de l’importation
   * _Remarque : correction_ : l’importation du client lors du partage de compte défini sur Global, le client importé existant dans le système est mise à jour.
Le client précédemment importé a été dupliqué.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2902_ : ajout/mise à jour de l’importation sur les produits Duplication des options personnalisables
   * _Remarque : correction_ : le problème a été résolu en attribuant les options de magasin correctes aux options de produit lors de l’importation des options de produit au format CSV.
Auparavant, affecté à la boutique d’administrateurs au lieu de leur boutique respective.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2990_ : client &quot;created_at&quot; date Non converti pour stocker le fuseau horaire lors de l’exportation
   * _Remarque : correction_ : une valeur de date &quot;created_at&quot; de colonne est convertie au format de date approprié en fonction du fuseau horaire de stockage dans la section CSV d’exportation client.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3165_ : [Cloud] Obtention d’une erreur lors de la vérification des données dans les données d’importation au moyen de CSV
   * _Remarque : correction_ : il n’y a aucune erreur lors de la vérification des données lors de l’importation CSV. Auparavant, le message d’erreur s’affichait : &quot;Nous ne trouvons pas de client correspondant à cet email et à ce code de site web dans la ou les lignes : 1&quot; lors de la vérification des données de la section d’importation à l’aide du fichier CSV de l’administrateur.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/8459b17d>

### Installation et administration

* _ACP2E-2102_ : bouton No Export VCL for Varnish 7 dans le panneau d’administration
   * _Remarque : correction_ : le bouton &quot;Export VCL pour vernis 7&quot; a été ajouté au panneau d’administration.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a4fbf702>

### Inventaire/MSI

* _AC-11593_ : La clé de l’API Google Google ne fonctionne pas lors de l’ajout d’une carte avec des attributs
   * _Remarque :_ : le système prend désormais en charge la dernière version de l’API Google Maps version 3.56, ce qui permet aux utilisateurs d’ajouter un bloc de contenu Map depuis le menu PageBuilder vers l’étape sans rencontrer d’erreur. Auparavant, les utilisateurs ne pouvaient pas ajouter de bloc de contenu Map en raison de problèmes de compatibilité avec la version de l’API Google Maps, ce qui entraînait l’affichage d’un message d’erreur &quot;Une erreur s’est produite&quot;.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/0574ac23>
* _ACP2E-2794_ : [Cloud] Problème critique avec liste de produits avec espaces vides
   * _Remarque :_ : le système affiche désormais correctement les listes de produits sans espaces vides lorsque les produits sont définis sur &quot;En rupture de stock&quot;, assurant ainsi un affichage cohérent et précis des produits disponibles. Auparavant, la définition d’un produit sur &quot;En rupture de stock&quot; entraînait l’affichage d’un espace vide dans la liste de produits, ce qui perturbait la mise en page et pouvait dérouter les clients.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ea79f7dd>, <https://github.com/magento/inventory/commit/b59e48ca>

### Commande

* _AC-10828_ : Écran d’aperçu de l’ordre du serveur principal : quantité en ordre inverse non visible au niveau de l’élément de commande
   * _Remarque : correction_ : le système affiche désormais le nombre d’éléments en arrière-plan dans la colonne Quantité de l’écran de présentation de la commande principale. Cela permet aux utilisateurs de suivre précisément l’état de tous les éléments d’une commande. Auparavant, la colonne de quantité affichait uniquement le nombre d’articles commandés, facturés et expédiés, mais n’affichait pas le nombre d’articles en backordered.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38252>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38320>
* _AC-10994_ : [Problème] Identifiant de magasin incorrect utilisé dans le moteur de rendu d’adresse de commande
   * _Remarque : Le système utilise désormais correctement l’identifiant de magasin associé à une commande lors du rendu de l’adresse de commande, en s’assurant que les adresses sont correctement formatées en fonction de leur identifiant de magasin respectif._ Auparavant, le système utilisait incorrectement l’identifiant de magasin actuel, ce qui pouvait entraîner une mise en forme incorrecte des adresses dans les cas où plusieurs emails de commande de différents magasins devaient être envoyés.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38412>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37932>
* _AC-11798_ : [Problème] Prix d’expédition affichant différents dans pdf imprimé
   * _Remarque :_ : le système affiche désormais correctement les prix d’expédition dans les PDF imprimés en fonction des paramètres de configuration de la taxe, assurant ainsi la cohérence entre la page d’affichage des factures de commande client et la facture imprimée. Auparavant, le prix de livraison affiché dans le PDF imprimé excluait la taxe, quels que soient les paramètres de configuration de la taxe.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38608>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38595>, <https://github.com/magento/magento2/commit/1bafc571>
* _ACP2E-2622_ : impossible d’enregistrer les modifications apportées au numéro de téléphone dans les détails de commande existants
   * _Remarque : correction_ : l’utilisateur peut désormais ajouter le préfixe international 00 dans le champ de l’adresse de commande
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38201>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2734_ : l&#39;envoi des emails échoue
   * _Remarque : le système comprend désormais une option de configuration async_sending_tries permettant de spécifier le nombre de tentatives d’envoi d’un email avant son arrêt, ce qui améliore la gestion des échecs d’envoi d’emails lorsque l’option &quot;Envoi asynchrone&quot; est activée._ Auparavant, si l’envoi d’un email échouait, le système tentait de le renvoyer en continu, ce qui entraînait une boucle infinie de messages d’erreur dans le journal système.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2756_ : [Cloud] État de la commande modifié en état de réalisation lors du remboursement partiel d’une commande partiellement expédiée
   * _Remarque :_ : lors de l’émission d’une note de crédit, l’état de la commande n’est plus &quot;terminé&quot; si des articles n’ont pas encore été expédiés.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-3002_ : [CLOUD] Impossible de désactiver l’envoi d’emails à partir de l’interface utilisateur d’administration comme le montrent les documents de développement
   * _Remarque : le système empêche désormais correctement l’envoi des emails de vente lorsque la communication par e-mail est désactivée._ Ces emails ne seront plus envoyés lorsque la communication par email sera réactivée. Auparavant, les courriers électroniques de vente démarrés alors que la communication par courrier électronique était désactivée étaient toujours envoyés une fois la communication par courrier électronique réactivée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-3045_ : commande clôturée sans remboursement complet
   * _Remarque_ : le système conserve désormais correctement l’état de la commande en &quot;Traitement&quot; et l’état de la facture en &quot;En attente&quot; lorsqu’une commande avec un paiement non capturé est créée pour une expédition. Ainsi, les commandes ne sont marquées que comme &quot;Fermées&quot; après avoir été entièrement remboursées. Auparavant, la création d’une expédition pour une commande avec une facture en attente changeait incorrectement le statut de la commande en &quot;Fermé&quot;.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/6a185204>

### Ordre, Renvoie

* _ACP2E-2982_ : le remboursement de la commande entraîne la duplication de l&#39;avoir
   * _Remarque : L’émission du remboursement sur l’API REST lorsque deux demandes identiques ont été exécutées simultanément ne crée plus de mémos de crédit en double._
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a4fbf702>

### Commande, Taxe

* _ACP2E-3003_ : [CLOUD] : base_row_total incorrect dans l’API de commande RESTFUL lors de l’activation de transactions transfrontalières et de l’application de remises sur les coupons
   * _Remarque : correction_ : la valeur base_row_total correcte est désormais renvoyée à partir de l’API de commande RESTFUL lorsque la transaction transfrontalière est activée et que la remise de coupon est appliquée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/9af794a4>

### Autres outils de développement

* _AC-10658_ : [Problème] Correction d’une erreur de syntaxe d’HTML dans Visual.phtml
   * _Remarque de correctif_ : le système ferme désormais correctement la balise de début dans le fichier visuel.phtml, en assurant une syntaxe d’HTML correcte. Auparavant, la balise de début n’était pas fermée correctement, ce qui provoquait une erreur de syntaxe d’HTML.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38247>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37457>
* _AC-11474_ : [Problème] Changement de &quot;actif&quot; en &quot;activé&quot; dans maintenance bin/magento:commande status
   * _Remarque de correctif_ : le système fournit désormais des messages d’état plus précis pour la commande du mode de maintenance, en passant de l’état &quot;actif&quot; à &quot;activé&quot; et de &quot;non actif&quot; à &quot;désactivé&quot;. Auparavant, le message d’état de la commande du mode de maintenance était affiché comme &quot;actif&quot; ou &quot;non actif&quot;, ce qui pouvait prêter à confusion.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38486>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38410>
* _AC-12571_ : la navigation dans l’arborescence des catégories entraîne des erreurs dans les redis : &quot;La session des redis a dépassé les connexions simultanées&quot;
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38851>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/0611e750>

### Paiements

* _ACP2E-2841_ : le flux de paiement crée une transaction chaque fois que nous cliquons sur le bouton de récupération sur l’écran d’affichage des transactions
   * _Remarque : le système récupère désormais correctement les informations de transaction sans créer de transaction de paiement à chaque clic sur le bouton de récupération dans l’écran d’affichage des transactions._ Auparavant, le fait de cliquer sur le bouton Récupérer créait incorrectement une nouvelle transaction de paiement pour une commande déjà payée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3028_ : message Paylater ne s’affichant pas dans PDP pour le compte marchand paypal canadien
   * _Remarque :_ : le système affiche désormais correctement le message PayLater pour les comptes marchands canadiens PayPal sur la page Détails du produit (PDP) lorsque le pays de l’acheteur peut être déterminé à partir de l’adresse de facturation ou de l’envoi du compte. Auparavant, le message PayLater ne s’affichait pas en raison d’un paramètre manquant, ce qui entraînait une erreur dans la console du navigateur.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/6a185204>

### Performances

* _AC-12000_ : [Problème] Nettoyage du code et ajout d’un nouveau bloc de tête critique et déplacement du CSS critique avant les ressources
   * _Remarque :_ : le système comprend désormais un nouveau bloc de tête critique et déplace le CSS critique avant les ressources, ce qui permet une personnalisation et une optimisation des performances accrues dans le front-end. Auparavant, le CSS critique n’était pas positionné avant les ressources, ce qui limitait les opportunités de personnalisation et d’optimisation.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38748>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/35580>
* _AC-12176_ : la compilation des thèmes se interrompt lorsque l’hôte mysql contient des informations sur le port
   * _Remarque de correctif_ : le système gère désormais correctement la configuration de l’hôte MySQL qui inclut les informations de port, ce qui garantit la compilation des thèmes réussie. Auparavant, la compilation des thèmes échouait si la configuration de l’hôte MySQL dans la connexion à la base de données incluait des informations de port.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38799>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38842>
* _ACP2E-2494_ : problème de performance lors du chargement des attributs de produit dans les règles de panier
   * _Remarque :_ : amélioration des performances des requêtes pour les règles de vente - de 150 ms environ à un seul chiffre ms.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2673_ : performance d&#39;indexation partielle des prix
   * _Remarque de correctif_ : les performances d’indexation partielle du prix ont été améliorées en optimisant certaines des requêtes de suppression utilisées dans le processus d’indexation.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2850_ : la commande est refusée lors de la configuration multi-magasin lors de l’utilisation du traitement d’ordre asynchrone + termes et conditions
   * _Remarque : les commandes effectuées à partir de sites web autres que les sites web par défaut avec conditions et conditions activées sont désormais traitées._
Avant d’être automatiquement rejetés.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2910_ : l’appel de l’API de repos de la commande prend beaucoup de temps à s’exécuter
   * _Remarque : le système exécute désormais l’appel de l’API Order Rest dans un délai raisonnable, ce qui améliore les performances lors de la récupération d’un grand nombre de commandes._ Auparavant, l’exécution de l’appel de l’API Order Rest prenait beaucoup de temps, ce qui entraînait des retards lors de la récupération d’un grand nombre de commandes.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/001e5188>

### Produit

* _AC-10535_ : des caractères spéciaux dans le nom de produit associé configurable sont convertis en entités d’HTML.
   * _Remarque :_ : le système conserve désormais correctement les caractères spéciaux dans les noms des produits associés lors de la modification d’un produit configurable, ce qui empêche leur conversion en entités HTMLS. Auparavant, les caractères spéciaux des noms de produits associés étaient convertis en entités d’HTML lors de la modification du produit configurable.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38146>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38447>
* _AC-10947_ : La fonction ProductRepository GetById ne crée pas la clé de cache correcte
   * _Remarque de correctif_ : le système crée désormais correctement une clé de cache dans la fonction GetById du référentiel de produit, que l’ID de magasin soit transmis sous la forme d’une chaîne ou d’un entier. Cela permet de s’assurer que le produit est récupéré de la mémoire lors des appels suivants, ce qui améliore les performances. Auparavant, le système récupérait le produit de la base de données chaque fois que la fonction était appelée, même avec les mêmes paramètres, en raison d’une création de clé de cache incorrecte.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38384>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38433>
* _AC-11992_ : [Problème] [MFTF] Ajout d’AdminClickAddOptionForBundleItemsActionGroup
   * _Remarque : Le système comprend désormais le module AdminClickAddOptionForBundleItemsActionGroup, ce qui améliore les fonctionnalités du panneau d’administration._ Auparavant, ce groupe d’actions n’était pas disponible.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/30857>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/30838>
* _AC-5969_ : AlertProcessor - Argument #2 ($storeId) doit être de type int, chaîne donnée
   * _Remarque : le système déclenche désormais correctement les emails d’alerte de produit en s’assurant que l’identifiant de magasin est du type de données correct._ Auparavant, les e-mails d’alerte de produit n’étaient pas envoyés en raison d’une incohérence de type dans l’identifiant de magasin.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/35602>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/0574ac23>
* _ACP2E-2944_ : la fonction [Cloud] addFilterToMap ne fonctionne pas pour certaines colonnes
   * _Remarque de correctif_ : le module personnalisé peut désormais être utilisé dans la grille de commande. Des erreurs précédentes se produisaient lors de l’utilisation d’un module personnalisé.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/3a7c4d17>

### Promotion

* _ACP2E-2602_ : attribut du client non visible lors de la création d’un compte à partir d’une invitation
   * _Remarque : les attributs du client sont disponibles lors de la création d’un compte à partir d’une invitation._
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2627_ : le code coupon avec la limite d&#39;utilisateurs par coupon n&#39;est pas libéré pour paiement en échec avec l&#39;annulation de la commande
   * _Remarque : le système met désormais immédiatement à jour les utilisations de coupon lorsqu’une commande est créée ou annulée et ajoute des utilisations de règle à une file d’attente pour éviter tout blocage potentiel._ Ainsi, un code de bon avec une limite &quot;Utilisateurs par coupon&quot; est libéré et peut être réutilisé si une commande est annulée en raison d’un paiement en échec. Auparavant, le système ne publiait pas le code de coupon en vue de le réutiliser, ce qui entraînait l’affichage d’un message d’erreur indiquant que le code de coupon n’était pas valide.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2811_ : [Cloud] La réindexation de l’indexeur de produits de règle de catalogue renvoie SQLSTATE[HY00] : Erreur générale : le serveur MySQL 2006 a disparu.
   * _Remarque de correctif_ : le système gère désormais correctement la valeur &quot;batchCount&quot; personnalisée dans le fichier di.xml pour le &quot;Magento\CatalogRule\Model\Indexer\IndexBuilder&quot;, ce qui empêche des erreurs SQL telles que &quot;Erreur générale : le serveur MySQL 2006 a disparu&quot; lors de la réindexation de l’indexeur de produit de règle de catalogue en raison d’une taille de lot incorrecte sur les catalogues volumineux.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b2286ecf>

### SEO

* _AC-11907_ : l’ajout de réécritures d’URL avec un accent entraîne un chargement infini.
   * _Remarque : le système crée et fonctionne désormais correctement les réécritures d’URL avec des accents, empêchant un chargement infini pendant le processus d’enregistrement._ Auparavant, l’ajout d’une réécriture d’URL avec un accent provoquait un problème de chargement infini.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38692>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/44cef3a9>
* _ACP2E-2641_ : URL de catégorie erronée multi-magasin réécriture pour la catégorie de troisième niveau
   * _Correction de la note_ : génère les réécritures d’URL correctes pour les enfants avec une clé d’URL étendue personnalisée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2770_ : des caractères à deux octets (caractères spéciaux) dans le champ Nom du produit bloquent la création du produit dans le serveur principal
   * _Remarque : correction_ : un nouveau paramètre a été ajouté pour vous permettre d’appliquer ou non la translittération à l’URL du produit. Le paramètre est disponible ici : Magasins > Configuration > Catalogue > Catalogue > Optimisation du moteur de recherche : &quot;Appliquer la translittération à l’URL du produit&quot;
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b2286ecf>

### Sécurité

* _AC-11762_ :
   * _Remarque : correction_ : mettez à jour le champ de fenêtre OTP 2FA avec la description correcte et la valeur par défaut après la modification par BiC
   * _Contribution du code GitHub_ : mise à jour de la commande pour la manière dont la période otp_window sera saisie à partir de maintenant bin/magento config:set twofactorauth/google/otp_window VALUE
dans la configuration bin/magento : définissez la valeur twofactorauth/google/leway
* _AC-11855_ : [Problème] Absente Font CSP Paylater Popup
   * _Remarque de correctif_ : le système permet désormais de charger la police &#39;https://www.paypalobjects.com/webstatic/mktg/2014design/font/PP-Sans/PayPalSansBig-Medium.woff&#39; sans enfreindre la directive de politique de sécurité du contenu, en assurant l’affichage correct de la fenêtre contextuelle Paylater. Auparavant, le chargement de la police était refusé en raison d’une violation de la directive de sécurité du contenu, ce qui entraînait des problèmes d’affichage avec la fenêtre contextuelle Paylater.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38624>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37401>
* _AC-11937_ :
   * _Remarque : correction_ : mettez à jour le champ de fenêtre OTP 2FA avec la description correcte et la valeur par défaut après la modification par BiC
   * _Contribution du code GitHub_ : mise à jour de la commande pour la manière dont la période otp_window sera saisie à partir de maintenant bin/magento config:set twofactorauth/google/otp_window VALUE
dans la configuration bin/magento : définissez la valeur twofactorauth/google/leway
* _AC-12309_ :
   * _Remarque : Mettez à jour la documentation utilisateur pour l’authentification à deux facteurs (2FA) afin de modifier la commande otp_window_
   * _Contribution du code GitHub_ : mettez à jour la documentation utilisateur pour l’authentification à deux facteurs (2FA) afin de modifier la commande des paramètres OTP_WINDOW comme suit : https://jira.corp.adobe.com/browse/AC-11762

### Expédition

* _AC-10757_ : [Problème] Correction d’une faute de frappe dans tracking.phtml - renommé JS-features &quot;currier&quot; en &quot;carrier&quot;
   * _Remarque de correctif_ : le système utilise désormais correctement le terme &quot;carrier&quot; au lieu de &quot;currier&quot; mal orthographié dans les fonctions du gestionnaire JavaScript utilisées dans le modèle de suivi de commande, ce qui garantit un nommage correct des fonctions et une clarté du code. Auparavant, le terme mal orthographié &quot;currier&quot; était utilisé, ce qui pouvait entraîner confusion et incohérence dans le code base.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/34523>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/33414>
* _AC-11811_ :
   * _Remarque_ : UPS REST &quot;Une expédition ne peut pas avoir un KGS/IN ou LBS/CM ou OZS/CM comme unité de mesure&quot;
   * _Problème GitHub_ : &lt;<https://github.com/magento/magento2/commit/9b1713d8>>
   * _Contribution du code GitHub_ : les taux UPS sont visibles dans le passage en caisse et le panier.
* _AC-11916_ :
   * __ : [QPT] UPS REST &quot;Une cargaison ne peut pas avoir un KGS/IN ou LBS/CM ou OZS/CM comme unité de mesure&quot;
   * _Contribution du code GitHub_ : les taux UPS sont visibles dans le passage en caisse et le panier.
* _AC-11938_ : UPS REST &quot;Une cargaison ne peut pas avoir un KGS/IN ou LBS/CM ou OZS/CM comme unité de mesure&quot;
   * _Remarque : assurez-vous que les taux UPS doivent être visibles dans le panier et le passage en caisse._
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38618>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/493e01f5>
* _AC-11983_ :
   * __ : [QPT] UPS REST &quot;Une cargaison ne peut pas avoir un KGS/IN ou LBS/CM ou OZS/CM comme unité de mesure&quot;
   * _Contribution du code GitHub_ : les taux UPS sont visibles dans le passage en caisse et le panier.
* _AC-11984_ :
   * __ : [QPT] UPS REST &quot;Une cargaison ne peut pas avoir un KGS/IN ou LBS/CM ou OZS/CM comme unité de mesure&quot;
   * _Contribution du code GitHub_ : les taux UPS sont visibles dans le passage en caisse et le panier.
* _ACP2E-2738_ : fenêtre de suivi indiquant une date de remise attendue incorrecte
   * _Remarque : correction_ : affiche la date de remise correcte pour l’opérateur Fedex.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2763_ : Les Taux De La Table S’Affichent Toujours Même Si La Livraison Est Libre
   * _Remarque : la méthode d’expédition Taux de la table s’affiche désormais même si l’option Expédition gratuite devient disponible après l’application du coupon._
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2765_ : échec du test MFTF AdminCreatingShippingLabelTest en raison de l’absence d’informations d’identification ajoutées dans l’environnement Jenkins
   * _Note de correctif_ : correctif de test mftf
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ea79f7dd>

### Ciblage

* _AC-9432_ : [Problème] Autoriser l’utilisation de plages CIDR dans la liste autorisée de maintenance
   * _Remarque de correctif_ : le système prend désormais en charge l’utilisation de plages CIDR en mode de maintenance pour autoriser la liste d’adresses IP, ce qui permet à une plage d’adresses IP de contourner le mode de maintenance. Auparavant, le mode de maintenance autorisait uniquement les adresses IP individuelles à contourner le mode de maintenance.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37943>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/30699>

### Framework de test

* _AC-11491_ :
   * _Remarque de correctif_ : [Ignorer] Besoin d’annuler le test d’intégration
   * _Problème GitHub_ : &lt;<https://github.com/magento/magento2/commit/493e01f5>>
   * _Contribution du code GitHub_ : n’ignorez pas tous les tests d’intégration qui sont ignorés dans cette requête de tirage publicitaire - https://github.com/magento-commerce/magento2ce/pull/8811/
* _AC-11654_ : test d’intégration échouant testDbSchemaUpToDate en raison du type de colonne JSON
   * _Remarque_ : le système reconnaît désormais correctement les types de colonnes JSON dans le schéma de base de données lors des tests d’intégration, ce qui empêche les échecs de test en raison d’une incohérence entre le schéma de base de données et le schéma déclaratif. Auparavant, le système identifiait incorrectement les types de colonnes JSON comme LONGTEXT dans MariaDB, ce qui entraînait l’échec des tests d’intégration.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ef81f5a2>

### Interface utilisateur

* _AC-12128_ : correctif de sécurité de Prototype.js CVE-2020-27511
   * _Remarque de correctif_ : le système a été mis à jour pour répondre à la vulnérabilité de sécurité CVE-2020-27511 dans Prototype.js 1.7.3, améliorant ainsi la sécurité globale du système. Avant cette mise à jour, le système était susceptible de subir un refus de service d’expression régulière (ReDOS) par l’élimination de balises d’HTML conçues.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12189_ : Grunt Less utilise pub/prefix pour sourcemaps
   * _Remarque de correctif_ : le système génère désormais des cartes sourcemap less/css sans le préfixe /pub pour les chemins d’accès lors de l’utilisation du graphique, rendant ainsi inutile toute solution de contournement dans la configuration du serveur web. Auparavant, l’utilisation du préfixe /pub dans les chemins d’accès des plans sources nécessitait une configuration spécifique dans le serveur web pour fonctionner correctement.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38837>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38840>
* _AC-1306_ : déploiement de contenu statique pour les modules désactivés
   * _Remarque de correctif_ : le système exclut désormais les CSS relatives aux modules désactivés des fichiers de sortie CSS finaux, en s’assurant que les styles superflus ne sont pas chargés. Auparavant, les feuilles CSS relatives aux modules désactivés étaient incluses dans les fichiers de sortie CSS finaux, ce qui entraînait le chargement de styles supplémentaires inutiles.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/24666>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/32922>
* _AC-9007_ : [Problème] Ne charge pas le contexte du bloc principal sur frontend
   * _Remarque de correctif_ : le système garantit désormais que le contexte de bloc principal n’est pas chargé sur le front-end, ce qui empêche la création de sessions d’arrière-plan inutiles et de verrouillages de session potentiels. Auparavant, le système chargeait incorrectement le contexte du bloc principal sur le front-end, ce qui entraînait la création de sessions d’arrière-plan et de verrous de session potentiels.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37617>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/36368>
* _ACP2E-2529_ : exception lors de la vérification du solde d’une carte-cadeau lorsque Recaptcha est activé
   * _Remarque : les utilisateurs pourront récupérer le solde de leur carte-cadeau dans l’écran d’affichage et de modification du panier._ Auparavant, ces détails n’étaient pas affichés lorsque reCAPTCHA était activé.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2-page-builder/commit/4a2795ea>
* _ACP2E-2729_ : [CLARIFICATION] Demande de fonctionnalité Conformité ADA
   * _Remarque :_ : le système assure désormais la conformité ADA en supprimant les propriétés CSS non prises en charge et en les remplaçant par celles prises en charge dans le fichier print.css. Auparavant, l’utilisation de propriétés CSS non prises en charge entraînait des problèmes de compatibilité des navigateurs.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-3061_ : [Cloud] Code de bibliothèque de confusion dans effective-drop.js de AC 2.4.4-p8
   * _Remarque : le système implémente désormais correctement la bibliothèque result.js, assurant le bon fonctionnement des effets de l’interface utilisateur jQuery._ Auparavant, la bibliothèque effective-drop.js était remplacée par la bibliothèque effective-clip.js, ce qui entraînait des problèmes potentiels avec les effets de l’interface utilisateur jQuery.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/35b1b1da>
