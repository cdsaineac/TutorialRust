# Concurrencia

### Hilos 

Ejecutan simultáneamente partes independientes de un programa.

#### Creando un hilo

1. Se importan las funciones relacionadas con hilos de `std::thread` con `use`. 

```rust,noplayground
use std::thread;
```
2. Para crear un hilo se usa `thread::spawn` que recibe una *closure* como argumento y retorna un *JoinHandler*.

```rust,noplayground
thread::spawn(|| { /* Código que se ejecutará en el hilo */ });
```

#### Creando un hilo - *Ejemplo 1*
```rust,editable
use std::thread;

fn main() {
    thread::spawn(|| {
        println!("Hola desde un nuevo hilo!");
    });
}
```
#### Creando un hilo - *Ejemplo 2*
```rust,editable
use std::thread;
use std::time::Duration;

fn main() {
    thread::spawn(|| {
        for i in 1..10 {
            println!("Hola {} desde el nuevo hilo!", i);
            thread::sleep(Duration::from_millis(1));
        }
    });

    for i in 1..5 {
        println!("Hola {} desde el hilo principal!", i);
        thread::sleep(Duration::from_millis(1));
    }
}
```
El nuevo hilo se detendrá cuando finalice el hilo principal.

Las llamadas a thread::sleep obligan a un hilo a detener su ejecución durante un breve período, lo que permite que se ejecute un hilo diferente.

#### Join handles

Para esperar a que todos los hilos terminen su ejecución, podemos usar el método `join`.
```rust,editable
use std::thread;

fn main() {
    let child = thread::spawn(|| {
        println!("Hola desde un hilo!");
    });
    let _ = child.join();
}
```
#### Join handle - *Ejemplo 2*
```rust,editable
use std::thread;
use std::time::Duration;

fn main() {
    let handle = thread::spawn(|| {
        for i in 1..10 {
            println!("Hola {} desde el nuevo hilo!", i);
            thread::sleep(Duration::from_millis(1));
        }
    });

    for i in 1..5 {
        println!("Hola {} desde el hilo principal!", i);
        thread::sleep(Duration::from_millis(1));
    }

    handle.join().unwrap();
}
```

#### `move` closure
Permite usar datos en un hilo en otro hilo.
```rust,editable
use std::thread;

fn main() {
    let v = vec![1, 2, 3];

    let handle = thread::spawn(|| {
        println!("Vector: {:?}", v);
    });

    handle.join().unwrap();
}
```

Si queremos forzar el closure para que se apropie de los valores que usa en el entorno, podemos usar `move` antes de la lista de parámetros.
```rust,editable
use std::thread;

fn main() {
    let v = vec![1, 2, 3];

    let handle = thread::spawn(move || {
        println!("Vector: {:?}", v);
    });

    handle.join().unwrap();
}
```