---
title: Configuration de la mise en cache
description: Découvrez la mise en cache et comment configurer les mécanismes de mise en cache pour l’application Adobe Commerce et Magento Open Source.
source-git-commit: ee2e446edf79efcd7cbbd67248f8e7ece06bfefd
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# Configuration de la mise en cache

[!DNL Commerce] vous permet de configurer des alternatives à la mise en cache du système de fichiers par défaut. Le présent guide aborde certaines de ces solutions; à savoir :

- Configurez les éléments suivants : [cache](https://glossary.magento.com/cache) dans les [!DNL Commerce] configuration :

   - [Base](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [Redis](config-redis.md)
   - Système de fichiers (par défaut) : Aucune configuration n’est nécessaire pour utiliser la mise en cache du système de fichiers par défaut.

- Configurez les [Varnish](config-varnish.md) sans modifier la variable [!DNL Commerce] configuration.

## Terminologie de mise en cache

[!DNL Commerce] utilise la terminologie de mise en cache suivante :

- **Frontière**: similaire à une interface ou une passerelle pour le stockage du cache, implémenté par [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend).
- **Types de cache**: peut être l’un des types fournis avec [!DNL Commerce] ou vous pouvez [créer le vôtre](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/).
- **Serveur principal**—Précise les détails [stockage du cache](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html), implémenté par [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)
- **Serveur principal à deux niveaux**—Stocke les enregistrements de cache dans deux serveurs principaux : plus rapide et plus lent.

   >[!INFO]
   >
   >La configuration du cache principal à deux niveaux dépasse le cadre de ce guide.

## Options de configuration

- Modification du fourni `default` front de cache—

   Vous ne modifiez que la variable `<magento_root>/app/etc/di.xml` fichier , le fichier global de l’application Commerce [injection de dépendance](https://glossary.magento.com/dependency-injection) configuration.

- Configuration de votre propre front de cache personnalisé —

   Vous ne modifiez que la variable `<magento_root>/app/etc/env.php` car il remplace la configuration équivalente dans la `di.xml` fichier .

>[!TIP]
>
>Le vernis ne nécessite pas de modifications au niveau de la fonction [!DNL Commerce] configuration. Voir [Configurer et utiliser le vernis](config-varnish.md).