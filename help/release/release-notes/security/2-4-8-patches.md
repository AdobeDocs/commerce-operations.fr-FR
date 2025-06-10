---
title: Notes De Mise À Jour Du Correctif De Sécurité D’Adobe Commerce 2.4.8
description: Découvrez les correctifs de sécurité, les améliorations de sécurité et les autres mises à jour liées à la sécurité inclus dans les versions des correctifs de sécurité pour Adobe Commerce version 2.4.7.
source-git-commit: e996ef274920b1828331e2bb1eadacbb2cde59a6
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---


# Notes de mise à jour des correctifs de sécurité d’Adobe Commerce 2.4.8

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.8-p1

La version de sécurité 2.4.8-p1 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités identifiées dans les versions précédentes de 2.4.8.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB25-50](https://helpx.adobe.com/fr/security/products/magento/apsb25-50.html).

{{b2b-patches}}

### Faits saillants

Les points forts de cette version sont les suivants :

* **Amélioration des performances de l’API** : résout la dégradation des performances des points d’entrée d’API web asynchrones en bloc introduits après le correctif de sécurité précédent<!-- AC-14078 -->.

* **Correctif des blocs d’accès CMS**—Résout un problème en raison duquel les utilisateurs administrateurs disposant d’autorisations limitées (comme un accès au marchandisage uniquement) ne pouvaient pas afficher la page de liste [!UICONTROL CMS Blocks].

  Auparavant, ces utilisateurs rencontraient une erreur en raison de paramètres de configuration manquants après l’installation des correctifs de sécurité précédents.<!-- AC-14087 -->

* **Compatibilité des limites de cookies** : résout une modification non rétrocompatible impliquant la constante `MAX_NUM_COOKIES` dans le framework. Cette mise à jour restaure le comportement attendu et assure la compatibilité des extensions ou des personnalisations qui interagissent avec les limites de cookies.<!-- AC-14475 -->

* **Correctif pour CVE-2024-34104** : résout une vulnérabilité d’autorisation incorrecte.<!-- AC-13917 -->

* **Correctif pour CVE-2025-47110** : résout une vulnérabilité des modèles d’e-mail.<!-- AC-14695 -->

* **Correctif pour VULN-31547** : résout une vulnérabilité de lien canonique de catégorie.<!-- AC-14713 -->

>[!BEGINSHADEBOX]

Les correctifs pour CVE-2025-47110 et VULN-31547 sont également disponibles en tant que correctif isolé. Pour plus d’informations, consultez l’article [Base de connaissances](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-50).

>[!ENDSHADEBOX]
