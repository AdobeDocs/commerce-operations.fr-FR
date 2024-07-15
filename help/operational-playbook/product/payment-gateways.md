---
title: Passerelles de paiement
description: Choisissez un fournisseur de passerelle de paiement pour votre projet de commerce électronique en fonction des besoins de votre entreprise.
exl-id: eab50191-0744-41da-99ba-2e06ea61da27
feature: Best Practices, Payments
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# Points de contrôle des paiements

Il fut un temps où l&#39;argent liquide était la principale source de transactions, mais le monde en ligne a pris le dessus et les méthodes de paiement en ligne remplacent les anciennes méthodes de paiement. Tout est maintenant en ligne, ce qui rend les choses plus faciles et plus accessibles, y compris les cartes de crédit, les portefeuilles électroniques et les virements bancaires.

![ Loggos du fournisseur de passerelle de paiement ](../../assets/playbooks/payment-gateways.png)

Une passerelle de paiement est un fournisseur de services qui connecte et traite les paiements pour les sites web de commerce électronique. Ils jouent un rôle essentiel dans les taux d’expérience d’achat et de conversion des clients. Les systèmes de paiement compliqués ont tendance à pousser les clients à abandonner leur panier. Il est important de fournir aux clients un système de paiement facile et convivial où même si un mode de paiement échoue, ils disposent d’une autre méthode pour les motiver à effectuer l’achat.

## Exigences de révision

Les détaillants doivent sélectionner la meilleure passerelle de paiement qui réponde à leurs besoins. Il existe de nombreuses passerelles de paiement sur le marché, comme Braintree et Stripe, mais avant de décider d&#39;une passerelle de paiement, posez-vous les questions suivantes :

- Quels sont mes besoins professionnels ?
- Est-ce dans mon budget ?
- Quelle est la solidité de la sécurité sur la passerelle de paiement ?
- Y aura-t-il un impact sur mon interface utilisateur/utilisateur storefront ?
- Quelle est la performance de la passerelle de paiement ?
- Comment le service d’assistance de la passerelle de paiement est-il effectué après l’achat ?
- Quel fournisseur de passerelle de paiement me convient le mieux ?
- La passerelle de paiement offre-t-elle d’autres fonctions, comme le calcul de la taxe, l’utilisation des géolocalisations et le calcul des frais de service ?

Vous devez connaître certaines limites des passerelles de paiement, notamment :

- Tous les types de cartes ne sont pas acceptés par les passerelles de paiement.
- Certaines options de paiement peuvent ne pas être disponibles pour les acheteurs internationaux.
- Des failles de sécurité dans la passerelle de paiement. Pour des raisons de sécurité, les clients ont tendance à hésiter à passer des commandes en ligne.

Lorsqu’une entreprise décide d’intégrer une passerelle de paiement à sa plateforme, il est toujours préférable de voir comment elle apparaît sur le storefront, quel type d’expérience elle fournit aux clients et si elle est conviviale. Assurez-vous également que la sécurité du paiement ne peut pas être compromise. Une passerelle de paiement efficace et sécurisée offre une meilleure expérience client.

## Considérations B2B et B2C

Les entreprises B2B et B2C ont des systèmes de paiement similaires, mais les entreprises B2B ont plus de règles, de réglementations et de processus. Les entreprises B2B ont tendance à traiter des volumes plus importants par rapport aux entreprises B2C.

Les clients B2C achètent des produits ou des services à usage individuel. Les clients paient généralement le même prix que les autres clients et il n’y a pas de négociation en cause. Les clients B2B incluent divers
les parties prenantes, ce qui rend l’approbation plus complexe et plus coûteuse.

Les clients B2B ont des commandes et des exigences différentes, qui doivent être traitées et approuvées par le représentant commercial ou un représentant commercial doit être impliqué lorsqu’un client achète en ligne à l’aide d’une demande de proposition (RFP) ou d’un bon de commande (PO).

Les paiements B2C peuvent être ponctuels et ont une valeur moindre. Les clients ajoutent des produits à leur panier et font le paiement en toute sécurité via une carte de crédit ou un e-portefeuille.

En raison de la valeur d’achat élevée des transactions B2B, les entreprises B2B offrent davantage d’options de paiement en plus des options standard, notamment les chèques, les virements bancaires et les bons de commande.

La mise en oeuvre des options de paiement appropriées dépend du type d’entreprise et des besoins de l’entreprise.
