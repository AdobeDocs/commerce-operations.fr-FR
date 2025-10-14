---
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---
# Points forts du correctif de sécurité d’août 2024

Les points forts de cette version sont les suivants :

* **Limitation de débit pour les[!DNL one-time passwords]** : les nouvelles options de configuration système suivantes sont désormais disponibles pour activer la limitation de débit lors de la validation de [!DNL two-factor authentication (2FA)] [!DNL one-time password (OTP)] :

   * [!UICONTROL **Limite de tentatives pour l’authentification à deux facteurs**]
   * [!UICONTROL **Durée de verrouillage de l’authentification à deux facteurs (secondes)**]

  Adobe recommande de définir un seuil pour la validation du mot de passe à usage unique 2FA afin de limiter le nombre de tentatives de reprise pour atténuer les attaques par force brute. Voir [Sécurité > 2FA](https://experienceleague.adobe.com/fr/docs/commerce-admin/config/security/2fa) dans le _Guide de référence de configuration_ pour plus d’informations. <!-- AC-12095 -->

* **Rotation de la clé de chiffrement** : une nouvelle commande d’interface de ligne de commande est désormais disponible pour modifier votre clé de chiffrement. Pour plus d’informations, consultez l’article [Dépannage de la rotation de la clé de chiffrement : CVE-2024-34102](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/troubleshooting-encryption-key-rotation-cve-2024-34102) de la base de connaissances .

* **Correctif pour [CVE-2020-27511](https://nvd.nist.gov/vuln/detail/CVE-2020-27511)** : résout une vulnérabilité de sécurité [!DNL Prototype.js].<!-- AC-11936 -->

* **Correctif pour [CVE-2024-39397](https://nvd.nist.gov/vuln/detail/CVE-2024-39397)**—Résout une vulnérabilité de sécurité d&#39;exécution de code à distance. Cette vulnérabilité affecte les commerçants qui utilisent le serveur web Apache pour les déploiements sur site ou auto-hébergés. Ce correctif est également disponible sous la forme d’un correctif isolé. Consultez l’article [&#x200B; Mise à jour de sécurité disponible pour Adobe Commerce - APSB24-61 &#x200B;](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb24-61) de la base de connaissances pour plus d’informations.<!-- ACSD-60551 -->
