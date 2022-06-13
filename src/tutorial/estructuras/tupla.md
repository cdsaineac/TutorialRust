# Estructuras de Tupla

Las estructuras de tupla son un hibrido entre ambos tipos de datos: tiene el significado que proporciona el nombre de la estructura, pero no tienen nombres en sus campos, es decir, solo tienen el nombre del tipo de dato. Son útiles en casos para cuales nombrar cada campo puede ser redundante.

```rust
struct Color (u32, u32, u32);
struct Coordenada (i32, i32);

let blanco = Color (255,255,255);
let origen = Coordenada (0,0);

println!("Color: {}, {}, {}", blanco.0,blanco.1,blanco.2);
println!("Punto: {}, {}", origen.0, origen.1);
```