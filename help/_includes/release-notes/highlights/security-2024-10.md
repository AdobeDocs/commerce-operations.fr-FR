---
source-git-commit: c71367c553dce66c146540389461f36eaa529bfc
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---
# Points forts du correctif de sécurité d’octobre 2024

Les points forts de cette version sont les suivants :

* **Mise à niveau de TinyMCE** : l’éditeur [WYSIWYG](https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/wysiwyg/editor) dans l’administration utilise désormais la dernière version de la dépendance TinyMCE (7.3&#x200B;).

   * TinyMCE 7.3 offre une expérience utilisateur améliorée, une meilleure collaboration et une efficacité accrue. TinyMCE 5 a été supprimé dans la version 2.4.8&#x200B;

   * En raison d’une vulnérabilité de sécurité ([CVE-2024-38357](https://nvd.nist.gov/vuln/detail/CVE-2024-38357)) signalée dans TinyMCE 5.10, la dépendance a également été mise à niveau pour toutes les lignes de version actuellement prises en charge et incluse dans tous les correctifs de sécurité d’octobre 2024 :

      * 2.4.7-p3
      * 2.4.6-p8
      * 2.4.5-p10
      * 2.4.4-p11

* **Mise à niveau de Require.js**—Adobe Commerce utilise désormais la dernière version de Require.js (2.3.7).

   * Étant donné qu’une vulnérabilité de sécurité ([CVE-2024-38999](https://nvd.nist.gov/vuln/detail/CVE-2024-38999)) a été signalée dans Require.js 2.3.6, la dépendance a également été mise à niveau pour toutes les lignes de version actuellement prises en charge et incluse dans tous les correctifs de sécurité d’octobre 2024 :

      * 2.4.7-p3
      * 2.4.6-p8
      * 2.4.5-p10
      * 2.4.4-p11

>[!NOTE]
>
>Ces mises à jour sont rétrocompatibles et n’ont aucune incidence sur les personnalisations et les extensions&#x200B;
