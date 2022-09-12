---
title: Présentation de l’installation sur site
description: Découvrez le processus d’installation pour les déploiements sur site d’Adobe Commerce et de Magento Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---


# Présentation de l’installation sur site

>[!NOTE]
>
>Le diagramme suivant présente un aperçu général de la _**sur site**_ installations d’Adobe Commerce et de Magento Open Source :

![Fonctionnement de l’installation](../assets/installation/install-diagram-24.svg)

Le flux général d&#39;installation est le suivant :

1. Configurez votre environnement de serveur.

   Installez le logiciel prérequis, notamment PHP, Apache, MySQL et le moteur de recherche. Voir [configuration requise](system-requirements.md) pour plus d’informations.

1. Get [clés d’authentification](prerequisites/authentication-keys.md) dans le référentiel Commerce Composer.

1. Procurez-vous le logiciel Adobe Commerce ou Magento Open Source.

   * (Recommandé) Obtenez la variable [Métaphorage du compositeur](composer.md) pour gérer les modules et leurs dépendances.

   * Si vous souhaitez contribuer au code du Magento Open Source ou personnaliser l’application, [clone](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) le référentiel GitHub ; Cette méthode nécessite une bonne connaissance de GitHub et du compositeur.

1. Installez l’application à l’aide de la ligne de commande.

   Si l’étape échoue car le logiciel prérequis n’est pas configuré correctement, consultez la section [conditions préalables](prerequisites/overview.md).

1. [Vérifier](next-steps/verify.md) l’installation en affichant votre storefront et l’administrateur.

