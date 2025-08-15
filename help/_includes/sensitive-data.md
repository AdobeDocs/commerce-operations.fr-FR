---
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '64'
ht-degree: 1%

---
# Données sensibles

Adobe Commerce utilise votre clé de chiffrement pour chiffrer les éléments suivants :

* Informations de carte de crédit
* Noms d’utilisateur et mots de passe spécifiés dans la configuration d’administration (par exemple, connexions aux passerelles de paiement)
* Valeurs CAPTCHA envoyées sur le réseau

Adobe Commerce ne chiffre ** :

* Noms d’utilisateur et mots de passe administratifs et clients (ces mots de passe sont hachés)
* Adresse
* Numéro de téléphone
* Autres types d&#39;informations d&#39;identification personnelle, à l&#39;exception des numéros de carte de crédit
