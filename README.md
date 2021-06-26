# Cambalache DB
Base de datos en entorno de desarrollo para la aplicación Cambalache.

## Requisitos
* [Docker](https://www.docker.com/) (Linux)
* [Docker Desktop](https://www.docker.com/products/docker-desktop) (Windows & Mac)
* [Docker Compose](https://docs.docker.com/compose/install/)

## 1. Preparación
Ejecutar los siguientes comandos para preparar el entorno de ejecución.

### 1.1. Linux & Mac
```shell
# Copiar plantillas
cp compose.template.yml compose.yml
cp init.template.sql init.sql

# Personalizar plantillas
# i   -> Editar valores necesarios
# :wq -> Guardar y salir
# :q! -> Salir sin guardar
vi compose.yml
vi init.sql
```

### 1.2. Windows
```shell
# Copiar plantillas
copy compose.template.yml compose.yml
copy init.template.sql init.sql

# Personalizar plantillas editando los valores necesarios
Notepad compose.yml
Notepad init.sql
```

## 2. Iniciar Servicio
Ejecutar los siguientes comandos para iniciar el servicio de PostgreSQL.
```shell
# Descargar imagen Docker
docker pull postgres:10

# Iniciar contenedor Docker
docker-compose -f compose.yml up -d
```

## 3. Crear Base de Datos y Usuario
Conectar al servicio de PostgreSQL iniciado en el paso 2 y ejecutar el
script **init.sql** para crear la base de datos, su usuario y conceder privilegios.


## 4. Eliminar Usuario y Base de Datos
Si es necesario, conectar al servicio de PostgreSQL iniciado en el paso 2 y ejecutar el
script **drop.sql** para revocar privilegios y eliminar el usuario y base de datos creados en el paso 3. 


## 5. Detener Servicio
Cuando sea necesario, ejecutar el siguiente comando para detener el servicio de PostgreSQL.
```shell
docker-compose -f compose.yml down
```
