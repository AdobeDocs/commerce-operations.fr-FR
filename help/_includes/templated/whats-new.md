---
source-git-commit: 076f76112159204c0f23d3ddfbb606e274c406eb
workflow-type: tm+mt
source-wordcount: '1538'
ht-degree: 1%
---
# Nouveautés du modèle

## Nouveautés

Cette page contient les modifications apportées au cours des 60 derniers jours. Toutes les mises à jour mineures, telles que la modification de copies, sont exclues de cette liste.

### 18 septembre 2026

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
      <td><p>Ajout de la section <a href="https://experienceleague.adobe.com/fr/docs/commerce-operations/release/planning/monthly-isolated-security-patches">Politique mensuelle d’application de correctifs de sécurité isolés</a>, expliquant comment Adobe Commerce fournit des correctifs CVE ciblés et isolés le mardi des correctifs entre les versions complètes des correctifs de sécurité, ainsi que la manière de les appliquer et de les vérifier.</p>
</td>
      <td>
        Nouvelle rubrique
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/681f7f0589aed8787aaf165d36ac00f670d751ce">validation</a></td>
    </tr>
  </tbody>
</table>

### 15 septembre 2026

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
      <td><p>Correction du guide <a href="https://experienceleague.adobe.com/fr/docs/commerce-operations/implementation-playbook/best-practices/planning/redis-valkey-service-configuration">Configuration du service Redis/Valkey</a> afin de clarifier le fait que les variables de déploiement <code>VALKEY_BACKEND</code> et <code>REDIS_BACKEND</code> ne déterminent pas le service de cache qu’Adobe Commerce utilise réellement et que <code>VALKEY_USE_SLAVE_CONNECTION</code>/<code>REDIS_USE_SLAVE_CONNECTION</code> doit correspondre au service réellement disponible dans l’environnement.</p>
</td>
      <td>
        Technique
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/49781ad38a266fffa1be080b5a093327a28cf6a6">validation</a></td>
    </tr>
  </tbody>
</table>

### 8 septembre 2026

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
      <td><p>L’automatisation des correctifs d’Adobe Commerce est désormais disponible. Voir la <a href="https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/caps-tool/intro">documentation</a> pour en savoir plus.</p>
</td>
      <td>
        Mise à jour majeure, nouvelle rubrique
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/a88bfea449616c0b79c5bd3380bec74c68687052">validation</a></td>
    </tr>
  </tbody>
</table>

### 26 Août 2026

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
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.82 pour <a href="https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4840">ACP2E-4840 : la requête de produits GraphQL renvoie une quantité nulle pour les produits en stock sur les stocks d’inventaire personnalisés</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/edfc38af34925749c5acb36d2c0bcfc5d16a577a">validation</a></td>
    </tr>
  </tbody>
</table>

### 19 Août 2026

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
      <td><p>Mise à jour de la documentation sur la mise en cache de Commerce avec des conseils plus clairs sur site par rapport au cloud et de nouveaux conseils de migration pour passer à Valkey avec le cache Symfony L2 :<br />- Mise à jour <a href="https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/cache/caching-overview">Présentation de la mise en cache et options de configuration</a>.<br />- Mise à jour <a href="https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/cache/cache-types">Configuration des fronts et des types de cache</a>.<br />- Mise à jour <a href="https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/cache/cache-options">Options de serveur principal et référence de stockage du cache</a>.<br />- Mise à jour de la configuration du cache <a href="https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/cache/level-two-cache"> L2 pour l’optimisation des performances</a> avec des conseils pour migrer de <code>RemoteSynchronizedCache</code> vers le cache Symfony L2.<br />- Mise à jour <a href="https://experienceleague.adobe.com/fr/docs/commerce-operations/implementation-playbook/best-practices/planning/redis-valkey-service-configuration">Bonnes pratiques pour la configuration de Valkey et Redis Service</a> avec des étapes de migration spécifiques au cloud vers le cache L2.</p>
</td>
      <td>
        Mise à jour majeure
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/3a840b544de95a4bb17ef49d0325b16d461aecaa">validation</a></td>
    </tr>
  </tbody>
</table>

### 14 Août 2026

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
      <td><p>Mise à jour des étapes permettant aux clients de vérifier la version de leurs dépendances de service dans l’interface utilisateur de Cloud et mise à jour du lien vers le guide expliquant comment les clients peuvent générer un rapport de compatibilité de mise à niveau pour leur magasin, dans <a href="https://experienceleague.adobe.com/fr/docs/commerce-operations/release/planning/security-enforcement-policy#action-1-verify-and-upgrade-third-party-software-dependencies">Vérification et mise à niveau des dépendances de logiciels tiers</a>.</p>
</td>
      <td>
        Technique
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/54ac98c35e1f161f390587601484db4e3294b6af">validation</a></td>
    </tr>
  </tbody>
</table>

### 13 Août 2026

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
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.82 pour <a href="https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4194">ACP2E-4194 : les requêtes GraphQL avec des noms de filtre inconnus provoquent des journaux d’exceptions PHP</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/d4202395c5b7bb5e8c4a95d8fb353ec0fc523fcb">validation</a></td>
    </tr>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.82 pour <a href="https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4695">ACP2E-4695 : l’indexeur de règles de catalogue manque de mémoire en raison d’une utilisation excessive de la mémoire</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/dc891435d573c4c333e58e25b2dbe003ffa08f27">validation</a></td>
    </tr>
    <tr>
      <td><p>Correction des fautes de frappe dans les dates EOS pour les versions 2.4.5 et 2.4.6 d’Adobe Commerce.</p>
</td>
      <td>
        Technique
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/8de65d309dcd4158627910ce5c0b87966db5c948">validation</a></td>
    </tr>
  </tbody>
</table>

### 12 Août 2026

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
      <td><p>Suppression de PHP 8.4 en tant que version PHP prise en charge dans les notes de mise à jour <a href="https://experienceleague.adobe.com/fr/docs/commerce-operations/release/notes/adobe-commerce/2-4-9#php-and-composer">2.4.9</a>, car il n'est pas recommandé pour l'utilisation en production et est uniquement présent pour la compatibilité de mise à niveau.</p>
</td>
      <td>
        Notes de mise à jour, techniques
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/603bb70012a2f92ceeaad644d5252c4677a1a47c">validation</a></td>
    </tr>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.82 pour <a href="https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4894">ACP2E-4894 : de nouvelles commandes apparaissent dans la grille Commandes d’administration avec un délai lorsque l’indexation asynchrone est activée</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/ad40d94c1618f7e423fd6a773185b8fba48c2c72">validation</a></td>
    </tr>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.82 pour <a href="https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4698">ACP2E-4698 : la modification en ligne de texte Page Builder enregistre les URL de médias absolus au lieu de la directive portable</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/68e5e99ac0717b0e358acd6acf9934044a917a82">validation</a></td>
    </tr>
    <tr>
      <td><p>Correction et achèvement des dates de mise en service de la fin de la prise en charge, de la prise en charge étendue et des correctifs de sécurité supplémentaires pour plusieurs lignes de version d’Adobe Commerce sur la page <a href="https://experienceleague.adobe.com/fr/docs/commerce-operations/release/versions">Versions publiées</a>.</p>
</td>
      <td>
        Technique
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/fc5a7f7a466e6419a3e712bcbec4224f98f8c480">validation</a></td>
    </tr>
  </tbody>
</table>

### mercredi 11 août 2026

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
      <td><p>Mise à jour de la <a href="https://experienceleague.adobe.com/fr/docs/commerce-operations/installation-guide/system-requirements">Configuration requise</a> pour ajouter RabbitMQ 3.13 en tant que version prise en charge pour Adobe Commerce 2.4.4-p18 (la plus récente), résolvant un bloqueur pour le chemin de mise à niveau du système d’exploitation Debian.</p>
</td>
      <td>
        Technique
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/046d641dc45b269c6495bef0c06c53bdc500227b">validation</a></td>
    </tr>
  </tbody>
</table>

### 10 Août 2026

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
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.82 pour <a href="https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4797">ACP2E-4797 : l’éditeur WYSIWYG d’administration et le Page Builder bloquent les caractères Unicode à 4 octets lorsque l’utf8mb4 est pris en charge</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/c97bb9c77eb0ec4bbc92d042cfa9fd440e970ca7">validation</a></td>
    </tr>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.82 pour <a href="https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4682">ACP2E-4682 : les pages de storefront qui vérifient la citation est actif créent des enregistrements de citation vides</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/ceac870e3ccb9eeee64e3b574aaccd33c6ab69d0">validation</a></td>
    </tr>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.82 pour <a href="https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4799">ACP2E-4799 : la requête GraphQL requisition_lists renvoie un total_count incorrect avec pagination</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/19f854db1a0ff78d0a6dca070b4b6db09d3de83e">validation</a></td>
    </tr>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.82 pour <a href="https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4870">ACP2E-4870 : les e-mails d’alertes de produit ignorent les paramètres d’e-mail de vue de magasin</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/907df07e641ab7124353f89ca799f92d097aa54f">validation</a></td>
    </tr>
    <tr>
      <td><p>Mise à jour du tableau <a href="https://experienceleague.adobe.com/fr/docs/commerce-operations/release/product-availability">Disponibilité du produit</a> avec la prise en charge d’Adobe Commerce 2.4.9 et suppression de l’entrée Page Builder, qui fait partie du produit principal depuis la version 2.4.3.</p>
</td>
      <td>
        Mise à jour majeure
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/a5120adab9f624677447889722359951e775c3f3">validation</a></td>
    </tr>
  </tbody>
</table>

### 9 Août 2026

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
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.82 pour <a href="https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4593">ACP2E-4593 : page CMS de restriction de site web incorrecte diffusée sur le site web secondaire dans les storefronts multi-sites</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/86c85db0098192092241b680d38b882f1a52b578">validation</a></td>
    </tr>
  </tbody>
</table>

### 6 Août 2026

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
      <td><p>Correction de la matrice de prise en charge des versions de l’extension B2B dans <a href="https://experienceleague.adobe.com/fr/docs/commerce-operations/release/product-availability">Disponibilité du produit</a> pour Adobe Commerce 2.4.6, 2.4.7 et 2.4.8.</p>
</td>
      <td>
        Technique
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/50fb71aa968abf1302e86ffeb3d3b3a66b3c33d5">validation</a></td>
    </tr>
  </tbody>
</table>

### 31 juillet 2026

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
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.82 pour <a href="https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4547">ACP2E-4547 : l’administrateur ne peut pas ajouter un produit de catalogue par défaut à un devis s’il n’est pas affecté au catalogue partagé de l’utilisateur</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/6d0313c01e979d3d4bd3e781e2f0e9c336bbd8c5">validation</a></td>
    </tr>
  </tbody>
</table>

### 30 Juillet 2026

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
      <td><p>Ajout de la section <a href="https://experienceleague.adobe.com/fr/docs/commerce-operations/release/planning/security-enforcement-policy">Politique de sécurité : actions requises et échéances</a> pour que les clients Adobe Commerce on Cloud puissent expliquer les exigences, le calendrier et les instructions de mise à niveau d’Adobe Commerce on Cloud avec des déploiements exécutant des versions non prises en charge ou des dépendances logicielles tierces.</p>
</td>
      <td>
        Nouvelle rubrique
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/b7649aae1f8cab020c1081db2b2363bca22adfed">validation</a></td>
    </tr>
  </tbody>
</table>

### 28 juillet 2026

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
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.82 pour <a href="https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4805">ACP2E-4805 : les demandes de passage en caisse ralentissent pour les produits configurables lorsque le premier enfant vendable apparaît plus loin dans la liste</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/1b5fb4826f6599d7b7609dedfeb545f29454ba4d">validation</a></td>
    </tr>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.82 pour <a href="https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4748">ACP2E-4748 : l’expiration des points de récompense s’exécute lentement sur les magasins avec un historique de points de récompense important</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/30fe149f9743ceca7f40374246b4fc9b9503c590">validation</a></td>
    </tr>
    <tr>
      <td><p>Ajout d’une description détaillée du correctif QPT 1.1.82 pour <a href="https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4875">ACP2E-4875 : les utilisateurs administrateurs se sont déconnectés lors de l’ouverture de comptes clients avec des carnets d’adresses volumineux</a>.</p>
</td>
      <td>
        Nouvelle rubrique, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/3174f84e0a8c64aaed50cc075a9287bc011778ef">validation</a></td>
    </tr>
  </tbody>
</table>
