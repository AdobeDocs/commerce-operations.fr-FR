---
source-git-commit: a841412309095c6efeb8d84d8612598fd6f1bd32
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---
# Points forts du correctif de sécurité de juin 2025

Les points forts de cette version sont les suivants :

- **Amélioration des performances de l’API** : résout la dégradation des performances des points d’entrée d’API web asynchrones en bloc introduits après le correctif de sécurité précédent<!-- AC-14078 -->.

- **Correctif des blocs d’accès CMS**—Résout un problème en raison duquel les utilisateurs administrateurs disposant d’autorisations limitées (comme un accès au marchandisage uniquement) ne pouvaient pas afficher la page de liste [!UICONTROL CMS Blocks].

  Auparavant, ces utilisateurs rencontraient une erreur en raison de paramètres de configuration manquants après l’installation des correctifs de sécurité précédents.<!-- AC-14087 -->

- **Compatibilité des limites de cookies** : résout une modification non rétrocompatible impliquant la constante `MAX_NUM_COOKIES` dans le framework. Cette mise à jour restaure le comportement attendu et assure la compatibilité des extensions ou des personnalisations qui interagissent avec les limites de cookies.<!-- AC-14475 -->

- **Opérations asynchrones** : opérations asynchrones restreintes pour remplacer les commandes précédentes de clients.<!-- AC-13917 -->

- **Correctif pour CVE-2025-47110** : résout une vulnérabilité des modèles d’e-mail.<!-- AC-14695 -->

>[!BEGINSHADEBOX]

Le correctif pour CVE-2025-47110 est également disponible sous la forme d’un correctif isolé. Pour plus d’informations, consultez l’article [Base de connaissances](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-50).

>[!ENDSHADEBOX]