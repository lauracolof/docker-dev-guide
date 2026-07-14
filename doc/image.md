# Imagenes de docker

### Para descargar una imagen
Docker pull {nombre-imagen}

esto trae algo así: 
```powershell
Using default tag: latest
latest: Pulling from library/hello-world
4f55086f7dd0: Pull complete 
d5e71e642bf5: Download complete 
Digest: sha256:96498ffd522e70807ab6384a5c0485a79b9c7c08ca79ba08623edcad1054e62d
Status: Downloaded newer image for hello-world:latest
docker.io/library/hello-world:latest
```
`latest: Pulling from library/hello-world`: no necesariamente trae la última imagen, aunque sea una convención. 

`Digest: sha256:96498ffd522e70807ab6384a5c0485a79b9c7c08ca79ba08623edcad1054e62d`, es la firma con la que valida que la imagen (hello-world) sea la misma que está en internet

`status: Downloaded newer image for hello-world:latest` este mensaje no descargó nada, dice qeu la imagen es más nueva que la que está

Si volvemos a ejecutar el comando, docker container run hello-world y ahí está. Hasta este momento habíamos confirmado la firma con la imagen.

Si quisieramos hacer lo mismo desde Docker Desktop

### Para eliminar las imagágenes
Podemos hacerlo por supuesto por la UI (Docker Desktop)
Pero tambien podemos hacerlo con los comandos: Si tecleamos `docker container --help`, se nos va a dar toda la lista de comandos disponibles.

- `docker container ls` (que reemplaza docker ps) nos muestra el listado de todos los contenedores que tenemos corriendo.

- `docker container ls -a` ero para que muestre todos, independientemente si están corriendo o no
- `docker container rm +` para eliminar un container o varios, con el comando  y el/los containerID, nombre o shortcut del id (primeros tres dígitos). 
- `docker container prune` para eliminar todos los containers deteneidos 