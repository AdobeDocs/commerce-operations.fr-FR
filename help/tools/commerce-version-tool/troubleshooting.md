---
title: Dépannage [!DNL Commerce Version Tool]
description: Découvrez comment résoudre les problèmes liés à la détection  [!DNL Commerce Version Tool]  compositeur, aux vérifications internes d’exécution d’essai, au cache du registre, à la sortie JSON et aux journaux d’audit.
TQID: 'https://experienceleague.adobe.com/JwRSy7pfM89WoifYUzTVPhR-WrDIvj2A2B8SaEnmyWM'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: c1579802-ddd4-4214-8a91-97b2066abe11id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: eafe79321da03f4778dd9e1b290141ef082a5eaf
workflow-type: tm+mt
source-wordcount: 1222
ht-degree: 0%

---

# Dépannage [!DNL Commerce Version Tool]

Utilisez cette page pour résoudre les problèmes courants de [!DNL Commerce Version Tool] ([!DNL CVT]) liés à la détection du compositeur, au chargement du registre, à la détection des correctifs d’exécution à sec internes, à la génération de sortie et à la journalisation d’audit.

## Étapes de dépannage rapide

Si l’outil de [!DNL CVT] ne renvoie pas le rapport d’état du correctif attendu :

- Vérifiez que l’installation cible utilise une version et une édition d’Adobe Commerce prises en charge.
- Vérifiez que `composer.lock` est présent et correspond à l’environnement que vous souhaitez inspecter.
- Vérifiez que PHP et le système `patch` binaire sont disponibles.
- Vérifiez que [!DNL CVT] pouvez lire le fichier de registre des correctifs.
- Examinez les `warnings`, les `missing_patches` et les `unknown_patches` dans la sortie.
- Vérifiez `var/log/patch_status.log` pour le résumé de l’audit de l’exécution, si le fichier journal est créé.

>[!TIP]
>
> Le fichier journal est particulièrement utile lorsque vous devez comprendre pourquoi un correctif n’a pas pu être classé. Pour chaque correctif inconnu, le journal enregistre la sortie brute des tentatives d’exécution d’essai suivantes et inversées, y compris les erreurs ou les échecs de bloc.
>
> Si vous rencontrez des problèmes lors de la récupération des fichiers de registre ou de correctif, vérifiez le champ avertissements dans le rapport. Ces détails n’apparaissent pas dans le journal.

## Problèmes courants et solutions

### Impossible de détecter la version de base

Si l’outil [!DNL CVT] ne parvient pas à trouver la version de base d’Adobe Commerce, vérifiez les conditions suivantes :

**Vérifier :**

- `composer.lock` est manquant.
- La commande `patch-status` s’exécute en dehors de la racine du projet Adobe Commerce (ou `--root` pointe vers le mauvais chemin). `composer.lock` est donc introuvable.
- `composer.lock` existe mais n’est pas un fichier JSON valide ou ne peut pas être lu.
- `composer.lock` ne contient aucun des packages de base reconnus (`magento/product-enterprise-edition`, `magento/product-community-edition`, `magento/magento2-base`).

**Messages d’avertissement :**

Si `composer.lock` existe mais qu’il est illisible, impossible à analyser ou ne contient pas de package de base reconnu, l’outil émet l’une des chaînes suivantes dans le champ de sortie des avertissements :

```shell-session
No recognized Commerce base package found in composer.lock
composer.lock exists but could not be read
composer.lock could not be parsed as JSON
```

>[!NOTE]
>
> Si `composer.lock` est entièrement manquant, l’outil `base_version: "unknown"` signale sans **aucun message d’avertissement**. Vérifiez toujours `base_version` dans la sortie directement. Ne vous fiez pas à la présence d’un avertissement pour résoudre ce problème.

L’une des conditions mentionnées précédemment indique que l’outil ne peut pas détecter la version de base. L’outil se ferme avec le code `1` et aucune détection de correctif n’est effectuée.

**Actions:**

- Exécutez la commande `patch-status` à partir de la racine du projet [!DNL Adobe Commerce] ou transmettez la `--root` appropriée.
- Vérifiez que `composer.lock` est présent, actif et valide dans le fichier JSON.
- Vérifiez que l’installation utilise une édition d’Adobe Commerce prise en charge afin `composer.lock` contienne l’un des packages de base reconnus.

### Aucun correctif ne s’applique à la version installée

Si [!DNL CVT] signale un `base_version` valide, mais que les `applied_patches`, `missing_patches` et `unknown_patches` sont vides, la version installée n’est pas couverte par le registre des correctifs actuel.

**Vérifier :**

- La version [!DNL Adobe Commerce] installée n&#39;est pas représentée dans le fichier de registre des correctifs. Par exemple, une version plus récente que les dernières entrées du registre.

**Messages d’avertissement :**

```shell-session
No patches found in registry for installed component versions (CE=2.4.7-p9)
```

Cet avertissement est différent de l’avertissement « la version de base ne peut pas être détectée ». La `base_version` est correcte, l’outil se ferme `0` et il n’y a rien dans le registre auquel comparer.

**Actions:**

- Confirmez `base_version` dans la sortie est ce que vous attendez.
- Confirmez `registry_source` est `remote` ou un `cache` récent, et non obsolète.
- Contactez l’assistance Adobe Commerce si la version doit déjà être couverte.

### Impossible de récupérer le registre des correctifs

Si l’outil [!DNL CVT] ne parvient pas à récupérer le dernier fichier de registre des correctifs, vérifiez les paramètres réseau et de cache :

**Vérifier :**

- Le réseau n&#39;est pas disponible.
- La requête du point d’entrée de correctif Adobe expire.
- `--no-cache` a été utilisé et le registre distant n&#39;est pas accessible.
- `PATCH_REGISTRY_URL` pointe vers un registre indisponible ou n’est pas une URL HTTPS valide.
- Si l’outil [!DNL CVT] ne parvient pas à récupérer le dernier fichier de registre des correctifs, vérifiez les paramètres réseau et de cache :

>[!NOTE]
>
>Si le fichier de registre est manquant ou a expiré, l&#39;outil télécharge le dernier registre à partir de l&#39;hôte distant.

**Messages d’avertissement :**

L’outil émet les chaînes suivantes dans le champ de sortie des avertissements pour ce scénario :

```shell-session
Remote registry fetch failed (HTTP 403). Check PATCH_REGISTRY_URL (if set) and network connectivity.
Remote registry response was not valid JSON; ignoring.
Could not load remote registry. Using cached registry (3 hours old). CVE coverage may be incomplete.
Patch registry could not be loaded.
Could not fetch remote registry and --no-cache was set; aborting.
```

Le message du cache obsolète inclut l’âge réel en heures, par exemple, `(3 hours old)`.

Les avertissements `patch registry could not be loaded` et `could not fetch remote registry` indiquent que l’outil s’est arrêté sans exécuter la détection de correctif.

**Actions:**

- Exécutez à nouveau la commande `patch-status` lorsque la connectivité réseau est disponible.
- Autorisez l’outil [!DNL CVT] à utiliser le registre mis en cache si un avertissement de cache périmé est acceptable pour l’analyse.
- Supprimez les `--no-cache`, sauf si vous avez besoin de nouvelles récupérations à distance.
- Vérifiez que l’outil [!DNL CVT] peut écrire dans `var/patch_metadata/` si vous souhaitez réutiliser le cache du Registre.

### La comparaison des correctifs ne peut pas être récupérée ni vérifiée.

Si l&#39;outil [!DNL CVT] ne peut pas tester un ou plusieurs correctifs applicables, vérifiez l&#39;accès à patch-diff :

**Vérifier :**

- Une comparaison des correctifs ne peut pas être téléchargée à partir du point d’entrée des correctifs Adobe.
- Les informations d’identification requises pour les téléchargements de correctifs authentifiés sont manquantes ou non valides.
- `PATCH_DIFF_BASE_URL` pointe vers une source patch-diff non disponible ou n’est pas une URL HTTPS valide.
- La comparaison des correctifs mis en cache est manquante ou illisible.
- La vérification SHA-256 échoue pour une comparaison de correctifs téléchargée.
- L’outil [!DNL CVT] ne peut pas écrire sur `var/patch_metadata/.patch_diffs/`.

**Messages d’avertissement :**

L’outil émet les chaînes suivantes dans le champ de sortie des avertissements pour ce scénario :

```shell-session
Patch 247p9-2026-05-001-EE requires authentication. Set credentials via COMPOSER_AUTH or auth.json.
Could not fetch patch 247p9-2026-05-001-EE (HTTP 401). Check credentials (COMPOSER_AUTH / auth.json).
Could not fetch patch 247p9-2026-05-001-EE (HTTP 404).
Could not fetch or verify patch 247p9-2026-05-001-EE. Check network connectivity and credentials (COMPOSER_AUTH / auth.json).
Could not fetch patch file for 247p9-2026-05-001-EE.
SHA-256 verification failed for patch 247p9-2026-05-001-EE; discarding download.
```

L’ID de correctif dans chaque message est l’ID d’entrée de registre réel, par exemple `247p9-2026-05-001-EE`. `SHA-256 verification failed` signifie qu’un fichier correctif récemment téléchargé ne correspond pas à sa somme de contrôle attendue. L’outil le supprime sans mise en cache et classe le correctif `unknown` pour cette exécution. Une entrée de cache *locale* corrompue est détectée et récupérée silencieusement au cours de la même exécution, sans avertissement. Dans les deux cas, aucun nettoyage manuel du cache n’est nécessaire.

**Actions:**

- Confirmez la connectivité réseau et relancez la commande.
- Vérifiez que les informations d’identification requises pour les téléchargements de correctifs authentifiés sont configurées.
- Vérifiez que l’outil [!DNL CVT] peut écrire dans `var/patch_metadata/.patch_diffs/`.
- Conservez les détails d’avertissement et de sortie si le correctif reste classé comme inconnu.

### Des correctifs manquants ou inconnus sont signalés

Si le rapport contient des valeurs `missing_patches` ou `unknown_patches` inattendues, consultez les détails de l’installation et de la sortie :

**Vérifier :**

- Les correctifs mensuels ont été appliqués hors séquence.
- Un correctif spécifique au composant, tel que B2B (Adobe Commerce business-to-business) ou Adobe Commerce Page Builder, est manquant.
- `composer.lock` signale une version de composant installée qui nécessite le correctif.
- Une comparaison des correctifs n’est pas disponible ou le résultat de la détection n’est pas concluant.

**Messages d’avertissement :**

L’outil émet les chaînes suivantes dans le champ de sortie des avertissements pour ce scénario :

```shell-session
No file_name or sha256 for 247p9-2026-05-001-EE
Registry entry '247p9-2026-05-001-EE' requires unknown patch '247p9-2026-04-001-EE'; skipping.
descendant diffs unavailable for 247p9-2026-06-001-EE; dry-run for 247p9-2026-05-001-EE may be inaccurate
Failed to reverse-apply 247p9-2026-06-001-EE when preparing dry-run for 247p9-2026-05-001-EE; result may be inaccurate
Failed to forward-apply prerequisite 247p9-2026-04-001-EE when preparing dry-run for 247p9-2026-05-001-EE; result may be inaccurate
```

Lorsque vous rencontrez des `may be inaccurate` dans un avertissement, la vérification d’essai s’exécute toujours, mais avec un degré de confiance réduit. Le correctif peut toujours être classé en `applied_patches` ou `missing_patches`, mais pas nécessairement `unknown_patches`.

Pour les correctifs inconnus en particulier, `var/log/patch_status.log` enregistre la sortie d’exécution d’essai de correctifs bruts (direct et inverse), qui indique quels fichiers et quels blocs n’ont pas pu correspondre.

Si vous rencontrez un avertissement indiquant qu&#39;aucun correctif n&#39;a été trouvé, reportez-vous à la section [aucun correctif ne s&#39;applique à la version installée](#no-patches-apply-to-the-installed-version) pour obtenir des conseils.

**Actions:**

- Passez en revue les champs `applied_patches`, `missing_patches` et `unknown_patches`.
- Vérifiez si les correctifs manquants s’appliquent à l’édition et aux composants installés.
- Comparez le résultat avec les notes de mise à jour des correctifs de sécurité appropriées.
- Vérifiez que la base de code inspectée correspond à l’environnement déployé sur lequel vous avez l’intention de créer des rapports.
- Contactez l&#39;assistance Adobe Commerce si le statut inconnu bloque la planification de la remédiation.

### La sortie n’est pas générée.

Si l’outil [!DNL CVT] se termine mais que la sortie JSON ou CSV attendue est manquante, vérifiez la syntaxe de la commande et la sortie du terminal :

**Actions:**

- Utilisez la sortie JSON par défaut si la sortie CSV n’est pas requise.
- Utilisez `--format=csv` pour générer une sortie CSV.
- Vérifiez que la sortie de la commande n&#39;est pas redirigée ou ignorée par le shell, le script ou l&#39;analyseur qui exécute l&#39;outil [!DNL CVT].
- Recherchez `stderr` messages d’erreur `patch-status:`.
- Si vous redirigez la sortie vers un fichier, par exemple `patch-status > report.json`, vérifiez que le shell dispose des autorisations d’écriture pour cette destination. L’outil écrit uniquement dans `stdout`.
- Vérifiez que l’outil [!DNL CVT] peut écrire dans `var/log/patch_status.log`.
- Exécutez à nouveau la commande et capturez la sortie du terminal pour le dépannage.

## Obtention d’aide

Lorsque vous contactez l’assistance Adobe Commerce, fournissez uniquement les détails nécessaires pour examiner le problème.

Inclure :

- Version et édition d’Adobe Commerce
- Version de l’outil [!DNL CVT]
- Source du registre à partir de la sortie de l’outil [!DNL CVT]
- Valeurs `applied_patches`, `missing_patches` et `unknown_patches` pertinentes
- Avertissements pertinents
- Message d’erreur ou sortie de commande

N’incluez pas de secrets, d’informations d’identification, de clés privées ou de données client non liées dans les pièces jointes ou les journaux partagés.

## Rubriques connexes

- [Introduction](intro.md)
- [Génération d’un rapport d’état des correctifs](generate-report.md)
- [Notes de mise à jour](release-notes.md)
