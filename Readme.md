# Repo to launch all microservices created

# This repo in github will be pointing to the diferentes Microservices-repos on github

# Steps to development environment

1. Clone the repositoty
2. Create a copy of `.env.example` to `.env` and set environment variables as needed
3. Execute the command `git submodule update --init --recursive` to rebuild submodules(microservices repositories)
4. Execute command `docker compose up --build` (this way allow you to see errors in real time, so if you use `docker compose up -d` in detached mode you have to execute command `docker logs <container>` to see errors)

# Production environment

1. Clone the repositoty
2. Create a copy of `.env.example` to `.env` and set environment variables as needed
3. Create the images with the command `docker compose -f docker-compose.prod.yml build`

### Pasos para crear los Git Submodules

1. Crear un nuevo repositorio en GitHub
2. Clonar el repositorio en la máquina local
3. Añadir el submodule, donde `repository_url` es la url del repositorio y `directory_name` es el nombre de la carpeta donde quieres que se guarde el sub-módulo (no debe de existir en el proyecto)

```
git submodule add <repository_url> <directory_name>
```

4. Añadir los cambios al repositorio (git add, git commit, git push)
   Ej:

```
git add .
git commit -m "Add submodule"
git push
```

5. Inicializar y actualizar Sub-módulos, cuando alguien clona el repositorio por primera vez, debe de ejecutar el siguiente comando para inicializar y actualizar los sub-módulos

```
git submodule update --init --recursive
```

6. Para actualizar las referencias de los sub-módulos

```
git submodule update --remote
```

## Importante

Si se trabaja en el repositorio que tiene los sub-módulos, **primero actualizar y hacer push** en el sub-módulo y **después** en el repositorio principal.

Si se hace al revés, se perderán las referencias de los sub-módulos en el repositorio principal y tendremos que resolver conflictos.
