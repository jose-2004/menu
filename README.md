## Codigo y explicacion y ejecucion

Se definen las acciones para cada elemento del menú:

- Nuevo Archivo: Abre un cuadro de diálogo para ingresar el nombre del nuevo archivo y muestra el nombre en la consola.
- Abrir Archivo: Abre un FileChooser para seleccionar un archivo y muestra el nombre del archivo en la consola.
- Guardar Archivo: Abre un FileChooser para guardar un archivo, escribe un contenido de ejemplo en el archivo y muestra el nombre del archivo en la consola.
- Salir: Muestra un cuadro de confirmación antes de cerrar la aplicación.
- Cortar, Copiar y Pegar: Muestra mensajes en la consola.
- Acerca de: Muestra un cuadro de diálogo con información sobre la aplicación.

The workspace contains two folders by default, where:

- `src`: the folder to maintain sources
- `lib`: the folder to maintain dependencies

Meanwhile, the compiled output files will be generated in the `bin` folder by default.

> If you want to customize the folder structure, open `.vscode/settings.json` and update the related settings there.

## Dependency Management

The `JAVA PROJECTS` view allows you to manage your dependencies. More details can be found [here](https://github.com/microsoft/vscode-java-dependency#manage-dependencies).
