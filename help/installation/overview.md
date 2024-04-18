---
title: Installation sur site - Aperçu
description: Découvrez le processus d’installation pour les déploiements sur site d’Adobe Commerce.
exl-id: a9f5b241-d05d-462c-8c7f-479a264c988f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%

---

# Installation sur site - Aperçu

>[!NOTE]
>
>Le diagramme suivant présente un aperçu général de la _**sur site**_ installations d’Adobe Commerce :

![Fonctionnement de l’installation](../assets/installation/install-diagram-24.svg)

Le flux général d&#39;installation est le suivant :

1. Configurez votre environnement de serveur.

   Installez le logiciel prérequis, notamment PHP, Apache, MySQL et le moteur de recherche. Voir [configuration requise](system-requirements.md) pour plus d’informations.

1. Get [clés d’authentification](prerequisites/authentication-keys.md) dans le référentiel du compositeur Commerce.

1. Procurez-vous le logiciel Adobe Commerce.

   * (Recommandé) Obtenez la variable [Métaphorage du compositeur](composer.md) pour gérer les modules et leurs dépendances.

   * Si vous souhaitez contribuer au code du Magento Open Source ou personnaliser l’application, [clone](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) le référentiel GitHub ; Cette méthode nécessite une bonne connaissance de GitHub et du compositeur.

1. Installez l’application à l’aide de la ligne de commande.

   Si l’étape échoue car le logiciel prérequis n’est pas configuré correctement, consultez la section [conditions préalables](prerequisites/overview.md).

1. [Vérifier](next-steps/verify.md) l’installation en affichant votre storefront et l’administrateur.
