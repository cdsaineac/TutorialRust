# Estructura Tipo-Unidad
También puedes definir estructuras que no tengan ningún campo. Se llaman structs unitarios porque se comportan de forma similar a () "Tupla de Tipo Unitaria". Las estructuras unitarias pueden ser útiles cuando necesitas implementar un rasgo (Trait) en algún tipo pero no tienes ningún dato que quieras almacenar en el propio tipo. 
```rust
struct AlwaysEqual;

let subject = AlwaysEqual;
```