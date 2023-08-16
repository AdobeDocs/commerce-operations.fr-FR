---
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---
# Options d’interface de ligne de commande pour les consommateurs de la file d’attente de messages

| Nom | Description | Valeur | Obligatoire |
|------|-------------|-------|----------|
| `--consumers-wait-for-messages` | Détermine si les consommateurs attendront un message de la file d’attente. | 1 - Oui, 0 - Non | Non |

* `0`: les consommateurs traitent les messages disponibles dans la file d’attente, ferment la connexion TCP et s’arrêtent. Les consommateurs n’attendent pas que des messages supplémentaires entrent dans la file d’attente, même si le nombre de messages traités est inférieur à la valeur `--max_messages` valeur spécifiée lors du démarrage des consommateurs.

* `1`: les consommateurs continuent à traiter les messages de la file d’attente des messages jusqu’à atteindre le nombre maximum de messages (valeur spécifiée pour `--max_messages` sur le `queue:consumers:start` ) avant de fermer la connexion TCP et d’arrêter le processus client. Si la file d’attente se vide avant d’atteindre `--max_messages` le consommateur attend que d’autres messages arrivent. Si vous utilisez des objets Worker pour exécuter des consommateurs au lieu d’utiliser une tâche cron, définissez cette variable sur `1`.

>[!WARNING]
>
>La variable `--consumers-wait-for-messages` est une option globale qui ne peut pas être configurée séparément pour chaque consommateur.
