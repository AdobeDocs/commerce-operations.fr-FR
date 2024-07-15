---
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '64'
ht-degree: 1%

---
# Données sensibles

Adobe Commerce utilise votre clé de chiffrement pour chiffrer les éléments suivants :

* Informations sur la carte de crédit
* Noms d’utilisateur et mots de passe spécifiés dans la configuration Admin (par exemple, connexions aux passerelles de paiement)
* Valeurs CAPTCHA envoyées sur le réseau

Adobe Commerce do *not* encrypt :

* Noms d’utilisateur et mots de passe administratifs et clients (ces mots de passe sont hachés)
* Adresse
* Numéro de téléphone
* Autres types d’informations d’identification personnelle, à l’exception des numéros de carte de crédit
