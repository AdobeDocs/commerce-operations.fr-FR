---
title: Exécutez  [!DNL Upgrade Compatibility Tool]
description: Pour exécuter le dans une interface  [!DNL Upgrade Compatibility Tool]  ligne de commande pour votre projet Adobe Commerce, procédez comme suit.
exl-id: ea467a74-18eb-476b-96e2-23f4fc257d73
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 0%

---

# Télécharger le [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

Pour commencer à utiliser le [!DNL Upgrade Compatibility Tool] dans une interface de ligne de commande, téléchargez-le en exécutant la commande suivante :

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

Vous devrez peut-être donner à l’outil des autorisations exécutables avec la commande `chmod` :

```bash
chmod +x ./uct/bin/uct
```

## [!DNL Upgrade Compatibility Tool] dans une interface de ligne de commande

Le [!DNL Upgrade Compatibility Tool] est un outil qui compare une instance personnalisée Adobe Commerce à une version spécifique en analysant tous les modules qui y sont installés. Elle renvoie une liste des problèmes, erreurs et avertissements critiques qui doivent être résolus avant la mise à niveau vers la dernière version d’Adobe Commerce.

Voir ce [tutoriel vidéo](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=fr) (06:02) pour en savoir plus sur le [!DNL Upgrade Compatibility Tool].

Commandes disponibles pour le [!DNL Upgrade Compatibility Tool] dans une interface de ligne de commande :

| **Commande** | **Description** |
|----------------|-----------------|
| `upgrade:check` | Cette commande exécute le [!DNL Upgrade Compatibility Tool] en analysant tous les modules qui y sont installés. |
| `dbschema:diff` | Cette commande affiche toutes les différences de schéma de base de données entre deux versions Adobe Commerce spécifiées. |
| `core:code:changes` | Cette commande compare votre installation Adobe Commerce actuelle à une installation classique. |
| `refactor` | Cette commande corrige automatiquement un ensemble réduit de problèmes. |
| `graphql:compare` | Cette commande permet d’inspecter deux points d’entrée GraphQL et de comparer leurs schémas. |
| `list` | Cette commande renvoie une liste de toutes les commandes [!DNL Upgrade Compatibility Tool] disponibles. |
| `help` | Cette commande renvoie toutes les options `help` disponibles pour la [!DNL Upgrade Compatibility Tool]. Cette commande peut être exécutée, ainsi qu’une option avec les commandes précédentes. |

## Utiliser la commande `upgrade:check`

La commande `upgrade:check` recherche les modifications du code principal pour cette instance Adobe Commerce spécifique et toutes les modifications du code personnalisé installées dans celle-ci.

La commande `upgrade:check` est la commande principale pour exécuter l&#39;outil :

```bash
bin/uct upgrade:check <dir>
```

Où `<dir>` valeur correspond au répertoire où se trouve votre instance Adobe Commerce.

Options disponibles pour la commande `upgrade:check` :

| **Commande** | **Options disponibles** |
|----------------|-----------------|
| `upgrade:check` | <ul><li>—help : renvoie toutes les options disponibles.</li><li>—current-version : version Adobe Commerce actuelle. La version de l’installation d’Adobe Commerce sera utilisée si elle est omise.</li><li>—min-issue-level : vous pouvez filtrer les événements en fonction du niveau minimal d’événement (la valeur par défaut est WARNING).</li><li>—ignore-current-version-compatibility-issues (ou -i) : si vous ne souhaitez pas inclure les problèmes critiques, les erreurs et les avertissements de la version actuelle dans votre rapport.</li><li>—coming-version (ou -c) : cible une version Adobe Commerce spécifique. La dernière disponible sera utilisée si elle est omise.</li></ul> |

Le [!DNL Upgrade Compatibility Tool] vous permet d’exécuter la commande `upgrade:check` avec une option de `--ignore-current-version-compatibility-issues`. Utilisez cette option uniquement lorsque vous souhaitez obtenir les nouveaux problèmes introduits avec la mise à jour de votre version actuelle vers la version ciblée dans votre rapport [!DNL Upgrade Compatibility Tool] :

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
> Cela s’applique uniquement aux validations d’API PHP.

### Ajout de l’option `--coming-version`

Vous pouvez comparer votre installation Adobe Commerce actuelle à n’importe quelle version d’Adobe Commerce `>=2.3` à l’aide de l’option `--coming-version` .

Vous devez fournir la version sous forme de paramètre lors de l’exécution de la commande `upgrade:check` :

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

où `-c, --coming-version[=COMING-VERSION]` fait référence à la version ciblée d’Adobe Commerce.

Il existe certaines limitations lors de l’exécution du `--coming-version` :

- Ce paramètre fait référence à toute balise qui identifie une version spécifique d’Adobe Commerce.
- Il est obligatoire de fournir celui-ci explicitement ; fournir uniquement la valeur de celui-ci ne fonctionne pas.
- Fournissez la version de balise sans guillemets (ni simples ni doubles) : ~~&#39;2.4.1-develop&#39;~~.
- Vous ne devez PAS fournir de versions antérieures à celle que vous avez actuellement installée, ni antérieures à la version 2.3, qui est la plus ancienne prise en charge pour le moment.

## Utiliser la commande `dbschema:diff`

Vous pouvez récupérer la différence entre le schéma de base de données de deux versions d’Adobe Commerce.

```bash
bin/uct dbschema:diff <current-version> <target-version>
```

Où les arguments sont les suivants :

- `<current-version>` : toute version d’Adobe Commerce à des fins de comparaison.
- `<target-version>` : également toute version d’Adobe Commerce à des fins de comparaison.

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

## Utiliser la commande `core:code:changes`

Vous pouvez comparer votre installation Adobe Commerce actuelle pour vérifier si le code de base d’Adobe Commerce a été modifié afin d’implémenter une personnalisation. Cette commande affiche uniquement une liste des modifications principales :

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

Où les arguments sont les suivants :

- `<dir>` : répertoire d’installation d’Adobe Commerce.
- `<vanilla dir>` : répertoire d’installation Adobe Commerce vanilla.

Options disponibles pour la commande `core:code:changes` :

| **Commande** | **Options disponibles** |
|----------------|-----------------|
| `core:code:changes` | `--help` : renvoie toutes les options de `--help` disponibles. |

>[!NOTE]
>
> Il est recommandé de tenir le code personnalisé en dehors du code principal. Pour connaître les bonnes pratiques de mise à niveau[&#x200B; consultez le &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf?lang=fr) guide de mise à niveau d’Adobe Commerce 2.4 .

### Installation Vanilla

Une installation _vanilla_ est une installation propre d’une balise ou d’une branche de version spécifiée pour une version spécifique.

La commande `bin/uct core:code:changes` vérifie s’il existe une instance classique dans votre système. Si c’est la première fois que vous utilisez une installation classique, une question interactive en ligne de commande vous invite à télécharger le projet classique à partir du référentiel Adobe Commerce (`https://repo.magento.com/`).

Vous pouvez exécuter une commande [!DNL Upgrade Compatibility Tool] avec l’option `--vanilla-dir` pour spécifier le répertoire d’installation d’Adobe Commerce vanilla.

Voir la rubrique [Déployer une instance Vanilla](https://developer.adobe.com/commerce/contributor/guides/code-contributions/#deploy-vanilla-magento-open-source-instance) pour plus d’informations.

## Utiliser la commande `refactor`

Le [!DNL Upgrade Compatibility Tool] permet de résoudre automatiquement un ensemble réduit de problèmes :

- Fonctions qui pouvaient être utilisées sans transmettre d’argument, mais dont l’utilisation était désormais obsolète.
- Utilisation de `$this` dans les modèles Magento.
- Utilisation du mot-clé PHP `final` dans les méthodes privées.

Pour cela, exécutez la commande `refactor` :

```bash
bin/uct refactor <dir>
```

Où `<dir>` valeur correspond au répertoire où se trouve votre instance Adobe Commerce.

Options disponibles pour la commande `refactor` :

| **Commande** | **Options disponibles** |
|----------------|-----------------|
| `refactor` | `--help` : renvoie toutes les options de `--help` disponibles. |

## Utiliser la commande `graphql:compare`

Cette commande permet aux [!DNL Upgrade Compatibility Tool] d’inspecter deux points d’entrée GraphQL et de comparer leurs schémas à la recherche de modifications avec rupture et dangereuses entre eux :

```bash
bin/uct graphql:compare <schema1> <schema2>
```

Où les arguments sont les suivants :

- `<schema1>` : URL du point d’entrée pour l’installation existante.
- `<schema2>` : URL du point d’entrée pour l’installation Vanilla.

Options disponibles pour la commande `graphql:compare` :

| **Commande** | **Options disponibles** |
|----------------|-----------------|
| `graphql:compare` | `--help` : renvoie toutes les options de `--help` disponibles. |

## Utiliser la commande `list`

Pour renvoyer une liste des commandes [!DNL Upgrade Compatibility Tool] disponibles, exécutez :

```bash
bin/uct list
```

## Utiliser la commande `help`

Pour afficher les options générales et l’aide de la commande [!DNL Upgrade Compatibility Tool], exécutez :

```bash
bin/uct --help
```

Cette opération renvoie une liste avec toutes les options de `help` disponibles pour le [!DNL Upgrade Compatibility Tool] dans une interface de ligne de commande :

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

Il est possible d’exécuter `--help` en tant qu’option lors de l’exécution d’une commande spécifique. Elle renvoie `--help` options de la commande spécifiée.

Exemple de la commande `upgrade:check` avec l&#39;option `--help` :

```bash
bin/uct upgrade:check --help
```

Cette opération renvoie des options spécifiques qui peuvent être exécutées pour la commande `upgrade:check` :

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

## Respect Des Bonnes Pratiques D’Adobe Commerce

- Évitez d’avoir deux modules portant le même nom.
- Respectez les normes de codage [Adobe Commerce](https://developer.adobe.com/commerce/php/coding-standards).
- Bonnes pratiques relatives au [&#x200B; guide de mise à niveau d’Adobe Commerce 2.4](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf?lang=fr)
- Exécutez le [!DNL Upgrade Compatibility Tool] à partir du [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html?lang=fr) pour les projets [Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=fr){target=_blank}.

## Optimisation des résultats

Le [!DNL Upgrade Compatibility Tool] fournit un rapport contenant les résultats avec tous les problèmes identifiés sur votre projet par défaut. Vous pouvez optimiser les résultats afin de vous concentrer sur les problèmes que vous devez résoudre pour terminer la mise à niveau :

- Utilisez l’option `--ignore-current-version-compatibility-issues` lorsque vous souhaitez uniquement obtenir les nouveaux problèmes introduits avec la mise à jour de votre version actuelle vers la version ciblée dans votre rapport [!DNL Upgrade Compatibility Tool].
- En ajoutant l’option `--min-issue-level` , ce paramètre permet de définir le niveau de problème minimal, afin de ne classer par priorité que les problèmes les plus importants de votre mise à niveau.
- Le [!DNL Upgrade Compatibility Tool] nécessite au moins 2 Go de RAM pour fonctionner. Ce paramètre est recommandé pour éviter les problèmes dus à une limitation de la mémoire. Le [!DNL Upgrade Compatibility Tool] affiche une question si vous exécutez la commande `upgrade:check` avec un paramètre de `memory_limit` faible.
