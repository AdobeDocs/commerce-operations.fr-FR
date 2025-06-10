---
source-git-commit: f9cc5ab0cb1b64455e12081ffbf719e0f2a791ad
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---
# Points forts du correctif de sécurité de juin 2025

Les points forts de cette version sont les suivants :

* **Amélioration des performances de l’API** : résout la dégradation des performances des points d’entrée d’API web asynchrones en bloc introduits après le correctif de sécurité précédent<!-- AC-14078 -->.

* **Correctif des blocs d’accès CMS**—Résout un problème en raison duquel les utilisateurs administrateurs disposant d’autorisations limitées (comme un accès au marchandisage uniquement) ne pouvaient pas afficher la page de liste [!UICONTROL CMS Blocks].

  Auparavant, ces utilisateurs rencontraient une erreur en raison de paramètres de configuration manquants après l’installation des correctifs de sécurité précédents.<!-- AC-14087 -->

* **Compatibilité des limites de cookies** : résout une modification non rétrocompatible impliquant la constante `MAX_NUM_COOKIES` dans le framework. Cette mise à jour restaure le comportement attendu et assure la compatibilité des extensions ou des personnalisations qui interagissent avec les limites de cookies.<!-- AC-14475 -->

* **Correctif pour CVE-2024-34104** : résout une vulnérabilité d’autorisation incorrecte.<!-- AC-13917 -->

* **Correctif pour CVE-2025-47110** : résout une vulnérabilité des modèles d’e-mail.<!-- AC-14695 -->

* **Correctif pour VULN-31547** : résout une vulnérabilité de lien canonique de catégorie.<!-- AC-14713 -->

>[!BEGINSHADEBOX]

Les correctifs pour CVE-2025-47110 VULN-31547 sont également disponibles en tant que correctif isolé. Pour plus d’informations, consultez l’article [Base de connaissances](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-50).

>[!ENDSHADEBOX]
