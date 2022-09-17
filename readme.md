# Postman 2 Markdown Converter

For that only time you need to convert your Postman documentation in a github´s readme ready format!

## Features & Problems

It saves you a lot of work by searching multilevel json documents and giving them an almost immpecable markdown format.
It still not recognize json codeblocks and might need a bunch og new lines added manually but is still a lot less work for you to export your Postman documentation to Github. I really hope it works for you and if you want you can send a pull request.
At this moment it get to (myJson.item[i].item[j].item[h].request.header[key].value) level down the postman json object so it can do a lot of work for you.

![](/demo/pm2md005.png)

### How to Use

0 - Put your Postman documentation file in the /demo folder (might be postman-collection.json) and rename it to docs.json, (topLeft img)

1 - Start convertidor.html maybe with vscode extension LiveServer. Now your html will show the content of docs.json in plaintext but with markdown format (topRight img)

2 - copy/paste html content inside a readme.md file (bottomLeft img) and upload it to your github project (bottomRight img). wuuuzaaaa!!!

3 - celebrate & buy me a coffe! <https://mpago.la/1fUb8kA>
(if a monetary contribution sounds like too much, consider subcribe to my youtube channel <https://www.youtube.com/OctarineCode>)

## Funciones y Problemas

No hay forma de exportar tu documentacion de Postman a Github directamente (o sea, si, pero no formateada) y de ahi que le dedique el tiempo a esto. Va a muchos niveles dentro del json ahorando mucho trabajo pero aun asi los bloques de codigo le cuesta identificarlos y al resto del texto generado le hace falta meter muchas lineas nuevas a mano, pero de nuevo, ahorra mucho trabajo y espero sus colaboraciones para mejorar el codigo!
Actualmente llega hasta este nivel de profundidad dentro del objeto json de postman (myJson.item[i].item[j].item[h].request.header[key].value), por lo que considero que te ahorrara mucho trabajo.

![](/demo/pm2md005.png)

### Como usar

0 - Pone tu archivo de Postman en la carpeta /demo y renombralo a docs.json (img arribaIzq)

1 - Levanta el archivo convertidor.html usando la extension de vscode LiveServer. Ahora ese html tendra todo el contenido del archivo json pero formateado como markdown. (img arribaDer)

2 - Copia el contenido del html adentro de un archivo nuevo que se llame readme.md (img abajoIzq), subilo al github de tu proyecto (img abajoDer)... y listo!

3 - manda un dinerillo <https://mpago.la/1fUb8kA> Si un aporte monetario parece excesivo, cosidera suscribirte a mi canal de youtube <https://www.youtube.com/OctarineCode>
