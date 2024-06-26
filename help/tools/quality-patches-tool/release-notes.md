---
title: Notes de mise à jour
description: Découvrez les correctifs disponibles pour Adobe Commerce et les problèmes qu’ils résolvent.
exl-id: 22262555-f5ea-49ad-98ad-ea8428ef66d5
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '20485'
ht-degree: 0%

---

# Notes de mise à jour

La variable [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) fournit des correctifs individuels développés par Adobe et la communauté Magento Open Source. Il vous permet d’appliquer, de rétablir et d’afficher des informations générales sur tous les correctifs individuels disponibles pour la version installée d’Adobe Commerce. Vous pouvez appliquer des correctifs aux projets Adobe Commerce et Magento Open Source, quel que soit le développeur du correctif. Par exemple, vous pouvez appliquer un correctif développé par la communauté aux projets Adobe Commerce.

>[!INFO]
>
>Voir [Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches) pour obtenir des instructions sur l’application de correctifs à vos projets Adobe Commerce. Voir [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le Guide de mise à jour du logiciel pour consulter la liste complète des correctifs publiés.

>[!INFO]
>
>Pour plus d’informations sur [!DNL quality patches] créé par la communauté pour Magento Open Source, voir la section [notes de mise à jour](https://github.com/magento/quality-patches/blob/master/community-release-notes.md).

## v1.1.48 {#v1-1-48}

* **ACSD-55566** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème en raison duquel la variable `mergeCart` la mutation échoue avec un &quot;*Erreur interne du serveur*&quot; dans la variable [!DNL GraphQL] lors de la fusion des paniers source et de destination ayant les mêmes éléments de lot.
* **ACSD-56546** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème d’affichage des produits configurables et groupés en tant que **En rupture de stock** sur le storefront lorsque la variable **affichage d’une configuration de produit obsolète** is *Désactivé*.
* **ACSD-56635** (pour Adobe Commerce >=2.4.6 &lt;2.4.7) - Correction du problème de duplication du client importé avec la même adresse électronique, lorsqu’un import est utilisé avec **partage de compte** défini sur *Global*.
* **ACSD-56741** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du message d’erreur &quot;*Tentative d’accès au décalage du tableau sur la valeur de type null*&quot; qui s’affiche pendant `setup:upgrade` lorsque la base de données contient une [!DNL MySQL] déclencheur non lié au mécanisme d’indexation et [!DNL MView].
* **ACSD-57315** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème lors de la création d’une transaction dans [!DNL PayPal Payflow Pro] chaque fois que la fonction [!UICONTROL Fetch] Cliquez sur le bouton . **[!UICONTROL View transaction]** dans l’écran Admin.
* **ACSD-57337** (pour Adobe Commerce >=2.4.4 &lt;2.4.6) - Correction du problème en raison duquel un utilisateur administrateur avec des restrictions d’accès à des sites web spécifiques pouvait voir des entreprises de tous les sites web dans la variable **[!UICONTROL Companies]** grid.
* **ACSD-57394** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème de tri incorrect des produits selon plusieurs champs de tri dans [!DNL GraphQL].
* **ACSD-57565** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel la variable **[!UICONTROL Order]** Le tableau de bord affiche des informations de commande incorrectes jusqu’à ce que la période soit mise à jour. Le tableau de bord affiche désormais les statistiques de commande correctes au premier chargement.
* **ACSD-57854** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème lors de l’utilisation du produit [!DNL GraphQL] les demandes renvoyaient des catégories désactivées dans les agrégations de catégories.
* **ACSD-58008** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel la mise à jour d’une mise à jour planifiée supprimait la version précédente d’un élément intermédiaire, si aucune date de fin n’était spécifiée.
* Correctifs mis à jour : MDVA-39305-V2, ACSD-48627, ACSD-54965

## v1.1.47 {#v1-1-47}

* **ACSD-55241** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel *[!UICONTROL Used]* et *[!UICONTROL Times Used]* Les attributs affichent des valeurs incorrectes pour les bons générés lorsqu’ils sont utilisés lors du passage en caisse avec plusieurs adresses.
* **ACSD-56760** (pour Adobe Commerce >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel un utilisateur administrateur limité à un site web spécifique ne pouvait pas trier ou ajouter de nouveaux produits dans une catégorie si le magasin web avait sa propre catégorie racine.
* **ACSD-56858** (pour Adobe Commerce >=2.4.2 &lt;2.4.7) - Correction du problème d’affichage incorrect des autorisations de rôle d’entreprise B2B pour un administrateur de société restreint.
* **ACSD-57074** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel la variable *Oui/Non* attribut personnalisé avec `attrbute_code` en commençant par `price_` ne fonctionne pas correctement avec l’indexation, et les produits avec de tels attributs ne sont pas disponibles au front-end.
* Correctifs mis à jour : ACSD-53378, ACSD-51819

## v1.1.46 {#v1-1-46}

* **ACSD-46767** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème en raison duquel la page de catégorie était mise en cache invalide lorsque la quantité en stock changeait, même si le produit était toujours en stock.
* **ACSD-54656** (pour Adobe Commerce >=2.4.5 &lt;2.4.6) - Correction du problème d’échec du recaptcha invisible lors de l’extraction, empêchant le placement d’une commande.
* **ACSD-55100** (pour Adobe Commerce >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel GraphQL ne renvoie pas plus de 10 000 produits dans les résultats de recherche.
* **ACSD-56621** (pour Adobe Commerce >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel le prénom et le nom mis à jour ne sont pas reflétés dans la section d’en-tête des salutations pour l’utilisateur administrateur de la société.
* **ACSD-56842** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel les proxies différées et les usines de proxy différées manquaient après l’exécution. `setup:di:compile`.
* **ACSD-57003** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel l’état de la commande était remplacé par *[!UICONTROL Complete]* au lieu d’être remplacé par *[!UICONTROL Processing]* lorsqu’une commande est partiellement remboursée et expédiée.
* Correctifs mis à jour : ACSD-50260-v2, ACSD-54966

## v1.1.45 {#v1-1-45}

* **ACSD-56886** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème qui entraînait l’rupture de stock d’un produit configurable lorsqu’un des deux produits enfants était désactivé par une mise à jour planifiée.
* **ACSD-56616** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction du problème en raison duquel les produits regroupés s’affichent comme en stock sur le storefront lorsque leurs produits simples sont en rupture de stock.
* **ACSD-56515** (pour Adobe Commerce >=2.4.2 &lt;2.4.7) - Correction du problème qui empêchait l’administrateur disposant d’autorisations au niveau du site web d’ajouter ou de modifier un bloc dynamique.
* **ACSD-56447** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel l’ajout d’un même produit au panier via des demandes d’API Web REST parallèles générait deux éléments distincts dans le panier.
* **ACSD-56415** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème de ralentissement des performances de l’indexation de prix partielle en raison d’une erreur `DELETE` requête lorsque la base de données contient de nombreuses données de prix partielles à indexer.
* **ACSD-54965** (pour Adobe Commerce >=2.4.5 &lt;2.4.6) - Correction du problème en raison duquel la grille de marchandisage visuel n’affichait pas le stock correct lorsqu’un produit était affecté à un stock personnalisé uniquement.
* **ACSD-52824** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel les boutons PayPal Express, Google Pay et Apple Pay s’affichaient pour les clients de l’entreprise lorsque ces méthodes de paiement étaient désactivées dans les paramètres de l’entreprise.
* Correctifs mis à jour : ACSD-56193

## v1.1.44 {#v1-1-44}

* **ACSD-56790** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème où un utilisateur est redirigé vers le tableau de bord administrateur lors du tri des produits de catégorie à l’aide de la variable **Sortir du stock vers le bas** et la variable `Invalid security or form key. Please refresh the page` s’affiche en haut de l’écran.
* **ACSD-56280** (pour Adobe Commerce >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel la commande d’éléments à partir d’un registre de cadeaux générait une exception.
* **ACSD-56246** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème de suppression des données de l’attribut de sélection multiple personnalisé lorsqu’une mise à jour planifiée d’un produit devient active.
* **ACSD-56193** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4) - Correction du problème en raison duquel le cache de vernis/de jeûne n’était pas mis à jour lorsqu’un bloc planifié était utilisé dans la description de catégorie à l’aide du générateur de pages.
* **ACSD-56158** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel la requête &quot;panier&quot; renvoyait la valeur de taxe totale pour chaque règle de taxe.
* **ACSD-56023** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel le contenu du widget n’était pas mis à jour sur la page CMS lorsque le cache était activé.
* **ACSD-55427** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel l’utilisateur administrateur ne pouvait pas annuler l’affectation d’un produit d’un catalogue partagé à partir de la page de produit dans l’administrateur.
* **ACSD-55352** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) : corrige le problème en raison duquel, après la création d’une note de crédit partielle avec des points de récompense client, les options d’état de la commande sont Fermées et les options de note de crédit disparaissent de la page de commande d’administrateur.
* **ACSD-55231** (pour Adobe Commerce >=2.4.2 &lt;2.4.7) - Correction du problème qui empêchait l’ajout de produits à un panier à l’aide de la fonctionnalité de commande rapide.
* **ACSD-54283** (pour Adobe Commerce >=2.4.3 &lt;2.4.4) - Correction du problème en raison duquel les produits/catégories non affectés au catalogue partagé par défaut (groupe général) étaient toujours inclus dans le plan de site XML.
* Correctifs mis à jour : ACSD-52041, ACSD-54040, ACSD-51819

## v1.1.43 {#v1-1-43}

* **ACSD-54972** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel l’URL de catégorie canonique n’était pas mise à jour après modification de l’URL de catégorie.
* **ACSD-53636** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.5) - Correction du problème en raison duquel le prix normal ne s’affichait pas sur les pages de liste de produits pour les produits configurables ayant des produits enfants avec des prix spéciaux.
* **ACSD-54885** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème lié au passage en caisse de plusieurs adresses lorsque l’utilisateur administrateur utilise la variable *Connexion en tant que client* .
* **ACSD-55610** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel une commande partiellement annulée avait un montant de remise incorrect.
* **ACSD-55334** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction des traductions des libellés via les dictionnaires de traduction dans la réponse GraphQL.
* **ACSD-54739** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel la condition d’état du stock de produit n’était pas appliquée aux règles de produit associées.
* **ACSD-53925** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème qui empêchait l’administrateur d’enregistrer le bloc CMS avec le carrousel de produit lors de la `catalog_product_price` dimensions-mode est défini sur *site web*.
* **ACSD-52714** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel le filtre de date ne fonctionnait pas dans la grille d’administration lorsque le format de date était défini comme *Y-m-d*.
* **ACSD-55055** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Améliore les performances de chargement des attributs de produit dans les règles de prix du panier dans le panier.
* **ACSD-53790** (pour Adobe Commerce >=2.4.6 &lt;2.4.7) - Correction du problème de création de plusieurs RMA pour un seul produit via l’API REST.
* **ACSD-56090** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.5) - Correction du problème en raison duquel la demande GraphQL répondait avec toutes les données des magasins plutôt que avec les données de magasin demandées spécifiquement.
* **ACSD-54983** (pour Adobe Commerce >=2.4.2 &lt;2.4.7) - Correction du problème qui empêchait l’obtention de l’UID de l’utilisateur de l’entreprise avec la requête GraphQL lorsque l’état de l’utilisateur était défini sur *[!UICONTROL Inactive]*.
* **ACSD-53309** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel la taxe n’est pas entièrement appliquée dans la variable *[!UICONTROL Regular Price]* libellé lorsque l’option personnalisable est sélectionnée.
* **ACSD-55305** (pour Adobe Commerce >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel la variable *[!UICONTROL Edit Company User]* dans la fenêtre contextuelle **[!UICONTROL myAccount]** > **[!UICONTROL Company Structure]** se bloque avec un chargeur à l’écran.
* Correctifs mis à jour : ACSD-49013

## v1.1.42 {#v1-1-42}

* **ACSD-53658** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel *[!UICONTROL Recently Viewed]* les données de produit ne sont pas mises à jour correctement dans la vue magasin.
* **ACSD-54626** (pour Adobe Commerce >=2.4.6 &lt;2.4.7) - Correction du problème qui empêchait la création d’une règle de bon de commande (`createPurchaseOrderApprovalRule`) avec la fonction `NUMBER_OF_SKUS` via [!DNL GraphQL].
* **ACSD-53845** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction de la variable [!DNL MySQL] problème de délai de connexion lors de `consumer max_messages` = 0.
* **ACSD-54890** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction du problème en raison duquel `aggregate_sales_report_bestsellers_data` causes [!DNL MySQL] erreurs dues à `/tmp` Le disque manque d’espace.
* **ACSD-55112** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction du problème en raison duquel la variable *[!UICONTROL Submit review]* peut être cliqué plusieurs fois sans [!DNL Google reCAPTCHA v3] validation.
* **ACSD-54264** (pour Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.7) - Correction du problème où le message d’erreur *&quot;Vous ne pouvez pas mettre à jour l’attribut requis. Identifiant de ligne : store_id&quot;* apparaît lorsqu’un client tente d’extraire avec un devis négociable provenant d’une autre vue de magasin.
* **ACSD-54418** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction du problème qui entraînait l’application incorrecte d’un montant fixe de remise à chaque produit enfant du lot à prix dynamique.
* **ACSD-55238** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correctifs de l’enregistrement du produit vide *[!UICONTROL Meta Description]*.
* **ACSD-54966** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème qui empêchait le réutilisation d’un code de bon à usage limité par client en cas d’échec de la commande précédente.
* **ACSD-54060** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème où un administrateur restreint ne peut pas enregistrer un produit s’il est un enfant d’un autre produit affecté à une portée différente.
* **ACSD-48910** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction du problème en raison duquel un produit en regroupement affecté à plusieurs sources était en rupture de stock après la facturation et l’expédition d’une commande, même s’il avait toujours une quantité non nulle.
* **ACSD-55381** (pour Adobe Commerce >=2.4.2 &lt;2.4.7) - Correction d’une erreur de serveur interne lors de l’interrogation `configurable_product_option_uid` et `configurable_product_option_value_uid` des champs de [!DNL B2B] *[!UICONTROL Requisition list]* via [!DNL GraphQL].
* **ACSD-55628** (pour Adobe Commerce >=2.4.4-p2 &lt; 2.4.5) || >=2.4.5-p1 &lt; 2.4.6) - Correction du téléchargement d’un fichier sur le formulaire d’enregistrement de la société et du remplacement d’un fichier pour un attribut du client sur le storefront.
* Correctifs mis à jour : ACSD-51240, ACSD-51890, ACSD-53098

## v1.1.41 {#v1-1-41}

* **ACSD-54376** (pour Adobe Commerce >=2.4.2 &lt;2.4.7) - Correction du problème qui se produit dans le panier lorsqu’un produit est supprimé du catalogue partagé après avoir été ajouté au panier.
* **ACSD-53722** (pour Adobe Commerce >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel le prix des options de produit groupées passe à 0 $ lorsque des mises à jour planifiées pour différentes portées sont actives.
* **ACSD-53643** (pour Adobe Commerce >=2.4.3 &lt;2.4.7) - Correction du problème en raison duquel le total de la commande était incorrect lors du placement d’une commande avec des produits désactivés ou en rupture de stock. Ce problème est résolu en masquant le paramètre *[!UICONTROL Place Order]* pour ces commandes d’achat.
* **ACSD-54067** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction du problème de lecture d’une vidéo de produit sur un appareil mobile.
* **ACSD-55414** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Améliore les performances lorsque la MariaDB tente de convertir l’entity_id du fichier EAV de chaîne en entier.
* **ACSD-51819** (pour Adobe Commerce >=2.4.4 &lt;2.4.4-p4) - Correction du problème en raison duquel plusieurs commandes peuvent être placées avec le même ID de guillemet.
* **ACSD-53118** (pour Adobe Commerce >=2.4.0 &lt;2.4.7) - Correction du problème en raison duquel la variable *[!UICONTROL Cart Price Rule]* est appliqué à l’aide du code de bon alors que le produit a un attribut vide.
* **ACSD-54324** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction d’un problème en raison duquel la demande de liste de demande GraphQL ne prend pas en compte les paramètres de pagination et renvoie tous les résultats.
* Correctifs mis à jour : MDVA-42855-v2

## v1.1.40 {#v1-1-40}

* **ACSD-54680** (pour Adobe Commerce >=2.4.0 &lt;2.4.6) - Correction du problème qui empêchait le traitement d’une citation B2B envoyée pour un produit avec plusieurs sources affectées.
* **ACSD-54040** (pour Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2.4.5-p4 &lt;2.4.6) - Correction du problème en raison duquel la variable *[!UICONTROL Created]* n’est pas renseigné lorsque les modules B2B sont activés.
* **ACSD-54319** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6) - Correction du problème où le prix du produit affichait zéro dans la variable *[!UICONTROL Product in Cart]* rapport.
* **ACSD-53378** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Amélioration du temps de chargement des pages de passage en caisse pour les clients qui disposent de carnets d’adresses volumineux.
* **ACSD-52657** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel le minicart n’est pas mis à jour dans l’aperçu de magasin secondaire, qui utilise un sous-domaine.
* **ACSD-53414** (pour Adobe Commerce >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel un utilisateur administrateur restreint pouvait voir les pages CMS en dehors de leur portée d’autorisation.
* **ACSD-54472** (pour Adobe Commerce >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel les clients d’une société refusée peuvent toujours s’authentifier et les clients d’une société bloquée et rejetée peuvent toujours passer des commandes. Le correctif ajoute une validation supplémentaire pour les points de terminaison GraphQL.
* **ACSD-52801** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) : ajoute l’option permettant d’effectuer une correspondance partielle lors de la recherche de produits dans GraphQL.
* **ACSD-55004** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème de blocage du programme de validation lors du téléchargement d’un fichier d’importation supérieur à la valeur configurée dans `php.ini`.
* **ACSD-54989** (pour Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.7) - Correction du problème qui empêchait l’administrateur d’une entreprise de passer une commande lorsque *[!UICONTROL Enable Purchase Orders]* est défini sur *[!UICONTROL Yes]* et *[!UICONTROL Purchase Order]* est défini sur *[!UICONTROL No]*.
* **ACSD-54007** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction de l’erreur *&quot;Clé de tableau non définie &quot;_scope&quot;* lors de l’importation de données client.
* **ACSD-55031** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction de la variable *Le type &quot;mixte&quot; ne peut pas être nul* lors de la compilation.
* **ACSD-54961** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction du problème qui empêchait un utilisateur administrateur restreint de mettre à jour en masse la variable *Révision du produit* statut.
* **ACSD-55256** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel seule la première image s’affichait correctement dans le curseur de l’image.
* Correctifs mis à jour : ACSD-52041, ACSD-54106

## v1.1.39 {#v1-1-39}

* **ACSD-53704** (pour Adobe Commerce >=2.4.0 &lt;2.4.7) - Correction du problème en raison duquel l’historique d’équilibrage des points de récompense est mal calculé après l’expiration des points de récompense.
* **ACSD-53583** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Améliore les performances de réindexation partielle pour *Produits de catégorie* et *Catégories de produits* indexeurs.
* **ACSD-54026** (pour Adobe Commerce >=2.4.6 &lt;2.4.7) - Correction d’un message d’erreur incorrect pour une `updateCompanyRole` Requête GraphQL pour un utilisateur non autorisé.
* **ACSD-54106** (pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.5) - Correction du problème de tri des produits de catégorie par nom pour les caractères accentués turcs.
* **ACSD-52219** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel les filtres enregistrés des grilles d’administration ne fonctionnaient pas comme prévu lors du basculement fréquent entre les vues de signet.
* **ACSD-54342** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction d’un message d’erreur incorrect *Erreur dans la structure des données : les valeurs sont mixtes* lors de l’importation d’un fichier CSV sans données valides.
* **ACSD-54660** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Ajout d’un nouvel attribut d’entrée *sort* pour trier les commandes client dans GraphQL par `sort_field` et `sort_direction`.
* **ACSD-54776** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction du problème si non coché. *[!UICONTROL Use Default Value]* Les valeurs des champs de produit et autres que par défaut ne sont pas enregistrées pour le deuxième affichage de site web, de magasin et de magasin.
* **ACSD-53998** (pour Adobe Commerce et Magento Open Source >=2.4.4-p2 &lt;2.4.5 || >=2.4.5-p1 &lt;2.4.7) - Correction du problème en raison duquel une **[!UICONTROL Dynamic Block]** basé sur un **[!UICONTROL Customer Segment]** ne fonctionne pas correctement après la déconnexion d’un compte client.
* **ACSD-53204** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correctifs *Le produit ne peut pas être enregistré.* erreur lors de demandes simultanées d’ajout d’images à la galerie de produits à l’aide de la fonction `rest/V1/products/<sku>/media` point de terminaison .
* **ACSD-47657** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Ajout d’un mécanisme de mise en cache pour les informations d’identification AWS. Un fournisseur d’informations d’identification utilise désormais le cache du Magento pour mettre en cache les informations d’identification extraites d’AWS pour la configuration EC2.
* Mise à jour des correctifs : ACSD-51984, ACSD-51574.

## v1.1.38 {#v1-1-38}

* **ACSD-53098** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4) - Correction du problème en raison duquel les produits affectés à un catalogue partagé n’apparaissent pas sur le storefront lors de l’exécution d’un index partiel.
* **ACSD-54018** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.6) - Correction des problèmes de performances avec la variable [!UICONTROL Product List] widget qui utilise un attribut non global dans la condition du widget.
* **ACSD-54111** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6) - Correction du problème qui empêchait l’affichage des miniatures de produit sur le storefront lorsque le rapport d’aspect de l’image de filigrane ne correspond pas à l’image de produit.
* **ACSD-47669** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6) - Correctifs *Violation de contrainte d’intégrité : 1452 Impossible d’ajouter ou de mettre à jour une ligne enfant : une contrainte de clé étrangère échoue* lors de l’importation de produits au format CSV.
* **ACSD-53347** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème où l’indexeur de prix prend trop de temps à s’exécuter.
* **ACSD-52287** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) : corrige le problème lié à un état de commande incorrect dans la grille d’ordre archivée lorsque l’indexation de grille asynchrone est activée.
* **ACSD-52929** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème lié aux demandes redondantes de réindexation des éléments source par défaut lorsque l’indexeur d’inventaire est configuré en mode asynchrone.
* **ACSD-53824** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel `UpdateMultiselectAttributesBackendTypes` le correctif de données de migration dépasse la limite de la taille des transactions de la base de données pendant la durée `setup:upgrade`.

## v1.1.37 {#v1-1-37}

* **ACSD-52613** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème d’actualisation des caches et des index même si aucune mise à jour n’est effectuée sur `Inventory_source` éléments par l’API REST.
* **ACSD-51884** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel le chemin du cache de l’image du produit était incorrect après l’exécution de la commande resize.
* **ACSD-53628** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel le rapport de commande client CSV affichait des caractères spéciaux incorrects.
* **ACSD-53148** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel deux demandes parallèles dans GraphQL pour l’ajout du même produit configurable au panier généraient deux articles distincts sur le panier avec le même SKU de produit.
* **ACSD-52606** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction du problème où le message d’erreur *Votre commande n’est pas prête pour la récupération* s’affiche lorsque l’utilisateur clique **[!UICONTROL Notify Order is Ready for Pickup]**.
* **ACSD-51574** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel l’image n’est pas mise à jour sur le front-end après son remplacement par une autre image portant le même nom.
* **ACSD-53728** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel l’indexation du produit EAV prenait plus de temps.
* **ACSD-53979** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème JS qui se produit sur la page d’accueil si le message de bienvenue contient une seule citation.
* **ACSD-52085** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel un produit configurable avec un prix spécial n’était pas visible dans le carrousel du produit.
* **ACSD-53795** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème lié à un type de données non valide dans `indexer_update_all_views` tâche cron.
* **ACSD-52143** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème de suppression des options personnalisées après l’importation du produit.
* **ACSD-53750** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction de la variable *Canalisation rompue ou connexion fermée* erreur lors d’une opération multi-thread `catalog_product_price` réindexer.
* **ACSD-49843** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.0 || >=2.4.1 &lt;2.4.7) - Correction du problème en raison duquel le lien sur le téléchargement de produit n’est pas disponible une fois que l’article commandé est automatiquement facturé par le mode de paiement en ligne avec la variable **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]** activée.
* **ACSD-47054** (pour Adobe Commerce >=2.4.2 &lt;2.4.6) - Correction du problème en raison duquel la réindexation de l’aperçu s’exécute pour tous les magasins, ce qui entraîne une lenteur.
* Ajout de nouvelles versions pour ACSD-46541, ACSD-47079.
* ACSD-49970-v3 remplacé par ACSD-54095.

## v1.1.36 {#v1-1-36}

* **ACSD-53239** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt; 2.4.6) - Correction du problème en raison duquel l’indexeur d’inventaire nettoie tous les caches en mode Mise à jour lors de la planification.
* **ACSD-50887** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction du problème de propriété de l’attribut de produit *[!UICONTROL Use in Search Results Layered Navigation]* peut être défini sur *Oui* sans le *[!UICONTROL Use in search]* option définie sur *Oui*.
* **ACSD-51846** (pour Adobe Commerce et Magento Open Source >=2.4.3-p2 &lt;2.4.6) - Correction de la variable *Erreur interne* problème qui se produit car tous les niveaux de charge utile de l’API REST ne sont pas validés.
* **ACSD-52906** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction du problème de définition incorrecte du cookie X-Magento-Vary pour les clients connectés qui appartiennent au même segment de client, ce qui entraîne une mise en cache incorrecte de certaines pages.
* **ACSD-52736** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.6) - Correction du problème en raison duquel une *Règle de prix du panier* qui inclut les exigences relatives à la quantité configurable de produits ne fonctionne pas comme prévu.
* **ACSD-47875** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel les utilisateurs administrateurs ne pouvaient pas ajouter de produit au panier d’un client à partir de l’administrateur pour une portée de vue de magasin spécifique avec gestion de l’inventaire.
* **ACSD-53176** (pour Adobe Commerce >=2.3.7 &lt;2.4.5) - Correction du problème en raison duquel *Règle de produit connexe* avec *est l’un des* La condition ne correspond pas aux produits.
* **ACSD-51666** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction de l’erreur *La session a expiré, veuillez vous reconnecter.* cela se produit lorsqu’un client tente de se connecter.
* Ajout de nouvelles versions pour MDVA-39305-v2.
* Mise à jour des exigences pour ACSD-19640.

## v1.1.35 {#v1-1-35}

* **ACSD-51899** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction du problème en raison duquel l’adresse de livraison par défaut à l’étape de livraison du passage en caisse était automatiquement renseignée avec une adresse de récupération en magasin précédemment sélectionnée.
* **ACSD-52041** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème où le message d’erreur : *[ERROR] [!DNL Page Builder] était rendu pendant 5 secondes sans relâcher de verrous.* apparaît dans le navigateur Chrome lors de l’enregistrement de contenu modifié avec [!DNL Page Builder].
* **ACSD-52095** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.6) - Correction du problème en raison duquel la variable `manage_stock` était incorrectement définie sur 0 dans le fichier CSV après l’exportation du produit.
* **ACSD-51358** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel la suppression d’une mise à jour planifiée sans date de fin entraînait la suppression d’autres mises à jour planifiées pour la même entité.
* **ACSD-48070** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel la modification d’une mise à jour planifiée déclenche une exception.
* **ACSD-51890** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction du problème en raison duquel la variable [!UICONTROL Submit review] peut être cliqué plusieurs fois sans [!DNL Google reCAPTCHA] validation v3.
* **ACSD-51984** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction du problème si non coché. *[!UICONTROL Use Default Value]* et *[!UICONTROL non-default product field]* ne sont pas enregistrées pour le deuxième affichage de site web, de magasin et de magasin.
* **ACSD-52398** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction de l’erreur *La quantité demandée n’est pas disponible.* qui se produit lors de la tentative de mise à jour de la quantité d’un produit regroupé dans le panier sur le storefront.
* **ACSD-52786** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction du problème d’une condition de règle de catalogue *SKU est* s’applique à tous les produits commençant par le SKU donné.
* **ACSD-52921** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème d’erreur interne qui se produisait lors de la demande de détails de panier auprès de GraphQL lorsqu’un produit configurable en rupture de stock se trouvait dans le panier.
* **ACSD-51683** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel une option personnalisable ne pouvait pas être ajoutée au panier à l’aide de GraphQL.
* **ACSD-52133** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème qui empêchait l’enregistrement d’un compte client après une mise à niveau.
* **ACSD-52202** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème en raison duquel la quantité vendable du stock par défaut passe incorrectement à 0 lorsqu’un stock autre que le stock par défaut est remplacé par 0 sur l’exécution de la commande.
* **ACSD-51265** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème avec `catalog_product_price` réindexation des performances lorsqu’il y a trop de produits regroupés dans le système.
* **ACSD-52831** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction du problème qui empêchait les clients d’envoyer des commandes de devis négociables lorsque [!DNL Google reCAPTCHA v3 Invisible] est activée.
* **ACSD-51845** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel les produits suivants avec des prix de niveau et différents ensembles d’attributs ne pouvaient pas être mis à jour via l’API REST en bloc asynchrone.
* **ACSD-52815** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel l’entrée pour le champ de quantité d’une source autre que la source par défaut ne prend en charge que 6 chiffres au maximum, contrairement à 8 pour un stock par défaut.
* **ACSD-51149** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel ImportExport planifié avec les autorisations de catalogue activées invalide les indexeurs, puis vident le cache par cron.
* **ACSD-50815** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction du problème en raison duquel la quantité décimale pour un produit simple ne peut pas être utilisée pour une nouvelle option Produit groupé .
* Mise à jour des versions pour ACSD-47803.
* Titre mis à jour pour ACSD-51892.
* Mise à jour de ACSD-51379.
* Mise à jour de ACSD-49970-v2.

## v1.1.34 {#v1-1-34}

* **ACSD-52277** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction du problème en raison duquel un utilisateur administrateur n’était pas redirigé correctement après avoir sélectionné une vue de magasin lors de la création d’une commande dans Admin.
* **ACSD-50813** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction du problème qui empêchait l’administrateur d’ajouter des produits groupés contenant une barre oblique dans le SKU avec la variable [!UICONTROL Add Products by SKU] à l’ordre d’administration.
* **ACSD-51630** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème en raison duquel un grand nombre de messages système ralentissait le téléchargement des pages d’administration.
* **ACSD-51853** (pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.7) - Correction du problème en raison duquel les styles de texte copiés ne sont pas appliqués lors de l’utilisation de la fonction [!UICONTROL Page Builder].
* **ACSD-52160** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème en raison duquel le résultat de la validation du produit par rapport à la règle de prix du panier n’était pas correctement évalué en fonction de la condition de la règle &quot;Si un article est TROUVÉ/INTROUVABLE dans le panier avec toutes/toutes ces conditions vraies&quot;.
* **ACSD-51636** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel l’administrateur de l’entreprise ne pouvait pas ajouter de nouveaux utilisateurs à partir de la section du compte client, même s’il disposait de tous les rôles et autorisations nécessaires.
* **ACSD-51739** (pour Adobe Commerce >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel une erreur était renvoyée lorsque la variable `structure_id` est demandé dans une requête GraphQL CompanyTeam .
* **ACSD-51857** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction du problème de lenteur des performances de la variable `aggregate_sales_report_bestsellers_data` rapport cron sur les commandes importantes et `sales_order_item` les tables de base de données étaient dues à la manière dont la requête de données principale était écrite.
* **ACSD-48448** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Résout le problème en raison duquel un problème de condition de concurrence se produit lors des annulations de commande, ce qui entraîne une entrée dupliquée dans la variable `inventory_reservation` table.
* **ACSD-52689** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.6) - Correction du problème qui empêchait le téléchargement des images vers le stockage Amazon S3 à l’aide de l’API REST.
* **B2B-2674** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Ajoutez la fonctionnalité de mise en cache à la requête GraphQL 1customAttributeMetadata1 .
* Ajout de nouvelles versions pour ACSD-44938.
* Ajout des exigences pour ACSD-46988.

## v1.1.33 {#v1-1-33}

* **ACSD-50478** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.5) - Correction de la commande de restauration de la base de données pour un cas où le fichier de vidage DB contient des déclencheurs et une balise *délimiteur* Commande SQL.
* **ACSD-50512** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction de la variable *Erreur : le lien téléchargeable n’est pas lié au produit. Vérifiez le lien et réessayez.* erreur qui se produit lors de la mise à jour de la date de début d’une mise à jour intermédiaire de produit téléchargeable.
* **ACSD-50949** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel le filtre de prix dans la recherche avancée ne renvoyait pas de résultats appropriés lorsqu’il était utilisé avec le filtre SKU.
* **ACSD-51645** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction de l’erreur générée lors de l’enregistrement d’une nouvelle règle de prix du panier si l’extension `Magento_OfflineShipping` est désactivée.
* **ACSD-50895** (pour Adobe Commerce >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel [!DNL Google Analytics] Les balises GTM 3 ne sont pas déclenchées si [!DNL Google Analytics] 4 GTM n’est pas configuré.
* **ACSD-51102** (pour Adobe Commerce >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel une règle de catalogue appliquée à un grand nombre de produits n’est pas correctement indexée lorsque la règle est activée par une mise à jour planifiée.
* **ACSD-50368** (pour Adobe Commerce et Magento Open Source >= 2.4.3 &lt;2.4.5) - Correction du problème en raison duquel la variable `group_id` est ignoré lorsqu’un client est créé par le biais de l’API REST asynchrone ou de l’API REST en bloc asynchrone.
* **ACSD-51497** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7) - Correction du problème qui empêchait un client de trier une page de catalogue par attribut personnalisé du type de liste déroulante.
* **ACSD-51408** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt; 2.4.7) - Correction du problème en raison duquel l’état de l’élément de commande était incorrectement défini sur *[!UICONTROL Backordered]*.
* **ACSD-51735** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.5) - Correction du problème en raison duquel l’état de l’élément de commande était incorrectement défini sur *[!UICONTROL Ordered]* lorsque le stock de produit est *0*.
* **ACSD-51792** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction du problème en raison duquel une page ne comporte pas l’événement d’impression lors de la [!DNL Google Tag Manager] 4 est activé.
* **ACSD-51471** (pour Adobe Commerce >=2.4.3 &lt;2.4.7) - Correction du problème qui empêchait un utilisateur administrateur d’enregistrer une mise à jour planifiée pour un produit groupé qui utilise un produit simple dont la mise à jour est planifiée.
* **ACSD-51700** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction de l’erreur qui se produit lors du changement d’affichage de magasin sur une page de modification de produit téléchargeable dans l’administrateur.
* **ACSD-51120** (pour Adobe Commerce >=2.3.7 &lt;2.4.3) - Correction du problème en raison duquel le cache des demandes de GET GraphQL n’est pas effacé pour les pages CMS contenant des blocs CMS mis à jour par le biais d’une mise à jour intermédiaire.
* **ACSD-51240** (pour Adobe Commerce >=2.4.4 &lt;2.4.6) - Correction du problème d’absence du fichier téléchargé si l’enregistrement est effectué via le formulaire d’enregistrement de l’entreprise.
* **ACSD-51907** (pour Adobe Commerce >=2.4.2 &lt;2.4.3) - Correction du problème qui empêchait un utilisateur administrateur restreint de créer une note de crédit avec un remboursement hors ligne.
* **ACSD-52148** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.4) - Correction du problème en raison duquel la variable [!DNL Google V3 reCAPTCHA] La connexion de l’administrateur échoue parfois.
* **ACSD-51431** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème d’état d’un indexeur *working* même s’il n’y a pas de nouvelles entrées dans le fichier changelog.
* **ACSD-51892** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème de performances où les fichiers de configuration se chargent plusieurs fois.
* ACSD-51114 obsolète.

## v1.1.32 {#v1-1-32}

* **ACSD-49628** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel la variable [!UICONTROL Page Builder's] plusieurs erreurs empêchent l’administrateur d’enregistrer un produit sans autorisations de contenu.
* **ACSD-51305** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème en raison duquel les produits enfants configurables en rupture de stock ne sont pas disponibles dans la réponse GraphQL.
* **ACSD-50621** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel [!UICONTROL Tier Prices] pour les différents sites web du catalogue partagé ne sont pas visibles lors de la tentative de modification dans un environnement multisite.
* **ACSD-51041** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.0 || >=2.4.1 &lt;2.4.6) - Améliore les performances de l’indexeur de prix.
* **ACSD-51379** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel les modifications apportées au contenu du texte de la page via [!UICONTROL Page Builder] ne sont pas enregistrées.
* **ACSD-49480** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème en raison duquel une seule règle de prix de panier était appliquée au panier.
* **ACSD-51230** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction du problème de suppression du compte de carte-cadeau lorsqu’un remboursement partiel d’un produit simple est traité à partir d’une commande.
* **ACSD-51238** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Correction du problème de suppression de la source d’inventaire lors de la mise à jour des produits configurables et de la modification du prix.
* **ACSD-50794** (pour Adobe Commerce >=2.4.1 &lt;2.4.7) - Correction du problème en raison duquel les détails du message cadeau ou de l’emballage cadeau ne sont pas mis à jour dans la base de données lors de sa suppression via GraphQL.
* **ACSD-51528** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel la variable *x_transfer_for* La colonne contient des valeurs &quot;null&quot; *sales_order* table.
* **ACSD-50849** (pour Adobe Commerce >=2.4.4 &lt;2.4.6) - Correction du problème en raison duquel l’ajout d’un nouveau produit à la catégorie après l’effacement du cache entraînait une incohérence des positions et des sélections des produits existants.
* **ACSD-51294** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel le prix GTM/GA, la quantité, la taxe, l’expédition et les recettes sont envoyés sous forme de chaîne à [!DNL Google Analytics] et GTM.
* **ACSD-51204** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème en raison duquel un produit entièrement vendu ne revenait pas en stock après la création d’une note de crédit.
* **ACSD-51291** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.4-p4 || >=2.4.5 &lt;2.4.5-p3) : correction du problème en raison duquel un administrateur restreint ayant accès à un site web pouvait ajouter des images/vidéos au produit affecté à plusieurs sites web.
* Ajout de nouvelles versions pour ACSD-50336.
* Correctifs remplacés ACSD-49970.

## v1.1.31 {#v1-1-31}

* **ACSD-50345** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4 || >=2.4.4-p1 &lt;2.4.6) - Correction du problème en raison duquel Recaptcha v2 ne se rechargeait pas après l’envoi d’un paiement en échec.
* **ACSD-50817** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Optimise la tâche Cron `sales_clean_quotes` pour exécuter plus rapidement.
* **ACSD-49392** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7) - Correction du problème en raison duquel l’état de la commande se fermait après un remboursement partiel pour un produit fourni.
* **ACSD-51036** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.5) - Correction du problème en raison duquel les conditions de concurrence lors d’appels d’API REST simultanés entraînaient le remplacement des informations d’état de livraison dans la variable [!UICONTROL Items Ordered] table.
* **ACSD-50858** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Améliore les performances de chargement du contenu des bannières.
* Ajout de nouvelles versions pour MDVA-39305-v2, ACSD-45169.
* Mise à jour des correctifs ACSD-50260-v2.

## v1.1.30 {#v1-1-30}

* **ACSD-50336** (pour Adobe Commerce et Magento Open Source >=2.4.4-p1 &lt;2.4.4-p3) - Correction du problème où les emails d’alerte de produit ne sont pas envoyés lorsqu’un produit est de nouveau en stock ou que le prix est modifié.
* **ACSD-50367** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel l’exportation de l’adresse du client ne fonctionne pas lorsqu’un attribut d’adresse du client à sélection multiple sans valeurs est créé.
* **ACSD-49877** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel la lecture automatique de la vidéo ne fonctionne pas sur mobile. [!DNL Safari] lorsque la vidéo est directement liée à un fichier vidéo distant et non à un service de diffusion en continu.
* **ACSD-50165** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction de l’erreur *Le fichier ne peut pas être supprimé. Warning!unlink : aucun fichier ou répertoire de ce type* lors de la purge du cache JS/CSS de l’administrateur.
* **ACSD-49737** (pour Adobe Commerce et Magento Open Source >=2.4.1-p1 &lt;2.4.7) - Correction du problème en raison duquel un coupon était incorrectement marqué comme utilisé après l’échec du paiement de la carte.
* **ACSD-50814** (pour Adobe Commerce et Magento Open Source >=2.4.6 &lt;2.4.7) - Correction du problème qui empêchait un utilisateur administrateur de créer une note de crédit.
* **ACSD-50116** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème qui empêchait un utilisateur administrateur de créer une réécriture d’URL pour les sous-catégories niveau 3 ou inférieur.
* **ACSD-49513** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.5) - Correction du problème d’échec de la synchronisation du stockage distant en raison de fichiers de 0 octet.
* **ACSD-46683** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème d’affichage du prix d’expédition *Pas encore calculé*.
* **ACSD-49129** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6) - Correction du problème en raison duquel la variable *[!UICONTROL content]* L’attribut (code image base64) n’est pas renvoyé dans `rest/V1/products/sku/media` réponses de l’API de média de produit.
* **ACSD-50276** (pour Adobe Commerce >=2.4.0 &lt;2.4.7) - Correction du problème en raison duquel le formulaire d’enregistrement du client ne fonctionnait pas sur le storefront si un attribut de client à sélection multiple était créé.
* **ACSD-50527** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) : corrige l’erreur qui se produit lors de l’enregistrement d’une page avec un bloc dynamique vide.
* **ACSD-49973** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.5) - Améliore les performances de récupération des produits regroupés via GraphQL.
* **ACSD-51114** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème en raison duquel un produit aléatoire disparaissait des catalogues volumineux lorsque l’indexation asynchrone était activée. Améliore les performances de la réindexation asynchrone pour les catalogues volumineux.
* **B2B-2598** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.7) - Ajout de la fonctionnalité de mise en cache à la variable [!UICONTROL availableStores], [!UICONTROL countries], [!UICONTROL country], [!UICONTROL currency], et [!UICONTROL storeConfig] Requêtes GraphQL.
* Ajout de nouvelles versions pour MDVA-42806, ACSD-48627, ACSD-46815.
* Mise à jour des métadonnées de correctifs pour ACSD-49773, ACSD-47179, ACSD-48300.

## v1.1.29 {#v1-1-29}

* **ACSD-49389** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.7) - Correction du problème d’envoi d’un email prêt à l’emploi par l’API lorsque la commande n’est pas prête pour la récupération.
* **ACSD-49822** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel les mises à jour dans [!UICONTROL Requisition List] ne sont pas répercutées sur la page [!UICONTROL Print Requisition List].
* **ACSD-48771** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème lié à la mise à niveau du type de contenu de bloc de colonnes à partir d’un contenu plus ancien. [!DNL Page Builder] versions.
* **ACSD-49464** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel les factures, les envois et les notes de crédit ne sont pas déplacés de l’archive lorsque orderId est différent.
* **ACSD-49773** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6) - Correction du problème d’échec de l’exportation de produits lorsque AWS S3 est utilisé comme stockage distant.
* **ACSD-49748** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction du problème qui empêchait l’envoi des invitations.
* **ACSD-49502** (pour Adobe Commerce >=2.4.3 &lt;2.4.7) - Correction du problème en raison duquel le lien téléchargeable n’était pas mis à jour correctement après l’application d’une mise à jour intermédiaire au produit téléchargeable.
* **ACSD-49527** (pour Adobe Commerce >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel les rôles de l’entreprise GraphQL n’affichent pas correctement la pagination.
* **ACSD-49706** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème d’enregistrement de la valeur par défaut pour un attribut d’échantillon visuel lorsqu’aucune valeur n’est sélectionnée.
* **ACSD-49835** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel la valeur de la case à cocher Utiliser par défaut n’était pas enregistrée correctement au niveau du magasin pour un attribut à sélection multiple.
* **ACSD-49898** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème où la grille de produits renvoie une exception lorsqu’un produit regroupé a un prix spécial qui dépasse 1 000.
* **ACSD-50234** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.5) - Correction du problème lié au mauvais nom de client dans l’email de confirmation lors du placement d’une commande avec [!DNL PayPal].
* **ACSD-49960** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel le filtrage par date ne fonctionnait pas pour la grille de commande du client.
* **ACSD-49849** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.6) - Correction du problème de remplacement de l’adresse électronique du client par [!DNL PayPal] lors du placement d’une commande avec [!DNL PayPal Express] via GraphQL.
* **ACSD-49839** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel la structure et les tarifs du catalogue partagé généraient une erreur dans Admin lorsque les produits contenaient des guillemets simples ou doubles dans le SKU.
* **ACSD-49970** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction d’une gestion incorrecte des erreurs GraphQL lors de la [!DNL New Relic] la création de rapports est activée.
* **ACSD-50260** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème en raison duquel les résultats de recherche de produits GraphQL étaient limités à 10 000 résultats uniquement.
* **ACSD-48813** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème en raison duquel la recherche n’affichait pas de résultats pertinents en fonction du poids de la recherche des attributs.

## v1.1.28 {#v1-1-28}

* **ACSD-48204** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.3) - Correction du problème en raison duquel une règle de prix de catalogue créée à partir de l’attribut Oui/Non ne prenait pas en compte la portée sélectionnée.
* **ACSD-47704** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel le produit regroupé affichait le prix de dans les produits en stock uniquement.
* **ACSD-49370** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel la variable *Heure de date* l’attribut de produit comporte une *FilterMatchTypeInput* saisissez dans le schéma GraphQL.
* **ACSD-48807** (pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.7) - Correction du problème en raison duquel les révisions des produits du client ne sont pas filtrées par l’aperçu de magasin via GraphQL.
* **ACSD-49433** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème en raison duquel le montant par défaut s’affichait comme sous-total dans le panier pour la carte cadeau avec un montant ouvert.
* **ACSD-48866** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème qui se produit lorsqu’une erreur se produit lors de la demande d’un flux RSS pour des catégories.
* **ACSD-48784** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction d’un problème en raison duquel les prix des segments de clients étaient incorrectement mis en cache entre les groupes de clients.
* **ACSD-48857** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème qui empêchait un utilisateur d’enregistrer les modifications après les avoir modifiées dans le créateur de pages.
* **ACSD-49065** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel les éléments de guillemet ne sont pas visibles dans l’administrateur si seulement ils sont affectés au stock personnalisé.
* **ACSD-49179** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel le rapport Commandes affichait des montants incorrects en cas de devises différentes pour différents magasins.
* **ACSD-49286** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème en raison duquel un produit était ajouté deux fois à un panier lorsque plusieurs widgets de produit étaient présents sur la page.
* **ACSD-49574** (pour Adobe Commerce >=2.4.4 &lt;2.4.7) - Ajoute une fonctionnalité permettant de prendre en charge les mises à jour de produit Carte cadeau dans un panier via GraphQL.
* Mise à jour du correctif : ACSD-48694.

## v1.1.27 {#v1-1-27}

* **ACSD-48362** (pour Adobe Commerce >=2.4.1 &lt;2.4.7) - Correction du problème en raison duquel l’adresse de livraison par défaut était utilisée à la place d’une nouvelle adresse lors du placement d’une commande avec un guillemet négociable.
* **ACSD-48059** (pour Adobe Commerce >=2.3.7 &lt;2.4.7) - Correction du problème qui empêchait les commerçants d’enregistrer le &quot;[!UICONTROL Match product by rule]&quot; dans la catégorie.
* **ACSD-48216** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7) - Correction du problème en raison duquel [!UICONTROL AUTO_INCREMENT] de [!UICONTROL inventory_source_item] augmente au niveau du tableau [!UICONTROL UPDATE] opération.
* **ACSD-47908** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7) : corrige l’erreur &quot;Une valeur inférieure ou égale à 0 est attendue&quot; lors de la sélection de la source et de la quantité à l’étape d’expédition lors du passage en caisse.
* **ACSD-49497** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.6) - Correction du problème où une commande reste en état de traitement après l’expédition et qu’un remboursement partiel est appliqué.
* **ACSD-48694** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.1 &lt;2.4.7) - Correction du problème en raison duquel l’erreur &quot;Changement d’état non valide demandé&quot; empêchait un client de passer une commande.
* **ACSD-49013** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.7) - Correction du problème en raison duquel la confirmation par email n’était pas traduite dans les paramètres régionaux du site web lors de la création de clients à l’aide de l’API en bloc.
* **ACSD-48164** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème qui empêchait un administrateur restreint d’enregistrer une valeur au niveau du site web.
* **ACSD-48404** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.4) - Correction du problème en raison duquel &quot;Mémoriser la pagination des catégories = Oui&quot; provoquait une erreur lors de l’activation du bouton Précédent du navigateur.
* **ACSD-48634** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction des erreurs JS sur une page de mise à jour intermédiaire lorsque &quot;[!UICONTROL Google Analytics Content Experiments]&quot; est activé.
* **ACSD-49042** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.5) - Correction du problème qui empêchait la commande d’un produit avec un ordre d’arrière-plan infini à partir de Storefront.
* Mise à jour des correctifs : ACSD-48366, ACSD-48661.

## v1.1.26 {#v1-1-26}

* **ACSD-47937** (pour Adobe Commerce et Magento Open Source 2.4.4) || >=2.4.5 &lt;2.4.6) - Correction du problème en raison duquel les notifications de baisse de prix ne sont pas toujours envoyées en raison de la mise en cache au niveau de l’application.
* **ACSD-48661** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème en raison duquel si la limite de crédit de l’entreprise est supérieure à 999, le séparateur de virgules empêche l’enregistrement de l’entreprise en raison d’une erreur de validation.
* **ACSD-48773** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.7) - Correction du problème en raison duquel le modèle d’email des points de récompense provient d’un mauvais magasin.
* **ACSD-48587** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.7) - Correction du problème qui empêchait l’affichage des produits correspondants des caractères spéciaux de HTML dans les règles de correspondance du widget de produits.
* **ACSD-48212** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.6) - Correction du problème en raison duquel l’importation de produit attribue le produit à la mauvaise source.
* **ACSD-47988** (pour Adobe Commerce et Magento Open Source >=2.3.7 &lt;2.4.6) - Correction du problème en raison duquel l’exportation de produits supprimait les balises de HTML de la description du produit du créateur de pages.
* **ACSD-48366** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème en raison duquel l’image du produit ne s’affichait pas dans le modèle de courrier électronique Retour au stock .
* **ACSD-48417** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.7) - Correction du problème d’apparition d’une erreur SQL après la création d’une modification de planification pour un produit et l’enregistrement d’un autre produit.

## v1.1.25 {#v1-1-25}

* **ACSD-48058** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction du problème en raison duquel la réindexation des prix du produit ne fonctionnait pas si le produit du lot n’était affecté à aucun site web.
* **ACSD-48262** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction du problème en raison duquel les produits ne sont pas visibles sur le front-end lorsque le paramètre &quot;Autoriser tous les produits par page&quot; est défini sur Oui.
* **ACSD-48293** (pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4) - Correction du problème en raison duquel les produits composites étaient en rupture de stock lorsque les produits enfants qui avaient été épuisés étaient retrouvés en stock.
* **ACSD-47520** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème qui entraînait la perte de points de récompense par les clients lors de la création d’une note de crédit.
* **ACSD-48044** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.4) - Correction du problème en raison duquel l’application de plusieurs cartes-cadeaux à une seule commande avec livraison multiple empêchait le placement des commandes.
* **ACSD-48300** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème qui empêchait la création d’un retour en cas de suppression du produit configurable.
* **ACSD-47910** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème des commandes, factures, envois et avoirs manquants dans les grilles d’entités respectives.
* **ACSD-47292** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème en raison duquel les produits en rupture de stock ne sont pas disponibles dans la réponse GraphQL si l’option &quot;Afficher les produits en rupture de stock&quot; est définie sur Oui.
* **ACSD-48234** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction du problème en raison duquel le résultat de la recherche catalogue affichait un nombre d’éléments de catégorie incorrect lorsque l’option &quot;Afficher en rupture de stock&quot; était activée.
* **ACSD-48313** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.5) - Correction du problème en raison duquel la colonne &quot;variations configurables&quot; n’est pas analysée si la valeur de l’attribut contient une virgule. Le même algorithme d’analyse est utilisé pour &quot;additional_attributes&quot;.
* **ACSD-48627** (pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6) - Correction du problème en raison duquel le produit configurable en rupture de stock provoquait une erreur lors de l’envoi d’une demande GraphQL pour obtenir les détails du panier.
* Mise à jour du correctif : MDVA-39384.

## v1.1.24 {#v1-1-24}

* **ACSD-45168** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6) - Correction du problème en raison duquel les URL compatibles avec l’optimisation pour les moteurs de recherche ne sont pas générées pour les produits dont la variable *url_key* attributs remplacés au niveau de l’affichage du magasin.
* **ACSD-46865** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème en raison duquel la grille Expédition et Mémo de crédit n’est pas renseignée lorsque l’indexation asynchrone est activée.
* **ACSD-47004** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6) - Correction du problème en raison duquel la TVA n’est pas appliquée à une adresse de facturation sans identifiant de TVA.
* **ACSD-47803** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel les échantillons de produits configurables en rupture de stock s’affichaient comme disponibles.
* **ACSD-47137** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Améliore la vitesse de chargement de la galerie d’images lorsque le dossier pub/média est très volumineux.
* **ACSD-46770** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème d’envoi des emails de l’ordre d’administration même lorsque la variable *Confirmation de commande par e-mail* n’est pas cochée.
* **ACSD-47955** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème en raison duquel GraphQL n’affiche pas correctement la remise au panier.
* **ACSD-46617** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel la variable *Continuer vers l’extraction* est grisé même si le sous-total est supérieur au nombre configuré *Montant minimal de la commande*.
* **ACSD-47079** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.5) - Correction du problème en raison duquel l’état du stock des produits composites (groupé, groupé et configurable) n’était pas mis à jour lorsque l’état du stock des sous-produits changeait via le POST API REST /rest/V1/inventory/source-items.
* **ACSD-47336** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correctifs *Quelque chose s&#39;est mal passé.* lors de l’affichage des notifications dans l’administrateur Commerce.
* **ACSD-47559** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel la zone Prévisualiser le modèle de courrier électronique n’est pas entièrement visible.
* **ACSD-47920** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel les commandes peuvent être placées via l’API REST en tant qu’utilisateur invité, même lorsque la variable *Autoriser le passage en caisse des invités* est désactivé.
* Correctifs remplacés : MDVA-39305, MDVA-42855.

## v1.1.23 {#v1-1-23}

* **ACSD-47179** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème qui empêchait un administrateur disposant d’un accès limité à une plage spécifique de supprimer les révisions de produits.
* **ACSD-47107** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.5) - Correction du problème en raison duquel la remise de la règle de prix du catalogue était appliquée aux options de produit personnalisées.
* **ACSD-47232** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème qui empêchait l’application des bons avec des conditions de poids total dans l’administrateur.
* **ACSD-46519** (pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.6) - Correction du problème en raison duquel la requête categoryList de GraphQL renvoie un nombre de produits incorrect pour une catégorie d’ancrage.
* **ACSD-47027** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6) - Correction d’une demande GraphQL updateCompanyRole lente.
* **ACSD-47666** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel la fonction de filtre ne fonctionnait pas dans la grille Admin > Système > Autorisations > Rôles utilisateur > un rôle > Utilisateurs de rôle .
* **ACSD-47497** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel l’onglet Services n’était pas visible dans la configuration sous Admin.
* Mise à jour du correctif : ACSD-47743.
* Correctifs remplacés : MDVA-42807.

## v1.1.22 {#v1-1-22}

* **ACSD-47444** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.3) - Correction de la variable _Tentative d’accès au décalage du tableau sur la valeur de type bool_ lors de l’accès à certains chemins de catégorie non existants pour les produits connus sous PHP 7.4.
* **ACSD-47332** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème d’échec de cron avec une erreur qui n’est signalée que lors de l’exécution entre 00:00 et 00:59 UTC.
* **ACSD-47280** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel la désactivation de la fonction de catalogue partagé sur une plage spécifique ne fonctionnait pas correctement.
* **ACSD-47106** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème qui empêchait l’enregistrement d’une valeur dans un nouvel attribut personnalisé sur la page de création d’une entreprise.
* Mise à jour du correctif : ACSD-45143.

## v1.1.21 {#v1-1-21}

* **ACSD-46809** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6) - Correction du problème qui entraînait l’erreur d’un utilisateur lors de l’attribution d’un grand nombre de sources de produits.
* **ACSD-46856** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Améliore les prix des niveaux de mise à jour des performances via Système > Configuration > Import > Advanced Tarification.
* **ACSD-46541** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.4) - Correction du problème qui empêchait un utilisateur administrateur de créer une note de crédit si un article de commande était supprimé.
* **ACSD-46581** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel le total de la taxe estimé n’est pas mis à jour après la sélection d’un pays dans le panier.
* **ACSD-46618** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème en raison duquel le widget de liste de produits affichait des prix en cache incorrects pour un client connecté.
* **ACSD-46674** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Correction du problème d’affichage des options personnalisées d’un type d’image en tant que HTML dans les emails des clients.
* **ACSD-46988** (pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6) - Correction du problème en raison duquel la requête d’API &quot;devise&quot; de GraphQL renvoyait des valeurs NULL pour une devise personnalisée.
* **ACSD-47076** (pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.5) - Correction du problème de lecture des vidéos Vimeo sur le storefront.
* **ACSD-45071** (pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4) - Correction du problème d’ajout de la source par défaut au produit lors de l’importation.
* **AC-3023** (pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6) - Mettez à jour le schéma DHL vers la dernière version 10.0.
* Mise à jour des correctifs : MDVA-42584.
* Correctifs remplacés : MDVA-36572, ACSD-45241.

## v1.1.20 {#v1-1-20}

* **ACSD-46520** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.5*) : correction d’un problème en raison duquel un utilisateur obtenait un état de commande incorrect lorsqu’il était remboursé à l’aide du crédit de magasin.
* **ACSD-46703** (*pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6*) - Correction d’un problème en raison duquel il n’était pas possible de faire glisser et déposer des options personnalisées sur une page de modification de produit.
* **ACSD-44851** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6*) - Correction du problème qui empêchait l’ouverture ou le développement d’une catégorie avec des sous-catégories.
* **ACSD-46815** (*pour Adobe Commerce et Magento Open Source >=2.4.5 &lt;2.4.6*) - Correction du problème en raison duquel la requête de l’arborescence de catégories était limitée à 20 catégories.
* **ACSD-45675** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.6*) - Correction du problème en raison duquel l’exportation de produits utilisait des noms de catégorie provenant de la variable *Affichage de magasin par défaut* portée.
* **ACSD-46869** (*pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.6*) - Correction du problème de mise à jour d’un produit configurable dans un panier via un *API REST PUT* sans modifier la quantité du produit.
* **MDVA-42768-V2** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.3*) - Correction du problème en raison duquel le produit configurable affichait le prix normal comme *0* when *Afficher en rupture de stock* is *Oui*.
* Mise à jour des correctifs : MDVA-44562, ACSD-46213, MDVA-41305, MDVA-38346, MDVA-13203.
* Correctif obsolète : MDVA-42768.

## v1.1.19 {#v1-1-19}

* **ACSD-46213** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.3*) - Correction du problème en raison duquel la requête de l’arborescence de catégories était limitée à 20 catégories.
* **ACSD-45781** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.2*) - Correction du problème qui empêchait l’affichage du champ de recherche avant du magasin sur mobile.
* **ACSD-46192** (*pour Adobe Commerce et Magento Open Source >=2.3.6 &lt;2.4.5*) - Correction du problème lié à l’utilisation de la variable `async/bulk/V1/configurable-products/bySku/options` point de terminaison .
* **ACSD-46404** (*pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.5*) - Correction du problème qui empêchait un utilisateur administrateur de se connecter après la mise à niveau vers la version 2.4.4.
* Mise à jour des correctifs : MDVA-41305, MDVA-38626, MDVA-38728, MDVA-41061-V4, MDVA-42269, MDVA-39305.

## v1.1.18 {#v1-1-18}

* **ACSD-45817** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Correction du problème en raison duquel une mutation de produit GraphQL pour un magasin spécifique renvoyait toutes les variantes configurables, y compris celles qui n’étaient pas affectées au magasin demandé.
* **ACSD-46146** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.6*) - Correction du problème d’envoi de deux emails de confirmation de commande après le placement d’une commande de la part de l’administrateur.
* **ACSD-45255** (*pour Adobe Commerce >=2.4.3 &lt;2.4.6*) - Correction d’une exception sur la page Rapport Faible Stock pour un utilisateur administrateur restreint.
* **ACSD-45488** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.6*) - Correction du problème en raison duquel un produit configurable avec plusieurs sources n’était pas automatiquement renvoyé à In Stock.
* **ACSD-45754** (*pour Adobe Commerce et Magento Open Source >=2.3.1 &lt;2.4.6*) - Correction du problème en raison duquel les points de récompense ne sont pas ajoutés après l’application d’un coupon au panier.
* **ACSD-45849** (*pour Adobe Commerce >=2.4.3 &lt;2.4.4*) - Correction du problème de perte des métadonnées vidéo après l’application d’une mise à jour intermédiaire.
* **ACSD-45257** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;2.4.4*) - Correction du problème qui empêchait GraphQL d’afficher correctement une remise au panier.
* **ACSD-44938** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.4*) - Correction du problème qui `VAT_ID` ne peut pas être appliqué dans une requête GraphQL pour un utilisateur invité.
* Mise à jour des correctifs : MDVA-43417.

## v1.1.17 {#v1-1-17}

* **ACSD-45241** (*pour Adobe Commerce et Magento Open Source >=2.3.5 &lt;2.4.4*) : correction d’un problème en raison duquel la quantité en stock d’un produit virtuel était mal calculée après la création d’une note de crédit.
* **ACSD-43887** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.5*) : correction d’un problème en raison duquel des détails incorrects s’affichaient sur la page de paiement du passage en caisse lorsque les commandes d’achat pour les entreprises étaient activées.
* **ACSD-45143** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.5*) - Correction du problème en raison duquel la variable `setShippingAddressesOnCart` mutation ne permet pas de définir le code de région numérique comme *region*.
* **ACSD-44591** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.6*) - Correction de l’erreur qui se produit lorsqu’une commande est passée sans confirmation CAPTCHA.
* **ACSD-45520** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.6*) - Correction du problème en raison duquel les options d’échantillon ne sont pas présélectionnées sur la page des détails du produit lorsqu’un utilisateur modifie des produits configurables à partir du panier.
* **ACSD-45169** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.6*) - Correction du problème qui [!DNL Visual Merchandiser] n’affiche pas le stock et le prix corrects d’un produit configurable après l’application d’une mise à jour intermédiaire.
* **ACSD-45424** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;2.4.6*) - Correction du problème de création d’une compensation de réservation incorrecte après un remboursement partiel (note de crédit).
* **MDVA-42807** (*pour Adobe Commerce et Magento Open Source >=2.3.1 &lt;2.4.6*) : correction d’un problème en raison duquel le symbole de devise personnalisé ne s’affichait pas au recto du magasin.
* Mise à jour des correctifs : MDVA-42689, AC-3022.

## v1.1.16 {#v1-1-16}

* **MDVA-44703** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4*) : correction d’un problème en raison duquel les totaux des commandes du rapport Commandes étaient mal calculés pour l’utilisateur administrateur restreint.
* **MDVA-44940** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4*) - Correction de l’erreur SQL qui se produisait lors de l’enregistrement de la catégorie à partir de l’administrateur.
* **MDVA-44562** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.2-p2*) - Correction du problème en raison duquel l’identifiant de magasin autre que l’identifiant par défaut pour les éléments de guillemet est remplacé par l’identifiant de magasin par défaut, en dépit de la requête GraphQL provenant de la vue de magasin autre que celle par défaut.
* **MDVA-43167** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Correction du problème en raison duquel l’action de masse de grille d’ordre d’administration ne s’appliquait pas à plusieurs pages lorsque l’utilisateur administrateur sélectionnait toutes les commandes.
* **MDVA-44044** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.2-p2*) - Correction du problème qui empêchait l’affichage d’un produit sur la page de catégorie après son affectation à un nouveau site web.
* **MDVA-42509** (*pour Adobe Commerce et Magento Open Source >=2.3.3 &lt;2.4.4*) - Correction du problème qui empêchait le téléchargement d’un fichier CSV pour un ordre rapide, ce qui entraînait une *Impossible d’envoyer le cookie* erreur.
* Mise à jour des correctifs : MDVA-41061, MDVA-42584.
* Le préfixe du nouveau [!DNL Quality Patches Tool] les correctifs seront modifiés à partir de *MDVA* to *ACSD* en raison de modifications de processus internes.

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4*) - Correction du problème qui empêchait l’ajout d’un élément supplémentaire au panier lorsque la quantité minimale de l’élément était déjà dans le panier.
* **MDVA-44887** (*pour Adobe Commerce et Magento Open Source >=2.4.4 &lt;2.4.5*) - Correction de la variable *SyntaxError non interceptée : jeton inattendu &quot;const&quot;* dans le panneau Admin.
* **MDVA-43718** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correctifs *Le consommateur n’est pas autorisé à accéder à %resources.* erreur qui s’affiche lors de l’accès à un catalogue partagé à partir d’une intégration personnalisée.
* **MDVA-44660** (*pour Adobe Commerce et Magento Open Source >=2.4.2-p1 &lt;2.4.5*) - Correction du problème en raison duquel le caractère accent grave ``` ` ``` ne peut pas être utilisé pour le prénom et le nom d’un client.
* **MDVA-40896** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4*) - Correction de la variable *Erreur : TypeError : argument 3 transmis au Magento* erreur dans l’API en bloc de produit asynchrone.
* **MDVA-38559** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.3*) - Correction de la variable */V1/customers/search API* pour les clients disposant de plusieurs abonnements.
* **MDVA-44533** (*pour Adobe Commerce et Magento Open Source >=2.3.1 &lt;2.4.4*) - Correction du problème en raison duquel la remise est incorrectement appliquée à un produit enfant groupé.
* Mise à jour des correctifs : MDVA-41061, MDVA-42269.

## v1.1.14 {#v1-1-14}

* **MDVA-43983** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.5*) - Correction du problème en raison duquel les produits *Non visible individuellement* apparaît toujours dans les résultats de recherche avancée du catalogue.
* **MDVA-44100** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.5*) - Correction du problème en raison duquel tous les FPT étaient affectés au dernier produit du panier et réinitialisés pour d’autres produits.
* **MDVA-43605** (*pour Adobe Commerce et Magento Open Source >=2.3.1 &lt;2.4.5*) - Correction du problème en raison duquel les données de commande renvoyaient des valeurs négatives pour les totaux des lignes lors de l’utilisation de l’API REST.
* **MDVA-43102** (*pour Adobe Commerce et Magento Open Source >=2.3.1 &lt;2.4.5*) - Correction du problème de mise à jour incorrecte de la quantité vendable lorsqu’un remboursement est effectué via l’API REST.
* **MDVA-43178** (*pour Adobe Commerce et Magento Open Source >=2.4.3-p2 &lt;2.4.5*) - Correction du problème qui empêchait la récupération d’un jeton client pour un magasin personnalisé dans GraphQL.
* **MDVA-43859** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.5*) - Correction du problème d’erreur *Aucune entité de ce type avec customerId =* est consigné lorsqu’un client supprimé tente de se connecter.
* **MDVA-44147** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.5*) - Correction du problème qui empêchait une requête GraphQL de renvoyer des listes de demandes d’acquisition.
* **MDVA-44505** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.3*) - Correction des problèmes en raison desquels le GraphQL Apply Reward Points ne mettait pas à jour le total général et où le crédit de magasin était appliqué plusieurs fois lors du placement de la commande.
* Mise à jour des correctifs : MDVA-29148, MDVA-36464-V5, MDVA-42584, MDVA-39993-V2.

## v1.1.13 {#v1-1-13}

* **MDVA-42969** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.3*) - Correction du problème de fonctionnement de la règle de produit connexe uniquement lorsque le segment client est défini sur *Tous*.
* **MDVA-39605** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;2.4.5*) - Correction d’un problème en raison duquel la valeur TTL (date d’expiration) du cache de Redis était incorrecte.
* **MDVA-43862** (*pour Adobe Commerce et Magento Open Source >=2.3.3 &lt;2.4.5*) - Correction du problème qui empêchait le client de mettre à jour les articles du panier à cause d’un GraphQL. *mutation UpdateCartItems* erreur.
* **MDVA-43824** (*pour Adobe Commerce et Magento Open Source >=2.3.6 &lt;=2.3.7-p3 || >=2.4.1 &lt;2.4.5*) - Correction du problème d’apparition d’une erreur lors de l’annulation de commandes avec une remise.
* **MDVA-43451** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.5*) - Correction du problème d’erreur *Le magasin demandé n’a pas été trouvé. Vérifiez le magasin, puis réessayez.* s’affiche lors de la configuration d’un catalogue partagé pour un site web spécifique.
* **MDVA-43491** (*pour Adobe Commerce et Magento Open Source >=2.3.5 &lt;2.4.5*) - Correction du problème en raison duquel le libellé de l’image de base n’était pas mis à jour lors de l’importation de produits pour un site web multi-magasin.
* **MDVA-43601** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction du problème des déclencheurs manquants après la réindexation complète.
* **MDVA-42046** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;=2.3.5-p2 || >=2.4.0 &lt;2.4.5*) - Correction du problème d’attribution d’une valeur incorrecte à un attribut de produit avec un champ de saisie de date lors de la mise à jour d’un produit.
* **MDVA-43935** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.5*) - Correction du problème qui entraînait l’affichage en double d’un produit de vente par montée en gamme.
* **MDVA-44188** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.5*) - Correction du problème qui entraînait l’envoi par le système d’emails avec `.-` dans les adresses ne sont pas envoyées.
* **MDVA-42283** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) : correction d’un problème en raison duquel le format de date et d’heure dans la grille d’ordre d’administration des paramètres régionaux français n’était pas valide.
* Mise à jour des correctifs : MDVA-41061-V2, MDVA-36309, MDVA-30862, MDVA-39713.
* Ajout de métadonnées de correctifs pour le [!DNL Site-Wide Analysis Tool].

## v1.1.12 {#v1-1-12}

* **MDVA-39713** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.3.6*) - Correction du problème en raison duquel l’utilisateur était en mesure de modifier l’heure de début d’une mise à jour planifiée active.
* **MDVA-42410** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) : correction d’un problème en raison duquel les rapports de coupon n’affichaient que la devise de base par défaut.
* **MDVA-41136** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction du problème en raison duquel la date d’expiration de la variable `mage-cache-sessid` n’est pas étendue, ce qui entraîne un nettoyage des données client.
* **MDVA-39993** (*pour Adobe Commerce et Magento Open Source >=2.3.5 &lt;=2.3.7-p2 || >=2.4.0 &lt;2.4.4*) - Correction du problème en raison duquel les modifications d’inventaire effectuées par le biais de l’API ne se répercutent pas sur la page du produit sur l’interface.
* **MDVA-42855** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.5*) - Correction d’un problème en raison duquel une nouvelle adresse du client n’était pas enregistrée dans le carnet d’adresses lors du passage en caisse.
* **MDVA-42645** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.5*) - Correction du problème qui empêchait l’administrateur de rembourser les points de récompense si la fonctionnalité de stockage du crédit était désactivée.
* **MDVA-43414** (*pour Adobe Commerce et Magento Open Source >=2.3.6 &lt;=2.3.7-p2*) - Correction de l’erreur fatale PHP qui se produit lors de l’exécution de la variable `inventory.reservations.updateSalabilityStatus` client de file d’attente sur des SKU numériques.
* **MDVA-41628** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.5*) - Correction du problème en raison duquel les utilisateurs administrateurs limités existants avaient accès aux nouvelles ressources lors de l’ajout de nouveaux modules.
* **MDVA-43348** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.5*) - Correction du problème qui entraînait l’affichage d’une erreur lors de la demande GraphQL de carte-cadeau si `gift_card_options` contain *uid*.
* **MDVA-39546** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction du problème en raison duquel la date de début de la mise à jour intermédiaire pouvait être définie sur une date antérieure à la date actuelle lors de la modification.
* **MDVA-42950** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction du problème de lecture des vidéos sur la page du produit.
* **MDVA-42689** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction du problème qui entraînait le lancement d’une *Violation de la contrainte d’intégrité* lors de la mise à jour des catégories de produits lors de l’importation.
* **MDVA-41229** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction du problème qui empêchait l’affichage des images disponibles sur le serveur principal après l’importation de produits configurables.
* **MDVA-43731** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4*) - Correction du problème qui *Synonymes de recherche* ne fonctionne plus lorsque la valeur ajoutée dans *Termes minimum à faire correspondre*.
* **MDVA-43232** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;2.4.5*) - Correction du problème de tri des produits dans [!DNL Visual Merchandiser] par Prix spécial au bas/en haut provoque une erreur lors de l’enregistrement de la catégorie.
* **MDVA-43726** (*pour Adobe Commerce et Magento Open Source >=2.3.3 &lt;2.4.3*) - Correction du problème en raison duquel la règle de prix du catalogue basée sur la correspondance des attributs au niveau du magasin ne s’appliquait pas après une réindexation partielle.
* Mise à jour des correctifs : MDVA-36464, MDVA-37478, MDVA-38608.
* Ajout de métadonnées de correctifs pour le [!DNL Site-Wide Analysis Tool].

## v1.1.11 {#v1-1-11}

* **MDVA-42790** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.5*) - Correction du problème en raison duquel les attributs de prix de produit ne pouvaient pas être mis à jour pour un site web spécifique via l’API REST.
* **MDVA-41350** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction d’un problème en raison duquel une exception était générée lorsqu’un utilisateur administrateur disposant d’un accès limité ajoute un produit en dehors de la portée de son rôle par SKU dans une commande.
* **MDVA-42269** (*pour Adobe Commerce et Magento Open Source >=2.4.3-p1 &lt;2.4.5*) - Correction du problème qui empêchait un utilisateur administrateur de se connecter à l’administrateur en raison de la variable *TypeError : strtotime() exige que le paramètre 1 soit une chaîne, null étant donné* erreur.
* **MDVA-40830** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction du problème en raison duquel le crédit de magasin était appliqué plusieurs fois lors de l’emplacement de la commande.
* **MDVA-42237** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.5*) - Correction du problème qui empêchait la mise à jour du prix spécial d’un produit configurable après modification du prix de son sous-produit.
* **MDVA-42520** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4*) - Correction du problème en raison duquel le taux de taxe était appliqué deux fois si la variable *Activer le commerce transfrontalier* est utilisée.
* Mise à jour des correctifs : MDVA-27239, MDVA-39305, MDVA-41236, MDVA-36832.
* Correctif obsolète : MDVA-37725.

## v1.1.10 {#v1-1-10}

* **MDVA-38728** (*pour Adobe Commerce et Magento Open Source >=2.3.2 &lt;2.4.5*) - Correction d’un problème en raison duquel la mise à jour en masse d’attributs crée une réécriture d’URL pour le magasin par défaut uniquement après modification. *Visibilité du produit*.
* **MDVA-43091** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4*) - Correction du problème qui entraînait l’erreur lors de la commande d’un produit en bundle auprès de l’administrateur dans le serveur principal. *Vous ne pouvez pas utiliser de quantité décimale pour ce produit.*.
* **MDVA-40816** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction du problème en raison duquel les règles de produit associées affichaient des produits de catégories non définies dans les conditions de règle.
* **MDVA-41305** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.5*) : correction d’un problème en raison duquel la mutation de GraphQL ne renvoyait pas d’options de produit configurables après l’avoir ajouté à la liste des souhaits.
* **MDVA-39181** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.5*) - Correction du problème en raison duquel les règles de produit associées affichaient des produits de catégories non définies dans les conditions de règle.
* **MDVA-42584** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.3*) - Correction du problème en raison duquel l’état du stock configurable dans le serveur principal n’était pas mis à jour après la modification de l’état du stock et de la quantité via l’importation ou l’API.
* **MDVA-40175** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.3*) - Correction du problème qui *Cliquez pour modifier le mode de livraison.* n’affiche pas de boutons radio pour sélectionner les méthodes de livraison dans l’Admin lors de la réorganisation.
* **MDVA-42768** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;2.4.5*) - Correction du problème en raison duquel le prix normal du produit configurable était de 0 lorsque *Afficher en rupture de stock* est Oui.
* **MDVA-43201** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Correction du problème d’erreur lors de la connexion du client lors de l’utilisation de l’attribut DOB avec certains paramètres régionaux.
* Mise à jour des correctifs : MDVA-35092, MDVA-33970.

## v1.1.9 {#v1-1-9}

* **MDVA-38346** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.5*) - Correction du problème de dysfonctionnement des filtres de dates lorsque le fuseau horaire Adobe Commerce est différent du fuseau horaire de l’environnement local.
* **MDVA-42657** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.5*) - Correction du problème qui empêchait l’utilisateur administrateur de sélectionner des catégories dans les conditions de segment du client.
* **MDVA-42806** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Correction du problème en raison duquel une erreur *Enregistrement d’une nouvelle société* un email est envoyé chaque fois qu’une société existante est mise à jour via l’API REST.
* **MDVA-37984** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.5*) - Correction du problème en raison duquel la variable [!DNL Visual Merchandiser] *Faire correspondre le produit par règle* ne filtre pas correctement les produits avec des mises à jour intermédiaires.
* **MDVA-40488** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Correction du problème en raison duquel les produits configurables avec des produits enfants en rupture de stock ne s’affichaient pas dans la plage de prix correcte.
* **MDVA-42507** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.5*) - Correction du problème de nettoyage du cache de la page entière après l’application de la mise à jour intermédiaire pour la règle de panier.
* **MDVA-39163** (*pour Adobe Commerce et Magento Open Source >=2.3.5 &lt;2.4.5*) - Correction du problème en raison duquel les méthodes d’expédition n’étaient pas disponibles lorsqu’un nouvel utilisateur était enregistré et que les produits du panier provenaient de la session d’invité.
* **MDVA-38626** (*pour Adobe Commerce et Magento Open Source >=2.3.3 &lt;2.4.5*) - Correction du problème qui empêchait l’utilisateur administrateur de passer une commande sur le serveur principal à l’aide de la variable [!DNL PayPal Payflow Pro] paiement.
* **MDVA-38666** (*pour Adobe Commerce et Magento Open Source >=2.3.2 &lt;2.3.6*) - Correction du problème qui empêchait l’utilisateur administrateur de modifier les options de produit configurables dans le panier du client.
* **MDVA-38526** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.4*) - Correction du problème qui empêchait l’utilisateur administrateur d’accéder à la variable [!DNL Site-Wide Analysis tool].
* Mise à jour des correctifs : MDVA-40101.

## v1.1.8 {#v1-1-8}

* **MDVA-41215** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction du problème en raison duquel les utilisateurs obtenaient l’erreur 500 après avoir défini la variable *mage-messages* s’il existe déjà, mais qu’il n’y a aucun nouveau message.
* **MDVA-41139** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;2.4.4*) - Correction du problème en raison duquel les produits configurables étaient en rupture de stock après l’importation du produit lorsqu’une quantité=0 d’un produit simple était utilisée pour l’une de ses sources.
* **MDVA-42326** (*pour Adobe Commerce et Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Correction du problème qui entraînait une erreur des clients lors de leur passage en caisse après un délai d’expiration de session, même si le panier persistant était activé.
* **MDVA-42341** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Correction du problème en raison duquel la variable `categoryList` La requête GraphQL ne filtre pas les résultats si une requête comporte l’en-tête Magasin .
* **MDVA-38393** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction du problème qui empêchait les règles du catalogue de fonctionner pour un produit configurable si son produit simple était renommé.
* **MDVA-39153** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) : correction d’un problème en raison duquel un montant de remise n’était pas correctement calculé lors d’une réorganisation dans l’Admin.
* Mise à jour des correctifs : MDVA-28993, MDVA-41061, MDVA-35984.

## v1.1.7 {#v1-1-7}

* **MDVA-39711** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.3*) - Correction du problème qui empêchait les utilisateurs administrateurs d’accéder à la grille du client après avoir supprimé le site web.
* **MDVA-40311** (*pour Adobe Commerce et Magento Open Source >=2.4.2-p2 &lt;2.4.4*) - Correction du problème en raison duquel les utilisateurs administrateurs recevaient le message d’erreur *Sécurité ou clé de formulaire non valide. Actualisez la page* après vous être connecté à l’administrateur si le chemin d’accès d’administrateur personnalisé est configuré et que la clé secrète est activée.
* **MDVA-41631** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.4*) - Correction d’un problème en raison duquel les utilisateurs recevaient une erreur lors de la tentative de récupération des informations de commande sans option. *telephone* via GraphQL.
* **MDVA-27239** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.3.6*) - Correction du problème qui empêchait l’affichage des produits de vente croisée.
* Mise à jour des correctifs : MDVA-37068, MDVA-35254, MDVA-41164, MDVA-37916, MDVA-37478, MDVA-34551, MDVA-317799 .

## v1.1.6 {#v1-1-6}

* **MDVA-40550** (*pour Adobe Commerce et Magento Open Source >=2.3.5 &lt;2.4.4*) - Correction du problème lié aux produits manquants sur le front-end lors de la réindexation.
* **MDVA-40120** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.4*) - Correction du problème en raison duquel le tri GraphQL par DESC/ASC ne fonctionne pas avec des produits ayant la même pertinence ou le même prix.
* **MDVA-41399** (*pour Adobe Commerce et Magento Open Source >=2.3.3 &lt;2.4.2*) - Correction du problème qui empêchait les utilisateurs administrateurs d’accéder à la variable *Gérer le panier* si un client ajoute un produit à la liste des souhaits.
* **MDVA-40609** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.3*) - Correction du problème d’absence des données de produits désactivées dans la variable `cataloginventory_stock_status` table d’index, affichant des quantités de produits désactivées incorrectes.
* **MDVA-39031** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.4*) - Correction du problème qui rendait possible l’ajout d’un produit au panier via GraphQL, même s’il n’est pas affecté au site web cible.
* **MDVA-41597** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Correction du problème qui entraînait une erreur des utilisateurs lors de l’ajout de plusieurs produits configurables au panier à l’aide de GraphQL.
* **MDVA-27456** (*pour Adobe Commerce et Magento Open Source >=2.3.5 &lt;2.3.7*) - Correction d’un problème en raison duquel les utilisateurs obtenaient une erreur lors d’une tentative de chargement [!DNL Swagger].
* **MDVA-32776** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.2*) - Correction du problème de non-mise à jour de l’état du stock lorsqu’une commande est passée mais n’est pas expédiée.
* **MDVA-30862** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;2.4.0*) - Correction du problème lié à une date de commande incorrecte sur la facture PDF imprimée.
* Amélioration de la page d’index pour la variable [!DNL Quality Patch Tool]. Ajout d’une recherche et d’un filtrage pratiques pour [!DNL quality patches] à la dernière version de l’outil.
* Mise à jour des correctifs : MDVA-33382, MDVA-39482.

## v1.1.5 {#v1-1-5}

* **MDVA-41236** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction du problème qui rendait impossible la création ou la modification d’une mise à jour planifiée existante pour un produit si la Date de fin a été supprimée précédemment.
* **MDVA-41046** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction du problème en raison duquel des produits simples avec des options personnalisées étaient disponibles pour l’affectation à des produits configurables/regroupés.
* **MDVA-40545** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction du problème en raison duquel seul le premier noeud d’une page était récupéré même s’il existait plusieurs noeuds pour la même page.
* **MDVA-41164** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.3-p1*) - Correction du problème qui empêchait un utilisateur administrateur d’enregistrer ou de modifier une société avec un attribut client personnalisé de type fichier ou image.
* **MDVA-39229** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction du problème qui entraînait l’affichage de l’erreur suivante après la mise à jour de l’heure de début de mise à jour de la règle de catalogue intermédiaire : *Une erreur s’est produite lors de la mise à jour de Cron Job staging_synchronize_entities_period : la mise à jour active ne peut pas être supprimée.*
* **MDVA-40619** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction du problème qui entraînait une erreur 500 lors de la tentative de modification en ligne d’une page CMS suite à des modifications apportées à la hiérarchie de la page CMS.
* **MDVA-41061** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.3*) - Correction du problème de réinitialisation de l’état du stock sur vendable lorsqu’un produit est enregistré depuis l’administrateur.
* **MDVA-31763** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction du problème en raison duquel les règles de prix du catalogue étaient restaurées (ou non appliquées) jusqu’à la réindexation manuelle.
* **MDVA-37748** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.3*) - Correction du problème en raison duquel une requête GraphQL renvoyait des produits non attribués à un catalogue partagé.

## v1.1.4 {#v1-1-4}

* **MDVA-40399** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) : correction d’un problème en raison duquel les factures partielles d’une même commande ne pouvaient pas être créées simultanément via l’API REST.
* **MDVA-40101** (*pour Adobe Commerce et Magento Open Source >=2.3.2 &lt;2.4.0*) - Correction du problème en raison duquel les articles ne sont pas supprimés du mini panier après un placement de commande réussi à l’aide de la commande [!DNL PayPal Express] Passage en caisse.
* **MDVA-40401** (*pour Adobe Commerce et Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Correction du problème en raison duquel la valeur d’utilisation des coupons changeait même si le placement d’une commande échouait.
* **MDVA-40537** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;=2.4.0-p1*) - Correction du problème qui entraînait une erreur lors de la création d’une vue de magasin si plusieurs pages CMS avec la même clé d’URL existaient.
* **MDVA-37725** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;=2.4.3-p1*) - Correction du problème en raison duquel les courriers électroniques de commande asynchrones envoyés à partir de sites web autres que les sites par défaut contenaient des URL de logo provenant du site web par défaut.
* **MDVA-39482** (*pour Adobe Commerce et Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Correction du problème de rupture de stock d’un produit importé avec une quantité &quot;0&quot; lorsque les commandes en arrière-plan étaient activées.
* **MDVA-40435** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;2.4.4*) : corrige le problème lié à une remise incorrecte sur les produits en bundle avec des prix dynamiques lorsqu’ils sont appliqués via GraphQL.
* **MC-42528** (*pour Adobe Commerce et Magento Open Source >=2.4.3 &lt;=2.4.3-p1*) - Correction du problème en raison duquel la variable `categoryList` La requête GraphQL renvoie les catégories affectées et non affectées.
* **MDVA-29400** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;=2.3.7-p1 || >=2.4.0 &lt;=2.4.0-p1*) - Correction du problème lié aux commandes dupliquées placées avec [!DNL PayPal Express Checkout].
* **MDVA-26005** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;=2.3.5-p2*) - Correction du problème qui rendait impossible la sélection d’une catégorie dans une arborescence de catégories pour les conditions des règles de prix du panier.
* **MDVA-25631** (*pour Adobe Commerce et Magento Open Source >=2.3.3 &lt;=2.3.5-p2*) : améliore les performances pour la modification et l’enregistrement des segments de clients qui contiennent un grand nombre de clients.

## v1.1.3 {#v1-1-3}

* **MDVA-40262** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Correction du problème qui empêchait l’affichage des requêtes de recherche GraphQL dans les termes de recherche courants dans l’Admin.
* **MDVA-40601** (*pour Adobe Commerce et Magento Open Source >=2.3.1 &lt;=2.4.2-p2*) - Correction du problème qui entraînait une erreur des utilisateurs lorsqu’ils tentaient d’obtenir des informations sur la catégorie modifiée par une mise à jour planifiée via GraphQL.
* **MDVA-37234** (*pour Adobe Commerce et Magento Open Source >=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*) - Correction du problème en raison duquel l’ajout d’un élément au panier plusieurs fois (requête parallèle) pour le même SKU créait une ligne en double pour le même ID de panier.
* **MDVA-33606** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;=2.4.2-p2*) - Correction du problème qui entraînait l’obtention d’un *Violation des contraintes uniques* lors de l’enregistrement d’une page CMS affectée à une hiérarchie.
* **MDVA-31590** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;=2.4.1-p1*) - Correction du problème qui empêchait les utilisateurs de mettre à jour les attributs en masse à l’aide des files d’attente asynchrones MySQL.
* **MDVA-36309** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Correction du problème de lenteur de la recherche de produits par attributs dans les grilles d’administration.

## v1.1.2 {#v1-1-2}

* **MDVA-38929** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) : correction d’un problème en raison duquel la facture avec FPT affichait un total général incorrect lorsque la commande était payée à partir du crédit de la boutique.
* **MDVA-37364** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;=2.4.3*) - Correction du problème en raison duquel l’attribut client personnalisé de type date rompt l’interface utilisateur de grille du client.
* **MDVA-39195** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Correction du problème qui *Ajouter au panier* était inactif sur la page de catégorie lorsque la redirection vers le panier était activée.
* **MDVA-37115** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Correction du problème en raison duquel une *Seulement 0 gauche* l’avis s’affiche sur la page produit configurable.
* **MDVA-39521** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.4*) - Correction du problème qui empêchait l’utilisateur de définir des adresses de livraison sur le panier avec un numéro de téléphone vide via GraphQL.
* **MDVA-39384** (*pour Adobe Commerce et Magento Open Source >=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*) - Correction du problème qui empêchait l’enregistrement de l’attribut client personnalisé pour un utilisateur de la société.
* **MDVA-39043** (*pour Adobe Commerce et Magento Open Source >=2.3.4 &lt;=2.4.3*) - Correction du problème qui entraînait une erreur lors de l’ajout de la variable *Produits* sur la page CMS.
* **MDVA-39966** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*) - Correction du problème lié au déploiement de paramètres régionaux incorrects.
* **MDVA-38852** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;=2.3.5-p2*) - Correction du problème en raison duquel l’inventaire des catalogues par conception verrouillait les tableaux pour les mises à jour qui diminuaient considérablement les performances dans les cas de plusieurs commandes parallèles.
* **MDVA-39986** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.3*) - Correction du problème qui empêchait l’utilisateur de passer une commande dans Admin on MacOS à l’aide du navigateur Safari.
* **MDVA-38447** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.4*) - Correction de deux problèmes : où la variable *Non visible individuellement* les produits enfants configurables sont renvoyés dans la réponse GraphQL et optimisent la requête de produits MySQL pour GraphQL avec filtre de catégorie.
* **MDVA-40134** (*pour Adobe Commerce et Magento Open Source >=2.4.2 &lt;2.4.3*) - Correction du problème en raison duquel GraphQL ne renvoyait aucun produit associé lorsque le catalogue partagé était activé.
* **MDVA-39935** (*pour Adobe Commerce et Magento Open Source >=2.4.1 &lt;2.4.4*) - Correction du problème en raison duquel GraphQL renvoyait des produits enfants configurables désactivés au niveau du site web.

## v1.1.1 {#v1-1-1}

* **MDVA-36021** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;2.4.4*) - Correction du problème en raison duquel la variable *Appel à une fonction membre getId()* s’affiche sur la page des détails de la commande dans Admin.
* **MDVA-34948** (*pour Adobe Commerce et Magento Open Source >=2.3.6 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.0-p1*) - Correction du problème lié aux requêtes de longue durée, comme `GET_LOCK`.
* **MDVA-39305** (*pour Adobe Commerce et Magento Open Source >=2.4.0 &lt;=2.4.2-p1*) - Correction du problème qui empêchait les clients enregistrés de se connecter avec Google ReCaptcha activé.
* **MDVA-37897** (*pour Adobe Commerce et Magento Open Source >=2.3.0 &lt;2.4.4*) - Correction d’un problème lié à une redirection incorrecte lorsqu’un client tente d’ajouter des produits avec des options du widget Récemment consultés.

## v1.1.0 {#v1-1-0}

* Des catégories de correctifs ont été introduites afin d’améliorer l’expérience utilisateur et de faciliter la recherche des correctifs requis pour les clients.
* La variable `patches.json` a été renommé `support-patches.json`.
* **MDVA-38799** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Correction du problème en raison duquel les produits téléchargeables n’étaient pas enregistrés après la création d’une mise à jour intermédiaire.
* **MDVA-37592** (*pour Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - Correction du problème en raison duquel le tri par prix ne fonctionne pas correctement pour les produits dont le prix zéro est affecté au catalogue partagé.
* **MDVA-38827** (*pour Adobe Commerce >=2.3.3-p1 &lt;2.4.4*) - Correction du problème qui entraînait la réception par les clients d’un courrier électronique d’expédition de commande contenant un message d’erreur.

## v1.0.26 {#v1-0-26}

* **MDVA-38468** (*pour Adobe Commerce >=2.3.2 &lt;=2.3.5-p2*) - Correction de l’erreur lors de l’enregistrement des pages CMS : *L’élément avec le même ID PAGE_ID existe déjà*.
* **MDVA-34680** (*pour Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;2.4.3*) - Correction du problème de l’heure de création du compte client qui n’était pas correctement filtrée dans la grille des clients.
* **MDVA-37068** (*pour Adobe Commerce >=2.3.1 &lt;2.4.4*) : correction d’un problème en raison duquel un taux d’imposition incorrect s’affichait lorsque le panier ne contenait que des produits virtuels.
* **MDVA-38608** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Correction du problème de suppression des tables temporaires lorsque la réindexation n’est pas terminée.
* **MDVA-38308** (*pour Adobe Commerce >=2.3.5 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.1-p1 || >=2.4.2 &lt;2.4.4*) - Correction des problèmes liés à l’ajout de [!DNL Vimeo] des vidéos aux produits.

## v1.0.25 {#v1-0-25}

* **MDVA-37916** (*pour Adobe Commerce >=2.3.6 &lt;2.4.3*) - Correction du problème qui empêchait le client d’accéder à la page de confirmation du paiement lors de l’utilisation de la variable [!DNL Paypal Payment Advanced] .
* **MDVA-37082** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Correction du problème qui se produisait lors de l’enregistrement du stock personnalisé de produits groupés pour que le produit s’affiche en rupture de stock dans le front-end.
* **MDVA-36572** (*pour Adobe Commerce >=2.3.5 &lt;2.4.3*) - Correction du problème en raison duquel les mises à jour Mémo de crédit ne provoquaient plus de mises à jour de réservation de produits en double dans la base de données.
* **MDVA-38132** (*pour Adobe Commerce >=2.3.3 &lt;2.4.3*) - Correction du problème qui se produisait lorsque le panneau d’administration n’était pas accessible en raison d’un événement *trop de redirections* erreur.
* **MDVA-38270** (*pour Adobe Commerce >=2.4.1 &lt;2.4.3*) - Correction du problème lié à l’absence d’informations sur les cartes cadeau dans le total de la commande dans GraphQL.

## v1.0.24 {#v1-0-24}

* **MDVA-37779** (*pour Adobe Commerce >=2.4.2 &lt;=2.4.4*) - Correction du problème lié à l’ajout d’un produit configurable au panier via GraphQL lorsque l’ID de site web ne correspond pas à l’ID de magasin.
* **MDVA-36832** (*pour Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - Correction du problème de duplication des images sur les pages lorsque la largeur d’affichage est de 768 px.
* **MDVA-37874** (*pour Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;=2.4.2-p1*) - Correction du problème qui *Montant de remise fixe pour le panier entier* s’applique incorrectement à un produit groupé contenant plusieurs options.
* **MDVA-37913** (*pour Adobe Commerce >=2.3.0 &lt;=2.4.0-p1*) - Correction du problème de disparition des liens téléchargeables si le produit téléchargeable était mis à jour via l’API.
* **MDVA-34330** (*pour Adobe Commerce >=2.3.1 &lt;=2.4.2-p1*) - Correction du problème en raison duquel les commandes de la grille Commandes ne sont pas filtrées en fonction du fuseau horaire de l’administrateur.

## v1.0.23 {#v1-0-23}

* **MDVA-37478** (*pour Adobe Commerce >=2.3.0 &lt;=2.3.7*) - Correction d’un problème en raison duquel Adobe Commerce générait une erreur lors de la création d’une facture partielle pour les commandes passées avec la variable *Paiement sur compte* mode de paiement via l’API REST.
* **MDVA-37362** (*pour Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - Correction du problème en raison duquel les valeurs des options de produit configurables et les valeurs d’attribut de variante étaient vides dans la réponse GraphQL.
* **MDVA-37288** (*pour Adobe Commerce 2.4.2*) - Correction du problème en raison duquel des prix de niveau incorrects étaient renvoyés après la demande GraphQL.
* **MDVA-37225** (*pour Adobe Commerce >=2.4.1 &lt;=2.4.2-p1*) - Correction du problème de blocage du processus de chargement lors de la création rapide d’un ordre lorsqu’il existe une valeur entière dans les SKU importés.
* **MDVA-37224** (*pour Adobe Commerce >=2.3.3 &lt;=2.4.2-p1*) - Correction du problème en raison duquel les clients ne pouvaient pas payer pour un devis négociable avec [!DNL PayFlow Pro] avec un autre produit dans le panier.
* **MDVA-36286** (*pour Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - Correction du problème de coupure de l’aperçu du widget des produits Page Builder lorsque le même SKU occupe une position différente dans les sous-catégories.
* **MDVA-30186** (*pour Adobe Commerce >=2.3.4 &lt;=2.3.5-p2, >=2.4.0 &lt;=2.4.0-p1, >=2.4.2 &lt;=2.4.2-p1*) - Correction du problème en raison duquel les options d’attribut étaient triées par valeur d’option au lieu du nombre d’éléments d’attribut dans la réponse GraphQL.

## v1.0.22 {#v1-0-22}

* **MDVA-36718** (*pour Adobe Commerce >=2.3.0 &lt;=2.4.2*) - Correction du problème en raison duquel les anciennes options personnalisées restaient après avoir été modifiées via l’API.
* **MDVA-35773** (*pour Adobe Commerce >=2.3.6 &lt;=2.3.6-p1 || >=2.4.1 &lt;=2.4.2*) - Correction du problème en raison duquel le total général n’était pas affiché comme zéro sur la facture pour les commandes avec une remise de 100 %.
* **MDVA-36833** (*pour Adobe Commerce 2.4.2*) - Correction du problème lié aux résultats de recherche qui affichaient un nombre aléatoire de produits par page après l’exclusion de certains produits du catalogue partagé.
* **MDVA-37182** (*pour Adobe Commerce >=2.4.1 &lt;=2.4.2*) - Correction du problème d’obtention de résultats de recherche incorrects dans les deux [!DNL Elasticsearch] version 6 et version 7.
* **MDVA-36253** (*pour Adobe Commerce >=2.4.0 &lt;=2.4.1-p1*) : correction du problème en raison duquel un sous-total incorrect s’affichait dans le mini panier après la suppression d’un article.
* **MDVA-36853** (*pour Adobe Commerce 2.4.2*) - Correction du problème en raison duquel aucune image n’apparaissait lors du chargement de galeries multimédia volumineuses.

## v1.0.21 {#v1-0-21}

* **MDVA-34665** (*pour Adobe Commerce >=2.3.4 &lt;=2.3.4-p2*) - Correction du problème lié aux produits regroupés manquants sur les pages de catégories.
* **MDVA-36615** (*pour Adobe Commerce 2.4.2*) - Correction du problème lié à un nombre de produits incorrect dans la grille de produits Admin .
* **MDVA-36464** (*pour Adobe Commerce >=2.4.0 &lt;=2.4.2*) - Correction du problème de dysfonctionnement de la configuration des notifications électroniques au niveau de l’affichage en magasin.
* **MDVA-36138** (*pour Adobe Commerce ^2.3.2*) - Correction d’un problème en raison duquel le prix de livraison n’était pas ajusté et le prix de livraison complet était présenté aux clients si tous les articles du panier ne remplissaient pas les critères de la règle du panier de livraison gratuit.
* **MDVA-36424** (*pour Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 || >=2.0.0 &lt;2.2.0*) - Correction du problème de disparition des images multimédia associées aux éléments du créateur de pages lorsque le contenu est modifié à plusieurs reprises si l’URL de base du serveur principal est différente de l’URL de base du storefront.
* **MDVA-35984** (*pour Adobe Commerce ^2.4.0*) - Correction du problème lié à une quantité de produit et une quantité vendable incorrectes après la création de plusieurs envois simultanés pour le même produit.

## v1.0.20 {#v1-0-20}

* **MDVA-36170** (*pour Adobe Commerce >=2.3.4 &lt;2.4.2*) - Ceci corrige le problème en raison duquel la requête GraphQL n’était pas mise en cache à l’aide de la balise de cache de catégorie.
* **MDVA-33168** (*pour Adobe Commerce >=2.3.3 &lt;2.4.2*) - Correction du problème lors de la mise à jour d’un attribut de produit via l’API, tous les autres attributs passant à une valeur vide.
* **MDVA-19640** (*pour Adobe Commerce >=2.3.0*) - Correction du problème qui [!DNL Advanced Reporting] n’affiche aucune donnée.
* **MDVA-11189** (*pour Adobe Commerce >=2.3.0 &lt;2.3.5*) - Correction du problème qui se produisait lors de l’importation d’un fichier CSV pour mettre à jour le stock de produits (lignes du `cataloginventory_stock` sont supprimées.
* **MDVA-26639** (*pour Adobe Commerce >=2.3.3-p1 &lt;2.3.6*) : correction d’un problème en raison duquel, si un modèle d’email de confirmation de commande était créé, les éléments de commande manquaient dans le courrier électronique de commande.
* **MDVA-15546** (*pour Adobe Commerce >=2.3.0*) - Correction du problème qui, après la création d’une commande, *Column entity_id où la clause est ambiguë* s’affiche dans le journal des exceptions.
* **MDVA-21095** (*pour Adobe Commerce >=2.3.0 &lt;2.3.5*) - Correction du problème lors d’une requête `INSERT INTO search_tmp` ne se terminera pas après la mise à jour de la valeur d’attribut de masse.
* **MDVA-23845** (*pour Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - Correction du problème en raison duquel les modèles d’email ne pouvaient pas être prévisualisés une fois la minification JavaScript activée.
* **MDVA-22026** (*pour Adobe Commerce >=2.3.2 &lt;2.3.4*) - Correction du problème d’échec de l’importation de produits à partir d’un fichier CSV, y compris des images provenant d’URL externes.
* **MDVA-22383** (*pour Adobe Commerce >=2.3.0 &lt;2.3.4*) : correction d’un problème en raison duquel l’enregistrement d’un produit prenait beaucoup de temps et les sauts de page.
* **MC-41359** (*pour Adobe Commerce >=2.3.6-p1 &lt;2.3.7, >=2.4.2 &lt;2.4.3*) - Correction du problème des paramètres de cookie SameSite incorrects.

## v1.0.19 {#v1-0-19}

* **MDVA-33614** (*pour Adobe Commerce 2.4.1*) - Correction du problème de renvoi de l’erreur suivante par le Créateur de pages : *Une erreur s’est produite lors du lancement du créateur de pages. Veuillez consulter votre contact du support technique.*
* **MDVA-35356** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) : correction d’un problème en raison duquel le retour du crédit de magasin était incorrect après l’annulation partielle de la commande.
* **MDVA-33289** (*pour Adobe Commerce >=2.4.0 &lt;2.4.3*) - Correction du problème d’affichage du code JavaScript brut dans l’interface utilisateur de l’adresse de facturation lors de l’extraction si [!DNL Google Tag Manager] est activée.
* **MDVA-35982** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Correction du problème qui empêchait les utilisateurs administrateurs limités à un site web spécifique de créer une livraison pour la commande passée sur le même site web.
* **MDVA-35155** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6*) - Correction du problème qui rendait impossible l’achat d’un produit en regroupement si le titre de l’option était modifié.
* **MDVA-35910** (*pour Adobe Commerce >=2.4.1 &lt;2.4.3*) - Correction du problème qui rendait impossible la création d’un nouveau compte client après la désactivation de la fonctionnalité Se connecter en tant que client .
* **MDVA-34474** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Correction du problème lors de l’ajout d’un produit à la liste des demandes à l’aide de l’API .
* **MDVA-34591** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Correction d’un problème lié à un mauvais calcul de remise de règle de panier pour *Remise de qualité maximale appliquée à* et *Étape de qualité de remise (Buy X)*.
* **MDVA-33704** (*pour Adobe Commerce >=2.4.0 &lt;2.4.3*) - Correction du problème en raison duquel la variable *Saut en magasin* l’option d’expédition ne s’affiche pas, bien que configurée pour être disponible.
* **MDVA-34928** (*pour Adobe Commerce >=2.3.5 &lt;2.3.5-p2*) - Correction du problème d’affichage indéfini du chargeur de page après la suppression du crédit de magasin du paiement.
* **MDVA-35254** (*pour Adobe Commerce >=2.3.1 &lt;2.4.3*) - Correction des problèmes liés à CAPTCHA lors de l’extraction.
* **MDVA-35569** (*pour Adobe Commerce >=2.3.4 &lt;2.4.2*) - Correction du problème en raison duquel la variable *taxes sur les produits fixes* n’est pas renseigné dans la réponse GraphQL lorsque l’état est spécifié.
* **MDVA-35847** (*pour Adobe Commerce >=2.4.1 &lt;2.4.3*) - Correction du problème B2B qui se produisait lorsque le formulaire Utilisateurs de l’entreprise était rompu si un attribut client personnalisé était utilisé.
* **MDVA-31307** (*pour Adobe Commerce >=2.4.0 &lt;2.4.2*) - Correction du problème en raison duquel *Mémoire insuffisante* erreurs sur certaines catégories en raison de problèmes de mise en whiteliste dynamique CSP pour les blocs mis en cache.

## v1.0.18 {#v1-0-18}

* **MDVA-32655** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) : corrige les erreurs *en cours* l’état du message à la valeur correcte *complete* message pour les consommateurs `quoteItemCleaner` après la suppression de plusieurs produits.
* **MDVA-34102** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) : fixe la quantité de Stock par défaut à zéro pour les produits désactivés sur les pages Grille de produits et Modifier le produit dans la zone d’administration.
* **MDVA-35286** (*pour Adobe Commerce >=2.4.0 &lt;2.4.2*) - Correction du problème en raison duquel une erreur se produisait lorsqu’un client regroupait des produits dans le panier et passait de l’extraction à l’extraction sur une seule page.
* **MDVA-35312** (*pour Adobe Commerce >=2.4.1-p1 &lt;2.4.2*) - Correction du code de réponse 500 lorsqu’une requête GraphQL vide.
* **MDVA-34189** (*pour Adobe Commerce >=2.3.4 &lt;2.4.3*) - Correction du délai d’attente de 503 premiers octets sur [!DNL Visual Merchandiser] requêtes lors du chargement de la page Catégorie d’administration .
* **MDVA-34695** (*pour Adobe Commerce >=2.3.0 &lt;2.4.1*) - Correctifs négatifs `children_count` après suppression des catégories.

## v1.0.17 {#v1-0-17}

* **MDVA-34012** (*pour Adobe Commerce >=2.3.1 &lt;2.4.3*) - Correction du problème en raison duquel la variable *Utiliser la valeur par défaut* est effacée une fois les modifications planifiées appliquées. Le problème s’affiche une fois que les modifications planifiées ne sont plus en vigueur.
* **MDVA-35064** (*pour Adobe Commerce >=2.3.3 &lt;2.4.3*) - Correction du problème en raison duquel les réécritures d’URL ne sont pas générées pour les produits configurables créés via l’API.
* **MDVA-34943** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) : correction d’un problème en raison duquel l’ordre rapide mettait en cache les SKU précédemment saisis.
* **MDVA-35197** (*pour Adobe Commerce >=2.3.5 &lt;2.4.0*) - Correction d’un problème qui entraînait une erreur lors de l’ajout au panier à l’aide de GraphQL si des produits précédemment ajoutés devenaient en rupture de stock.
* **MDVA-34850** (*pour Adobe Commerce >=2.3.1 &lt;2.4.0*) - Correction du problème en raison duquel les options en rupture de stock d’un produit configurable ne s’affichaient pas au lieu d’être affichées comme étant ponctuelles.
* **MDVA-34867** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Correction du problème qui empêchait l’enregistrement des valeurs d’un champ de condition défini pour une mise à jour planifiée.
* **MDVA-35092** (*pour Adobe Commerce >=2.3.5 &lt;2.4.3*) - Correction du problème qui empêchait les utilisateurs d’ajouter [!DNL Vimeo] vidéos en raison d’un abandon [!DNL Vimeo] API.

## v1.0.16 {#v1-0-16}

* **MDVA-33453** (*pour Adobe Commerce >=2.3.6 &lt;2.4.3*) - Correction du problème de coupure de l’aperçu du type de contenu de produits du créateur de pages si les produits correspondants avaient des prix différents pour chaque site web.
* **MDVA-32634** (*pour Adobe Commerce ^2.3.1*) - Correction du problème en raison duquel la variable `url_path` de la catégorie affectée à tous les magasins reste inchangée après le déplacement de la catégorie dans la hiérarchie.
* **MDVA-33344** (*pour Adobe Commerce ^2.3.0*) - Correction du problème de codage en dur `rma_item` L’identifiant du jeu d’attributs par défaut de l’entité est utilisé à la place de la valeur de la base de données.
* **MDVA-34192** (*pour Adobe Commerce >=2.3.4 &lt;2.4.3*) - Correction du problème qui empêchait de modifier/spécifier la date de naissance du client au format jj/mm/aaaa.
* **MDVA-34847** (*pour Adobe Commerce ^2.3.0*) - Correction de la conversion de type ID de magasin en entier pour les conditions SQL dans les collections d’administrateurs pour les utilisateurs administrateurs disposant d’autorisations personnalisées.
* **MDVA-34886** (*pour Adobe Commerce ^2.3.2*) - Correction du problème en raison duquel la recherche ne renvoyait aucun résultat si *poids* l’attribut product est configuré comme pouvant faire l’objet d’une recherche.

## v1.0.15 {#v1-0-15}

* **MDVA-33559** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Correction du problème de [!DNL PayPal Payflow Pro] échec de paiement avec erreur de format de liste des paramètres de redirection.
* **MDVA-34023** (*pour Adobe Commerce >=2.3.0 &lt;2.4.3*) - Correction du problème d’erreur *Aucune entité de ce type avec addressId* s’affiche de manière aléatoire sur les navigateurs des visiteurs.
* **MDVA-32759** (*pour Adobe Commerce >=2.3.1 &lt;2.4.3 avec extension B2B*) - Correction du problème en raison duquel les catalogues partagés supprimaient les tarifs de niveau existant.
* **MDVA-33482** (*pour Adobe Commerce ^2.3.5*) : correction d’un problème en raison duquel la génération d’un avoir sur une facture partielle générait une taxe sur le total de la commande au lieu de la taxe sur cette facture partielle.
* **MDVA-33393** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction de l’erreur *countryId fourni n’existe pas*.
* **MDVA-33632** (*pour Adobe Commerce >=2.3.0 &lt;2.3.7*) - Fournit un correctif pour lequel le message d’exception *Ce produit est en rupture de stock* s’affiche désormais pour un utilisateur administrateur lorsqu’il tente de réorganiser un produit en rupture de stock.
* **MDVA-34469** (*pour Adobe Commerce >=2.4.1 &lt;2.4.2*) - Correction du problème d’échec des mutations GraphQL sur le panier d’un client lors de l’utilisation de plusieurs vues de magasin.
* **MDVA-33976** (*pour Adobe Commerce >=2.3.0 &lt;2.3.7*) - Correction du problème qui entraînait l’affichage du produit en rupture de stock sur le storefront après la suppression de la deuxième option du produit en regroupement.
* **MDVA-33894** (*pour Adobe Commerce >=2.4.0 &lt;2.4.1 avec extension B2B*) - Correction de plusieurs problèmes liés à la fonctionnalité de commande rapide, notamment l’ajout et la suppression de plusieurs produits et le respect de la casse des SKU.
* **MDVA-27664** (*pour Adobe Commerce >=2.3.4 &lt;2.3.6*) - Correction du problème dans le formulaire d’enregistrement du client qui provoquait l’affichage d’une erreur : *ERROR - La date de naissance ne doit pas être supérieure à aujourd’hui.*
* **MDVA-33970** (*pour Adobe Commerce >=2.3.4 &lt;2.4.2*) : correction d’un problème en raison duquel un mauvais signe de devise s’affichait dans la Note de crédit lorsque la portée de l’attribut de prix était définie sur le site web.
* **MDVA-33992** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème des prix spéciaux B2B qui s’affichaient incorrectement lors du passage en caisse.
* **MDVA-34100** (*pour Adobe Commerce >=2.3.4 &lt;2.4.2 avec extension B2B*) - Correction du problème qui empêchait la création d’un compte d’entreprise à partir de la page de structure de l’entreprise.

## v1.0.14 {#v1-0-14}

* **MDVA-31969** (*pour Adobe Commerce >=2.3.3 &lt;2.3.5, >=2.4.0 &lt;2.4.2*) - Correction du problème lié aux images dupliquées après l’importation d’un produit à partir d’un fichier CSV.
* **MDVA-33382** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction des problèmes d’invalidation des indexeurs après suppression de produits d’une catégorie.
* **MDVA-28511** (*pour Adobe Commerce >=2.3.5 &lt;2.3.6*) - Correction du problème lorsqu’il n’est pas possible de terminer [!DNL PayPal] passage en caisse si le champ Nom contient certains caractères (comme des majuscules accentuées).
* **MDVA-31519** (*pour Adobe Commerce >=2.3.5 &lt;2.3.6*) - Correction du problème lié aux délais d’attente dans le passage en caisse des invités lorsqu’une règle de vente à l’échelle du site est en cours d’utilisation.
* **MDVA-33281** (*pour Adobe Commerce >=2.3.4 &lt;2.3.6*) - Correction du problème d’erreur fatale dans `inventory:reservation:list-inconsistencies` en raison d’un type de paramètre de SKU incorrect.
* **MDVA-24201** (*pour Adobe Commerce >=2.3.0 &lt;2.3.5*) : correction d’un problème en raison duquel les prix ne reflètent pas la règle de prix du panier planifiée tant qu’ils n’ont pas été réindexés manuellement.
* **MDVA-32694** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6 || >= 2.4.0 &lt;2.4.2*) - Correction du problème qui empêchait un utilisateur administrateur d’ajouter un produit à un guillemet négociable s’il était lié à un magasin autre qu’un magasin par défaut.
* **MDVA-33516** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6*) - Correction du problème qui entraînait une erreur lors de la modification d’un produit groupé dans une liste de demandes.
* **MDVA-33975** (*pour Adobe Commerce >=2.3.4 &lt;2.4.2*) - Correction de plusieurs problèmes liés au calcul des prix dans les requêtes GraphQL.

## v1.0.13 {#v1-0-13}

* **MDVA-30858** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème lié à [!DNL PayPal] Les rapports de règlement ne sont pas disponibles sous **Rapports** > **Ventes** > **[!DNL PayPal]** Accord comme prévu.
* **MCP-87** (*pour Adobe Commerce >=2.3.1 &lt;2.4.2*) - Amélioration du temps d’indexation pour les indexeurs de produits de catégorie et de stocks pour les profils volumineux.
* **MDVA-33106** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème en raison duquel les modifications de produit reprogrammées étaient effacées après le cron . `run` est exécutée.
* **MDVA-19391** (*pour Adobe Commerce >=2.3.0 &lt;2.3.5*) - Correction du problème qui `analytics_collect_data` renvoie une erreur en raison d’enregistrements de description NULL dans la variable `catalog_category_entity_text` table.
* **MDVA-20376** (*pour Adobe Commerce >=2.3.2 &lt;2.3.4*) - Correction du problème lié à la variable *Aucune entité de ce type avec customerId = 1* dans la variable `exception.log` pour les clients connectés après l’emplacement de la commande.
* **MDVA-23764** (*pour Adobe Commerce >=2.3.2 &lt;2.3.5*) - Correction du bogue dans `JsFooterPlugin.php` qui affecte l&#39;affichage des blocs dynamiques.
* **MDVA-13203** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème en raison duquel la variable *Intégrité contrainte violation search_tmp_table* s’affiche après une réindexation complète.
* **MDVA-23426** (*pour Adobe Commerce >=2.3.3 &lt;2.3.5*) - Correction du problème en raison duquel les emails de notification envoyés par Adobe Commerce contenaient un corps vide avec du contenu ajouté en tant que pièce jointe.
* **MDVA-22150** (*pour Adobe Commerce >=2.3.1 &lt;2.3.4*) - Correction du problème qui empêchait les clients disposant d’un produit configurable dans le panier et d’un bon appliqué de se connecter si ce produit configurable était désactivé dans l’administrateur.
* **MDVA-32545** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) : correction d’un problème qui empêchait l’envoi automatique de factures lors de la création de commandes de la part de l’administrateur.
* **MDVA-32714** (*pour Adobe Commerce >=2.3.4 &lt;2.4.1*) - Correction du problème en raison duquel le prix du groupe de clients ne fonctionnait pas dans la requête de produit GraphQL.

## v1.0.12 {#v1-0-12}

* **MDVA-31399** (*pour Adobe Commerce >=2.3.2 &lt;2.4.2*) - Ajoute la variable *Sous-Total (Incl. Tax)* pour fixer les conditions des règles de prix.
* **MDVA-31236** (*pour Adobe Commerce >=2.4.0 &lt;2.4.2*) - Correction du problème qui empêchait les administrateurs disposant d’un accès aux ressources personnalisées de configurer 2FA ou de se connecter.
* **MDVA-30845** (*pour Adobe Commerce >=2.3.5 &lt;2.3.7*) - Correction du problème en raison duquel la variable *Désolée, aucun guillemet n&#39;est disponible pour l&#39;instant pour cette commande* s’affiche lorsque vous ne vous connectez pas à UPS XML/USPS/DHL et qu’aucun autre mode de livraison n’est disponible.
* **MDVA-32133** (*pour Adobe Commerce >=2.4.0 &lt;2.4.1*) - Correction du problème en raison duquel la galerie multimédia ne se chargeait pas à partir du Créateur de pages dans certains cas.
* **MDVA-12304** (*pour Adobe Commerce >=2.3.0*) : augmente le nombre maximum de cookies de 50 à 200.
* **MDVA-32632** (*pour Adobe Commerce >=2.3.2 &lt;2.3.5*) - Correction du problème d’affichage des commandes dans le système de paiement, mais pas dans Adobe Commerce.
* **MDVA-32449** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || >=2.4.1 &lt;2.4.2 avec extension B2B*) - Correction d’un problème en raison duquel l’historique des commandes se charge très lentement ou ne se charge pas du tout.
* **MDVA-32739** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème qui entraînait l’envoi d’anciens courriers électroniques de vente lors de l’activation des notifications par courrier électronique asynchrone.

## v1.0.11 {#v1-0-11}

* **MC-38509** (*pour Adobe Commerce 2.3.6, 2.4.1*) - Correction du problème en raison duquel la variable *Création d’un compte* reste désactivé après correction des données incorrectes dans la variable *Créer un compte client* formulaire.
* **MDVA-31006** (*pour Adobe Commerce 2.3.0, 2.3.1*) - Correction du problème d’affichage des commandes dupliquées après le placement d’une commande à l’aide de [!DNL Paypal Express] paiement.
* **MDVA-25602** (*pour Adobe Commerce 2.3.0*) - Correction d’un problème lié à [!DNL PayPal Payflow Pro] mode de paiement et traitement des cookies comme `SameSite=Lax` par défaut, dans le navigateur Chrome 80 et la réponse de l’API redirigent vers la page de connexion du client.

## v1.0.10 {#v1-0-10}

Correctifs mineurs pour les versions de correctif

## v1.0.9 {#v1-0-9}

* **MDVA-31363** (*pour Adobe Commerce >=2.3.2 &lt;2.4.2*) - Correction du problème en raison duquel la règle sur le prix du panier avec coupon ne s’appliquait pas via GraphQL lorsque *Remise de montant fixe pour le panier entier* est utilisée.
* **MDVA-30889** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème d’erreur qui se produisait après la facturation d’un lot avec des produits virtuels et simples comme options.
* **MDVA-31791** (*pour Adobe Commerce >=2.3.4 &lt;2.3.5*) - Améliore les performances de la page de produits lorsque des règles cibles ou des produits liés sont utilisés.
* **MDVA-31168** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème qui empêchait l’affichage du fichier CSV d’exportation de produits et provoquait une erreur d’allocation de mémoire.
* **MDVA-32313** (*pour Adobe Commerce >=2.3.0 &lt;2.3.4*) - Correction du problème en raison duquel les produits configurables pouvaient être ajoutés à la liste des souhaits avec des options de configuration incorrectes.
* **MDVA-31759** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème en raison duquel les produits ne sont pas mis à jour avec *menu déroulant* et *textarea* valeurs d’attribut lors de l’importation CSV.
* **MDVA-32012** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème qui empêchait la validation des codes postaux en Corée et en Argentine.
* **MDVA-31640** (*pour Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) - Correction d’un problème en raison duquel un prix spécial ne pouvait pas être mis à jour via l’API REST.
* **MDVA-28651** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6 || >2.4.0 avec extension B2B*) - Correction d’un problème de performances lors du chargement de guillemets négociables via l’API REST.

## v1.0.8 {#v1-0-8}

* **MDVA-31242** (*pour Adobe Commerce >=2.3.0 &lt;2.4.1 avec extension B2B*) - Correction du problème d’affichage d’un signe de devise incorrect dans la grille Mémo de crédit.
* **MDVA-31295** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème en raison duquel les points de récompense ne sont pas calculés lorsqu’une commande partielle est terminée et que les éléments sont taxés.
* **MDVA-30112** (*pour Adobe Commerce >=2.3.4 &lt;2.4.2*) : résout le problème en raison duquel, si le nombre de commandes dépasse la valeur *taille du lot* , Adobe Commerce considère les commandes avec la variable *en attente* comme incohérences.
* **MDVA-31150** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) : correction d’un problème en raison duquel les soldes des cartes de crédit et des cadeaux de la boutique n’étaient pas renvoyés par l’appel de l’API REST GET, lorsque la facture était validée par l’appel de l’API REST et que la commande était partiellement payée par les comptes de carte de crédit et de cadeau de la boutique.
* **MDVA-30963** (*pour Adobe Commerce >=2.3.2 &lt;2.4.2*) - Correction du problème en raison duquel les résultats de filtrage de produits définis sur ne contenaient que les valeurs spécifiées pour *Toutes les vues de magasin* dans Admin, incluez les produits dont les valeurs sont remplacées au niveau de la vue de magasin.
* **MDVA-29954** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || 2.4.2 avec extension B2B*) - Correction du problème en raison duquel la variable *Nouvelle demande d’enregistrement d’entreprise* et *Vous avez été lié à une société.* les emails sont envoyés à partir d’une adresse incorrecte.
* **MDVA-28357** (*pour Adobe Commerce >=2.3.2 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) : remplace l’analyseur standard par un analyseur personnalisé avec un jeton de mot-clé pour le champ SKU dans la variable [!DNL ElasticSearch] pour que les requêtes de recherche avec caractères génériques fonctionnent avec les SKU contenant un trait d’union (&quot;-&quot;).

## v1.0.7 {#v1-0-7}

* **MDVA-30972** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème en raison duquel l’état de la commande personnalisée était remplacé par *Traitement* après la création d’un envoi partiel à l’aide de WebApi.
* **MDVA-30428** (*pour Adobe Commerce >=2.3.4 &lt;2.3.5*) - Correction du problème qui empêchait les clients d’ajouter un produit à une liste bloquée si ce produit était affecté à une source d’inventaire personnalisée.
* **MDVA-30594** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème qui empêchait l’enregistrement d’une commande contenant plusieurs adresses lors de l’extraction lorsque FPT était configuré.
* **MDVA-29148** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème lors de la création d’un produit via un appel API, l’attribut personnalisé de produit de `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (comme Multiselect) le type n’utilise pas sa valeur par défaut si aucune valeur n’a été fournie dans la payload.
* **MDVA-30837** (*pour Adobe Commerce >=2.3.1 &lt;2.3.5*) - Ajout d’un paramètre de configuration *Inclure la taxe au montant : oui/non* dans la configuration de la méthode d’expédition gratuite . When *Inclure la taxe au montant* est défini sur *Oui*, Montant minimum de la commande est calculé comme suit : Sous-total + Taxe. When *Inclure la taxe au montant* est défini sur *Non*, Montant minimum de la commande est calculé comme sous-total
* **MDVA-25028** (*pour Adobe Commerce >=2.3.2 &lt;2.3.3 || >=2.3.5 &lt;2.3.6*) - Correction du problème qui se produisait lorsque des commandes étaient passées à l’aide de [!DNL PayPal Payflow Pro] ne sont pas définies sur l’état Fraude suspectée lorsque des filtres de fraude sont déclenchés.
* **MDVA-31224** (*pour Adobe Commerce >=2.3.3 &lt;2.3.5*) - Améliore les performances de la fonction `catalog_product_price` opération de réindexation pour les produits du lot.
* **MDVA-31321** (*pour Adobe Commerce >=2.3.2 &lt;2.3.5*) - Correction d’une page vierge (erreur) lors de la *Tout afficher* est sélectionnée. [!DNL Elasticsearch] renvoie une grande liste d’identifiants de produit. Dans ce scénario, la clause order by est convertie dans un format SQL incorrect.
* **MDVA-30815** (*pour Adobe Commerce >=2.3.2 &lt;2.3.4*) - Correction du problème qui entraînait l’affichage d’une page vierge dans Adobe Commerce lorsque vous modifiez le nombre de résultats de recherche à afficher sur la page des résultats de recherche. [!DNL Elasticsearch] affiche désormais correctement les résultats des pages de catégorie lorsque vous modifiez le nombre de résultats de recherche affichés par page.
* **MDVA-30782** (*pour Adobe Commerce >=2.3.5 &lt;2.4.2*) - Correction du problème d’affichage du bloc dynamique, quelle que soit la règle du panier.
* **MDVA-31021** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème de performances dans `module-catalog-import-export/Model/Import/Product/Option.php`. S’il y a plus de ~100 000 enregistrements dans `catalog_product_option` , la validation d’un nouveau fichier CSV avec un seul produit prend moins de 10 secondes.
* **MDVA-31007** (*pour Adobe Commerce >=2.4.0 &lt;2.4.1*) - Correction du problème en raison duquel les attributs d’adresse personnalisés ne s’affichaient pas correctement dans la page des détails de la commande dans la zone de mon compte et dans le serveur principal.
* **MDVA-29389** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème lié à la création de rapports avancés où l’événement `analytics_collect_data` cronjob dit : *Le port doit être configuré dans le paramètre hôte (comme localhost:3306).*.
* **MDVA-31343** (*pour Adobe Commerce >=2.3.4 &lt;2.3.6*) - Correction du problème lié à la classe body supprimée `page-layout-category-full-width` lorsqu’une catégorie est planifiée.
* **MDVA-30945** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction d’un problème en raison duquel vous recevez un message d’erreur fatal lors de la mise à jour des paniers. `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.

## v1.0.6 {#v1-0-6}

* **MDVA-28993** (*pour Adobe Commerce >=2.3.4 &lt;2.4.0*) : met en oeuvre le *La valeur minimale doit correspondre* fonctionnalité et recherche partielle [!DNL Elasticsearch] moteur. Résout les problèmes liés aux tirets dans les requêtes de recherche.
* **MDVA-30102** (*pour Adobe Commerce >=2.3.2 &lt;=2.4.0*) - Correction du problème de croissance rapide du cache Redis, car les caches de mise en page n’ont pas TTL.
* **MDVA-30599** (*pour Adobe Commerce >=2.3.4 &lt;=2.4.0*) - Correction du problème en raison duquel les guillemets d’invité créés à l’aide de l’API étaient incorrectement marqués comme guillemets pour les clients connectés.
* **MDVA-29446** (*pour Adobe Commerce >=2.3.3 &lt;=2.4.0*) - Correction d’un problème en raison duquel le prix de la méthode d’expédition non applicable s’affichait comme zéro pendant le passage en caisse.
* **MDVA-30357** (*pour Adobe Commerce >=2.3.2 &lt;=2.4.0*) - Correction du problème lié à la création d’URL d’image incorrectes lors de la génération d’un plan de site par cron.
* **MDVA-30565** (*pour Adobe Commerce >=2.3.2 &lt;=2.3.3-p1*) - Correction du problème qui *Aucune entité de ce type avec cartid = 0* s’affiche pour les clients invités lors du passage en caisse en storefront si le panier persistant est activé.
* **MDVA-29787** (*pour Adobe Commerce >=2.3.0 &lt;=2.4.0*) - Correction du problème en raison duquel la règle de ciblage pour les produits associés ne fonctionnait pas lorsque *est l’un des* est utilisée pour définir les produits à afficher.
* **MDVA-30977** (*pour Adobe Commerce >=2.3.4 &lt;=2.3.5-p2*) - Correction du problème des produits aléatoires manquants dans les catégories après la réindexation.
* **MDVA-28202** (*pour Adobe Commerce >=2.3.4 &lt;=2.4.2*) - Correction du problème de navigation par calques qui ne filtrait pas correctement les produits configurables lorsque MSI est utilisé.
* **MDVA-28300** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6*) - Correction du problème en raison duquel la demande GQL ne reflétait pas les modifications de prix des règles de prix du catalogue.
* **MDVA-31006** (*pour Adobe Commerce >=2.3.2 &lt;=2.4.2*) - Correction du problème d’affichage des commandes dupliquées après le placement d’une commande à l’aide de [!DNL Paypal Express] paiement.

## v1.0.5 {#v1-0-5}

* **MDVA-30841** (*pour Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Correction du problème de navigation par couches, où la variable *Non* La valeur des attributs de produit de type booléen n’était pas incluse dans la navigation par couche si [!DNL Elasticsearch] a été utilisé comme moteur de recherche.
* **MDVA-28191** (*pour Adobe Commerce >=2.3.3 &lt;2.4.2*) - Correction du problème en raison duquel aucun mode de paiement n’était chargé lors de la création de la commande via l’administrateur.
* **MDVA-29959** (*pour Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 avec extension B2B*) - Correction du problème en raison duquel l’utilisateur administrateur restreint avec *Entreprises* Les autorisations ne sont pas autorisées pour supprimer le compte de la société.
* **MDVA-30265** (*pour Adobe Commerce >=2.3.3 &lt;2.4.2*) - Correction du problème en raison duquel le lien de suivi des envois ne fonctionnait plus après la création de la facture.
* **MDVA-28409** (*pour Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Correction du problème en raison duquel la variable `sales_clean_quotes` la tâche cron échoue avec *out de mémoire* lorsque le nombre de guillemets expirés dans la base est énorme.
* **MDVA-30593** (*pour Adobe Commerce >=2.3.0 &lt;2.3.4*) - Correction du problème en raison duquel les guillemets qui ont expiré selon le paramètre Durée de vie des guillemets ne sont pas nettoyés.
* **MDVA-30107** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6*) - Correction du problème en raison duquel le sélecteur de magasin ne fonctionnait pas comme prévu si différentes URL de base étaient utilisées pour les vues de magasin.
* **MDVA-28763** (*pour Adobe Commerce >=2.3.2 &lt;2.3.4*) - Correction du problème de duplication de l’image du produit après la mise à jour des informations sur le produit à l’aide de l’API REST plusieurs fois.
* **MDVA-30284** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème de l’échec de l’indexeur de recherche catalogue en raison de ce qui suit : *[!DNL Elasticsearch]erreur : la limite du nombre total de champs dans l&#39;index a été dépassée.*
* **MDVA-29042** (*pour Adobe Commerce >=2.3.3 &lt;=2.3.4-p2 avec extension B2B*) - Correction du problème en raison duquel les autorisations du catalogue étaient modifiées en *Autoriser* automatiquement après l’ajout d’un nouveau produit au catalogue partagé.
* **MDVA-30428** (*pour Adobe Commerce >=2.3.3 &lt;2.4.2*) - Correction du problème qui empêchait les clients d’ajouter un produit à une liste bloquée si ce produit était affecté à une source d’inventaire personnalisée.
* **MDVA-28661** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2 avec extension B2B*) - Correction du problème qui entraînait l’apparition d’une erreur dans la section du compte de société Utilisateurs de l’entreprise après la modification de l’administrateur de l’entreprise.

## v1.0.4 {#v1-0-4}

* **MDVA-30195** (*pour Adobe Commerce 2.3.1 - 2.3.4-p2*) - Correction du problème d’échec des tâches cron si le nom de la base de données est trop long, ce qui empêchait la mise à jour des catégories sur le front-end.
* **MDVA-30106** (*pour Adobe Commerce ^2.3.0*) - Correction d’un problème en raison duquel les paiements de passage en caisse ne sont pas chargés avec *Impossible de lire la propriété &quot;length&quot; de null* dans la console JS.
* **MDVA-28656** (*pour Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.2*) : correction d’un problème en raison duquel, si une commande était passée sans aucune information de paiement (avec, par exemple, une remise de 100 %) et qu’une facture était créée pour la commande, l’état de la commande passe à *Fermé* au lieu de Terminé.
* **MDVA-30209** (*pour Adobe Commerce 2.3.0 - 2.3.3-p1*) - Correction du problème en raison duquel le groupe de clients était remplacé par défaut si le client mettait à jour les informations de son compte.
* **MDVA-30123** (*pour Adobe Commerce >=2.3.4 &lt;2.4.2*) - Correction du problème en raison duquel les libellés des options d’attribut ne sont pas correctement traduits pour les requêtes GraphQL.
* **MDVA-29996** (*pour Adobe Commerce >=2.3.3 &lt;2.4.2*) : correction d’un problème en raison duquel, après l’activation de l’autorisation de catégorie, la page de catégorie n’était pas mise en cache par le cache de la page entière.
* **MDVA-30164** (*pour Adobe Commerce >=2.3.1 &lt;2.4.2*) - Correction du problème en raison duquel les enregistrements de clients ne pouvaient pas être exportés à partir de la grille Clients s’il existait des attributs de client personnalisés.
* **MDVA-30444** (*pour Adobe Commerce >=2.3.0 &lt;2.4.1*) - Correction du problème qui empêchait l’envoi d’un email de confirmation pour les commandes passées à l’aide de GraphQL.
* **MDVA-30490** (*pour Adobe Commerce 2.3.4 - 2.3.5-p2*) - Correction du problème en raison duquel la comparaison de produits renvoyait la page d’erreur 500 si l’un des produits avait une brève description vide.
* **MDVA-30232** (*pour Adobe Commerce >=2.3.1 &lt;2.4.1*) - Correction du problème qui empêchait la réorganisation si la commande d’origine contenait une carte-cadeau.
* **MDVA-29965** (*pour Adobe Commerce >=2.3.3 &lt;2.4.0*) - Correction d’un problème en raison duquel les clients recevaient une erreur de clé de formulaire non valide lors de l’ajout d’un produit au panier.
* **MDVA-30008** (*pour Adobe Commerce >=2.3.0 &lt;2.4.2*) - Correction du problème B2B où il n’est pas possible de passer des commandes via l’API d’administration pour un produit qui se trouve dans un catalogue public.
* **MDVA-22469** (*pour Adobe Commerce 2.3.2-p2 - 2.3.3-p1*) - Correction du problème qui, après la mise à niveau vers Adobe Commerce 2.3.3, le Créateur de pages ne fonctionnait pas dans le panneau d’administration et qui empêchait le chargement de certains fichiers JS et CSS.
* **MC-35984** (*pour Adobe Commerce >=2.4.0 &lt;2.4.1*) - Correction du problème qui empêchait les marchands d’interagir avec des éléments de page sur la page Renvoie après la création d’un libellé d’expédition pour une autorisation de marchandisage de retour (RMA).

## v1.0.3 {#v1-0-3}

* **MDVA-25602** (*pour Adobe Commerce 2.3.0 - 2.3.4*) - Correction du problème lié à [!DNL PayPal Payflow Pro] mode de paiement et traitement des cookies comme `SameSite=Lax` par défaut, dans le navigateur Chrome 80 et la réponse de l’API redirigent vers la page de connexion du client.
* **MDVA-26694** (*pour Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0*) - Correction d’un problème en raison duquel les caches de produit et de catalogue expiraient tous les jours, bien que le délai d’expiration soit différent.
* **MDVA-27825** (*pour Adobe Commerce >=2.3.0 &lt;2.4.1*) - Correction du problème d’échec de l’exportation de grandes quantités de données en raison d’une fuite de mémoire.
* **MDVA-29085** (*pour Adobe Commerce >=2.3.0 &lt;=2.3.5-p1*) - Correction du problème B2B qui empêchait l’envoi de nouveaux emails d’entreprise requis si une entreprise était créée par l’API.
* **MDVA-29344** (*pour Adobe Commerce >=2.3.5 &lt;=2.4.0-p1*) - Correction du problème de blocage du Créateur de pages après la copie de texte d’un élément d’en-tête vers un élément de texte.
* **MDVA-29835** (*pour Adobe Commerce >2.3.1 &lt;2.4.2*) : correction d’un problème en raison duquel les commandes de cartes-cadeaux comportaient deux codes au lieu d’un.
* **MDVA-30052** (*pour Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - Correction d’un problème en raison duquel le contenu privé (stockage local) n’était pas renseigné correctement, ce qui entraînait des problèmes de performances.
* **MDVA-30131** (*pour Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Correction du problème de navigation par couches, où la variable *Non* La valeur des attributs de produit de type booléen n’était pas incluse dans la navigation par couche si [!DNL Elasticsearch] a été utilisé comme moteur de recherche.
* **MDVA-35514** (*pour Adobe Commerce >=2.4.0 &lt;2.4.1*) - Correction du problème lié à la création d’un libellé d’expédition et à l’ajout de produits commandés à un package dans la fenêtre modale Créer des packages .
