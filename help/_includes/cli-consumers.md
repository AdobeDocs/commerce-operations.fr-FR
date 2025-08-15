---
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---
# Options de l’interface de ligne de commande pour les consommateurs de file d’attente de messages

| Nom | Description | Valeur | Obligatoire |
|------|-------------|-------|----------|
| `--consumers-wait-for-messages` | Détermine si les consommateurs attendront un message de la file d’attente. | 1 - Oui, 0 - Non | Non |

* `0` : les consommateurs et consommatrices traitent les messages disponibles dans la file d’attente, ferment la connexion TCP et s’arrêtent. Les consommateurs et consommatrices n’attendent pas que des messages supplémentaires entrent dans la file d’attente, même si le nombre de messages traités est inférieur à la valeur de `--max_messages` spécifiée lors du démarrage des consommateurs et consommatrices.

* `1` : les clients continuent à traiter les messages de la file d&#39;attente des messages jusqu&#39;à ce qu&#39;ils atteignent le nombre maximal de messages (la valeur spécifiée pour `--max_messages` sur la commande `queue:consumers:start`) avant de fermer la connexion TCP et d&#39;arrêter le traitement des clients. Si la file d’attente se vide avant d’atteindre `--max_messages`, le client attend l’arrivée d’autres messages. Si vous utilisez des programmes de travail pour exécuter des consommateurs au lieu d’utiliser une tâche cron, définissez cette variable sur `1`.

>[!WARNING]
>
>L’option `--consumers-wait-for-messages` est une option globale et ne peut pas être configurée séparément pour chaque client.
