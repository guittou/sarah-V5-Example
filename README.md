# sarah-V5-Example
![GitHub Logo](/images/flow.png)

Example d'uttilisation sarah V5

Pour ceux qui ne comprennent pas la nouvelle version c’est en fait assez simple.

La brique SARAH transmet un objet à la brique suivante qui s’appelle « msg » et qui contient les valeurs en  fonction des fichier xml dans le dossier grammar :

objet en sortie de la brique sarah

msg : Object
object
payload: object
  text: "sarah éteins Bureau"
  confidence: 0.8701451
options: object
  plugin: "domticz-http"
  action: "Off"
  command: "switch"
  device: "21"
  type: "light"

La partie « options »  provient des élément indiqués dans les fichiers xml .

L’option :

-	plugin : 

 <tag>out.action.plugin="domticz-http";</tag> 

-	action et command :

<item>éteins<tag>out.action.action="Off";</tag><tag>out.action.command="switch";</tag></item>

-	device et type:

 <item>Bureau <tag>out.action.device="21";</tag><tag>out.action.type="light";</tag></item>

pour récupérer une de ces options dans une fonction ou une autre brique c’est par exemple :

  var action = msg.payload.options.action;
  var command = msg.payload.options.command;
  var device = msg.payload.options.device;
  var type = msg.payload.options.type; 

je ne vais pas tout détailler mais voilà en gros comment ça marche après le code dans les fonctions c’est du js
Editer le code des brique vous devriez réussir à comprendre avec ces explications sommaires.

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

Par contre même si J’arrive bien à récupérer toute les valeurs de domticz via la brique mqtt output, je n’ai pas encore réussi à récupérer l’état d’un device à la demande.

Donc si quelqu’un sait comment faire je suis preneur.

La branche utilisant mqtt n’est pas utilisée il faut  changer la variable dans le fichier domoticz.xml :

  <tag>out.action.plugin="domticz-http";</tag>
  
En
  
  <tag>out.action.plugin="mqtt";</tag>

Pour utiliser le broker mqtt pour piloter domoticz à la place du http.

J’ai donc obtenu avec cette v5 les mêmes fonctions que je réalisais avant avec la v3 et la V4.

Mais je pense que je vais très vite me pencher sur toutes les autres possibilités de cette nouvelle version, Comme la montré Stéphane Bascher avec l’utilisation de l’api google.

Il ne manque plus que la détection du HOTWORD à faire sur linux (snowboy par example https://flows.nodered.org/node/node-red-contrib-snowboy) et on pourra enfin ce passer de windows.


Merci à tous les développeurs des plugins précèdent qui m’ont servi jusqu’à maintenant.
Et bien su merci à Jean-Philippe Encausse et VISEO pour cette nouvelle version.












