Para la realización de esta práctica lo primero que hecho ha sido completar las dos actividades de la asignatura m1 y m2, las cuales han sido de una manera u otra, parte de la PEC. A continuación muestro lo aprendido en las actividades y cómo las he aplicado a la PEC.

En la actividad m1 he aprendido diversas herramientas que utilizaré durante la realización de la práctica y que me ayudarán con el correcto cumplimiento de los objetivos de la PEC.
De las herramientas que más me han llamado la atención o que desconocía hasta el momento y que usaré durante la PEC son:

En el caso del inspector del navegador: la funcionalidad de la compatibilidad con los distintos navegadores (compatibility), la edición del código CSS o HTML en vivo para ver los cambios en el momento, el histórico de cambios (changes), las fuentes aplicadas (fonts) y la sección de CSS computed para entender qué estilo se está aplicando a un determinado element (computed). Por otro lado, la herramienta responsive para poder observar la web en distintos dispositivos y ver que el diseño de la web es responsive. 

En la actividad m2 he creado el boilerplate que me servirá como estructura base del proyecto. En primer lugar, he elegido Visual Studio Code para el desarollo de la web. Visual Studio incluye la terminal, que será la que usaré para la ejecución de comandos durante la PEC.

GESTOR DE PAQUETES
Como gestor de paquetes, he elegido npm, tal y como recomienda la asignatura. En mi caso, ya tenía instalado npm, concretamente, la versión 8.1.3. He ejecutado el comando "npm update -global npm" para actualizar npm y ahora tengo la versión 8.6.0. A continuación, he ejecutado los siguientes comandos para insertar mi nombre como autora y mi correo electrónico:

npm set init.author.name "Ana Sancho Callealta"
npm set init.email "asanchoca@uoc.edu"

Después, he creado el archivo package.json mediante el comando "npm init":

{
  "name": "pec1",
  "version": "1.0.0",
  "description": "Biografía de los Red Hot Chili Peppers",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "Ana Sancho Callealta",
  "license": "ISC"
}

MODULE BUNDLERS
Como module bundler, utilizaré Parcel por su simplicidad en la configuración. La primera acción que he realizado ha sido eliminar el campo "main" del package.json para que no entre en conflicto con Parcel. Luego, he ejectuado el comando "npm install --save-dev parcel" para su instalación en la carpeta del proyecto y he creado la carpeta "src" con el archivo "index.html", el cual será el entry point de la aplicación.

La funcionalidad principal de Parcel que me ayudará en todo el proyecto será el "server build in", gracias al cual la aplicación hace el build automáticamente cuando encuentra modificaciones en el proyecto y de esta manera se pueden observar los nuevos cambios aplicados al momento. Para ello, uso el comando "npx parcel src/index.html":

anasancho@MacBook-Pro PEC1 % npx parcel src/index.html
Server running at http://localhost:1234
✨ Built in 1.24s

A continuación he creado la carpeta "styles" y dentro de ella, el archivo styles.css donde irá el código CSS para el estilo de la web. También he modificado el archivo package.json para no tener que indicar cada vez el index.html en el comando:

{
  "name": "pec1",
  "source": "src/index.html",
  "version": "1.0.0",
  "description": "Biografía de los Red Hot Chili Peppers",
  "scripts": {
    "start": "parcel"
  },
  "author": "Ana Sancho Callealta",
  "license": "ISC",
  "devDependencies": {
    "parcel": "^2.4.1"
  }
}

He añadido la ruta del index con "source" y el script "start": "parcel". A partir de ahora, puedo lanzar la aplicación con el comando "npx parcel".

Uno de los problemas que encontré fue en la ejecución del comando "npm run build":
npm ERR! Missing script: "build"
Había olvidado incluir en el package.json el script "build": "parcel build". Añadiéndolo, solucioné el problema.

BROWSERLIST
Browserslist puede ser configurado a nivel del package.json o mediante el archivo .browserslist. Yo he decidido añadir la configuración al package.json, puesto que me resulta más claro tener la información ahí y al ser una única línea, no aumenta demasiado el tamaño del .json. He realizado un estudio sobre los navegadores que podrán soportar mi web. Mi objetivo principal con este estudio, es que la web llegue a un porcentaje de usuarios aproximado del 90-95%. Para la realización de este estudio, me he servido del comando "npx autoprefixer --info", el cual proporciona información sobre los navegadores soportados y el porcentaje de público objetivo. Todas las queries realizadas en browserslist, al estar separadas por una coma ',' corresponden a la operación OR.

//Últimas dos versiones de todos los navegadores del mercado.
"browserslist": "last 2 versions"
These browsers account for 77.92% of all users globally

//Navegadores con un uso global mayor al 1% (según estadísticas) / Últimas dos versiones de todos los navegadores del mercado / Navegadores que tengan soporte oficial o que hayan sido actualizados en los últimos 2 años
"browserslist": "> 1%, last 2 versions, not dead"
These browsers account for 85.4% of all users globally

//Navegadores con un uso global mayor al 0.5% (según estadísticas) / Últimas dos versiones de todos los navegadores del mercado / Navegadores que tengan soporte oficial o que hayan sido actualizados en los últimos 2 años
"browserslist": "> 0.5%, last 2 versions, not dead"
These browsers account for 88.79% of all users globally

//Navegadores con un uso global mayor al 0.2% (según estadísticas) + Últimas dos versiones de todos los navegadores del mercado + Navegadores que tengan soporte oficial o que hayan sido actualizados en los últimos 2 años
"browserslist": "> 0.2%, last 2 versions, not dead"
These browsers account for 90.79% of all users globally

//Navegadores con un uso global mayor al 0.2% (según estadísticas) + Últimas dos versiones de todos los navegadores del mercado + Versiones de navegadores lanzadas en los últimos 2 años + Navegadores que tengan soporte oficial o que hayan sido actualizados en los últimos 2 años.
//Últimas dos versiones de todos los navegadores del mercado
"browserslist": "> 0.2%, last 2 versions, last 2 years, not dead"
These browsers account for 92.85% of all users globally

Con esta query "> 0.2%, last 2 versions, last 2 years, not dead" he conseguido alcanzar un 92.85% de usuarios, soportando navegadores con uso mayor del 0.2%, que sean las dos últimas versiones del mercado, que las versiones hayan sido lanzadas en los dos últimos años o que sean navegadores con soporte oficial o actualizados en los últimos 2 años. He decidido no centrarme en X navegadores en concreto para dar más cobertura al máximo número de usuarios posibles, ya que los parámetros que utilizado en la query hacen referencia a todos los navegadores existentes en el mercado.

Para la realización de este estudio, he consultado las siguientes urls:
https://github.com/browserslist/browserslist#query-composition
https://browserslist.dev/


DEPENDENCIAS
A continuación he instalado rimraf y npm-run-all mediante el comando "npm install --save-dev rimraf npm-run-all". Rimraf corresponde con el comando UNIX "rm -rf" y lo utilizaré en esta PEC para limpiar la caché de parcel (.parcel-cache) y el contenido antiguo de la carpeta dist, para que no crezca infinitamente cada vez que se hace un build. Npm-run-all sirve para poder ejecutar múltiples scripts de npm en paralelo. Gracias a esta dependencia, he podido añadir el clean en los scripts de "start" y "build". Por tanto, ahora el package.json queda tal que así:

{
  "name": "pec1",
  "source": "src/index.html",
  "browserslist": "> 0.2%, last 2 versions, last 2 years, not dead",
  "version": "1.0.0",
  "description": "Biografía de los Red Hot Chili Peppers",
  "scripts": {
    "start": "npm-run-all clean parcel:dev",
    "build": "npm-run-all clean parcel:build",
    "parcel:dev": "parcel",
    "parcel:build": "parcel build",
    "clean": "rimraf dist .parcel-cache"
  },
  "author": "Ana Sancho Callealta",
  "license": "ISC",
  "devDependencies": {
    "npm-run-all": "^4.1.5",
    "parcel": "^2.4.1",
    "rimraf": "^3.0.2"
  }
}

PREPROCESADORES DE CÓDIGO
Los navegadores únicamente entienden HTML, CSS y JS, por tanto, si utilizamos otros lenguajes, como por ejemplo TypeScript (para JS) o Saas (para CSS), tenemos que usar una herramienta que "traduzca" estos lenguajes para que sean comprensibles para el navegador. En el caso de esta PEC, usaré Babel y PostCSS, los cuales ya vienen instalados con Parcel y son los recomendados por la asignatura. Al realizar las actividades del módulo m2 de la asignatura, podemos observar cómo se han añadido las dependencias de Autoprefixer y postCSS.

//package.json
"devDependencies": {
    "autoprefixer": "^10.4.4",
    "npm-run-all": "^4.1.5",
    "parcel": "^2.4.1",
    "postcss": "^8.4.12",
    "rimraf": "^3.0.2",
    "tailwindcss": "^3.0.23"
}

Además, he añadido el plugin Tailwindcss, mediante la creación del archivo ".postcssrc" y la inclusión del plugin en dicho archivo. Tailwindcss permite escanear archivos HTML y componentes JS y crea el código CSS mediante la lectura de clases en el código.

//.postcssrc
{
  "plugins": {
    "tailwindcss": true
  }
}

GIT
En la configuración de GIT, encontré un problema de permisos al intentar hacer push del código. Mi cuenta github no está configurada con SSH, si no con HTTPS, y por error, había configurado el origin remoto con la URL SSH. Cambié el origin a la URL HTTPS, GIT me pidió las credenciales de mi cuenta mediante consola y a continuación pude hacer correctamente el push del código.

