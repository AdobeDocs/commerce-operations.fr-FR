---
title: Tâche cron personnalisée et référence de groupe cron
description: Découvrez comment personnaliser les crons à l’aide de groupes cron.
source-git-commit: ee2e446edf79efcd7cbbd67248f8e7ece06bfefd
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---


# Personnalisation de la référence des crons

Cette rubrique vous aide à configurer des onglets et éventuellement des groupes cron pour les modules personnalisés. Si votre [module](https://glossary.magento.com/module) doit planifier des tâches périodiquement, vous devez configurer un crontab pour ce module. A _crontab_ est une configuration de tâche cron.

Vous pouvez éventuellement configurer un groupe personnalisé qui vous permet, entre autres, d’exécuter des tâches cron définies dans ce groupe indépendamment des autres tâches cron.

Pour consulter un tutoriel détaillé, voir [Configuration de tâches cron personnalisées et de groupes cron (tutoriel)](custom-cron-tutorial.md).

Pour obtenir un aperçu des tâches cron, voir [Configuration des tâches cron](../cli/configure-cron-jobs.md).

## Configuration des groupes cron

Cette section explique comment créer éventuellement un groupe cron pour un module personnalisé. Si vous n’avez pas besoin de le faire, passez à la section suivante.

A _groupe cron_ est un groupe logique qui permet d’exécuter facilement cron pour plusieurs processus à la fois. La plupart des modules Commerce utilisent la variable `default` le groupe cron; certains modules utilisent la méthode `index` groupe.

Si vous implémentez cron pour un module personnalisé, vous pouvez choisir d’utiliser la variable `default` ou un autre groupe.

**Pour configurer un groupe cron pour votre module**:

Créez un `crontab.xml` dans votre répertoire de module :

```text
<your component base dir>/<vendorname>/module-<name>/etc/crontab.xml
```

Pour un groupe, le fichier doit contenir les contenus suivants :

```xml
<config>
    <group id="<group_name>">
        <job name="<job_name>" instance="<classpath>" method="<method>">
            <schedule><time></schedule>
        </job>
    </group>
</config>
```

Où :

| Valeur | Description |
|---|---|
| `group_name` | Nom du groupe cron. Le nom du groupe ne doit pas nécessairement être unique. Vous pouvez exécuter cron pour un groupe à la fois. |
| `job_name` | Identifiant unique de cette tâche cron. |
| `classpath` | Classe à instancier (classpath). |
| `method` | Méthode dans `classpath` pour appeler. |
| `time` | Planification au format cron. Omettez ce paramètre si la planification est définie dans la base de données Commerce ou dans un autre espace de stockage. |

Le résultat `crontab.xml` avec deux groupes peut ressembler à ceci :

```xml
<config>
    <group id="default">
        <job name="<job_1_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
        <job name="<job_2_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
    </group>
    <group id="index">
        <job name="<job_3_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
        <job name="<job_4_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
    </group>
</config>
```

À titre d’exemple, reportez-vous à la section [Magento_Customer crontab.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/crontab.xml).

### Définition des options du groupe Cron

Vous pouvez déclarer un nouveau groupe et spécifier ses options de configuration (toutes exécutées dans [vue de magasin](https://glossary.magento.com/store-view) portée) via le `cron_groups.xml` fichier situé dans :

```text
<your component base dir>/<vendorname>/module-<name>/etc/cron_groups.xml
```

Vous trouverez ci-dessous un exemple de la fonction `cron_groups.xml` fichier :

```xml
<config>
    <group id="<group_name>">
        <schedule_generate_every>1</schedule_generate_every>
        <schedule_ahead_for>4</schedule_ahead_for>
        <schedule_lifetime>2</schedule_lifetime>
        <history_cleanup_every>10</history_cleanup_every>
        <history_success_lifetime>60</history_success_lifetime>
        <history_failure_lifetime>600</history_failure_lifetime>
        <use_separate_process>1</use_separate_process>
    </group>
</config>
```

Où :

| Option | Description |
| -------------------------- | ------------------------------------------------------------------------------------------------------ |
| `schedule_generate_every` | Fréquence (en minutes) pendant laquelle les plannings sont écrits dans la variable `cron_schedule` table. |
| `schedule_ahead_for` | Heure (en minutes) à l’avance à laquelle les plannings sont écrits dans la variable `cron_schedule` table. |
| `schedule_lifetime` | Fenêtre de temps (en minutes) pendant laquelle une tâche cron doit démarrer ou la tâche cron est considérée comme manquée (&quot;trop tard&quot; pour s’exécuter). |
| `history_cleanup_every` | Durée (en minutes) pendant laquelle l’historique cron est conservé dans la base de données. |
| `history_success_lifetime` | Temps (en minutes) pendant lequel l’enregistrement des tâches cron terminées est conservé dans la base de données. |
| `history_failure_lifetime` | Temps (en minutes) pendant lequel l’enregistrement des tâches cron en échec est conservé dans la base de données. |
| `use_separate_process` | Exécution des tâches de ce groupe cron dans un processus php distinct |

## Désactivation d’une tâche cron

Les tâches Cron n’ont pas de `disable` comme nous l’avons fait pour [observateurs](https://developer.adobe.com/commerce/php/development/components/events-and-observers/#observers). Cependant, une tâche cron peut être désactivée en utilisant la technique suivante : `schedule` une heure contenant une date qui ne se produira jamais.

Par exemple, désactivez la variable `visitor_clean` tâche cron définie dans `Magento_Customer` module :

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 * * *</schedule>
    </job>
</group>
...
```

Pour désactiver la fonction `visitor_clean` tâche cron, créez un module personnalisé et réécrivez `visitor_clean` tâche cron `schedule`:

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 30 2 *</schedule>
    </job>
</group>
...
```

Maintenant, le `visitor_clean` La tâche cron a été définie pour s’exécuter à 00:00 le 30 février, à la date qui ne se produira jamais.
