# sarah-V5-Example
![GitHub Logo](/images/flow.png)

Example d'uttilisation sarah V5


Vous pouvez récupérer  les 3 fichiers xml (à placer dans le dossier sarah\viseo-bot-project\data\grammar) et le fichier flow-sarah que vous pouvez importer dans l’interface web de node-red :

https://github.com/guittou/sarah-V5-Example

Pour importer le flow copier le contenu du fichier flow-sarah puis coller le dans l’interface (en haut à droite puis import --> clipboard) :

![GitHub Logo](/images/import-flow.png)

Vous obtiendrez comme chez moi une sarah fonctionnelle avec les fonctions heure météo et domoticz

Pour l’heure rien à faire.

Pour la météo rentrer votre clé d’api openweathermap en éditant la brique « meteo » et en modifiant la variable « apikey ».

![GitHub Logo](/images/apikey.png)

Modifier aussi le fichier meteo.xml pour rentrer le parametre de votre ville

	<item>Rennes<tag> out.action.id="2983990"; </tag></item>

Pour Domoticz j’ai essayé en http et ça fonctionne bien.

Modifier les variables ip et port dans la brique « domoticz-http »

![GitHub Logo](/images/domoticz-http.png)

Puis le fichier domticz.xml pour rentrer les détails de vos périphériques

<item>Bureau <tag>out.action.device="21";</tag><tag>out.action.type="light";</tag></item>
<item>Salon <tag>out.action.device="1";</tag><tag>out.action.type="scene";</tag></item>

J’ai aussi essayé en utilisant le broker mqtt  (https://www.domoticz.com/wiki/MQTT).
Ça fonctionne pour réaliser une action sur un device ou une scène (editer la brique domoticz-mqtt-output)

La branche utilisant mqtt n’est pas utilisée il faut  changer la variable dans le fichier domoticz.xml :

  <tag>out.action.plugin="domticz-http";</tag>
  
En
  
  <tag>out.action.plugin="mqtt";</tag>

Pour utiliser le broker mqtt pour piloter domoticz à la place du http.
















