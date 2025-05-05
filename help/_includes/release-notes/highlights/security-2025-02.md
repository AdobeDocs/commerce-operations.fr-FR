---
source-git-commit: db78f1339aaa8fab11a5ef7aa4d1fe17d0c3fb0e
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---
# Points forts du correctif de sécurité de février 2025

Cette version comprend les éléments suivants :

* **Gestion des clés de chiffrement et rechiffrement des données** - Redéfinition de la gestion des clés de chiffrement pour améliorer la convivialité et éliminer les limites et bogues existants.<!-- AC-12679 -->

  De nouvelles commandes d’interface de ligne de commande sont désormais disponibles pour [modifier](https://experienceleague.adobe.com/fr/docs/commerce-admin/systems/security/encryption-key) les clés et [rechiffrer](https://developer.adobe.com/commerce/php/development/security/data-encryption/) certaines données de configuration du système, de paiement et de champ personnalisé. La modification des clés dans l’interface utilisateur d’administration n’est plus prise en charge dans cette version. Vous devez utiliser les commandes de l’interface de ligne de commande.

* **Correctif pour [CVE-2025-24434](https://nvd.nist.gov/vuln/detail/CVE-2025-24434)** : résout une vulnérabilité d’autorisation.

  Ce correctif est également disponible sous la forme d’un correctif isolé. Pour plus d’informations, consultez l’article [Base de connaissances](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-08). <!-- AC-12755 -->
