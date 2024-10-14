---
source-git-commit: 00b8e1bb5ee259763ddb2c52065cee2af98641e0
workflow-type: tm+mt
source-wordcount: '1154'
ht-degree: 0%

---
# Principales fonctionnalités d’Adobe Commerce 2.4.7 version bêta en octobre 2024

## Tons clairs

Cette version d’Adobe Commerce comprend plusieurs correctifs de sécurité critiques et améliorations de la plateforme.

### Sécurité

Les améliorations de sécurité suivantes apportées à cette version améliorent la conformité aux dernières bonnes pratiques en matière de sécurité :

>[!NOTE]
>
>Pour obtenir les informations les plus récentes sur les correctifs de bogues de sécurité, reportez-vous à la section [Bulletin de sécurité Adobe APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html).

<table style="table-layout:auto">
    <tbody>
        <tr>
            <td><strong>Paramètres</strong></td>
            <td>Cette version de comprend les améliorations suivantes apportées aux paramètres de sécurité :
              <ul>
                <li><strong>Rotation de la clé de chiffrement</strong> : une nouvelle commande d’interface de ligne de commande est désormais disponible pour modifier votre clé de chiffrement. Pour plus d’informations, reportez-vous à l’article <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/troubleshooting-encryption-key-rotation-cve-2024-34102">Résolution des problèmes de rotation de la clé de chiffrement : CVE-2024-34102</a> de la base de connaissances.<!-- AC-12589 --></li>
                <li><strong>Paramètres de mot de passe unique (OTP)</strong> : cette mise à jour est nécessaire pour résoudre une erreur qui a été introduite par une <a href="https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value">modification rétrocompatible</a> dans 2.4.7. La description du champ <strong>[!UICONTROL OTP Window]</strong> fournit désormais une explication exacte du paramètre et la valeur par défaut a été changée de <code>1</code> à <code>29</code>.<!-- AC-11762 --></li>
              </ul>
            </td>
        </tr>
    </tbody>
</table>

### Plateforme

Les mises à niveau suivantes de la plateforme de cette version garantissent qu’Adobe Commerce reste une plateforme robuste et fiable, prête à répondre aux besoins des environnements commerciaux modernes :

<table style="table-layout:auto">
    <tbody>
        <tr>
            <td><strong>Base</strong></td>
            <td>En accord avec notre <a href="/help/release/lifecycle-policy.md">politique de cycle de vie de prise en charge</a>, Adobe Commerce est désormais compatible avec les versions de prise en charge à long terme suivantes (LTS) des technologies de base de données suivantes :
              <ul>
                <li><strong>MariaDB 11.4 LTS</strong> <em>_(pris en charge jusqu’en 2029)_</em> : la version précédente (MariaDB 10.6) arrive en fin de vie en 2026, ce qui rend cette mise à niveau essentielle pour maintenir l’intégrité et les performances du système. MariaDB 10.6 est toujours prise en charge, mais Adobe recommande d’effectuer une mise à niveau vers MariaDB 1.4 lors de la mise à niveau vers Adobe Commerce 2.4.8.</li>
                <li><strong>MySQL 8.4 LTS</strong> <em>_(pris en charge jusqu’en 2032)_</em> : la version précédente (MySQL 8.0) arrive en fin de vie en 2026, ce qui rend cette mise à niveau essentielle au maintien de l’intégrité et des performances du système. MySQL 8.0 est toujours pris en charge, mais Adobe recommande d’effectuer une mise à niveau vers MySQL 8.4 lors de la mise à niveau vers Adobe Commerce 2.4.8.</li>
              </ul>
            </td>
        </tr>
        <tr>
            <td><strong>PHP</strong></td>
            <td>Cette version comprend les améliorations PHP suivantes :
            <ul>
              <li><strong>PHP 8.1</strong> : cette version supprime la compatibilité PHP 8.1 pour Adobe Commerce 2.4.8. Vous devez effectuer la mise à niveau vers PHP 8.3 avant de passer à Adobe Commerce 2.4.8.</li>
              <li><strong>PHP 8.2</strong> : l’une des modifications importantes de PHP 8.2 implique l’abandon de la transmission de la valeur null à des paramètres de fonction interne non nullables. Cette version traite des fonctionnalités obsolètes de PHP 8.1 dans les composants principaux de la plateforme et assure la compatibilité avec PHP 8.2.</li>
              <li><strong>PHPUnit 10</strong> : cette version résout plusieurs problèmes critiques, améliore la compatibilité et garantit que la structure de test Adobe Commerce s’aligne sur les dernières normes du secteur. Adobe recommande à tous les fournisseurs de Commerce Marketplace et aux clients avec des personnalisations de vérifier que leurs tests d’unité et d’intégration s’exécutent sur PHPUnit 10 au lieu de 9.</li>
            </ul>
            </td>
        </tr>
        <tr>
            <td><strong>Composants</strong></td>
            <td>Les <a href="/help/release/packages/adobe-commerce.md">composants et dépendances</a> tiers suivants ont été mis à jour vers les dernières versions stables afin d’améliorer la stabilité et les performances de la plateforme :
              <ul>
                <li>jquery/validate 1.20.x</li>
                <li>moment.js 2.30.1</li>
                <li>monolog/monolog 3.x</li>
                <li>monolog/Require.js 2.3.7</li>
                <li>TinyMCE 7.x</li>
                <li>wikimedia/less.php 5.x</li>
              </ul>
            </td>
        </tr>
        <tr>
            <td><strong>Rechercher</strong></td>
            <td>Adobe Commerce est désormais optimisé pour OpenSearch 2.x et n’est plus compatible avec Elasticsearch. Tous les modules et classes Elasticsearch 7 et 8 sont désormais obsolètes dans le code base. Adobe recommande vivement de passer à OpenSearch pour les déploiements d’infrastructure cloud et sur site afin d’assurer une prise en charge continue et une compatibilité. Voir <a href="/help/upgrade/prepare/opensearch-migration.md">Migration vers OpenSearch</a>.
              <ul>
                <li>Les options Elasticsearch 7 et Elasticsearch 8 sont désormais étiquetées "(obsolètes)" dans la configuration d’administration.</li>
                <li>Lorsqu’un utilisateur sélectionne Elasticsearch comme moteur de recherche dans la configuration Admin, Commerce affiche une notification indiquant que l’option <em>"Ce moteur de recherche n’est plus prise en charge par Adobe. Nous vous recommandons plutôt d’utiliser OpenSearch comme moteur de recherche."</em></li>
              </ul>
            </td>
        </tr>
    </tbody>
</table>

### Performances

Cette version de comprend les améliorations de performances suivantes :

<table style="table-layout:auto">
    <tbody>
        <tr>
            <td><strong>Indexateurs</strong></td>
            <td>Le <a href="/help/implementation-playbook/best-practices/maintenance/indexer-configuration.md#set-indexers-to-update-on-schedule">mode indexeur</a> par défaut pour tous les indexeurs est désormais [!UICONTROL **Update by Schedule**] lors de l’installation d’une nouvelle version d’Adobe Commerce ou de la mise à niveau à partir d’une version précédente. La nouvelle valeur par défaut garantit que les indexeurs sont dans la configuration recommandée, ce qui améliore les performances du système et réduit les problèmes potentiels.</td>
        </tr>
    </tbody>
</table>

### Qualité

Cette version de comprend les améliorations de qualité suivantes :

<table style="table-layout:auto">
    <tbody>
        <tr>
           <td><strong>Inventaire</strong></td>
           <td>Le système fonctionne désormais sans la dépendance précédemment masquée du catalogue introduite par InventoryIndexer, ce qui garantit que la création du produit, le changement de mode d’affichage, la modification de l’état du stock et d’autres fonctionnalités associées fonctionnent comme prévu. Auparavant, cette dépendance masquée provoquait des incohérences lorsque différentes entités étaient synchronisées et que l’indexeur utilisait différentes entités.</td>
        </tr>
        <tr>
            <td><strong>Commandes</strong></td>
            <td>Pour minimiser la confusion, l’étiquette du bouton [!UICONTROL **Submit Comment**] a été remplacée par [!UICONTROL **Update**] dans la page <a href="https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-processing#notes-for-this-order">détails de la commande</a>.</td>
        </tr>
    </tbody>
</table>

### GraphQL

Cette version de comprend les améliorations GraphQL suivantes :

<table style="table-layout:auto">
    <tbody>
        <tr>
           <td><strong>Améliorations générales</strong></td>
           <td>Cette version de comprend les améliorations générales de l’API GraphQL suivantes :
             <ul>
               <li><!--LYNX-401--><strong>StoreConfig</strong> : ajout des champs <code>grouped_product_image</code> et <code>configurable_product_image</code> au type <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-StoreConfig"><code>StoreConfig</code></a>.</li>
              <li><!--LYNX-387--><strong>CartItemPrice</strong> : les nouveaux champs suivants ont été ajoutés au type <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartItemPrices"><code>CartItemPrices</code></a> pour prendre en charge des calculs précis de prix d’affichage et de réduction :
                <ul>
                  <li><code>original_item_price</code></li>
                  <li><code>original_row_total</code></li>
                  <li><code>row_total_including_catalog_discounts_only</code></li>
                </ul>
              </li>
              <li><!--LYNX-451--><strong>CartPrice</strong> : ajout du champ <code>grand_total_excluding_tax</code> au type <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartPrices"><code>CartPrices</code></a>, ce qui permet d’obtenir des prix inclusifs clairement.</li>
              <li><!--LYNX-542--><strong>mutation updateCartItems</strong> : mise à jour de la mutation <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#mutation-updateCartItems"><code>updateCartItems</code></a> pour renvoyer des réponses de succès avec des détails d’erreur au lieu d’exceptions. Amélioration du mappage des erreurs afin d’améliorer la clarté des notifications utilisateur.</li>
              <li><!--LYNX-522--><strong>requête recaptchaV3Config</strong> : ajout d’un champ <code>theme</code> à la requête <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#query-recaptchaV3Config"><code>recaptchaV3Config</code></a>. Ce champ vous permet de spécifier le nom du thème à utiliser pour le rendu du reCaptcha.</li>
              <li><!--LYNX-540--><strong>ProductInterface</strong> : ajout d’un champ <code>quantity</code> dans <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-ProductInterface"><code>ProductInterface</code></a> pour fournir des détails de niveau stock. Il affiche le stock disponible ou la valeur nulle en fonction des paramètres d’administration.</li>
               <li><!--LYNX-460--><strong>Produits groupés</strong> : affichage correct des prix pour les produits groupés, assurant des informations de prix et de devise précises.</li>
               <li><!--LYNX-547--><strong>Quantity</strong> : messagerie améliorée pour les notifications de quantité insuffisante et indisponible.</li>
               <li><!--LYNX-541--><strong>InsuffisammentStockError type</strong> : ajout d’un nouveau type <code>InsufficientStockError</code> pour gérer les cas où les niveaux de stock sont insuffisants. Ajustement du schéma pour la prise en charge de nouveaux types d’erreur, amélioration des fonctionnalités de création de rapports d’erreur.</li>
               <li><!--LYNX-476--><strong>Montant de l’inventaire</strong> : messagerie d’erreur améliorée pour inclure les quantités d’inventaire disponibles. Fournit aux utilisateurs des informations plus claires sur les niveaux de stock lors des mises à jour de commande.</li>
               <li><!--LYNX-377--><strong>Quantité demandée</strong> : ajout de <code>not_available_message</code> au <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartItemInterface"><code>CartItemInterface</code></a>.</li>
             </ul>
           </td>
        </tr>
        <tr>
           <td><strong>Gestion des clients</strong></td>
           <td>Cette version de comprend les améliorations suivantes apportées à la gestion des clients :
             <ul>
               <li><!--LYNX-391--><strong>generateCustomerToken mutation</strong> : gestion améliorée des erreurs dans la mutation <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#mutation-generateCustomerToken"><code>generateCustomerToken</code></a> afin de fournir des messages spécifiques pour les emails non confirmés. Prend en charge de meilleures conseils aux utilisateurs et une meilleure résolution des erreurs.</li>
               <li><!--LYNX-390--><strong>renendConfirmationEmail mutation</strong> : ajout d’une nouvelle mutation <code>resendConfirmationEmail</code> pour l’envoi de confirmations d’emails.</li>
             </ul>
           </td>
        </tr>
        <tr>
           <td><strong>Gestion des commandes</strong></td>
           <td>Cette version de comprend les améliorations suivantes de la gestion des commandes utilisateur :
             <ul>
              <li><!--LYNX-470--><strong>Date de première commande</strong> : ajout d’un nouveau champ <code>date_of_first_order</code> au type <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrders"><code>CustomerOrders</code></a>.</li>
              <li><!--LYNX-468--><strong>OrderAddress</strong> : extension du type <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-OrderAddress"><code>OrderAddress</code></a> pour inclure des attributs personnalisés, amélioration de la visibilité des détails de la commande. Prend en charge l’affichage d’informations supplémentaires sur les pages de confirmation de commande.</li>
              <li><!--LYNX-458--><strong>requêtes guestOrder et guestOrderByToken</strong> : mise à jour des requêtes <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#query-guestOrder"><code>guestOrder</code></a> et <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#query-guestOrderByToken"><code>guestOrderByToken</code></a> afin d’inclure des attributs d’adresse personnalisés, ce qui permet d’obtenir des informations complètes sur les adresses des nouveaux comptes.</li>
              <li><!--LYNX-450--><strong>Type de CustomerOrder</strong> : ajout du champ<code>is_virtual</code> au type <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrder"><code>CustomerOrder</code></a>, prenant en charge l’identification des produits virtuels. Améliore le traitement des commandes en faisant la distinction entre les produits virtuels et physiques.</li>
              <li><!--LYNX-449--><strong>orderItemPrice</strong> : ajout d’un type <code>OrderItemPrices</code> similaire à <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartItemPrices"><code>CartItemPrices</code></a> à <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-OrderItemInterface"><code>OrderItemInterface</code></a> avec plusieurs nouveaux champs pour le prix.</li>
              <li><!--LYNX-448--><strong>Fusionner les commandes d’invités</strong> : fonctionnalité d’API améliorée pour fusionner les commandes d’invités avec les comptes de clients en fonction de la correspondance des emails. Simplifie la gestion des commandes pour les clients réguliers.</li>
              <li><!-- LYNX-523: --><strong>available_actions field</strong> : extension du type <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrder"><code>CustomerOrder</code></a> pour inclure un champ <code>available_actions</code> pour une meilleure gestion des commandes. Le champ `available_actions` correspond à une énumération qui répertorie les actions possibles qui peuvent être effectuées dans l’ordre.</li>
              <li><!-- LYNX-524 --><strong>Type CustomerOrder</strong> : ajout du champ <code>customer_info</code> au type <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrder"><code>CustomerOrder</code></a>. Ce champ nécessite et <code>OrderCustomerInfo</code>, qui définit les détails sur le nom du client.</li>
              <li><!--LYNX-519--><strong>Codes d’erreur pour l’annulation de commande</strong> : ajout de codes d’erreur détaillés au type <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CancelOrderOutput"><code>CancelOrderOutput</code></a>. Amélioration de la gestion des erreurs et des commentaires des utilisateurs pour les processus d’annulation de commande.</li>
              <li><!--LYNX-515--><strong>Possibilité pour les utilisateurs invités de créer des retours pour les commandes</strong> : correction de la mutation <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#mutation-requestReturn"><code>requestReturn</code></a> pour prendre en charge les retours des commandes invités.</li>
              <li><!--LYNX-505--><strong>confirmCancelOrder mutation</strong> : ajout d’une nouvelle mutation <code>confirmCancelOrder</code> afin de faciliter l’annulation de commande pour les utilisateurs invités.</li>
             </ul>
           </td>
        </tr>
    </tbody>
</table>
