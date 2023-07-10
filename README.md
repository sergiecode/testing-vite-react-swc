# Crear un proyecto con Vite

Este repositorio proporciona instrucciones sobre cómo crear un proyecto con Vite, un bundler de JavaScript rápido y ligero.

## Requisitos previos

Asegúrate de tener instalada la versión de Node.js 14.18+ o 16+. Si estás utilizando NPM, ejecuta el siguiente comando:

```
    npm create vite@latest
```

Si necesitas utilizar una plantilla específica, puedes especificarla junto con el nombre de tu proyecto. Por ejemplo, para crear un proyecto Vite + Vue, ejecuta alguno de los siguientes comandos:

# NPM 6.x
```
    npm create vite@latest my-vue-app --template vue
```

# NPM 7+, utilizando doble guión extra:
```
    npm create vite@latest my-vue-app -- --template vue
```
Para obtener más información sobre las plantillas compatibles, consulta el repositorio [create-vite](https://github.com/vitejs/create-vite).

## Plantillas de la comunidad

Si estás buscando plantillas adicionales mantenidas por la comunidad, puedes visitar [Awesome Vite](https://github.com/vitejs/awesome-vite). Estas plantillas incluyen herramientas y están dirigidas a diferentes frameworks. Puedes utilizar la herramienta [degit](https://github.com/Rich-Harris/degit) para clonar una plantilla y comenzar tu proyecto.
```
    npx degit user/project my-project
    cd my-project
    
    npm install
    npm run dev
```
Si el proyecto utiliza la rama principal (main) como rama por defecto, añade el sufijo `#main` al repositorio del proyecto al utilizar degit.

## Archivo index.html y la raíz del proyecto

En un proyecto Vite, el archivo index.html es fundamental y se encuentra en el directorio raíz del proyecto en lugar de estar oculto dentro de una carpeta pública. Durante el desarrollo, Vite actúa como un servidor y index.html es el punto de entrada de tu aplicación.

Vite trata index.html como código fuente y forma parte del gráfico de módulos. Resuelve las etiquetas `<script type="module" src="...">` que hacen referencia a tu código JavaScript. Incluso las etiquetas `<script type="module">` en línea y las hojas de estilo CSS referenciadas mediante `<link href>` también aprovechan las características específicas de Vite. Además, las URL dentro de index.html se vuelven a basar automáticamente, por lo que no es necesario utilizar marcadores de posición especiales como `%PUBLIC_URL%`.

Vite utiliza un "directorio raíz" desde el cual se sirven los archivos, y esto se referencia como `<root>` en la documentación. Las URL absolutas en tu código fuente se resolverán utilizando la raíz del proyecto como base, lo que te permite escribir código como si estuvieras trabajando con un servidor de archivos estático normal. Vite también puede manejar las dependencias que se resuelven fuera del directorio raíz, lo que lo hace útil incluso en una configuración basada en monorepo.

Vite también es compatible con aplicaciones multipágina que tienen varios puntos de entrada HTML.

## Especificar una raíz alternativa

Al ejecutar `vite`, se inicia el servidor de desarrollo utilizando el directorio de trabajo actual como raíz. Si necesitas especificar una raíz alternativa, puedes ejecutar `vite serve some/sub/dir`. Ten en cuenta que Vite también buscará tu archivo de configuración (`vite.config.js`) dentro de la raíz especificada.
