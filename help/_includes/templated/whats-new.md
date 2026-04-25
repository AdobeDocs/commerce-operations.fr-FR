---
source-git-commit: e0905f357c5ab84b30304eeaad00d9ae4ec0c168
workflow-type: tm+mt
source-wordcount: '2620'
ht-degree: 0%

---
# Nouveautés du modèle

## Nouveautés

Cette page contient les modifications apportées au cours des 60 derniers jours. Toutes les mises à jour mineures, telles que la modification de copies, sont exclues de cette liste.

### April 23, 2026

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
      <td><p>Added <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/overview">Overview: Quality Patches Tool (QPT) v1.1.78</a>.</p>
</td>
      <td>
        New topic, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/3f14416d89140ee75ec437a42fbebae804282b72">validation</a></td>
    </tr>
  </tbody>
</table>

### 20 Avril 2026

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
      <td><ul>
  <li>Updated <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/lifecycle-policy">Lifecycle policy</a> with revised end-of-support table, extended support scope, and a new section on additional security fixes provisioning for 2.4.4 and 2.4.5.<br />- Updated <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/versioning-policy">Versioning policy</a> and <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/schedule">Release schedule</a> for isolated security fixes prerequisites and hotfix/individual patch delivery through the Quality Patches Tool; moved isolated security fixes detail into the shared security patch overview include.<br />- Refreshed the 2026 release calendar to match current schedule.</li>
</ul>
</td>
      <td>
        Technical, major update
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/0bc6807d7f4bfd84ac698de81f8cf6f56d849af7">validation</a></td>
    </tr>
  </tbody>
</table>

### April 8, 2026

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
      <td><p>Updated <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements">System requirements</a> with New Relic (APM) supported versions for Commerce on Cloud by release.</p>
</td>
      <td>
        Technical, feedback
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/f82d05cf0f7d2749b313ef5f7e89e1e36248bf30">validation</a></td>
    </tr>
    <tr>
      <td><p>Updated <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/beta">Beta releases</a> with a Category Merchandising (Public Beta) program for SaaS projects, including links to <a href="https://experienceleague.adobe.com/en/docs/commerce/optimizer/merchandising/rules/add">Category merchandising</a> and related merchandising rules topics.</p>
</td>
      <td>
        Mise à jour majeure
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/a9f3594a0ccf4326b0541a4f2b07fdf49cde7148">validation</a></td>
    </tr>
  </tbody>
</table>

### April 3, 2026

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
      <td><p>Added instructions for properly overriding Adobe Commerce’s default L2 cache directories in <code class="language-plaintext highlighter-rouge">env.php</code> to ensure that cache files are stored in the intended location and prevent split cache directories and GlusterFS segmentation faults. See the updated guidance in <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/redis-service-configuration">Best practices for Redis and Valkey services configuration</a>.</p>
</td>
      <td>
        Technical, feedback
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/c3030226d7832b17c82be375431795cba44d72f9">validation</a></td>
    </tr>
  </tbody>
</table>

### April 1, 2026

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
      <td><p>Updated the <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/schedule">2026 Adobe Commerce release calendar</a> with the most current release information.</p>
</td>
      <td>
        Notes de mise à jour
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/3f32d342cbdc3e962fede45de828d836c242bc9a">validation</a></td>
    </tr>
    <tr>
      <td><p>Updated the <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/redis-valkey-service-configuration">best practices for Redis and Valkey configuration</a> and provided related configuration guidance.</p>
</td>
      <td>
        Technical, feedback
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/c96e5b397a2ffee8fadaf638e721799b40d320d3">validation</a></td>
    </tr>
  </tbody>
</table>

### 19 mars 2026

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
      <td><p>Added detailed description of the QPT 1.1.76 fix for <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69319">ACSD-69319: Bundle prices were not indexed properly when child products had stock under custom sources</a>.</p>
</td>
      <td>
        New topic, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/7646d46e37385cf0a2bfbee6de82410ca54629a1">validation</a></td>
    </tr>
  </tbody>
</table>

### March 18, 2026

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
      <td><p>Added detailed description of the QPT 1.1.76 fix for <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69086">ACSD-69086: Installation fails on MariaDB 10.11 due to unsupported database version check</a>.</p>
</td>
      <td>
        New topic, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/016d24d990492d009677c218b253ae88c21634e6">validation</a></td>
    </tr>
  </tbody>
</table>

### 17 mars 2026

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
      <td><p>Added detailed description of the QPT 1.1.76 fix for <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69331">ACSD-69331: Content creators in the media gallery could not create folders with only the <code class="language-plaintext highlighter-rouge">create_folder</code> permission. After the fix, they can create folders as expected</a>.</p>
</td>
      <td>
        New topic, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/40a14de0a67a0c373dcbb497f1893a98322435b3">validation</a></td>
    </tr>
  </tbody>
</table>

### March 13, 2026

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
      <td><p>Updated <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements">System requirements</a>: added Elasticsearch to the technology stack table for v2.4.8.</p>
</td>
      <td>
        Technique
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/a9fe1555d9c9d5b27d8fb7fe23a312e8f124d94c">validation</a></td>
    </tr>
  </tbody>
</table>

### March 12, 2026

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
      <td><p>Added detailed description of the QPT 1.1.77 fix for <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68759">ACSD-68759: Customer account creation error with Arabic locale when Date of Birth is shown</a>.</p>
</td>
      <td>
        New topic, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/d3c2d0ebea67fb376a43a67995f3ce278ceac3ee">validation</a></td>
    </tr>
    <tr>
      <td><p>Added detailed description of the QPT 1.1.77 fix for <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69237">ACSD-69237: Sales__async_insert cron jobs process only 100 entries per run</a>.</p>
</td>
      <td>
        New topic, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/0842ba414e45857e36d61c589687718435739efa">validation</a></td>
    </tr>
    <tr>
      <td><p>Added detailed description of the QPT 1.1.76 fix for <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69203">ACSD-69203: Products List widget returns incorrect results when multiple categories are used in the category condition</a>.</p>
</td>
      <td>
        New topic, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/1c435f9cef082a01dbcc160443291e6b7655f009">validation</a></td>
    </tr>
  </tbody>
</table>

### March 11, 2026

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
      <td><p>Added detailed description of the QPT 1.1.76 fix for <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69115">ACSD-69115: Shopping cart errors not displayed to admin users for customers assigned to non‑default websites</a>.</p>
</td>
      <td>
        New topic, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/9441537126c958bfcc6485e627cbad7efd16128e">validation</a></td>
    </tr>
    <tr>
      <td><p>Added detailed description of the QPT 1.1.77 fix for <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69016">ACSD-69016: Special price isn't applied on websites with different time zones</a>.</p>
</td>
      <td>
        New topic, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/b9788fef5bab2eb33334ef9f62bb52fa7b9f243e">validation</a></td>
    </tr>
    <tr>
      <td><p>Updated <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements">System requirements</a>: MariaDB 10.6 is still supported for 2.4.5-p16.</p>
</td>
      <td>
        Technique
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/pull/173">demande de tirage</a></td>
    </tr>
  </tbody>
</table>

### March 10, 2026

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
      <td><p>Added detailed description of the QPT 1.1.77 fix for <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69351">ACSD-69351: Gift card balances and expiration dates displayed across incorrect websites</a>.</p>
</td>
      <td>
        New topic, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/092972cf6a0689b886e1729bb195bfc9cea7cb07">validation</a></td>
    </tr>
    <tr>
      <td><p>Added detailed description of the QPT 1.1.76 fix for <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-67370">ACSD-67370: Incorrect prices were shown for Bundle products on PDP/PLP and the cart page for multi-currency stores</a>.</p>
</td>
      <td>
        New topic, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/6be4fb9868ce348b9d7ab911b501807c2e9603a5">validation</a></td>
    </tr>
    <tr>
      <td><p>Updated security patch release notes (2.4.4, 2.4.5, 2.4.6, 2.4.7) to reference <a href="https://helpx.adobe.com/security/products/magento/apsb26-05.html">Adobe Security Bulletin APSB26-05</a>: <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-4-patches">2.4.4 patches</a>, <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-5-patches">2.4.5 patches</a>, <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-6-patches">2.4.6 patches</a>, and <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-7-patches">2.4.7 patches</a>.</p>
</td>
      <td>
        Technique
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/aca7de52b79acd844950e792430937795bd23eba">validation</a></td>
    </tr>
    <tr>
      <td><p>Updated <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/uct">Upgrade Compatibility Tool CLI reference</a> to version 3.0.26: revised command examples and available-version lists for <code class="language-plaintext highlighter-rouge">dbschema:diff</code> and <code class="language-plaintext highlighter-rouge">upgrade:check</code>.</p>
</td>
      <td>
        Technique
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/4fa8705ac5d11e6baf2e9fe250e4fc87a1327116">validation</a></td>
    </tr>
    <tr>
      <td><p>Version du 26 mars :<br />- Ajout de points forts aux <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/adobe-commerce/2-4-9">notes de mise à jour de la version 2.4.9-bêta1 d’Adobe Commerce</a> pour résumer les mises à jour importantes incluses dans la version.<br />- Ajout d’un avis de fin de prise en charge (EOS) de MySQL 8.0 aux notes de mise à jour des correctifs de sécurité pour <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-5-patches">2.4.5</a>, <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-6-patches">2.4.6</a> et <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-7-patches">2.4.7</a>, conseillant aux clients sur site de migrer vers une version compatible de MariaDB avant le 30 avril 2026.<br />- Documentation de <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-4-patches#p17">2.4.4-p17</a> <br />bin/magento (CLI sur site Adobe Commerce 2.4.9-beta1)<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/commerce-on-premises-beta"> Référence CLI documentant toutes les commandes, arguments et options disponibles pour la CLI sur site 2.4.9-beta1.</a>- Notes de mise à jour du correctif de sécurité avec de nouvelles versions de correctifs et mises en évidence : <br />2.4.5-p16<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-5-patches">, </a>2.4.6-p14<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-6-patches">, </a>2.4.7-p9<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-7-patches"> et </a>2.4.8-p4<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-8-patches">- Mise à jour de la configuration requise </a> pour Adobe Commerce 2.4.9 beta1 (en remplaçant les colonnes alpha avec la version 2.4.9-bêta1), actualisation des versions dépendantes (PHP 8.5/8.4, ActiveMQ Artemis, services AWS) et ajout de correctifs versions 2.4.8-p4, 2.4.7-p9, 2.4.6-p14, 2.4.5-p16 et 2.4.4-p17.<br />- Mise à jour des <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/adobe-commerce/2-4-9">notes de mise à jour d’Adobe Commerce 2.4.9-bêta1 <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements"> et <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/magento-open-source/2-4-9">notes de mise à jour de Magento Open Source 2.4.9-bêta1 avec du contenu à problèmes résolus pour beta1.</a>- Mise à jour des <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/adobe-commerce/2-4-9">notes de mise à jour d’Adobe Commerce 2.4.9-beta1<br /> et des <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/magento-open-source/2-4-9">notes de mise à jour de Magento Open Source 2.4.9-beta1</a> </a> <br /> </a> </a> avec les points forts de la version bêta1, y compris les mises à jour du framework (OpenSearch 3.x, Valkey 8.x, ActiveMQ, Composer, PHP 8.5), les améliorations de la sécurité et de l’ACL, l’expédition (USPS, DHL), les améliorations de Braintree et d’autres modifications de la version 2.4.9-beta1.</p>
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

### 9 mars 2026

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

### 6 mars 2026

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
      <td><p>Mise à jour de <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/beta">versions de Beta</a> avec deux nouveaux programmes Beta publics : Règles de marchandisage globales et par vue de catalogue, et Recommandations de produits globales et par vue de catalogue.</p>
</td>
      <td>
        Mise à jour majeure
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/5533640a3f0f648162ebfc3609eb4e35fd32f6d7">validation</a></td>
    </tr>
  </tbody>
</table>

### 5 mars 2026

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

### 3 mars 2026

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

### 2 mars 2026

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

### 27 Février 2026

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

### 26 Février 2026

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
