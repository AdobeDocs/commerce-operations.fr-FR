---
title: référence system.xml
description: Découvrez comment le fichier XML système gère la configuration de l’application Commerce.
feature: Configuration, System
badge: label="Contribué par David Lambauer" type="Informative" url="https://github.com/DavidLambauer" tooltip="David Lambauer"
exl-id: a6c5de6c-e8da-4eca-bbfb-592904b2c53f
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '2685'
ht-degree: 0%

---

# référence system.xml

Le `system.xml` vous permet de gérer la configuration du système Commerce. Utilisez cette rubrique comme référence générale pour le `system.xml` fichier . Le `system.xml` se trouve sous `etc/adminhtml/system.xml` dans une extension Commerce 2 donnée.

Le fragment de code suivant affiche le squelette nu du fichier :

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <!-- PLACE YOUR MODULE SPECIFIC CONFIGURATION HERE -->
    </system>
</config>
```

>[!TIP]
>
>Si vous souhaitez une validation instantanée *XSD dans votre IDE, vous pouvez exécuter `bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>`.

## Onglets // Sections // Groupes // Champs

Dans le `system.xml` , il est possible de définir quatre types différents d&#39;entités, qui sont liées les unes aux autres. La section suivante décrit la relation entre les onglets, les sections, les groupes et les champs. La capture d’écran suivante affiche la configuration du système Commerce 2 dans le serveur principal d’administration.
Les carrés rouges représentent les différents types définis dans la variable `system.xml` fichier :

![Capture d’écran affichant une section configurée dans l’Admin.](../../assets/configuration/magento2-system-configuration.png)

Les onglets sont utilisés pour fractionner sémantiquement différentes zones de configuration. Chaque onglet peut contenir une ou plusieurs sections, qui peuvent également être référencées sous forme de sous-menus. Une section contient un ou plusieurs groupes.
Chaque groupe répertorie un ou plusieurs champs. Vous pouvez également utiliser un groupe pour ajouter une description générale pour les champs suivants. Comme mentionné, chaque groupe peut comporter un ou plusieurs champs. Les champs sont la plus petite entité du contexte de configuration du système.

## Onglets

A `<tab>`-Balisez les références à un onglet existant ou nouveau dans la configuration du système.

### Référence d’attribut d’onglet

A `<tab>`-Tag peut avoir les attributs suivants :

| Attribut | Description | Type | Obligatoire |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------|----------|----------|
| `id` | Définit l’identifiant utilisé pour référencer la section. | `typeId` | required |
| `translate` | Définit le champ à traduire. Fournir `label` pour rendre le libellé traduisible. | `string` | facultatif |
| `type` | Définit le type d’entrée de l’élément de HTML rendu. Par défaut, la valeur `text`. | `string` | facultatif |
| `sortOrder` | Définit l’ordre de tri de la section. Des nombres élevés poussent la section en bas de la page ; Les numéros bas poussent la section en haut. | `float` | facultatif |
| `class` | Ajoute une classe CSS définie à l’élément de HTML de l’onglet rendu. | `string` | facultatif |

### Référence du noeud de tabulation

A `<tab>`-Tag peut avoir l’enfant suivant :

| Noeud | Description | Type |
|---------|------------------------------------------------------|----------|
| `label` | Définit le libellé affiché dans l’interface frontale. | `string` |

### Exemple : Créer un onglet

Le fragment de code suivant illustre la création d’un nouvel onglet avec des exemples de données.

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>
    </system>
</config>
```

Le fragment de code ci-dessus crée un onglet avec l’identifiant `A_UNIQUE_ID`. Comme la variable `translate`-attribute est défini et référence le libellé, la variable `label`-node est traduisible. Pendant le processus de rendu, la classe CSS `a-custom-css-class-to-style-this-tab` sera appliqué sur l’élément de HTML créé pour cet onglet.
Le `sortOrder`-attribute avec la valeur de `10` définit la position de l’onglet dans la liste de tous les onglets lors du rendu.

## Sections

A `<section>`-Balisez les références à une section existante ou à une nouvelle section dans la configuration du système.

### Référence d’attribut de section

A `<section>`-Tag peut avoir les attributs suivants :

| Attribut | Description | Type | Obligatoire |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | Définit l’identifiant utilisé pour référencer la section. | `typeId` | required |
| `translate` | Définit le champ à traduire. Fournir `label` pour rendre le libellé traduisible. | `string` | facultatif |
| `type` | Définit le type d’entrée de l’élément de HTML rendu. La valeur par défaut est `text`. | `string` | facultatif |
| `sortOrder` | Définit l’ordre de tri de la section. Les nombres élevés pousseront la section au bas de la page ; Les numéros bas pousseront la section vers le haut. | `float` | facultatif |
| `showInDefault` | Définit si la section s’affiche dans la portée de configuration par défaut. Spécifier `1` pour afficher la section et `0` pour masquer la section. | `int` | facultatif |
| `showInStore` | Définit si la section s’affiche au niveau du magasin. Spécifier `1` pour afficher la section et `0` pour masquer la section. | `int` | facultatif |
| `showInWebsite` | Définit si la section s’affiche au niveau du site web. Spécifier `1` pour afficher la section et `0` pour masquer la section. | `int` | facultatif |
| `canRestore` | Définit si la section peut être restaurée par défaut. | `int` | facultatif |
| `advanced` | Obsolète depuis la version 100.0.2. | `bool` | facultatif |
| `extends` | En fournissant un identifiant d’une autre section, le contenu de ce noeud étend la section que vous avez référencée. | `string` | facultatif |

### Référence de noeud de section

A `<section>`-Tag peut avoir les enfants suivants :

| Noeud | Description | Type |
|------------------|-----------------------------------------------------------------------------------------------------------------------|---------------------|
| `label` | Définit le libellé affiché dans l’interface frontale. | `string` |
| `class` | Ajoute une classe CSS définie à l’élément de HTML de section rendue. | `string` |
| `tab` | Fait référence à l’onglet associé. Attend l’identifiant de l’onglet. | `typeTabId` |
| `header_css` | Ni utilisé ni évalué au moment de la rédaction de cet article. | `string` |
| `resource` | Fait référence à une ressource ACL afin de fournir des paramètres d’autorisation pour cette section. | `typeAclResourceId` |
| `group` | Définissez un ou plusieurs sous-groupes. | `typeGroup` |
| `frontend_model` | Spécifie un modèle front-end différent pour modifier le rendu et modifier la sortie. | `typeModel` |
| `include` | Utilisé pour inclure des `system_include.xsd` fichiers compatibles. Généralement utilisé pour structurer les grandes dimensions `system.xml` fichiers . | `includeType` |

### Exemple : Créer une section et l’affecter à un onglet

Le fragment de code suivant illustre l’utilisation de base de la création d’une section.

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>
        </section>
    </system>
</config>
```

La section décrite ci-dessus définit l’ID `A_UNIQUE_SECTION_ID`, est visible dans la vue de configuration par défaut et dans un contexte de magasin. Le `label`-node est traduisible. La section est associée à l’onglet avec l’identifiant `A_UNIQUE_ID`. La section n’est accessible que par les utilisateurs disposant des autorisations définies dans la liste de contrôle d’accès. `VENDOR_MODULE::path_to_the_acl_resource`.

## Groupes

Le `<group>`-Tag est utilisé pour regrouper des champs.

### Référence d’attribut de groupe

A `<group>`-Tag peut avoir les attributs suivants :

| Attribut | Description | Type | Obligatoire |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | Définit l’identifiant utilisé pour référencer le groupe. | `typeId` | required |
| `translate` | Définit les champs qui doivent être traduisibles. Fournir `label` pour rendre le libellé traduisible. Plusieurs champs doivent être séparés par un espace. | `string` | facultatif |
| `type` | Définit le type d’entrée de l’élément de HTML rendu. La valeur par défaut est `text`. | `string` | facultatif |
| `sortOrder` | Définit l’ordre de tri de la section. Les nombres élevés pousseront la section au bas de la page ; Les numéros bas pousseront la section vers le haut. | `float` | facultatif |
| `showInDefault` | Définit si le groupe est affiché dans la portée de configuration par défaut. Spécifier `1` pour afficher le groupe et `0` pour masquer le groupe. | `int` | facultatif |
| `showInStore` | Définit si le groupe est affiché au niveau du magasin. Spécifier `1` pour afficher le groupe et `0` pour masquer le groupe. | `int` | facultatif |
| `showInWebsite` | Définit si le groupe est affiché au niveau du site web. Spécifier `1` pour afficher le groupe et `0` pour masquer le groupe. | `int` | facultatif |
| `canRestore` | Définit si le groupe peut être restauré par défaut. | `int` | facultatif |
| `advanced` | Obsolète depuis la version 100.0.2. | `bool` | facultatif |
| `extends` | En fournissant l’identifiant d’un autre groupe, le contenu de ce noeud étend la section que vous avez référencée. | `string` | facultatif |

### Référence de noeud de groupe

A `<group>`-Tag peut avoir les enfants suivants :

| Noeud | Description | Type |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| `label` | Définit le libellé affiché dans l’interface frontale. | `string` |
| `fieldset_css` | Ajoute une ou plusieurs classes CSS à un jeu de champs de groupe. | `string` |
| `frontend_model` | Spécifie un modèle front-end différent pour modifier le rendu et modifier la sortie. | `typeModel` |
| `clone_model` | Spécifie un modèle donné pour cloner des champs. | `typeModel` |
| `clone_fields` | Clonage des champs activé ou désactivé. | `int` |
| `help_url` | Non extensible. Voir ci-dessous. | `typeUrl` |
| `more_url` | Non extensible. Voir ci-dessous. | `typeUrl` |
| `demo_link` | Non extensible. Voir ci-dessous. | `typeUrl` |
| `comment` | Ajoute un commentaire sous le libellé du groupe. En utilisant `<![CDATA[//]]>` Le HTML peut être appliqué. | `string` |
| `hide_in_single_store_mode` | Si le groupe doit être visible en mode de magasin unique. `1` masque le groupe ; `0` affiche le groupe. | `int` |
| `field` | Définissez un ou plusieurs champs qui doivent être disponibles dans ce groupe. | `field` |
| `group` | Définissez un ou plusieurs sous-groupes. | `unbounded` |
| `depends` | Peut être utilisé pour déclarer des dépendances sur d’autres champs. N’est utilisé pour afficher des champs/groupes spécifiques que lorsqu’un champ donné a une valeur de `1`. Ce noeud attend une `section/group/field`-string. | `depends` |
| `attribute` | Les attributs personnalisés peuvent être utilisés par les modèles frontend. Généralement utilisé pour rendre un modèle front-end donné plus dynamique. | `attribute` |
| `include` | Utilisé pour inclure des `system_include.xsd` fichiers compatibles. Généralement utilisé pour structurer les grandes dimensions `system.xml` fichiers . | `includeType` |

>[!WARNING]
>
>Les noeuds `more_url`, `demo_url` et `help_url` sont définis par un modèle front-end PayPal qui n’est utilisé qu’une seule fois. Ces noeuds ne sont pas réutilisables.

### Exemple : Création d’un groupe pour une section donnée

Le fragment de code suivant illustre l’utilisation de base de la création d’un groupe.

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>

            <group id="A_UNIQUE_GROUP_ID" translate="label comment" sortOrder="10" showInDefault="1" showInWebsite="0" showInStore="1">
                <label>A meaningful group label</label>
                <comment>An additional comment helping users to understand the effect when configuring the fields defined in this group.</comment>
                <!-- Add your fields here. -->
            </group>
        </section>
    </system>
</config>
```

Le groupe décrit ci-dessus définit l’ID `A_UNIQUE_GROUP_ID`, est visible dans la vue de configuration par défaut et dans un contexte de magasin. Les deux `label` et le `comment` sont marqués comme traduisibles.

## Champs

Le `<field>`-Tag est utilisé dans `<group>`-Balises pour définir des valeurs de configuration spécifiques.

### Référence d’attribut de champ

A `<field>`-Tag peut avoir les attributs suivants :

| Attribut | Description | Type | Obligatoire |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | Définit l’identifiant utilisé pour référencer le champ. | `typeId` | required |
| `translate` | Définit les champs qui doivent être traduisibles. Fournir `label` pour rendre le libellé traduisible. Plusieurs champs doivent être séparés par un espace. | `string` | facultatif |
| `type` | Définit le type d’entrée de l’élément de HTML rendu. La valeur par défaut est `text`. | `string` | facultatif |
| `sortOrder` | Définit l’ordre de tri de la section. Des nombres élevés poussent la section en bas de la page ; Les numéros bas poussent la section en haut. | `float` | facultatif |
| `showInDefault` | Définit si le champ s’affiche dans la portée de configuration par défaut. Spécifier `1` pour afficher le champ et `0` pour masquer le champ. | `int` | facultatif |
| `showInStore` | Définit si le champ s’affiche au niveau du magasin. Spécifier `1` pour afficher le champ et `0` pour masquer le champ. | `int` | facultatif |
| `showInWebsite` | Définit si le champ s’affiche au niveau du site web. Spécifier `1` pour afficher le champ et `0` pour masquer le champ. | `int` | facultatif |
| `canRestore` | Définit si le champ peut être restauré par défaut. | `int` | facultatif |
| `advanced` | Obsolète depuis la version 100.0.2. | `bool` | facultatif |
| `extends` | En fournissant l’identifiant d’un autre champ, le contenu de ce noeud étend la section que vous avez référencée. | `string` | facultatif |

### Référence de type de champ

A `<field>`-Tag peut avoir les valeurs suivantes pour la variable `type=""` attribute:

| Type | Description |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `text` | Champ de texte standard à une seule ligne |
| `textarea` | Bloc de texte |
| `select` | Liste déroulante normale, qui peut nécessiter une personnalisation `source_model`. Utilisé également pour `Yes/No` sélections. Voir `Magento\Search\Model\Adminhtml\System\Config\Source\Engine` par exemple. |
| `multiselect` | Comme `select` mais plusieurs options sont valides. |
| `button` | Bouton qui déclenche un événement immédiat. Nécessite un modèle front-end personnalisé pour définir le texte du bouton et l’action. Voir `Magento\ScheduledImportExport\Block\Adminhtml\System\Config\Clean` par exemple. |
| `obscure` | Un champ de texte avec la valeur chiffrée et affichée sous la forme `****`. La modification du type à l’aide de &quot;Inspect Element&quot; dans le navigateur ne permet pas de révéler la valeur. |
| `password` | Comme `obscure` mais que la valeur masquée n’est pas chiffrée et la modification forcée du type à l’aide de &quot;Inspect Element&quot; dans le navigateur n’affiche pas la valeur. |
| `file` | Permet de charger un fichier en vue de son traitement. |
| `label` | Affiche un libellé au lieu d’un champ modifiable. Utilisez ce type lorsqu’un champ n’est modifiable que sur des portées spécifiques, par exemple au niveau de la vue de magasin uniquement. |
| `time` | Contrôle pour définir l’heure à l’aide de trois listes déroulantes : Heure, minute et seconde. |
| `allowspecific` | Une liste de plusieurs pays spécifiques. Nécessite un `source_model` par exemple `Magento\Shipping\Model\Config\Source\Allspecificcountries` |
| `image` | Permet de charger une image. |
| `note` | Permet d’ajouter une note d’information à la page. Ce type nécessite une `frontend_model` pour effectuer le rendu de la note. |

Il est également possible de créer un type de champ personnalisé. Cela est souvent effectué lorsqu’un bouton spécial, avec une action, est requis. Pour ce faire, deux éléments principaux sont nécessaires :

- Création d’un bloc dans le `adminhtml` area
- La définition de la variable `type=""` au chemin d’accès à ce bloc

Le bloc lui-même nécessite, au minimum, un `__construct` et une `getElementHtml()` . Le [Magento_OfflineShipping](https://github.com/magento/magento2/blob/2.4/app/code/Magento/OfflineShipping) est un exemple simple d’un type personnalisé.

Par exemple, dans le module OfflineShipping , le bouton Exporter est défini dans la variable `Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export` et la définition du champ ressemble à ceci :

```xml
<field id="export" translate="label" type="Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export" sortOrder="5" showInDefault="0" showInWebsite="1" showInStore="0">
    <label>Export</label>
</field>
```

### Référence du noeud de champ

A `<field>`-Tag peut avoir les enfants suivants :

| Noeud | Description | Type |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|
| `label` | Définit le libellé affiché dans l’interface frontale. | `string` |
| `comment` | Ajoute un commentaire sous le libellé du champ. En utilisant `<![CDATA[//]]>` Le HTML peut être appliqué. | `string` |
| `tooltip` | Autre élément front-end possible pouvant être utilisé pour décrire la signification de ce champ. S’affiche sous la forme d’une petite icône en regard du champ. | `string` |
| `hint` | Affiche des informations supplémentaires. Disponible uniquement avec des `frontend_model`. | `string` |
| `frontend_class` | Ajoute une classe CSS définie à l’élément de HTML de section rendue. | `string` |
| `frontend_model` | Spécifie un modèle front-end différent pour modifier le rendu et modifier la sortie. | `typeModel` |
| `backend_model` | Spécifie un modèle d’arrière-plan différent pour modifier les valeurs configurées. | `typeModel` |
| `source_model` | Spécifie un modèle source différent qui fournit un ensemble spécifique de valeurs. | `typeModel` |
| `config_path` | Peut être utilisé pour remplacer le chemin de configuration générique d’un champ. | `typeConfigPath` |
| `validate` | Définissez différentes règles de validation (séparées par des espaces). La liste de référence complète des règles de validation disponibles est répertoriée ci-dessous. | `string` |
| `can_be_empty` | Utilisé lorsque `type` is `multiselect` pour indiquer qu’un champ peut être vide. | `int` |
| `if_module_enabled` | Utilisé pour afficher un champ uniquement lorsqu’un module donné est activé. | `typeModule` |
| `base_url` | Utilisé en combinaison avec `upload_dir` pour les chargements de fichiers. | `typeUrl` |
| `upload_dir` | Spécifiez un répertoire cible pour les téléchargements. Ce noeud comporte des attributs et des noeuds supplémentaires. Cherchez-les avant d&#39;utiliser ceci. | `typeUploadDir` |
| `button_url` | Affiche un bouton si `button_url` et `button_label` sont spécifiées. Généralement utilisé en combinaison avec un modèle front-end personnalisé. | `typeUrl` |
| `button_label` | Affiche un bouton si `button_label` et `button_url` sont spécifiées. Généralement utilisé en combinaison avec un modèle front-end personnalisé. | `string` |
| `more_url` | Non extensible. Voir ci-dessous. | `typeUrl` |
| `demo_url` | Non extensible. Voir ci-dessous. | `typeUrl` |
| `hide_in_single_store_mode` | Si le groupe doit être visible en mode de magasin unique. `1` masque le groupe ; `0` affiche le groupe. | `int` |
| `source_service` | Service utilisé pour renseigner les options sélectionnées. | `complexType` |
| `options` | Inutilisée. Potentiellement obsolète. | `complexType` |
| `depends` | Peut être utilisé pour déclarer des dépendances à d’autres champs. N’est utilisé que pour afficher des champs/groupes spécifiques lorsqu’un champ donné a une valeur de `1`. Ce noeud attend une `section/group/field`-string. | `complexType` |
| `attribute` | Les attributs personnalisés peuvent être utilisés par les modèles frontend. Généralement utilisé pour rendre un modèle front-end donné plus dynamique. | `complexType` |
| `requires` | Non extensible. Voir ci-dessous. | `complexType` |

>[!WARNING]
>
>Les noeuds `more_url`, `demo_url`, `requires` et `options` sont définis par un modèle de paiement principal différent et ne sont utilisés qu’une seule fois. Ces noeuds ne sont pas réutilisables.

### Exemple : Créer deux champs dans un groupe donné

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>

            <group id="A_UNIQUE_GROUP_ID" translate="label" sortOrder="10" showInDefault="1" showInWebsite="0" showInStore="1">
                <label>A meaningful group label</label>
                <comment>An additional comment helping users to understand the effect when configuring the fields defined in this group.</comment>

                <field id="A_UNIQUE_FIELD_ID" translate="label" sortOrder="10" showInDefault="0" showInWebsite="0" showInStore="1" type="select">
                    <label>Feature Flag Example</label>
                    <comment>This field is an example for a basic yes or no select.</comment>
                    <tooltip>Usually these kinds of fields are used to enable or disable a given feature. Other fields might be dependent to this and will only appear if this field is set to yes.</tooltip>
                    <source_model>Magento\Config\Model\Config\Source\Yesno</source_model>
                </field>

                <field id="ANOTHER_UNIQUE_FIELD_ID" translate="label" sortOrder="10" showInDefault="0" showInWebsite="0" showInStore="1" type="text">
                    <label>A meaningful field label</label>
                    <comment>A descriptive text explaining this configuration field.</comment>
                    <tooltip>Another possible frontend element that also can be used to describe the meaning of this field. Will be displayed as a small icon beside the field.</tooltip>
                    <validate>required-entry no-whitespace</validate> <!-- Field is required and must not contain any whitespace. -->
                    <if_module_enabled>VENDOR_MODULE</if_module_enabled>
                    <depends> <!-- This field will only be visible if the field with the id A_UNIQUE_FIELD_ID is set to value 1 -->
                        <field id="A_UNIQUE_FIELD_ID">1</field>
                    </depends>
                </field>
            </group>
        </section>
    </system>
</config>
```

L’exemple ci-dessus crée deux champs, visibles/configurables par défaut et en mode magasin. Les deux champs ont un commentaire et une info-bulle pour décrire leur objectif à l’utilisateur. Le `label`-node est traduisible.
Le champ avec l&#39;identifiant `ANOTHER_UNIQUE_FIELD_ID` est visible lorsque le module donné dans la variable `if_module_enabled` est activé globalement. Le champ valide également sa valeur par rapport aux règles `required-entry` et `no-whitespace`.
Le champ avec l&#39;identifiant `A_UNIQUE_FIELD_ID` définit un modèle source différent qui fournit les valeurs. `Yes` et `No`.

### Modèles sources courants

Les modèles sources suivants sont fournis par Commerce 2 Core. En général, il existe beaucoup d&#39;autres modèles sources; la liste suivante décrit les plus courantes. Gardez à l’esprit que ces modèles sources ont besoin de l’attribut field . `type` à définir sur `select` afin de fonctionner correctement.

| Modèle source | Description |
|-----------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| `Magento\Config\Model\Config\Source\Yesnocustom` | Fournit les valeurs `Yes`, `No` et `Specified`. |
| `Magento\Config\Model\Config\Source\Enabledisable` | Fournit les valeurs `Enable`, `Disable`. Enregistre les valeurs sous la forme `0` et `1` dans la base de données. |
| `Magento\AdminNotification\Model\Config\Source\Frequency` | Fournit les valeurs `1 Hour`,`2 Hours`,`6 Hours`,`12 Hours` et `24 Hours`. Les valeurs sont enregistrées sous forme d’entiers. |
| `Magento\Catalog\Model\Config\Source\TimeFormat` | Fournit les valeurs du format d’heure (12 h/24 h). |
| `Magento\Cron\Model\Config\Source\Frequency` | Fournit les valeurs `Daily`, `Weekly` et `Monthly`. Les valeurs sont enregistrées dans la base de données sous la forme `D`, `W` et `M`. |
| `Magento\GoogleAdwords\Model\Config\Source\Language` | Fournit les valeurs d’un code à 2 lettres d’une langue donnée au format ISO 639-1 (ex. en). |
| `Magento\Config\Model\Config\Source\Locale` | Fournit les valeurs similaires à celle ci-dessus, mais conserve un code de paramètres régionaux (en_US, par exemple). |

### Validation de champ

Une ou plusieurs classes validator peuvent être affectées à un champ pour s’assurer que l’entrée de l’utilisateur respecte les exigences de l’extension. Les règles de validation peuvent être appliquées avec la variable `<validate>`-Tag.
L’exemple suivant valide un champ et ajoute plusieurs règles de validation différentes.

```xml
<field id="A_CUSTOM_IDENTIFIER" showInDefault="1" showInWebsite="0" showInStore="1">
    <validate>required-entry validate-clean-url no-whitespace</validate>
</field>
```

Les règles de validation suivantes sont disponibles :

| Règle | Description |
|---------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| `alphanumeric` | Autorise uniquement les lettres, les chiffres, les espaces ou les traits de soulignement. |
| `integer` | Permet un nombre non décimal positif ou négatif. |
| `ipv4` | Permet une adresse IP v4 valide. |
| `ipv6` | Permet une adresse IP v6 valide. |
| `letters-only` | Autorise uniquement les lettres. Par exemple : `abcABC`. |
| `letters-with-basic-punc` | Autorise uniquement les lettres ou la ponctuation.<br>Doit transmettre l’expression suivante : `/^[a-z\-.,()\u0027\u0022\s]+$/i`. |
| `mobileUK` | Permet un numéro de téléphone portable (Royaume-Uni). |
| `no-marginal-whitespace` | Désactive les espaces au début ou à la fin de la valeur. |
| `no-whitespace` | Interdit les espaces blancs. |
| `phoneUK` | Permet un numéro de téléphone (Royaume-Uni). |
| `phoneUS` | Permet un numéro de téléphone (États-Unis). |
| `required-entry` | Désactive la valeur vide (validation équivalente en tant que `validate-no-empty`).<br>Message d’échec de validation : &quot;Il s’agit d’un champ obligatoire.&quot; |
| `time` | Permet une heure valide au format 24 heures, entre 00:00 et 23:59. Par exemple `15`, `15:05` ou `15:05:48`. |
| `time12h` | Permet une heure valide au format 12 heures, entre 00h00 et 11h00:59:17 h. Par exemple `3 am`, `11:30 pm`, `02:15:00 pm`. |
| `validate-admin-password` | Autorise 7 caractères ou plus, à l’aide de caractères numériques et alphabétiques. |
| `validate-alphanum-with-spaces` | Permet l’utilisation de lettres (a-z ou A-Z), de nombres (0-9) ou d’espaces uniquement. |
| `validate-clean-url` | Permet une URL valide. Par exemple : `https://www.example.com` ou `www.example.com`. |
| `validate-currency-dollar` | Permet un montant valide (dollar). Par exemple, 100,00 $. |
| `validate-data` | N’autorise l’utilisation que de lettres (a-z ou A-Z), de chiffres (0-9) ou de traits de soulignement (\_).<br>Le premier caractère doit être une lettre.<br>(Doit correspondre à l’expression : `/^[A-Za-z]+[A-Za-z0-9_]+$/`)<br>Message d’échec de validation : &quot;N’utilisez que des lettres (a-z ou A-Z), des chiffres (0-9) ou un trait de soulignement (\_) dans ce champ, et le premier caractère doit être une lettre.&quot; |
| `validate-date-au` | Applique le format de date suivant : jj/mm/aaaa. Par exemple, 17/03/2006 pour le 17 mars 2006. |
| `validate-email` | Permet une adresse électronique valide. Par exemple, johndoe@domain.com. |
| `validate-emailSender` | Permet une adresse électronique valide. Par exemple, johndoe@domain.com. |
| `validate-fax` | Permet un numéro de fax valide. Par exemple, 123-456-7890. |
| `validate-no-empty` | Désactive la valeur vide (validation équivalente en tant que `requried-entry`).<br>Message d’échec de validation : &quot;Valeur vide.&quot; |
| `validate-no-html-tags` | Désactive l’utilisation des balises de HTML. |
| `validate-password` | Autorise 6 caractères ou plus. Les espaces de début et de fin seront ignorés. |
| `validate-phoneLax` | Permet un numéro de téléphone valide. Par exemple, (123) 456-7890 ou 123-456-7890. |
| `validate-phoneStrict` | Permet un numéro de téléphone valide. Par exemple, (123) 456-7890 ou 123-456-7890. |
| `validate-select` | Impose que l’option sélectionnée sélectionnée ne comporte pas de `null` valeur, valeur de chaîne de `none` ou longueur de chaîne de 0. |
| `validate-ssn` | Autorise un numéro de sécurité sociale (US) valide. Par exemple, 123-45-6789. |
| `validate-street` | Autorise l’utilisation des lettres (a-z ou A-Z), des nombres (0-9), des espaces et du caractère &quot;#&quot; uniquement. |
| `validate-url` | Permet une URL valide. Le protocole est requis (http://, https:// ou ftp://). |
| `validate-xml-identifier` | Permet un identifiant XML valide. Par exemple, quelque chose_1, bloc5, id-4. |
| `validate-zip-us` | Autorise un code postal (US) valide. Par exemple, 90602 ou 90602-1234. |
| `vinUS` | Permet la valeur du numéro d’identification du véhicule (E.U.). |

### Valeurs par défaut

Les valeurs par défaut des champs peuvent être définies dans le `etc/config.xml` en spécifiant la valeur par défaut dans la variable `section/group/field_ID` noeud .

#### Exemple : Définition de la valeur par défaut pour `ANOTHER_UNIQUE_FIELD_ID` (Portée par défaut)

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <default>
        <A_UNIQUE_SECTION_ID>
            <A_UNIQUE_GROUP_ID>
                <ANOTHER_UNIQUE_FIELD_ID>This is the default value</ANOTHER_UNIQUE_FIELD_ID>
            </A_UNIQUE_GROUP_ID>
        </A_UNIQUE_SECTION_ID>
    </default>
</config>
```

#### Exemple : Définition de la valeur par défaut pour `ANOTHER_UNIQUE_FIELD_ID` (Portée du site web)

En utilisant la variable `websites` , spécifiez la valeur par défaut d’un site web spécifique.

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <websites>
        <WEBSITE_CODE>
            <A_UNIQUE_SECTION_ID>
                <A_UNIQUE_GROUP_ID>
                    <ANOTHER_UNIQUE_FIELD_ID>This is the default value</ANOTHER_UNIQUE_FIELD_ID>
                </A_UNIQUE_GROUP_ID>
            </A_UNIQUE_SECTION_ID>
        </WEBSITE_CODE>
    </websites>
</config>
```
