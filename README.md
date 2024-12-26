# Guia para arrancar el proyecto localmente

### Tecnologias implementadas:

`Node.js, React, Tailwind CSS, Express.js, MongoDB, Mongoose, JWT, Cloudinary, TypeScript`

Repositorio de Frontend - https://github.com/Calvinuhh/devtree_client

Repositorio de Backend - https://github.com/Calvinuhh/devtree_server

La version de `Node` utilizada para la prueba es la version `22.11.0`, en caso de no contar con esa version se puede hacer uso de `Nvm` (Node Version Manager) para instalar la version correspondiente.

Este proyecto tiene separacion de **_Frontend y Backend_** por lo que se tendra que descargar ambos repositorios por separado.

Se recomienda tener a la mano el `CLOUD NAME`, `API KEY` y `API SECRET` de Cloudinary ya que este proyecto utiliza **Cloudinary** en el **_Backend_**.

Primeramente de descargaran los 2 repositorios en una carpeta que sera la carpeta raiz.

### Repositorio de Frontend:

```
git clone https://github.com/Calvinuhh/devtree_client.git
```

### Repositorio de Backend:

```
git clone https://github.com/Calvinuhh/devtree_server.git
```

Obtendremos 2 carpetas: **_devtree_client_** y **_devtree_server_**

La primera accion que se realizara sera instalar las dependencias de ambos proyectos, en cada carpeta se escribira el comando `npm install` para instalar las dependencias.

## devtree_client

```powershell
cd devtree_client
npm install
```

## devtree_server

```powershell
cd devtree_server
npm install
```

# Variables de entorno

Una vez instaladas las dependencias cambiaremos el archivo `.env.demo` a `.env` en ambas carpetas, tanto de **_devtree_client_** como **_devtree_server_**

Ahora bien ya cambiamos el nombre del archivo de las variables de entorno ahora la siguiente accion sera reemplazar las variables de entorno por las correspondientes, se mostrara a continuacion que variables de entorno contiene cada carpeta.

### devtree_client

```powershell
VITE_SERVER_URL=(URL del Server)
```

### devtree_server

```powershell
PORT=(puerto del server)
DB_URI=(URI de mongodb)
CLIENT_URL=(URL del Cliente)
JWT_SECRET=(Secret)

CLOUD_NAME=(Cloudinary CLOUD_NAME)
API_KEY=(Cloudinary API_KEY)
API_SECRET=(Cloudinary API_SECRET)
```

Reemplazar las variables de entorno con los valores necesarios para levantar los proyectos en desarrollo.

Tener en cuenta que en la variable de entorno `VITE_SERVER_URL` de **_devtree_client_** hace referencia a la URL donde esta levantado el servidor, por lo que si por ejemlo el servidor es: `http://localhost:3000` ese sera el valor que se le asignara a la variable `VITE_SERVER_URL`.

Este proyecto utiliza un cluster de **_Mongo Atlas_**, por lo que la variable `DB_URI` debe hacer referencia al _string_ de conexion de la instancia del cluster de Mongo Atlas, en caso de no implementar un cluster de **_Mongo Atlas_** normalmente el valor de **_DB_URI_** seria el siguiente: `mongodb://localhost:27017/{db_name}` para realizar una conexion local con MongoDB

Si no funciona con _localhost_ se puede intentar con un string basado en una conexion **IPv4**

por ejemplo: `mongodb://127.0.0.1:27017/{db_name}`

Como se puede observar el **_ultimo_** parametro del string seria el nombre de como se quiera nombrar a la nueva base de datos.

Como se menciono anteriormente si no se quiere implementar **_Mongo Atlas_** se puede probar con una base de datos localmente y para esto se levantara el servidor de la base de datos de **Mongo** con el siguiente comando:

```powershell
mongod
```

Una vez levantado el servidor de la base de datos, se procedera a levantar el servidor.

## devtree_server

Para esto en la carpeta devtree_server se implementara el comando npm run:

```powershell
  start
    node dist/index.js
available via `npm run-script`:
  dev
    nodemon src/index.ts
  devNoWarnings
    nodemon --watch src --exec "node --no-warnings -r ts-node/register" src/index.ts
  build
    tsc
```

Al implementar el comando `npm run dev` en la consola se mostraran unas alertas como estas:

```powershell
> server@1.0.0 dev
> nodemon src/index.ts

[nodemon] 3.1.9
[nodemon] to restart at any time, enter `rs`
[nodemon] watching path(s): *.*
[nodemon] watching extensions: ts,json
[nodemon] starting `ts-node src/index.ts`
(node:12972) ExperimentalWarning: CommonJS module C:\Users\calvi\Downloads\devtree_server\src\utils\manageHandle.ts is loading ES Module C:\Users\calvi\Downloads\devtree_server\node_modules\slug\slug.js using require().
Support for loading ES Module in require() is an experimental feature and might change at any time
(Use `node --trace-warnings ...` to show where the warning was created)
Base de datos conectada exitosamente
Server listening on port: 3000, node version: 22.12
```

Ya que la libreria **slug** genera un conflicto con el tema de las importaciones de los modulos, esto no genera ningun problema realmente, el proyecto sigue su correcto funcionamiento a pesar de estas advertencias.

Sin embargo para no ver las advertencias se pude levantar el servidor con el comando `npm run devNoWarnings`.

```powershell
> server@1.0.0 devNoWarnings
> nodemon --watch src --exec "node --no-warnings -r ts-node/register" src/index.ts

[nodemon] 3.1.9
[nodemon] to restart at any time, enter `rs`
[nodemon] watching path(s): src\**\*
[nodemon] watching extensions: ts,json
[nodemon] starting `node --no-warnings -r ts-node/register src/index.ts`
Base de datos conectada exitosamente
Server listening on port: 3000, node version: 22.12
```

Una vez el servidor levantado en la carpeta de **_devtree_client_** levantaremos el proyecto del _frontend_

## devtree_client

```powershell
npm run dev
```

```powershell
> client@0.0.0 dev
> vite


  VITE v6.0.3  ready in 408 ms

  ➜  Local:   http://localhost:5173/
  ➜  Network: use --host to expose
  ➜  press h + enter to show help
```

Con el servidor y el cliente levantados y si reemplazamos las variables de entorno correctamente podremos ver el proyecto funcionando

<img src="https://res.cloudinary.com/deotitxt8/image/upload/v1735235147/devtree/Screenshot_2024-12-26_124527_xfknxf.png">
