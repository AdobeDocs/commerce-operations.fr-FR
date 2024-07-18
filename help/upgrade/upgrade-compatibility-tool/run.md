---
title: Exécutez la fonction [!DNL Upgrade Compatibility Tool]
description: Suivez ces étapes pour exécuter  [!DNL Upgrade Compatibility Tool]  dans une interface de ligne de commande pour votre projet Adobe Commerce.
exl-id: ea467a74-18eb-476b-96e2-23f4fc257d73
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '1077'
ht-degree: 0%

---

# Téléchargez le [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

Pour commencer à utiliser le [!DNL Upgrade Compatibility Tool] dans une interface de ligne de commande, téléchargez-le en exécutant la commande suivante :

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

Vous devrez peut-être accorder à l’outil des autorisations exécutables avec la commande `chmod` :

```bash
chmod +x ./uct/bin/uct
```

## [!DNL Upgrade Compatibility Tool] dans une interface de ligne de commande

[!DNL Upgrade Compatibility Tool] est un outil qui vérifie une instance personnalisée Adobe Commerce par rapport à une version spécifique en analysant tous les modules qui y sont installés. Elle renvoie une liste des problèmes, erreurs et avertissements critiques qui doivent être résolus avant la mise à niveau vers la dernière version d’Adobe Commerce.

Consultez ce [tutoriel vidéo](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02) pour en savoir plus sur [!DNL Upgrade Compatibility Tool].

Commandes disponibles pour [!DNL Upgrade Compatibility Tool] dans une interface de ligne de commande :

| **Commande** | **Description** |
|----------------|-----------------|
| `upgrade:check` | Cette commande exécute le [!DNL Upgrade Compatibility Tool] en analysant tous les modules qui y sont installés. |
| `dbschema:diff` | Cette commande affiche toutes les différences de schéma de base de données entre deux versions Adobe Commerce spécifiées. |
| `core:code:changes` | Cette commande compare votre installation actuelle d’Adobe Commerce à une installation Vanilla propre. |
| `refactor` | Cette commande corrige automatiquement un ensemble réduit de problèmes. |
| `graphql:compare` | Cette commande permet d’analyser deux points de terminaison GraphQL et de comparer leurs schémas. |
| `list` | Cette commande renvoie une liste de toutes les commandes [!DNL Upgrade Compatibility Tool] disponibles. |
| `help` | Cette commande renvoie toutes les options `help`disponibles pour [!DNL Upgrade Compatibility Tool]. Cette commande peut être exécutée ainsi qu&#39;une option avec les commandes précédentes. |

## Utilisation de la commande `upgrade:check`

La commande `upgrade:check` recherche les modifications de code principal pour cette instance Adobe Commerce spécifique et toutes les modifications de code personnalisé qui y sont installées.

La commande `upgrade:check` est la commande principale pour exécuter l’outil :

```bash
bin/uct upgrade:check <dir>
```

Où la valeur `<dir>` est le répertoire dans lequel se trouve votre instance Adobe Commerce.

Options disponibles pour la commande `upgrade:check` :

| **Commande** | **Options disponibles** |
|----------------|-----------------|
| `upgrade:check` | <ul><li>—help : renvoie toutes les options disponibles.</li><li>—current-version : version Adobe Commerce actuelle. Ce paramètre est obligatoire et doit toujours être utilisé.</li><li>—min-issue-level : vous pouvez filtrer les problèmes en fonction du niveau de problème minimum (la valeur par défaut est WARNING).</li><li>—ignore-current-version-compatibility-issues (ou -i) : si vous ne souhaitez pas inclure de problèmes critiques, d’erreurs et d’avertissements de la version actuelle dans votre rapport.</li><li>—coming-version (ou -c) : ciblez une version spécifique d’Adobe Commerce. La dernière version disponible sera utilisée si elle est omise.</li></ul> |

[!DNL Upgrade Compatibility Tool] permet d&#39;exécuter la commande `upgrade:check` avec une option `--ignore-current-version-compatibility-issues`. Utilisez cette option lorsque vous souhaitez uniquement obtenir de nouveaux problèmes introduits avec la mise à jour de votre version actuelle vers la version ciblée dans votre rapport [!DNL Upgrade Compatibility Tool] :

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
> Cela s’applique uniquement aux validations d’API PHP.

### Ajout de l’option `--coming-version`

Vous pouvez comparer votre installation actuelle d’Adobe Commerce avec n’importe quelle version d’Adobe Commerce `>=2.3` à l’aide de l’option `--coming-version` .

Vous devez fournir la version comme paramètre lors de l’exécution de la commande `upgrade:check` :

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

Où `-c, --coming-version[=COMING-VERSION]` fait référence à la version ciblée Adobe Commerce.

Il existe certaines limites lors de l’exécution de l’ `--coming-version` :

- Ce paramètre fait référence à toute balise qui identifie une version spécifique d’Adobe Commerce.
- Il est nécessaire de fournir explicitement celui-ci ; fournir uniquement la valeur de celui-ci ne fonctionne pas.
- Fournissez la version de la balise sans guillemets (ni simples ni doubles) : ~~&#39;2.4.1-develop&#39;~~.
- Vous ne devez PAS fournir d’anciennes versions que celle que vous avez installée actuellement, ni plus de 2.3, qui est la plus ancienne version prise en charge pour le moment.

## Utilisation de la commande `dbschema:diff`

Vous pouvez récupérer la différence entre le schéma de base de données de deux versions d’Adobe Commerce.

```bash
bin/uct dbschema:diff <current-version> <target-version>
```

Où les arguments sont les suivants :

- `<current-version>` : toute version Adobe Commerce à des fins de comparaison.
- `<target-version>` : également toute version Adobe Commerce à des fins de comparaison.

Exemple d&#39;exécution :

```bash
bin/uct dbschema:diff 2.4.3 2.4.3-p3

DB schema differences between versions 2.4.3 and 2.4.3-p3:

Table klarna_payments_quote constraint QUOTE_ID_KLARNA_PAYMENTS_QUOTE_QUOTE_ID_QUOTE_ENTITY_ID is present only in version 2.4.3-p3
Table klarna_payments_quote index KLARNA_PAYMENTS_QUOTE_SESSION_ID is present only in version 2.4.3-p3
Table customer_entity column session_cutoff is present only in version 2.4.3-p3
Table customer_visitor column session_id length value is different. 2.4.3: "64", 2.4.3-p3: "1"
Table customer_visitor column session_id comment value is different. 2.4.3: "Session ID", 2.4.3-p3: "Deprecated: Session ID value no longer used"
Table customer_visitor column created_at is present only in version 2.4.3-p3
Table oauth_consumer column secret length value is different. 2.4.3: "32", 2.4.3-p3: "128"
Table oauth_token column secret length value is different. 2.4.3: "32", 2.4.3-p3: "128"
Table admin_user_session column session_id nullable value is different. 2.4.3: "false", 2.4.3-p3: "true"
Table admin_user_session column session_id length value is different. 2.4.3: "128", 2.4.3-p3: "1"
Table admin_user_session column session_id comment value is different. 2.4.3: "Session ID value", 2.4.3-p3: "Deprecated: Session ID value no longer used"

Total detected differences between version 2.4.3 and 2.4.3-p3: 11
```

## Utilisation de la commande `core:code:changes`

Vous pouvez comparer votre installation Adobe Commerce actuelle pour vérifier si le code principal d’Adobe Commerce a été modifié pour mettre en oeuvre une personnalisation. Cette commande affiche uniquement une liste des modifications principales :

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

Où les arguments sont les suivants :

- `<dir>` : répertoire d’installation Adobe Commerce.
- `<vanilla dir>` : répertoire d’installation Adobe Commerce vanilla.

Options disponibles pour la commande `core:code:changes` :

| **Commande** | **Options disponibles** |
|----------------|-----------------|
| `core:code:changes` | `--help` : renvoie toutes les options `--help` disponibles. |

>[!NOTE]
>
> Il est recommandé d’exclure le code personnalisé du code principal. Consultez le [guide de mise à niveau](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) d’Adobe Commerce 2.4 pour plus d’informations sur les bonnes pratiques de mise à niveau.

### Installation de vanille

Une installation _vanilla_ est une installation propre d’une balise ou d’une branche de version spécifiée pour une version spécifique.

La commande `bin/uct core:code:changes` vérifie si votre système contient une instance Vanilla. Si c’est la première fois que vous utilisez une installation Vanilla, une question de ligne de commande interactive vous invite à télécharger le projet Vanilla à partir du référentiel Adobe Commerce (`https://repo.magento.com/`).

Vous pouvez exécuter une commande [!DNL Upgrade Compatibility Tool] avec l’option `--vanilla-dir` pour spécifier le répertoire d’installation Vanilla Adobe Commerce.

Pour plus d’informations, consultez la rubrique [Déployer l’instance Vanilla](https://developer.adobe.com/commerce/contributor/guides/code-contributions/#deploy-vanilla-magento-open-source-instance) .

## Utilisation de la commande `refactor`

Le [!DNL Upgrade Compatibility Tool] peut résoudre automatiquement un ensemble réduit de problèmes :

- Fonctions qui étaient autorisées à être utilisées sans passer d’argument, mais avec une telle utilisation désormais obsolète.
- Utilisation de `$this` dans les modèles de Magento.
- Utilisation du mot-clé PHP `final` dans des méthodes privées.

Pour cela, exécutez la commande `refactor` :

```bash
bin/uct refactor <dir>
```

Où la valeur `<dir>` est le répertoire dans lequel se trouve votre instance Adobe Commerce.

Options disponibles pour la commande `refactor` :

| **Commande** | **Options disponibles** |
|----------------|-----------------|
| `refactor` | `--help` : renvoie toutes les options `--help` disponibles. |

## Utilisation de la commande `graphql:compare`

Cette commande permet à [!DNL Upgrade Compatibility Tool] d’analyser deux points de terminaison GraphQL et de comparer leurs schémas afin de rechercher des modifications risquées et entraînant des ruptures :

```bash
bin/uct graphql:compare <schema1> <schema2>
```

Où les arguments sont les suivants :

- `<schema1>` : URL du point d’entrée pour l’installation existante.
- `<schema2>` : URL du point d’entrée pour l’installation Vanilla.

Options disponibles pour la commande `graphql:compare` :

| **Commande** | **Options disponibles** |
|----------------|-----------------|
| `graphql:compare` | `--help` : renvoie toutes les options `--help` disponibles. |

## Utilisation de la commande `list`

Pour renvoyer une liste des commandes disponibles [!DNL Upgrade Compatibility Tool], exécutez :

```bash
bin/uct list
```

## Utilisation de la commande `help`

Pour afficher les options générales de la commande [!DNL Upgrade Compatibility Tool] et obtenir de l’aide, exécutez :

```bash
bin/uct --help
```

Elle renvoie une liste contenant toutes les options `help` disponibles pour [!DNL Upgrade Compatibility Tool] dans une interface de ligne de commande :

```
- --raw             To output raw command list
- --format=FORMAT   The output format (txt, xml, json, or md) [default: "txt"]
- --short           To skip describing commands' arguments
- -h, --help            Display help for the given command. When no command is given display help for the list command
- -q, --quiet           Do not output any message
- -V, --version         Display this application version
- --ansi|--no-ansi  Force (or disable --no-ansi) ANSI output
- -n, --no-interaction  Do not ask any interactive question
- -v|vv|vvv, --verbose  Increase the verbosity of messages: 1 for normal output, 2 for more verbose output and 3 for debug
```

Il est possible d&#39;exécuter `--help` comme option lors de l&#39;exécution d&#39;une commande spécifique. Elle renvoie `--help` options pour la commande spécifiée.

Exemple de commande `upgrade:check` avec l&#39;option `--help` :

```bash
bin/uct upgrade:check --help
```

Elle renvoie des options spécifiques pouvant être exécutées pour la commande `upgrade:check` :

```
- -a, --current-version[=CURRENT-VERSION]: Current Adobe Commerce version, version of the Adobe Commerce installation will be used if omitted.
- -c, --coming-version[=COMING-VERSION]: Target Adobe Commerce version, latest released version of Adobe Commerce will be used if omitted. Provides a list of all available Adobe Commerce versions.
- --json-output-path[=JSON-OUTPUT-PATH]: Path of the file where the output will be exported in json format.
- --html-output-path[=HTML-OUTPUT-PATH]: Path of the file where the output will be exported in HTML format.
- --min-issue-level[=MIN-ISSUE-LEVEL]            Minimal issue level you want to see in the report (warning, error or critical). [default: "warning"]
- -i, --ignore-current-version-compatibility-issues  Ignore common issues for current and coming version
- --context=CONTEXT: Execution context. This option is for integration purposes and does not affect the execution result.
- -h, --help: Display help for that specific command. If no command is provided, `list` command is the default result.
- -q, --quiet: Do not output any messages while executing the command.
- -v, --version: Display application version.
- --ansi, --no-ansi: Enable ANSI output.
- -n, --no-interaction: Do not ask any interactive question while executing the command.
- -v, --vv, --vvv, --verbose: Increase verbosity of output communications. 1 for normal output, 2 for verbose output, and 3 for DEBUG output.
```

## Suivre les bonnes pratiques d’Adobe Commerce

- Évitez d’avoir deux modules portant le même nom.
- Suivez les [normes de codage](https://developer.adobe.com/commerce/php/coding-standards/) d’Adobe Commerce.
- Bonnes pratiques relatives à la mise à niveau vers Adobe Commerce 2.4 [Guide de mise à niveau](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf).
- Exécutez le [!DNL Upgrade Compatibility Tool] à partir des projets [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html) pour [Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html){target=_blank}.

## Optimiser vos résultats

[!DNL Upgrade Compatibility Tool] fournit un rapport contenant les résultats avec tous les problèmes identifiés par défaut sur votre projet. Vous pouvez optimiser les résultats pour vous concentrer sur les problèmes que vous devez corriger pour terminer la mise à niveau :

- Utilisez l’option `--ignore-current-version-compatibility-issues` lorsque vous souhaitez uniquement obtenir de nouveaux problèmes introduits avec la mise à jour de votre version actuelle vers la version ciblée de votre rapport [!DNL Upgrade Compatibility Tool].
- En ajoutant l’option `--min-issue-level`, ce paramètre permet de définir le niveau de problème minimum, afin de n’aider à classer par priorité que les problèmes les plus importants liés à votre mise à niveau.
- L’exécution de [!DNL Upgrade Compatibility Tool] nécessite au moins 2 Go de mémoire vive. Ce paramètre est recommandé pour éviter les problèmes en raison d’une faible limitation de mémoire. [!DNL Upgrade Compatibility Tool] affiche une question si vous exécutez la commande `upgrade:check` avec un paramètre `memory_limit` faible.
