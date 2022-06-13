# Enumeraciones

Las enumeraciones permiten definir un tipo enumerando sus posibles variantes, de ahí su nombre. 
```rust
enum Mensaje {
    Salir, //Estructura unitaria
    CambiarColor(i32, i32, i32), //Estructura de Tupla
    Mover { x: i32, y: i32 }, //Estructura
    Escribir(String), //Estructura de Tupla
}

let w: Mensaje = Mensaje::Escribir(String::from("Hola Mundo!"));
let x: Mensaje = Mensaje::Mover { x: 3, y: 4 };
```
Utilizamos la sintaxis :: para hacer uso de cada variante: las variantes están dentro del ámbito del enum. Lo que hace que lo siguiente sea valido:
```rust
#enum Mensaje {
#    Salir, //Estructura unitaria
#    CambiarColor(i32, i32, i32), //Estructura de Tupla
#    Mover { x: i32, y: i32 }, //Estructura
#    Escribir(String), //Estructura de Tupla
#}
enum TurnoJuegoMesa {
    Mover { celdas: i32 }, //Estructura
    Pasar, //Estructura unitaria
}
let y: TurnoJuegoMesa = TurnoJuegoMesa::Mover { celdas: 1 };
let z: Mensaje = Mensaje::Mover { x: 3, y: 4 };
```