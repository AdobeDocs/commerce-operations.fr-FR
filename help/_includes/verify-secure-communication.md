---
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 1%

---
# Vérifier que la communication est sécurisée

Cette section décrit deux manières de vérifier que l’authentification HTTP de base fonctionne :

* Utilisation d’une commande `curl` pour vérifier que vous devez saisir un nom d’utilisateur et un mot de passe pour obtenir l’état du cluster
* Configuration de l’authentification HTTP de base dans Admin

## Utilisation d’une commande `curl` pour vérifier l’état de la grappe

Saisissez la commande suivante :

```bash
curl -i http://<hostname, ip, or localhost>:<proxy port>/_cluster/health
```

Par exemple, si vous saisissez la commande sur le serveur du moteur de recherche et que votre proxy utilise le port 8080 :

```bash
curl -i http://localhost:8080/_cluster/health
```

Le message suivant s’affiche pour indiquer que l’authentification a échoué :

```
HTTP/1.1 401 Unauthorized
Date: Tue, 23 Feb 2016 20:35:29 GMT
Content-Type: text/html
Content-Length: 194
Connection: keep-alive
WWW-Authenticate: Basic realm="Restricted"
<html>
<head><title>401 Authorization Required</title></head>
<body bgcolor="white">
  <center><h1>401 Authorization Required</h1></center>
</body>
</html>
```

Essayez maintenant la commande suivante :

```bash
curl -i -u <username>:<password> http://<hostname, ip, or localhost>:<proxy port>/_cluster/health
```

Par exemple :

```bash
curl -i -u magento_elasticsearch:mypassword http://localhost:8080/_cluster/health
```

Cette fois, la commande réussit avec un message similaire à ce qui suit :

```
HTTP/1.1 200 OK
Date: Tue, 23 Feb 2016 20:38:03 GMT
Content-Type: application/json; charset=UTF-8
Content-Length: 389
Connection: keep-alive
{"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
```

## Configuration de l’authentification HTTP de base dans Admin

Effectuez les mêmes tâches que celles décrites dans la [Configuration du moteur de recherche](../configuration/search/configure-search-engine.md) *sauf* cliquez sur **[!UICONTROL Yes]** dans la liste **[!UICONTROL Enable HTTP Auth]** et saisissez votre nom d’utilisateur et votre mot de passe dans les champs fournis.

Cliquez sur **[!UICONTROL Test Connection]** pour vous assurer qu&#39;il fonctionne, puis sur **[!UICONTROL Save Config]**.

Vous devez vider le cache et réindexer avant de continuer.
