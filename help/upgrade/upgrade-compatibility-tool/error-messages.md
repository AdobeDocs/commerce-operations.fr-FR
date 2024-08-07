---
title: '[!DNL Upgrade Compatibility Tool] Messages d’erreur'
description: En savoir plus sur les messages d’erreur que vous rencontrez lors de l’utilisation de  [!DNL Upgrade Compatibility Tool]  sur votre projet Adobe Commerce.
exl-id: fe4a17a9-a807-4315-b3cd-e35f34e39f6d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '4105'
ht-degree: 4%

---

# [!DNL Upgrade Compatibility Tool] messages d’erreur

{{commerce-only}}

Cette référence de message d’erreur fournit des informations sur les erreurs qui peuvent se produire lors de l’exécution de [!DNL Upgrade Compatibility Tool].

Les messages d’erreur sont classés par niveau (problèmes critiques, erreurs et avertissements) et par type (code principal, code personnalisé et schémas GraphQL). Chaque type contient les informations suivantes :

- **Code d’erreur** : identifiant attribué par Adobe Commerce au message d’erreur.
- **Description de l’erreur** : description qui résume la cause de l’erreur.
- **Action suggérée par l’erreur** : le cas échéant, fournit des conseils pour dépanner et résoudre l’erreur.

## Problèmes critiques

### Code principal

Ces erreurs sont signalées lorsque certains fichiers principaux sont manquants ou ne correspondent pas à l’original.

| Code d’erreur | Description de l’erreur | Action suggérée |
| --- | --- | --- |
| 2001 | Fichier principal introuvable | Exécutez la commande `composer install` à partir du répertoire racine du projet. |
| 2002 | Le fichier principal a été modifié. | Exécutez la commande `composer install` à partir du répertoire racine du projet. |
| 2003 | La dépendance du compositeur n’est pas installée | Une dépendance de compositeur manquante peut entraîner des problèmes. Restaurez la dépendance en exécutant `composer require package_name`. |
| 2005 | Le dossier principal est introuvable | Exécutez la commande `composer install` à partir du répertoire racine du projet. |

{style="table-layout:auto"}

### Code personnalisé

Des erreurs critiques sont générées lorsque le code personnalisé fait référence à des entités qui ne sont pas présentes dans la version cible d’Adobe Commerce. Ces erreurs sont également signalées lorsque les normes de codage critiques ont été rompues.

| Code d’erreur | Description de l’erreur | Action suggérée |
| --- | --- | --- |
| 1110 | Instanciation d’une classe/interface Adobe Commerce inexistante | Mettez à jour le code pour utiliser une classe marquée comme `@api`. Instanciation d’une classe/interface Adobe Commerce inexistante. |
| 1111 | Extension à partir d’une classe Adobe Commerce inexistante | La classe étendue n’est plus présente dans le code base. L’héritage n’est pas la méthode recommandée pour étendre les fonctionnalités d’Adobe Commerce. Mettez à jour le code pour utiliser une classe marquée comme `@api`. |
| 1112 | Importation d’une classe Adobe Commerce inexistante | Mettez à jour le code pour utiliser une classe marquée comme `@api`. |
| 1113 | Chargement d’une classe Adobe Commerce inexistante | Mettez à jour le code pour utiliser une classe marquée comme `@api`. |
| 1114 | Utilisation d’une classe Adobe Commerce inexistante | Mettez à jour le code pour utiliser une classe marquée comme `@api`. |
| 1214 | Utiliser la constante Adobe Commerce inexistante | Envisagez plutôt d’introduire et d’utiliser une constante privée de la valeur requise dans le code personnalisé. |
| 1215 | Remplacer la constante Adobe Commerce inexistante | Envisagez plutôt d’introduire et d’utiliser une constante privée de la valeur requise dans le code personnalisé. |
| 1216 | Assignation de la constante Adobe Commerce inexistante | Envisagez plutôt d’introduire et d’utiliser une constante privée de la valeur requise dans le code personnalisé. |
| 1312 | Interface Adobe Commerce non existante importée | Envisagez de supprimer l’héritage ou de le remplacer par l’interface introduite dans la portée de la personnalisation. |
| 1314 | Utilisation d’une interface Adobe Commerce inexistante | Envisagez de supprimer l’héritage ou de le remplacer par l’interface introduite dans la portée de la personnalisation. |
| 1317 | Interface Adobe Commerce héritée et inexistante | Envisagez de supprimer l’héritage ou de le remplacer par l’interface introduite dans la portée de la personnalisation. |
| 1318 | Mise en oeuvre d’une interface Adobe Commerce inexistante | Envisagez de supprimer l’héritage ou de le remplacer par l’interface introduite dans la portée de la personnalisation. |
| 1410 | Appel d’une méthode Adobe Commerce inexistante | Mettez à jour le code pour utiliser une classe marquée comme `@api`. |
| 1514 | Utilisation d’une propriété Adobe Commerce inexistante | Mettez à jour le code pour utiliser une classe marquée comme `@api`. |
| 1515 | Remplacement d’une propriété Adobe Commerce inexistante | Mettez à jour le code pour utiliser une classe marquée comme `@api`. |
| 1516 | Attribution d’une propriété Adobe Commerce inexistante | Mettez à jour le code pour utiliser une classe marquée comme `@api`. Mettez à jour le niveau d’accès aux propriétés sur private s’il peut être utilisé dans une seule classe. |
| 5002 | La balise PHP d’ouverture doit être le premier contenu du fichier . | Assurez-vous qu’il n’y a aucun contenu dans le fichier avant la balise d’ouverture PHP. |
| 5003 | Fonction obsolète | Utilisez un remplacement suggéré dans le message d’erreur. Si le message ne suggère pas de remplacement, une révision approfondie est nécessaire pour sélectionner une autre fonction ou implémentation. |
| 5005 | Erreur de syntaxe PHP | Le code doit être mis à jour pour être conforme aux normes de syntaxe PHP. |
| 5072 | Violation de conception du Magento 2 possible. Détection d’une construction Magento 1.x classique | Mettre à jour la construction vers les normes Magento 2. |
| 5076 | Impossible d’utiliser dans l’espace de noms, car il est réservé depuis PHP 7 | Remplacez le mot réservé dans l’espace de noms par un mot-clé non réservé. |
| 5077 | Ne peut pas utiliser comme nom de classe, car il est réservé depuis PHP 7 | Remplacez le nom de classe réservé par un nom non réservé. |

{style="table-layout:auto"}

### Schéma DB

Les problèmes critiques liés au schéma de base de données sont signalés si les tables ou colonnes principales supprimées sont référencées par des contraintes personnalisées.

| Code d’erreur | Description de l’erreur | Action suggérée |
| --- | --- | --- |
| 7009 | La contrainte personnalisée fait référence à une table principale qui a été supprimée de la version cible. | Suppression des attributs de contrainte ou de mise à jour referenceTable et referenceColumn |
| 7010 | La contrainte personnalisée fait référence à une colonne principale supprimée de la version cible. | Supprimer la contrainte ou mettre à jour l’attribut referenceColumn |

{style="table-layout:auto"}

### Schéma GraphQL

Des problèmes critiques liés au schéma GraphQL sont soulevés si les éléments du schéma ne sont pas présents dans la version cible.

| Code d’erreur | Description de l’erreur | Action suggérée |
| --- | --- | --- |
| 3101 | Le type a été supprimé | Liste de toutes les requêtes qui référencent ce champ. Vérifiez si ces requêtes sont utilisées par l’implémentation de personnalisation. Mettez à jour le code client pour gérer l’interface de requête modifiée. |
| 3102 | Type supprimé de l’union | Si le type d’union est utilisé dans l’implémentation de création de requête GraphQL ou de traitement de réponse, il peut être nécessaire de le mettre à jour. |
| 3103 | Champ supprimé | Vérifiez si le champ est référencé dans le code base de personnalisation. Ajustez l’implémentation pour gérer correctement le nouveau type de champ. |
| 3105 | Interface mise en oeuvre supprimée | Vérifiez si le type implémentant l’interface supprimée est utilisé dans la personnalisation. La mise en oeuvre doit peut-être être mise à jour si elle repose sur l’interface supprimée. |
| 3106 | Valeur supprimée de l’énumération | Si la valeur d’énumération supprimée est utilisée dans l’implémentation de création de requête GraphQL ou de traitement de réponse, elle peut nécessiter une mise à jour. |
| 3107 | Argument supprimé | Vérifiez si le champ est utilisé dans le code base de personnalisation. Supprimez l’argument de ce champ. |
| 3109 | Directive supprimée | Vérifiez si la directive est utilisée dans le code base de personnalisation. Ajustez la mise en oeuvre pour supprimer la référence à la directive. |
| 3110 | Argument de directive supprimé | Vérifiez si la directive est utilisée dans le code base de personnalisation. Supprimez l’argument de directive . |
| 3111 | Directive répétable supprimée | Vérifiez si la directive est utilisée dans le code base de personnalisation. Ajustez l’implémentation pour gérer les modifications de l’interface. |
| 3112 | Emplacement de la directive supprimé | Vérifiez si la directive est utilisée dans le code base de personnalisation. Ajustez l’implémentation pour gérer les modifications de l’interface. |
| 3201 | Type modifié | Liste de toutes les requêtes qui référencent ce champ. Vérifiez si ces requêtes sont utilisées par l’implémentation de personnalisation. Mettez à jour le code client pour gérer l’interface de requête modifiée. |
| 3203 | Type de champ modifié | Vérifiez si le champ est référencé dans le code base de personnalisation. Ajustez l’implémentation pour gérer correctement le nouveau type de champ. |
| 3207 | Argument changé de type | Vérifiez si le champ est utilisé dans le code base de personnalisation. Mettez à jour le type d’argument de ce champ. |
| 3303 | Champ de saisie requis ajouté | Le champ doit être ajouté à la requête si la requête comprenant ce champ est utilisée pour la personnalisation. |
| 3307 | Argument obligatoire ajouté | Vérifiez si le champ est utilisé dans le code base de personnalisation. Le nouvel argument requis doit être spécifié lors de l’utilisation du champ . |
| 3310 | Argument de directive requis ajouté | Vérifiez si la directive est utilisée dans le code base de personnalisation. Ajoutez l’argument de directive . |

{style="table-layout:auto"}

## Erreurs

### Code personnalisé

Des erreurs de code personnalisé sont générées lorsque le code personnalisé utilise des points d’entrée Adobe Commerce qui ne sont pas considérés/marqués comme `@api`. Le comportement préservé de ces points d’entrée n’est pas garanti. La personnalisation doit se baser sur les points d’entrée `@api` à la place. La fonctionnalité basée sur le code Adobe Commerce non-API doit être testée après la mise à niveau. Ces erreurs sont également signalées lorsque les normes de codage majeures ont été rompues.

| Code d’erreur | Description de l’erreur | Action suggérée |
| --- | --- | --- |
| 1104 | Utilisation d’une classe non API héritant de l’interface API | Les classes qui ne sont pas marquées comme `@api` peuvent être modifiées. Envisagez de mettre à jour le code pour vous baser sur l’interface marquée comme `@api` à la place. Dans le cas contraire, les fonctionnalités reposant sur cette mise en oeuvre doivent être testées après la mise à niveau. |
| 1121 | Extension à partir de la classe API non Adobe Commerce | La classe étendue n’est plus présente dans le code base. L’héritage n’est pas la méthode recommandée pour étendre les fonctionnalités d’Adobe Commerce. Mettez à jour le code pour utiliser une classe marquée comme `@api`. |
| 1122 | Importation d’une classe API non Adobe Commerce | La classe étendue n’est plus présente dans le code base. Mettez à jour le code pour utiliser une classe marquée comme `@api`. Dans le cas contraire, les fonctionnalités reposant sur cette mise en oeuvre doivent être testées après la mise à niveau. |
| 1123 | Chargement de la classe API non Adobe Commerce | La classe étendue n’est plus présente dans le code base. Mettez à jour le code pour utiliser une classe marquée comme `@api`. Dans le cas contraire, les fonctionnalités reposant sur cette mise en oeuvre doivent être testées après la mise à niveau. |
| 1124 | Utilisation d’une classe API non Adobe Commerce | La classe étendue n’est plus présente dans le code base. Mettez à jour le code pour utiliser une classe marquée comme `@api`. Dans le cas contraire, les fonctionnalités reposant sur cette mise en oeuvre doivent être testées après la mise à niveau. |
| 1224 | Utilisation d’une constante API non Adobe Commerce | Les constantes qui ne sont pas marquées comme `@api` peuvent être modifiées. Envisagez plutôt d’introduire et d’utiliser une constante privée de la valeur requise dans le code personnalisé. |
| 1225 | Remplacement de la constante d’API non Adobe Commerce | Les constantes qui ne sont pas marquées comme `@api` peuvent être modifiées. Envisagez plutôt d’introduire et d’utiliser une constante privée de la valeur requise dans le code personnalisé. |
| 1226 | Assignation de la constante API non-Adobe Commerce | Les constantes qui ne sont pas marquées comme `@api` peuvent être modifiées. Envisagez plutôt d’introduire et d’utiliser une constante privée de la valeur requise dans le code personnalisé. |
| 1322 | Interface API non Adobe Commerce importée | Les interfaces non marquées comme `@api` peuvent être modifiées. Envisagez de supprimer cet héritage ou de le remplacer par un héritage de l’interface Adobe Commerce marquée comme `@api` ou une interface introduite dans la portée du code de personnalisation. |
| 1324 | Interface API non Adobe Commerce utilisée | Les interfaces non marquées comme `@api` peuvent être modifiées. Envisagez de supprimer cet héritage ou de le remplacer par un héritage de l’interface Adobe Commerce marquée comme `@api` ou une interface introduite dans la portée du code de personnalisation. |
| 1327 | Interface API héritée non-Adobe Commerce | Les constantes qui ne sont pas marquées comme `@api` peuvent être modifiées. Envisagez plutôt d’introduire et d’utiliser une constante privée de la valeur requise dans le code personnalisé. |
| 1328 | Mise en oeuvre de l’interface API non Adobe Commerce | Les interfaces non marquées comme `@api` peuvent être modifiées. Envisagez de supprimer cet héritage ou de le remplacer par un héritage de l’interface Adobe Commerce marquée comme `@api` ou une interface introduite dans la portée du code de personnalisation. |
| 1420 | Instanciation de l’interface/classe d’API non Adobe Commerce | Les classes qui ne sont pas marquées comme `@api` peuvent être modifiées. Envisagez de mettre à jour le code pour vous baser sur l’interface marquée comme `@api` à la place. Dans le cas contraire, les fonctionnalités reposant sur cette mise en oeuvre doivent être testées après la mise à niveau. En outre, la méthode recommandée pour récupérer une instance de la classe consiste à utiliser l’ID. Pensez à utiliser une fabrique si une nouvelle instance de la classe est requise. |
| 1428 | Dépendance possible sur les détails de l’implémentation. | Les classes qui ne sont pas marquées comme `@api` peuvent être modifiées. Envisagez de mettre à jour le code pour vous baser sur l’interface marquée comme `@api` à la place. Dans le cas contraire, les fonctionnalités reposant sur cette mise en oeuvre doivent être testées après la mise à niveau. |
| 1429 | Appel de méthodes API autres qu’Adobe Commerce | Les méthodes qui ne sont pas marquées comme `@api` ou qui ne sont pas déclarées dans la classe/l’interface d’API peuvent être modifiées. Même si l’interface de la méthode n’est pas mise à jour dans la nouvelle version, son comportement ou sa sortie peuvent être différents. Envisagez de vous fier à une méthode d’interface. Dans le cas contraire, les fonctionnalités reposant sur cette mise en oeuvre doivent être testées après la mise à niveau. |
| 1449 | Appel à une méthode autre que l’interface (présente dans l’implémentation) | Les méthodes qui ne sont pas déclarées dans l’interface peuvent être modifiées. Envisagez de vous fier à une méthode d’interface. Dans le cas contraire, les fonctionnalités reposant sur cette mise en oeuvre doivent être testées après la mise à niveau. |
| 1524 | Utilisation de la propriété d’API non Adobe Commerce | Les valeurs des propriétés qui ne sont pas marquées comme `@api` peuvent être modifiées. Utilisez plutôt la méthode de l’interface API . |
| 1525 | Remplacement de la propriété d’API non Adobe Commerce | Les valeurs des propriétés qui ne sont pas marquées comme `@api` peuvent être modifiées. Utilisez plutôt la méthode de l’interface API . |
| 1526 | Attribution de la propriété d’API non Adobe Commerce | Les valeurs des propriétés qui ne sont pas marquées comme `@api` peuvent être modifiées. Utilisez plutôt la méthode de l’interface API . |
| 5004 | La fonction sans argument a été abandonnée. | Transmettez l’entrée à valider comme premier argument de la fonction. |
| 5007 | L&#39;utilisation de certaines fonctions est déconseillée. | Évitez d’utiliser ces fonctions. |
| 5009 | Les directives de modèle ne peuvent pas appeler de méthodes. Seul l’accès aux tableaux scalaires est autorisé | Supprimez les appels de méthode du modèle. |
| 5010 | Le bloc de commentaire de modèle `@vars` contient un fichier JSON non valide | Correction d’un fichier JSON non valide. |
| 5011 | Le bloc de commentaire de modèle `@vars` contient une étiquette non valide | Correction d’un libellé non valide. |
| 5012 | Une variable utilisée dans le modèle est manquante dans le bloc de commentaire du modèle `@vars`. | Ajoutez la variable manquante au bloc de commentaire @vars. |
| 5013 | Évitez d’utiliser une balise auto-fermante avec un élément html non vide | Utilisez plutôt la balise close . |
| 5014 | L’attribut `"active"` est obsolète | La liste des modules actifs est définie dans la configuration du déploiement. |
| 5015 | Le noeud `<param>` est obsolète | Utilisez `<argument name="..." xsi:type="...">` à la place. |
| 5016 | Le noeud `<instance>` est obsolète | Utilisez `<argument name="..." xsi:type="object">` à la place. |
| 5017 | Le noeud `<array>` est obsolète | Utilisez `<argument name="..." xsi:type="array">` à la place. |
| 5018 | Le noeud `<item key="...">` est obsolète | Utilisez `<item name="..." xsi:type="...">` à la place. |
| 5019 | Le noeud `<value>` est obsolète | Indiquez plutôt la valeur réelle sous la forme d’un littéral de texte. |
| 5020 | Noeud obsolète : `<supported_blocks>` | À remplacer par `<supported_containers>`. |
| 5021 | Noeud obsolète : `<block_name>` | À remplacer par `<container_name>`. |
| 5022 | Nom d’usine détecté | Le type de widget ne doit pas commencer par /. |
| 5023 | Structure ACL obsolète détectée en ligne | Consultez le site lib/internal/Magento/Framework/Acl/etc/acl.xsd. |
| 5024 | Structure de menu obsolète détectée en ligne | Consultez le site app/code/Magento/Backend/etc/menu.xsd. |
| 5025 | Structure de configuration système obsolète détectée dans le fichier | Consultez le site app/code/Magento/Config/etc/system_file.xsd. |
| 5026 | N’utilisez pas d’attribut de type `"text/javascript"` | Utilisez uniquement les membres publics. |
| 5028 | L&#39;accès aux membres protégés et privés de la classe `Block` est obsolète dans les modèles phtml. | Utilisez uniquement les membres publics. |
| 5031 | Contient la méthode obsolète | Utilisez plutôt la méthode `getConnection()` . |
| 5042 | Format incorrect de la référence de classe PHP | Vérifiez que la classe est référencée à l’aide de lettres, de nombres et d’aucune barre oblique. |
| 5043 | Format incorrect de référence de module | Vérifiez que le module est référencé à l’aide de lettres, de chiffres, de traits de soulignement et sans barre oblique. |
| 5044 | La classe `Zend_Db_Select` est limitée | Remplacement suggéré : `\Magento\Framework\DB\Select`. |
| 5045 | La classe `Zend_Db_Adapter_Pdo_Mysql` est limitée | Remplacement suggéré : `\Magento\Framework\DB\Adapter\Pdo\Mysql`. |
| 5046 | La classe `Magento\Framework\Serialize\Serializer\Serialize` est limitée | Remplacement suggéré : `Magento\Framework\Serialize\SerializerInterface`. |
| 5047 | La classe `ArrayObject` est limitée | Remplacement suggéré : classe personnalisée, étendue de `ArrayObject` avec des méthodes de sérialisation/déssérialisation remplacées. |
| 5048 | La classe `Magento\Framework\View\Element\UiComponent\ArrayObjectFactory` est limitée | Remplacement suggéré : usine qui crée une classe personnalisée, étendue à partir de `ArrayObject` avec des méthodes de sérialisation/non sérialisation remplacées. |
| 5050 | Le bloc référencé est supprimé. | Supprimez la référence au bloc. |
| 5051 | `output="toHtml"` est obsolète | Utilisez `output="1"`. |
| 5052 | La classe `\Magento\Framework\View\Element\Text\ListText` n&#39;est plus censée être utilisée dans la mise en page. | Supprimez la classe `\Magento\Framework\View\Element\Text\ListText` de la mise en page. |
| 5053 | L’appel de la méthode via l’instruction de mise en page `<action>` n’est pas autorisé | Évitez d’utiliser une méthode offensante dans `<action>`. |
| 5054 | `helper` attribut contient `/` | Supprimez `/` de l’attribut d’assistance. |
| 5055 | L’attribut `helper` ne contient pas `::` | Ajoutez `::` à l’attribut d’assistance. |
| 5056 | Les scripts d’installation sont obsolètes | Utilisez l’approche de schéma déclaratif dans le fichier etc/db_schema.xml du module. |
| 5057 | Les scripts InstallSchema sont obsolètes | Utilisez l’approche de schéma déclaratif dans le fichier etc/db_schema.xml du module. |
| 5058 | Les scripts InstallData sont obsolètes | Utilisez l’approche des correctifs de données dans le répertoire Setup/Patch/Data du module. |
| 5059 | Les scripts d’installation sont obsolètes | Créez une classe InstallData dans le dossier Setup du module\. |
| 5060 | Les scripts de mise à niveau sont obsolètes | Utilisez l’approche de schéma déclaratif dans le fichier etc/db_schema.xml du module. |
| 5061 | Les scripts UpgradeSchema sont obsolètes | Utilisez l’approche de schéma déclaratif dans le fichier etc/db_schema.xml du module. |
| 5062 | Les scripts UpgradeData sont obsolètes | Utilisez l’approche des correctifs de données dans le répertoire Setup/Patch/Data du module. |
| 5063 | Les scripts de mise à niveau sont obsolètes | Utilisez l’approche des correctifs de données dans le répertoire Setup/Patch/Data du module. |
| 5064 | Les scripts récurrents sont obsolètes | Créez la classe Récurrente dans le dossier Setup du module\. |
| 5065 | &#39;data&#39; se trouve dans un répertoire non valide | Créez un patch de données dans le dossier Setup/Patch/Data du module pour les mises à niveau de données ou utilisez l’approche de schéma déclaratif dans le fichier etc/db_schema.xml du module pour les modifications de schéma. |
| 5066 | &#39;sql&#39; se trouve dans un répertoire non valide | Créez un patch de données dans le dossier Setup/Patch/Data du module pour les mises à niveau de données ou utilisez l’approche de schéma déclaratif dans le fichier etc/db_schema.xml du module pour les modifications de schéma. |
| 5067 | Les noeuds identifiés par XPath sont obsolètes. | Le XML obsolète souligné dans l’erreur doit être mis à jour. Suivez les suggestions du message d’erreur. |
| 5068 | La directive `{{htmlescape}}` est obsolète | Utilisez `{{var}}` à la place. |
| 5069 | La directive `{{escapehtml}}` est obsolète | Utilisez `{{var}}` à la place. |
| 5070 | Le troisième paramètre n&#39;est plus nécessaire pour `getChildHtml()` | Supprimez le troisième paramètre de l’appel à `getChildHtml()`. |
| 5071 | Le quatrième paramètre n&#39;est plus nécessaire pour `getChildHtml()` | Supprimez le 4e paramètre de l’appel à `getChildHtml()`. |
| 5073 | Les noms de table hérités avec barre oblique doivent être corrigés en noms de table directs. | Utilisez plutôt le nom direct de la table. |
| 5075 | Les modules d’application ne doivent pas utiliser les classes des modules de test | Supprimez l’utilisation des classes des modules de test. |
| 5078 | La classe doit être demandée dans le constructeur, sinon le compilateur ne pourra pas trouver et générer ces classes. | Ajoutez une classe au constructeur. |
| 5079 | L’utilisation des variables de classe var est déconseillée. | Évitez d’utiliser &quot;var&quot; pour déclarer la variable de classe. |
| 5080 | Instruction SQL brute possible détectée | Utilisez plutôt des référentiels ou des correctifs de données. |
| 5081 | Il est déconseillé d’utiliser des assistants dans les modèles. | Utilisez ViewModel à la place. |
| 5082 | L’utilisation de $this dans les modèles est obsolète. | Utilisez $block à la place. |
| 5083 | Les constantes ne sont pas autorisées comme premier argument de la fonction de traduction | Utilisez plutôt un littéral de chaîne. |
| 5085 | L&#39;utilisation de certaines fonctions est déconseillée. | Utilisez plutôt la fonction alternative conseillée sur le message. |
| 5087 | Problème de compatibilité entre versions PHP | Suivez les suggestions du message et consultez le [guide de migration](https://www.php.net/manual/en/migration81.php). |
| 5088 | Paramètres facultatifs détectés après les paramètres requis | Déplacez les paramètres requis après les paramètres facultatifs. |
| 5089 | Visibilité des méthodes `final private` trouvée | Remplacez la visibilité de la méthode `final private` par `private` uniquement. |
| 5090 | La méthode magique `__set_state` n’est pas définie comme `static` | La méthode magique `__set_state` doit être définie comme `static`. |
| 5091 | Classe avec la méthode `__toString()` n&#39;héritant pas de l&#39;interface `Stringable` | Ajoutez l&#39;interface `Stringable` à la classe avec la méthode `__toString()`. |
| 5092 | Méthode `is_resource()` utilisée pour les fonctions qui renvoient désormais Objet | Remplacez `is_resource()` par `instanceof` Objet. |
| 6001 | `jQuery.andSelf()` supprimé | Utilisez `jQuery.addBack()`. |
| 6002 | jQuery `$.bind` et `$.unbind` sont obsolètes | Utilisez `$.on` et `$.off` à la place. |
| 6003 | La méthode jQuery pour s’abonner à un événement est obsolète et ne doit pas être utilisée. | Utilisez plutôt la méthode `.on("event name", fn)` pour vous abonner à cet événement. |
| 6003 | La méthode jQuery pour déclencher un événement est obsolète et ne doit pas être utilisée. | Utilisez plutôt la méthode `.trigger("event name")` pour déclencher cet événement. |
| 6004 | jQuery `$.delegate` et `$.undelegate` sont obsolètes | Utilisez `$.on` et `$.off` à la place. |
| 6005 | (`jQuery.load()` / `jQuery.unload()` / `jQuery.error()`) a été supprimé | Utilisez plutôt (`.on("load", fn)` / `.on("unload", fn)` / `.on("error", fn)`). |
| 6006 | `jQuery.size()` supprimé | Utilisez `jQuery.length`. |
| 6007 | `jQuery.trim` est obsolète | Utilisez `String.prototype.trim`. |
| 6008 | (`addButton`, `addContextToolbar`, `addMenuItem`, `addSidebar`, `file_browser_callback`, `insert_button_items`, thème &quot;inlite&quot;, thème &quot;mobile&quot;, thème &quot;moderne&quot;) est supprimé. | Mettre à jour le code pour qu’il soit compatible avec tinymce5. |
| 6009 | `jQuery.isFunction()` est obsolète | Dans la plupart des cas, il peut être remplacé par [type x === &quot;fonction&quot;]. |
| 6009 | `jQuery.type()` est obsolète | Remplacez par une vérification de type appropriée telle que [type x === &quot;function&quot;]. |
| 6009 | `jQuery.isArray()` est obsolète | Utilisez plutôt la méthode native Array.isArray . |
| 6009 | `jQuery.parseJSON()` est obsolète | Pour analyser les chaînes JSON, utilisez plutôt la méthode native JSON.parse . |
| 6010 | (`jQuery.expr[":"]`, `jQuery.expr.filters`) est obsolète | Utilisez jQuery.expr.pseudos à la place. |

{style="table-layout:auto"}

### Schéma DB

Les erreurs de schéma de base de données sont générées si les tables de base de données, colonnes, index ou contraintes, ajoutées ou supprimées dans la version cible d’Adobe Commerce, peuvent entraîner des conflits avec le schéma de base de données personnalisé.

| Code d’erreur | Description de l’erreur | Action suggérée |
| --- | --- | --- |
| 7001 | La version principale cible introduit un tableau portant le même nom qu’un tableau déclaré par un module personnalisé. | Utilisez la nouvelle table principale (le cas échéant) ou renommez la table personnalisée. |
| 7002 | Le tableau principal étendu par un module personnalisé a été supprimé dans la version cible. | Toutes les références de tableau principal supprimées doivent être supprimées du code base. |
| 7003 | La version de base cible introduit une colonne portant le même nom qu’une colonne déclarée par un module personnalisé. | Utilisez la nouvelle colonne principale (le cas échéant) ou renommez la colonne personnalisée. |
| 7004 | La colonne core qui est étendue par un module personnalisé a été supprimée dans la version cible. | Toutes les références de colonne principales supprimées doivent être supprimées du code base. |
| 7005 | La version principale cible introduit un index avec le même referenceId qu’un index déclaré par un module personnalisé. | Supprimez (en cas de duplication à l’index principal introduit) ou renommez l’index personnalisé. |
| 7006 | L’index principal étendu par un module personnalisé a été supprimé dans la version cible. | Toutes les références d’index principal supprimées doivent être supprimées du code base. |
| 7007 | La version de base de la cible introduit une contrainte portant le même nom qu’une contrainte déclarée par un module personnalisé. | Supprimer (en cas de duplication à la contrainte principale introduite) ou renommer la contrainte personnalisée |
| 7008 | La contrainte principale étendue par un module personnalisé a été supprimée de la version cible. | Utilisez la nouvelle contrainte principale (le cas échéant) ou renommez la contrainte personnalisée. |

{style="table-layout:auto"}

## Avertissements

### Code principal

Ces avertissements sont signalés lorsqu’il existe des incohérences mineures dans le code base.

| Code d’erreur | Description de l’erreur | Action suggérée |
| --- | --- | --- |
| 2004 | Non-correspondance de version de dépendance du compositeur | Ce problème indique que la version de dépendance du compositeur en mode réel et le projet réel sont différents. Mettez à jour la dépendance en exécutant `composer update <package_name>`. |

{style="table-layout:auto"}

### Code personnalisé

Des avertissements de code personnalisé sont générés lorsque les références au code obsolète sont détectées. Ces références doivent être remplacées par les points d’extension pris en charge. Pour les recommandations, prêtez attention à l’annotation `@see` de l’élément obsolète. Ces erreurs sont également signalées lorsque des normes de codage mineures ont été rompues.

| Code d’erreur | Description de l’erreur | Action suggérée |
| --- | --- | --- |
| 1131 | Extension à partir de la classe Adobe Commerce ``@deprecated`` | La classe étendue sera supprimée dans les versions à venir. L’héritage n’est pas la méthode recommandée pour étendre les fonctionnalités d’Adobe Commerce. Mettez à jour le code pour utiliser une classe marquée comme `@api`. |
| 1132 | Importation de la classe Adobe Commerce `@deprecated` | La classe étendue sera supprimée dans les versions à venir. Pensez plutôt à utiliser la classe Adobe Commerce marquée comme `@api` . |
| 1133 | Chargement de la classe Adobe Commerce `@deprecated` | La classe étendue sera supprimée dans les versions à venir. Pensez plutôt à utiliser la classe Adobe Commerce marquée comme `@api` . |
| 1134 | Utilisation de la classe Adobe Commerce `@deprecated` | La classe étendue sera supprimée dans les versions à venir. Pensez plutôt à utiliser la classe Adobe Commerce marquée comme `@api` . |
| 1234 | Utilisation de la constante Adobe Commerce `@deprecated` | La constante obsolète sera supprimée dans les versions à venir. Pensez plutôt à utiliser une constante marquée comme `@api` ou une constante privée dans votre mise en oeuvre. |
| 1235 | Remplacement de la constante Adobe Commerce `@deprecated` | La constante obsolète sera supprimée dans les versions à venir. Pensez plutôt à utiliser une constante marquée comme `@api` ou une constante privée dans votre mise en oeuvre. |
| 1236 | Assignation de la constante Adobe Commerce `@deprecated` | La constante obsolète sera supprimée dans les versions à venir. Pensez plutôt à utiliser une constante marquée comme `@api` ou une constante privée dans votre mise en oeuvre. |
| 1332 | Interface Adobe Commerce `@deprecated` importée | L’interface obsolète sera supprimée dans les versions à venir. Pensez plutôt à utiliser une interface ou une classe marquée comme `@api` . |
| 1334 | Interface Adobe Commerce `@deprecated` utilisée | L’interface obsolète sera supprimée dans les versions à venir. Pensez plutôt à utiliser une interface ou une classe marquée comme `@api` . |
| 1337 | Hérité de l’interface Adobe Commerce `@deprecated` | L’interface obsolète sera supprimée dans les versions à venir. Envisagez de supprimer l’héritage de l’interface en utilisant une interface marquée comme `@api` ou une interface introduite dans votre implémentation à la place. |
| 1338 | Mise en oeuvre de l’interface Adobe Commerce `@deprecated` | L’interface obsolète sera supprimée dans les versions à venir. Envisagez de supprimer l’héritage de l’interface en utilisant une interface marquée comme `@api` ou une interface introduite dans votre implémentation à la place. |
| 1430 | Appel d’une méthode d’objet de données non déclarée | Les méthodes magiques non déclarées peuvent être modifiées. Utilisez plutôt des méthodes d’interface. |
| 1439 | Appeler la méthode Adobe Commerce `@deprecated` | La méthode obsolète sera supprimée dans les versions à venir. Envisagez plutôt de vous fier aux méthodes déclarées dans les interfaces d’API. |
| 1440 | Non-correspondance de la signature de méthode | Un appel ou un remplacement de la méthode principale est détecté avec des paramètres, des arguments ou un type de retour qui ne correspondent pas à la signature de la méthode. |
| 1534 | Utilisation de la propriété Adobe Commerce `@deprecated` | La méthode obsolète sera supprimée dans les versions à venir. Envisagez plutôt de vous fier aux méthodes déclarées dans les interfaces d’API. |
| 1535 | Remplacement de la propriété Adobe Commerce `@deprecated` | La propriété obsolète sera supprimée dans les versions à venir. Envisagez de vous fier aux méthodes déclarées dans les interfaces API ou d’utiliser une propriété privée dans votre implémentation. |
| 1536 | Attribution de la propriété Adobe Commerce `@deprecated` | La méthode obsolète sera supprimée dans les versions à venir. Envisagez plutôt de vous fier aux méthodes déclarées dans les interfaces d’API. |
| 5006 | Les proxys et les intercepteurs ne doivent jamais être explicitement demandés dans les constructeurs. | La classe d’origine doit être déclarée en tant que type du paramètre constructeur . La classe Interceptor/Proxy sera transmise par l’implémentation d’injection de dépendance de framework. |
| 5074 | Utilisation de la méthode obsolète `getResource()` pour (enregistrer/charger/supprimer) les données détectées. | Utilisez un référentiel à la place. |
| 5086 | La visibilité n&#39;est pas déclarée sur une constante | Déclarez la visibilité sur toutes les constantes. |

{style="table-layout:auto"}

### Schéma GraphQL

Les avertissements de schéma GraphQL sont générés lorsque les éléments supplémentaires sont ajoutés au schéma dans la nouvelle version. Il est recommandé de passer en revue la mise en oeuvre pour voir si elles doivent être utilisées pour les requêtes.

| Code d’erreur | Description de l’erreur | Action suggérée |
| --- | --- | --- |
| 3206 | Valeur par défaut de l’argument modifiée | Si la requête est utilisée dans la personnalisation, il se peut que la valeur de l’argument doive être spécifiée explicitement. |
| 3302 | Type ajouté à l’union | Le type a été ajouté à l’union. Vérifiez le traitement de l’implémentation du résultat de la requête retournant ce type d’union et assurez-vous qu’il est en mesure de gérer le type ajouté. |
| 3304 | Champ de saisie facultatif ajouté | Champ de saisie facultatif ajouté. Vérifiez la mise en oeuvre pour vous assurer. |
| 3305 | Interface mise en oeuvre ajoutée | Le champ peut accepter/fournir des informations supplémentaires qui peuvent être prises en compte dans l’implémentation. |
| 3306 | Valeur ajoutée à l’énumération | Une valeur a été ajoutée à une énumération. Si les clients contiennent une instruction switch sur la valeur de l’énumération et n’incluent pas de casse par défaut, cette modification peut entraîner un comportement inattendu. |
| 3308 | Argument facultatif ajouté | Si la requête utilise un nouvel argument dans la personnalisation, il peut être nécessaire de l’ajouter à la requête. |

{style="table-layout:auto"}
