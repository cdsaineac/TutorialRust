# Funciones

La función main, es el punto de entrada de toda la ejecución del programa. La palabra clave fn permite declarar nuevas funciones y el cuerpo de la función se define dentro de corchetes {}.
```rust
fn main() {
    println!("Hola, Mundo!");

    mi_funcion();
}

fn mi_funcion() {
    println!("Esta es mi función.");
}
```
### Parámetros
Para definir funciones que tienen parámetros, se debe seguir esta estructura:

```rust
fn main() {
    println!("Hola, Mundo!");

    mi_funcion(11,'p');
}

fn mi_funcion(x: i32, caracter: char) {
    println!("El valor de x es: {} y el caracter es {}", x,caracter);
}
```
### Retornando valores
No es necesario especificar el retorno dentro del cuerpo de la función, pero si se denota con una flecha -> en la declaración, luego de indicar los parámetros.

```rust
fn main() {
    let x = suma_dos(7);

    println!("El valor de x es: {}", x);
}

fn suma_dos(x: i32) -> i32 {
    x + 1
}
```