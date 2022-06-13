# Instalación

El primer paso es descargar Rust a través de 'rustup', una herramienta de línea de comandos para administrar versiones de Rust y las herramientas relacionadas.

> Nota: Si prefieres no usar `rustup` por alguna razón, puedes consultar:
> [Otros medios de instalación][otherinstall] para más opciones.

[otherinstall]: https://forge.rust-lang.org/infra/other-installation-methods.html

A través de los siguientes pasos se explica como instalar la versión estable más reciente del compilador de Rust. Esto garantiza que todos los ejemplos en el libro seguirán compilando con versiones de Rust más nuevas. La salida podría diferir ligeramente debido a que Rust usualmente implementa mensajes de error y avisos para versiones previas.

### Instalando `rustup` en Linux o macOS

Si estás usando Linux o macOS, se debe abrir la terminal e ingresar el siguiente comando:

```console
$ curl --proto '=https' --tlsv1.3 https://sh.rustup.rs -sSf | sh
```

Esto descarga un script e inicia la instalación de la herramienta `rustup`, la cual instala la versión estable más reciente de Rust. Si la instalación es exitosa, aparecerá el siguiente mensaje en consola:

```text
Rust is installed now. Great!
```

También necesitará un "Linker", el cual es un programa que usa Rust para juntar sus salidas compiladas en un solo archivo. Si tienes errores con el Linker, se deberían solucionar instalando un compilador de C, el cual usualmente incluye un Linker. 

### Instalando `rustup` en Windows

En Windows, ve a [https://www.rust-lang.org/tools/install](https://www.rust-lang.org/tools/install) y sigue las instrucciones para instalar Rust. En algún punto de la instalación, recibirás un mensaje explicando que también es necesario instalar "C++ build tools" para Visual Studio 2013 o versiones posteriores. Es posible realizar esta instalación siguiendo las instrucciones descritas en el siguiente enlace: [Build Tools for Visual Studio 2019](https://visualstudio.microsoft.com/visual-cpp-build-tools/).

El resto de este libro usa comandos que funcionarán tanto en *cmd.exe* como en PowerShell


### Comprobando, Actualizando y desinstalando

Luego de la instalación, puedes comprobar el funcionamiento correcto de Rust ejecutando el siguiente comando en consola:

```console
$ rustc --version
```

Deberías ver, como respuesta, el número de la versión junto con algunos datos adicionales en el siguiente formato:

```text
rustc x.y.z (abcabcabc yyyy-mm-dd)
```

Si ves esta información, has instalado Rust satisfactoriamente! En caso contrario, debes verificar que Rust está en la variable de sistema `%PATH%` o si requieres de ayuda adicional, puedes visitar los foros de ayuda para principiantes que se encuentran en los siguientes enlaces:

- [Discord](https://discord.gg/rust-lang) 
- [Users Rust](https://users.rust-lang.org/)
- [Rust en stackoverflow](https://stackoverflow.com/questions/tagged/rust)


Posteriormente, puedes actualizar Rust a su última versión a través del comando:

```console
$ rustup update
```

Finalmente, si requieres desinstalar Rust y `rustup`, debes ejecutar el siguiente script desde la consola:

```console
$ rustup self uninstall
```