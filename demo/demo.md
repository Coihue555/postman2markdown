# DEMO DOCS

Esta documentación en Github cuenta con una Tabla de Contenidos, la cual se accede haciendo clic en el botón que esta junto al texto readme.md.

![](https://via.placeholder.com/300)

![](https://via.placeholder.com/300)

Mediante la Tabla de Contenidos podrá ir directamente a la sección de su ínterés. Las secciones Configuraciones Previas y Errores tienen aclaraciones importantes para ayudarlo a hacer pruebas en los endpoints de la API, si considera que alguna sección necesita alguna aclaración el repositorio será actualizado.

## Configuraciones Previas

Para comenzar a trabajar con la API de forma cómoda se harán algunas configuraciones en Postman.

![](https://via.placeholder.com/300)

En la sección Environments(1) se agrega un nuevo entorno, en este caso APP(2) y dentro del mismo se crea la variable urlAPP que será la url endpoint3 de la api y la variable token que se creara sola luego de hacer el POST de endpoint1, en la siguiente sección. Estas variables al estar configuradas con el TYPE secret se mostraran como * en las rutas. \[urlAPP\] precede a las rutas: por ejemplo: •••••••/endpoint1/autorizacion \[token\] va en los Headers como valor de APPDesarrollo_token Este campo deberemos incluirlo siempre que el manual muestre:

#### REQUEST HEADERS

![](https://via.placeholder.com/300)

Si hay mas **Request Headers** se colocan debajo de APPDesarrollo_token junto a sus valores.

#### BODY <!-- here was needed a manual newline -->
Campos que van al **BODY** se configuran en la pestaña Body(1), se marca como raw(2) y en formato JSON(3)

![](https://via.placeholder.com/300)



#### REQUEST PARAMS y QUERIES <!-- here was needed a manual newline -->
Valores que se identifiquen como **PARAMS** son valores que son incluidos al final de la ruta URL que llama a la API. al igual que los valores que sean identificados como **QUERIES**

## endpoint1

Con el token que obtengamos aquí se pueden realizar las peticiones a la API.

### POST /endpoint1/autorizacion

> {{urlAPP}}/endpoint1/autorizacion

El campo idApp que se pide en el **BODY** viene en el state al iniciar el proyecto y se usa donde diga {{idApp}}

![](https://via.placeholder.com/300)



#### Respuesta: <!-- here was needed a manual newline -->

```json
{ "token": "eyJhbGciOiJIUzIxzczcxczJ9.eyJpZEFwcENsaWVfsdfsdDkwNzI5OCwiZXh****w*" } 
``` 

Como un extra, el siguiente código en la pestaña Test de Postman recibe el token de la respuesta y lo guarda como variable para ser usada en las demas consultas a la API

```javascript

var json = JSON.parse(responseBody); pm.environment.set("token", json.token); 
```

#### Error:

```json
{ "inStatus": 409, "msg": "Error interno generando llave de acceso " } 
```


#### BODY

```json
{ "idApp": "f21d4175-1cf9-4673-91e6-5c66039100f7" }

```

## endpoint2

Acá recibimos, creamos o editamos los permisos obligatorios u opcionales(endpoint2s) que serán requeridos en la UltraApp.

![](https://via.placeholder.com/300)

Por ejemplo en este caso, varA, varB, var2, varC, varD, varE, etc, ya que estamos tomando datos de un objeto.

### GET Listado endpoint2

> {{urlAPP}}/endpoint2

Con este llamado a la API recibimos la lista completa de permisos requeridos u opcionales(endpoint2s) que tenga la UltraAppe

#### Ej Respuesta:
```json
{ "inStatus": 200, "msgStatus": "ok", "data": [ { "estado": "A", "idendpoint2": "0e07282gttb4e-a702-*44d**3", "tipo": "perfil", "valorInterno": "var2", "descripcion": "var2" }, ] } 
```

#### Request Headers

| campo | valor |
-------|------
| APPDesarrollo_token | {{token}} |

### GET Buscar por Id

> {{urlAPP}}/endpoint2/{{idendpoint2}}

{{idendpoint2}} es un valor que recibimos en **Listado endpoint2**. Al pasarlo al final de la url veremos solo la variable seleccionada

#### Ej Respuesta:
```json
{ "inStatus": 200, "msgStatus": "ok", "data": [ { "estado": "A", "idendpoint2": "we*w**-e486-4b4e-a702-*44d**3", "tipo": "perfil", "valorInterno": "var2", "descripcion": "var2" }, ] } 
```

#### REQUEST PARAMS:
```json
"idendpoint2" valor que val al final de la url, lo podemos obtener del llamado a Listado endpoint2 
```

#### Request Headers

| campo | valor |
-------|------
| APPDesarrollo_token | {{token}} |

### PUT Modificar endpoint2

> {{urlAPP}}/endpoint2/{{idendpoint2}}

Con esta consulta editamos el endpoint2. Por Ej. si cambiamos "descripcion" cambiaremos el texto que se muestra por pantalla

#### Ej Respuesta:

```json
{ "inStatus": 200, "msgStatus": "ok", "data": [ {} ] } 
```

#### Request PARAMS:

```json
{idendpoint2} 
```

#### Request Headers

| campo | valor |
-------|------
| APPDesarrollo_token | {{token}} |

#### BODY

```json
{ "estado": "A", "tipo": "perfil", "valorInterno": "var2", "descripcion": "var22" }

```

### POST Nuevo endpoint2

> {{urlAPP}}/endpoint2

Creamos un nuevo campo requerido por UltraApp

#### Request Headers

| campo | valor |
-------|------
| APPDesarrollo_token | {{token}} |



#### BODY

```json
{ "tipo": "perfil", "valorInterno": "var2", "descripcion": "var2" }

```

## endpoint3

En esta sección veremos los endpoints Obtener Todos, Obtener Uno, Modificar y Crear Nuevo relacionados a endpoint3s, siendo estas las endpoint3s de las distintas Endpointes.

### GET Obtener endpoint3 Todos

> {{urlAPP}}/endpoint3/

Con este llamado a la API obtendremos todas las endpoint3s de las Endpointes,

#### Request Headers

| campo | valor |
-------|------
| APPDesarrollo_token | {{token}} |

### GET Obtener endpoint3

> {{urlAPP}}/endpoint3/{{param1}}/{{param2}}

Con este llamado a la API obtendremos solo la colección de la pasemos su varA{param1} y version{param2}. Ambos valores se pueden obtener previamente desde /endpoint3/Obtener endpoint3 Todos 

Request PARAMS: 
| **campo** | **valor** | 
| --- | --- | 
| param1 | varA de alguna Endpoint | 
| param2 | 1 por defecto |

#### Request Headers

| campo | valor |
-------|------
| APPDesarrollo_token | {{token}} |

### POST Nuevo endpoint3

> {{urlAPP}}/endpoint3/

Con este llamado a la API crearemos la endpoint3 para una colección nueva, 

**"param1"**: "", //varA de la colección 
**"data"**: "", //todos los campos que será necesario pasar dentro del campo data de cada elemento individual de esta particular colección 
**"param2"**: 1, //por el momento va 1 por defecto 
**"dataKey"**: "", // 
**"dataIndice"**: "" // 
**"dataRequerid"**: "", //dentro de data, los campos que son obligatorios 
**"dataAuto"**: "" //Algunas Endpointes tendrán campos autogenerados, estos campos deben ser declarados en dataRequerid **"estadoInicial"**: "A", //Activo es A, Pendiente es W 
**"requiereValidacion"**: "N" //N para no, S para si 
**"referencia"**:"", // 
**"idReferencia"**:"" //

#### Request Headers

| campo | valor |
-------|------
| APPDesarrollo_token | {{token}} |



#### BODY

```json
{ "param1":"", "param2":"", "dataKey":"", "dataIndices":"", "data":"", "dataRequerid":"", "dataAuto":"", "estadoInicial":"", "requiereValidacion":"", "referencia":"", "idReferencia":"" }

```

### PUT Modificar endpoint3

> {{urlAPP}}/endpoint3/{{param1}}/{{param2}}

Con este llamado podemos modificar la endpoint3 de alguna colección que hayamos creado previamente.

#### Request Headers

| campo | valor |
-------|------
| APPDesarrollo_token | {{token}} |



#### BODY

```json
{ "dataKey":"", "dataIndices":"", "data":"", "dataRequerid":"", "dataAuto":"", "estadoInicial":"", "requiereValidacion":"", "referencia":"", "idReferencia":"" }

```

## endpoint4

En esta sección se agrupan los endpoints relacionados a los endpoint4es. Estos pueden ser del tipo: A - algo autogenerado, C - Consulta SQL, E - Expresión regular (formato de varE, formato de fecha, etc)

### GET Obtener endpoint4 Todos

> {{urlAPP}}/endpoint4/

Con este llamado a la API obtendremos todos los endpoint4es disponibles. 
**"param1"**: "UltraAppe", //el varA de la colección a la que pertenece el campo param3 sobre el cual se aplicará el tipo 
**"param3"**: "param1", //campo de data de param1 
**"tipoendpoint4"**: "C", //A(autogenerado), C(Consulta SQL), E(Expresión regular) 
**"endpoint4"**:"" //el algo aplicado

#### Ej Respuesta:

```json
{ "inStatus": 200, "msgStatus": "ok", "data": [ { "param1": "UltraAppe", "param3": "param1", "tipoendpoint4": "C", "endpoint4": "select top(1) param1 from tabla where param1 = '#param1' and estado = 'A'" }, { "param1": "UltraAppe", "param3": "secret", "tipoendpoint4": "A", "endpoint4": "#generaSecret" }, { "param1": "objeto", "param3": "varE", "tipoendpoint4": "E", "endpoint4": "(([^<>()[\\]\\\\.,;:\\s@\\\"]+(\\.[^<>()[\\]\\\\.,;:\\s@\\\"]+)*)|(\\\".+\\\"))@((\\[[0-9]{1,3}\\.[0-9]{1,3}\\.[0-9]{1,3}\\.[0-9]{1,3}\\])|(([a-zA-Z\\-0-9]+\\.)+[a-zA-Z]{2,}))$" }, ] } 
```

#### Request Headers

| campo | valor |
-------|------
| APPDesarrollo_token | {{token}} |

### GET Obtener endpoint4

> {{urlAPP}}/endpoint4/{{param1}}/{{param3}}

Con este llamado a la API obtendremos un algo en particular.

#### Request PARAMS: 
Estos parámetros pueden ser obtenidos previamente con /endpoint4/Obtener endpoint4 Todos y van al final de la url 
| **campo** | **valor** | 
| --- | --- | 
| param1 | varA de la colección | 
| param3 | campo dentro de data de la colección en la cual se aplica el algo |

#### Request Headers

| campo | valor |
-------|------
| APPDesarrollo_token | {{token}} |

### POST Nuevo endpoint4

> {{urlAPP}}/endpoint4/

Con este llamado a la API crearemos un nuevo algo 
**BODY** 
| **campo** | **valor** | 
| --- | --- | 
| param1 | donde a la que pertenecerá | 
| param3 | campo dentro de data sobre la cual se aplicará el algo | 
| tipoendpoint4 | A(algo autogenerado), C(Consulta SQL), E(expresion regular RegEx) | 
| endpoint4 | cadena con el algo a aplicar | 

Ejemplos de algo: 
**Autogenerado**: #valor?N (aplica un valor y si no existe deja N) 
**Consulta SQL**: "select top(1) param1 from algo where param1 = '#param1' and estado = 'A'" 
**Expresión Regular**: '^\[0-9\]+$' //para verificar que sean solo números

#### Request Headers

| campo | valor |
-------|------
| APPDesarrollo_token | {{token}} |



#### BODY

```json
{ "param1":"", "param3":"", "tipoendpoint4":"", "endpoint4":"" }

```

### PUT Modificar endpoint4

> {{urlAPP}}/endpoint4/{{param1}}/{{param3}}



#### Request PARAMS: 
Estos parámetros pueden ser obtenidos previamente con /endpoint4/Obtener endpoint4 Todos y van al final de la url 
| **campo** | **valor** | 
| --- | --- | 
| param1 | varA de la colección | 
| param3 | campo dentro de data de la colección en la cual se aplica el algo |

#### Request Headers

| campo | valor |
-------|------
| APPDesarrollo_token | {{token}} |



#### BODY

```json
{ "tipoendpoint4":"", "endpoint4":"" }

```

## Endpoint

Si bien estas consultas son comunes a todas las Endpointes (EndpointAA, EndpointBB, EndpointCC, EndpointDD, UltraAppe), se genera una carpeta para cada colección para una implementación mas rápida de Obtener Todos, Obtener Uno, Modificar, Crear. Cada nueva colección cambiara el valor del Header \[Endpoint\]. La estructura del body request o el body response cambiara solo dentro del campo data, ya que la estructura de datos de cada colección es distinta.

### EndpointAA

Esta colección de sdfsdf por el momento solo se usa para el menú desplegable del formulario de Crear Cuenta en APP. Facilita mostrar luego solamente las sdfsdfs del sdfsdf seleccionado.

#### GET Todos los EndpointAA

> {{urlAPP}}/Endpoint/getKey

El campo param1 luego lo usaremos en \[EndpointAA por Id\].

#### Ej Respuesta:

```json
{} 
```

#### Request Headers

| campo | valor |
-------|------
| Endpoint | EndpointAA |
| valorkey | descripcion |
| valor | % |
| operador | like |
| APPDesarrollo_token | {{token}} |

#### GET EndpointAA Concatenado

> {{urlAPP}}/Endpoint/getKey

El campo param1 luego lo usaremos en \[EndpointAA por Id\]. Este llamado a la API es igual a Todos los algo solo que en los headers jugamos con la consulta que realizamos. En este ejemplo traemos todos los algo cuyo campo \[descripcion\] termine en "ddddd" y \[codigovarD\] termine en l

#### Ej Respuesta:
```json
{ "inStatus": 200, "msgStatus": "ok", "data": [ { "param1": "72e52d74-3d50-4e3a-a331-f5a38382176b", "data": "{\"creadoEl\":\"20220718155719849\",\"descripcion\":\"algo\",\"codigovarD\":\"asasas\"}, ] } 
```


#### Request Headers
| campo | valor |
-------|------
| Endpoint | EndpointAA |
| valorkey | descripcion,codigovarD |
| valor | d |
| operador | like,like |
| APPDesarrollo_token | {{token}} |


#### GET EndpointAA por id

> {{urlAPP}}/Endpoint/{{param1}}

Obtenemos solo el vvvv del cual pasemos el valor de param1 obtenido en la lista anterior \[Todos los algo\]

#### Requested PARAMS
```json
param1 
```


#### Request Headers
| campo | valor |
-------|------
| APPDesarrollo_token | {{token}} |
| Endpoint | EndpointAA |


### EndpointBB

Esta colección de cosas por el momento solo se usa para el menú desplegable del formulario de Crear Cuenta en APP. Facilita mostrar luego solamentesd la EndpointBB seleccionada.

#### GET Obtener EndpointBB por EndpointAA

> {{urlAPP}}/Endpoint/getKey

El Header \[valor\] se reemplaza por el param1 del EndpointAA del cual deseamos traer las cosas

#### Ej Respuesta:
```json
{ "inStatus": 200, "msgStatus": "ok", "motracosa": "ok", } 
```


#### Request Headers
| campo | valor |
-------|------
| Endpoint | EndpointBB |
| valorkey | idUno |
| valor | {{param1}} |
| operador | = |
| APPDesarrollo_token | {{token}} |


### EndpointCC

Esta colección de EndpointCC por el momento solo se usa para el menú desplegable del formulario de Crear Cuenta en APP.

#### GET Obtener EndpointCC por EndpointBB

> {{urlAPP}}/Endpoint/getKey

El Header \[valor\] se reemplaza por el param1 de la EndpointBB de la cual deseamos traer las EndpointCC

#### Ej Respuesta:
```json
{ "inStatus": 200, "msgStatus": "ok", "data": [ { "param1": "004843c7-0353-47e0-818a-2cfd8689ba71", "estado": "A", "creadoEl": "20220718164327268" }, ] } 
```


#### Request Headers
| campo | valor |
-------|------
| Endpoint | valor1 |
| valorkey | idEndpointBB |
| valor | {{param1}} |
| operador | = |
| APPDesarrollo_token | {{token}} |


### EndpointDD

Un EndpointDD es una fsdfsd registrada en el portal APP.

#### POST Crear EndpointDD

> {{urlAPP}}/Endpoint/

Creamos un nuevo EndpointDD con todos los campos solicitados en **BODY**.

#### Ej Respuesta:
```json
{ "inStatus": 200, "msgStatus": "ok", } 
```


#### Request Headers
| campo | valor |
-------|------
| APPDesarrollo_token | {{token}} |


#### BODY

```json

{ "Endpoint":"EndpointDD", "param2":"1", "data":{ "varA":"ddddddd", "varB":"ddddddddd", "dddddddddd":"ddddddd", "ddddddddd":"90666000", "varE":"nuevdsdsdsds", "varD":"dssfsdfsdfsd", "ddddd":"dss", "var2":"dsfsfdsf", "ddddddd":"cfc3643d-b5dd26cb", "sssssss":"", "ssssss":"", "varDOtro":"", "sfsfdsdf":["ffeefcbd-447d-408a-81be-806126fd147f","b0ece4f0-2459-s-ddd-005d712251aa","Kd","ddfdd","170","","","ddddd",""], "imagenEndpoint":"", "dfdsfsdfs":"", "fdsfsdfsdf":"" } }

```

#### GET Obtener EndpointDDs Todos

> {{urlAPP}}/Endpoint/getKey

Con este llamado traemos todos los sfd registrados en APP La consulta seria: Traer de \[Endpoint\](en este caso EndpointDD) todas las filas con \[valorKey\](en este caso varA) \[operador\](like significa 'que sean como') \[valor\](% es un comodín que trae todos)


#### Request Headers
| campo | valor |
-------|------
| APPDesarrollo_token | {{token}} |
| Endpoint | EndpointDD |
| valor | % |
| valorKey | varA |
| operador | like |


#### GET Obtener EndpointDDs Todos Concatenado

> {{urlAPP}}/Endpoint/getKey

Con este llamado traemos todos los dstrados en APP cuyo varB sea ddd La consulta seria: Traer de \[Endpoint\](en este caso EndpointDD) todas las filas con \[valorKey\](en este caso varA y varB, separado por coma pero no por espacio) \[operador\](like significa 'que sean como', uno para cada campo, separado por coma pero no por espacio) \[valor\](% es un comodín que trae cualquier caracter o caracteres, uno para cada campo, separado por coma pero no por espacio, pero en el caso de varB debe continuar con ddd, o terminar con ddddd)


#### Request Headers
| campo | valor |
-------|------
| APPDesarrollo_token | {{token}} |
| Endpoint | EndpointDD |
| valor | %,% |
| valorKey | varA,varB |
| operador | like,like |


#### GET Obtener EndpointDD

> {{urlAPP}}/Endpoint/{{param1}}

En este caso {param1} pertenece a algún EndpointDD de los que hayamos obtenido medianted


#### Request Headers
| campo | valor |
-------|------
| Endpoint | EndpointDD |
| APPDesarrollo_token | {{token}} |


#### PUT Modificar EndpointDD

> {{urlAPP}}/Endpoint/{{param1}}

El parámetro {{param1}} pertenece a alguno de los EndpointDDs que obtuvimos de \[Obtener EndpointDDs Todos\]. En el **BODY** dentro de \[data\] podemos enviar 1 o varios campos pertenecientes a la colección junto a los valores que queremos modificar. Nótese que agregar \[dat


#### Request Headers
| campo | valor |
-------|------
| APPDesarrollo_token | {{token}} |


#### BODY

```json

{ "}" }

```

### UltraAppe

Una UltraAppe sdfsdgsdfghdsf sdfsd fsdfsdfsdfsdsd sdfsdfsdfsdfsdfsfsdfP.

#### GET Obtener UltraAppe Todas

> {{urlAPP}}/Endpoint/getKey

Con este llamado traemos todos las UltraAppes registradas en APP. La consulta seria: Traer de \[Endpoint\](en este caso UltraAppe) todas las filas con \[valorKey\](en este caso varA) \[operador\](like significa 'que sean como') \[valor\](% es un comodín que significa todos)


#### Request Headers
| campo | valor |
-------|------
| APPDesarrollo_token | {{token}} |
| Endpoint | UltraAppe |
| valor | % |
| valorKey | varA |
| operador | like |


#### GET Obtener UltraAppe

> {{urlAPP}}/Endpoint/{{idAppe}}

En este caso {param1} pertenece a alguna UltraAppe de las que hayamos obtenido mediante \[Obtener UltraAppe Todos\]. Al hacer pruebas en Postman nótese que adentro de \[data\] viene otro campo \[data\], el cual trae un string con toda la información de la UltraA


#### Request Headers
| campo | valor |
-------|------
| Endpoint | UltraAppe |
| APPDesarrollo_token | {{token}} |


#### POST Crear UltraAppe

> {{urlAPP}}/Endpoint/

Con este llamado a la API creamos una nueva UltraAppe. {Endpoint}: en este caso es UltraAppe {param2}:siempre es 1 {data}:en este caso notaremos que los datos son distintos a EndpointDD. Aqui los campos son { "creadoEl": "20220727184216989", //autogenerado "varA": "Super App!", //el varA de la app a crear "logo": "url_de_la_imagen.png", "redirectUrl": "", //ruta de redireccionamiento de la app "endpoint2Requeridos": \["idendpoint21", "idendpoint22", "idendpoint23", "idendpoint24"\], //campos requeridos por la app "endpoint2Opcionales": \[ "idendpoint2A", "idendpoint2B", "idendpoint2C"\], //campos opcionales de la app "origen": \["url_de_la_app"[\]](http://localhost:8095/), //url de origen "param1": "**",** //id del algo "secret": "$2a$10$htFjv2.3*******" }


#### Request Headers
| campo | valor |
-------|------
| APPDesarrollo_token | {{token}} |


#### BODY

```json

{ "Endpoint": "UltraAppe", "param2": "1", "data": { "Endpoint": "UltraAppe", "Endpoint": "UltraAppe", } }

```

#### PUT Modificar UltraAppe

> {{urlAPP}}/Endpoint/{{param1}}

Con este llamado a la API podremos editar la información de UltraAppe. {{param1}} lo obtenemos de Obtener UltraAppe Todas. Dentro


#### Request Headers
| campo | valor |
-------|------
| APPDesarrollo_token | {{token}} |


#### BODY

```json

{ "Endpoint": "UltraAppe", "param2": "1", "data": { "Endpoint": "UltraAppe", "param2": "1", }" }

```

#### GET Obtener Valida-Data Todos

> {{urlAPP}}/Endpoint/getValidaDataAll/{{param1}}

Este llamado a la API nos trae todas las solicitudes de permisos que ha hecho la UltraAppe. Los estados pueden ser W(pendiente), o A(aprobado)

#### Request PARAMS: {{param1}} pertenece a alguna UltraAppe obtenida mediante Obtener UltraAppe Todas

#### Ej Respuesta:
```json
{ "inStatus": 200, "msgStatus": "ok", "data": [ { "param1": "1fe2acfc-dgggg862-4*", "data": "{\"origen\":[\"http://localhost:8090/\"],\"creadoEl\":\"20220819161352821\"}", "estado": "W", "creadoEl": "20220819161352821", "idValidacion": "8b1445gggggda215074a" } ] } 
```

#### Request Headers
| campo | valor |
-------|------
| APPDesarrollo_token | {{token}} |
| Endpoint | UltraAppe |

#### GET Obtener Valida-Data por Id

> {{urlAPP}}/Endpoint/getcxzc/{{idzxcon}}

Con este llamado a lcxzczxczxczx

#### Request Headers

| campo | valor |
-------|------
| APPDesarrollo_token | {{token}} |
| Endpoint | UltraAppe |
| param1 | {{param1}} |

#### GET Obtiene Valida-Data Pendientes

> {{urlAPP}}/Endpoint/getValidaDataPendientes

Con este llamado a la API obtendremos todas las UltraAppes que tengan solicitudes de permisos pendientes.

#### Ej Respuesta: 
sdfsfdsdfsdfsdfsdfsd sfsdfsfdsdfsdfsdfsdfdsf


#### Request Headers
| campo | valor |
-------|------
| APPDesarrollo_token | {{token}} |
| Endpoint | UltraAppe |


#### PUT Modificar Estado

> {{urlAPP}}/Endpoint/estado

Con este llamado a la API podemos modificar el estado de una UltraAppe. Por ejemplo: de W(pendiente) a A(aprobado).

#### Ej Respuesta: 
dgsdffffffffffffffffffffffffffff sdffsdfsdfsfsf


#### Request Headers
| campo | valor |
-------|------
| APPDesarrollo_token | {{token}} |


#### BODY

```json

{ "Endpoint": "UltraAppe", "param1":"1fe2acsdfcd9d", "estado":"A" }

```

#### PUT Valida Data Id

> {{urlAPP}}/Endpoint/ValidaDataId/{ idValidacion }

Con este llamado a la API modificamos el estado de un permiso solicitado. En el BODY \[resultado\] va alguna observación sobre la decisión de aprobar o denegar el permiso solicitado.

#### Request PARAMS: 
{ idValidacion } lo podemos obtener de \[Obtener Valida-Data Todos\]
```json
{ idValidacion } 
```

#### Ej Respuesta:
```json
{ "inStatus": 200, "msgStatus": "data validada actualizada", "data": [ {} ] } 
```


#### Request Headers
| campo | valor |
-------|------
| APPDesarrollo_token | {{token}} |


#### BODY

```json

{ "Endpoint":"UltraAppe", "param1":"{{param1}}", "estado":"A", "resultado":"Razon por la que se aprueba o niega el permiso" }

```

## Endpoint Login

### PUT Modificar Login

> {{urlAPP}}/EndpointLogin/

Con este llamado a la API se realiza el Login. {Endpoint}: por ej: EndpointDD, asdsadad, etc {valorId}: idEndpointDD, param1, etc {password}: el password registrado perteneciente a {valorId}

#### Request Headers

| campo | valor |
-------|------
| APPDesarrollo_token | {{token}} |



#### BODY

```json
{ "Endpoint":"", "valorId":"", "password":"" }

```

## Correo

### POST Crear Correo

> {{urlAPP}}/correo/

Con este llamado a la API se pueden enviar correos electrónicos. {para}: varE del destinatario {asunto}: resumen del contenido que muestra el mail en la bandeja de recibidos. {cuerpo}: Cuerpo del mensaje en texto plano {cuerpohtml}: Cuerpo del mensaje con html y css embebido. Cada estilo debe ser aplicado en cada etiqueta html, ya que se comienza dentro de una etiqueta DIV en lugar de una etiqueta BODY dentro de una etiqueta HTML Por ej: button style="font: inherit; background-color: #359ff4; border: none; padding: 20px; margin-top: 40px; letter-spacing: 2px; font-weight: 600; color: white; font-size: 20px; border-radius: 5px; box-shadow: 3px 3px #266da7;"

#### Request Headers

| campo | valor |
-------|------
| APPDesarrollo_token | {{token}} |


#### BODY

```json
{ "para":"correo@gmail.com", "asunto":"prueba pm", "cuerpo":"", "cuerpohtml":"div
parrafo


ver" }

```

## Errores


#### 01 - Barras Invertidas en las cadenas de texto 
En ocasiones las respuestas son formateadas por Postman para escapar algunos caracteres especiales. Como vimos en