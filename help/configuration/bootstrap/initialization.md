---
title: Initialisation de l’application et amorçage
description: Découvrez la logique d’initialisation et de bootstrap de l’application Commerce.
feature: Configuration, Install, Media
exl-id: 46d1ffc0-7870-4dd1-beec-0a9ff858ab62
source-git-commit: 403a5937561d82b02fd126c95af3f70b0ded0747
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 0%

---

# Présentation de l’initialisation et de l’amorçage

Pour exécuter l’application Commerce, les actions suivantes sont implémentées dans [pub/index.php][index] :

- Insérez [app/bootstrap.php][bootinitial], qui effectue des routines d’initialisation essentielles telles que la gestion des erreurs, l’initialisation du chargeur automatique, la définition des options de profilage et la définition du fuseau horaire par défaut.
- Créez une instance de [\Magento\Framework\App\Bootstrap.php][bootstrap] <!-- It requires initialization parameters to be specified in constructor. Normally, the $_SERVER super-global variable is supposed to be passed there. -->
- Créez une instance d’application Commerce : [\Magento\Framework\AppInterface][app-face]
- Exécuter Commerce

## Logique d’exécution du Bootstrap

[L’objet bootstrap][bootinitial] utilise l’algorithme suivant pour exécuter l’application Commerce :

1. Initialise le gestionnaire d’erreurs.
1. Crée le [gestionnaire d’objets][object] et les services partagés de base qui sont utilisés partout et qui sont affectés par l’environnement. Les paramètres d’environnement sont correctement injectés dans ces objets.
1. Affirme que le mode de maintenance _n’est pas_ activé ; dans le cas contraire, il s’arrête.
1. Affirme que l’application Commerce est installée ; dans le cas contraire, elle s’arrête.
1. Démarre l’application Commerce.

   Toute exception non interceptée au lancement de l’application est automatiquement retransmise à Commerce dans la méthode `catchException()` que vous pouvez utiliser pour gérer l’exception. Ce dernier doit renvoyer `true` ou `false` :

   - Si `true` : Commerce a géré l’exception avec succès. Pas besoin de faire quoi que ce soit d&#39;autre.
   - Si `false` : (ou tout autre résultat vide) Commerce ne gérait pas l’exception. L’objet bootstrap exécute la sous-routine de gestion des exceptions par défaut.

1. Envoie la réponse fournie par l’objet d’application.

   >[!INFO]
   >
   >Les assertions que l’application Commerce est installée et non en mode de maintenance sont le comportement par défaut de la classe `\Magento\Framework\App\Bootstrap`. Vous pouvez le modifier à l’aide d’un script de point d’entrée lors de la création de l’objet bootstrap.

   Exemple de script de point d’entrée qui modifie l’objet bootstrap :

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

L’objet bootstrap indique comment l’application Commerce gère les exceptions non interceptées comme suit :

- En [mode développeur](../bootstrap/application-modes.md#developer-mode), affiche l’exception en l’état.
- Dans tout autre mode, tente de consigner une exception et d’afficher un message d’erreur générique.
- Arrête Commerce avec le code d’erreur `1`

## Applications de point d’entrée

Nous disposons des applications de point d’entrée suivantes (c’est-à-dire, des applications définies par Commerce qui sont utilisées par le serveur web comme index de répertoire) :

### Point d’entrée HTTP

[\Magento\Framework\App\Http][http] fonctionne comme suit :

1. Détermine la [zone d’application](https://developer.adobe.com/commerce/php/architecture/modules/areas/).
1. Démarre le contrôleur frontal et les systèmes de routage afin de trouver et d’exécuter une action de contrôleur.
1. Utilise un objet de réponse HTTP pour renvoyer le résultat obtenu à partir de l’action du contrôleur.
1. Gestion des erreurs (dans l’ordre de priorité suivant) :

   1. Si vous utilisez le [mode développeur](../bootstrap/application-modes.md#developer-mode) :
      - Si l’application Commerce n’est pas installée, redirigez-vous vers l’assistant de configuration.
      - Si l’application Commerce est installée, affichez une erreur et un code d’état HTTP 500 (Erreur interne du serveur).
   1. Si l’application Commerce est en mode de maintenance, affichez une landing page &quot;Service non disponible&quot; conviviale avec le code d’état HTTP 503 (Service non disponible).
   1. Si l’application Commerce n’est _pas_ installée, redirigez-vous vers l’assistant de configuration.
   1. Si la session n’est pas valide, redirigez-vous vers la page d’accueil.
   1. En cas d’erreur d’initialisation d’une autre application, affichez une page conviviale &quot;Page introuvable&quot; avec le code d’état HTTP 404 (introuvable).
   1. Pour toute autre erreur, affichez une page conviviale &quot;Service indisponible&quot; avec la réponse HTTP 503, générez un rapport d’erreur et affichez son identifiant sur la page.

### Point d’entrée de ressource statique

[\Magento\Framework\App\StaticResource][static-resource] est une application permettant de récupérer des ressources statiques (par exemple, CSS, JavaScript et images). Les actions comportant une ressource statique sont reportées jusqu’à ce que la ressource soit demandée.

>[!INFO]
>
>Le point d’entrée pour les fichiers d’affichage statique n’est pas utilisé dans le [mode de production](application-modes.md#production-mode) pour éviter toute attaque potentielle sur le serveur. En mode de production, l’application Commerce s’attend à ce que toutes les ressources nécessaires existent dans le répertoire `<your Commerce install dir>/pub/static`.

En mode développeur ou par défaut, une requête pour une ressource statique inexistante est redirigée vers le point d’entrée statique conformément aux règles de réécriture spécifiées par le `.htaccess` approprié.
Lorsque la requête est redirigée vers le point d’entrée, l’application Commerce analyse l’URL demandée en fonction des paramètres récupérés et trouve la ressource demandée.

- En mode [développeur](application-modes.md#developer-mode), le contenu du fichier est renvoyé de sorte que chaque fois que la ressource est demandée, le contenu renvoyé est à jour.
- En mode [default](application-modes.md#default-mode) , la ressource récupérée est publiée afin d’être accessible par l’URL demandée précédemment.

  Toutes les futures demandes de la ressource statique sont traitées par le serveur de la même manière que les fichiers statiques, c’est-à-dire sans impliquer le point d’entrée. S’il est nécessaire de synchroniser les fichiers publiés avec les fichiers d’origine, le répertoire `pub/static` doit être supprimé. Par conséquent, les fichiers sont automatiquement republiés avec la requête suivante.

### Point d’entrée de la ressource multimédia

[Magento\MediaStorage\App\Media][media] récupère des ressources multimédias (c’est-à-dire tout fichier téléchargé dans le stockage multimédia) à partir de la base de données. Il est utilisé chaque fois que la base de données est configurée comme un stockage multimédia.

`\Magento\Core\App\Media` tente de trouver le fichier multimédia dans le stockage de base de données configuré et de l’écrire dans le répertoire `pub/static`, puis renvoie son contenu. En cas d’erreur, il renvoie un code d’état HTTP 404 (Not Found) dans l’en-tête sans contenu.

<!-- Link Definitions -->

[app-face]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/AppInterface.php
[bootinitial]: https://github.com/magento/magento2/tree/2.4/app/bootstrap.php
[bootstrap]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Bootstrap.php
[http]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Http
[index]: https://github.com/magento/magento2/tree/2.4/pub/index.php
[media]: https://github.com/magento/magento2/tree/2.4/app/code/Magento/MediaStorage/App/Media.php
[object]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/ObjectManager
[static-resource]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/StaticResource.php
