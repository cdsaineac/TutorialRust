# **Paso de mensajes entre hilos**

En Rust existe el concepto de *channel* para el paso de mensajes en programación concurrente. Este es como si fuera un caudal de agua, donde lo que se ponga en él va a correr en el sentido que vaya el agua.

Este canal tiene dos partes: un transmisor y un receptor. El transmisor es por medio del cual se envia la información y el receptor es donde llega esa información.



### ¿Como se declara un canal en Rust?

`let (tx, rx) = mpsc::channel();`

En este caso ***tx*** va a ser el transmisor del canal y ***rx*** va a ser el receptor.

## Ejemplo Basico

```rust
use std::sync::mpsc;
use std::thread;

let (tx, rx) = mpsc::channel();
let valor = "$100.000";

thread::spawn(move || {
    let precio = String::from(valor);
    println!("Precio: {}", precio);
    tx.send(precio).unwrap();
    //println!("Precio: {}", precio);
});

let received = rx.recv().unwrap();
println!("El precio del producto es: {}", received);
```

## Ejemplo Basico - Parte2
```rust
use std::sync::mpsc;
use std::thread;

let (tx, rx) = mpsc::channel();

let precio = 100000;

println!("El precio del producto es: ${}.", precio);

thread::spawn(move || {
    let bono = 10000;
    let valor = precio - bono;
    tx.send(valor).unwrap();
    println!("Bono de ${} aplicado.", bono);
});

let total = rx.recv().unwrap();

println!("El precio total es: ${}.", total);
```
## Ejemplo Enviando 2 Variables
```rust
use std::sync::mpsc;
use std::thread;
use std::time::Duration;

let (tx, rx) = mpsc::channel();

let precio = 100000;

println!("El precio del producto es: ${}.", precio);

thread::spawn(move || {
    let bono = 10000;
    let valor = precio - bono;
    tx.send(bono).unwrap();
    //thread::sleep(Duration::from_secs(1));
    tx.send(valor).unwrap();
});

for receptor in rx {
    println!("${}", receptor);
}
```

## Ejemplo Enviando 2 Variables de Diferentes Hilos
```rust
use std::sync::mpsc;
use std::thread;
use std::time::Duration;

let (tx, rx) = mpsc::channel();

let precio = 100000;

println!("El precio del producto es: ${}.", precio);

let tx1 = tx.clone();
thread::spawn(move || {
    let iva = 19000;
    tx1.send(iva).unwrap();
    //thread::sleep(Duration::from_secs(1));
});

thread::spawn(move || {
    let bono = 10000;
    let valor = precio + 19000 - bono;
    tx.send(bono).unwrap();
    //thread::sleep(Duration::from_secs(1));
    tx.send(valor).unwrap();
});

for receptor in rx {
    println!("${}", receptor);
}
```

## Ejemplo Enviando Variables Entre Nuevos Hilos
```rust
use std::sync::mpsc;
use std::thread;
use std::time::Duration;

let (tx, rx) = mpsc::channel();
let (tx2, rx2) = mpsc::channel();

let precio = 100000;

println!("El precio del producto es: ${}.", precio);

thread::spawn(move || {
    let iva = 19000;
    tx2.send(iva).unwrap();
    //thread::sleep(Duration::from_secs(1));
});

thread::spawn(move || {
    let bono = 10000;
    let impuesto = rx2.recv().unwrap();
    let valor = precio + impuesto - bono;
    tx.send(impuesto).unwrap();
    tx.send(bono).unwrap();
    //thread::sleep(Duration::from_secs(1));
    tx.send(valor).unwrap();
});

for receptor in rx {
    println!("${}", receptor);
}
```