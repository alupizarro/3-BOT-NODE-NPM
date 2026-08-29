# Proyecto Node.js y npm

## Objetivo

En este trabajo realicé un proyecto de Node.js utilizando npm. Configuré el `package.json`, el `package-lock.json`, las `dependencies`, las `devDependencies` y los scripts.
También hice pruebas con `npm install` y `npm ci` desde una copia limpia del proyecto para poder ver la diferencia entre los dos comandos.

## Crear el proyecto

Primero creé una carpeta llamada `3-BOT-NODE-NPM`.
Desde la terminal comprobé que Node.js y npm estuvieran instalados:
```bash
node -v
npm -v
```
Las versiones que utilicé fueron:
* Node.js: `v24.15.0`
* npm: `11.12.1`
Después inicialicé el proyecto con:

```bash
npm init -y
```
Este comando creó el archivo `package.json`.

## Archivo package.json

El archivo `package.json` tiene la información principal y la configuración del proyecto.
También configuré los scripts:
```json
"scripts": {
  "dev": "nodemon index.js",
  "test": "node index.js",
  "start": "node index.js"
}
```

### Scripts

* `npm run dev`: ejecuta el proyecto utilizando `nodemon`.
* `npm test`: ejecuta el archivo `index.js`.
* `npm start`: inicia el proyecto.
Probé los tres scripts para comprobar que funcionaran.

## Archivo index.js

Creé el archivo `index.js` con un mensaje sencillo para comprobar que Node.js y los scripts funcionaran correctamente:
```javascript
console.log("¡Hola! El proyecto del bot está funcionando correctamente.");
```
También lo ejecuté directamente con:
```bash
node index.js
```
Y apareció el siguiente mensaje:
```text
¡Hola! El proyecto del bot está funcionando correctamente.
```

## Dependencies

Instalé `lodash` como dependencia del proyecto utilizando:
```bash
npm install lodash
```
Esto agregó `lodash` dentro de `dependencies`.
Las `dependencies` son las dependencias que necesita el proyecto.

## DevDependencies

Instalé `nodemon` como dependencia de desarrollo con:
```bash
npm install --save-dev nodemon
```
Esto agregó `nodemon` dentro de `devDependencies`.

Las `devDependencies` son dependencias que se utilizan durante el desarrollo.
Después configuré `nodemon` en el script `dev`:
```json
"dev": "nodemon index.js"
```
Lo probé con:
```bash
npm run dev
```

## package-lock.json

Cuando instalé las dependencias, npm creó automáticamente el archivo `package-lock.json`.
Este archivo guarda información sobre las versiones de las dependencias que se instalaron. No lo modifiqué manualmente.

## node_modules

La carpeta `node_modules` contiene las dependencias que instala npm.
No la incluí en el repositorio de Git porque se puede volver a crear utilizando:
```bash
npm install```
o:
```bash
npm ci
```

## .gitignore

Creé el archivo `.gitignore` y agregué:
```text
node_modules/
```
De esta forma Git no incluye la carpeta `node_modules` en el repositorio.

## Prueba de npm install

Para hacer la prueba desde una copia limpia utilicé una copia del proyecto llamada:
```text
3-BOT-NODE-NPM-INSTALL
```
En esa copia eliminé la carpeta `node_modules`, dejando los archivos principales del proyecto.
Después ejecuté:

```bash
npm install
```
El resultado fue:
```text
added 29 packages, and audited 30 packages in 17s
5 packages are looking for funding
run `npm fund` for details
found 0 vulnerabilities
```

Esto me dejó comprobar que `npm install` volvió a instalar las dependencias y creó nuevamente la carpeta `node_modules`.

Después ejecuté otra vez:
```bash
npm install
```
Y apareció:
```text
up to date, audited 30 packages in 2s
5 packages are looking for funding
run `npm fund` for details
found 0 vulnerabilities
```
Esto me permitió ver que, como los paquetes ya estaban instalados, npm indicó que todo estaba actualizado.

## Prueba de npm ci

Después volví a eliminar la carpeta `node_modules` de la copia de prueba para hacer una instalación limpia.
Ejecuté:
```bash
npm ci
```
El resultado fue:
```text
added 29 packages, and audited 30 packages in 8s
5 packages are looking for funding
run `npm fund` for details
found 0 vulnerabilities
```
Después de ejecutar el comando volvió a aparecer la carpeta `node_modules`.

## Diferencia entre npm install y npm ci

Después de hacer las pruebas pude ver la diferencia entre los dos comandos.

### npm install

Se utiliza para instalar las dependencias del proyecto.
En la copia limpia volvió a instalar los paquetes y creó la carpeta `node_modules`.
Cuando lo ejecuté otra vez, indicó que los paquetes ya estaban instalados y que todo estaba actualizado.

### npm ci

Se utiliza para hacer una instalación limpia utilizando el archivo `package-lock.json`.
En mi prueba eliminé primero `node_modules` y después ejecuté `npm ci`. El comando volvió a instalar los paquetes.

## Comparación realizada

| Comando                  | Situación                | Resultado                                  |
| ------------------------ | ------------------------ | ------------------------------------------ |
| `npm install`            | Copia sin `node_modules` | Instaló 29 paquetes                        |
| `npm install` nuevamente | Paquetes ya instalados   | Indicó `up to date`                        |
| `npm ci`                 | Copia sin `node_modules` | Instaló 29 paquetes utilizando el lockfile |

## Estructura del proyecto

```text
3-BOT-NODE-NPM/
│
├── node_modules/
├── .gitignore
├── index.js
├── package.json
├── package-lock.json
└── README.md
```
La carpeta `node_modules` está en mi computadora, pero no se sube al repositorio porque está incluida en el archivo `.gitignore`.

## Comandos principales utilizados

```bash
node -v
npm -v
npm init -y
node index.js
npm run dev
npm test
npm start
npm install lodash
npm install --save-dev nodemon
npm install
npm ci
git init
git status
git add .
git commit -m "Crear proyecto Node.js y npm"
git log --oneline
```

## Repositorio instalable

El proyecto cuenta con los archivos `package.json` y `package-lock.json`.
Por eso, al tener una copia del proyecto, se pueden instalar las dependencias con:
```bash
npm install
```
También se puede hacer una instalación limpia con:
```bash
npm ci
```
Después de instalar las dependencias se puede ejecutar el proyecto con:
```bash
npm run dev
npm test
npm start
```

## Registro de decisiones

Utilicé `lodash` como dependencia y `nodemon` como dependencia de desarrollo.
También utilicé `nodemon` en el script `dev` para poder ejecutar el programa mientras se realizan cambios.
Decidí no incluir `node_modules` en el repositorio porque las dependencias se pueden volver a instalar utilizando `package.json` y `package-lock.json`.
Por último, hice una copia limpia del proyecto y realicé las pruebas con `npm install` y `npm ci`. Esto me permitió ver en la práctica cómo funcionan los dos comandos y cuál es la diferencia entre ellos.
