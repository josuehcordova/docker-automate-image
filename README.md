# docker-automate-image
scripts npm para automatizar el trabajo con imágenes de docker.
scripts npm para automatizar las imágenes del acoplador.

Una forma fácil de ejecutar la secuencia típica de compilación, ejecución y envío de una imagen de acoplador desde un proyecto de nodo a un repositorio de acoplador privado o al concentrador de acoplador público.

Utiliza el nombre y el número de versión de package.json para mantener alineados el nombre y la versión de su ventana acoplable.

## Uso
en su proyecto, ejecute

    npm install docker-build-run-push --save

Si está presionando a un repositorio de docker privado, agregue lo siguiente a su paquete. Json

    "docker-registry": "docker.your-private.com",

O si está presionando al concentrador público de acopladores, agregue lo siguiente a su paquete. Json

    "docker-user": "juecho".

Agregue algunos scripts que se vean así. Puede ajustarse a su gusto

    "scripts": {
  	    "docker-build": "rm -rf node_modules && npm i --production && docker-build",
  	    "docker-run": "docker-run",
  	    "docker-push": "docker-push",
    },

Ahora en su proyecto, cuando esté listo para hacer una nueva imagen, introduzca su número de versión en package.json.

Para construir rápidamente una imagen de ventana acoplable local, para ejecutarla más tarde

    npm run docker-build

Ejecuta la imagen del acoplador local recién construido

    npm run docker-run

Empuje la imagen del acoplador al registro docker especificado en su paquete. Json

    npm run docker-push

Argumentos de docker-push
Incluir un tag diferente segun el ambiente 
    npm run docker-push tag=prod

Argumentos de docker-run
Es común tener que pasar argumentos cuando se ejecuta una ventana acoplable. El carácter '+' para dividir los argumentos para el comando docker.

Aquí hay algunos ejemplos de lo que significan

Ejecute un comando diferente en la imagen del acoplador y luego el CMD especificado

    npm run docker-run — node ./bin/cli.js

Pase un puerto y un archivo env como argumentos.

    npm run docker-run -- -p 3000:3000 --env-file .env +

Comience una terminal interactiva

    npm run docker-run -- -i -t + /bin/bash

También puede hacerlo agregando directamente a su script npm. Aquí hay un ejemplo de configuración de variables de entorno para docker:

    "docker-run": "docker-run \"-e SPOT_TASKS=geocode,khatba,es-sync +\"",
