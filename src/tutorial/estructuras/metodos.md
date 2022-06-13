# Métodos

Los métodos son similares a las funciones: se declaran con la palabra clave fn y su nombre; pueden tener parámetros y un valor de retorno, y contienen código que se ejecuta cuando se invoca. 
Sin embargo, los métodos son diferentes de las funciones en que se definen dentro del contexto de una estructura (o una enumeración o un objeto de rasgo), y su primer parámetro es siempre self, que representa la instancia de la estructura en la que se está llamando al método.

```rust
struct Rectangulo {
    alto: u32,
    ancho: u32,
}

impl Rectangulo {
    fn area(&self) -> u32 {
        self.alto * self.ancho
    }
    
    fn puede_contener(&self, otro: &Rectangulo) -> bool {
        self.alto > otro.alto && self.ancho > otro.ancho
    }
}
```

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
let rectangulo_uno = Rectangulo {
    alto: 50,
    ancho: 35,
};
println!("Area del rentangulo: {}", rectangulo_uno.area());

let rectangulo_dos = Rectangulo {
    alto: 60,
    ancho: 40,
};
println!("Puede 2 contener a 1: {}", rectangulo_dos.puede_contener(&rectangulo_uno));
println!("Puede 1 contener a 2: {}", rectangulo_uno.puede_contener(&rectangulo_dos));
```