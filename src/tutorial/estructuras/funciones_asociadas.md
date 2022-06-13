# Funciones asociadas

Podemos definir funciones dentro de los bloques impl que no toman como parámetro a self. Estas se denominan funciones asociadas porque están asociadas con la estructura. Siguen siendo funciones, no métodos, porque no tienen una instancia de la estructura con la que trabajar.
Las funciones asociadas se utilizan a menudo para constructores que devolverán una nueva instancia de la estructura.

```rust
#struct Rectangulo {
#    alto: u32,
#    ancho: u32,
#}
#
#impl Rectangulo {
#    fn area(&self) -> u32 {
#        self.alto * self.ancho
#    }
#    
#    fn puede_contener(&self, otro: &Rectangulo) -> bool {
#        self.alto > otro.alto && self.ancho > otro.ancho
#    }
#}
impl Rectangulo {
    fn cuadrado(lado: u32) -> Rectangulo {
        Rectangulo {
            alto: lado,
            ancho: lado,
        }
    }
}
let cuadrado_uno = Rectangulo::cuadrado(10);
println!("Area del cuadrado: {}", cuadrado_uno.area());
```