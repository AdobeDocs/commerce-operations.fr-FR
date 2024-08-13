---
source-git-commit: 07947c20ef49d1b3ad5df441c0a47982216ff36f
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---
# Principales caractéristiques des correctifs de sécurité d’août 2024

Cette version comprend les points forts suivants :

* **Limitation de débit pour[!DNL one-time passwords]** : les nouvelles options de configuration système suivantes sont désormais disponibles pour activer la limitation de débit sur la validation [!DNL two-factor authentication (2FA)] [!DNL one-time password (OTP)] :

   * [!UICONTROL **Limite des tentatives de reprise pour l’authentification à deux facteurs**]
   * [!UICONTROL **Délai d’expiration de l’authentification à deux facteurs (secondes)**]

  Adobe conseille de définir un seuil pour la validation OTP 2FA afin de limiter le nombre de tentatives pour atténuer les attaques par force brute. Voir [Sécurité > 2FA](https://experienceleague.adobe.com/en/docs/commerce-admin/config/security/2fa) dans le _Guide de référence de configuration_ pour plus d’informations. <!-- AC-12095 -->

* **Rotation de la clé de chiffrement** : une nouvelle commande d’interface de ligne de commande est désormais disponible pour modifier votre clé de chiffrement. Pour plus d’informations, reportez-vous à l’article [Résolution des problèmes de rotation de la clé de chiffrement : CVE-2024-34102](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/troubleshooting-encryption-key-rotation-cve-2024-34102) de la base de connaissances.

* **Correctif pour [CVE-2020-27511](https://nvd.nist.gov/vuln/detail/CVE-2020-27511)**—Résout une vulnérabilité de sécurité [!DNL Prototype.js].<!-- AC-11936 -->

* **Correctif pour [CVE-2024-39397](https://nvd.nist.gov/vuln/detail/CVE-2024-39397)** : résout une vulnérabilité de sécurité d’exécution de code distant. Cette vulnérabilité affecte les marchands utilisant le serveur web Apache pour les déploiements sur site ou auto-hébergés. Ce correctif est également disponible en tant que correctif isolé. Pour plus d&#39;informations, consultez l&#39;article [Mise à jour de sécurité disponible pour Adobe Commerce - APSB24-61](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb24-61) de la base de connaissances.<!-- ACSD-60551 -->
