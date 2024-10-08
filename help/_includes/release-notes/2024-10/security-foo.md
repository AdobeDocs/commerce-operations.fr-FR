---
source-git-commit: cb4f388c90902c2fe1df4a5d84841280fa740104
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---
# Principales caractéristiques des correctifs de sécurité d’octobre 2024

Cette version comprend les points forts suivants :

* **Mise à niveau TinyMCE** : l’ [éditeur WYSIWYG](https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/wysiwyg/editor) de l’administrateur utilise désormais la dernière version de la dépendance TinyMCE (7.3 &#x200B;).

   * TinyMCE 7.3 offre une expérience utilisateur améliorée, une meilleure collaboration et une efficacité accrue. TinyMCE 5 a été supprimé dans la ligne de mise à jour 2.4.8. &#x200B;

   * Comme une vulnérabilité de sécurité ([CVE-2024-38357](https://nvd.nist.gov/vuln/detail/CVE-2024-38357)) a été signalée dans TinyMCE 5.10, la dépendance a également été mise à niveau pour toutes les lignes de mise à jour actuellement prises en charge et incluse dans tous les correctifs de sécurité d’octobre 2024 :

      * 2.4.7-p3
      * 2.4.6-p8
      * 2.4.5-p10
      * 2.4.4-p11

* **Mise à niveau de Require.js** : Adobe Commerce utilise désormais la dernière version de Require.js (2.3.7).

   * Comme une vulnérabilité de sécurité ([CVE-2024-38999](https://nvd.nist.gov/vuln/detail/CVE-2024-38999)) a été signalée dans Require.js 2.3.6, la dépendance a également été mise à niveau pour toutes les lignes de version actuellement prises en charge et incluse dans tous les correctifs de sécurité d’octobre 2024 :

      * 2.4.7-p3
      * 2.4.6-p8
      * 2.4.5-p10
      * 2.4.4-p11

>[!NOTE]
>
>Ces mises à jour sont rétrocompatibles et ne doivent pas impacter les personnalisations et les extensions. &#x200B;
