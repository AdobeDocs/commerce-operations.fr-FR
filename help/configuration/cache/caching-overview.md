---
title: Configuration de la mise en cache
description: Découvrez la mise en cache et comment configurer les mécanismes de mise en cache de l’application Adobe Commerce.
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# Configuration de la mise en cache

[!DNL Commerce] vous permet de configurer des alternatives à la mise en cache du système de fichiers par défaut. Le présent guide aborde certaines de ces solutions :

- Configurez les mécanismes de mise en cache suivants dans le [!DNL Commerce] configuration :

   - [Base](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [Redis](config-redis.md)
   - Système de fichiers (par défaut) : aucune configuration n’est nécessaire pour utiliser la mise en cache du système de fichiers par défaut.

- Configurez la variable [Varnish](config-varnish.md) sans modifier la variable [!DNL Commerce] configuration.

## Terminologie de mise en cache

[!DNL Commerce] utilise la terminologie de mise en cache suivante :

- **Frontière**: similaire à une interface ou une passerelle pour le stockage du cache, implémenté par [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend).
- **Types de cache**: peut être l’un des types fournis avec [!DNL Commerce] ou vous pouvez [créer les vôtres](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/).
- **Serveur principal**—Précise les détails [stockage du cache](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html), implémenté par [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)
- **Serveur principal à deux niveaux**: stocke les enregistrements de cache dans deux arrière-plans : un plus rapide et un plus lent.

  >[!INFO]
  >
  >La configuration du cache principal à deux niveaux dépasse le cadre de ce guide.

## Options de configuration

- Modification du fourni `default` front de cache—

  Vous ne modifiez que la variable `<magento_root>/app/etc/di.xml` fichier , configuration d’injection de dépendance globale de l’application Commerce.

- Configuration de votre propre front de cache personnalisé —

  Vous ne modifiez que la variable `<magento_root>/app/etc/env.php` car il remplace la configuration équivalente dans la `di.xml` fichier .

>[!TIP]
>
>Le vernis ne nécessite pas de modifications au niveau du [!DNL Commerce] configuration. Voir [Configurer et utiliser le vernis](config-varnish.md).
