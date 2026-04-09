---
source-git-commit: d4759f2394d55d115e5da80c271152ee621a2683
workflow-type: tm+mt
source-wordcount: '1639'
ht-degree: 2%

---
# Nouveautés du modèle

## Nouveautés

Cette page contient les modifications apportées au cours des 60 derniers jours. Toutes les mises à jour mineures, telles que la modification de copies, sont exclues de cette liste.

### samedi 3 avril 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Description</th>
      <th>Type</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Ajout d’instructions pour remplacer correctement les répertoires de cache L2 par défaut d’Adobe Commerce dans <code class="language-plaintext highlighter-rouge">env.php</code> afin de garantir que les fichiers cache sont stockés à l’emplacement prévu et d’éviter les erreurs de segmentation GlusterFS et les répertoires de cache partagés. Consultez les conseils mis à jour dans <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/redis-service-configuration">Bonnes pratiques pour la configuration des services Redis et Valkey</a>.</p>
</td>
      <td>
        Technique, commentaires
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/c3030226d7832b17c82be375431795cba44d72f9">validation</a></td>
    </tr>
  </tbody>
</table>

### jeudi 1 avril 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Description</th>
      <th>Type</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Mise à jour du calendrier de mise à jour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/schedule">2026 d’Adobe Commerce</a> avec les informations de mise à jour les plus récentes.</p>
</td>
      <td>
        Notes de mise à jour
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/3f32d342cbdc3e962fede45de828d836c242bc9a">validation</a></td>
    </tr>
    <tr>
      <td><p>Mise à jour des <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/redis-valkey-service-configuration">bonnes pratiques pour la configuration de Redis et Valkey</a> et conseils de configuration associés.</p>
</td>
      <td>
        Technique, commentaires
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/c96e5b397a2ffee8fadaf638e721799b40d320d3">validation</a></td>
    </tr>
  </tbody>
</table>

### vendredi 19 mars 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Description</th>
      <th>Type</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.76 pour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69319">ACSD-69319 : les prix des lots n’étaient pas correctement indexés lorsque les produits enfants étaient en stock sous des sources personnalisées</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/7646d46e37385cf0a2bfbee6de82410ca54629a1">validation</a></td>
    </tr>
  </tbody>
</table>

### jeudi 18 mars 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Description</th>
      <th>Type</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.76 pour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69086">ACSD-69086 : l’installation échoue sur MariaDB 10.11 en raison de la vérification de la version de la base de données non prise en charge</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/016d24d990492d009677c218b253ae88c21634e6">validation</a></td>
    </tr>
  </tbody>
</table>

### mercredi 17 mars 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Description</th>
      <th>Type</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.76 pour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69331">ACSD-69331 : les créateurs de contenu dans la galerie de médias ne pouvaient pas créer de dossiers avec uniquement l’autorisation <code class="language-plaintext highlighter-rouge">create_folder</code> . Après le correctif, ils peuvent créer des dossiers comme prévu</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/40a14de0a67a0c373dcbb497f1893a98322435b3">validation</a></td>
    </tr>
  </tbody>
</table>

### samedi 13 mars 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Description</th>
      <th>Type</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Mise à jour de la <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements">Configuration requise </a> : ajout d’Elasticsearch au tableau de pile technologique pour la version 2.4.8.</p>
</td>
      <td>
        Technique
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/a9fe1555d9c9d5b27d8fb7fe23a312e8f124d94c">validation</a></td>
    </tr>
  </tbody>
</table>

### vendredi 12 mars 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Description</th>
      <th>Type</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.77 pour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68759">ACSD-68759 : erreur de création de compte client avec des paramètres régionaux arabes lorsque la date de naissance s’affiche</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/d3c2d0ebea67fb376a43a67995f3ce278ceac3ee">validation</a></td>
    </tr>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.77 pour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69237">ACSD-69237 : les tâches cron Sales__async_insert ne traitent que 100 entrées par exécution</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/0842ba414e45857e36d61c589687718435739efa">validation</a></td>
    </tr>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.76 pour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69203">ACSD-69203 : le widget Liste de produits renvoie des résultats incorrects lorsque plusieurs catégories sont utilisées dans la condition de catégorie</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/1c435f9cef082a01dbcc160443291e6b7655f009">validation</a></td>
    </tr>
  </tbody>
</table>

### jeudi 11 mars 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Description</th>
      <th>Type</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.76 pour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69115">ACSD-69115 : erreurs de panier non affichées pour les utilisateurs administrateurs pour les clients affectés à des sites web autres que ceux par défaut</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/9441537126c958bfcc6485e627cbad7efd16128e">validation</a></td>
    </tr>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.77 pour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69016">ACSD-69016 : Le prix spécial n’est pas appliqué aux sites web avec des fuseaux horaires différents</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/b9788fef5bab2eb33334ef9f62bb52fa7b9f243e">validation</a></td>
    </tr>
    <tr>
      <td><p>Mise à jour de la <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements">Configuration requise </a> : MariaDB 10.6 est toujours pris en charge dans la version 2.4.5-p16.</p>
</td>
      <td>
        Technique
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/pull/173">demande de tirage</a></td>
    </tr>
  </tbody>
</table>

### mercredi 10 mars 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Description</th>
      <th>Type</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.77 pour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69351">ACSD-69351 : soldes de cartes-cadeaux et dates d’expiration affichés sur des sites web incorrects</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/092972cf6a0689b886e1729bb195bfc9cea7cb07">validation</a></td>
    </tr>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.76 pour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-67370">ACSD-67370 : des prix incorrects ont été affichés pour les produits groupés sur PDP/PLP et la page du panier pour les magasins multidevises</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/6be4fb9868ce348b9d7ab911b501807c2e9603a5">validation</a></td>
    </tr>
    <tr>
      <td><p>Mise à jour des notes de mise à jour des correctifs de sécurité (2.4.4, 2.4.5, 2.4.6 et 2.4.7) pour faire référence au <a href="https://helpx.adobe.com/security/products/magento/apsb26-05.html">bulletin de sécurité Adobe APSB26-05</a> : <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-4-patches">2.4.4 correctifs</a>, <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-5-patches">2.4.5 correctifs</a>, <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-6-patches">2.4.6 correctifs</a> et <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-7-patches">2.4.7 correctifs</a>.</p>
</td>
      <td>
        Technique
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/aca7de52b79acd844950e792430937795bd23eba">validation</a></td>
    </tr>
    <tr>
      <td><p>Mise à jour de la <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/uct">référence de l’interface de ligne de commande de l’outil de compatibilité de mise à niveau</a> vers la version 3.0.26 : exemples de commande révisés et listes de versions disponibles pour <code class="language-plaintext highlighter-rouge">dbschema:diff</code> et <code class="language-plaintext highlighter-rouge">upgrade:check</code>.</p>
</td>
      <td>
        Technique
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/4fa8705ac5d11e6baf2e9fe250e4fc87a1327116">validation</a></td>
    </tr>
    <tr>
      <td><p>Version du 26 mars :<br />- Ajout de points forts aux <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/adobe-commerce/2-4-9">notes de mise à jour d’Adobe Commerce 2.4.9-bêta1</a> pour résumer les mises à jour importantes incluses dans la version.<br />- Ajout d’un avis de fin de prise en charge (EOS) de MySQL 8.0 aux notes de mise à jour des correctifs de sécurité pour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-5-patches">2.4.5</a>, <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-6-patches">2.4.6</a> et <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-7-patches">2.4.7</a>, conseillant aux clients sur site de migrer vers une version compatible de MariaDB avant le 30 avril 2026.<br />- Version du correctif de sécurité <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-4-patches#p17">2.4.4-p17</a> documentée.<br />- Ajout d’une référence de l’interface de ligne de commande <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/commerce-on-premises-beta">bin/magento (Adobe Commerce On-Premise 2.4.9-Beta1)</a> documentant toutes les commandes, arguments et options disponibles pour l’interface de ligne de commande 2.4.9-Beta1 On-Premise.<br />- Mise à jour des notes de mise à jour des correctifs de sécurité avec de nouvelles versions de correctifs et points forts : <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-5-patches">2.4.5-p16</a>, <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-6-patches">2.4.6-p14</a>, <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-7-patches">2.4.7-p9</a> et <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-8-patches">2.4.8-p4</a>.<br />- Mise à jour de la <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements">Configuration requise</a> pour Adobe Commerce 2.4.9 bêta1 (remplacement des colonnes alpha par 2.4.9 bêta1), actualisation des versions dépendantes (PHP 8.5/8.4, ActiveMQ Artemis, services AWS) et ajout de correctifs versions 2.4.8-p4, 2.4.7-p9, 2.4.6-p14, 2.4.5-p16 et 2.4.4-p17.<br />- Mise à jour des <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/adobe-commerce/2-4-9">notes de mise à jour de la version 2.4.9-bêta1 d’Adobe Commerce</a> et des <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/magento-open-source/2-4-9">notes de mise à jour de la version 2.4.9-bêta1 de Magento Open Source</a> avec du contenu corrigé pour la version bêta1.<br />- Mise à jour des <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/adobe-commerce/2-4-9">notes de mise à jour de la version 2.4.9-bêta1 d’Adobe Commerce</a> et des <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/magento-open-source/2-4-9">notes de mise à jour de la version 2.4.9-bêta1 de Magento Open Source</a> avec les points forts de la version bêta1, y compris les mises à jour du framework (OpenSearch 3.x, Valkey 8.x, ActiveMQ, Composer, PHP 8.5), les améliorations de la sécurité et des listes de contrôle d’accès, l’expédition (USPS, DHL), les améliorations de Braintree et d’autres modifications de la version 2.4.9-bêta1.</p>
</td>
      <td>
        Mise à jour majeure
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/e4cec53679d038d2324f89478c5495de98a29fb3">validation</a></td>
    </tr>
    <tr>
      <td><p>Mise à jour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/versions">versions publiées</a> après la version de mars 2026.</p>
</td>
      <td>
        Technique
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/9bc44a3ec7199ccb08927caf3d7904611cc7b167">validation</a></td>
    </tr>
  </tbody>
</table>

### mardi 9 mars 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Description</th>
      <th>Type</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.76 pour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-67091">ACSD-67091 : le nettoyage de l’index de produit des règles de catalogue échoue en raison de la taille maximale du jeu d’écriture lors de suppressions volumineuses</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/520273fb4c1b30e3f8b346f7079062cf9c8b37f3">validation</a></td>
    </tr>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.76 pour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69261">ACSD-69261 : coupon de panier à usage unique réutilisé en raison d’une gestion incorrecte de times_used dans les flux de facturation et d’annulation partiels</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/536364742e2102f8386b3e13503cf2965821f04b">validation</a></td>
    </tr>
  </tbody>
</table>

### samedi 6 mars 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Description</th>
      <th>Type</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.76 pour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69541">ACSD-69541 : la réduction de la quantité d’un produit dans l’administration à une quantité inférieure à celle qui existe déjà dans un panier a rendu impossible la modification de la quantité de produit dans ce panier via GraphQL</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/b2b801b88aee7fc6c275be3fb32a2e75bbe6f20d">validation</a></td>
    </tr>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.76 pour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69308">ACSD-69308 : les règles de prix de catalogue ne s’appliquaient pas lorsque <code class="language-plaintext highlighter-rouge">special_price</code> était défini uniquement au niveau du site web (et non au niveau de « Toutes les vues de la boutique »). Après la correction, les règles de prix de catalogue s’appliquent correctement en vérifiant d’abord le magasin par défaut du site web</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/db07a5d6f991ff36536a4365ee88fa25062dbe43">validation</a></td>
    </tr>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.77 pour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69020">ACSD-69020 : les produits configurables apparaissent dans les carrousels de Page Builder lorsque les produits enfants correspondent aux filtres</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/5ce526100a22243b91f75b8a52690e529b64b152">validation</a></td>
    </tr>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.76 pour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69325">ACSD-69325 : la modification du boîtier de SKU a entraîné la rupture de stock du produit sur le storefront</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/bceda2e729082e0dc81f7eb81838ca5c5049342d">validation</a></td>
    </tr>
    <tr>
      <td><p>Mise à jour de <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/beta">versions de </a> avec deux nouveaux programmes Beta publics : Règles de marchandisage globales et par vue de catalogue, et Recommandations de produits globales et par vue de catalogue.</p>
</td>
      <td>
        Mise à jour majeure
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/5533640a3f0f648162ebfc3609eb4e35fd32f6d7">validation</a></td>
    </tr>
  </tbody>
</table>

### vendredi 5 mars 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Description</th>
      <th>Type</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.76 pour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69129">ACSD-69129 : la mise à jour du prix du niveau de l’API REST échoue après la suppression du site web de base par défaut et l’utilisation du site web secondaire par défaut</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/06d33e9ed08e079365ac6ae6087e4bdf30bbf45e">validation</a></td>
    </tr>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.76 pour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-68410">ACSD-68410 : le passage en caisse de devis négociable inclut des articles de panier non souhaités</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/123a0b7c2335fd27d6c8fabbb8a6520af2ac0c76">validation</a></td>
    </tr>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.77 pour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68892">ACSD-68892 : comportement de mise en cache rapide incohérent pour les pages pouvant être mises en cache</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/d727bea23f1a60b597bb795948eb924e76e869a5">validation</a></td>
    </tr>
  </tbody>
</table>

### mercredi 3 mars 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Description</th>
      <th>Type</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.77 pour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-63687">ACSD-63687 : des prix incorrects s’affichent en raison de problèmes de nettoyage du cache Redis</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/e8a9b37a61119e7604461c83f135a282b15a93ef">validation</a></td>
    </tr>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.77 pour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68664">ACSD-68664 : l’aperçu de la mise à jour planifiée comporte des erreurs sur les domaines de magasin personnalisés</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/d0a57180c224fc7d1eba3e4e5b87a87ddb11d88c">validation</a></td>
    </tr>
  </tbody>
</table>

### mardi 2 mars 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Description</th>
      <th>Type</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.76 pour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69333">ACSD-69333 : les modifications de SKU sont autorisées pour les produits avec une mise à jour planifiée active</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/b9ea11e00223a3c4a4cd5be1eca1a3175074124c">validation</a></td>
    </tr>
  </tbody>
</table>

### samedi 27 février 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Description</th>
      <th>Type</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Ajout d'une description détaillée du correctif QPT 1.1.77 pour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69311">ACSD-69311 : calcul incorrect de la taxe dans les avoirs après remboursement partiel des factures</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/c6d81e7aeb4e2b4d2d5a140e9bf7b8c8ba5f5deb">validation</a></td>
    </tr>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.77 pour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69494">ACSD-69494 : les demandes de remboursement asynchrones avec is_online ne déclenchent pas de remboursements en ligne</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/29a5f90122336bde78ed00e778b43b7c56549eef">validation</a></td>
    </tr>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.77 pour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68537">ACSD-68537 : les performances de passage en caisse se dégradent avec de nombreux segments de clients</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/70729169b3588f5061f98b555577c2b62215e6f0">validation</a></td>
    </tr>
  </tbody>
</table>

### vendredi 26 février 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Description</th>
      <th>Type</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.77 pour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68341">ACSD-68341 : plusieurs mises à jour des cookies X-Magento-Vary se produisent au chargement du PDP</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/88ae7472fc5ec3c7b422a9a1d568204c42e017bb">validation</a></td>
    </tr>
  </tbody>
</table>

### samedi 20 février 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Description</th>
      <th>Type</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Ajout de la <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/overview">Présentation : Outil de correctifs de qualité (QPT) version 1.1.77</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/09c026905c464ec0e41d12db8a5822b3e3b57064">validation</a></td>
    </tr>
  </tbody>
</table>

### 27 février 2018

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Description</th>
      <th>Type</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.75 pour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-75/acsd-68359">ACSD-68359 : corrige l’erreur 414 lors de la sélection de Choisir en magasin avec de grands paniers</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/33348fa893265e14d9e2cec9f30ffd6cf42b0878">validation</a></td>
    </tr>
  </tbody>
</table>

### samedi 13 février 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Description</th>
      <th>Type</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.75 pour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-75/acsd-68517">ACSD-68517 : corrige une erreur de nouvel envoi de formulaire sur les pages Catalogue et Recherche catalogue</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/3b3f33eda0f87829f97a875ec9805c6e257d9b09">validation</a></td>
    </tr>
  </tbody>
</table>

### vendredi 12 février 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Description</th>
      <th>Type</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Mise à jour du <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/schedule">calendrier de publication des correctifs</a> afin de clarifier les directives et le calendrier de publication actuels.</p>
</td>
      <td>
        Technique, commentaires
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/8ee6404271170b19ff27a3ab64711061505494b3">validation</a></td>
    </tr>
    <tr>
      <td><p>Ajout de la <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/overview">Présentation : Outil de correctifs de qualité (QPT) version 1.1.76</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/6e7e67291cabb1a35b132e3ae2d407e2ffefe7f1">validation</a></td>
    </tr>
  </tbody>
</table>

### jeudi 11 février 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Description</th>
      <th>Type</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.75 pour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-75/acsd-68573">ACSD-68573 : les autorisations de catégorie n’ont pas été correctement appliquées aux éléments de la liste de souhaits du client. Après le correctif, les éléments de liste de souhaits sont correctement affichés et paginés sur le web et dans </a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/19e5faea683395375efefe6fc57e0897392ef354">validation</a></td>
    </tr>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.75 pour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-75/acsd-68793">ACSD-68793 : les produits valides ont été incorrectement rejetés lors de leur affectation à un catalogue partagé</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/bbd18afc87f16777b6218cdcf7ec0798c1640083">validation</a></td>
    </tr>
  </tbody>
</table>

### mercredi 10 février 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Description</th>
      <th>Type</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.75 pour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-75/acsd-68925">ACSD-68925 : les réponses des requêtes GraphQL sont désormais alignées sur les spécifications GraphQL via HTTP. Un code de réponse 4XX est renvoyé lorsque la requête ne peut pas être analysée, n’est pas autorisée ou rencontre un problème général. Si la requête est analysée</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/210a5038743bec986807d7dff5db31d74670461e">validation</a></td>
    </tr>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.75 pour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-75/acsd-68289">ACSD-68289 : la recherche en texte intégral renvoie désormais les produits correspondants si la condition de correspondance minimale est remplie collectivement pour tous les champs pouvant faire l’objet d’une recherche, plutôt que d’exiger que la condition soit remplie par un seul champ</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/d26429ef5b2dee650e14914d3b9678895a23f73e">validation</a></td>
    </tr>
  </tbody>
</table>
