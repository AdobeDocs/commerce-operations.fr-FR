---
title: Génération d’un rapport d’état des correctifs
description: Découvrez comment utiliser pour générer  [!DNL Commerce Version Tool]  rapports d’état des correctifs Adobe Commerce au format JSON ou CSV.
TQID: 'https://experienceleague.adobe.com/-lC-20YMpbTM3tTZjbBO5zD5gb9n7cRah5Ycy8wQoyw'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b5f00040-57a0-4a6d-a39e-383b1936c2c9id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: c1579802-ddd4-4214-8a91-97b2066abe11id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: cb0391ae368b53a795535f3adb636628a339b963
workflow-type: tm+mt
source-wordcount: 590
ht-degree: 2%

---

# Génération d’un rapport d’état des correctifs

Utilisez [!DNL Commerce Version Tool] ([!DNL CVT]) pour générer un rapport d’état des correctifs pour une installation d’Adobe Commerce. Le rapport identifie les correctifs de sécurité mensuels appliqués, manquants et inconnus et renvoie la sortie JSON par défaut.

## Conditions préalables

Avant d’exécuter [!DNL CVT], vérifiez les points suivants :

- L’installation cible utilise une version et une édition d’Adobe Commerce prises en charge.
- `composer.lock` est présent et correspond à l’environnement que vous souhaitez inspecter.
- PHP et le système `patch` binaire sont disponibles.
- Vous pouvez lire les fichiers du projet à partir de l’environnement dans lequel vous exécutez la commande .
- L’outil peut écrire dans `var/patch_metadata/` et `var/log/` si vous souhaitez des fichiers cache et des entrées de journal d’audit.
- Les informations d’identification sont disponibles via `COMPOSER_AUTH` ou `auth.json` si des correctifs avec droits d’accès s’appliquent à l’installation.

L’outil [!DNL CVT] vérifie les informations d’identification de correctif `COMPOSER_AUTH`, le `auth.json` de projet Adobe Commerce et le `auth.json` du compositeur global.

## Générer le rapport

À partir de la racine du projet Adobe Commerce, exécutez :

```bash
php vendor/bin/patch-status
```

Pour vérifier une autre installation d’Adobe Commerce, utilisez l’option `--root` :

```bash
php vendor/bin/patch-status --root=/path/to/commerce
```

## Options des commandes

JSON est le format de sortie par défaut. La sortie CSV est prise en charge pour les analyseurs, les tableaux de bord et les rapports de conformité.

| Option | Description |
| --- | --- |
| `--root=PATH` | Indique le chemin d’accès à la racine d’installation d’Adobe Commerce. La valeur par défaut est le répertoire actif. |
| `--format=json\|csv` | Définit le format de sortie. La valeur par défaut est `json`. |
| `--no-cache` | Ignore les caches de registre et de comparaison des correctifs, force de nouvelles récupérations distantes et se ferme avec une erreur si le registre distant n&#39;est pas disponible. |
| `--version`, `-V` | Imprime la version de l’outil. |
| `--help`, `-h` | Imprime le message d’aide. |

{style="table-layout:auto"}

## Vérifier la sortie JSON et CSV

L’exemple suivant affiche la sortie JSON par défaut.

```bash
php vendor/bin/patch-status
```

```json
{
  "base_version": "2.4.7-p9",
  "installed_components": {
    "CE": "2.4.7-p9",
    "EE": "2.4.7-p9",
    "B2B": "1.5.2-p5"
  },
  "applied_patches": [
    "247p9-2026-05-001-CE",
    "247p9-2026-05-001-EE"
  ],
  "missing_patches": [
    "247p9-2026-06-001-CE",
    "247p9-2026-06-001-EE"
  ],
  "unknown_patches": [],
  "vulnerability_status": {
    "CVE-2026-12354": { "status": "PROTECTED" },
    "CVE-2026-67890": { "status": "VULNERABLE" }
  },
  "registry_source": "remote",
  "warnings": []
}
```

Pour générer une sortie CSV, utilisez l’option `--format=csv` :

```bash
php vendor/bin/patch-status --format=csv
```

La sortie CSV produit une ligne par CVE et convient aux feuilles de calcul, aux scanners, aux tableaux de bord et aux outils de conformité.

## Comprendre les résultats du rapport

Examinez les correctifs manquants et inconnus avant de revendiquer le statut de sécurité.

### Valeurs de statut du correctif

Le rapport patch-status regroupe les résultats des patches selon les valeurs suivantes :

| Statut du correctif | Signification |
| --- | --- |
| Appliqué | L’outil [!DNL CVT] détecte le correctif de sécurité mensuel dans la base de code d’Adobe Commerce. |
| Manquant | Le correctif s’applique à la version ou au composant Adobe Commerce installé, mais l’outil [!DNL CVT] ne le détecte pas. |
| Inconnu | L’outil ne peut pas confirmer l’état du correctif à partir du registre disponible, de la comparaison des correctifs ou du résultat de la détection. |

{style="table-layout:auto"}

### Valeurs de statut CVE

La sortie JSON signale les valeurs de statut CVE en majuscules.

| Statut CVE | Signification |
| --- | --- |
| `PROTECTED` | Le correctif applicable est détecté pour le CVE ou le composant. |
| `VULNERABLE` | Il manque un correctif applicable pour le CVE ou le composant. |
| `UNKNOWN` | L’outil [!DNL CVT] ne peut pas déterminer l’état du fichier CVE à partir des données de registre et de détection disponibles. |
| `NOT_APPLICABLE` | Le CVE s’applique à un composant qui n’est pas installé, comme Adobe Commerce business-to-business (B2B), Adobe Commerce Page Builder ou Adobe Commerce Inventory. |

{style="table-layout:auto"}

### Champs de sortie clés

Le rapport peut inclure les informations suivantes :

- **Version de base d’Adobe Commerce** - Version de base installée détectée depuis `composer.lock`.
- **Source du registre** - Indique si les métadonnées de correctif proviennent de `remote`, `cache` ou `stale_cache`.
- **Composants installés** - zones de package Adobe Commerce détectées depuis `composer.lock`.
- **Correctifs appliqués** - Correctifs de sécurité mensuels détectés dans la base de code Adobe Commerce.
- **Correctifs manquants** - Correctifs de sécurité mensuels qui s’appliquent, mais ne sont pas détectés.
- **Correctifs inconnus** - Correctifs que l’outil [!DNL CVT] ne peut pas classer.
- **État de vulnérabilité par CVE** - Couverture CVE mappée à un état protégé, vulnérable, sans objet ou inconnu.
- **Avertissements** - Conditions susceptibles d&#39;affecter la fiabilité ou l&#39;exhaustivité du rapport.

## Registre et cache des correctifs

Le fichier de registre des correctifs contient les métadonnées de correctif utilisées par l&#39;outil [!DNL CVT] pour déterminer les correctifs qui s&#39;appliquent à une version installée. L’outil utilise un nouveau cache de registre lorsqu’il est disponible, récupère le registre distant si nécessaire et peut utiliser un cache obsolète avec un avertissement si le réseau n’est pas disponible. N’utilisez `--no-cache` que lorsque vous avez besoin d’effectuer de nouvelles récupérations à distance.

## Rubriques connexes

- [Introduction](intro.md)
- [Dépannage](troubleshooting.md)
- [Notes de mise à jour](release-notes.md)
