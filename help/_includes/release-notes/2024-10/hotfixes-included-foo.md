---
source-git-commit: 5ef5c2dedbbef2858a6bbc6c0aca13fd9adae0c8
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---
# Correctifs inclus dans les correctifs de sécurité d’octobre (sauf 2.4.4)

Cette version comprend un correctif pour résoudre un problème avec la passerelle de paiement du Braintree.

Le système comprend désormais les champs nécessaires pour remplir les exigences du mandat VISA 3DS lors de l’utilisation de Braintree comme passerelle de paiement. Cela permet de s&#39;assurer que toutes les transactions sont conformes aux dernières normes de sécurité établies par VISA. Auparavant, ces champs supplémentaires n&#39;étaient pas inclus dans les informations de paiement envoyées, ce qui aurait pu entraîner le non-respect des nouvelles exigences en matière de VISA.

<!--
BUNDLE-3360
-->