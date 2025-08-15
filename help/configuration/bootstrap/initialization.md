---
title: Initialisation et amorçage de l'application
description: Découvrez la logique d’initialisation et de bootstrap de l’application Commerce.
feature: Configuration, Install, Media
exl-id: 46d1ffc0-7870-4dd1-beec-0a9ff858ab62
source-git-commit: 403a5937561d82b02fd126c95af3f70b0ded0747
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 0%

---

# Présentation de l&#39;initialisation et du bootstrap

Pour exécuter l’application Commerce, les actions suivantes sont implémentées dans [pub/index.php][index] :

- Incluez [app/bootstrap.php][bootinitial], qui effectue les routines d&#39;initialisation essentielles telles que le traitement des erreurs, l&#39;initialisation du chargeur automatique, la définition des options de profilage et la définition du fuseau horaire par défaut.
- Créez une instance de [\Magento\Framework\App\Bootstrap.php][bootstrap] <!-- It requires initialization parameters to be specified in constructor. Normally, the $_SERVER super-global variable is supposed to be passed there. -->
- Créez une instance d’application Commerce : [\Magento\Framework\AppInterface][app-face]
- Exécuter Commerce

## Logique d’exécution de Bootstrap

[L’objet bootstrap][bootinitial] utilise l’algorithme suivant pour exécuter l’application Commerce :

1. Initialise le gestionnaire d’erreurs.
1. Crée les [gestionnaire d’objets][object] et les services partagés de base qui sont utilisés partout et qui sont affectés par l’environnement. Les paramètres d’environnement sont correctement injectés dans ces objets.
1. Affirme que le mode de maintenance n’est _pas_ activé ; dans le cas contraire, s’arrête.
1. Affirme que l’application Commerce est installée ; dans le cas contraire, elle s’arrête.
1. Démarre l’application Commerce.

   Toute exception non interceptée lors du lancement de l’application est automatiquement renvoyée à Commerce dans la méthode `catchException()` que vous pouvez utiliser pour gérer l’exception. Ce dernier doit renvoyer `true` ou `false` :

   - Si `true` : exception gérée par Commerce avec succès. Pas besoin de faire autre chose.
   - Si `false` : (ou tout autre résultat vide) Commerce n’a pas géré l’exception. L’objet bootstrap exécute la sous-routine de gestion des exceptions par défaut.

1. Envoie la réponse fournie par l’objet d’application.

   >[!INFO]
   >
   >Les assertions selon lesquelles l’application Commerce est installée et n’est pas en mode de maintenance constituent le comportement par défaut de la classe `\Magento\Framework\App\Bootstrap`. Vous pouvez le modifier à l’aide d’un script de point d’entrée lors de la création de l’objet Bootstrap.

   Exemple de script de point d’entrée qui modifie l’objet Bootstrap :

   ```php
   <?php
   use Magento\Framework\App\Bootstrap;
   require __DIR__ . '/app/bootstrap.php';
   
   $params = $_SERVER;
   $params[Bootstrap::PARAM_REQUIRE_MAINTENANCE] = true; // default false
   $params[Bootstrap::PARAM_REQUIRE_IS_INSTALLED] = false; // default true
   $bootstrap = Bootstrap::create(BP, $params);
   
   /** @var \Magento\Framework\App\Http $app */
   $app = $bootstrap->createApplication('Magento\Framework\App\Http');
   $bootstrap->run($app);
   ```

## Gestion des exceptions par défaut

L’objet bootstrap spécifie la manière dont l’application Commerce gère les exceptions non interceptées comme suit :

- En [mode Développeur](../bootstrap/application-modes.md#developer-mode), affiche l’exception en l’état.
- Dans tout autre mode, tente de consigner une exception et d’afficher un message d’erreur générique.
- Termine Commerce avec le code d’erreur `1`

## Applications de point d’entrée

Nous disposons des applications de point d’entrée suivantes (c’est-à-dire des applications définies par Commerce qui sont utilisées par le serveur web comme index de répertoire) :

### Point d’entrée HTTP

[\Magento\Framework\App\Http][http] fonctionne comme suit :

1. Détermine la [zone d&#39;application](https://developer.adobe.com/commerce/php/architecture/modules/areas/).
1. Démarre le contrôleur avant et les systèmes de routage afin de trouver et d&#39;exécuter une action du contrôleur.
1. Utilise un objet de réponse HTTP pour renvoyer le résultat obtenu à partir de l’action du contrôleur.
1. Traitement des erreurs (dans l&#39;ordre de priorité suivant) :

   1. Si vous utilisez [mode Développeur](../bootstrap/application-modes.md#developer-mode) :
      - Si l’application Commerce n’est pas installée, redirigez-vous vers l’assistant d’installation.
      - Si l’application Commerce est installée, affichez une erreur et le code d’état HTTP 500 (Internal Server Error).
   1. Si l’application Commerce est en mode de maintenance, affichez une page de destination conviviale indiquant « Service indisponible » avec le code d’état HTTP 503 (Service indisponible).
   1. Si l’application Commerce n’est _pas_ installée, redirigez-la vers l’assistant d’installation.
   1. Si la session n’est pas valide, redirigez-la vers la page d’accueil.
   1. En cas d’autre erreur d’initialisation de l’application, affichez une page conviviale « Page introuvable » avec le code d’état HTTP 404 (Not Found).
   1. Pour toute autre erreur, affichez une page conviviale « Service indisponible » avec la réponse HTTP 503, générez un rapport d’erreur et affichez son identifiant sur la page.

### Point d’entrée de ressource statique

[\Magento\Framework\App\StaticResource][static-resource] est une application permettant de récupérer des ressources statiques (par exemple, CSS, JavaScript et images). Cela reporte toutes les actions avec une ressource statique jusqu’à ce que la ressource soit demandée.

>[!INFO]
>
>Le point d’entrée des fichiers de vue statiques n’est pas utilisé en [mode de production](application-modes.md#production-mode) afin d’éviter des exploits potentiels sur le serveur. En mode de production, l’application Commerce s’attend à ce que toutes les ressources nécessaires existent dans le répertoire `<your Commerce install dir>/pub/static`.

En mode par défaut ou développeur, une requête de ressource statique inexistante est redirigée vers le point d’entrée statique conformément aux règles de réécriture spécifiées par le `.htaccess` approprié.
Lorsque la requête est redirigée vers le point d’entrée, l’application Commerce analyse l’URL demandée en fonction des paramètres récupérés et recherche la ressource demandée.

- En mode [développeur](application-modes.md#developer-mode), le contenu du fichier est renvoyé, de sorte que chaque fois que la ressource est demandée, le contenu renvoyé est à jour.
- En mode [par défaut](application-modes.md#default-mode), la ressource récupérée est publiée afin d’être accessible par l’URL précédemment demandée.

  Toutes les futures demandes de la ressource statique sont traitées par le serveur de la même manière que les fichiers statiques ; c’est-à-dire sans impliquer le point d’entrée. S’il est nécessaire de synchroniser les fichiers publiés avec les fichiers d’origine, le répertoire `pub/static` doit être supprimé ; par conséquent, les fichiers sont automatiquement republiés avec la requête suivante.

### Point d’entrée des ressources multimédia

[Magento\MediaStorage\App\Media][media] récupère les ressources multimédias (c’est-à-dire tous les fichiers chargés dans le stockage multimédia) de la base de données. Il est utilisé chaque fois que la base de données est configurée en tant que stockage multimédia.

`\Magento\Core\App\Media` tente de trouver le fichier multimédia dans le stockage de base de données configuré et de l&#39;écrire dans le répertoire `pub/static`, puis de renvoyer son contenu. En cas d’erreur, il renvoie un code d’état HTTP 404 (Introuvable) dans l’en-tête sans contenu.

<!-- Link Definitions -->

[app-face]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/AppInterface.php
[bootinitial]: https://github.com/magento/magento2/tree/2.4/app/bootstrap.php
[bootstrap]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Bootstrap.php
[http]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Http
[index]: https://github.com/magento/magento2/tree/2.4/pub/index.php
[media]: https://github.com/magento/magento2/tree/2.4/app/code/Magento/MediaStorage/App/Media.php
[object]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/ObjectManager
[static-resource]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/StaticResource.php
