---
source-git-commit: 475dbc056ac3e6a00c8f794259bb0fbf04143687
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 0%

---
# Données sensibles

Adobe Commerce et Magento Open Source utilisent votre clé de chiffrement pour chiffrer les éléments suivants :

* Informations sur la carte de crédit
* Noms d’utilisateur et mots de passe spécifiés dans la configuration Admin (par exemple, connexions aux passerelles de paiement)
* Valeurs CAPTCHA envoyées sur le réseau

Adobe Commerce et Magento Open Source font *not* encrypt:

* Noms d’utilisateur et mots de passe administratifs et clients (ces mots de passe sont hachés)
* Adresse
* Numéro de téléphone
* Autres types d’informations d’identification personnelle, à l’exception des numéros de carte de crédit
