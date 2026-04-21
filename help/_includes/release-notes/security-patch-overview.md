---
source-git-commit: 52c330f62d722a4cae7f7f360ca61eca0f04b961
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---
# À propos des versions des correctifs de sécurité Adobe Commerce

**Correctif de bug de sécurité** : changement de code logiciel qui résout un problème de sécurité identifié et fournit les résultats attendus dans une zone de produit affectée. Ces correctifs sont généralement rétrocompatibles.

**Amélioration de la sécurité** : amélioration logicielle ou modification de configuration visant à améliorer la sécurité de manière proactive au sein de l’application. Ces améliorations de sécurité permettent de gérer les risques de sécurité qui affectent la position de sécurité de l’application Adobe Commerce, mais peuvent être rétrocompatibles.

Grâce aux mises à jour de correctifs de sécurité, vous pouvez renforcer la sécurité de votre site sans appliquer d’autres correctifs de qualité et améliorations qui sont contenus dans une mise à jour complète de correctifs. Les versions des correctifs de sécurité sont ajoutées avec « -pN », où N est la version de correctif incrémentiel commençant par 1 (par exemple, 2.3.5-p1). Les versions de correctifs de sécurité peuvent également inclure des correctifs requis pour résoudre les problèmes critiques affectant l’application Adobe Commerce.

Les versions de correctifs de sécurité peuvent également inclure des modifications liées à la conformité requises pour s’assurer que l’application Adobe Commerce peut répondre aux exigences de conformité. Ces modifications peuvent introduire des modifications non rétrocompatibles et sont nécessaires pour s’assurer que toutes les lignes de version prises en charge restent conformes.

Chaque version de correctif de sécurité est basée sur la version complète antérieure du correctif. Il contient les correctifs de qualité et de sécurité de la version précédente du correctif ainsi que les correctifs de sécurité créés entre la version précédente complète du correctif et la version précédente du correctif de sécurité.

Pour obtenir des instructions sur le téléchargement et l’application de correctifs de sécurité, consultez [Comment obtenir et appliquer des correctifs de sécurité](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/how-to/how-to-obtain-and-apply-security-patches) dans la _base de connaissances Adobe Commerce_.

>[!NOTE]
>
>Les correctifs de sécurité de prise en charge étendue sont disponibles uniquement pour les clients Adobe Commerce et ne sont pas disponibles pour la base de code Magento Open Source. Voir [&#x200B; Prise en charge étendue &#x200B;](https://experienceleague.adobe.com/fr/docs/commerce-operations/release/planning/lifecycle-policy#extended-support).

## Fichier de correctif de sécurité isolé

Les fichiers de correctifs de sécurité isolés sont des fichiers de correctifs autonomes non cumulatifs qui incluent des correctifs pour une ou plusieurs vulnérabilités de sécurité uniquement, sans mises à jour de fonctionnalités supplémentaires ni modifications autres que de sécurité. Ces correctifs sont publiés indépendamment pour permettre une correction plus rapide et sont intégrés au correctif de sécurité complet suivant. Vous trouverez des informations détaillées sur les vulnérabilités dans le bulletin de sécurité associé, qui contient un lien vers un article de la base de connaissances (Base de connaissances) contenant des instructions pour l’application du correctif et des informations supplémentaires.

Pour appliquer un fichier de correctif de sécurité isolé, les clients doivent disposer de la dernière version du correctif de sécurité uniquement (la dernière version -p) pour leur ligne de version prise en charge, car les fichiers de correctif de sécurité isolés sont testés exclusivement par rapport à cette version.

Consultez le [Centre de sécurité](https://helpx.adobe.com/fr/security/products/magento.html) pour connaître les dernières mises à jour de sécurité disponibles pour Adobe Commerce.

