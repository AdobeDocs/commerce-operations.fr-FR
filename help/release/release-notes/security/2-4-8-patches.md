---
title: Notes De Mise À Jour Du Correctif De Sécurité D’Adobe Commerce 2.4.8
description: Découvrez les correctifs de sécurité, les améliorations de sécurité et les autres mises à jour liées à la sécurité inclus dans les versions des correctifs de sécurité pour Adobe Commerce version 2.4.7.
exl-id: 5f8866ed-9215-4b2e-9c77-b2d474f6c1f9
source-git-commit: 40328796c25c56c101f95e286298325b5d1ef439
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# Notes de mise à jour des correctifs de sécurité d’Adobe Commerce 2.4.8

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.8-p3

La version de sécurité 2.4.8-p3 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités identifiées dans les versions précédentes de 2.4.8.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB25-94](https://helpx.adobe.com/security/products/magento/apsb25-94.html).

{{b2b-patches}}

### Faits saillants

Les points forts de cette version sont les suivants :

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

* Correction pour ACP2E-3874 : la réponse de l’API REST pour les détails de commande contient désormais des valeurs correctes pour les attributs `base_row_total` et `row_total` au cas où plusieurs mêmes éléments auraient été commandés.

* Correction de -AC-15446 : correction d’une erreur dans `Magento\Framework\Mail\EmailMessage`, en raison de laquelle `getBodyText()` tentait d’appeler une méthode `getTextBody()` inexistante sur `Symfony\Component\Mime\Message`, afin d’assurer la compatibilité avec Magento 2.4.8-p2 et `magento/framework` 103.0.8-p2.

{{oct-2025-backports}}

## 2.4.8-p2

La version de sécurité 2.4.8-p2 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités identifiées dans les versions précédentes de 2.4.8.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB25-71](https://helpx.adobe.com/security/products/magento/apsb25-71.html).

{{b2b-patches}}

## 2.4.8-p1

La version de sécurité 2.4.8-p1 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités identifiées dans les versions précédentes de 2.4.8.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB25-50](https://helpx.adobe.com/security/products/magento/apsb25-50.html).

{{b2b-patches}}

### Faits saillants

Les points forts de cette version sont les suivants :

* **Amélioration des performances de l’API** : résout la dégradation des performances des points d’entrée d’API web asynchrones en bloc introduits après le correctif de sécurité précédent<!-- AC-14078 -->.

* **Correctif des blocs d’accès CMS**—Résout un problème en raison duquel les utilisateurs administrateurs disposant d’autorisations limitées (comme un accès au marchandisage uniquement) ne pouvaient pas afficher la page de liste [!UICONTROL CMS Blocks].

  Auparavant, ces utilisateurs rencontraient une erreur en raison de paramètres de configuration manquants après l’installation des correctifs de sécurité précédents.<!-- AC-14087 -->

* **Compatibilité des limites de cookies** : résout une modification non rétrocompatible impliquant la constante `MAX_NUM_COOKIES` dans le framework. Cette mise à jour restaure le comportement attendu et assure la compatibilité des extensions ou des personnalisations qui interagissent avec les limites de cookies.<!-- AC-14475 -->

* **Opérations asynchrones** : opérations asynchrones restreintes pour remplacer les commandes précédentes de clients.<!-- AC-13917 -->

* **Correctif pour CVE-2025-47110** : résout une vulnérabilité des modèles d’e-mail.<!-- AC-14695 -->

* **Correctif pour VULN-31547** : résout une vulnérabilité de lien canonique de catégorie.<!-- AC-14713 -->

>[!BEGINSHADEBOX]

Les correctifs pour CVE-2025-47110 et VULN-31547 sont également disponibles en tant que correctif isolé. Pour plus d’informations, consultez l’article [Base de connaissances](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-50).

>[!ENDSHADEBOX]

<!-- Last updated from includes: 2025-10-06 13:12:34 -->
