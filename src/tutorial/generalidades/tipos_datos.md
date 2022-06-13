# Tipos de datos

Cada valor en Rust es de un cierto tipo, lo cual le dice a Rust qué tipo de dato se está especificando para que sepa cómo trabajar con esos datos.

Debemos tener en cuenta que Rust es un lenguaje de tipado estático, esto significa que debe conocer los tipos de todas las variables en el momento de la compilación. El compilador **generalmente** puede inferir qué tipo queremos usar en función del valor y cómo lo usamos.

Veremos dos subconjuntos de tipos de datos: escalares y compuestos.

## Tipos escalares

Un tipo escalar representa un valor único. Rust tiene cuatro tipos escalares principales: enteros, números de punto flotante, booleanos y caracteres. 

### Tipos enteros

Un número entero es un número sin un componente fraccionario. En Rust es importante indicar el tamaño que este entero ocupará y si lleva signo o no. Las siguientes variantes son validas para usarse en la declaración de un entero:

| Length  | Signed  | Unsigned |
|---------|---------|----------|
| 8-bit   | `i8`    | `u8`     |
| 16-bit  | `i16`   | `u16`    |
| 32-bit  | `i32`   | `u32`    |
| 64-bit  | `i64`   | `u64`    |
| 128-bit | `i128`  | `u128`   |
| arch    | `isize` | `usize`  |

### Tipos de puntos flotantes

Rust también tiene dos tipos primitivos para números de coma flotante. Los tipos de coma flotante de Rust son f32 y f64, que tienen un tamaño de 32 bits y 64 bits, respectivamente. Todos los números de tipo punto flotante tienen signo.
```rust
fn main() {
    let x = 2.0; // f64 por defecto

    let y: f32 = 3.0; // f32
}
```
Recordar que, como en muchos otros lenguajes, Rust permite realizar operaciones matemáticas básicas tales como 
- Suma *+*
- Resta *-*
- Multiplicación *\**
- División */*
- Módulo *%* 

### El tipo booleano
Los booleanos tienen un tamaño de un byte. El tipo booleano en Rust se especifica mediante bool

```rust
fn main() {
    let t = true;

    let f: bool = false; // con tipado de tipo explícito
}
```

### El tipo caracter
**char** de Rust es el tipo alfabético más primitivo del lenguaje:
```rust
fn main() {
    let c = 'z';
    let z = 'ℤ';
}
```

## Tipos Compuestos

Los tipos compuestos pueden agrupar varios valores en un solo tipo. Rust tiene dos tipos de compuestos primitivos: tuplas y matrices.

### El tipo de tupla

Una tupla es una forma general de agrupar una cantidad de valores con una variedad de tipos en un tipo compuesto. Las tuplas tienen una longitud fija: una vez declaradas, no pueden crecer ni reducir su tamaño.
```rust
fn main() {
    let tup: (i32, f64, u8) = (500, 6.4, 1);
    println!("El primer valor de la tupla es: {}", tup.0);
    println!("El segundo valor de la tupla es: {}", tup.1);
    println!("El tercer valor de la tupla es: {}", tup.2);
}
```
### El tipo arreglo
Otra forma de tener una colección de valores múltiples es con una matriz . A diferencia de una tupla, todos los elementos de una matriz deben tener el mismo tipo. A diferencia de los arreglos en otros lenguajes, los arreglos en Rust tienen una longitud fija.
```rust
fn main() {
    let a = [1, 2, 3];
    println!("El primer valor del arreglo es: {}", a[0]);
    println!("El segundo valor del arreglo es: {}", a[1]);
    println!("El tercer valor del arreglo es: {}", a[2]);
}
```