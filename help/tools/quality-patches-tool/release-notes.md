---
title: Notes de mise à jour
description: Découvrez les correctifs disponibles pour Adobe Commerce et les problèmes qu’ils résolvent.
exl-id: 22262555-f5ea-49ad-98ad-ea8428ef66d5
source-git-commit: 811c29c722448a0dc0c9172f58020bd17241513c
workflow-type: tm+mt
source-wordcount: '26381'
ht-degree: 0%

---

# Notes de mise à jour

Le [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) fournit des correctifs individuels développés par Adobe et la communauté Magento Open Source. Il vous permet d’appliquer, d’annuler et d’afficher des informations générales sur tous les correctifs individuels disponibles pour la version installée d’Adobe Commerce. Vous pouvez appliquer des correctifs à des projets Adobe Commerce et Magento Open Source, quelle que soit la personne qui les a développés. Par exemple, vous pouvez appliquer un correctif développé par la communauté aux projets Adobe Commerce.

>[!INFO]
>
>Voir [Application de correctifs](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches) pour obtenir des instructions sur l’application de correctifs à vos projets Adobe Commerce. Voir [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le Guide de mise à jour logicielle pour consulter la liste complète des correctifs publiés.

>[!INFO]
>
>Pour plus d’informations sur les [!DNL quality patches] créées par la communauté pour Magento Open Source, consultez les [notes de mise à jour](https://github.com/magento/quality-patches/blob/master/community-release-notes.md).

## v1.1.65 {#v1-1-65}

* **ACP2E-3753** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Correction du problème où les e-mails d’alerte de produit dans une configuration multi-magasin étaient toujours envoyés à l’aide du thème par défaut, quelle que soit la configuration du magasin ou du thème.
* **ACSD-64118** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème où les requêtes simultanées d’enregistrement et de mise à jour du même produit entraînent une incohérence des données ou des produits dupliqués.
* **ACSD-64813** (pour Adobe Commerce >=2.4.4 &lt;2.4.9) - Correction du problème en raison duquel l’annulation de l’affectation de catégories d’un catalogue partagé [!DNL B2B] via [!DNL REST]’API prend trop de temps ou expire avec des catalogues volumineux.
* **ACSD-65202** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Correction du problème en raison duquel la page « Mon compte » n’affiche pas les commandes récentes provenant d’autres vues du magasin au sein du même magasin.
* **ACSD-65254** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Correction du problème en raison duquel les notifications par e-mail n’étaient pas envoyées aux clients après la mise à jour de leurs adresses e-mail sur leurs comptes à l’aide de la mutation `updateCustomerEmail` [!DNL GraphQL].
* **ACSD-65331** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Correction du problème en raison duquel le magasin sélectionné dans [!UICONTROL Pick in Store] a été effacé après avoir consulté à plusieurs reprises la page de passage en caisse.
* **ACSD-65822** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige le problème d’affichage incorrect des quantités de lots et de produits configurables dans le panneau Panier sous [!UICONTROL Customer's Activities].
* **ACSD-66093** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige le problème de saisie des adresses e-mail dans les champs [!UICONTROL First Name] et [!UICONTROL Last Name] du client invité, ce qui entraîne des e-mails de confirmation de commande non valides.
* Versions mises à jour : **ACSD-51291**
* Correctifs remplacés : **ACSD-61522**

## v1.1.64 {#v1-1-64}

* **ACP2E-3838** (pour Adobe Commerce et Magento Open Source >=2.4.4-p9 &lt;2.4.4-p13 || >=2.4.5-p8 &lt;2.4.5-p12 || >=2.4.6-p6 &lt;2.4.6-p10 || >=2.4.7 &lt;2.4.7-p5) - Corrige le problème où les erreurs CORS [!DNL Page Builder] empêchent d’enregistrer les modifications dans le panneau d’administration en mode production.
* **ACP2E-3841** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.8) - Correction d’un problème en raison duquel les règles de prix de panier pour les produits à expédition multiple ne s’appliquent pas correctement lorsque des conditions de sous-sélection sont utilisées et que l’expédition gratuite est activée.
* **ACSD-63139** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel l’exportation du produit échoue lorsque les attributs du produit contiennent des milliers de valeurs d’option.
* **ACSD-65100** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Correction d’un problème en raison duquel la suppression des valeurs de [!UICONTROL Maximum Width] et [!UICONTROL Maximum Height] dans la configuration [!UICONTROL Media Gallery Image Optimization] entraînait une erreur lors du processus d’optimisation des images.
* **ACSD-65127** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Correction du problème en raison duquel l’activation de la minimisation de JavaScript en mode de production entraîne la génération d’erreurs par [!DNL TinyMCE] 6 dans la console du navigateur, ce qui affecte les fonctionnalités et l’expérience utilisateur.
* **ACSD-65787** (pour Adobe Commerce et Magento Open Source >=2.4.7-p5 &lt;2.4.8) - Correction du problème de blocage de la classe SchemaBuilder lors de la création ou des mises à jour de schémas en raison d’une « colonne » de clé de tableau non définie lors du traitement des données de table.
* **ACSD-65223** (pour Adobe Commerce, B2B 1.5.1) - Correction d’un problème en raison duquel les termes et accords sélectionnés manuellement pour les commandes fournisseur [!DNL B2B] entraînaient une erreur.
* **ACSD-65540** (pour Adobe Commerce, B2B 1.5.2) - Correction du problème d’erreur de syntaxe SQL due à l’absence de la fonction `REGEXP_LIKE` lors de la mise à jour de la table `company_structure`.
* **ACSD-65684** (pour Adobe Commerce, B2B 1.5.2) - Corrige le problème de performances en raison duquel la mise à niveau du module de `Magento_Company` après la mise à niveau vers [!DNL B2B] 1.5.2 prenait trop de temps lors du traitement d’un grand nombre d’enregistrements (~100 000+) dans la table `company_structure`.
* Versions mises à jour : **ACSD-48234**, **ACSD-51819**, **ACSD-57570**, **ACSD-56415**

## v1.1.63 {#v1-1-63}

* **ACSD-64627** (pour Adobe Commerce >=2.4.6-p8 &lt;2.4.8) - Correction du problème en raison duquel les attributs personnalisés du client ne peuvent pas être enregistrés lors de l’ajout ou de la modification d’utilisateurs dans la structure de l’entreprise.
* **ACSD-64753** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Correction du problème en raison duquel le magasin présélectionné dans « Ramassage en magasin » ne se met pas à jour lorsque l’adresse de livraison change, même si elle se trouve en dehors du rayon du magasin.
* **ACSD-65195** (pour Adobe Commerce >=2.4.4 &lt;2.4.8) - Correction du problème en raison duquel la `createCompany` de mutation de GraphQL renvoie une erreur pour un pays ne disposant pas d’une région requise.
* **LYNX-839** (pour Adobe Commerce 2.4.8) - Suppression de l’exposition du groupe de clients, des segments et des informations sur les règles promotionnelles via GraphQL.
* Versions mises à jour : **MDVA-12304**, **ACSD-48234**, **ACSD-58054**

## v1.1.62 {#v1-1-62}

* **ACSD-63406** (pour Adobe Commerce et Magento Open Source >=2.4.4-p9 &lt;2.4.5 || >=2.4.5-p8 &lt;2.4.6 || >=2.4.6-p6 &lt;2.4.8) - Correction du problème en raison duquel les guillemets persistants expirés ne sont effacés par aucune tâche cron lors de l’exécution de la tâche cron `persistent_clear_expired`.
* **ACSD-63520** (pour Adobe Commerce et Magento Open Source >=2.4.7 &lt;2.4.8) - Correction du problème en raison duquel les images ajoutées par le biais de **[!UICONTROL Configurations]** dans le panneau d’administration ne respectent pas la taille maximale de chargement.
* **ACSD-64523** (pour Adobe Commerce et Magento Open Source >=2.4.7 &lt;2.4.8) - Correction du problème en raison duquel il était possible de créer des produits sans nom via le processus d’importation (admin ou API), ce qui rompait l’interface d’administration et entraînait des produits non valides.
* **ACSD-64532** (pour Adobe Commerce et Magento Open Source >=2.4.6-p2 &lt;2.4.8) - Correction du problème en raison duquel une variable ENV définie sur « false » est traitée comme une chaîne « false » au lieu d’une valeur booléenne false.
* **ACSD-64592** (pour Adobe Commerce >=2.4.4 &lt;2.4.8) - Corrige le problème en raison duquel le lien de réclamation figurant dans l’e-mail pour une carte-cadeau dans les magasins non par défaut redirigeait toujours la réclamation de la carte-cadeau vers le site web par défaut.
* **ACSD-65164** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.8) - Correction du problème en raison duquel le message d’erreur *Certaines des options d’élément sélectionnées ne sont actuellement pas disponibles* se produit lors de la réorganisation d’un produit configurable avec une seule option personnalisée de case à cocher sélectionnée.
* **ACSD-64732** (pour Adobe Commerce >=2.4.4 &lt;2.4.8) - Correction du problème en raison duquel les contrôleurs tiers n’étaient pas correctement mis en cache avec les segments des clients.

## v1.1.61 {#v1-1-61}

* **ACP2E-3689** (pour Adobe Commerce et Magento Open Source >=2.4.7 &lt;2.4.8) - Correction de plusieurs problèmes liés à l’affichage de l’arborescence des catégories à des niveaux plus profonds et reflétant les relations ancre/non-ancre.
* **ACP2E-3705** (pour Adobe Commerce >=2.4.7 &lt;2.4.8) - Correction d’un problème en raison duquel l’exécution du cron `indexer_update_all_views` échoue lorsque `MAGE_INDEXER_THREADS_COUNT` est défini.
* **ACSD-63883** (pour Adobe Commerce >=2.4.4 &lt;2.4.7-p4) - Correction du problème en raison duquel la liste de demandes d’approvisionnement renvoie un `items_count` incorrect dans la réponse de GraphQL.
* **ACSD-63974** (pour Adobe Commerce >=2.4.4 &lt;2.4.8) - Correction du problème en raison duquel le chargement de la page de la liste des demandes d’approvisionnement prend trop de temps lorsqu’il y a trop d’éléments, en ajoutant une fonction de pagination à la grille de la liste des demandes d’approvisionnement sur le Storefront, qui affiche uniquement des parties d’enregistrements limitées au nombre d’enregistrements par page, au lieu de tous les enregistrements à la fois.
* **ACSD-64178** (pour Adobe Commerce et Magento Open Source >=2.4.7 &lt;2.4.8) - Correction du problème en raison duquel la page de modification du jeu d’attributs se charge lentement s’il existe des milliers d’attributs de produit.
* **ACSD-64209** (pour Adobe Commerce >=2.4.4 &lt;2.4.8) - Correction du problème en raison duquel le planificateur cron récupère toutes les cotations négociables sans exclure celles dont le statut est **[!UICONTROL ordered]**, ce qui entraîne le déclenchement d’un e-mail ou d’e-mails.
* **ACSD-64431** (pour Adobe Commerce et Magento Open Source >=2.4.7 &lt;2.4.8) - La mutation `placeOrder` qui contient les informations sur le code de coupon dans la requête ne renvoie plus d’erreur interne, mais indique que la commande a été passée avec succès.
* **ACSD-64467** (pour Adobe Commerce et Magento Open Source >=2.4.7 &lt;2.4.8) - Correction du problème en raison duquel l’éditeur WYSIWYG apparaissait vide après l’enregistrement d’une description de catégorie au niveau de l’affichage du magasin.
* **ACSD-64546** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige le problème où un message d’erreur générique se produit dans l’interface utilisateur et où une exception *Conversion de tableau en chaîne* est stockée dans les journaux lors de la création de l’étiquette d’expédition de l’onduleur, en veillant à ce que l’erreur réelle s’affiche dans l’interface utilisateur et à ce que le message d’erreur correct soit stocké dans les journaux.
* **ACSD-64684** (pour Adobe Commerce >=2.4.4 &lt;2.4.8) - Corrige le problème où une erreur de validation se produit lors de l’édition et de l’enregistrement d’une carte cadeau avec une valeur supérieure à *999* en raison de la virgule (séparateur des milliers) dans le nombre *mille (1 000)*.
* Versions mises à jour : **ACSD-49392**, **ACSD-50368**, **ACSD-51819**, **ACSD-54966-V2**, **ACSD-57003**, **ACSD-62979**, **ACSD-64112**
* Correctifs remplacés : **ACSD-49392**, **ACSD-58739**, **ACSD-62689**, **ACSD-64112**
* Correctifs obsolètes : **ACSD-46192**, **ACSD-52133**

## v1.1.60 {#v1-1-60}

* **ACSD-63323** (pour Adobe Commerce >=2.4.7 &lt;2.4.8) - Correction d’un problème en raison duquel l’option **[!UICONTROL Select All]** ne fonctionne pas lors de l’ajout de produits à une catégorie. En outre, cela garantit que la pagination et le libellé du nombre d’enregistrements fonctionnent correctement lors de l’ajout de produits à une catégorie via la grille contextuelle.
* **ACSD-63992** (pour Adobe Commerce >=2.4.4 &lt;2.4.8) - Correction d’un problème en raison duquel une règle de prix de panier avec un coupon et une condition basée sur une méthode d’expédition ne peuvent pas être correctement appliquées via l’interface utilisateur d’administration.
* **ACSD-64111** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Correction du problème qui se produit lorsqu’une erreur se produit lors de la définition de conditions imbriquées pour un composant Produit dans [!DNL Page Builder].
* **ACSD-64137** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Correction d’un problème en raison duquel la recherche d’emplacements de retrait par code postal ne fonctionnait pas correctement pour la localisation en néerlandais.
* **ACSD-64149** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Correction du problème en raison duquel un segment client avec une condition de période peut être enregistré lorsqu’une seule des dates est modifiée.
* Versions mises à jour : **MDVA-12304**, **ACSD-45049**, **MDVA-43824**, **ACSD-46192**, **ACSD-50368**, **ACSD-52133**, **ACSD-47657**, **ACSD-51819**, **ACSD-54966,** ACSD-**, 55628** ACSD-**, 45049** ACSD-**63242**

## v1.1.59 {#v1-1-59}

* **ACSD-63454** (pour Adobe Commerce et Magento Open Source >=2.4.7 &lt;2.4.8) - Correction du problème en raison duquel la valeur par défaut d’une liste déroulante et d’attributs à sélection multiple n’est pas enregistrée correctement dans la base de données.
* **ACSD-63574** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.5) - Corrige le problème en raison duquel l’ajout d’une liste de produits groupée à un bloc via le Page Builder entraînait une erreur.
* **ACSD-63793** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.8) - Corrige le problème lorsque les processus d’importation interfèrent les uns avec les autres dans différents onglets du navigateur.
* **ACSD-64113** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.8) - Correction du problème provoquant des erreurs dans l’administration lors du chargement d’images avec une largeur relativement faible par rapport à leur hauteur (ou vice versa) via la galerie de médias.
* **ACSD-64212** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.8) - Correction du problème en raison duquel une commande n’est pas associée à un compte client lors de la création du compte via GraphQL après la commande.
* **ACSD-63469** (pour Adobe Commerce et Magento Open Source >=2.4.7 &lt;2.4.8) - Correction du problème d’application incorrecte des remises forfaitaires pour l’ensemble du panier lorsque plusieurs règles étaient appliquées.
* **ACSD-63870** (pour Adobe Commerce >=2.4.4 &lt;2.4.4-p11) - Correction d’un problème en raison duquel un client de la société n’était pas correctement déconnecté lorsque le statut de la société change pendant la session active du client.
* **ACSD-64112** (pour Adobe Commerce >=2.4.5 &lt;2.4.8) - Correction d’un problème en raison duquel l’exécution du cron `indexer_update_all_views` échoue lorsque `MAGE_INDEXER_THREADS_COUNT` est défini.
* Versions mises à jour : **ACSD-61622**
* Correctifs remplacés : **ACSD-61553**
* Correctifs obsolètes : **ACSD-61199**

## v1.1.58 {#v1-1-58}

* **ACSD-48570** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel la page de réinitialisation du mot de passe n’était pas accessible en cliquant sur le lien [!UICONTROL Admin] Réinitialiser le mot de passe lorsque **Ajouter le code de magasin aux URL** était *activé*, ce qui entraînait auparavant l’affichage de la page de connexion ou d’une page 404.
* **ACSD-62118** (pour Adobe Commerce >=2.4.6 &lt;2.4.8) - Correction du problème en raison duquel la table `sales_order_tax_item` n’est pas entièrement mise à jour lorsque des commandes [!DNL B2B] sont passées à l’aide de la méthode Bon de commande.
* **ACSD-63067** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige le problème où toutes les quantités de produits sont incorrectement mises en surbrillance et où le message *[!DNL Please specify the quantity of product(s).]* s’affiche pour tous les produits d’un produit regroupé lorsqu’une seule quantité est incorrecte.
* **ACSD-63090** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Correction du problème de suppression des articles du panier lors de la suppression d’un produit après son ajout au panier.
* **ACSD-63182** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige le problème où une erreur se produit lors de l’enregistrement d’un produit groupé dupliqué avec **[!DNL MSI]** *activé*.
* **ACSD-63283** (pour Adobe Commerce >=2.4.4 &lt;2.4.8) - Correction du problème en raison duquel la commande d’éléments à partir du registre des cadeaux provoque une exception et en raison duquel les mises à jour du registre des cadeaux incluent des éléments qui n’appartiennent pas au registre.
* **ACSD-63299** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Correction du problème en raison duquel le prix spécial d’un produit configurable ne s’affiche pas sur le storefront.
* **ACSD-63325** (pour Adobe Commerce et Magento Open Source >=2.4.7 &lt;2.4.8) - Corrige le problème en raison duquel une erreur `Syntax Error: Unexpected <EOF>` se produit lors de l’envoi d’une demande de [!DNL GraphQL] vide.
* **ACSD-63329** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Correction du problème en raison duquel les valeurs par défaut des attributs avec des types d’entrée **[!UICONTROL Date]** ou **[!UICONTROL Date and Time]** ne sont pas définies lors de la création de produits via l’[!DNL REST API].
* **ACSD-63572** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.8) - Correction du problème en raison duquel les tables temporaires de l’indexeur `CatalogRule` ne sont pas nettoyées si le processus de l’indexeur est arrêté.
* **ACSD-63578** (pour Adobe Commerce >=2.4.4 &lt;2.4.8) - Correction du problème en raison duquel le fait de cliquer sur le bouton **[!UICONTROL Delete]** dans **[!UICONTROL Add to Order by SKU]** de l’[!UICONTROL Admin] ne supprime pas le [!DNL SKU].
* Versions mises à jour : **MDVA-39305-V3**
* Correctifs remplacés : **ACSD-56280**
* Correctifs obsolètes : **ACSD-62872**

## v1.1.57 {#v1-1-57}

* **ACSD-57570** (pour Adobe Commerce >=2.4.4 &lt;2.4.4-p10) - Correction du problème en raison duquel un utilisateur administrateur restreint ayant accès à un magasin particulier ne peut pas toujours voir tous les catalogues partagés auxquels les produits sont affectés, ni ne peut voir les clients qui ne peuvent pas être enregistrés, ce qui entraîne des incohérences dans le système.
* **ACSD-58325** (pour Adobe Commerce >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel le bouton **[!UICONTROL Import]** est disponible même après une erreur de validation.
* **ACSD-59083** (pour Adobe Commerce >=2.4.4 &lt;2.5.0) - Correction du problème en raison duquel certaines opérations de mise à jour de la base de données génèrent une erreur *Table ou vue de base introuvable* si la mise à jour de la [!DNL mview] est exécutée en même temps.
* **ACSD-61622** (pour Adobe Commerce et Magento Open Source >=2.4.6-p1 &lt;2.4.7) - Correction du problème en raison duquel les taux spécifiques au compte de [!DNL FedEx] sont manquants dans la réponse.
* **ACSD-61895** (pour Adobe Commerce >=2.4.4 &lt;2.5.0) - Correction du problème en raison duquel les catégories [!DNL GraphQL] la requête renvoient des catégories avec l’autorisation **autoriser** même si la catégorie racine ne dispose pas de l’autorisation **autoriser**.
* **ACSD-62212** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.5.0) - Correction du problème en raison duquel le contenu de l’e-mail **Mot de passe oublié** n’est pas traduit dans la langue de la vue du magasin.
* **ACSD-62481** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.5.0) - Correction du problème en raison duquel le panier du client devient vide même si **[!UICONTROL Persistence]** est activé.
* **ACSD-62629** (pour Adobe Commerce et Magento Open Source >=2.4.7 &lt;2.5.0) - Correction d’un problème en raison duquel une liste de produits utilisée dans **[!UICONTROL Widgets]** ne reflète pas la condition de catégorie.
* **ACSD-62635** (pour Adobe Commerce et Magento Open Source >=2.4.7 &lt;2.5.0) - Corrige le problème d’affichage incorrect des produits associés à plusieurs magasins dans la requête de produit [!DNL GraphQL].
* **ACSD-62671** (pour Adobe Commerce et Magento Open Source >=2.4.7 &lt;2.5.0) - Correction du problème en raison duquel la requête [!DNL GraphQL] ne renvoie pas d’informations d’adresse à jour lors de la première tentative.
* **ACSD-62689** (pour Adobe Commerce et Magento Open Source >=2.4.7 &lt;2.5.0) - Correction du problème en raison duquel le client ne peut pas ajouter de catégories dans **[!UICONTROL Related Product Rules and Widgets]** après *profondeur 4*.
* **ACSD-62708** (pour Adobe Commerce et Magento Open Source >=2.4.4-p11 &lt;2.4.5 || >=2.4.5-p10 &lt;2.4.6-p2 || >=2.4.6-p8 &lt;2.4.7-p1) - Correction du problème en raison duquel la taille de police de l’éditeur [!DNL TinyMCE] 7 dans l’administration affichait *PT* et non *PX*. Désormais, vous pouvez également définir la taille de police en *PX* au lieu de *PT*.
* **ACSD-62758** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.5.0) - Correction d’un problème en raison duquel les vidéos de produit ne s’affichent pas correctement sur la page de détails du **[!UICONTROL Configurable Product]** si le [!DNL URL] contient des options sélectionnées.
* **ACSD-62951** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.5.0) - Correction du problème d’envoi de l’e-mail d’avoir sans inclure d’éléments ni de totaux.
* **ACSD-62965** (pour Adobe Commerce >=2.4.7 &lt;2.5.0) - Corrige le problème en raison duquel un message `LocalizedException` n’est pas inclus dans la réponse de [!DNL GraphQL] d’emplacement de commande.
* **ACSD-63286** (pour Adobe Commerce >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel les produits affectés à un catalogue partagé via [!DNL API] n’apparaissent pas sur le storefront tant qu’une réindexation manuelle n’a pas été exécutée.
* **ACSD-63326** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.5.0) - Corrige le problème en raison duquel le [!UICONTROL Admin] est redirigé vers une page endommagée après avoir passé une commande sur le serveur principal.
* Versions mises à jour : **ACSD-51739**
* Correctifs remplacés : **MDVA-43451**, **ACSD-62755**

## v1.1.56 {#v1-1-56}

* **ACSD-63244** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige le problème en raison duquel une erreur [!DNL JavaScript] empêche [!DNL Google Maps] rendu correct. Correction du problème en raison duquel il existe de nombreuses *Uncaught TypeError : this._each n&#39;est pas une fonction* erreurs dans la console du panneau [!UICONTROL Admin].
* **ACSD-63242** (pour Adobe Commerce et Magento Open Source >=2.4.6-p8 &lt;2.4.7 || >=2.4.7-p3 &lt;2.4.8) - Correction du problème de lenteur des importations lors de l’ajout de produits de catalogue comportant plus de 10 000 entrées.
* **ACSD-63062** (pour Adobe Commerce et Magento Open Source >=2.4.7 &lt;2.4.8) - Correction du problème en raison duquel des calculs de remise de panier incorrects se produisent lorsque plusieurs règles qui se chevauchent sont appliquées.
* **ACSD-62979** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige le problème en raison duquel l’utilisation d’un [!UICONTROL Store ID] incorrect dans l’en-tête [!DNL GraphQL] provoque une erreur de mémoire fatale.
* **ACSD-62971** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Correction du problème en raison duquel l’importation d’origines de stock avec des valeurs non numériques dans la colonne **quantité** entraîne la définition de la **quantité** sur *0*.
* **ACSD-62872** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Correction du problème lié à la validation d’attributs uniques lorsque les mises à jour du planning sont validées de manière incorrecte.
* **ACSD-62755** (pour Adobe Commerce et Magento Open Source >=2.4.4-p11 &lt;2.4.5 || >=2.4.5-p10 &lt;2.4.6 || >=2.4.6-p8 &lt;2.4.7 || >=2.4.7-p3 &lt;2.4.8) - Correction du problème où [!DNL TinyMCE] 7 exige que la taille de la police et la police soient spécifiquement ajoutées dans les paramètres d’initialisation de l’éditeur.
* **ACSD-62670** (pour Adobe Commerce et Magento Open Source >=2.4.4-p11 &lt;2.4.5 || >=2.4.5-p10 &lt;2.4.6 || >=2.4.6-p8 &lt;2.4.7 || >=2.4.7-p3 &lt;2.4.8) - Correction du problème en raison duquel l’exportation du rapport [!UICONTROL Products Ordered] vers [!DNL CSV] et [!DNL XML] renvoie une erreur.
* **ACSD-62577** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige le problème de performances lentes des requêtes de recherche storefront en optimisant les index de requête et de table.
* **ACSD-62475** (pour Adobe Commerce et Magento Open Source >=2.4.7 &lt;2.4.8) - Correction d’un problème de fusion incorrecte des produits [!UICONTROL Gift Card] dans le panier.
* **ACSD-62428** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel `is_out_of_stock` est défini sur une valeur incorrecte dans l’index de recherche de catalogue lorsque l’[!DNL SKU] n’est pas défini comme attribut consultable.
* **ACSD-62355** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.8) - Améliore le temps de chargement de la page d’édition du produit configurable lorsque le produit configurable est basé sur de nombreux attributs avec de nombreuses valeurs.
* **ACSD-61805** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige le problème où les produits restent en rupture de stock sur le storefront après la mise à jour du statut de la commande en attente via le [!DNL REST API].
* **ACSD-60811** (pour Adobe Commerce et Magento Open Source >=2.4.7 &lt;2.4.8) - Correction du problème en raison duquel la mise à jour du statut de la commande avec une valeur ou un commentaire personnalisé n’est possible que si le statut actuel est *traitement* ou *fraude*.
* **ACSD-62952** (pour Adobe Commerce >=2.4.4 &lt;2.4.8) - Correction du problème d’affichage inexact de la date de [!UICONTROL Gift Registry] sur le storefront.
* **ACSD-55339** (pour Adobe Commerce >=2.4.4 &lt;2.4.8) - Correction du problème où un produit [!DNL SKU] commençant par « 0 » (zéro) supprime le « 0 », empêchant la mise à jour du devis.
**
* Correctifs mis à jour : **ACSD-59514**
* Versions mises à jour : **ACSD-60816**
* Correctifs remplacés : **ACSD-59967**

## v1.1.55 {#v1-1-55}

* **ACSD-58383** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Correction du problème en raison duquel l’émission d’un remboursement via le [!DNL REST API] avec deux demandes identiques exécutées simultanément crée des avoirs en double.
* **ACSD-58471** (pour Adobe Commerce >=2.4.4 &lt;2.4.8) - Correction du problème en raison duquel le contenu dynamique ne se charge pas sur la page des détails du produit, au moment où les règles de prix de catalogue associées étaient planifiées.
* **ACSD-58566** (pour Adobe Commerce >=2.4.6 &lt;2.4.8) - Correction du problème en raison duquel [!DNL GraphQL] renvoie une erreur de serveur interne lors de l’interrogation du champ `created_at` dans la mutation `addPurchaseOrderComment`.
* **ACSD-58685** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Correction du problème en raison duquel les e-mails de vente déclenchés alors que la communication par e-mail était désactivée étaient toujours envoyés une fois la communication par e-mail réactivée.
* **ACSD-58735** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Correction du problème en raison duquel un administrateur restreint ne pouvait pas afficher les paniers abandonnés sur la page du compte client dans la [!UICONTROL Admin] d’un site web associé.
* **ACSD-58828** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.8) - Correction du problème en raison duquel le message de validation côté serveur *adresse requise* s’affiche si un champ obligatoire reste vide, à côté du message de validation côté client. La validation côté serveur n’affiche pas le message pour les champs obligatoires vides, et la validation côté client gère la notification d’erreur, en indiquant *Ceci est un champ obligatoire*.
* **ACSD-60344** (pour Adobe Commerce >=2.4.4 &lt;2.4.8) - Correction du problème d’envoi d’e-mails de confirmation de commande en double lors de l’utilisation d’un **[!UICONTROL Purchase Order]** avec approbation automatique.
* **ACSD-61348** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Correction du problème en raison duquel les éléments de liste de souhaits sont visibles via [!DNL GraphQL], mais pas sur le storefront dans un environnement multisite.
* **ACSD-61534** (pour Adobe Commerce et Magento Open Source >=2.4.7 &lt;2.4.8) - Correction du problème en raison duquel la configuration de conception ne pouvait pas être définie à l’aide de la commande `bin/magento config:set` et les valeurs verrouillées pouvaient être modifiées par la manipulation du formulaire. Désormais, les valeurs verrouillées définies à partir du [!DNL CLI] avec `--lock-env` ou `--lock-conf` ne peuvent pas être mises à jour.
* **ACSD-61785** (pour Adobe Commerce >=2.4.4 &lt;2.4.8) - Correction du problème en raison duquel la mise à jour de l’attribut `reward_warning_notification` n’était pas possible via [!DNL GraphQL] mutation et les appels de [!DNL REST API], l’alignement de son comportement sur `reward_update_notification`.
* **ACSD-62591** (pour Adobe Commerce et Magento Open Source >=2.4.7 &lt;2.4.8) - Correction d’un problème en raison duquel le thème ne change pas correctement lorsque les **[!UICONTROL User Agent Rules]** sont configurées.
* **ACSD-62793** (pour Adobe Commerce et Magento Open Source >=2.4.7 &lt;2.4.8) - Correction du problème en raison duquel les attributs `datetime` dans les données exportées n’incluent pas le composant « Heure ». De plus, si **[!UICONTROL Fields Enclosure]** est *activé*, les valeurs d’attribut dans la colonne `additional_attributes` sont placées entre guillemets doubles.
* **ACSD-62332** (pour Adobe Commerce >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel la requête de [!DNL GraphQL] de liste de produits était limitée à un `total_count` de 10 000 produits. Correction du problème en raison duquel [!DNL Live Search] définit la page active sur *1* au lieu de la page *2* dans les critères de recherche lors de l’interrogation via [!DNL GraphQL].
* Versions mises à jour : **ACSD-46581**, **ACSD-49513**, **ACSD-52801**, **ACSD-59514**
* Correctifs remplacés : **ACSD-52801**, **ACSD-55100**
* Correctifs obsolètes : **ACSD-52085**, **ACSD-57854**

## v1.1.54 {#v1-1-54}

* **AC-13283** (pour Adobe Commerce et Magento Open Source 2.4.6-p8) - Rétablit les modifications rétrocompatibles de la commande incluses dans 2.4.6-p8.
* **ACSD-60267** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Correction du problème en raison duquel la Taxe fixe sur les produits (FPT) s’applique correctement lors de l’ajout de produits simples avec FPT directement au panier, mais échoue lors de la sélection de ces produits par le biais d’options de produits configurables.
* **ACSD-61103** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel le nombre d’échecs dans le tableau `customer_entity` n’est pas réinitialisé à zéro après la connexion réussie d’un client par le biais de points d’entrée de l’API.
* **ACSD-61134** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel le mode de paiement [!DNL Braintree Vault] est automatiquement désélectionné dans le workflow de passage en caisse lorsqu’un acheteur met à jour son adresse de facturation en désélectionnant la case à cocher *[!UICONTROL My billing and shipping address are the same]*.
* **ACSD-61199** (pour Adobe Commerce >=2.4.4 &lt;2.4.8) - Correction du problème en raison duquel l’onglet de hiérarchie de page CMS n’affiche pas une arborescence appropriée lors de la modification d’une page CMS avec une hiérarchie existante.
* **ACSD-61200** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Correction du problème en raison duquel les calculs pour *[!UICONTROL Total Amount]* et *[!UICONTROL Total Amount Actual]* dans les ventes ne comportent pas les *[!UICONTROL Discount Tax Compensation Amount]* et *[!UICONTROL Shipping Discount Tax Compensation Amount]*, ce qui entraîne des incohérences dans les données de commande client.
* **ACSD-61522** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige le problème en raison duquel il est possible de saisir des adresses e-mail dans les champs *[!UICONTROL First Name]* et *[!UICONTROL Last Name]* du client invité et d’envoyer des e-mails de confirmation de commande non valides.
* **ACSD-61756** (pour Adobe Commerce >=2.4.4 &lt;2.4.7) - Améliore les performances des filtres `AdvancedSalesRule`.
* **ACSD-61799** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.5) - Correction du problème en raison duquel la remise totale est incorrectement calculée lorsque plusieurs règles de panier avec des remises fixes sont appliquées au devis.
* **ACSD-61845** (pour Adobe Commerce et Magento Open Source >=2.4.7-p1 &lt;2.4.8) - Corrige l’erreur qui se produit lorsqu’une requête est envoyée avec uniquement un en-tête *text/html* accept.
* **ACSD-62056** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Correction du problème d’échec du chargement des images pour un produit configurable si MSI est installé.
* **ACSD-62485** (pour Adobe Commerce >=2.4.4 &lt;2.4.6-p8 || >=2.4.7 &lt;2.4.8) - Corrige le problème où `async.operations.all` consommateur cesse de fonctionner lors de la création d’une entreprise.
* Versions mises à jour : **ACSD-48661**, **ACSD-55100**, **ACSD-61553**
* Correctifs obsolètes : **ACSD-51846**

## v1.1.53 {#v1-1-53}

* **ACSD-48318** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel l’imbrication de l’émulation d’environnement n’est pas autorisée. Désormais, l’émulation commence pendant l’appel `send()` une fois qu’elle s’arrête pendant l’appel `getInfoBlockHtml()`.
* **ACSD-59930** (pour Adobe Commerce >=2.4.6 &lt;2.4.8) - Améliore les performances des flux **[!UICONTROL Create]**, **[!UICONTROL Save]** et **[!UICONTROL Delete]** de l’entreprise.
* **ACSD-60584** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel un jeton d’accès créé pour l’utilisateur sur un site web est autorisé à accéder aux informations du client ou à les modifier sur d’autres sites web.
* **ACSD-60804** (pour Adobe Commerce >=2.4.4 &lt;2.4.8) - Correction du problème en raison duquel la modification d’un client lié à une société supprimée entraînait l’erreur *Appel à une fonction membre `getSuperUserId()` sur null*.
* **ACSD-61133** (pour Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.8) - Correction du problème en raison duquel le [!DNL cron] `sales_clean_quotes` supprime les devis des commandes fournisseur non approuvées.
* **ACSD-61528** (pour Adobe Commerce >=2.4.6 &lt;2.4.8) - Correction du problème en raison duquel la récupération de rôles à partir du [!UICONTROL Admin] à l’aide de [!DNL GraphQL] ne renvoie aucun résultat.
* **ACSD-61553** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel les remises **[!UICONTROL Cart Price Rule]** sont incorrectement calculées lorsque plusieurs remises avec des priorités et des **[!UICONTROL Maximum Qty Discount is Applied To]** différentes sont appliquées au produit.
* **ACSD-61667** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Améliore les performances de l’inventaire pour la création d’expédition dans le cas de nombreuses sources avec retrait en magasin.
* **ACSD-61969** (pour Adobe Commerce >=2.4.7 &lt;2.4.8) - Correction du problème en raison duquel l’utilisateur ou l’utilisatrice doit saisir un code de coupon sensible à la casse pour correspondre exactement à celui qui a été configuré.
* Versions mises à jour : **ACSD-54989**, **ACSD-60632**

## v1.1.52 {#v1-1-52}

* **BUNDLE-3375** (pour Adobe Commerce et Magento Open Source) : ajoute tous les champs nécessaires pour répondre aux exigences du mandat 3DS VISA lors de l’utilisation de [!DNL Braintree] comme passerelle de paiement.
* **ACSD-59366** (pour Adobe Commerce >=2.4.6 &lt;2.4.8) - Correction du problème d’erreur qui se produit lors de la tentative de suppression d’une équipe contenant des utilisateurs désactivés qui ne sont pas visibles dans la liste des équipes.
* **ACSD-59865** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige le problème où un [!UICONTROL Cart Price Rule] n’annule pas les règles précédemment appliquées si la quantité de produit dans le panier n’est pas suffisante pour que les règles soient appliquées.
* **ACSD-59925** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige le problème lié au tri des éléments dans le [!UICONTROL Media Gallery] par position dans GraphQL.
* **ACSD-59952** (pour Adobe Commerce >=2.4.4 &lt;2.4.8) - Correction du problème d’erreur lors de la création d’un [!UICONTROL Shared Catalog] avec un ID de groupe affecté à un [!UICONTROL Shared Catalog] existant.
* **ACSD-60590** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Améliore les performances de génération de [!UICONTROL Bestsellers Aggregated Daily Reports] pour un grand volume de commandes passées.
* **ACSD-60673** (pour Adobe Commerce >=2.4.4 &lt;2.4.8) - Correction d’un problème en raison duquel la [!UICONTROL Cart Price Rule] de plusieurs modes de paiement lors du passage en caisse ne s’applique pas correctement au mode de paiement spécifique.
* **ACSD-60684** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige le problème en raison duquel le tri des produits GraphQL par plusieurs champs ne fonctionne pas comme prévu.
* **ACSD-60788** (pour Adobe Commerce >=2.4.7 &lt;2.4.8) - Correction du problème où les scripts personnalisés pour [!DNL Google Tag Manager] ne sont pas exécutés en raison d’erreurs de politique de sécurité du contenu (CSP).
* **ACSD-61322** (pour Adobe Commerce >=2.4.6 &lt;2.4.8) - Correction du problème en raison duquel les [!UICONTROL Products/Categories] non affectés au [!UICONTROL Shared Catalog] pour la valeur par défaut (groupe général) sont toujours inclus dans le plan de site XML.
* **ACSD-61366** (pour Adobe Commerce et Magento Open Source >=2.4.7 &lt;2.4.8) - Correction du problème en raison duquel la commande `setup:static-content:deploy --jobs 4` s’exécute avec plusieurs tâches échouant avec le paramètre *Le port doit être configuré dans le paramètre d’hôte* erreur lorsque le port est spécifié pour la connexion à la base de données.
* Correctifs mis à jour : ACSD-51857, ACSD-57394

## v1.1.51 {#v1-1-51}

* **ACSD-59786** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.8) - Correction du problème en raison duquel GraphQL renvoie une erreur de serveur interne lors de la tentative d’obtention d’un ID de devis pour un devis expiré.
* **ACSD-60234** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Correction du problème en raison duquel un montant incorrect est affiché sur [!DNL PayPal] lorsque la remise est appliquée par le mode de paiement.
* **ACSD-59967** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7-p2) - Corrige le problème en raison duquel une erreur JavaScript empêche [!DNL Google Maps] rendu correct.
* **ACSD-60326** (pour Adobe Commerce >=2.4.4 &lt;2.4.8) - Correction du problème en raison duquel une erreur se produit sur la requête GraphQL pour le statut du retour des clients.
* **ACSD-60538** (pour Adobe Commerce >=2.4.7 &lt;2.4.8) - Correction du problème en raison duquel, si un produit est désactivé dans *[!UICONTROL All Store Views]* et activé uniquement dans des portées d’affichage de magasin spécifiques, les attributs de produit ne s’affichent pas correctement dans la réponse de GraphQL, ce qui entraîne l’affichage incorrect du produit.
* **ACSD-60631** (pour Adobe Commerce et Magento Open Source >=2.4.7 &lt;2.4.8) - Correction du problème en raison duquel GraphQL renvoie une erreur lorsque le même produit simple est affecté à plusieurs produits configurables.
* **ACSD-60632** (pour Adobe Commerce et Magento Open Source >=2.4.5-p8 &lt;2.4.8) - Correction du problème d’enregistrement d’une nouvelle adresse à chaque tentative de placement de commande, que la commande soit créée avec succès ou non.
* **ACSD-60816** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel les scripts [!DNL New Relic Browser Monitoring] injectés par l’agent APM ne sont pas conformes à la CSP (Content Security Policy), ce qui empêche leur exécution.
* **ACSD-61195** (pour Adobe Commerce et Magento Open Source >=2.4.7 &lt;2.4.8) - Corrige le problème en raison duquel aucun article de panier n’est renvoyé sur la dernière page de la requête GraphQL de panier.
* Correctifs mis à jour : ACSD-59378

## v1.1.50 {#v1-1-50}

* **ACSD-59280** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.5) - Corrige l’erreur *Appel à une méthode non définie ReflectionUnionType::getName()* qui se produit lors de l’installation des versions 2.4.4-pX.
* **ACSD-45049** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.4-p8 || >=2.4.5 &lt;2.4.6) - Correction d’un problème en raison duquel un paramètre d’attribut de *[!UICONTROL Is required]* client ne fonctionne pas correctement selon la portée du site web dans Admin.
* **ACSD-46938** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème de performances de la recréation des déclencheurs de base de données lors de l’`setup:upgrade`.
* **ACSD-48210** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel la mise à jour d’un attribut *[!UICONTROL Website Scope]* dans une vue de magasin spécifique remplace les valeurs d’attribut dans la portée globale.
* **ACSD-54887** (pour Adobe Commerce et Magento Open Source >=2.4.4-p4 &lt;2.4.4-p9 || >=2.4.5-p3 &lt;2.4.5-p8 || >=2.4.6-p1 &lt;2.4.6-p6) - Corrige le problème où le panier du client est effacé après l’expiration de la session client avec [!UICONTROL Persistent Shopping Cart] activé.
* **ACSD-58141** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Correction du problème en raison duquel PHPSESSID se régénère sur les requêtes POST sur la zone de storefront pour un client connecté si le [!DNL L2 Redis cache] est activé et que le client est mis à jour à partir de l’administrateur.
* **ACSD-58352** (pour Adobe Commerce >=2.4.4 &lt;2.4.7) - Correction du problème où les libellés d’attribut de retour pour la vue de magasin par défaut sont renvoyés via l’API GraphQL lorsqu’une vue de magasin autre que la vue par défaut est spécifiée dans l’en-tête de la requête.
* **ACSD-58442** (pour Adobe Commerce >=2.4.4 &lt;2.4.7-p1) - Corrige le problème où les appareils d’une largeur de 768 px sont traités comme mobiles, ce qui entraîne le chargement du menu et de l’en-tête dans une vue mobile au lieu de bureau.
* **ACSD-58790** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige la fonctionnalité de pincement pour zoomer sur les images de la page des détails du produit en mode mobile sur [!DNL Chrome].
* **ACSD-59036** (pour Adobe Commerce et Magento Open Source >=2.4.7 &lt;2.4.8) - Correction d’une exception qui se produit lors du chargement des prix des produits avec des limites inférieure et supérieure égales à 0 $.
* **ACSD-59229** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel les informations relatives au groupe de clients sont enregistrées dans le mauvais segment en raison de l’ancienne valeur de X-Magento-Vary dans la requête.
* **ACSD-59378** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction du problème en raison duquel les réécritures d’URL au niveau du magasin sont incorrectement mises à jour lors de l’importation.
* **ACSD-59514** (pour Adobe Commerce >=2.4.4 &lt;2.4.7-p2) - Correction du problème en raison duquel les formulaires de la zone d’administration contenant [!DNL Page Builder] renvoient l’erreur *[!DNL Page Builder]s’affichait pendant 5 secondes sans libérer les verrous.* dans la console du navigateur après l’envoi du formulaire et les modifications ne peuvent pas être enregistrées.
* **ACSD-60303** (pour Adobe Commerce >=2.4.4-p9 &lt;2.4.5 || >=2.4.5-p8 &lt;2.4.6 || >=2.4.6-p6 &lt;2.4.8) - Correction du problème en raison duquel une commande de l’administrateur ne peut pas être passée si la minimisation HTML est activée.
* **ACSD-60441** (pour Adobe Commerce et Magento Open Source 2.4.4-p9) || 2.4.5-p8 || 2.4.6-p6 || 2.4.7-p1) - Correction du problème lié à la mise à jour des clients via `V1/customers` point d’entrée [!DNL REST API] lors de l’utilisation du jeton d’accès à l’intégration généré à partir du serveur principal.
* Correctifs mis à jour : ACSD-57003

## v1.1.49 {#v1-1-49}

* **ACSD-56979** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème de suppression des images de produit après la suppression d’une mise à jour d’évaluation.
* **ACSD-57086** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème de traitement incorrect des commandes passées à partir de sites web autres que ceux par défaut dont les conditions générales sont activées.
* **ACSD-57588** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel l’envoi d’une commande à plusieurs adresses déclenche une erreur lors du traitement de l’identifiant de la région.
* **ACSD-57643** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction d’un problème en raison duquel des produits dotés d’options personnalisées étaient incorrectement ajoutés au panier via GraphQL.
* **ACSD-57846** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel les produits GraphQL recherchés avec un filtre à prix zéro ne renvoient aucun résultat en raison d’une exception.
* **ACSD-57941** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème d’affectation incorrecte des options de produit à l’admin store plutôt qu’à leurs magasins respectifs.
* **ACSD-58375** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel une configuration de *[!DNL YouTube API Key]* incorrecte entraînait une erreur lors de l’ajout d’une vidéo [!DNL YouTube] au niveau de l’affichage du magasin.
* **ACSD-58739** (pour Adobe Commerce et Magento Open Source >=2.4.7 &lt;2.4.8) - Correction du problème en raison duquel la réindexation partielle génère une erreur.
* **ACSD-58446** (pour Adobe Commerce >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel, lors de la suppression d’une équipe avec des utilisateurs ou des équipes enfants, quel que soit leur statut (inactif), le système fournit un message d’erreur informatif incompatible avec l’interface utilisateur.
* **ACSD-58054** (pour Adobe Commerce >=2.4.4 &lt;2.4.6) - Correction du problème en raison duquel il est possible de générer des jetons client pour les clients inactifs via l’API.
* **ACSD-58163** (pour Adobe Commerce >=2.4.3 &lt;2.4.7) - Correction du problème où un *[!UICONTROL Cart Price Rule]* n’applique pas de remise pour un client invité du panier d’*[!UICONTROL Customer Segment]* correspondant sans code de coupon.
* **ACSD-57045** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel les réécritures d’URL provoquent un bouclage de page infini après la désactivation de la case *[!UICONTROL Website Root]* dans *[!UICONTROL Hierarchy]*.
* Correctifs mis à jour : ACSD-46815, ACSD-47027, ACSD-51683, ACSD-55031, ACSD-51819, ACSD-54965-v2

## v1.1.48 {#v1-1-48}

* **ACSD-55566** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème en raison duquel la mutation `mergeCart` échoue avec une « *Erreur de serveur interne* » dans la réponse [!DNL GraphQL] lors de la fusion des paniers source et de destination qui ont les mêmes éléments de lot.
* **ACSD-56546** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème d’affichage des produits configurables et groupés comme **En rupture de stock** sur le storefront lorsque l’**affichage de la configuration en rupture de produit** est *Désactivé*.
* **ACSD-56635** (pour Adobe Commerce >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel le client importé est dupliqué avec la même adresse e-mail, lorsqu’une importation est utilisée avec **partage de compte** défini sur *Global*.
* **ACSD-56741** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige le message d’erreur « *Tentative d’accès au décalage de tableau sur la valeur de type null* » qui s’affiche pendant le `setup:upgrade` lorsque la base de données contient un déclencheur [!DNL MySQL] personnalisé non lié au mécanisme d’indexation et à la [!DNL MView].
* **ACSD-57315** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige le problème lorsqu’une nouvelle transaction est créée dans [!DNL PayPal Payflow Pro] chaque fois que l’utilisateur clique sur le bouton [!UICONTROL Fetch] de l’écran **[!UICONTROL View transaction]** dans l’Administration.
* **ACSD-57337** (pour Adobe Commerce >=2.4.4 &lt;2.4.6) - Correction du problème en raison duquel un utilisateur administrateur avec des restrictions d’accès à des sites web spécifiques peut voir les sociétés de tous les sites web dans la grille de **[!UICONTROL Companies]**.
* **ACSD-57394** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige le problème de tri incorrect des produits par plusieurs champs de tri dans [!DNL GraphQL].
* **ACSD-57565** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel le tableau de bord **[!UICONTROL Order]** affiche des informations de commande incorrectes jusqu’à ce que la période soit mise à jour. Le tableau de bord affiche désormais les statistiques d’ordre correctes lors du premier chargement.
* **ACSD-57854** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème lorsque les requêtes de [!DNL GraphQL] de produit renvoyaient des catégories désactivées dans les agrégations de catégories.
* **ACSD-58008** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel la mise à jour d’une mise à jour planifiée supprimait la version précédente d’un élément intermédiaire, si aucune date de fin n’était spécifiée.
* Correctifs mis à jour : MDVA-39305-V2, ACSD-48627, ACSD-54965

## v1.1.47 {#v1-1-47}

* **ACSD-55241** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel les attributs *[!UICONTROL Used]* et *[!UICONTROL Times Used]* affichent des valeurs incorrectes pour les coupons générés lorsqu’ils sont utilisés lors du passage en caisse avec plusieurs adresses.
* **ACSD-56760** (pour Adobe Commerce >=2.4.6 &lt;2.4.7) - Correction du problème au cours duquel un utilisateur administrateur limité à un site web spécifique ne peut pas trier ou ajouter de nouveaux produits à l’intérieur d’une catégorie dans le cas où la boutique en ligne a sa propre catégorie racine.
* **ACSD-56858** (pour Adobe Commerce >=2.4.2 &lt;2.4.7) - Correction du problème d’affichage incorrect des autorisations des rôles de société B2B pour un administrateur d’entreprise restreint.
* **ACSD-57074** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel l’attribut personnalisé *Oui/Non* avec `attrbute_code` commençant par `price_` ne fonctionne pas correctement avec l’indexation et les produits dotés de ces attributs ne sont pas disponibles en front-end.
* Correctifs mis à jour : ACSD-53378, ACSD-51819

## v1.1.46 {#v1-1-46}

* **ACSD-46767** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème d’invalidation de la page de catégorie lorsque la quantité en stock change, même si le produit est toujours en stock.
* **ACSD-54656** (pour Adobe Commerce >=2.4.5 &lt;2.4.6) - Correction du problème d’échec de Recaptcha invisible lors du passage en caisse, empêchant le passage d’une commande.
* **ACSD-55100** (pour Adobe Commerce >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel GraphQL ne renvoie pas plus de 10 000 produits dans les résultats de recherche.
* **ACSD-56621** (pour Adobe Commerce >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel le prénom et le nom mis à jour ne sont pas reflétés dans la section d’en-tête des salutations pour l’utilisateur administrateur de la société.
* **ACSD-56842** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel les proxys différés et les fabriques de proxy différés sont manquants après l’exécution de `setup:di:compile`.
* **ACSD-57003** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel le statut de la commande est modifié en *[!UICONTROL Complete]* au lieu d’être modifié en *[!UICONTROL Processing]* lorsqu’une commande est partiellement remboursée et partiellement expédiée.
* Correctifs mis à jour : ACSD-50260-v2, ACSD-54966

## v1.1.45 {#v1-1-45}

* **ACSD-56886** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème de rupture de stock d’un produit configurable lorsque l’un des deux produits enfants est désactivé par une mise à jour planifiée.
* **ACSD-56616** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction du problème d’affichage des produits groupés en stock sur le storefront lorsque leurs produits simples sont en rupture de stock.
* **ACSD-56515** (pour Adobe Commerce >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel les administrateurs disposant d’autorisations au niveau du site web ne peuvent pas ajouter ni modifier un bloc dynamique.
* **ACSD-56447** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel l’ajout d’un même produit au panier via des requêtes d’API web REST parallèles génère deux éléments distincts dans le panier.
* **ACSD-56415** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel les performances de l’indexation partielle des prix sont ralenties en raison d’une requête `DELETE` lorsque la base de données contient de nombreuses données de prix partielles à indexer.
* **ACSD-54965** (pour Adobe Commerce >=2.4.5 &lt;2.4.6) - Correction du problème en raison duquel la grille de marchandisage visuelle n’affiche pas le stock correct lorsqu’un produit est affecté à un stock personnalisé uniquement.
* **ACSD-52824** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction du problème d’affichage des boutons PayPal Express, Google Pay et Apple Pay pour les clients d’entreprise lorsque ces modes de paiement sont désactivés dans les paramètres de l’entreprise.
* Correctifs mis à jour : ACSD-56193

## v1.1.44 {#v1-1-44}

* **ACSD-56790** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige le problème où un utilisateur est redirigé vers le tableau de bord d’administration lors du tri des produits de catégorie à l’aide de l’option **Déplacer les produits en rupture de stock vers le bas** et où l’erreur `Invalid security or form key. Please refresh the page` s’affiche en haut de l’écran.
* **ACSD-56280** (pour Adobe Commerce >=2.4.4 &lt;2.4.7) - Correction d’un problème en raison duquel la commande d’articles dans un registre des cadeaux entraînait une exception.
* **ACSD-56246** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème de suppression des données de l’attribut multi-sélection personnalisé lorsqu’une mise à jour planifiée d’un produit devient active.
* **ACSD-56193** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4) - Correction du problème en raison duquel le cache Vernis/Fastly n’est pas mis à jour lorsqu’un bloc planifié est utilisé dans la description de la catégorie à l’aide de Page Builder.
* **ACSD-56158** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel la requête « panier » renvoie la valeur fiscale totale pour chaque règle de taxe.
* **ACSD-56023** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel le contenu du widget n’est pas mis à jour sur la page CMS lorsque le cache est activé.
* **ACSD-55427** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel l’utilisateur administrateur ne peut pas annuler l’affectation d’un produit d’un catalogue partagé à partir de la page produit de l’interface utilisateur d’administration.
* **ACSD-55352** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel, après la création d’un avoir partiel avec des points de récompense client, le statut de la commande passe à Fermé et les options d’avoir disparaissent de la page de commande de l’administrateur.
* **ACSD-55231** (pour Adobe Commerce >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel vous ne pouvez pas ajouter de produits à un panier à l’aide de la fonctionnalité de commande rapide.
* **ACSD-54283** (pour Adobe Commerce >=2.4.3 &lt;2.4.4) - Correction du problème en raison duquel les produits/catégories non affectés au catalogue partagé pour la valeur par défaut (groupe général) sont toujours inclus dans le plan de site XML.
* Correctifs mis à jour : ACSD-52041, ACSD-54040, ACSD-51819

## v1.1.43 {#v1-1-43}

* **ACSD-54972** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel l’URL de catégorie canonique n’est pas mise à jour après avoir modifié l’URL de catégorie.
* **ACSD-53636** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.5) - Correction du problème en raison duquel le prix normal n’est pas affiché sur les pages de liste des produits pour les produits configurables qui ont des produits enfants avec des prix spéciaux.
* **ACSD-54885** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige le problème lié au passage en caisse de plusieurs adresses lorsque l’utilisateur administrateur utilise la fonctionnalité *Se connecter en tant que client*.
* **ACSD-55610** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel une commande partiellement annulée présente un montant de remise incorrect.
* **ACSD-55334** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Corrige les traductions de libellés via les dictionnaires de traduction dans la réponse GraphQL.
* **ACSD-54739** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel la condition de statut du stock de produits n’est pas appliquée aux règles de produits associées.
* **ACSD-53925** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel l’administrateur ne peut pas enregistrer le bloc CMS avec le carrousel de produit lorsque `catalog_product_price` mode dimensions est défini sur *site web*.
* **ACSD-52714** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel le filtre de date ne fonctionne pas dans la grille d’administration lorsque le format de date est défini sur *Y-m-d*.
* **ACSD-55055** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Améliore les performances de chargement des attributs de produit dans les règles de prix de panier dans le panier.
* **ACSD-53790** (pour Adobe Commerce >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel plusieurs RMA pour un seul produit peuvent être créés via l’API REST.
* **ACSD-56090** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.5) - Correction du problème en raison duquel la requête GraphQL répond avec les données de tous les magasins plutôt qu’avec les données du magasin spécifiquement demandées.
* **ACSD-54983** (pour Adobe Commerce >=2.4.2 &lt;2.4.7) - Corrige le problème en raison duquel il n’est pas possible d’obtenir l’UID de l’utilisateur de l’entreprise avec la requête GraphQL lorsque le statut de l’utilisateur est défini sur *[!UICONTROL Inactive]*.
* **ACSD-53309** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème d’application partielle de la taxe dans le libellé *[!UICONTROL Regular Price]* lorsque l’option personnalisable est sélectionnée.
* **ACSD-55305** (pour Adobe Commerce >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel la fenêtre contextuelle *[!UICONTROL Edit Company User]* de la page **[!UICONTROL myAccount]** > **[!UICONTROL Company Structure]** se fige avec un chargeur à l’écran.
* Correctifs mis à jour : ACSD-49013

## v1.1.42 {#v1-1-42}

* **ACSD-53658** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction d’un problème en raison duquel les données de *[!UICONTROL Recently Viewed]* produit ne sont pas correctement mises à jour dans la vue du magasin.
* **ACSD-54626** (pour Adobe Commerce >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel vous ne pouvez pas créer de règle de bon de commande (`createPurchaseOrderApprovalRule`) avec l’attribut `NUMBER_OF_SKUS` via [!DNL GraphQL].
* **ACSD-53845** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige le problème de délai d’expiration de la connexion [!DNL MySQL] lorsque `consumer max_messages` = 0.
* **ACSD-54890** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction du problème en raison duquel `aggregate_sales_report_bestsellers_data` provoque des erreurs [!DNL MySQL] dues au manque d’espace `/tmp` disque.
* **ACSD-55112** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction du problème en raison duquel il est possible de cliquer plusieurs fois sur le bouton *[!UICONTROL Submit review]* sans validation [!DNL Google reCAPTCHA v3].
* **ACSD-54264** (pour Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.7) - Correction du problème en raison duquel le message d’erreur *« Vous ne pouvez pas mettre à jour l’attribut demandé. ID de ligne : store_id »* s’affiche lorsqu’un client tente de passer en caisse avec un devis négociable provenant d’une autre vue de magasin.
* **ACSD-54418** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige le problème où un montant fixe de remise est incorrectement appliqué à chaque produit enfant du bundle à prix dynamique.
* **ACSD-55238** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correctifs enregistrant le *[!UICONTROL Meta Description]* de produit vide.
* **ACSD-54966** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel un code de coupon à utilisation limitée par client ne peut pas être réutilisé en cas d’échec de la commande précédente.
* **ACSD-54060** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème en raison duquel un administrateur restreint ne peut pas enregistrer un produit s’il est l’enfant d’un autre produit affecté à une portée différente.
* **ACSD-48910** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction d’un problème en raison duquel un produit groupé affecté à plusieurs sources est en rupture de stock après qu’une commande a été facturée et expédiée, même s’il contient toujours une quantité différente de zéro.
* **ACSD-55381** (pour Adobe Commerce >=2.4.2 &lt;2.4.7) - Corrige une erreur de serveur interne lors de l’interrogation de champs `configurable_product_option_uid` et `configurable_product_option_value_uid` depuis un *[!UICONTROL Requisition list]* [!DNL B2B] via [!DNL GraphQL].
* **ACSD-55628** (pour Adobe Commerce >=2.4.4-p2 &lt; 2.4.5 || >=2.4.5-p1 &lt; 2.4.6) - Correctifs du chargement d’un fichier sur le formulaire d’enregistrement de l’entreprise et du remplacement d’un fichier pour un attribut du client sur le storefront.
* Correctifs mis à jour : ACSD-51240, ACSD-51890, ACSD-53098

## v1.1.41 {#v1-1-41}

* **ACSD-54376** (pour Adobe Commerce >=2.4.2 &lt;2.4.7) - Corrige le problème qui se produit dans le panier lorsqu’un produit est supprimé du catalogue partagé après avoir déjà été ajouté au panier.
* **ACSD-53722** (pour Adobe Commerce >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel le prix des options de produit groupées passe à 0 $ lorsque les mises à jour planifiées pour différentes portées deviennent actives.
* **ACSD-53643** (pour Adobe Commerce >=2.4.3 &lt;2.4.7) - Correction du problème en raison duquel le total de la commande est incorrect lors de la passation d’une commande avec des produits désactivés ou en rupture de stock. Elle est corrigée en masquant le bouton *[!UICONTROL Place Order]* pour ces commandes fournisseur.
* **ACSD-54067** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction d’un problème qui empêchait la lecture d’une vidéo de produit sur un appareil mobile.
* **ACSD-55414** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Améliore les performances lorsque la base de données MariaDB tente de convertir le paramètre entity_id EAV de chaîne en entier.
* **ACSD-51819** (pour Adobe Commerce >=2.4.4 &lt;2.4.4-p4) - Correction du problème en raison duquel plusieurs commandes peuvent être passées avec le même ID de devis.
* **ACSD-53118** (pour Adobe Commerce >=2.4.0 &lt;2.4.7) - Correction du problème en raison duquel le *[!UICONTROL Cart Price Rule]* est appliqué à l’aide d’un code de coupon alors que le produit possède un attribut vide, ce qui aurait dû entraîner l’invalidation de la règle.
* **ACSD-54324** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel la requête requisition_lists de GraphQL ne prend pas en compte les paramètres de pagination et renvoie tous les résultats.
* Correctifs mis à jour : MDVA-42855-v2

## v1.1.40 {#v1-1-40}

* **ACSD-54680** (pour Adobe Commerce >=2.4.0 &lt;2.4.6) - Corrige le problème en raison duquel il n’est pas possible de traiter un devis B2B envoyé pour un produit avec plusieurs sources affectées.
* **ACSD-54040** (pour Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2.4.5-p4 &lt;2.4.6) - Corrige le problème où le champ *[!UICONTROL Created]* est vide dans les détails de commande lorsque les modules B2B sont activés.
* **ACSD-54319** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6) - Correction du problème en raison duquel le prix du produit affiche zéro dans le rapport de *[!UICONTROL Product in Cart]*.
* **ACSD-53378** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Améliore le temps de chargement des pages de passage en caisse pour les clients qui disposent de carnets d’adresses volumineux.
* **ACSD-52657** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel le mini-graphique n’est pas mis à jour sur le magasin secondaire qui utilise un sous-domaine.
* **ACSD-53414** (pour Adobe Commerce >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel un utilisateur administrateur restreint peut voir les pages CMS en dehors de sa portée d’autorisations.
* **ACSD-54472** (pour Adobe Commerce >=2.4.6 &lt;2.4.7) - Corrige le problème en raison duquel les clients d’une société refusée peuvent toujours s’authentifier et les clients d’une société bloquée et d’une société refusée peuvent toujours passer des commandes. Le correctif ajoute une validation supplémentaire pour les points d’entrée GraphQL.
* **ACSD-52801** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Ajoute l’option permettant d’effectuer une correspondance partielle lors de la recherche de produits dans GraphQL.
* **ACSD-55004** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige le problème en raison duquel le programme de validation se bloque lors du téléchargement d’un fichier d’importation dont la valeur est supérieure à la valeur configurée dans `php.ini`.
* **ACSD-54989** (pour Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.7) - Correction du problème en raison duquel un administrateur d’entreprise ne peut pas passer de commande lorsque *[!UICONTROL Enable Purchase Orders]* est défini sur *[!UICONTROL Yes]* et *[!UICONTROL Purchase Order]* sur *[!UICONTROL No]*.
* **ACSD-54007** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige l’erreur *« Clé de tableau non définie »_scope »* lors de l’importation de données client.
* **ACSD-55031** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Corrige l’erreur *Le type « mixte » ne peut pas être considéré comme une valeur nulle* lors de la compilation.
* **ACSD-54961** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction du problème en raison duquel un utilisateur administrateur restreint ne peut pas mettre à jour en masse le statut *Révision du produit*.
* **ACSD-55256** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel seule la première image s’affiche correctement dans le curseur d’image.
* Correctifs mis à jour : ACSD-52041, ACSD-54106

## v1.1.39 {#v1-1-39}

* **ACSD-53704** (pour Adobe Commerce >=2.4.0 &lt;2.4.7) - Correction d’un problème en raison duquel l’historique de solde des points de récompense est mal calculé après l’expiration des points de récompense.
* **ACSD-53583** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Améliore les performances de réindexation partielle pour les indexeurs *Produits de catégorie* et *Catégories de produits*.
* **ACSD-54026** (pour Adobe Commerce >=2.4.6 &lt;2.4.7) - Corrige un message d’erreur incorrect pour une requête `updateCompanyRole` GraphQL destinée à un utilisateur non autorisé.
* **ACSD-54106** (pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.5) - Corrige le problème en raison duquel le tri des produits de catégorie par nom pour les caractères accentués turcs est incorrect.
* **ACSD-52219** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel les grilles d’administration enregistrées par les filtres ne fonctionnent pas comme prévu lorsque vous basculez fréquemment entre les vues de signets.
* **ACSD-54342** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige un message d’erreur incorrect *Erreur dans la structure des données : les valeurs sont mélangées* lors de l’importation d’un fichier CSV sans données valides.
* **ACSD-54660** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Ajout d’un nouvel attribut d’entrée *sort* pour trier les commandes client dans GraphQL par `sort_field` et `sort_direction`.
* **ACSD-54776** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel les valeurs de champ de produit *[!UICONTROL Use Default Value]* et non par défaut non cochées ne sont pas enregistrées pour la deuxième vue de site web, de magasin et de magasin.
* **ACSD-53998** (pour Adobe Commerce et Magento Open Source >=2.4.4-p2 &lt;2.4.5 || >=2.4.5-p1 &lt;2.4.7) - Corrige le problème en raison duquel une **[!UICONTROL Dynamic Block]** basée sur une **[!UICONTROL Customer Segment]** ne fonctionne pas correctement après s’être déconnectée d’un compte client.
* **ACSD-53204** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correctifs *Le produit ne peut pas être enregistré.* erreur lors de requêtes simultanées d’ajout d’images à la galerie de produits à l’aide du point d’entrée `rest/V1/products/<sku>/media`.
* **ACSD-47657** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Ajout d’un mécanisme de mise en cache pour les informations d’identification AWS. Un fournisseur d’informations d’identification utilise désormais le cache de Magento pour mettre en cache les informations d’identification récupérées d’AWS pour la configuration EC2.
* Correctifs mis à jour : ACSD-51984, ACSD-51574.

## v1.1.38 {#v1-1-38}

* **ACSD-53098** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4) - Correction du problème en raison duquel les produits affectés à un catalogue partagé n’apparaissent pas sur le storefront lors de l’exécution d’un index partiel.
* **ACSD-54018** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.6) - Corrige les problèmes de performances avec le widget [!UICONTROL Product List] qui utilise un attribut non global dans la condition du widget.
* **ACSD-54111** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6) - Correction du problème en raison duquel les images miniatures des produits ne s’affichent pas sur le storefront lorsque les proportions de l’image du filigrane ne correspondent pas à l’image du produit.
* **ACSD-47669** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6) - Correctifs *Violation de contrainte d’intégrité : 1452 Impossible d’ajouter ou de mettre à jour une ligne enfant : échec d’une contrainte de clé étrangère* erreur lors de l’importation de produits CSV.
* **ACSD-53347** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel l’indexation des prix prend trop de temps à s’exécuter.
* **ACSD-52287** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction d’un problème lié à un statut de commande incorrect dans la grille de commande archivée lorsque l’indexation de grille asynchrone est activée.
* **ACSD-52929** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème lié aux requêtes redondantes pour réindexer les éléments sources par défaut lorsque l’indexeur d’inventaire est configuré en mode asynchrone.
* **ACSD-53824** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel `UpdateMultiselectAttributesBackendTypes` correctif de données de migration dépasse la limite de taille des transactions de la base de données lors de la `setup:upgrade`.

## v1.1.37 {#v1-1-37}

* **ACSD-52613** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème d’actualisation des caches et des index même si aucune mise à jour n’est apportée aux éléments `Inventory_source` par l’API REST.
* **ACSD-51884** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel le chemin d’accès au cache de l’image du produit devient incorrect après l’exécution de la commande de redimensionnement.
* **ACSD-53628** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel le rapport de commande client CSV affiche des caractères spéciaux incorrects.
* **ACSD-53148** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel deux requêtes parallèles dans GraphQL pour ajouter le même produit configurable au panier généraient deux articles distincts sur le panier avec le même SKU de produit.
* **ACSD-52606** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction du problème en raison duquel le message d’erreur *Votre commande n’est pas prête pour le retrait* s’affiche lorsque l’utilisateur clique sur **[!UICONTROL Notify Order is Ready for Pickup]**.
* **ACSD-51574** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige le problème en raison duquel l’image n’est pas mise à jour sur le front-end après l’avoir remplacée par une autre image portant le même nom.
* **ACSD-53728** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige le problème en raison duquel l’indexation de l’éditeur de texte enrichi du produit prend plus de temps.
* **ACSD-53979** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème JS qui se produit sur la page d’accueil si le message de bienvenue contient une apostrophe.
* **ACSD-52085** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel un produit configurable à un prix spécial n’est pas visible dans le carrousel du produit.
* **ACSD-53795** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction d’un problème lié à un type de données non valide dans `indexer_update_all_views` tâche cron.
* **ACSD-52143** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème de suppression des options personnalisées après l’importation du produit.
* **ACSD-53750** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige l’erreur *Canal rompu ou connexion fermée* lors de la réindexation de `catalog_product_price` multithread.
* **ACSD-49843** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.0 || >=2.4.1 &lt;2.4.7) - Correction d’un problème en raison duquel le lien de téléchargement du produit n’est pas disponible après la facturation automatique de l’article commandé par un mode de paiement en ligne avec le paramètre **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]** activé.
* **ACSD-47054** (pour Adobe Commerce >=2.4.2 &lt;2.4.6) - Correction du problème en raison duquel la réindexation de l’aperçu exécute la réindexation pour tous les magasins, ce qui entraîne un ralentissement.
* Ajout de nouvelles versions pour ACSD-46541, ACSD-47079.
* ACSD-49970-v3 remplacé par ACSD-54095.

## v1.1.36 {#v1-1-36}

* **ACSD-53239** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt; 2.4.6) - Correction du problème en raison duquel l’indexeur d’inventaire nettoie tous les caches en mode Mise à jour selon le calendrier.
* **ACSD-50887** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction du problème en raison duquel la *[!UICONTROL Use in Search Results Layered Navigation]* de la propriété d’attribut de produit peut être définie sur *Oui* sans que l’option de *[!UICONTROL Use in search]* ne soit définie sur *Oui*.
* **ACSD-51846** (pour Adobe Commerce et Magento Open Source >=2.4.3-p2 &lt;2.4.6) - Correction du problème *Erreur interne* qui se produit car tous les niveaux de la payload de l’API REST ne sont pas validés.
* **ACSD-52906** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel le cookie X-Magento-Vary est défini de manière incorrecte pour les clients connectés appartenant au même segment client, ce qui entraîne une mise en cache incorrecte de certaines pages.
* **ACSD-52736** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.6) - Correction d’un problème en raison duquel une *règle de prix de panier* qui inclut des exigences pour la quantité de produit configurable ne fonctionne pas comme prévu.
* **ACSD-47875** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel les utilisateurs administrateurs ne sont pas en mesure d’ajouter un produit à un panier client à partir de l’administration pour une portée d’affichage de magasin spécifique avec la gestion des stocks.
* **ACSD-53176** (pour Adobe Commerce >=2.3.7 &lt;2.4.5) - Correction du problème en raison duquel *Règle du produit associé* avec *est l’une des* conditions ne correspond pas aux produits.
* **ACSD-51666** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige l’erreur *La session a expiré, veuillez vous reconnecter.* qui se produit lorsqu’un client tente de se connecter.
* Ajout de nouvelles versions pour MDVA-39305-v2.
* Mise à jour des exigences pour ACSD-19640.

## v1.1.35 {#v1-1-35}

* **ACSD-51899** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction du problème en raison duquel l’adresse d’expédition par défaut à l’étape de passage en caisse est automatiquement renseignée avec une adresse de retrait en magasin sélectionnée précédemment.
* **ACSD-52041** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige le problème en raison duquel le message d’erreur *[ERROR] [!DNL Page Builder] s’affichait pendant 5 secondes sans libérer les verrous.* s’affiche dans le navigateur Chrome lors de l’enregistrement du contenu modifié avec [!DNL Page Builder].
* **ACSD-52095** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.6) - Correction d’un problème en raison duquel la valeur `manage_stock` était incorrectement définie sur 0 dans le fichier CSV après l’exportation du produit.
* **ACSD-51358** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel la suppression d’une mise à jour planifiée sans date de fin entraîne la suppression d’autres mises à jour planifiées pour la même entité.
* **ACSD-48070** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel la modification d’une mise à jour planifiée déclenche une exception.
* **ACSD-51890** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige le problème en raison duquel il est possible de cliquer plusieurs fois sur le bouton [!UICONTROL Submit review] sans [!DNL Google reCAPTCHA] validation v3.
* **ACSD-51984** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel les valeurs *[!UICONTROL Use Default Value]* et *[!UICONTROL non-default product field]* non cochées ne sont pas enregistrées pour la deuxième vue de site web, de magasin et de magasin.
* **ACSD-52398** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige l’erreur *La quantité demandée n’est pas disponible* qui se produit lors de la tentative de mise à jour de la quantité d’un produit groupé dans le panier sur le storefront.
* **ACSD-52786** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction du problème où une condition de règle de catalogue *SKU est* s’applique à tous les produits commençant par le SKU donné.
* **ACSD-52921** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel une erreur interne se produit lors de la demande des détails du panier à GraphQL lorsqu’un produit configurable en rupture de stock se trouve dans le panier.
* **ACSD-51683** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel une option personnalisable ne peut pas être ajoutée au panier à l’aide de GraphQL.
* **ACSD-52133** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige le problème en raison duquel un compte client ne peut pas être enregistré après une mise à niveau.
* **ACSD-52202** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème en raison duquel la quantité vendable du stock par défaut passe incorrectement à 0 lorsqu’un stock autre que le stock par défaut passe à 0 quantité lors de l’exécution de la commande.
* **ACSD-51265** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige le problème lié aux performances de réindexation `catalog_product_price` lorsqu’il y a trop de produits groupés dans le système.
* **ACSD-52831** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel les clients ne peuvent pas passer d’ordres de devis négociables lorsque l’[!DNL Google reCAPTCHA v3 Invisible] est activée.
* **ACSD-51845** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel les produits suivants avec des prix de niveau et différents jeux d’attributs ne peuvent pas être mis à jour via l’API REST en bloc asynchrone.
* **ACSD-52815** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel l’entrée du champ de quantité d’une source autre que celle par défaut ne prend en charge que 6 chiffres au maximum, contrairement à 8 pour un stock par défaut.
* **ACSD-51149** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel l’import-export planifié avec les autorisations de catalogue activées invalide les indexeurs, puis les vidages de cache par cron.
* **ACSD-50815** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction du problème en raison duquel la quantité décimale pour un produit simple ne peut pas être utilisée pour une nouvelle option de produit groupé.
* Versions mises à jour pour ACSD-47803.
* Titre mis à jour pour ACSD-51892.
* Mise à jour de l’ACSD-51379.
* Mise à jour d’ACSD-49970-v2.

## v1.1.34 {#v1-1-34}

* **ACSD-52277** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction d’un problème en raison duquel un utilisateur administrateur n’est pas redirigé correctement après avoir sélectionné une vue de magasin lors de la création d’une commande dans Admin.
* **ACSD-50813** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel l’administrateur n’était pas en mesure d’ajouter des produits groupés contenant une barre oblique dans le SKU avec la fonctionnalité [!UICONTROL Add Products by SKU] à la commande d’administration.
* **ACSD-51630** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème en raison duquel un grand nombre de messages système ralentit le téléchargement des pages d’administration.
* **ACSD-51853** (pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.7) - Correction du problème en raison duquel les styles de texte copiés ne sont pas appliqués lors de l’utilisation de l’[!UICONTROL Page Builder].
* **ACSD-52160** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction d’un problème en raison duquel le résultat de validation du produit par rapport à la règle de prix du panier n’était pas correctement évalué en fonction de la condition de règle « Si un article est TROUVÉ/INTROUVABLE dans le panier avec Toutes/Toutes ces conditions sont vraies ».
* **ACSD-51636** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel l’administrateur de la société ne peut pas ajouter de nouveaux utilisateurs à partir de la section compte client bien qu’il dispose de tous les rôles et autorisations nécessaires.
* **ACSD-51739** (pour Adobe Commerce >=2.4.6 &lt;2.4.7) - Corrige le problème où une erreur est renvoyée lorsque l’`structure_id` est demandée dans une requête CompanyTeam GraphQL.
* **ACSD-51857** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction du problème en raison duquel la lenteur des performances du rapport `aggregate_sales_report_bestsellers_data` cron sur les tables de base de données sales_order et `sales_order_item` volumineuses était due à la manière dont la requête de données principale a été écrite.
* **ACSD-48448** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige le problème en raison duquel un problème de condition de concurrence se produit lors des annulations de commande, ce qui entraîne une entrée dupliquée dans la table `inventory_reservation`.
* **ACSD-52689** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.6) - Correction du problème en raison duquel les images ne peuvent pas être chargées vers le stockage Amazon S3 à l’aide de l’API REST.
* **B2B-2674** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Ajoutez une fonctionnalité de mise en cache à la requête GraphQL 1customAttributeMetadata1.
* Ajout de nouvelles versions pour ACSD-44938.
* Ajout d’exigences pour ACSD-46988.

## v1.1.33 {#v1-1-33}

* **ACSD-50478** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.5) - Corrige la commande de restauration de la base de données pour un cas où l’image mémoire de la base de données contient des déclencheurs et une commande SQL *délimiteur*.
* **ACSD-50512** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Corrige le *Erreur : le lien téléchargeable n’est pas associé au produit. Vérifiez le lien et réessayez.* erreur qui se produit lors de la mise à jour de la date de début d’une mise à jour d’évaluation de produit téléchargeable.
* **ACSD-50949** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel le filtre de prix dans la recherche avancée ne renvoie pas les résultats appropriés lorsqu’il est utilisé avec le filtre de SKU.
* **ACSD-51645** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige l’erreur générée lors de l’enregistrement d’une nouvelle règle de prix de panier si le `Magento_OfflineShipping` d’extension est désactivé.
* **ACSD-50895** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel les balises [!DNL Google Analytics] 3 GTM ne sont pas déclenchées si [!DNL Google Analytics] 4 GTM n’est pas configuré.
* **ACSD-51102** (pour Adobe Commerce >=2.4.2 &lt;2.4.7) - Corrige le problème où une règle de catalogue appliquée à un grand nombre de produits n’est pas correctement indexée lorsque la règle est activée par une mise à jour planifiée.
* **ACSD-50368** (pour Adobe Commerce et Magento Open Source >= 2.4.3 &lt;2.4.5) - Correction du problème en raison duquel le `group_id` du client est ignoré lors de la création d’un client via l’API Async REST ou l’API Async Bulk REST.
* **ACSD-51497** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7) - Correction du problème en raison duquel un client ne peut pas trier une page de catalogue par attribut personnalisé de type liste déroulante.
* **ACSD-51408** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt; 2.4.7) - Corrige le problème en raison duquel le statut de l’élément de commande est incorrectement défini sur *[!UICONTROL Backordered]*.
* **ACSD-51735** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.5) - Corrige le problème en raison duquel le statut de l’élément de commande est incorrectement défini sur *[!UICONTROL Ordered]* lorsque le stock de produits est *0*.
* **ACSD-51792** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction du problème en raison duquel une page ne comporte pas d’événement d’impression lorsque la [!DNL Google Tag Manager] 4 est activée.
* **ACSD-51471** (pour Adobe Commerce >=2.4.3 &lt;2.4.7) - Correction du problème en raison duquel un utilisateur administrateur ne peut pas enregistrer une mise à jour planifiée pour un produit groupé qui utilise un produit simple disposant lui-même d’une mise à jour planifiée.
* **ACSD-51700** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Corrige l’erreur qui se produit lors du changement de vue de la boutique sur une page de modification de produit téléchargeable dans l’administration.
* **ACSD-51120** (pour Adobe Commerce >=2.3.7 &lt;2.4.3) - Correction du problème en raison duquel le cache des demandes GraphQL GET n’est pas effacé pour les pages CMS contenant des blocs CMS mis à jour par le biais d’une mise à jour d’évaluation.
* **ACSD-51240** (pour Adobe Commerce >=2.4.4 &lt;2.4.6) - Corrige le problème en raison duquel le fichier chargé est manquant si l’enregistrement est effectué via le formulaire d’enregistrement de la société.
* **ACSD-51907** (pour Adobe Commerce >=2.4.2 &lt;2.4.3) - Correction du problème en raison duquel un utilisateur administrateur restreint ne peut pas créer d’avoir avec remboursement hors ligne.
* **ACSD-52148** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.4) - Correction du problème en raison duquel la connexion de l’administrateur [!DNL Google V3 reCAPTCHA] échoue parfois.
* **ACSD-51431** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel un statut d’indexeur *fonctionne* même s’il n’existe aucune nouvelle entrée dans le journal des modifications.
* **ACSD-51892** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige le problème de performances en raison duquel les fichiers de configuration se chargent plusieurs fois.
* ACSD-51114 obsolète.

## v1.1.32 {#v1-1-32}

* **ACSD-49628** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel les [!UICONTROL Page Builder's] erreurs multiples empêchent l’administrateur d’enregistrer un produit sans autorisations de contenu.
* **ACSD-51305** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel les produits enfants configurables en rupture de stock ne sont pas disponibles dans la réponse de GraphQL.
* **ACSD-50621** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel les [!UICONTROL Tier Prices] des différents sites web du catalogue partagé ne sont pas visibles lors de la tentative de modification dans un environnement multi-site.
* **ACSD-51041** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.0 || >=2.4.1 &lt;2.4.6) - Améliore les performances de l’indexeur des prix.
* **ACSD-51379** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel les modifications apportées au contenu textuel de la page via [!UICONTROL Page Builder] ne sont pas enregistrées.
* **ACSD-49480** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème en raison duquel une seule règle de prix de panier est appliquée au panier.
* **ACSD-51230** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction du problème de suppression du compte de carte cadeau lorsqu’un remboursement partiel d’un produit simple est traité à partir d’une commande.
* **ACSD-51238** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème de suppression de la source d’inventaire lors de la mise à jour de produits configurables et de la modification du prix.
* **ACSD-50794** (pour Adobe Commerce >=2.4.1 &lt;2.4.7) - Correction d’un problème en raison duquel les informations sur le message cadeau ou l’emballage du cadeau ne sont pas mises à jour dans la base de données lors de sa suppression via GraphQL.
* **ACSD-51528** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel la colonne *x_forwarded_for* contient des valeurs nulles dans la table *sales_order*.
* **ACSD-50849** (pour Adobe Commerce >=2.4.4 &lt;2.4.6) - Corrige le problème en raison duquel l’ajout d’un nouveau produit à la catégorie après l’effacement du cache entraîne une incohérence des positions et des sélections des produits existants.
* **ACSD-51294** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel le prix, la quantité, les taxes, l’expédition et les recettes GTM/GA sont envoyés sous forme de chaîne à [!DNL Google Analytics] et GTM.
* **ACSD-51204** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème en raison duquel un produit entièrement vendu ne revient pas en stock après la création d’un avoir.
* **ACSD-51291** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.4-p4 || >=2.4.5 &lt;2.4.5-p3) - Correction du problème où un administrateur restreint ayant accès à un site web peut ajouter des images/vidéos au produit affecté à plusieurs sites web.
* Ajout de nouvelles versions pour ACSD-50336.
* Correctifs ACSD-49970 remplacés.

## v1.1.31 {#v1-1-31}

* **ACSD-50345** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4 || >=2.4.4-p1 &lt;2.4.6) - Correction du problème en raison duquel Recaptcha v2 ne se recharge pas après l’envoi d’un paiement en échec.
* **ACSD-50817** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Optimise les `sales_clean_quotes` de tâche Cron pour une exécution plus rapide.
* **ACSD-49392** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7) - Correction du problème en raison duquel le statut de la commande passe à Clôturé après un remboursement partiel pour un produit groupé.
* **ACSD-51036** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.5) - Correction du problème en raison duquel les conditions de concurrence lors d’appels simultanés de l’API REST entraînent un remplacement des informations de statut d’expédition dans la table [!UICONTROL Items Ordered].
* **ACSD-50858** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Améliore les performances pour le chargement des contenus de bannières.
* Ajout de nouvelles versions pour MDVA-39305-v2, ACSD-45169.
* Mise à jour des correctifs ACSD-50260-v2.

## v1.1.30 {#v1-1-30}

* **ACSD-50336** (pour Adobe Commerce et Magento Open Source >=2.4.4-p1 &lt;2.4.4-p3) - Correction du problème en raison duquel les e-mails d’alerte produit ne sont pas envoyés lorsqu’un produit est de nouveau en stock ou que le prix est modifié.
* **ACSD-50367** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel l’exportation de l’adresse du client ne fonctionne pas lorsqu’un attribut d’adresse du client à sélection multiple sans valeurs est créé.
* **ACSD-49877** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel la lecture automatique de la vidéo ne fonctionne pas sur les [!DNL Safari] mobiles lorsque la vidéo est directement liée à un fichier vidéo distant et non à un service de streaming.
* **ACSD-50165** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige l’erreur *Le fichier ne peut pas être supprimé. Avertissement!unlink: aucun fichier ou répertoire de ce type* lors du vidage du cache JS/CSS de l’administrateur.
* **ACSD-49737** (pour Adobe Commerce et Magento Open Source >=2.4.1-p1 &lt;2.4.7) - Correction du problème en raison duquel un coupon est incorrectement marqué comme utilisé après un échec de paiement par carte.
* **ACSD-50814** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel un utilisateur administrateur n’est pas en mesure de créer un avoir.
* **ACSD-50116** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel un utilisateur administrateur ne peut pas créer de réécriture d’URL pour les sous-catégories de niveau 3 ou inférieur.
* **ACSD-49513** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.5) - Correction du problème d’échec de la synchronisation du stockage distant en raison de fichiers de 0 octet.
* **ACSD-46683** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige le problème en raison duquel le prix d’expédition indique *Pas encore calculé*.
* **ACSD-49129** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6) - Correction du problème en raison duquel l’attribut *[!UICONTROL content]* (code d’image base64) n’est pas renvoyé dans les réponses de l’API de médias du produit `rest/V1/products/sku/media`.
* **ACSD-50276** (pour Adobe Commerce >=2.4.0 &lt;2.4.7) - Correction du problème en raison duquel le formulaire d’enregistrement du client ne fonctionne pas sur le storefront si un attribut client à sélection multiple est créé.
* **ACSD-50527** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Corrige l’erreur qui se produit lors de l’enregistrement d’une page avec un bloc dynamique vide.
* **ACSD-49973** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.5) - Améliore les performances de récupération des produits groupés via GraphQL.
* **ACSD-51114** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème en raison duquel un produit aléatoire disparaît des catalogues volumineux lorsque l’indexation asynchrone est activée. Amélioration des performances de la réindexation asynchrone pour les catalogues volumineux.
* **B2B-2598** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Ajoutez une fonctionnalité de mise en cache aux requêtes [!UICONTROL availableStores], [!UICONTROL countries], [!UICONTROL country], [!UICONTROL currency] et [!UICONTROL storeConfig] GraphQL.
* Ajout de nouvelles versions pour MDVA-42806, ACSD-48627, ACSD-46815.
* Mise à jour des métadonnées des correctifs pour ACSD-49773, ACSD-47179, ACSD-48300.

## v1.1.29 {#v1-1-29}

* **ACSD-49389** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige le problème en raison duquel un e-mail prêt à être récupéré est envoyé par l’API lorsque la commande n’est pas prête à être récupérée.
* **ACSD-49822** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel les mises à jour de la page [!UICONTROL Requisition List] ne sont pas répercutées sur le [!UICONTROL Print Requisition List].
* **ACSD-48771** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème lié à la mise à niveau du type de contenu du bloc de colonne à partir des versions [!DNL Page Builder] plus anciennes.
* **ACSD-49464** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel les factures, les expéditions et les avoirs ne sont pas retirés de l’archive lorsque l’orderId est différent.
* **ACSD-49773** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6) - Correction du problème en raison duquel l’exportation du produit échoue lorsque AWS S3 est utilisé comme stockage distant.
* **ACSD-49748** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Corrige le problème en raison duquel les invitations ne peuvent pas être envoyées.
* **ACSD-49502** (pour Adobe Commerce >=2.4.3 &lt;2.4.7) - Correction d’un problème en raison duquel le lien téléchargeable n’est pas correctement mis à jour après l’application d’une mise à jour d’évaluation au produit téléchargeable.
* **ACSD-49527** (pour Adobe Commerce >=2.4.2 &lt;2.4.7) - Corrige le problème d’affichage incorrect de la pagination des rôles d’entreprise GraphQL.
* **ACSD-49706** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel la valeur par défaut est enregistrée pour un attribut d’échantillon visuel lorsqu’aucune valeur n’est sélectionnée.
* **ACSD-49835** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Corrige le problème en raison duquel la valeur de la case à cocher Utiliser par défaut n’est pas enregistrée correctement au niveau du magasin pour un attribut à sélection multiple.
* **ACSD-49898** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème en raison duquel la grille de produits renvoie une exception lorsqu’un produit groupé a un prix spécial qui dépasse 1 000.
* **ACSD-50234** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.5) - Correction d’un problème lié à un nom de client incorrect dans l’e-mail de confirmation lors de la commande auprès de [!DNL PayPal].
* **ACSD-49960** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel le filtrage par date ne fonctionne pas pour la grille de commandes client.
* **ACSD-49849** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.6) - Correction du problème où l’e-mail du client était remplacé par [!DNL PayPal] e-mail lors de la commande avec [!DNL PayPal Express] via GraphQL.
* **ACSD-49839** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel la tarification et la structure du catalogue partagé génèrent une erreur dans l’administration lorsque les produits comportent des guillemets simples ou doubles dans le SKU.
* **ACSD-49970** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction d’une gestion incorrecte des erreurs GraphQL lorsque la création de rapports [!DNL New Relic] est activée.
* **ACSD-50260** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel les résultats de recherche de produits GraphQL sont limités à 10 000 résultats uniquement.
* **ACSD-48813** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème en raison duquel la recherche n’affiche pas de résultats pertinents en fonction du poids de recherche des attributs.

## v1.1.28 {#v1-1-28}

* **ACSD-48204** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.3) - Correction du problème en raison duquel une règle de prix de catalogue créée en fonction de l’attribut Oui/Non ne prend pas en compte la portée sélectionnée.
* **ACSD-47704** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel le produit groupé affichait uniquement le prix des produits en stock.
* **ACSD-49370** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige le problème en raison duquel l’attribut de produit *Date et heure* est de type *FilterMatchTypeInput* dans le schéma GraphQL.
* **ACSD-48807** (pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.7) - Correction du problème en raison duquel les évaluations des produits client ne sont pas filtrées par storeview via GraphQL.
* **ACSD-49433** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème en raison duquel le montant par défaut s’affiche sous la forme d’un sous-total dans le panier pour la carte cadeau avec un montant ouvert.
* **ACSD-48866** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème qui se produit lorsqu’une erreur se produit lors de la demande d’un flux RSS pour des catégories.
* **ACSD-48784** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige le problème en raison duquel les prix des segments de clients sont incorrectement mis en cache entre les groupes de clients.
* **ACSD-48857** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème en raison duquel un utilisateur ne peut pas enregistrer les modifications après les avoir modifiées avec Page Builder.
* **ACSD-49065** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel les éléments de devis ne sont pas visibles dans l’administration s’ils sont uniquement affectés au stock personnalisé.
* **ACSD-49179** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel le rapport Commandes affiche des montants incorrects en cas de devises différentes pour différents magasins.
* **ACSD-49286** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème en raison duquel un produit est ajouté deux fois à un panier lorsque plusieurs widgets de produit sont présents sur la page.
* **ACSD-49574** (pour Adobe Commerce >=2.4.4 &lt;2.4.7) - Ajoute des fonctionnalités pour prendre en charge les mises à jour des produits de cartes-cadeaux dans un panier via GraphQL.
* Correctif mis à jour : ACSD-48694.

## v1.1.27 {#v1-1-27}

* **ACSD-48362** (pour Adobe Commerce >=2.4.1 &lt;2.4.7) - Correction du problème en raison duquel l’adresse d’expédition par défaut est utilisée au lieu d’une nouvelle adresse lors de la commande avec un devis négociable.
* **ACSD-48059** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel les commerçants ne peuvent pas enregistrer le « [!UICONTROL Match product by rule] » dans la catégorie.
* **ACSD-48216** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7) - Correction du problème en raison duquel la [!UICONTROL AUTO_INCREMENT] de la table [!UICONTROL inventory_source_item] augmente lors de l’opération de [!UICONTROL UPDATE].
* **ACSD-47908** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7) - Corrige l’erreur « Une valeur inférieure ou égale à 0 est attendue » lors de la sélection de la source et de la quantité à l’étape d’expédition lors du passage en caisse.
* **ACSD-49497** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.6) - Corrige le problème où une commande reste en état de traitement après l’expédition et où un remboursement partiel est appliqué.
* **ACSD-48694** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.1 &lt;2.4.7) - Corrige le problème en raison duquel l’erreur « Changement d’état non valide demandé » empêche un client de passer une commande.
* **ACSD-49013** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction d’un problème en raison duquel les paramètres régionaux des e-mails de confirmation ne sont pas traduits dans les paramètres régionaux du site web lors de la création de clients à l’aide de l’API en bloc.
* **ACSD-48164** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel un administrateur restreint ne peut pas enregistrer de valeur au niveau du site web.
* **ACSD-48404** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.4) - Correction du problème en raison duquel « Mémoriser la pagination de catégorie = Oui » provoque une erreur lors de l’appui sur le bouton Précédent du navigateur.
* **ACSD-48634** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige les erreurs JS sur une page de mise à jour d’évaluation lorsque « [!UICONTROL Google Analytics Content Experiments] » est activé.
* **ACSD-49042** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.5) - Corrige le problème en raison duquel un produit avec une commande en souffrance infinie ne peut pas être commandé depuis Storefront.
* Correctifs mis à jour : ACSD-48366, ACSD-48661.

## v1.1.26 {#v1-1-26}

* **ACSD-47937** (pour Adobe Commerce et Magento Open Source 2.4.4) || >=2.4.5 &lt;2.4.6) - Correction du problème où les notifications de baisse de prix ne sont pas toujours envoyées en raison de la mise en cache au niveau de l’application.
* **ACSD-48661** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel si la limite de crédit de la société est supérieure à 999, le séparateur par virgules empêche l’enregistrement de la société en raison d’une erreur de validation.
* **ACSD-48773** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel le modèle d’e-mail de points de récompense est extrait du mauvais magasin.
* **ACSD-48587** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel les caractères spéciaux HTML dans les règles de correspondance du widget de produits ne leur permettent pas d’afficher les produits correspondants.
* **ACSD-48212** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.6) - Correction du problème en raison duquel l’importation du produit affecte le produit à une source incorrecte.
* **ACSD-47988** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.6) - Correction du problème en raison duquel l’exportation du produit efface les balises HTML de la description du produit page builder.
* **ACSD-48366** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction d’un problème en raison duquel l’image du produit ne s’affichait pas sur le modèle d’e-mail Retour à la création de stock.
* **ACSD-48417** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème d’apparition d’une erreur SQL après la création d’une modification de planning pour un produit et l’enregistrement d’un autre produit.

## v1.1.25 {#v1-1-25}

* **ACSD-48058** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction du problème en raison duquel la réindexation du prix des produits ne fonctionne pas si le produit groupé n’est affecté à aucun site web.
* **ACSD-48262** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction du problème en raison duquel les produits ne sont pas visibles sur le serveur frontal lorsque le paramètre « Autoriser tous les produits par page » est défini sur Oui.
* **ACSD-48293** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4) - Corrige le problème de rupture de stock des produits composites lorsque les produits enfants qui ont été vendus sont retournés en stock.
* **ACSD-47520** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel les clients perdent des points de récompense lors de la création d’un avoir.
* **ACSD-48044** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.4) - Corrige le problème en raison duquel l’application de plusieurs cartes-cadeaux à une seule commande avec expédition multiple empêche le passage de commandes.
* **ACSD-48300** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel il est impossible de créer un retour si le produit configurable est supprimé.
* **ACSD-47910** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Corrige le problème des commandes, factures, expéditions et avoirs manquants dans les grilles d’entité respectives.
* **ACSD-47292** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème en raison duquel les produits en rupture de stock ne sont pas disponibles dans la réponse de GraphQL si l’option « Afficher les produits en rupture de stock » est définie sur Oui.
* **ACSD-48234** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction du problème en raison duquel le résultat de la recherche catalogue affiche un nombre d’éléments de catégorie incorrect lorsque l’option « Afficher les éléments en rupture de stock » est activée.
* **ACSD-48313** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.5) - Correction du problème en raison duquel la colonne « configurable_variations » n’est pas analysée si la valeur de l’attribut contient une virgule. Le même algorithme d’analyse est utilisé pour « additional_attributes ».
* **ACSD-48627** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction du problème en raison duquel le produit configurable en rupture de stock provoquait une erreur lors de l’envoi d’une requête GraphQL pour obtenir les détails du panier.
* Mise à jour du correctif : MDVA-39384.

## v1.1.24 {#v1-1-24}

* **ACSD-45168** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6) - Correction du problème en raison duquel les URL compatibles avec les moteurs de recherche ne sont pas générées pour les produits dont les attributs *url_key* sont remplacés au niveau de la vue du magasin.
* **ACSD-46865** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème en raison duquel la grille Expédition et Avoir n’est pas renseignée lorsque l’indexation asynchrone est activée.
* **ACSD-47004** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6) - Correction d’un problème en raison duquel la TVA n’est pas appliquée à une adresse de facturation sans numéro de TVA.
* **ACSD-47803** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème d’affichage des échantillons de produits configurables en rupture de stock.
* **ACSD-47137** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Améliore la vitesse de chargement de la galerie d’images lorsque le dossier pub/media est très volumineux.
* **ACSD-46770** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème d’envoi des e-mails de commande de l’administrateur même lorsque la case *Confirmation de commande par e-mail* n’est pas cochée.
* **ACSD-47955** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Corrige le problème en raison duquel GraphQL n’affiche pas correctement la remise du panier.
* **ACSD-46617** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel le bouton *Continuer la récupération* est grisé même si le sous-total est supérieur au *Montant minimum de commande* configuré.
* **ACSD-47079** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.5) - Correction du problème en raison duquel l’état du stock des produits composites (groupés, et configurables) n’est pas mis à jour lorsque l’état du stock des sous-produits change via l’API REST POST /rest/V1/inventory/source-items.
* **ACSD-47336** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correctifs *Un problème est survenu.* erreur lors de l’ignorance des notifications dans Commerce Admin.
* **ACSD-47559** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige le problème en raison duquel la zone Prévisualiser le modèle d’e-mail n’est pas entièrement visible.
* **ACSD-47920** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel des commandes peuvent être passées via l’API Rest en tant qu’utilisateur invité, même si l’option *Autoriser le passage en caisse des invités* est désactivée.
* Correctifs remplacés : MDVA-39305, MDVA-42855.

## v1.1.23 {#v1-1-23}

* **ACSD-47179** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel un administrateur disposant d’un accès restreint à une portée spécifique ne peut pas supprimer les révisions de produit.
* **ACSD-47107** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.5) - Correction du problème en raison duquel la remise de la règle de prix de catalogue est appliquée aux options de produits personnalisés.
* **ACSD-47232** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel les coupons avec des conditions de poids total ne peuvent pas être appliqués dans l’administration.
* **ACSD-46519** (pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.6) - Correction du problème en raison duquel la requête categoryList de GraphQL renvoie un product_count incorrect pour une catégorie d’ancrage.
* **ACSD-47027** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6) - Corrige une demande de GraphQL updateCompanyRole lente.
* **ACSD-47666** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel la fonction de filtrage ne fonctionne pas dans la grille Admin > Système > Autorisations > Rôles utilisateur > un rôle > Rôles utilisateurs .
* **ACSD-47497** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige le problème en raison duquel l’onglet Services n’est pas visible dans la Configuration sous l’Administration.
* Correctif mis à jour : ACSD-47743.
* Correctifs remplacés : MDVA-42807.

## v1.1.22 {#v1-1-22}

* **ACSD-47444** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.3) - Corrige l’erreur _Tentative d’accès au décalage de tableau sur une valeur de type bool_ lors de l’accès à certains chemins de catégorie non existants pour des produits connus sur PHP 7.4.
* **ACSD-47332** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel cron échoue avec une erreur qui n’est signalée que lors de l’exécution entre 00:00 et 00:59 UTC.
* **ACSD-47280** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige le problème en raison duquel la désactivation de la fonctionnalité de catalogue partagé sur une portée spécifique ne fonctionne pas correctement.
* **ACSD-47106** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème en raison duquel une valeur ne peut pas être enregistrée dans un nouvel attribut personnalisé sur une page de création d’entreprise.
* Correctif mis à jour : ACSD-45143.

## v1.1.21 {#v1-1-21}

* **ACSD-46809** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6) - Corrige le problème où un utilisateur ou une utilisatrice reçoit une erreur lors de l’affectation d’un grand nombre de sources de produits.
* **ACSD-46856** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Améliore les performances en mettant à jour les prix par niveau via Système > Configuration > Importer > Tarification avancée.
* **ACSD-46541** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.4) - Correction du problème en raison duquel un utilisateur administrateur ne peut pas créer d’avoir si un élément de commande est supprimé.
* **ACSD-46581** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel le total de taxe estimé n’est pas mis à jour après la sélection d’un pays dans le panier.
* **ACSD-46618** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel le widget Liste de produits affiche des prix mis en cache incorrects pour un client connecté.
* **ACSD-46674** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème d’affichage des options personnalisées d’un type d’image sous forme d’HTML dans les e-mails des clients.
* **ACSD-46988** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème en raison duquel la requête de l’API « currency » de GraphQL renvoie des valeurs NULL pour une devise personnalisée.
* **ACSD-47076** (pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.5) - Correction du problème en raison duquel les vidéos Vimeo ne peuvent pas être lues sur le storefront.
* **ACSD-45071** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4) - Correction du problème en raison duquel la source par défaut est ajoutée au produit lors de l’importation.
* **AC-3023** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Mettez à jour le schéma DHL vers la dernière version 10.0.
* Correctifs mis à jour : MDVA-42584.
* Correctifs remplacés : MDVA-36572, ACSD-45241.

## v1.1.20 {#v1-1-20}

* **ACSD-46520** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.5*) - Corrige le problème en raison duquel un utilisateur obtient un statut de commande incorrect lorsqu’il est remboursé à l’aide du crédit de magasin.
* **ACSD-46703** (*pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6*) - Corrige le problème en raison duquel il n’est pas possible de glisser-déposer des options personnalisées sur une page de modification du produit.
* **ACSD-44851** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6*) - Corrige le problème en raison duquel une catégorie comportant des sous-catégories ne peut pas s’ouvrir ni se développer.
* **ACSD-46815** (*pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6*) - Corrige le problème en raison duquel la requête d’arborescence de catégories est limitée à 20 catégories.
* **ACSD-45675** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6*) - Corrige le problème en raison duquel l’exportation du produit utilise des noms de catégorie de la portée *Affichage du magasin par défaut*.
* **ACSD-46869** (*pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6*) - Corrige le problème où un produit configurable dans un panier n’est pas mis à jour via une requête *API REST PUT* sans modifier la quantité de produit.
* **MDVA-42768-V2** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.3*) - Corrige le problème en raison duquel le prix normal d’un produit configurable est de *0* lorsque *Afficher en rupture de stock* est *Oui*.
* Correctifs mis à jour : MDVA-44562, ACSD-46213, MDVA-41305, MDVA-38346, MDVA-13203.
* Correctif obsolète : MDVA-42768.

## v1.1.19 {#v1-1-19}

* **ACSD-46213** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.3*) - Corrige le problème en raison duquel la requête d’arborescence de catégories est limitée à 20 catégories.
* **ACSD-45781** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.2*) - Corrige le problème en raison duquel le champ de recherche front-end du magasin n’est pas affiché sur les appareils mobiles.
* **ACSD-46192** (*pour Adobe Commerce et Magento Open Source >=2.3.6 &lt;2.4.5*) - Corrige le problème lié à l’utilisation du point d’entrée `async/bulk/V1/configurable-products/bySku/options`.
* **ACSD-46404** (*pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.5*) - Corrige le problème en raison duquel un utilisateur administrateur ne peut pas se connecter après la mise à niveau vers la version 2.4.4.
* Correctifs mis à jour : MDVA-41305, MDVA-38626, MDVA-38728, MDVA-41061-V4, MDVA-42269, MDVA-39305.

## v1.1.18 {#v1-1-18}

* **ACSD-45817** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige le problème où une mutation de produit GraphQL pour un magasin spécifique renvoie toutes les variantes configurables, y compris celles qui ne sont pas affectées au magasin demandé.
* **ACSD-46146** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.6*) - Corrige le problème en raison duquel deux e-mails de confirmation de commande sont envoyés après avoir passé une commande auprès de l’administrateur.
* **ACSD-45255** (*pour Adobe Commerce >=2.4.3 &lt;2.4.6*) - Corrige une exception sur la page Rapport sur les stocks faibles pour un utilisateur administrateur restreint.
* **ACSD-45488** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6*) - Corrige le problème où un produit configurable avec plusieurs sources n’est pas automatiquement renvoyé à In Stock.
* **ACSD-45754** (*pour Adobe Commerce et Magento Open Source >=2.3.1 &lt;2.4.6*) - Correction du problème en raison duquel les points de récompense ne sont pas ajoutés après l’application d’un coupon au panier.
* **ACSD-45849** (*pour Adobe Commerce >=2.4.3 &lt;2.4.4*) - Corrige le problème de perte des métadonnées vidéo après l’application d’une mise à jour d’évaluation.
* **ACSD-45257** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;2.4.4*) - Corrige le problème en raison duquel GraphQL n’affiche pas correctement la remise du panier.
* **ACSD-44938** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.4*) - Corrige le problème en raison duquel l’`VAT_ID` ne peut pas être appliquée dans une requête GraphQL pour un utilisateur invité.
* Correctifs mis à jour : MDVA-43417.

## v1.1.17 {#v1-1-17}

* **ACSD-45241** (*pour Adobe Commerce et Magento Open Source >=2.3.5 &lt;2.4.4*) - Corrige le problème en raison duquel la quantité de stock d’un produit virtuel est mal calculée après la création d’un avoir.
* **ACSD-43887** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.5*) - Correction du problème en raison duquel des détails incorrects s’affichent sur la page de paiement de la commande lorsque les bons de commande pour les sociétés sont activés.
* **ACSD-45143** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.5*) - Corrige le problème en raison duquel la mutation `setShippingAddressesOnCart` ne permet pas de définir le code de région numérique comme *région*.
* **ACSD-44591** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.6*) - Corrige l’erreur qui se produit lorsqu’une commande est passée sans confirmation CAPTCHA.
* **ACSD-45520** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.6*) - Correction du problème en raison duquel les options d’échantillon ne sont pas présélectionnées sur la page des détails du produit lorsqu’un utilisateur modifie des produits configurables à partir du panier.
* **ACSD-45169** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.6*) - Corrige le problème en raison duquel [!DNL Visual Merchandiser] n’affiche pas le stock et le prix corrects d’un produit configurable après l’application d’une mise à jour d’évaluation.
* **ACSD-45424** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;2.4.6*) - Corrige le problème en raison duquel une compensation de réservation incorrecte est créée après un remboursement partiel (avoir).
* **MDVA-42807** (*pour Adobe Commerce et Magento Open Source >=2.3.1 &lt;2.4.6*) - Corrige le problème en raison duquel le signe de devise personnalisé n’est pas affiché en façade.
* Correctifs mis à jour : MDVA-42689, AC-3022.

## v1.1.16 {#v1-1-16}

* **MDVA-44703** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4*) - Correction du problème en raison duquel le total des commandes du rapport Commandes est mal calculé pour l’utilisateur administrateur restreint.
* **MDVA-44940** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4*) - Corrige l’erreur SQL qui se produit lors de l’enregistrement de la catégorie depuis Admin.
* **MDVA-44562** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.2-p2*) - Correction du problème où l’ID de magasin non par défaut pour les articles de devis est remplacé par l’ID de magasin par défaut, malgré la requête GraphQL provenant de la vue de magasin non par défaut.
* **MDVA-43167** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Correction du problème en raison duquel l’action de masse de la grille de commandes de l’administrateur ne s’applique pas à plusieurs pages lorsque l’utilisateur administrateur sélectionne toutes les commandes.
* **MDVA-44044** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.2-p2*) - Corrige le problème lorsqu’un produit n’est pas affiché sur la page de catégorie après avoir été affecté à un nouveau site web.
* **MDVA-42509** (*pour Adobe Commerce et Magento Open Source >=2.3.3 &lt;2.4.4*) - Corrige le problème en raison duquel un fichier CSV n’a pas pu être chargé pour une commande rapide, ce qui entraînait une erreur *Impossible d’envoyer le cookie*.
* Correctifs mis à jour : MDVA-41061, MDVA-42584.
* Le préfixe des nouveaux correctifs [!DNL Quality Patches Tool] sera modifié de *MDVA* en *ACSD* en raison de modifications du processus interne.

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4*) - Correction d’un problème en raison duquel un article supplémentaire ne peut pas être ajouté au panier lorsque la quantité minimale de l’article y est déjà.
* **MDVA-44887** (*pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.5*) - Corrige l’erreur *Uncaught SyntaxError: Unexpected token &#39;const&#39;* dans le panneau d’administration.
* **MDVA-43718** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correctifs *Le client n’est pas autorisé à accéder à %resources.* erreur qui s’affiche lors de l’accès à un catalogue partagé à partir d’une intégration personnalisée.
* **MDVA-44660** (*pour Adobe Commerce et Magento Open Source >=2.4.2-p1 &lt;2.4.5*) - Corrige le problème en raison duquel le ``` ` ``` de caractère d’accentuation grave ne pouvait pas être utilisé pour le prénom et le nom d’un client.
* **MDVA-40896** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4*) - Corrige l’erreur *Erreur : typeError : argument 3 transmis à Magento* dans l’API en bloc de produit asynchrone.
* **MDVA-38559** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.3*) - Corrige l’erreur */V1/customers/search API* pour les clients disposant de plusieurs abonnements.
* **MDVA-44533** (*pour Adobe Commerce et Magento Open Source >=2.3.1 &lt;2.4.4*) - Corrige le problème en raison duquel la remise est appliquée à tort à un produit enfant groupé.
* Correctifs mis à jour : MDVA-41061, MDVA-42269.

## v1.1.14 {#v1-1-14}

* **MDVA-43983** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.5*) - Correction du problème en raison duquel les produits *Non visibles individuellement* apparaissent toujours dans les résultats de la recherche avancée du catalogue.
* **MDVA-44100** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.5*) - Correction du problème en raison duquel tous les FPT sont affectés au dernier produit du panier et réinitialisés pour d’autres produits.
* **MDVA-43605** (*pour Adobe Commerce et Magento Open Source >=2.3.1 &lt;2.4.5*) - Correction du problème en raison duquel les données de commande renvoient des valeurs négatives pour les totaux des lignes lors de l’utilisation de l’API Rest.
* **MDVA-43102** (*pour Adobe Commerce et Magento Open Source >=2.3.1 &lt;2.4.5*) - Correction d’un problème en raison duquel la quantité commercialisable n’est pas mise à jour correctement lorsqu’un remboursement est effectué via l’API REST.
* **MDVA-43178** (*pour Adobe Commerce et Magento Open Source >=2.4.3-p2 &lt;2.4.5*) - Corrige le problème en raison duquel un jeton client pour un magasin personnalisé ne peut pas être récupéré dans GraphQL.
* **MDVA-43859** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.5*) - Correction du problème où l’erreur *Aucune entité de ce type avec customerId =* n’est consignée lorsqu’un client supprimé tente de se connecter.
* **MDVA-44147** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.5*) - Corrige le problème en raison duquel une demande GraphQL ne renvoie pas de listes de demandes.
* **MDVA-44505** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.3*) - Corrige les problèmes où l’application de points de récompense par GraphQL ne met pas à jour le total général et où le crédit de magasin est appliqué plusieurs fois pendant le placement de la commande.
* Correctifs mis à jour : MDVA-29148, MDVA-36464-V5, MDVA-42584, MDVA-39993-V2.

## v1.1.13 {#v1-1-13}

* **MDVA-42969** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.3*) - Correction du problème en raison duquel la règle relative aux produits associés ne fonctionne que lorsque le segment client est défini sur *Tous*.
* **MDVA-39605** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;2.4.5*) - Corrige le problème en raison duquel la TTL (date d’expiration) du cache Redis a une valeur incorrecte.
* **MDVA-43862** (*pour Adobe Commerce et Magento Open Source >=2.3.3 &lt;2.4.5*) - Corrige le problème en raison duquel le client ne peut pas mettre à jour les articles du panier en raison d’une erreur GraphQL *mutation UpdateCartItems*.
* **MDVA-43824** (*pour Adobe Commerce et Magento Open Source >=2.3.6 &lt;=2.3.7-p3 || >=2.4.1 &lt;2.4.5*) - Correction du problème d’affichage d’une erreur lors de l’annulation des commandes avec une remise.
* **MDVA-43451** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.5*) - Corrige le problème en raison duquel l’erreur *Le magasin demandé est introuvable. Vérifiez le magasin et réessayez.* s’affiche lors de la configuration d’un catalogue partagé pour un site web spécifique.
* **MDVA-43491** (*pour Adobe Commerce et Magento Open Source >=2.3.5 &lt;2.4.5*) - Correction du problème en raison duquel le libellé de l’image de base n’est pas mis à jour lors de l’importation de produits pour un site web multi-magasin.
* **MDVA-43601** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige le problème en raison duquel des déclencheurs étaient manquants après la réindexation complète.
* **MDVA-42046** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;=2.3.5-p2 || >=2.4.0 &lt;2.4.5*) - Corrige le problème où une valeur incorrecte est affectée à un attribut de produit avec un champ de saisie de date lors de la mise à jour d’un produit.
* **MDVA-43935** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.5*) - Corrige le problème d’affichage en double du produit de montée en gamme.
* **MDVA-44188** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.5*) - Correction du problème en raison duquel les e-mails émis par le système avec des adresses `.-` ne sont pas envoyés.
* **MDVA-42283** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction d’un problème en raison duquel le format de date et d’heure dans la grille de commande d’administration pour les paramètres régionaux français n’était pas valide.
* Correctifs mis à jour : MDVA-41061-V2, MDVA-36309, MDVA-30862, MDVA-39713.
* Ajout de correctifs de métadonnées pour le [!DNL Site-Wide Analysis Tool].

## v1.1.12 {#v1-1-12}

* **MDVA-39713** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.3.6*) - Corrige le problème en raison duquel l’utilisateur ou l’utilisatrice peut modifier l’heure de début d’une mise à jour planifiée active.
* **MDVA-42410** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction du problème en raison duquel les rapports de coupon affichaient uniquement la devise de base par défaut.
* **MDVA-41136** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige le problème en raison duquel la date d’expiration du `mage-cache-sessid` n’est pas prolongée, ce qui entraîne un nettoyage des données client.
* **MDVA-39993** (*pour Adobe Commerce et Magento Open Source >=2.3.5 &lt;=2.3.7-p2 || >=2.4.0 &lt;2.4.4*) - Correction du problème en raison duquel les modifications d’inventaire effectuées par le biais de l’API ne sont pas reflétées sur la page du produit sur le serveur frontal.
* **MDVA-42855** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.5*) - Corrige le problème en raison duquel une nouvelle adresse du client n’est pas enregistrée dans le carnet d’adresses lors du passage en caisse.
* **MDVA-42645** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.5*) - Correction du problème en raison duquel l’administrateur ne peut pas rembourser les points de récompense si la fonctionnalité de crédit de magasin est désactivée.
* **MDVA-43414** (*pour Adobe Commerce et Magento Open Source >=2.3.6 &lt;=2.3.7-p2*) - Corrige l’erreur fatale PHP qui se produit lors de l’exécution du client de la file d’attente `inventory.reservations.updateSalabilityStatus` sur des SKU numériques.
* **MDVA-41628** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.5*) - Correction du problème en raison duquel les utilisateurs administrateurs restreints existants accèdent aux nouvelles ressources lorsque de nouveaux modules sont ajoutés.
* **MDVA-43348** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.5*) - Correction du problème en raison duquel la requête de GraphQL de carte cadeau affichait une erreur si `gift_card_options` contenait *uid*.
* **MDVA-39546** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction du problème en raison duquel la date de début de la mise à jour d’évaluation pouvait être définie à une date antérieure à la date actuelle lors de la modification.
* **MDVA-42950** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction d’un problème qui empêchait la lecture des vidéos sur la page produit.
* **MDVA-42689** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige le problème en raison duquel Adobe Commerce renvoie une erreur *violation de contrainte d’intégrité* lors de la mise à jour des catégories de produits lors de l’importation.
* **MDVA-41229** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction du problème en raison duquel les images disponibles sur le serveur principal ne s’affichent pas sur le serveur frontal après l’importation de produits configurables.
* **MDVA-43731** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4*) - Correction du problème en raison duquel *les synonymes de recherche* ne fonctionnent plus lorsque de la valeur est ajoutée dans *Termes minimaux à correspondre*.
* **MDVA-43232** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;2.4.5*) - Correction du problème en raison duquel le tri des produits dans [!DNL Visual Merchandiser] par Prix spécial en bas/en haut provoque une erreur lors de l’enregistrement de la catégorie.
* **MDVA-43726** (*pour Adobe Commerce et Magento Open Source >=2.3.3 &lt;2.4.3*) - Correction du problème en raison duquel la règle de prix de catalogue basée sur la correspondance d’attributs au niveau du magasin ne s’applique pas après une réindexation partielle.
* Correctifs mis à jour : MDVA-36464, MDVA-37478, MDVA-38608.
* Ajout de correctifs de métadonnées pour le [!DNL Site-Wide Analysis Tool].

## v1.1.11 {#v1-1-11}

* **MDVA-42790** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.5*) - Correction du problème en raison duquel les attributs de prix de produit ne peuvent pas être mis à jour pour un site web spécifique via l’API REST.
* **MDVA-41350** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige le problème où une exception est déclenchée lorsqu’un utilisateur administrateur à accès restreint ajoute un produit en dehors de sa portée de rôle par SKU dans une commande.
* **MDVA-42269** (*pour Adobe Commerce et Magento Open Source >=2.4.3-p1 &lt;2.4.5*) - Correction du problème en raison duquel un utilisateur administrateur ne peut pas se connecter à l’administrateur en raison de l’erreur *TypeError: strtotime() attend que le paramètre 1 soit une chaîne, une valeur nulle étant donnée*.
* **MDVA-40830** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige le problème en raison duquel le crédit de magasin est appliqué plusieurs fois lors du placement de la commande.
* **MDVA-42237** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.5*) - Correction du problème en raison duquel un prix spécial de produit configurable n’est pas mis à jour après les modifications de son prix de sous-produit.
* **MDVA-42520** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4*) - Corrige le problème en raison duquel le taux de taxe est appliqué deux fois si *Activer le commerce transfrontalier* est utilisé.
* Correctifs mis à jour : MDVA-27239, MDVA-39305, MDVA-41236, MDVA-36832.
* Correctif obsolète : MDVA-37725.

## v1.1.10 {#v1-1-10}

* **MDVA-38728** (*pour Adobe Commerce et Magento Open Source >=2.3.2 &lt;2.4.5*) - Correction du problème en raison duquel une mise à jour en masse des attributs crée une réécriture d’URL pour le magasin par défaut uniquement après avoir modifié *Visibilité du produit*.
* **MDVA-43091** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4*) - Correction du problème en raison duquel la commande d’un produit groupé par l’administrateur sur le serveur principal générait l’erreur *Vous ne pouvez pas utiliser de quantité décimale pour ce produit*.
* **MDVA-40816** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction du problème en raison duquel les règles de produit associées affichent des produits provenant de catégories non définies dans les conditions de la règle.
* **MDVA-41305** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.5*) - Corrige le problème en raison duquel la mutation de GraphQL ne renvoie pas d’options de produit configurables après l’avoir ajoutée à la liste de souhaits.
* **MDVA-39181** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.5*) - Correction du problème en raison duquel les règles de produit associées affichent des produits provenant de catégories non définies dans les conditions de la règle.
* **MDVA-42584** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.3*) - Correction du problème en raison duquel l’état du stock configurable sur le serveur principal n’est pas mis à jour après le changement de la quantité et de l’état du stock via l’importation ou l’API.
* **MDVA-40175** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.3*) - Correction du problème en raison duquel *Cliquez pour modifier le mode d’expédition* n’affiche pas de boutons radio permettant de sélectionner les modes d’expédition dans l’administration lors de la réorganisation.
* **MDVA-42768** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;2.4.5*) - Corrige le problème en raison duquel le produit configurable affiche le prix normal sur 0 lorsque *Afficher en rupture de stock* est Oui.
* **MDVA-43201** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige le problème où une erreur se produit lors de la connexion du client lors de l’utilisation de l’attribut DOB avec certains paramètres régionaux.
* Correctifs mis à jour : MDVA-35092, MDVA-33970.

## v1.1.9 {#v1-1-9}

* **MDVA-38346** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction d’un problème en raison duquel les filtres de date ne fonctionnent pas correctement lorsque le fuseau horaire d’Adobe Commerce est différent de celui de l’environnement local.
* **MDVA-42657** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.5*) - Corrige le problème en raison duquel l’utilisateur administrateur ne peut pas sélectionner de catégories dans les conditions de segment client.
* **MDVA-42806** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige le problème d’envoi d’un e-mail *Nouvel enregistrement de société* chaque fois qu’une société existante est mise à jour via l’API REST.
* **MDVA-37984** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.5*) - Corrige le problème en raison duquel la fonctionnalité [!DNL Visual Merchandiser] *Correspondre au produit par règle* ne filtre pas correctement les produits avec les mises à jour d’évaluation.
* **MDVA-40488** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Correction du problème en raison duquel les produits configurables avec des produits enfants en rupture de stock ne s’affichent pas dans la plage de prix appropriée.
* **MDVA-42507** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.5*) - Correction du problème de nettoyage du cache de page complète après l’application de la mise à jour d’évaluation pour la règle de panier.
* **MDVA-39163** (*pour Adobe Commerce et Magento Open Source >=2.3.5 &lt;2.4.5*) - Correction du problème en raison duquel les méthodes d’expédition ne sont pas disponibles lorsqu’un nouvel utilisateur est enregistré et que les produits du panier proviennent de la session invité.
* **MDVA-38626** (*pour Adobe Commerce et Magento Open Source >=2.3.3 &lt;2.4.5*) - Corrige le problème en raison duquel l’utilisateur administrateur n’est pas en mesure de passer une commande sur le serveur principal à l’aide du paiement [!DNL PayPal Payflow Pro].
* **MDVA-38666** (*pour Adobe Commerce et Magento Open Source >=2.3.2 &lt;2.3.6*) - Correction du problème en raison duquel l’utilisateur administrateur n’est pas en mesure de modifier les options de produit configurables dans le panier du client.
* **MDVA-38526** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.4*) - Corrige le problème en raison duquel l’utilisateur administrateur ne peut pas accéder au [!DNL Site-Wide Analysis tool].
* Correctifs mis à jour : MDVA-40101.

## v1.1.8 {#v1-1-8}

* **MDVA-41215** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige le problème où les utilisateurs obtiennent l’erreur 500 après avoir défini le cookie *mage-messages* s’il existe déjà, mais qu’il n’existe aucun nouveau message.
* **MDVA-41139** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4*) - Correction du problème en raison duquel les produits configurables sont en rupture de stock après l’importation d’un produit lorsque la quantité d’un produit simple est égale à 0 pour l’une de ses sources.
* **MDVA-42326** (*pour Adobe Commerce et Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Corrige le problème où les clients obtiennent une erreur lors du passage en caisse après un délai d’expiration de session, même si le panier persistant est activé.
* **MDVA-42341** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige le problème en raison duquel la requête GraphQL `categoryList` ne filtre pas les résultats si une requête comporte l’en-tête Store.
* **MDVA-38393** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction du problème en raison duquel les règles de catalogue cessent de fonctionner pour un produit configurable si son produit simple est renommé.
* **MDVA-39153** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige le problème en raison duquel un montant de remise est calculé de manière incorrecte lors de la réorganisation dans l’administrateur.
* Correctifs mis à jour : MDVA-28993, MDVA-41061, MDVA-35984.

## v1.1.7 {#v1-1-7}

* **MDVA-39711** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.3*) - Correction du problème en raison duquel les utilisateurs administrateurs ne peuvent pas accéder à la grille du client après la suppression du site web.
* **MDVA-40311** (*pour Adobe Commerce et Magento Open Source >=2.4.2-p2 &lt;2.4.4*) - Corrige le problème en raison duquel les utilisateurs administrateurs reçoivent le message d’erreur *Sécurité non valide ou clé de formulaire. Actualisez la page* après vous être connecté à l’administrateur si le chemin d’accès d’administrateur personnalisé est configuré et que la clé secrète est activée.
* **MDVA-41631** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.4*) - Corrige le problème en raison duquel les utilisateurs et les utilisatrices obtiennent une erreur lorsqu’ils tentent de récupérer les informations de commande sans une valeur *téléphone* facultative via GraphQL.
* **MDVA-27239** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.3.6*) - Correction du problème d’affichage des produits de ventes croisées.
* Correctifs mis à jour : MDVA-37068, MDVA-35254, MDVA-41164, MDVA-37916, MDVA-37478, MDVA-34551, MDVA-31791.

## v1.1.6 {#v1-1-6}

* **MDVA-40550** (*pour Adobe Commerce et Magento Open Source >=2.3.5 &lt;2.4.4*) - Correction du problème lié aux produits manquants sur le serveur frontal lors de la réindexation.
* **MDVA-40120** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.4*) - Correction du problème en raison duquel le tri GraphQL par DESC/ASC ne fonctionne pas avec les produits ayant la même pertinence ou le même prix.
* **MDVA-41399** (*pour Adobe Commerce et Magento Open Source >=2.3.3 &lt;2.4.2*) - Correction du problème en raison duquel les utilisateurs administrateurs ne peuvent pas accéder à la page *Gérer le panier* si un client ajoute un produit à la liste de souhaits.
* **MDVA-40609** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.3*) - Correction du problème en raison duquel les données des produits désactivés étaient absentes de la table d’index des `cataloginventory_stock_status`, affichant des quantités de produits désactivées incorrectes.
* **MDVA-39031** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.4*) - Corrige le problème en raison duquel il est possible d’ajouter un produit au panier via GraphQL même s’il n’est pas affecté au site web cible.
* **MDVA-41597** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige le problème où les utilisateurs et utilisatrices reçoivent une erreur lors de l’ajout de plusieurs produits configurables au panier à l’aide de GraphQL.
* **MDVA-27456** (*pour Adobe Commerce et Magento Open Source >=2.3.5 &lt;2.3.7*) - Corrige le problème en raison duquel les utilisateurs obtiennent une erreur lors du chargement de [!DNL Swagger].
* **MDVA-32776** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.2*) - Correction du problème en raison duquel le statut du stock n’est pas mis à jour lorsqu’une commande est passée mais n’est pas envoyée.
* **MDVA-30862** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;2.4.0*) - Correction d’un problème lié à une date de commande incorrecte sur la facture PDF imprimée.
* Amélioration de la page d’index pour la [!DNL Quality Patch Tool] . Ajout de la recherche et du filtrage pratiques pour [!DNL quality patches] à la dernière version de l’outil.
* Correctifs mis à jour : MDVA-33382, MDVA-39482.

## v1.1.5 {#v1-1-5}

* **MDVA-41236** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige le problème en raison duquel il est impossible de créer une mise à jour planifiée ou de modifier une mise à jour planifiée existante pour un produit si la date de fin a été précédemment supprimée.
* **MDVA-41046** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction du problème en raison duquel des produits simples avec des options personnalisées étaient disponibles pour l’affectation à des produits configurables/regroupés.
* **MDVA-40545** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction du problème où seul le premier nœud d’une page était récupéré, même s’il y avait plusieurs nœuds pour la même page.
* **MDVA-41164** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.3-p1*) - Corrige le problème en raison duquel un utilisateur administrateur n’est pas en mesure d’enregistrer ou de modifier une société avec un attribut client personnalisé de type fichier ou image.
* **MDVA-39229** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige le problème en raison duquel l’erreur suivante apparaît après la mise à jour de l’heure de début de la mise à jour de l’évaluation de la règle de catalogue : *Cron Job staging_synchronize_entities_period a une erreur : La mise à jour active ne peut pas être supprimée.*
* **MDVA-40619** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction du problème en raison duquel les modifications apportées à la hiérarchie des pages de CMS provoquent une erreur 500 lors de la tentative de modification sur la ligne d’une page CMS.
* **MDVA-41061** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.3*) - Correction du problème en raison duquel le statut du stock est réinitialisé sur vendable lorsqu’un produit est enregistré depuis l’administration.
* **MDVA-31763** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige le problème en raison duquel les règles de prix de catalogue sont rétablies (ou ne sont pas appliquées) jusqu’à la réindexation manuelle.
* **MDVA-37748** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.3*) - Correction du problème où une requête GraphQL renvoie des produits non affectés à un catalogue partagé.

## v1.1.4 {#v1-1-4}

* **MDVA-40399** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Correction du problème en raison duquel les factures partielles d’une même commande ne peuvent pas être créées simultanément via l’API REST.
* **MDVA-40101** (*pour Adobe Commerce et Magento Open Source >=2.3.2 &lt;2.4.0*) - Correction d’un problème en raison duquel les articles ne sont pas supprimés du mini panier après un placement de commande réussi à l’aide de [!DNL PayPal Express] Passage en caisse.
* **MDVA-40401** (*pour Adobe Commerce et Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Correction du problème en raison duquel la valeur d’utilisation des coupons change même en cas d’échec de la commande.
* **MDVA-40537** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;=2.4.0-p1*) - Correction du problème en raison duquel les utilisateurs obtiennent une erreur lors de la création d’une vue de magasin s’il existe plusieurs pages CMS avec la même clé URL.
* **MDVA-37725** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;=2.4.3-p1*) - Correction du problème en raison duquel les e-mails de commande asynchrones envoyés à partir de sites web non par défaut contiennent des URL de logo provenant du site web par défaut.
* **MDVA-39482** (*pour Adobe Commerce et Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Correction du problème en raison duquel un produit est en rupture de stock s’il est importé avec une quantité de « 0 » lorsque les commandes en souffrance sont activées.
* **MDVA-40435** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;2.4.4*) - Corrige le problème en appliquant une remise incorrecte aux produits groupés avec des prix dynamiques lorsqu’ils sont appliqués via GraphQL.
* **MC-42528** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;=2.4.3-p1*) - Corrige le problème en raison duquel la requête GraphQL `categoryList` renvoie à la fois les catégories affectées et non affectées.
* **MDVA-29400** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;=2.3.7-p1 || >=2.4.0 &lt;=2.4.0-p1*) - Corrige le problème lié aux commandes dupliquées passées avec [!DNL PayPal Express Checkout].
* **MDVA-26005** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;=2.3.5-p2*) - Corrige le problème en raison duquel il est impossible de sélectionner une catégorie dans une arborescence de catégories pour les conditions de la règle Prix du panier.
* **MDVA-25631** (*pour Adobe Commerce et Magento Open Source >=2.3.3 &lt;=2.3.5-p2*) - Améliore les performances de modification et d’enregistrement des segments de clients contenant un grand nombre de clients.

## v1.1.3 {#v1-1-3}

* **MDVA-40262** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Correction du problème en raison duquel les requêtes de recherche GraphQL ne s’affichent pas dans les termes de recherche populaires dans l’Administration.
* **MDVA-40601** (*pour Adobe Commerce et Magento Open Source >=2.3.1 &lt;=2.4.2-p2*) - Corrige le problème où les utilisateurs et utilisatrices obtiennent une erreur lorsqu’ils ou elles tentent d’obtenir des informations sur la catégorie modifiée par une mise à jour planifiée via GraphQL.
* **MDVA-37234** (*pour Adobe Commerce et Magento Open Source >=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*) - Corrige le problème en raison duquel l’ajout multiple d’un élément au panier (requête parallèle) pour le même SKU crée un élément de ligne en double pour le même ID de panier.
* **MDVA-33606** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;=2.4.2-p2*) - Corrige le problème où les utilisateurs obtiennent une erreur *Violation de contrainte unique* lors de l’enregistrement d’une page CMS affectée à une hiérarchie.
* **MDVA-31590** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;=2.4.1-p1*) - Corrige le problème en raison duquel les utilisateurs ne peuvent pas mettre à jour les attributs en bloc à l’aide des files d’attente asynchrones MySQL.
* **MDVA-36309** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Corrige le problème en raison duquel la recherche de produits par attributs est lente dans les grilles d’administration.

## v1.1.2 {#v1-1-2}

* **MDVA-38929** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction du problème en raison duquel la facture avec FPT affiche un total général incorrect lorsque la commande est payée à partir du crédit de la boutique.
* **MDVA-37364** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;=2.4.3*) - Correction du problème en raison duquel l’attribut du client personnalisé de type date rompt l’interface utilisateur de grille du client.
* **MDVA-39195** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Correction du problème en raison duquel le bouton *Ajouter au panier* était inactif sur la page de catégorie lorsque la redirection vers le panier était activée.
* **MDVA-37115** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Corrige le problème en raison duquel un avis *Il ne reste que 0* inutile s’affiche sur la page des produits configurables.
* **MDVA-39521** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.4*) - Corrige le problème en raison duquel l’utilisateur ne peut pas définir d’adresses d’expédition sur le panier avec un numéro de téléphone vide via GraphQL.
* **MDVA-39384** (*pour Adobe Commerce et Magento Open Source >=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*) - Correction du problème en raison duquel l’attribut client personnalisé d’un utilisateur d’entreprise n’est pas enregistré.
* **MDVA-39043** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;=2.4.3*) - Correction du problème en raison duquel l’utilisateur administrateur à accès limité reçoit une erreur lors de la tentative d’ajout du widget *Produits* à la page CMS.
* **MDVA-39966** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*) - Corrige le problème de déploiement de paramètres régionaux incorrects.
* **MDVA-38852** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;=2.3.5-p2*) - Correction du problème en raison duquel l’inventaire des catalogues verrouille par conception les tables pour les mises à jour qui réduisent considérablement les performances dans les cas où plusieurs commandes sont parallèles.
* **MDVA-39986** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.3*) - Corrige le problème en raison duquel l’utilisateur ne peut pas passer de commande dans l’administration sur MacOS à l’aide du navigateur Safari.
* **MDVA-38447** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige deux problèmes : où les produits enfants configurables *Non visibles individuellement* sont renvoyés dans la réponse GraphQL et optimisent la requête MySQL pour la requête de produits GraphQL avec le filtre de catégorie.
* **MDVA-40134** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.3*) - Correction du problème en raison duquel GraphQL ne renvoie pas les produits associés lorsque le catalogue partagé est activé.
* **MDVA-39935** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.4*) - Correction du problème en raison duquel le GraphQL renvoie des produits enfants configurables désactivés au niveau du site web.

## v1.1.1 {#v1-1-1}

* **MDVA-36021** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.4*) - Corrige le problème en raison duquel l’erreur *Appel à une fonction membre getId()* s’affiche sur la page des détails de la commande dans l’Administration.
* **MDVA-34948** (*pour Adobe Commerce et Magento Open Source >=2.3.6 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.0-p1*) - Corrige le problème lié aux requêtes de longue durée, comme les `GET_LOCK`.
* **MDVA-39305** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;=2.4.2-p1*) - Corrige le problème en raison duquel les clients enregistrés ne peuvent pas se connecter avec Google ReCaptcha activé.
* **MDVA-37897** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige le problème avec une redirection incorrecte lorsqu’un client tente d’ajouter des produits avec des options du widget Récemment consultés.

## v1.1.0 {#v1-1-0}

* Des catégories de correctifs ont été introduites afin d’améliorer l’expérience utilisateur et de faciliter la recherche de correctifs requis pour les clients.
* Le fichier `patches.json` a été renommé `support-patches.json`.
* **MDVA-38799** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige le problème en raison duquel les produits téléchargeables n’étaient pas enregistrés après la création d’une mise à jour d’évaluation.
* **MDVA-37592** (*pour Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - Corrige le problème lorsque le tri par prix ne fonctionne pas correctement pour les produits dont le prix zéro est affecté au catalogue partagé.
* **MDVA-38827** (*pour Adobe Commerce >=2.3.3-p1 &lt;2.4.4*) - Corrige le problème en raison duquel les clients reçoivent un e-mail d’expédition de commande contenant un message d’erreur.

## v1.0.26 {#v1-0-26}

* **MDVA-38468** (*pour Adobe Commerce >=2.3.2 &lt;=2.3.5-p2*) - Corrige l’erreur lors de l’enregistrement des pages CMS : *Un élément portant le même ID PAGE_ID existe déjà*.
* **MDVA-34680** (*pour Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;2.4.3*) - Correction du problème en raison duquel l’heure de création du compte client n’est pas correctement filtrée dans la grille des clients.
* **MDVA-37068** (*pour Adobe Commerce >=2.3.1 &lt;2.4.4*) - Correction du problème en raison duquel un taux de taxe incorrect s’affiche lorsque le panier comporte uniquement des produits virtuels.
* **MDVA-38608** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Correction du problème en raison duquel les tables temporaires ne sont pas supprimées lorsque la réindexation n’est pas terminée avec succès.
* **MDVA-38308** (*pour Adobe Commerce >=2.3.5 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.1-p1 || >=2.4.2 &lt;2.4.4*) - Corrige les problèmes liés à l’ajout de vidéos [!DNL Vimeo] aux produits.

## v1.0.25 {#v1-0-25}

* **MDVA-37916** (*pour Adobe Commerce >=2.3.6 &lt;2.4.3*) - Corrige le problème en raison duquel le client n’est pas redirigé vers la page de confirmation de paiement lors de l’utilisation de la méthode [!DNL Paypal Payment Advanced].
* **MDVA-37082** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige le problème qui se produit lorsque l’enregistrement du stock personnalisé de produits groupés entraîne la rupture de stock du produit dans le serveur frontal.
* **MDVA-36572** (*pour Adobe Commerce >=2.3.5 &lt;2.4.3*) - Correction du problème en raison duquel les mises à jour des avoirs ne provoquent plus de mises à jour en double des réservations de produits dans la base de données.
* **MDVA-38132** (*pour Adobe Commerce >=2.3.3 &lt;2.4.3*) - Corrige le problème lorsque le panneau d’administration est inaccessible en raison d’une erreur *trop de redirections*.
* **MDVA-38270** (*pour Adobe Commerce >=2.4.1 &lt;2.4.3*) - Correction du problème lié à l’absence des informations de carte cadeau dans le total des commandes dans GraphQL.

## v1.0.24 {#v1-0-24}

* **MDVA-37779** (*pour Adobe Commerce >=2.4.2 &lt;=2.4.4*) - Corrige le problème lié à l’ajout d’un produit configurable au panier via GraphQL lorsque l’ID du site web ne correspond pas à l’ID du magasin.
* **MDVA-36832** (*pour Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - Correction du problème de duplication des images sur les pages lorsque la largeur d’affichage est de 768 px.
* **MDVA-37874** (*pour Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;=2.4.2-p1*) - Correction du problème où *Montant de remise fixe pour l’ensemble du panier* est incorrectement appliqué à un lot de produits contenant plusieurs options.
* **MDVA-37913** (*pour Adobe Commerce >=2.3.0 &lt;=2.4.0-p1*) - Correction du problème en raison duquel les liens téléchargeables disparaissent si le produit téléchargeable est mis à jour via l’API.
* **MDVA-34330** (*pour Adobe Commerce >=2.3.1 &lt;=2.4.2-p1*) - Corrige le problème en raison duquel les commandes de la grille Commandes ne sont pas filtrées en fonction du fuseau horaire de l’administrateur.

## v1.0.23 {#v1-0-23}

* **MDVA-37478** (*pour Adobe Commerce >=2.3.0 &lt;=2.3.7*) - Correction du problème en raison duquel Adobe Commerce renvoie une erreur lors de la création d’une facture partielle pour les commandes passées avec la méthode de paiement *Paiement sur compte* via l’API REST.
* **MDVA-37362** (*pour Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - Correction du problème en raison duquel les valeurs d’option de produit configurables et les valeurs d’attribut de variante étaient vides dans la réponse GraphQL.
* **MDVA-37288** (*pour Adobe Commerce 2.4.2*) - Correction du problème en raison duquel des prix de niveau incorrects étaient renvoyés après une demande de GraphQL.
* **MDVA-37225** (*pour Adobe Commerce >=2.4.1 &lt;=2.4.2-p1*) - Correction du problème en raison duquel le processus de chargement est bloqué lors de la création rapide d’une commande lorsqu’il existe une valeur entière dans les SKU importés.
* **MDVA-37224** (*pour Adobe Commerce >=2.3.3 &lt;=2.4.2-p1*) - Correction du problème en raison duquel les clients ne peuvent pas payer de devis négociable avec [!DNL PayFlow Pro] avec un autre produit du panier.
* **MDVA-36286** (*pour Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - Correction du problème en raison duquel l’aperçu du widget Produits de Page Builder se rompt si le même SKU a une position différente dans les sous-catégories.
* **MDVA-30186** (*pour Adobe Commerce >=2.3.4 &lt;=2.3.5-p2, >=2.4.0 &lt;=2.4.0-p1, >=2.4.2 &lt;=2.4.2-p1*) - Corrige le problème où les options d’attribut sont triées par valeur d’option au lieu du nombre d’éléments d’attribut dans la réponse GraphQL.

## v1.0.22 {#v1-0-22}

* **MDVA-36718** (*pour Adobe Commerce >=2.3.0 &lt;=2.4.2*) - Corrige le problème où les anciennes options personnalisées restent après avoir été modifiées via l’API.
* **MDVA-35773** (*pour Adobe Commerce >=2.3.6 &lt;=2.3.6-p1 || >=2.4.1 &lt;=2.4.2*) - Correction du problème en raison duquel le total général n’était pas indiqué comme zéro sur la facture pour les commandes avec une remise de 100 %.
* **MDVA-36833** (*pour Adobe Commerce 2.4.2*) - Correction du problème en raison duquel les résultats de recherche affichaient un nombre aléatoire de produits par page après l’exclusion de certains produits du catalogue partagé.
* **MDVA-37182** (*pour Adobe Commerce >=2.4.1 &lt;=2.4.2*) - Corrige le problème d’obtention de résultats de recherche incorrects dans les versions 6 et 7 de [!DNL Elasticsearch].
* **MDVA-36253** (*pour Adobe Commerce >=2.4.0 &lt;=2.4.1-p1*) - Correction du problème en raison duquel un sous-total incorrect s’affiche dans le mini panier après la suppression d’un article.
* **MDVA-36853** (*pour Adobe Commerce 2.4.2*) - Correction du problème en raison duquel aucune image n’apparaît lors du chargement de galeries de médias volumineuses.

## v1.0.21 {#v1-0-21}

* **MDVA-34665** (*pour Adobe Commerce >=2.3.4 &lt;=2.3.4-p2*) - Corrige le problème lié aux produits groupés manquants sur les pages de catégorie.
* **MDVA-36615** (*pour Adobe Commerce 2.4.2*) - Correction d’un problème lié à un nombre de produits incorrect dans la grille de produits de l’administrateur.
* **MDVA-36464** (*pour Adobe Commerce >=2.4.0 &lt;=2.4.2*) - Corrige le problème en raison duquel la configuration des notifications par e-mail ne fonctionne pas au niveau de la vue du magasin.
* **MDVA-36138** (*pour Adobe Commerce ^2.3.2*) - Correction d’un problème en raison duquel le prix d’expédition n’est pas ajusté et que le prix d’expédition complet est affiché aux clients si tous les articles du panier ne sont pas éligibles à la règle de panier d’expédition gratuit.
* **MDVA-36424** (*pour Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 || >=2.0.0 &lt;2.2.0*) - Correction du problème en raison duquel les images multimédia associées aux éléments du générateur de page disparaissent lorsque le contenu est modifié à plusieurs reprises si l’URL de base du serveur principal est différente de l’URL de base du storefront.
* **MDVA-35984** (*pour Adobe Commerce ^2.4.0*) - Correction d’un problème lié à une quantité de produit et à une quantité vendables incorrectes, après la création de plusieurs expéditions simultanées pour le même produit.

## v1.0.20 {#v1-0-20}

* **MDVA-36170** (*pour Adobe Commerce >=2.3.4 &lt;2.4.2*) - Correction du problème en raison duquel la requête GraphQL n’est pas mise en cache à l’aide de la balise de cache de catégorie.
* **MDVA-33168** (*pour Adobe Commerce >=2.3.3 &lt;2.4.2*) - Corrige le problème lors de la mise à jour d’un attribut de produit via l’API, tous les autres attributs sont remplacés par une valeur vide.
* **MDVA-19640** (*pour Adobe Commerce >=2.3.0*) - Corrige le problème en raison duquel [!DNL Advanced Reporting] n’affiche aucune donnée.
* **MDVA-11189** (*pour Adobe Commerce >=2.3.0 &lt;2.3.5*) - Corrige le problème en raison duquel, après avoir importé un fichier CSV pour mettre à jour le stock de produits, les lignes du tableau `cataloginventory_stock` sont supprimées.
* **MDVA-26639** (*pour Adobe Commerce >=2.3.3-p1 &lt;2.3.6*) - Correction du problème en raison duquel, si un nouveau modèle d’e-mail de confirmation de commande est créé, les éléments de commande sont manquants dans l’e-mail de commande.
* **MDVA-15546** (*pour Adobe Commerce >=2.3.0*) - Corrige le problème en raison duquel, après la création d’une commande, un *Id_entité_colonne où la clause est ambiguë* l’erreur s’affiche dans le journal des exceptions.
* **MDVA-21095** (*pour Adobe Commerce >=2.3.0 &lt;2.3.5*) - Corrige le problème lorsqu’une `INSERT INTO search_tmp` de requête ne se termine pas après la mise à jour en masse de la valeur d’attribut.
* **MDVA-23845** (*pour Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - Correction du problème en raison duquel les modèles d’e-mail ne peuvent pas être prévisualisés une fois que la minimisation de JavaScript est activée.
* **MDVA-22026** (*pour Adobe Commerce >=2.3.2 &lt;2.3.4*) - Corrige le problème d’échec de l’importation de produits à partir d’un fichier CSV, y compris des images provenant d’URL externes.
* **MDVA-22383** (*pour Adobe Commerce >=2.3.0 &lt;2.3.4*) - Correction du problème en raison duquel l’enregistrement d’un produit prend beaucoup de temps et les sauts de page.
* **MC-41359** (*pour Adobe Commerce >=2.3.6-p1 &lt;2.3.7, >=2.4.2 &lt;2.4.3*) - Corrige le problème de paramètres de cookie SameSite incorrects.

## v1.0.19 {#v1-0-19}

* **MDVA-33614** (*pour Adobe Commerce 2.4.1*) - Correction du problème en raison duquel Page Builder renvoie l’erreur suivante : *Une erreur s’est produite lors du lancement de Page Builder. Veuillez consulter votre contact d’assistance technique.*
* **MDVA-35356** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige le problème lié à un retour de crédit de magasin incorrect après l’annulation d’une commande partiellement facturée.
* **MDVA-33289** (*pour Adobe Commerce >=2.4.0 &lt;2.4.3*) - Corrige le problème en raison duquel le code JavaScript brut s’affiche dans l’interface utilisateur de l’adresse de facturation lors du passage en caisse si [!DNL Google Tag Manager] est activé.
* **MDVA-35982** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Correction du problème en raison duquel les utilisateurs administrateurs limités à un site web spécifique ne peuvent pas créer d’expédition pour la commande passée sur le même site web.
* **MDVA-35155** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6*) - Corrige le problème en raison duquel il est impossible d’acheter un produit groupé si le titre de l’option a été modifié.
* **MDVA-35910** (*pour Adobe Commerce >=2.4.1 &lt;2.4.3*) - Corrige le problème en raison duquel il est impossible de créer un compte client après avoir désactivé la fonctionnalité Connexion en tant que client.
* **MDVA-34474** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige le problème lié à l’ajout d’un produit à la liste de demandes d’approvisionnement à l’aide de l’API.
* **MDVA-34591** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige le problème en raison d’un calcul de remise de règle de panier incorrect pour *La remise Qté maximale est appliquée à* et *Étape Qté de remise (Acheter X)*.
* **MDVA-33704** (*pour Adobe Commerce >=2.4.0 &lt;2.4.3*) - Corrige le problème en raison duquel l’option *En magasin, retrait* expédition ne s’affiche pas, bien qu’elle soit configurée pour être disponible.
* **MDVA-34928** (*pour Adobe Commerce >=2.3.5 &lt;2.3.5-p2*) - Correction du problème en raison duquel le chargeur de page s’affiche indéfiniment après la suppression du crédit de la boutique du paiement.
* **MDVA-35254** (*pour Adobe Commerce >=2.3.1 &lt;2.4.3*) - Corrige les problèmes liés à CAPTCHA lors de l’extraction.
* **MDVA-35569** (*pour Adobe Commerce >=2.3.4 &lt;2.4.2*) - Correction du problème en raison duquel le champ *taxes fixes sur les produits* n’est pas renseigné dans la réponse GraphQL lorsque l’état est spécifié.
* **MDVA-35847** (*pour Adobe Commerce >=2.4.1 &lt;2.4.3*) - Correction du problème B2B en raison duquel le formulaire Utilisateurs de l’entreprise est rompu si un attribut client personnalisé est utilisé.
* **MDVA-31307** (*pour Adobe Commerce >=2.4.0 &lt;2.4.2*) - Correction du problème de *mémoire insuffisante* erreurs sur certaines catégories en raison de problèmes de whitelistage CSP dynamique pour les blocs mis en cache.

## v1.0.18 {#v1-0-18}

* **MDVA-32655** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige le statut incorrect *en cours* du message en *terminé* pour les `quoteItemCleaner` de consommateurs après la suppression de plusieurs produits.
* **MDVA-34102** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige la quantité de Stock par défaut égale à zéro pour les produits désactivés sur les pages Grille de produits et Modifier le produit dans la zone Admin.
* **MDVA-35286** (*pour Adobe Commerce >=2.4.0 &lt;2.4.2*) - Corrige le problème en raison duquel une erreur se produit si un client a regroupé des produits dans le panier et passe de la Finalisation de l’achat avec plusieurs adresses à la Finalisation de l’achat sur une page.
* **MDVA-35312** (*pour Adobe Commerce >=2.4.1-p1 &lt;2.4.2*) - Corrige le code de réponse 500 lorsqu’une requête GraphQL vide.
* **MDVA-34189** (*pour Adobe Commerce >=2.3.4 &lt;2.4.3*) - Corrige le délai d’expiration de 503 premiers octets des requêtes [!DNL Visual Merchandiser] lors du chargement de la page de catégorie Admin.
* **MDVA-34695** (*pour Adobe Commerce >=2.3.0 &lt;2.4.1*) - Corrige les `children_count` négatifs après la suppression des catégories.

## v1.0.17 {#v1-0-17}

* **MDVA-34012** (*pour Adobe Commerce >=2.3.1 &lt;2.4.3*) - Corrige le problème en raison duquel la case *Utiliser la valeur par défaut* est décochée une fois les modifications planifiées appliquées. Le problème apparaît une fois que les modifications planifiées ne sont plus en vigueur.
* **MDVA-35064** (*pour Adobe Commerce >=2.3.3 &lt;2.4.3*) - Correction du problème en raison duquel les réécritures d’URL ne sont pas générées pour les produits configurables créés via l’API.
* **MDVA-34943** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige le problème en raison duquel les commandes rapides mettent en cache les SKU saisies précédemment.
* **MDVA-35197** (*pour Adobe Commerce >=2.3.5 &lt;2.4.0*) - Corrige le problème en raison duquel une erreur se produit lors de l’ajout au panier à l’aide de GraphQL si des produits ajoutés précédemment sont en rupture de stock.
* **MDVA-34850** (*pour Adobe Commerce >=2.3.1 &lt;2.4.0*) - Correction du problème d’affichage des options en rupture de stock d’un produit configurable au lieu de leur affichage en tant que texte barré.
* **MDVA-34867** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige le problème en raison duquel les valeurs d’un champ de condition défini pour une mise à jour planifiée ne sont pas enregistrées.
* **MDVA-35092** (*pour Adobe Commerce >=2.3.5 &lt;2.4.3*) - Correction du problème en raison duquel les utilisateurs ne peuvent pas ajouter de vidéos [!DNL Vimeo] en raison de l’obsolescence de l’API [!DNL Vimeo].

## v1.0.16 {#v1-0-16}

* **MDVA-33453** (*pour Adobe Commerce >=2.3.6 &lt;2.4.3*) - Correction du problème en raison duquel l’aperçu du type de contenu des produits Page Builder se rompt si les produits correspondants ont des prix différents pour chaque site web.
* **MDVA-32634** (*pour Adobe Commerce ^2.3.1*) - Correction du problème en raison duquel le `url_path` de la catégorie affectée à tous les magasins reste inchangé après le déplacement de la catégorie dans la hiérarchie.
* **MDVA-33344** (*pour Adobe Commerce ^2.3.0*) - Correction du problème en raison duquel l’ID d’ensemble d’attributs par défaut de l’entité `rma_item` codée en dur est utilisé au lieu de la valeur de la base de données.
* **MDVA-34192** (*pour Adobe Commerce >=2.3.4 &lt;2.4.3*) - Corrige le problème en raison duquel il est impossible de modifier/spécifier la date de naissance du client au format jj/mm/aaaa.
* **MDVA-34847** (*pour Adobe Commerce ^2.3.0*) - Correction de la conversion des types d’ID de magasin en entiers pour les conditions SQL dans les collections d’administration pour les utilisateurs administrateurs disposant d’autorisations personnalisées.
* **MDVA-34886** (*pour Adobe Commerce ^2.3.2*) - Correction du problème en raison duquel la recherche ne renvoie pas de résultats si l’attribut de produit *weight* est configuré comme pouvant faire l’objet d’une recherche.

## v1.0.15 {#v1-0-15}

* **MDVA-33559** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige le problème d’échec du paiement [!DNL PayPal Payflow Pro] avec l’erreur de format de liste de paramètres de redirection.
* **MDVA-34023** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Correction du problème en raison duquel l’erreur *Aucune entité de ce type avec addressId* s’affiche de manière aléatoire sur les navigateurs des visiteurs.
* **MDVA-32759** (*pour Adobe Commerce >=2.3.1 &lt;2.4.3 avec extension B2B*) - Correction du problème en raison duquel les catalogues partagés suppriment la tarification de niveau existant.
* **MDVA-33482** (*pour Adobe Commerce ^2.3.5*) - Correction d&#39;un problème en raison duquel la génération d&#39;un avoir sur une facture partielle entraînait la taxe de la commande totale au lieu de la taxe de cette facture partielle.
* **MDVA-33393** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige l’erreur *L’ID de pays fourni n’existe pas*.
* **MDVA-33632** (*pour Adobe Commerce >=2.3.0 &lt;2.3.7*) - Fournit un correctif où le message d’exception *Ce produit est en rupture de stock* s’affiche désormais pour un utilisateur administrateur qui tente de commander à nouveau un produit en rupture de stock.
* **MDVA-34469** (*pour Adobe Commerce >=2.4.1 &lt;2.4.2*) - Corrige le problème en raison duquel les mutations GraphQL sur le panier d’un client échouent lors de l’utilisation de plusieurs vues de magasin.
* **MDVA-33976** (*pour Adobe Commerce >=2.3.0 &lt;2.3.7*) - Corrige le problème où le produit groupé s’affiche En rupture de stock sur le storefront après la suppression de la deuxième option du produit groupé.
* **MDVA-33894** (*pour Adobe Commerce >=2.4.0 &lt;2.4.1 avec extension B2B*) - Corrige plusieurs problèmes liés à la fonctionnalité de commande rapide, y compris l’ajout et la suppression de plusieurs produits et le respect de la casse des SKU.
* **MDVA-27664** (*pour Adobe Commerce >=2.3.4 &lt;2.3.6*) - Correction d’un problème dans le formulaire d’enregistrement des clients qui entraînait l’affichage d’une erreur : *ERREUR - La date de naissance ne doit pas être postérieure à aujourd’hui.*
* **MDVA-33970** (*pour Adobe Commerce >=2.3.4 &lt;2.4.2*) - Correction du problème en raison duquel un signe de devise incorrect était présent dans l’avoir lorsque la portée de l’attribut de prix est définie sur le site web.
* **MDVA-33992** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige le problème d’affichage incorrect des prix spéciaux B2B lors du passage en caisse.
* **MDVA-34100** (*pour Adobe Commerce >=2.3.4 &lt;2.4.2 avec extension B2B*) - Corrige le problème en raison duquel un compte de société ne peut pas être créé à partir de la page de structure de la société.

## v1.0.14 {#v1-0-14}

* **MDVA-31969** (*pour Adobe Commerce >=2.3.3 &lt;2.3.5, >=2.4.0 &lt;2.4.2*) - Corrige le problème lié aux images dupliquées après l’importation du produit à partir d’un fichier CSV.
* **MDVA-33382** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige les problèmes d’invalidation des indexeurs après la suppression de produits d’une catégorie.
* **MDVA-28511** (*pour Adobe Commerce >=2.3.5 &lt;2.3.6*) - Corrige le problème en raison duquel il n’est pas possible de terminer [!DNL PayPal] extraction si le champ Nom contient certains caractères (comme des majuscules).
* **MDVA-31519** (*pour Adobe Commerce >=2.3.5 &lt;2.3.6*) - Corrige le problème des délais d’attente dans le passage en caisse des invités lorsqu’une règle de vente à l’échelle du site est en cours d’utilisation.
* **MDVA-33281** (*pour Adobe Commerce >=2.3.4 &lt;2.3.6*) - Corrige le problème d’erreur fatale dans `inventory:reservation:list-inconsistencies` en raison d’un type de paramètre de SKU incorrect.
* **MDVA-24201** (*pour Adobe Commerce >=2.3.0 &lt;2.3.5*) - Corrige le problème en raison duquel les prix ne reflètent pas la règle de prix de panier planifiée tant qu’ils n’ont pas été réindexés manuellement.
* **MDVA-32694** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6 || >= 2.4.0 &lt;2.4.2*) - Correction du problème en raison duquel un utilisateur administrateur ne peut pas ajouter un produit à un devis négociable s’il est lié à un magasin autre que celui par défaut.
* **MDVA-33516** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6*) - Corrige le problème en raison duquel la modification d’un produit groupé dans une liste de demandes d’approvisionnement entraîne une erreur.
* **MDVA-33975** (*pour Adobe Commerce >=2.3.4 &lt;2.4.2*) - Corrige plusieurs problèmes liés au calcul du prix dans les requêtes GraphQL.

## v1.0.13 {#v1-0-13}

* **MDVA-30858** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème en raison duquel les rapports de règlement [!DNL PayPal] n’étaient pas disponibles sous **Rapports** > **Ventes** > Règlement **[!DNL PayPal]** comme prévu.
* **MCP-87** (*pour Adobe Commerce >=2.3.1 &lt;2.4.2*) - Amélioration du temps d’indexation des produits et des indexeurs de stock de catégorie pour les profils volumineux.
* **MDVA-33106** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige le problème en raison duquel les modifications de produit replanifiées sont effacées après l’exécution de la commande cron `run`.
* **MDVA-19391** (*pour Adobe Commerce >=2.3.0 &lt;2.3.5*) - Correction du problème en raison duquel `analytics_collect_data` renvoie une erreur en raison d’enregistrements de description NULL dans la table `catalog_category_entity_text`.
* **MDVA-20376** (*pour Adobe Commerce >=2.3.2 &lt;2.3.4*) - Corrige le problème lié à l’erreur *Aucune entité de ce type avec customerId = 1* dans le `exception.log` pour les clients connectés après le placement de la commande.
* **MDVA-23764** (*pour Adobe Commerce >=2.3.2 &lt;2.3.5*) - Corrige le bug dans les `JsFooterPlugin.php` qui affecte l’affichage des blocs dynamiques.
* **MDVA-13203** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige le problème en raison duquel l’erreur *table search_tmp_ pour la violation des contraintes d’intégrité* s’affiche après une réindexation complète.
* **MDVA-23426** (*pour Adobe Commerce >=2.3.3 &lt;2.3.5*) - Correction du problème où les e-mails de notification envoyés par Adobe Commerce contiennent un corps vide avec du contenu ajouté en tant que pièce jointe.
* **MDVA-22150** (*pour Adobe Commerce >=2.3.1 &lt;2.3.4*) - Correction du problème en raison duquel les clients disposant d’un produit configurable dans le panier et d’un coupon appliqué ne peuvent pas se connecter si ce produit configurable est désactivé dans l’administration.
* **MDVA-32545** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige le problème en raison duquel les factures ne sont pas envoyées automatiquement lors de la création de commandes à partir de l’administrateur.
* **MDVA-32714** (*pour Adobe Commerce >=2.3.4 &lt;2.4.1*) - Correction d’un problème en raison duquel le prix du groupe client ne fonctionne pas dans la requête de produit GraphQL.

## v1.0.12 {#v1-0-12}

* **MDVA-31399** (*pour Adobe Commerce >=2.3.2 &lt;2.4.2*) - Ajoute le *Sous-total (y compris Taxe)* option pour les conditions de règle de prix.
* **MDVA-31236** (*pour Adobe Commerce >=2.4.0 &lt;2.4.2*) - Correction du problème en raison duquel les administrateurs disposant d’un accès aux ressources personnalisées ne peuvent pas configurer 2FA ni se connecter.
* **MDVA-30845** (*pour Adobe Commerce >=2.3.5 &lt;2.3.7*) - Correction du problème en raison duquel la *Désolé, aucun devis n&#39;est disponible pour cette commande à ce stade* une erreur s&#39;affiche lorsque vous ne parvenez pas à vous connecter à UPS XML/USPS/DHL et aucune autre méthode d&#39;expédition n&#39;est disponible.
* **MDVA-32133** (*pour Adobe Commerce >=2.4.0 &lt;2.4.1*) - Corrige le problème en raison duquel la galerie multimédia ne se charge pas à partir de Page Builder dans certains cas.
* **MDVA-12304** (*pour Adobe Commerce >=2.3.0*) - Augmente le nombre maximal de cookies de 50 à 200.
* **MDVA-32632** (*pour Adobe Commerce >=2.3.2 &lt;2.3.5*) - Correction du problème d’affichage des ordres dans le système de paiement, mais pas dans Adobe Commerce.
* **MDVA-32449** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || >=2.4.1 &lt;2.4.2 avec extension B2B*) - Corrige le problème en raison duquel l’historique de commandes se charge très lentement ou ne se charge pas du tout.
* **MDVA-32739** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème en raison duquel l’activation des notifications par e-mail asynchrones envoie d’anciens e-mails de vente.

## v1.0.11 {#v1-0-11}

* **MC-38509** (*pour Adobe Commerce 2.3.6, 2.4.1*) - Correction du problème en raison duquel le bouton *Créer un compte* reste désactivé après la correction de données non valides dans le formulaire *Créer un compte client*.
* **MDVA-31006** (*pour Adobe Commerce 2.3.0, 2.3.1*) - Correction du problème d’affichage des commandes en double après le passage d’une commande à l’aide d’un paiement [!DNL Paypal Express].
* **MDVA-25602** (*pour Adobe Commerce 2.3.0*) - Correction d’[!DNL PayPal Payflow Pro] problème lié au mode de paiement et au traitement des cookies comme `SameSite=Lax` par défaut dans le navigateur Chrome 80 et la redirection de la réponse de l’API vers la page de connexion du client.

## v1.0.10 {#v1-0-10}

Correctifs mineurs pour les versions de correctifs

## v1.0.9 {#v1-0-9}

* **MDVA-31363** (*pour Adobe Commerce >=2.3.2 &lt;2.4.2*) - Correction du problème en raison duquel la règle de prix de panier avec coupon ne s’applique pas via GraphQL lorsque l’action *Remise de montant fixe pour l’ensemble du panier* est utilisée.
* **MDVA-30889** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige le problème où une erreur se produit après la facturation d’un bundle avec des produits simples et virtuels comme options.
* **MDVA-31791** (*pour Adobe Commerce >=2.3.4 &lt;2.3.5*) - Améliore les performances de la page produit dans les cas où des règles cible ou des produits liés sont utilisés.
* **MDVA-31168** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige le problème en raison duquel le fichier CSV d’exportation du produit n’apparaît pas et une erreur d’allocation de mémoire se produit.
* **MDVA-32313** (*pour Adobe Commerce >=2.3.0 &lt;2.3.4*) - Correction du problème en raison duquel des produits configurables pouvaient être ajoutés à la liste de souhaits avec les mauvaises options de configuration.
* **MDVA-31759** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème où les produits ne sont pas mis à jour avec les valeurs d’attribut *dropdown* et *textarea* lors de l’importation du fichier CSV.
* **MDVA-32012** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige le problème en raison duquel les codes postaux en Corée et en Argentine ne peuvent pas être validés.
* **MDVA-31640** (*pour Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) - Correction du problème en raison duquel un prix spécial ne peut pas être mis à jour via l’API REST.
* **MDVA-28651** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6 || >2.4.0 avec extension B2B*) - Correction du problème de performances lié au chargement de devis négociables via l’API REST.

## v1.0.8 {#v1-0-8}

* **MDVA-31242** (*pour Adobe Commerce >=2.3.0 &lt;2.4.1 avec extension B2B*) - Corrige le problème d’affichage d’un signe de devise incorrect dans la grille d’avoir.
* **MDVA-31295** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige le problème où les points de récompense ne sont pas calculés lorsqu’une commande partielle est terminée et que les articles sont taxés.
* **MDVA-30112** (*pour Adobe Commerce >=2.3.4 &lt;2.4.2*) - Correction du problème en raison duquel, si le nombre de commandes dépasse la valeur *taille-lot*, Adobe Commerce considère les commandes avec le statut *en attente* comme des incohérences.
* **MDVA-31150** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème en raison duquel les soldes des cartes de crédit et des cartes cadeaux du magasin ne sont pas renvoyés par l’appel API REST de GET Invoice, lorsque la facture a été validée par l’appel API REST et que la commande a été partiellement payée par les comptes de carte de crédit et de carte cadeau du magasin.
* **MDVA-30963** (*pour Adobe Commerce >=2.3.2 &lt;2.4.2*) - Correction du problème en raison duquel les résultats de filtrage des produits définis sur contiennent uniquement les valeurs spécifiées pour la portée *Toutes les vues de magasin* dans l’administration, incluent les produits dont les valeurs sont remplacées au niveau de la vue de magasin.
* **MDVA-29954** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || 2.4.2 avec extension B2B*) - Correction du problème en raison duquel les e-mails *Nouvelle demande d’enregistrement de l’entreprise* et *Vous avez été lié à une entreprise* sont envoyés à la mauvaise adresse.
* **MDVA-28357** (*pour Adobe Commerce >=2.3.2 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) - Remplace l’analyseur standard par un analyseur personnalisé avec un jeton de mot-clé pour le champ SKU dans l’index de [!DNL ElasticSearch] afin que les requêtes de recherche par caractères génériques fonctionnent avec les SKU contenant un trait d’union (« - »).

## v1.0.7 {#v1-0-7}

* **MDVA-30972** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème en raison duquel le statut de la commande personnalisée était remplacé par *Traitement* après la création partielle d’une expédition à l’aide de WebApi.
* **MDVA-30428** (*pour Adobe Commerce >=2.3.4 &lt;2.3.5*) - Correction du problème en raison duquel les clients ne peuvent pas ajouter un produit à leur liste de souhaits si ce produit est affecté à une source d’inventaire personnalisée.
* **MDVA-30594** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige le problème en raison duquel une commande comportant plusieurs adresses n’a pas pu être enregistrée pendant la phase de passage en caisse lorsque le protocole FPT est configuré.
* **MDVA-29148** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème lors de la création d’un produit via un appel API, l’attribut personnalisé de produit de type `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (comme Multiselect) n’utilise pas sa valeur par défaut si aucune valeur n’était fournie dans la payload.
* **MDVA-30837** (*pour Adobe Commerce >=2.3.1 &lt;2.3.5*) - Ajout d’un paramètre de configuration *Inclure la taxe dans le montant : Oui/Non* dans la configuration du mode d’expédition gratuite. Lorsque *Inclure la taxe au montant* est défini sur *Oui*, le montant minimum de la commande est calculé comme suit : Sous-total + taxe. Lorsque *Inclure la taxe au montant* est défini sur *Non*, le montant minimum de la commande est calculé comme un sous-total
* **MDVA-25028** (*pour Adobe Commerce >=2.3.2 &lt;2.3.3 || >=2.3.5 &lt;2.3.6*) - Correction du problème en raison duquel les commandes passées à l’aide de [!DNL PayPal Payflow Pro] ne sont pas définies sur le statut Fraude suspectée lorsque des filtres de fraude sont déclenchés.
* **MDVA-31224** (*pour Adobe Commerce >=2.3.3 &lt;2.3.5*) - Améliore les performances de l’opération de réindexation `catalog_product_price` pour les produits groupés.
* **MDVA-31321** (*pour Adobe Commerce >=2.3.2 &lt;2.3.5*) - Corrige une page vierge (erreur) lorsque *Tout afficher* est sélectionné. [!DNL Elasticsearch] renvoie une liste volumineuse d’identifiants de produit. Dans ce scénario, la clause order by est convertie dans un format SQL incorrect.
* **MDVA-30815** (*pour Adobe Commerce >=2.3.2 &lt;2.3.4*) - Correction du problème en raison duquel, lorsque vous modifiez le nombre de résultats de recherche à afficher sur la page des résultats de recherche, Adobe Commerce affiche une page vierge. [!DNL Elasticsearch] affiche désormais correctement les résultats des pages de catégorie lorsque vous modifiez le nombre de résultats de recherche affichés par page.
* **MDVA-30782** (*pour Adobe Commerce >=2.3.5 &lt;2.4.2*) - Corrige le problème d’affichage du bloc dynamique quelle que soit la règle du panier.
* **MDVA-31021** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige le problème lié aux problèmes de performances dans `module-catalog-import-export/Model/Import/Product/Option.php`. S’il y a plus de 100 000 enregistrements dans `catalog_product_option` tableau, la validation d’un nouveau fichier CSV avec un seul produit prend moins de 10 secondes.
* **MDVA-31007** (*pour Adobe Commerce >=2.4.0 &lt;2.4.1*) - Correction d’un problème en raison duquel les attributs d’adresse personnalisée ne s’affichaient pas correctement dans la page des détails de la commande dans la zone Mon compte et sur le serveur principal.
* **MDVA-29389** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème lié aux rapports avancés où la tâche cron `analytics_collect_data` indique : *Le port doit être configuré dans le paramètre de l’hôte (comme localhost:3306)*.
* **MDVA-31343** (*pour Adobe Commerce >=2.3.4 &lt;2.3.6*) - Corrige le problème lié au `page-layout-category-full-width` de classe de corps supprimé lorsqu’une catégorie est planifiée.
* **MDVA-30945** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige le problème en raison duquel vous recevez un message d’erreur irrécupérable lors de la mise à jour des `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php` de panier.

## v1.0.6 {#v1-0-6}

* **MDVA-28993** (*pour Adobe Commerce >=2.3.4 &lt;2.4.0*) - Implémente la fonctionnalité *La valeur minimale doit correspondre* et la recherche partielle [!DNL Elasticsearch] moteur. Résout les problèmes liés aux tirets dans les requêtes de recherche.
* **MDVA-30102** (*pour Adobe Commerce >=2.3.2 &lt;=2.4.0*) - Correction du problème en raison duquel le cache Redis augmente rapidement, car les caches de disposition n’ont pas de TTL.
* **MDVA-30599** (*pour Adobe Commerce >=2.3.4 &lt;=2.4.0*) - Correction du problème en raison duquel les devis d’invités créés à l’aide de l’API sont incorrectement marqués comme devis pour les clients connectés.
* **MDVA-29446** (*pour Adobe Commerce >=2.3.3 &lt;=2.4.0*) - Corrige le problème en raison duquel le prix d’un mode d’expédition non applicable est indiqué comme zéro lors du passage en caisse.
* **MDVA-30357** (*pour Adobe Commerce >=2.3.2 &lt;=2.4.0*) - Correction du problème en raison duquel des URL d’image incorrectes sont créées lors de la génération d’un plan de site par cron.
* **MDVA-30565** (*pour Adobe Commerce >=2.3.2 &lt;=2.3.3-p1*) - Correction du problème où *Aucune entité de ce type avec l’erreur cartid = 0* ne s’affiche pour le client invité lors du passage en caisse du storefront si le panier persistant est activé.
* **MDVA-29787** (*pour Adobe Commerce >=2.3.0 &lt;=2.4.0*) - Correction du problème en raison duquel la règle cible pour les produits associés ne fonctionne pas lorsque *est l’une des* conditions est utilisée pour définir les produits à afficher.
* **MDVA-30977** (*pour Adobe Commerce >=2.3.4 &lt;=2.3.5-p2*) - Corrige le problème en raison duquel les produits aléatoires étaient absents des catégories après la réindexation.
* **MDVA-28202** (*pour Adobe Commerce >=2.3.4 &lt;=2.4.2*) - Correction du problème en raison duquel la navigation par couches ne filtre pas correctement les produits configurables lorsque MSI est utilisé.
* **MDVA-28300** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6*) - Correction du problème en raison duquel la requête GQL ne reflète pas les modifications de prix des règles de prix de catalogue.
* **MDVA-31006** (*pour Adobe Commerce >=2.3.2 &lt;=2.4.2*) - Correction du problème d’apparition de commandes en double après le passage d’une commande à l’aide d’un paiement [!DNL Paypal Express].

## v1.0.5 {#v1-0-5}

* **MDVA-30841** (*pour Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Correction du problème lié à la navigation par couches, où la valeur *Non* pour les attributs de produit de type booléen n’était pas incluse dans la navigation par couches si [!DNL Elasticsearch] était utilisée comme moteur de recherche.
* **MDVA-28191** (*pour Adobe Commerce >=2.3.3 &lt;2.4.2*) - Corrige le problème en raison duquel aucun mode de paiement n’est chargé lors de la création de la commande via l’administrateur.
* **MDVA-29959** (*pour Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 avec extension B2B*) - Correction du problème en raison duquel un utilisateur administrateur restreint disposant d’autorisations *Entreprises* n’est pas autorisé à supprimer le compte d’entreprise.
* **MDVA-30265** (*pour Adobe Commerce >=2.3.3 &lt;2.4.2*) - Corrige le problème en raison duquel le lien de suivi des expéditions cesse de fonctionner après la création de la facture.
* **MDVA-28409** (*pour Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Correction du problème d’échec de la tâche cron `sales_clean_quotes` avec une erreur *mémoire insuffisante* lorsque le nombre de guillemets expirés dans la base de données est énorme.
* **MDVA-30593** (*pour Adobe Commerce >=2.3.0 &lt;2.3.4*) - Correction du problème en raison duquel les devis ayant expiré en fonction du paramètre Durée de vie du devis ne sont pas nettoyés.
* **MDVA-30107** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6*) - Correction d’un problème en raison duquel le sélecteur de boutique ne fonctionne pas comme prévu si différentes URL de base sont utilisées pour les vues de boutique.
* **MDVA-28763** (*pour Adobe Commerce >=2.3.2 &lt;2.3.4*) - Correction du problème de duplication d’images de produit après plusieurs mises à jour des informations de produit à l’aide de l’API REST.
* **MDVA-30284** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème en raison duquel l’indexeur de la recherche catalogue échoue en raison de l’erreur *[!DNL Elasticsearch]suivante : la limite du nombre total de champs de l’index a été dépassée.*
* **MDVA-29042** (*pour Adobe Commerce >=2.3.3 &lt;=2.3.4-p2 avec extension B2B*) - Corrige le problème où les autorisations du catalogue étaient modifiées en *Autoriser* automatiquement après l’ajout d’un nouveau produit au catalogue partagé.
* **MDVA-30428** (*pour Adobe Commerce >=2.3.3 &lt;2.4.2*) - Correction du problème en raison duquel les clients ne peuvent pas ajouter un produit à leur liste de souhaits si ce produit est affecté à une source d’inventaire personnalisée.
* **MDVA-28661** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2 avec extension B2B*) - Corrige le problème où une erreur est générée dans la section Compte d’entreprise des utilisateurs de l’entreprise après la modification de l’administrateur de l’entreprise.

## v1.0.4 {#v1-0-4}

* **MDVA-30195** (*pour Adobe Commerce 2.3.1 - 2.3.4-p2*) - Correction du problème en raison duquel les tâches cron échouent si le nom de la base de données est trop long, ce qui entraîne la non-mise à jour des catégories sur le front-end.
* **MDVA-30106** (*pour Adobe Commerce ^2.3.0*) - Correction d’un problème en raison duquel les paiements ne sont pas chargés avec l’erreur *Impossible de lire la propriété &#39;longueur&#39; de null* dans la console JS.
* **MDVA-28656** (*pour Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.2*) - Correction du problème en raison duquel, si une commande a été passée sans informations de paiement requises (avec une remise de 100 %, par exemple) et qu’une facture a été créée pour la commande, le statut de la commande passe à *Fermée* au lieu de Terminée.
* **MDVA-30209** (*pour Adobe Commerce 2.3.0 - 2.3.3-p1*) - Correction du problème en raison duquel le groupe de clients était remplacé par défaut si le client mettait à jour ses informations de compte.
* **MDVA-30123** (*pour Adobe Commerce >=2.3.4 &lt;2.4.2*) - Correction d’un problème en raison duquel les libellés d’option d’attribut ne sont pas traduits correctement pour les requêtes GraphQL.
* **MDVA-29996** (*pour Adobe Commerce >=2.3.3 &lt;2.4.2*) - Correction du problème en raison duquel, après l’activation de l’autorisation de catégorie, la page de catégorie n’est pas mise en cache par le cache de page complète.
* **MDVA-30164** (*pour Adobe Commerce >=2.3.1 &lt;2.4.2*) - Corrige le problème en raison duquel les enregistrements des clients ne peuvent pas être exportés à partir de la grille des clients s’il existe des attributs de client personnalisés.
* **MDVA-30444** (*pour Adobe Commerce >=2.3.0 &lt;2.4.1*) - Correction du problème en raison duquel aucun e-mail de confirmation n’est envoyé pour les commandes passées à l’aide de GraphQL.
* **MDVA-30490** (*pour Adobe Commerce 2.3.4 - 2.3.5-p2*) - Correction du problème en raison duquel la comparaison de produits renvoie la page d’erreur 500 si l’un des produits comporte une description courte vide.
* **MDVA-30232** (*pour Adobe Commerce >=2.3.1 &lt;2.4.1*) - Corrige le problème en raison duquel il n’est pas possible de commander à nouveau si la commande d’origine contient une carte cadeau.
* **MDVA-29965** (*pour Adobe Commerce >=2.3.3 &lt;2.4.0*) - Correction du problème en raison duquel les clients et les clientes obtenaient une erreur de clé de formulaire non valide lors de l’ajout d’un produit au panier.
* **MDVA-30008** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème B2B en raison duquel il n’est pas possible de passer des commandes via l’API d’administration pour un produit qui se trouve dans un catalogue public.
* **MDVA-22469** (*pour Adobe Commerce 2.3.2-p2 - 2.3.3-p1*) - Correction du problème en raison duquel, après la mise à niveau vers Adobe Commerce 2.3.3, Page Builder ne fonctionne pas dans le panneau d’administration et certains fichiers JS et CSS ne se chargent pas.
* **MC-35984** (*pour Adobe Commerce >=2.4.0 &lt;2.4.1*) - Correction du problème en raison duquel les commerçants ne pouvaient pas interagir avec les éléments de page de la page Retours après la création d’une étiquette d’expédition pour une autorisation de retour de marchandise (RMA).

## v1.0.3 {#v1-0-3}

* **MDVA-25602** (*pour Adobe Commerce 2.3.0 - 2.3.4*) - Correction du problème lié à [!DNL PayPal Payflow Pro] méthode de paiement et au traitement des cookies comme `SameSite=Lax` par défaut dans le navigateur Chrome 80 et la redirection de la réponse de l’API vers la page de connexion du client.
* **MDVA-26694** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0*) - Corrige le problème en raison duquel les caches de produits et de catalogues expirent quotidiennement, même si leur expiration est planifiée différemment.
* **MDVA-27825** (*pour Adobe Commerce >=2.3.0 &lt;2.4.1*) - Correction du problème en raison duquel l’exportation de gros volumes de données a échoué en raison d’une fuite de mémoire.
* **MDVA-29085** (*pour Adobe Commerce >=2.3.0 &lt;=2.3.5-p1*) - Correction du problème B2B en raison duquel aucun e-mail de nouvelle société obligatoire n’est envoyé si une société est créée par API.
* **MDVA-29344** (*pour Adobe Commerce >=2.3.5 &lt;=2.4.0-p1*) - Corrige le problème en raison duquel Page Builder est bloqué après avoir copié du texte d’un élément d’en-tête vers un élément de texte.
* **MDVA-29835** (*pour Adobe Commerce >2.3.1 &lt;2.4.2*) - Correction du problème en raison duquel les commandes de cartes-cadeaux contenaient deux codes au lieu d’un.
* **MDVA-30052** (*pour Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - Correction d’un problème en raison duquel le contenu privé (stockage local) n’était pas correctement renseigné, ce qui entraînait des problèmes de performances.
* **MDVA-30131** (*pour Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Correction du problème lié à la navigation par couches, où la valeur *Non* pour les attributs de produit de type booléen n’était pas incluse dans la navigation par couches si [!DNL Elasticsearch] était utilisée comme moteur de recherche.
* **MDVA-35514** (*pour Adobe Commerce >=2.4.0 &lt;2.4.1*) - Correction du problème lié à la création d’une étiquette d’expédition et à l’ajout de produits commandés à un package dans la fenêtre modale Créer des packages.
