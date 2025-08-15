---
source-git-commit: 6ca34e8713f4f138961786de206cd360f0bc1be7
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%

---
# Points forts du correctif de sécurité de février 2025

Les points forts de cette version sont les suivants :

* **Gestion des clés de chiffrement et rechiffrement des données** - Redéfinition de la gestion des clés de chiffrement pour améliorer la convivialité et éliminer les limites et bogues existants.<!-- AC-12679 -->

  De nouvelles commandes d’interface de ligne de commande sont désormais disponibles pour [modifier](https://experienceleague.adobe.com/fr/docs/commerce-admin/systems/security/encryption-key) les clés et [rechiffrer](https://developer.adobe.com/commerce/php/development/security/data-encryption/) certaines données de configuration du système, de paiement et de champ personnalisé. La modification des clés dans l’interface utilisateur d’administration n’est plus prise en charge dans cette version. Vous devez utiliser les commandes de l’interface de ligne de commande.

* **Correctif pour [CVE-2025-24434](https://nvd.nist.gov/vuln/detail/CVE-2025-24434)** : résout une vulnérabilité d’autorisation.

  Ce correctif est également disponible sous la forme d’un correctif isolé. Pour plus d’informations, consultez l’article [Base de connaissances](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-08). <!-- AC-12755 -->

* **Mise à niveau de la version de TinyMCE** : la dépendance TinyMCE a été mise à niveau de la version 7 vers la version 6.8.5 pour résoudre les problèmes de compatibilité des licences.

  Cette modification garantit une conformité continue pendant qu’Adobe évalue un autre éditeur WYSIWYG open source.
