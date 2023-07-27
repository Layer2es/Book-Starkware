# Book-Starkware
Libro de L2 en Español con Información en general del ecosistema de Starkware

## Parte 1: Instalación de mdBook

mdBook es una herramienta que te permite crear libros y documentación en formato HTML a partir de archivos Markdown. 

1. **Instala Rust**: mdBook está escrito en Rust, por lo que primero debes asegurarte de tener Rust y su herramienta de gestión de paquetes, Cargo, instalados en tu sistema. Puedes instalar Rust utilizando rustup siguiendo las instrucciones en [rustup.rs](https://rustup.rs/), aunque el comando que puede utilizar previo revisar documentación:

    ```
    curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
    ```

2. **Instala mdBook**: Con Rust y Cargo instalados, ahora puedes instalar mdBook. Abre una terminal o línea de comandos y ejecuta el siguiente comando:

   ```
   cargo install mdbook
   ```

   Esto descargará e instalará mdBook en tu sistema.

3. **Instala la extensión de traducción (opcional)**: Si planeas traducir el libro a otros idiomas, puedes instalar la extensión de traducción. Ejecuta el siguiente comando:

   ```
   cargo install mdbook-i18n-helpers
   ```

## Parte 2: Interactuar con los archivos .md

Una vez que tengas mdBook instalado, puedes interactuar con los archivos .md de la siguiente manera:

1. **Clona el repositorio**: Comienza clonando el repositorio que contiene el libro en el que deseas trabajar.

2. **Edita archivos .md**: Utiliza cualquier editor de texto o IDE para editar los archivos .md del libro en inglés (o el idioma principal). Los archivos .md contienen el contenido del libro en formato Markdown.

3. **Visualizar cambios localmente**: Para ver los cambios que realizas en el libro, puedes usar el siguiente comando en la terminal dentro del directorio del repositorio:

   ```
   mdbook serve --open
   ```

   Esto iniciará un servidor local y abrirá el libro en tu navegador en [localhost:3000](http://localhost:3000). Cualquier cambio que hagas en los archivos .md se reflejará en el libro que estás viendo en el navegador. Puedes refrescar la página del navegador para ver los cambios.

## Parte 3: Crear una solicitud de extracción (Pull Request)

Una vez que hayas realizado los cambios en el libro y estés satisfecho con ellos, puedes contribuir al repositorio creando una solicitud de extracción (Pull Request). Aquí tienes los pasos básicos para hacerlo:

1. **Haz un fork del repositorio**: Visita el repositorio en GitHub y haz clic en el botón `Fork` en la esquina superior derecha. Esto creará una copia del repositorio en tu cuenta de GitHub.

2. **Clona tu repositorio fork**: Clona el repositorio que acabas de forkear en tu máquina local usando el comando `git clone`.

3. **Crea una rama (branch)**: Antes de realizar cambios, crea una rama nueva usando `git checkout -b nombre-de-tu-rama`. Es buena práctica trabajar en una rama separada para cada funcionalidad o corrección que desees aportar.

4. **Realiza los cambios**: Edita los archivos .md según tus contribuciones.

5. **Realiza commit de los cambios**: Después de hacer los cambios, utiliza `git add` para agregar los archivos modificados y `git commit -m "Descripción de tus cambios"` para realizar el commit de los cambios.

6. **Envía la rama al repositorio remoto**: Usa `git push origin nombre-de-tu-rama` para enviar la rama al repositorio en GitHub.

7. **Crea la Pull Request**: Ve a tu repositorio en GitHub y verás un mensaje sugiriendo que hagas una Pull Request. Haz clic en el botón `Compare & pull request` para crear la Pull Request.

8. **Describe tu Pull Request**: Proporciona una descripción clara y concisa de los cambios que has realizado y por qué deberían ser aceptados. Luego, crea la Pull Request.

Una vez que hayas creado la Pull Request, los colaboradores del proyecto revisarán tus cambios y, si todo está bien, los integrarán en el libro principal.

