# Contenedores-en-Conexi-n

#  Contenedores en Conexión: Informe Técnico

Este informe documenta paso a paso la creación de contenedores Docker para tres motores de bases de datos (MySQL, MariaDB y PostgreSQL), su conexión desde clientes externos y la verificación de bases de datos creadas. Incluye comandos utilizados, reflexiones técnicas, puntos de evidencia visual y recomendaciones para automatizar el proceso.

---

##  Objetivo del proyecto

- Aprender a crear contenedores de bases de datos con Docker desde la terminal (CMD).
- Conectarse a cada contenedor desde clientes como DBeaver, HeidiSQL y Beekeeper Studio.
- Crear bases de datos dentro de cada contenedor y verificar su persistencia.
- Documentar el proceso con capturas de pantalla y reflexiones técnicas.

---

##  Tecnologías utilizadas

- **Docker CLI** para la creación y gestión de contenedores.
- **Imágenes oficiales**: `mysql:8`, `mariadb:10.5`, `postgres:13`.
- **Clientes de conexión**: DBeaver, HeidiSQL, Beekeeper Studio.
- **Sistema operativo**: Windows 10 (CMD como terminal principal).

---

##  Paso a paso con comandos y explicación

### 1. Crear contenedor MySQL

```bash
docker run -d --name mysql_container -e MYSQL_ROOT_PASSWORD=rootpass -p 3306:3306 mysql:8

-d: ejecuta el contenedor en segundo plano.

--name: asigna un nombre identificable al contenedor.

-e: define variables de entorno (en este caso, la contraseña del usuario root).

-p: expone el puerto 3306 del contenedor al host.

# Crear contenedor MariaDB

docker run -d --name mariadb_container -e MARIADB_ROOT_PASSWORD=rootpass -p 3307:3306 mariadb:10.5

Similar a MySQL, pero con puerto 3307 para evitar conflicto.

MariaDB es compatible con clientes MySQL.

# Crear contenedor PostgreSQL

docker run -d --name postgres_container -e POSTGRES_PASSWORD=rootpass -p 5432:5432 postgres:13

PostgreSQL usa el puerto 5432 por defecto.

La variable POSTGRES_PASSWORD define la contraseña del usuario postgres.

## Verificar contenedores activos

docker ps

Muestra los contenedores en ejecución.

Verifica que los tres motores estén corriendo correctamente.

## Verificar todos los contenedores (activos e inactivos)

docker ps -a

Incluye contenedores detenidos.

Útil para verificar el estado general del entorno.

### Conexión desde clientes externos

MySQL (puerto 3306)
Cliente: DBeaver o HeidiSQL.

Host: localhost

Usuario: root

Contraseña: rootpass

MariaDB (puerto 3307)
Cliente: HeidiSQL o DBeaver.

Host: localhost

Usuario: root

Contraseña: rootpass

PostgreSQL (puerto 5432)
Cliente: Beekeeper Studio o DBeaver.

Host: localhost

Usuario: postgres

Contraseña: rootpass

## Detener un contenedor (opcional)

docker stop mysql_container

Detiene el contenedor sin eliminarlo.

Útil para liberar recursos o simular fallos.

# FIN
