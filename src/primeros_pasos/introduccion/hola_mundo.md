# Hola Mundo

Ya que Rust se ha instalado, podemos iniciar programando el tradicional Hola Mundo como programa de prueba.

### Creando un directorio de proyecto

El primer paso es crear un directorio para almacenar el código de Rust. Para esto se debe abrir la terminal e ingresar los siguientes comandos:

```console
$ mkdir ~/projects
$ cd ~/projects
$ mkdir hello_world
$ cd hello_world
```

En caso de que se esté usando CMD de Windows, se deben usar estos comandos:

```cmd
> mkdir "%USERPROFILE%\projects"
> cd /d "%USERPROFILE%\projects"
> mkdir hello_world
> cd hello_world
```

### Escribiendo y corriendo el primer programa de Rust

Posterior a la creación del directorio, se debe crear un archivo fuente, al que nombraremos *main.rs*. Los archivos de Rust siempre terminan con la extensión *.rs*

En el archivo creado, escribiremos el código de la siguiente manera:

```rust, editable
fn main() {
    println!("Hello, world!");
}
```