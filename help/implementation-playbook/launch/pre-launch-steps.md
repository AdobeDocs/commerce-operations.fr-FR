---
title: Étapes préalables au lancement
description: Utilisez nos listes de contrôle de prélancement pour garantir une mise en oeuvre fluide du site Adobe Commerce.
exl-id: bd10881f-0336-4aa4-82ad-4d635010e2e4
feature: Deploy
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---

# Étapes de prélancement

Une fois le déploiement et les tests terminés dans les environnements d’évaluation, vous pouvez commencer la préparation du lancement du site. L’évaluation est un environnement de quasi-production s’exécutant sur des composants matériels, des configurations, une architecture et des services similaires. Il peut réduire vos temps d’arrêt et faire en sorte que votre extension, votre service, vos configurations personnalisées et votre acceptation par les utilisateurs du commerce testent des composants essentiels pour publier vos sites et magasins.

La liste de contrôle de prélancement doit être vérifiée avant l’état de lancement, qui comprend les vérifications principales suivantes :

- Désactivation du code pour le déploiement
- Assurez-vous que les temps d’arrêt ont été communiqués au préalable d’au moins un jour pour la version de maintenance et d’une semaine pour le premier lancement.
- Les scripts de déploiement sont entièrement configurés/configurés pour les environnements de production/d’évaluation/d’intégration.
- Les bases de données sont toutes configurées et identiques entre les environnements d’évaluation et de production.
- Les certificats SSL (TLS) sont validés pour les environnements d’évaluation/de production.
- Les services de messagerie sont correctement configurés et fonctionnent pour les emails transactionnels.
- Le réseau de diffusion de contenu est configuré pour les environnements d’évaluation/de production.
- Configuration de l’analyse de sécurité pour les environnements d’évaluation/de production
   - Analyse de la sécurité Adobe Commerce
- Effectuez une évaluation des performances en procédant comme suit :
   - JMeter
   - Siège
   - Test de page web
   - Vitesse de la page Google
- Validation de toutes les intégrations tierces qui fonctionneront dans l’application (OMS, CRM)
- Activation de l’outil de surveillance des performances (nouvelles versions)
- Activités de migration de données en répétition (le cas échéant)

![Diagramme présentant la phase 1 du processus de lancement](../../assets/playbooks/launch-steps-1.svg)

Les principales différences entre les implémentations sur site et cloud d’Adobe Commerce sont les scripts et les outils de déploiement, ainsi que la configuration pour SSL, le service de messagerie et le réseau de diffusion de contenu. Cependant, le processus reste le même.

Pour le certificat SSL (TLS), Adobe Commerce sur l’infrastructure cloud fournit un certificat de caractères génériques Fastly. Pour commencer à l’utiliser, vous devez réussir la validation : ajoutez l’enregistrement TXT Fastly au nom de domaine apex dans vos paramètres DNS. L’enregistrement TXT rapide se trouve dans la feuille de calcul intégrée, sinon vous devez envoyer un ticket d’assistance pour l’obtenir. Remplacez ce texte par vos questions/commentaires ici. Si vous utilisez votre propre certificat SSL (TLS) au lieu d’un certificat générique Fastly, envoyez un ticket d’assistance avec votre certificat joint à la configuration.

Adobe Commerce sur l’infrastructure cloud fournit la fonctionnalité SendGrid Mail pour vos emails transactionnels. Pour les plans Pro, vous devez ajouter des enregistrements SendGrid à vos paramètres DNS. Les enregistrements SendGrid se trouvent dans la feuille de calcul intégrée. Sinon, SI ou le commerçant doit envoyer des tickets d’assistance pour les obtenir. Pour commencer, vous n’avez pas besoin d’apporter de modifications à votre DNS ; SendGrid est préconfiguré pour vous.

## Liste de contrôle complète avant le lancement

La liste de contrôle complète de prélancement répertorie toutes les activités principales dont l’exhaustivité est nécessaire pour passer à l’état de lancement.

- Mise à jour des plans d’atténuation des risques liés à la mise en service
- Noms de domaine corrects fournis
- Les emails sortants ont été testés.
- Le certificat SSL est configuré et configuré.
- La configuration très importante de l’application Adobe Commerce est correctement mise à jour.
- Les URL de base et l’URL d’administration de base sont correctement définies sur le nom d’hôte final.
- Les mots de passe de l’administrateur ont été modifiés.
- Tous les utilisateurs ayant accès à l’application qui n’en requièrent plus l’accès sont supprimés.
- Configuration des paiements pour l’environnement de production (pour certains, le paiement utilise le mode sandbox pour les tests)
- Les données de test (client, liste bloquée, révisions, commandes et données associées) de la base de données de production sont effacées.

![Diagramme présentant la phase 2 du processus de lancement](../../assets/playbooks/launch-steps-2.svg)
