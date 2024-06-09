## Codigo y explicacion y ejecucion

Se definen las acciones para cada elemento del menú:

- Nuevo Archivo: Abre un cuadro de diálogo para ingresar el nombre del nuevo archivo y muestra el nombre en la consola.
- Abrir Archivo: Abre un FileChooser para seleccionar un archivo y muestra el nombre del archivo en la consola.
- Guardar Archivo: Abre un FileChooser para guardar un archivo, escribe un contenido de ejemplo en el archivo y muestra el nombre del archivo en la consola.
- Salir: Muestra un cuadro de confirmación antes de cerrar la aplicación.
- Cortar, Copiar y Pegar: Muestra mensajes en la consola.
- Acerca de: Muestra un cuadro de diálogo con información sobre la aplicación.

Codigo
       
    import javafx.application.Application;           
    import javafx.scene.Scene;
    import javafx.scene.control.*;
    import javafx.scene.layout.BorderPane;
    import javafx.stage.FileChooser;
    import javafx.stage.Stage;
    import java.io.File;
    import java.io.FileWriter;
    import java.io.IOException;
    
       
    public class MenuBarExample extends Application {

    @Override
    public void start(Stage primaryStage) {
        // Crear la barra de menú principal
        MenuBar menuBar = new MenuBar();

        // Menús principales
        Menu menuArchivo = new Menu("Archivo");
        Menu menuEditar = new Menu("Editar");
        Menu menuAyuda = new Menu("Ayuda");

        // Añadir menús principales a la barra de menú
        menuBar.getMenus().addAll(menuArchivo, menuEditar, menuAyuda);

        // Elementos del menú "Archivo"
        MenuItem nuevoArchivo = new MenuItem("Nuevo");
        MenuItem abrirArchivo = new MenuItem("Abrir");
        MenuItem guardarArchivo = new MenuItem("Guardar");
        MenuItem salir = new MenuItem("Salir");

        // Añadir elementos al menú "Archivo"
        menuArchivo.getItems().addAll(nuevoArchivo, abrirArchivo, guardarArchivo, new SeparatorMenuItem(), salir);

        // Elementos del menú "Editar"
        MenuItem cortar = new MenuItem("Cortar");
        MenuItem copiar = new MenuItem("Copiar");
        MenuItem pegar = new MenuItem("Pegar");

        // Añadir elementos al menú "Editar"
        menuEditar.getItems().addAll(cortar, copiar, pegar);

        // Elementos del menú "Ayuda"
        MenuItem acercaDe = new MenuItem("Acerca de");

        // Añadir elementos al menú "Ayuda"
        menuAyuda.getItems().add(acercaDe);

        // Definir acciones para cada elemento de menú
        nuevoArchivo.setOnAction(e -> {
            TextInputDialog dialog = new TextInputDialog("Nuevo archivo");
            dialog.setTitle("Nuevo Archivo");
            dialog.setHeaderText("Crear un nuevo archivo");
            dialog.setContentText("Nombre del archivo:");

            dialog.showAndWait().ifPresent(name -> System.out.println("Archivo creado: " + name));
        });

        abrirArchivo.setOnAction(e -> {
            FileChooser fileChooser = new FileChooser();
            fileChooser.setTitle("Abrir Archivo");
            File file = fileChooser.showOpenDialog(primaryStage);
            if (file != null) {
                System.out.println("Archivo abierto: " + file.getName());
            }
        });

        guardarArchivo.setOnAction(e -> {
            FileChooser fileChooser = new FileChooser();
            fileChooser.setTitle("Guardar Archivo");
            File file = fileChooser.showSaveDialog(primaryStage);
            if (file != null) {
                try (FileWriter writer = new FileWriter(file)) {
                    writer.write("Contenido de ejemplo");
                    System.out.println("Archivo guardado: " + file.getName());
                } catch (IOException ex) {
                    System.out.println("Error al guardar el archivo: " + ex.getMessage());
                }
            }
        });

        salir.setOnAction(e -> {
            Alert alert = new Alert(Alert.AlertType.CONFIRMATION);
            alert.setTitle("Salir");
            alert.setHeaderText("Salir de la aplicación");
            alert.setContentText("¿Estás seguro de que deseas salir?");
            alert.showAndWait().ifPresent(response -> {
                if (response == ButtonType.OK) {
                    primaryStage.close();
                }
            });
        });

        cortar.setOnAction(e -> System.out.println("Cortar"));
        copiar.setOnAction(e -> System.out.println("Copiar"));
        pegar.setOnAction(e -> System.out.println("Pegar"));

        acercaDe.setOnAction(e -> {
            Alert alert = new Alert(Alert.AlertType.INFORMATION);
            alert.setTitle("Acerca de");
            alert.setHeaderText("Acerca de esta aplicación");
            alert.setContentText("Esta es una aplicación de ejemplo para mostrar una barra de menú en JavaFX.");
            alert.showAndWait();
        });

        // Layout principal
        BorderPane root = new BorderPane();
        root.setTop(menuBar);

        // Crear la escena y añadirla al escenario
        Scene scene = new Scene(root, 800, 600);
        primaryStage.setTitle("Ejemplo de MenuBar en JavaFX");
        primaryStage.setScene(scene);
        primaryStage.show();
    }

    public static void main(String[] args) {
        launch(args);
    }
    } 

##  Ejecucion

![image](https://github.com/jose-2004/menu/assets/80079088/6bb5aec8-cbc1-455a-8a11-1a9fa8c6e041)
![image](https://github.com/jose-2004/menu/assets/80079088/583360f7-0aeb-4d31-86f0-55e657ebc37d)


