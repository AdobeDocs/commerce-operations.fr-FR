---
title: Messages d’erreur [!DNL Upgrade Compatibility Tool]
description: En savoir plus sur les messages d’erreur que vous rencontrez lors de l’utilisation de l’ [!DNL Upgrade Compatibility Tool]  sur votre projet Adobe Commerce.
exl-id: fe4a17a9-a807-4315-b3cd-e35f34e39f6d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '4105'
ht-degree: 4%

---

# [!DNL Upgrade Compatibility Tool] des messages d’erreur

{{commerce-only}}

Cette référence de message d’erreur fournit des informations sur les erreurs qui peuvent se produire lors de l’exécution du [!DNL Upgrade Compatibility Tool].

Les messages d’erreur sont classés par niveau (problèmes critiques, erreurs et avertissements) et par type (code principal, code personnalisé et schémas GraphQL). Chaque type contient les informations suivantes :

- **Code d’erreur** : identifiant attribué par Adobe Commerce au message d’erreur.
- **Description de l’erreur** : une description qui résume la cause de l’erreur.
- **Action suggérée en cas d’erreur** : le cas échéant, fournit des conseils pour dépanner et résoudre l’erreur.

## Problèmes critiques

### Code principal

Ces erreurs sont signalées lorsque certains des fichiers principaux sont manquants ou ne correspondent pas à l’original.

| Code d’erreur | Description de l’erreur | Action suggérée |
| --- | --- | --- |
| 2001 | Fichier principal introuvable | Exécutez la commande `composer install` à partir du répertoire racine du projet. |
| 2002 | Le fichier principal a été modifié | Exécutez la commande `composer install` à partir du répertoire racine du projet. |
| 2003 | Dépendance du compositeur non installée | Une dépendance de compositeur manquante peut potentiellement entraîner des problèmes. Restaurez la dépendance en exécutant `composer require package_name`. |
| 2005 | Dossier principal introuvable | Exécutez la commande `composer install` à partir du répertoire racine du projet. |

{style="table-layout:auto"}

### Code personnalisé

Des erreurs critiques sont générées lorsque le code personnalisé référence des entités qui ne sont pas présentes dans la version Adobe Commerce cible. Ces erreurs sont également signalées lorsque des normes de codage critiques ont été rompues.

| Code d’erreur | Description de l’erreur | Action suggérée |
| --- | --- | --- |
| 1110 | Instanciation d’une classe/interface Adobe Commerce inexistante | Mettez à jour le code pour utiliser une classe marquée comme `@api`. Instanciation d’une classe/interface Adobe Commerce inexistante. |
| 1111 | Extension à partir d’une classe Adobe Commerce inexistante | La classe étendue n&#39;est plus présente dans la base de code. L’héritage n’est pas la méthode recommandée pour étendre les fonctionnalités d’Adobe Commerce. Mettez à jour le code pour utiliser une classe marquée comme `@api`. |
| 1112 | Import d’une classe Adobe Commerce inexistante | Mettez à jour le code pour utiliser une classe marquée comme `@api`. |
| 1113 | Chargement d’une classe Adobe Commerce inexistante | Mettez à jour le code pour utiliser une classe marquée comme `@api`. |
| 1114 | Utilisation d’une classe Adobe Commerce inexistante | Mettez à jour le code pour utiliser une classe marquée comme `@api`. |
| 1214 | Utilisation d’une constante Adobe Commerce inexistante | Envisagez plutôt d’introduire et d’utiliser une constante privée de la valeur requise dans le code personnalisé. |
| 1215 | Remplacement d’une constante Adobe Commerce inexistante | Envisagez plutôt d’introduire et d’utiliser une constante privée de la valeur requise dans le code personnalisé. |
| 1216 | Attribution d’une constante Adobe Commerce inexistante | Envisagez plutôt d’introduire et d’utiliser une constante privée de la valeur requise dans le code personnalisé. |
| 1312 | Interface Adobe Commerce importée inexistante | Envisagez de supprimer l’héritage ou de le remplacer par l’interface introduite dans le cadre de la personnalisation. |
| 1314 | Interface Adobe Commerce utilisée inexistante | Envisagez de supprimer l’héritage ou de le remplacer par l’interface introduite dans le cadre de la personnalisation. |
| 1317 | Interface Adobe Commerce inexistante héritée | Envisagez de supprimer l’héritage ou de le remplacer par l’interface introduite dans le cadre de la personnalisation. |
| 1318 | Interface Adobe Commerce inexistante implémentée | Envisagez de supprimer l’héritage ou de le remplacer par l’interface introduite dans le cadre de la personnalisation. |
| 1410 | Méthode Adobe Commerce d’appel inexistante | Mettez à jour le code pour utiliser une classe marquée comme `@api`. |
| 1514 | Utilisation d’une propriété Adobe Commerce inexistante | Mettez à jour le code pour utiliser une classe marquée comme `@api`. |
| 1515 | Remplacement d’une propriété Adobe Commerce inexistante | Mettez à jour le code pour utiliser une classe marquée comme `@api`. |
| 1516 | Attribution d’une propriété Adobe Commerce inexistante | Mettez à jour le code pour utiliser une classe marquée comme `@api`. Mettez à jour le niveau d’accès de la propriété sur privé s’il ne peut être utilisé que dans une seule classe. |
| 5002 | La balise PHP d&#39;ouverture doit être le premier contenu du fichier | Assurez-vous qu&#39;il n&#39;y a aucun contenu dans le fichier avant la balise PHP d&#39;ouverture. |
| 5003 | La fonction a été abandonnée | Utilisez un remplacement suggéré dans le message d’erreur. Si le message ne suggère pas de remplacement, un examen approfondi est nécessaire pour sélectionner une autre fonction ou implémentation. |
| 5005 | Erreur de syntaxe PHP | Le code doit être mis à jour pour se conformer aux normes de syntaxe PHP. |
| 5072 | Violation possible de la conception de Magento 2. Détection d’une version Magento 1.x standard | Mise à jour de la construction selon les normes Magento 2. |
| 5076 | Impossible d&#39;utiliser dans l&#39;espace de noms car il est réservé depuis PHP 7 | Remplacez le mot réservé dans l’espace de noms par un mot-clé non réservé. |
| 5077 | Impossible d&#39;utiliser comme nom de classe car il est réservé depuis PHP 7 | Remplacez le nom de classe réservé par un nom non réservé. |

{style="table-layout:auto"}

### Schéma de base de données

Les problèmes critiques de schéma de base de données sont signalés si les tables principales ou colonnes supprimées sont référencées par des contraintes personnalisées.

| Code d’erreur | Description de l’erreur | Action suggérée |
| --- | --- | --- |
| 7009 | La contrainte personnalisée référence une table principale qui a été supprimée dans la version cible | Supprimez la contrainte ou mettez à jour les attributs referenceTable et referenceColumn |
| 7010 | La contrainte personnalisée référence une colonne principale qui a été supprimée dans la version cible | Supprimez la contrainte ou mettez à jour l’attribut referenceColumn |

{style="table-layout:auto"}

### Schéma GraphQL

Les problèmes critiques liés au schéma GraphQL sont signalés si les éléments de schéma ne sont pas présents dans la version cible.

| Code d’erreur | Description de l’erreur | Action suggérée |
| --- | --- | --- |
| 3101 | Type supprimé | Répertoriez toutes les requêtes qui font référence à ce champ. Vérifiez si ces requêtes sont utilisées par l’implémentation de la personnalisation. Mettez à jour le code client pour gérer l’interface de requête modifiée. |
| 3102 | Type supprimé de l’union | Si le type d’union est utilisé dans l’implémentation de la création ou du traitement de la réponse de la requête GraphQL, il peut être nécessaire de le mettre à jour. |
| 3103 | Champ supprimé | Vérifiez si le champ est référencé dans la base de code de personnalisation. Ajustez l’implémentation pour gérer correctement le nouveau type de champ. |
| 3105 | Interface implémentée supprimée | Vérifiez si le type implémentant l’interface supprimée est utilisé dans la personnalisation. Il se peut que l’implémentation doive être mise à jour si elle repose sur l’interface supprimée. |
| 3106 | Valeur supprimée de l’énumération | Si la valeur d’énumération supprimée est utilisée dans l’implémentation de la création ou du traitement de la réponse de la requête GraphQL, elle doit peut-être être mise à jour. |
| 3107 | Argument supprimé | Vérifiez si le champ est utilisé dans la base de code de personnalisation. Supprimez l’argument de ce champ. |
| 3109 | Directive supprimée | Vérifiez si la directive est utilisée dans la base de code de personnalisation. Adapter la mise en œuvre pour supprimer la référence à la directive. |
| 3110 | Argument de directive supprimé | Vérifiez si la directive est utilisée dans la base de code de personnalisation. Supprimez l’argument de directive . |
| 3111 | Directive répétable supprimée | Vérifiez si la directive est utilisée dans la base de code de personnalisation. Ajustez l’implémentation pour gérer les modifications de l’interface. |
| 3112 | Emplacement de la directive supprimé | Vérifiez si la directive est utilisée dans la base de code de personnalisation. Ajustez l’implémentation pour gérer les modifications de l’interface. |
| 3201 | Type modifié | Répertoriez toutes les requêtes qui font référence à ce champ. Vérifiez si ces requêtes sont utilisées par l’implémentation de la personnalisation. Mettez à jour le code client pour gérer l’interface de requête modifiée. |
| 3203 | Type de modification du champ | Vérifiez si le champ est référencé dans la base de code de personnalisation. Ajustez l’implémentation pour gérer correctement le nouveau type de champ. |
| 3207 | Type d’argument modifié | Vérifiez si le champ est utilisé dans la base de code de personnalisation. Mettez à jour le type d’argument pour ce champ. |
| 3303 | Champ de saisie obligatoire ajouté | Le champ doit être ajouté à la requête si la requête, y compris ce champ, est utilisée pour la personnalisation. |
| 3307 | Argument obligatoire ajouté | Vérifiez si le champ est utilisé dans la base de code de personnalisation. Le nouvel argument requis doit être spécifié lors de l’utilisation du champ . |
| 3310 | Argument de directive obligatoire ajouté | Vérifiez si la directive est utilisée dans la base de code de personnalisation. Ajoutez l’argument directive . |

{style="table-layout:auto"}

## Erreurs

### Code personnalisé

Les erreurs de code personnalisé sont générées lorsque le code personnalisé utilise les points d’entrée d’Adobe Commerce qui ne sont pas considérés/marqués comme `@api`. Le comportement préservé de ces points d’entrée n’est pas garanti. La personnalisation doit plutôt s’appuyer sur des points d’entrée `@api`. La fonctionnalité qui repose sur un code Adobe Commerce non API doit être testée après la mise à niveau. Ces erreurs sont également signalées lorsque les principales normes de codage ont été rompues.

| Code d’erreur | Description de l’erreur | Action suggérée |
| --- | --- | --- |
| 1104 | Utilisation d’une classe non-API qui hérite de l’interface API | Les classes qui ne sont pas marquées comme `@api` peuvent être modifiées. Pensez à mettre à jour le code pour qu’il repose sur l’interface marquée comme `@api`. Dans le cas contraire, la fonctionnalité qui repose sur cette implémentation doit être testée après la mise à niveau. |
| 1121 | Extension d’à partir d’une classe d’API non Adobe Commerce | La classe étendue n&#39;est plus présente dans la base de code. L’héritage n’est pas la méthode recommandée pour étendre les fonctionnalités d’Adobe Commerce. Mettez à jour le code pour utiliser une classe marquée comme `@api`. |
| 1122 | Importation d’une classe d’API non Adobe Commerce | La classe étendue n&#39;est plus présente dans la base de code. Mettez à jour le code pour utiliser une classe marquée comme `@api`. Dans le cas contraire, la fonctionnalité qui repose sur cette implémentation doit être testée après la mise à niveau. |
| 1123 | Chargement de la classe d’API non Adobe Commerce | La classe étendue n&#39;est plus présente dans la base de code. Mettez à jour le code pour utiliser une classe marquée comme `@api`. Dans le cas contraire, la fonctionnalité qui repose sur cette implémentation doit être testée après la mise à niveau. |
| 1124 | Utilisation d’une classe d’API non Adobe Commerce | La classe étendue n&#39;est plus présente dans la base de code. Mettez à jour le code pour utiliser une classe marquée comme `@api`. Dans le cas contraire, la fonctionnalité qui repose sur cette implémentation doit être testée après la mise à niveau. |
| 1224 | Utilisation d’une constante API non Adobe Commerce | Les constantes qui ne sont pas marquées comme `@api` peuvent être modifiées. Envisagez plutôt d’introduire et d’utiliser une constante privée de la valeur requise dans le code personnalisé. |
| 1225 | Remplacement de la constante API non-Adobe Commerce | Les constantes qui ne sont pas marquées comme `@api` peuvent être modifiées. Envisagez plutôt d’introduire et d’utiliser une constante privée de la valeur requise dans le code personnalisé. |
| 1226 | Attribution d’une constante API non Adobe Commerce | Les constantes qui ne sont pas marquées comme `@api` peuvent être modifiées. Envisagez plutôt d’introduire et d’utiliser une constante privée de la valeur requise dans le code personnalisé. |
| 1322 | Interface API non Adobe Commerce importée | Les interfaces non marquées comme `@api` peuvent être modifiées. Envisagez de supprimer cet héritage ou de le remplacer par un héritage à partir de l’interface d’Adobe Commerce marquée comme `@api` ou d’une interface introduite dans la portée du code de personnalisation. |
| 1324 | Interface d’API non Adobe Commerce utilisée | Les interfaces non marquées comme `@api` peuvent être modifiées. Envisagez de supprimer cet héritage ou de le remplacer par un héritage à partir de l’interface d’Adobe Commerce marquée comme `@api` ou d’une interface introduite dans la portée du code de personnalisation. |
| 1327 | Interface d’API non Adobe Commerce héritée | Les constantes qui ne sont pas marquées comme `@api` peuvent être modifiées. Envisagez plutôt d’introduire et d’utiliser une constante privée de la valeur requise dans le code personnalisé. |
| 1328 | Interface d’API non Adobe Commerce implémentée | Les interfaces non marquées comme `@api` peuvent être modifiées. Envisagez de supprimer cet héritage ou de le remplacer par un héritage à partir de l’interface d’Adobe Commerce marquée comme `@api` ou d’une interface introduite dans la portée du code de personnalisation. |
| 1420 | Instancier la classe/l’interface de l’API non Adobe Commerce | Les classes qui ne sont pas marquées comme `@api` peuvent être modifiées. Pensez à mettre à jour le code pour qu’il repose sur l’interface marquée comme `@api`. Dans le cas contraire, la fonctionnalité qui repose sur cette implémentation doit être testée après la mise à niveau. En outre, la méthode recommandée pour récupérer une instance de la classe consiste à utiliser ID. Envisagez d’utiliser une fabrique si une nouvelle instance de la classe est requise. |
| 1428 | Dépendance possible des détails de mise en œuvre. | Les classes qui ne sont pas marquées comme `@api` peuvent être modifiées. Pensez à mettre à jour le code pour qu’il repose sur l’interface marquée comme `@api`. Dans le cas contraire, la fonctionnalité qui repose sur cette implémentation doit être testée après la mise à niveau. |
| 1429 | Appeler les méthodes d’API non Adobe Commerce | Les méthodes qui ne sont pas marquées comme `@api` ou qui ne sont pas déclarées dans la classe/l’interface de l’API peuvent être modifiées. Même si l’interface de la méthode n’est pas mise à jour dans la nouvelle version, son comportement ou sa sortie peuvent être différents. Envisagez d’utiliser une méthode d’interface. Dans le cas contraire, la fonctionnalité qui repose sur cette implémentation doit être testée après la mise à niveau. |
| 1449 | Appel à la méthode hors interface (présente dans l’implémentation) | Les méthodes qui ne sont pas déclarées dans l’interface peuvent être modifiées. Envisagez d’utiliser une méthode d’interface. Dans le cas contraire, la fonctionnalité qui repose sur cette implémentation doit être testée après la mise à niveau. |
| 1524 | Utilisation d’une propriété d’API non Adobe Commerce | Les valeurs des propriétés qui ne sont pas marquées comme `@api` peuvent être modifiées. Envisagez plutôt la méthode de l’interface API . |
| 1525 | Remplacement de la propriété d’API non-Adobe Commerce | Les valeurs des propriétés qui ne sont pas marquées comme `@api` peuvent être modifiées. Envisagez plutôt la méthode de l’interface API . |
| 1526 | Attribution d’une propriété d’API non Adobe Commerce | Les valeurs des propriétés qui ne sont pas marquées comme `@api` peuvent être modifiées. Envisagez plutôt la méthode de l’interface API . |
| 5004 | La fonction sans argument a été abandonnée | Transmettez l’entrée à valider comme premier argument de la fonction . |
| 5007 | L&#39;utilisation de certaines fonctions est découragée | Évitez d’utiliser ces fonctions. |
| 5009 | Les directives de modèle ne peuvent pas appeler de méthodes. Seul l’accès au tableau scalaire est autorisé. | Supprimez les appels de méthode du modèle. |
| 5010 | Le modèle `@vars` le bloc de commentaires contient un fichier JSON non valide. | Correction d’un fichier JSON non valide. |
| 5011 | Le modèle `@vars` le bloc de commentaire contient un libellé non valide. | Correction d’un libellé non valide. |
| 5012 | Il manque une variable utilisée dans le modèle `@vars` le bloc de commentaire | Ajoutez la variable manquante @vars bloc de commentaires. |
| 5013 | Évitez d’utiliser une balise à fermeture automatique avec un élément HTML non vide | Utilisez plutôt la balise close . |
| 5014 | L’attribut `"active"` est obsolète | La liste des modules actifs est définie dans la configuration du déploiement. |
| 5015 | Le nœud `<param>` est obsolète | Utilisez `<argument name="..." xsi:type="...">` à la place. |
| 5016 | Le nœud `<instance>` est obsolète | Utilisez `<argument name="..." xsi:type="object">` à la place. |
| 5017 | Le nœud `<array>` est obsolète | Utilisez `<argument name="..." xsi:type="array">` à la place. |
| 5018 | Le nœud `<item key="...">` est obsolète | Utilisez `<item name="..." xsi:type="...">` à la place. |
| 5019 | Le nœud `<value>` est obsolète | Indiquez plutôt la valeur réelle sous la forme d’un littéral de texte. |
| 5020 | Nœud obsolète : `<supported_blocks>` | À remplacer par `<supported_containers>`. |
| 5021 | Nœud obsolète : `<block_name>` | À remplacer par `<container_name>`. |
| 5022 | Nom d’usine détecté | Le type de widget ne doit pas commencer par /. |
| 5023 | Structure de liste de contrôle d’accès obsolète détectée en ligne | Vérifiez lib/internal/Magento/Framework/Acl/etc/acl.xsd. |
| 5024 | Structure de menu obsolète détectée en ligne | Vérifiez app/code/Magento/Backend/etc/menu.xsd. |
| 5025 | Structure de configuration système obsolète détectée dans le fichier | Vérifiez app/code/Magento/Config/etc/system_file.xsd. |
| 5026 | Ne pas utiliser l’attribut de type `"text/javascript"` | Utilisez uniquement des membres publics. |
| 5028 | L&#39;accès aux membres protégés et privés de `Block` classe est obsolète dans les modèles phtml | Utilisez uniquement des membres publics. |
| 5031 | Contient une méthode obsolète | Utilisez plutôt `getConnection()` méthode . |
| 5042 | Format incorrect de la référence de classe PHP | Vérifiez que la classe est référencée uniquement à l’aide de lettres CamelCased, de chiffres et sans barre oblique. |
| 5043 | Format incorrect de la référence du module | Vérifiez que le module est référencé uniquement à l’aide de lettres, de chiffres, de traits de soulignement et sans barre oblique. |
| 5044 | La classe `Zend_Db_Select` est restreinte | Remplacement suggéré : `\Magento\Framework\DB\Select`. |
| 5045 | La classe `Zend_Db_Adapter_Pdo_Mysql` est restreinte | Remplacement suggéré : `\Magento\Framework\DB\Adapter\Pdo\Mysql`. |
| 5046 | La classe `Magento\Framework\Serialize\Serializer\Serialize` est restreinte | Remplacement suggéré : `Magento\Framework\Serialize\SerializerInterface`. |
| 5047 | La classe `ArrayObject` est restreinte | Remplacement suggéré : classe personnalisée, étendue à partir de `ArrayObject` avec des méthodes serialize/unserialize remplacées. |
| 5048 | La classe `Magento\Framework\View\Element\UiComponent\ArrayObjectFactory` est restreinte | Remplacement suggéré : usine qui crée une classe personnalisée, étendue à partir de `ArrayObject` avec des méthodes serialize/unserialize écrasées. |
| 5050 | Le bloc référencé est supprimé | Supprimez la référence au bloc . |
| 5051 | `output="toHtml"` est obsolète | Utilisez `output="1"`. |
| 5052 | La classe `\Magento\Framework\View\Element\Text\ListText` n’est plus censée être utilisée dans la disposition | Supprimez le `\Magento\Framework\View\Element\Text\ListText` de classe de la mise en page. |
| 5053 | L’appel de la méthode via l’instruction de mise en page `<action>` n’est pas autorisé | Évitez d’utiliser une méthode offensante dans `<action>`. |
| 5054 | `helper` attribut contient `/` | Supprimez `/` de l’attribut d’assistance . |
| 5055 | `helper` attribut ne contient pas `::` | Ajoutez `::` à l’attribut d’assistance . |
| 5056 | Les scripts d’installation sont obsolètes. | Utilisez l’approche de schéma déclaratif dans le fichier etc/db_schema.xml du module\. |
| 5057 | Les scripts InstallSchema sont obsolètes | Utilisez l’approche de schéma déclaratif dans le fichier etc/db_schema.xml du module\. |
| 5058 | Les scripts InstallData sont obsolètes | Utilisez l’approche des correctifs de données dans le répertoire Setup/Patch/Data du module. |
| 5059 | Les scripts d’installation sont obsolètes. | Créez une classe InstallData dans le dossier Setup du module\. |
| 5060 | Les scripts de mise à niveau sont obsolètes. | Utilisez l’approche de schéma déclaratif dans le fichier etc/db_schema.xml du module\. |
| 5061 | Les scripts UpgradeSchema sont obsolètes. | Utilisez l’approche de schéma déclaratif dans le fichier etc/db_schema.xml du module\. |
| 5062 | Les scripts UpgradeData sont obsolètes | Utilisez l’approche des correctifs de données dans le répertoire Setup/Patch/Data du module. |
| 5063 | Les scripts de mise à niveau sont obsolètes. | Utilisez l’approche des correctifs de données dans le répertoire Setup/Patch/Data du module. |
| 5064 | Les scripts périodiques sont obsolètes | Créez une classe récurrente dans le dossier Setup du module\. |
| 5065 | &#39;data&#39; se trouve dans un répertoire non valide | Créez un correctif de données dans le dossier Setup/Patch/Data du module pour les mises à niveau de données ou utilisez l’approche de schéma déclaratif dans le fichier etc/db_schema.xml du module pour les modifications de schéma. |
| 5066 | &#39;sql&#39; se trouve dans un répertoire non valide | Créez un correctif de données dans le dossier Setup/Patch/Data du module pour les mises à niveau de données ou utilisez l’approche de schéma déclaratif dans le fichier etc/db_schema.xml du module pour les modifications de schéma. |
| 5067 | Les nœuds identifiés par XPath sont obsolètes | Le XML obsolète signalé dans l’erreur doit être mis à jour. Suivez les suggestions du message d’erreur. |
| 5068 | La directive `{{htmlescape}}` est obsolète | Utilisez `{{var}}` à la place. |
| 5069 | La directive `{{escapehtml}}` est obsolète | Utilisez `{{var}}` à la place. |
| 5070 | Le troisième paramètre n’est plus nécessaire pour `getChildHtml()` | Supprimez le troisième paramètre de l’appel à `getChildHtml()`. |
| 5071 | Le quatrième paramètre n’est plus nécessaire pour `getChildHtml()` | Supprimez le 4e paramètre de l’appel à `getChildHtml()`. |
| 5073 | Les noms de table hérités avec une barre oblique doivent être corrigés pour les noms de table directs | Utilisez plutôt le nom direct de la table. |
| 5075 | Les modules d’application ne doivent pas utiliser les classes des modules de test | Supprimez l’utilisation des classes des modules de test. |
| 5078 | La classe doit être demandée dans le constructeur, sinon le compilateur ne pourra pas trouver et générer ces classes | Ajoutez la classe au constructeur . |
| 5079 | L’utilisation de variables de classe var est déconseillée | Évitez d&#39;utiliser &#39;var&#39; pour déclarer une variable de classe. |
| 5080 | Instruction SQL brute possible détectée | Utilisez plutôt des référentiels ou des correctifs de données. |
| 5081 | L’utilisation d’assistants dans les modèles est découragée | Utilisez plutôt ViewModel . |
| 5082 | L’utilisation de $this dans les modèles est obsolète | Utilisez $block à la place. |
| 5083 | Les constantes ne sont pas autorisées comme premier argument de la fonction de traduction | Utilisez plutôt un littéral de chaîne. |
| 5085 | L&#39;utilisation de certaines fonctions est découragée | Utilisez plutôt la fonction alternative indiquée dans le message. |
| 5087 | Problème de compatibilité PHP entre versions | Suivez les suggestions du message et vérifiez le [guide de migration](https://www.php.net/manual/en/migration81.php). |
| 5088 | Paramètres facultatifs trouvés après les paramètres obligatoires | Déplacer les paramètres obligatoires après les paramètres facultatifs. |
| 5089 | Visibilité de la méthode `final private` | Modifiez la visibilité de la méthode de `final private` en `private` uniquement. |
| 5090 | La méthode magique `__set_state` n’est pas définie comme `static` | La méthode magique `__set_state` doit être définie comme `static`. |
| 5091 | Classe avec méthode `__toString()` n’héritant pas de l’interface `Stringable` | Ajoutez `Stringable` interface à la classe avec la méthode `__toString()`. |
| 5092 | `is_resource()` méthode utilisée pour les fonctions qui renvoient désormais Object | Remplacez `is_resource()` par `instanceof` objet . |
| 6001 | `jQuery.andSelf()` supprimé | Utilisez `jQuery.addBack()`. |
| 6002 | Les `$.bind` et `$.unbind` jQuery sont obsolètes | Utilisez `$.on` et `$.off` à la place. |
| 6003 | La méthode jQuery pour s’abonner à un événement est obsolète et ne doit pas être utilisée | Utilisez plutôt `.on("event name", fn)` méthode pour vous abonner à cet événement. |
| 6003 | La méthode jQuery pour déclencher l’événement est obsolète et ne doit pas être utilisée | Utilisez plutôt `.trigger("event name")` méthode pour déclencher cet événement. |
| 6004 | Les `$.delegate` et `$.undelegate` jQuery sont obsolètes | Utilisez `$.on` et `$.off` à la place. |
| 6005 | (`jQuery.load()` / `jQuery.unload()` / `jQuery.error()`) a été supprimé | Utilisez (`.on("load", fn)` / `.on("unload", fn)` / `.on("error", fn)`) à la place. |
| 6006 | `jQuery.size()` supprimé | Utilisez `jQuery.length`. |
| 6007 | `jQuery.trim` est obsolète | Utilisez `String.prototype.trim`. |
| 6008 | (`addButton`, `addContextToolbar`, `addMenuItem`, `addSidebar`, `file_browser_callback`, `insert_button_items`, thème « inlite », thème « mobile », thème « moderne ») est supprimé | Mettez à jour le code pour qu’il soit compatible avec tinymce5. |
| 6009 | `jQuery.isFunction()` est obsolète | Dans la plupart des cas, il peut être remplacé par [type de x === « fonction »]. |
| 6009 | `jQuery.type()` est obsolète | Remplacez par une vérification de type appropriée comme [type de x === « fonction »]. |
| 6009 | `jQuery.isArray()` est obsolète | Utilisez plutôt la méthode native Array.isArray . |
| 6009 | `jQuery.parseJSON()` est obsolète | Pour analyser les chaînes JSON, utilisez plutôt la méthode JSON.parse native. |
| 6010 | (`jQuery.expr[":"]`, `jQuery.expr.filters`) est obsolète | Utilisez plutôt jQuery.expr.pseudos . |

{style="table-layout:auto"}

### Schéma de base de données

Les erreurs de schéma de base de données sont générées si les tables, colonnes, index ou contraintes de la base de données, ajoutés ou supprimés dans la version Adobe Commerce cible, peuvent entraîner des conflits avec le schéma de base de données personnalisé.

| Code d’erreur | Description de l’erreur | Action suggérée |
| --- | --- | --- |
| 7001 | La version principale de Target introduit une table portant le même nom qu&#39;une table déclarée par un module personnalisé | Utilisez la nouvelle table principale (le cas échéant) ou renommez la table personnalisée |
| 7002 | La table principale étendue par un module personnalisé a été supprimée dans la version cible | Toutes les références de table de base supprimées doivent être supprimées de la base de code |
| 7003 | La version principale de Target introduit une colonne portant le même nom qu’une colonne déclarée par un module personnalisé | Utilisez la nouvelle colonne principale (le cas échéant) ou renommez la colonne personnalisée |
| 7004 | La colonne principale étendue par un module personnalisé a été supprimée dans la version cible | Toutes les références de colonnes de base supprimées doivent être supprimées de la base de code |
| 7005 | La version principale cible introduit un index avec le même referenceId qu’un index déclaré par un module personnalisé | Supprimer (s’il existe un doublon de l’index principal introduit) ou renommer l’index personnalisé |
| 7006 | L’index principal étendu par un module personnalisé a été supprimé dans la version cible | Toutes les références d’index de base supprimées doivent être supprimées de la base de code |
| 7007 | La version principale cible introduit une contrainte portant le même nom qu’une contrainte déclarée par un module personnalisé | Supprimer (si elle est dupliquée dans la contrainte de base introduite) ou renommer la contrainte personnalisée |
| 7008 | La contrainte principale étendue par un module personnalisé a été supprimée dans la version cible | Utilisez la nouvelle contrainte principale (le cas échéant) ou renommez la contrainte personnalisée |

{style="table-layout:auto"}

## Avertissements

### Code principal

Ces avertissements sont signalés lorsqu’il existe des incohérences mineures dans la base de code principale.

| Code d’erreur | Description de l’erreur | Action suggérée |
| --- | --- | --- |
| 2004 | Incompatibilité de version de dépendance du compositeur | Le problème indique que la version de dépendance du compositeur dans l’étalon et le projet réel est différente. Mettez à jour la dépendance en exécutant `composer update <package_name>`. |

{style="table-layout:auto"}

### Code personnalisé

Des avertissements de code personnalisé sont générés lorsque des références à du code obsolète sont détectées. Ces références doivent être remplacées par les points d’extension pris en charge. Pour obtenir des recommandations, prêtez attention à l’annotation `@see` de l’élément obsolète . Ces erreurs sont également signalées lorsque des normes de codage mineures ont été rompues.

| Code d’erreur | Description de l’erreur | Action suggérée |
| --- | --- | --- |
| 1131 | Extension d’à partir de la classe ``@deprecated`` d’Adobe Commerce | La classe étendue sera supprimée dans les versions à venir. L’héritage n’est pas la méthode recommandée pour étendre les fonctionnalités d’Adobe Commerce. Mettez à jour le code pour utiliser une classe marquée comme `@api`. |
| 1132 | Importation d’une classe de `@deprecated` Adobe Commerce | La classe étendue sera supprimée dans les versions à venir. Envisagez plutôt d’utiliser une classe Adobe Commerce marquée comme `@api`. |
| 1133 | Chargement de la classe `@deprecated` d’Adobe Commerce | La classe étendue sera supprimée dans les versions à venir. Envisagez plutôt d’utiliser une classe Adobe Commerce marquée comme `@api`. |
| 1134 | Utilisation de la classe `@deprecated` d’Adobe Commerce | La classe étendue sera supprimée dans les versions à venir. Envisagez plutôt d’utiliser une classe Adobe Commerce marquée comme `@api`. |
| 1234 | Utilisation de la constante `@deprecated` d’Adobe Commerce | La constante obsolète sera supprimée dans les versions à venir. Envisagez plutôt d’utiliser une constante marquée comme `@api` ou une constante privée dans votre implémentation . |
| 1235 | Remplacement de la constante `@deprecated` d’Adobe Commerce | La constante obsolète sera supprimée dans les versions à venir. Envisagez plutôt d’utiliser une constante marquée comme `@api` ou une constante privée dans votre implémentation . |
| 1236 | Attribution d’une constante de `@deprecated` Adobe Commerce | La constante obsolète sera supprimée dans les versions à venir. Envisagez plutôt d’utiliser une constante marquée comme `@api` ou une constante privée dans votre implémentation . |
| 1332 | Interface Adobe Commerce `@deprecated` importée | L’interface obsolète sera supprimée dans les versions à venir. Envisagez plutôt d’utiliser une interface ou une classe marquée comme `@api`. |
| 1334 | Interface `@deprecated` Adobe Commerce utilisée | L’interface obsolète sera supprimée dans les versions à venir. Envisagez plutôt d’utiliser une interface ou une classe marquée comme `@api`. |
| 1337 | Hérité de l’interface `@deprecated` d’Adobe Commerce | L’interface obsolète sera supprimée dans les versions à venir. Envisagez de supprimer l’héritage de l’interface en utilisant une interface marquée comme `@api` ou une interface introduite dans votre implémentation à la place. |
| 1338 | Interface `@deprecated` Adobe Commerce implémentée | L’interface obsolète sera supprimée dans les versions à venir. Envisagez de supprimer l’héritage de l’interface en utilisant une interface marquée comme `@api` ou une interface introduite dans votre implémentation à la place. |
| 1430 | Appel non déclaré méthode dataobject | Les méthodes magiques qui ne sont pas déclarées peuvent être modifiées. Envisagez plutôt des méthodes d’interface . |
| 1439 | Méthode de `@deprecated` Call Adobe Commerce | La méthode obsolète sera supprimée dans les versions à venir. Envisagez plutôt de vous fier à des méthodes déclarées dans les interfaces API. |
| 1440 | Incompatibilité de signature de méthode | Un appel ou un remplacement de la méthode principale est détecté avec des paramètres, des arguments ou un type de retour qui ne correspond pas à la signature de la méthode. |
| 1534 | Utilisation de la propriété `@deprecated` d’Adobe Commerce | La méthode obsolète sera supprimée dans les versions à venir. Envisagez plutôt de vous fier à des méthodes déclarées dans les interfaces API. |
| 1535 | Remplacement de la propriété Adobe Commerce `@deprecated` | La propriété obsolète sera supprimée dans les versions à venir. Envisagez plutôt de vous fier à des méthodes déclarées dans les interfaces API ou d’utiliser une propriété privée dans votre implémentation . |
| 1536 | Attribution d’une propriété de `@deprecated` Adobe Commerce | La méthode obsolète sera supprimée dans les versions à venir. Envisagez plutôt de vous fier à des méthodes déclarées dans les interfaces API. |
| 5006 | Les proxys et les intercepteurs NE DOIVENT jamais être explicitement demandés dans les constructeurs | La classe d’origine doit être déclarée en tant que type du paramètre du constructeur. La classe Intercepteur/Proxy sera transmise par l’implémentation de l’injection de dépendance de framework. |
| 5074 | Utilisation de la méthode obsolète `getResource()` pour (enregistrer / charger / supprimer) les données détectées. | Utilisez plutôt un référentiel. |
| 5086 | La visibilité n&#39;est pas déclarée sur une constante | Déclarez la visibilité sur toutes les constantes. |

{style="table-layout:auto"}

### Schéma GraphQL

Les avertissements relatifs au schéma GraphQL sont générés lorsque des éléments supplémentaires sont ajoutés au schéma dans la nouvelle version. Il est recommandé de passer en revue la mise en œuvre pour voir si elles doivent être utilisées pour les requêtes.

| Code d’erreur | Description de l’erreur | Action suggérée |
| --- | --- | --- |
| 3206 | Valeur par défaut de l’argument modifiée | Si la requête est utilisée dans la personnalisation, la valeur de l’argument doit peut-être être spécifiée explicitement. |
| 3302 | Type ajouté à l’union | Le type a été ajouté à l’union. Vérifiez l’implémentation qui traite le résultat de la requête qui renvoie ce type d’union et assurez-vous qu’elle est en mesure de gérer le type ajouté. |
| 3304 | Champ de saisie facultatif ajouté | Champ de saisie facultatif ajouté. Vérifiez l’implémentation pour vous assurer que . |
| 3305 | Interface implémentée ajoutée | Le champ peut accepter/fournir des informations supplémentaires qui peuvent être prises en compte dans la mise en œuvre. |
| 3306 | Valeur ajoutée à l’énumération | Une valeur a été ajoutée à une énumération. Si les clients contiennent une instruction switch sur la valeur de l’énumération et n’incluent pas de cas par défaut, cette modification peut entraîner un comportement inattendu. |
| 3308 | Argument facultatif ajouté | Si la requête utilise un nouvel argument dans la personnalisation, il se peut qu’elle doive être ajoutée à la requête. |

{style="table-layout:auto"}
