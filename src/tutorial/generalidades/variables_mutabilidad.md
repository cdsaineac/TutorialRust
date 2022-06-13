# Variables y mutabilidad

Por defecto, las variables en Rust son inmutables, lo que quiere decir que una vez que un valor está vinculado a un nombre, no puede cambiar ese valor. Este es uno de los muchos beneficios que da Rust para escribir código de una manera que se aproveche la seguridad y la fácil concurrencia. Sin embargo, aún tiene la opción de hacer que sus variables sean mutables.

#### Ejemplo declaración de variables 
```rust, editable
fn main() {
    let x = 5;
    println!("El valor de x es: {}", x);
    //x = 6;
    //println!("El valor de x es: {}", x);
}
```
#### Ejemplo declaración de variables mutables
```rust, editable
fn main() {
    let mut x = 5;
    println!("El valor de x es: {}", x);
    x = 6;
    println!("El valor de x es: {}", x);
}
```

## Constantes
Las constantes también son valores que están vinculados a un nombre y no se les permite cambiar, pero hay algunas diferencias entre constantes y variables.
1. No se permite usar *mut* 
2. Se debe indicar el tipo de dato al momento de declararla
3. Se pueden declarar en cualquier ámbito, incluido el ámbito local (alcance)
4. Solo pueden declararse formalmente, no como resultado de un valor calculado en timpo de ejecución

```rust, noplayground
const TRES_HORAS_EN_SEGUNDOS: u32 = 60 * 60 * 3;
```

## Shadowing
Este término se refiere a cuando una variable se declara con el mismo nombre de una variable previamente creada.    

```rust
fn main() {
    let x = 5;

    let x = x + 1;

    {
        let x = x * 2;
        println!("El valor de x en el alcance interno es: {}", x);
    }

    println!("El valor de x es: {}", x);
}
```
Es importante reconocer la diferencia entre mutabilidad y shadowing, debido a que efectivamente estamos creando una nueva variable cuando usamos *let* nuevamente, y no sobreescribiendo la variable anterior.