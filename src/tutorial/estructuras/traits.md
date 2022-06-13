# Traits (Rasgos)

Un trait indica al compilador una funcionalidad que tendrá un tipo en particular y que puede compartir con otros tipos. Podemos usar traits para definir el comportamiento compartido de una manera abstracta. Incluso, podemos usar trait para especificar que un tipo genérico puede ser cualquier tipo que tenga cierto comportamiento.

Los rasgos son similares a una característica que suele llamarse interfaces en otros lenguajes, aunque con algunas diferencias.

```rust
trait TieneArea {
    fn area(&self) -> f64; //Un funcion sin definir
}

struct Circulo {
    x: f64,
    y: f64,
    radio: f64,
}

impl TieneArea for Circulo {
    fn area(&self) -> f64 {
        std::f64::consts::PI * (self.radio * self.radio) //redifinicion de area para circulo
    }
}

struct Cuadrado {
    x: f64,
    y: f64,
    lado: f64,
}

impl TieneArea for Cuadrado {
    fn area(&self) -> f64 {
        self.lado * self.lado //redifinicion de area para cuadrado
    }
}
```

Los traits son útiles porque permiten a un tipo hacer ciertas promesas acerca de su comportamiento. La funciones genéricas pueden explotar esto para restringir los tipos que aceptan. Considera esta función, la cual no compila:

```rust
#trait TieneArea {
#    fn area(&self) -> f64; //Un funcion sin definir
#}
#
#struct Circulo {
#    x: f64,
#    y: f64,
#    radio: f64,
#}
#
#impl TieneArea for Circulo {
#    fn area(&self) -> f64 {
#        std::f64::consts::PI * (self.radio * self.radio) //redifinicion de area para circulo
#    }
#}
#
#struct Cuadrado {
#    x: f64,
#    y: f64,
#    lado: f64,
#}
#
#impl TieneArea for Cuadrado {
#    fn area(&self) -> f64 {
#        self.lado * self.lado //redifinicion de area para cuadrado
#    }
#}

fn imprimir_area<T>(figura: T) {
    println!("Esta figura tiene un area de {}", figura.area());
}
```
La sintaxis <T: TieneArea> se traduce en “cualquier tipo que implemente el trait TieneArea.”. A consecuencia de que los traits definen firmas de tipos de función, podemos estar seguros que cualquier tipo que implemente TieneArea tendrá un método .area().

```rust
#trait TieneArea {
#    fn area(&self) -> f64; //Un funcion sin definir
#}
#
#struct Circulo {
#    x: f64,
#    y: f64,
#    radio: f64,
#}
#
#impl TieneArea for Circulo {
#    fn area(&self) -> f64 {
#        std::f64::consts::PI * (self.radio * self.radio) //redifinicion de area para circulo
#    }
#}
#
#struct Cuadrado {
#    x: f64,
#    y: f64,
#    lado: f64,
#}
#
#impl TieneArea for Cuadrado {
#    fn area(&self) -> f64 {
#        self.lado * self.lado //redifinicion de area para cuadrado
#    }
#}
#fn imprimir_area<T: TieneArea>(figura: T) {
#    println!("Esta figura tiene un area de {}", figura.area());
#}
let c = Circulo {
    x: 0.0f64,
    y: 0.0f64,
    radio: 1.0f64,
};

let s = Cuadrado {
    x: 0.0f64,
    y: 0.0f64,
    lado: 1.0f64,
};

imprimir_area(c);
imprimir_area(s);
```