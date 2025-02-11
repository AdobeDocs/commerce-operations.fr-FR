---
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---
# Correctifs inclus dans les correctifs de sécurité d’octobre (sauf la version 2.4.4)

Cette version comprend un correctif permettant de résoudre un problème lié à la passerelle de paiement Braintree.

Le système comprend désormais les champs nécessaires pour répondre aux exigences du mandat 3DS VISA lors de l’utilisation de Braintree comme passerelle de paiement. Cela garantit que toutes les transactions sont conformes aux dernières normes de sécurité établies par VISA. Auparavant, ces champs supplémentaires n’étaient pas inclus dans les informations de paiement envoyées, ce qui aurait pu entraîner le non-respect des nouvelles exigences en matière de VISA.

<!--
BUNDLE-3360
-->