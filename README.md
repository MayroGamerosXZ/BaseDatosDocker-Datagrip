Crear tu Primera Base de Datos en PostgreSQL usando Docker y DataGrip

Base de Datos Docker a Data Grip
Este documento explica de manera clara y sencilla cómo ejecutar una base de datos PostgreSQL en Docker, configurar DataGrip para conectarse a ella y crear una base de datos desde el entorno gráfico.

1. Ejecutar PostgreSQL con Docker
Para iniciar un contenedor de PostgreSQL utilizando Docker, ejecuta el siguiente comando en tu terminal:

Ejecutar en Terminal Docker
docker run --name NicoRobin -e POSTGRES_USER=robin -e POSTGRES_PASSWORD=robin1710 -p 5432:5432 -d postgres
Explicación de los parámetros:

--name NicoRobin: Nombre del contenedor (opcional).
-e POSTGRES_USER=robin: Usuario principal de la base de datos.
-e POSTGRES_PASSWORD=robin1710: Contraseña del usuario.
-p 5432:5432: Mapea el puerto 5432 del contenedor al de tu máquina local.
-d postgres: Usa la imagen oficial de PostgreSQL y ejecuta en modo detached.

Para comprobar que el contenedor está corriendo, utiliza:

Ejecutar en Terminal Docker
docker ps
Deberías ver una salida similar a:

Code
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS          PORTS                    NAMES
99075d3eb477   postgres  "docker-entrypoint.s…"  X seconds ago    Up X seconds    0.0.0.0:5432->5432/tcp   NicoRobin

2. Configuración de DataGrip
Sigue estos pasos para conectar DataGrip a tu base de datos PostgreSQL en Docker:

Abre DataGrip.
Haz clic en el botón "+" para agregar una nueva conexión y selecciona "PostgreSQL".
Ingresa los siguientes datos:
Host: localhost
Puerto: 5432
Usuario: robin
Contraseña: robin1710
Base de datos: postgres (por defecto)
Haz clic en "Test Connection" para verificar que la conexión sea exitosa.
Si todo está correcto, haz clic en "OK" para guardar la configuración.


3. Crear una nueva base de datos desde DataGrip
Conéctate al servidor utilizando la configuración anterior.
Haz clic derecho sobre el servidor o la conexión, selecciona "New" > "Database...".
Escribe el nombre deseado para la nueva base de datos.
Haz clic en "OK" para crearla.
¡Listo! Ahora tienes un entorno PostgreSQL corriendo en Docker y gestionado fácilmente desde DataGrip.

4. Recomendaciones y resolución de problemas
Verifica el puerto: Si tienes otra instancia de PostgreSQL corriendo en tu máquina local, puede haber conflicto en el puerto 5432. Puedes cambiar el puerto en el comando Docker (por ejemplo, -p 5433:5432) y ajustar la conexión en DataGrip.
Persistencia de datos: Si quieres que los datos de tu base de datos persistan aunque el contenedor se elimine, puedes agregar un volumen al comando Docker:

Ejecutar en Terminal Docker
docker run --name NicoRobin -e POSTGRES_USER=robin -e POSTGRES_PASSWORD=robin1710 -p 5432:5432 -v pgdata:/var/lib/postgresql/data -d postgres
Así, tus datos permanecerán guardados en el volumen pgdata.

Detener y eliminar el contenedor: Si quieres detener el contenedor, usa:

Ejecutar en Terminal Docker
docker stop NicoRobin

Para eliminarlo:
Ejecutar en Terminal Docker
docker rm NicoRobin

Creado por: Mayro Gameros
Contacto: barriosgamerosmayro@gmail.com
