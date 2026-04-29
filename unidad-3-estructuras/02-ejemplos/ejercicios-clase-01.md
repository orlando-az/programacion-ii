# Registros: struct en C#

Hasta ahora todos los arreglos guardaban un solo tipo de dato. Un arreglo de enteros guarda enteros, un arreglo de strings guarda strings. Pero en la vida real los datos no vienen solos — vienen agrupados.

Pensemos en un sistema de recursos humanos. Para cada empleado se necesita guardar su nombre, su cargo, su salario y sus años de experiencia. Con arreglos separados esos datos se desvinculan fácilmente al ordenar o filtrar. El `struct` resuelve exactamente ese problema.

---

## 🎯 ¿Qué se aprenderá hoy?

- Qué es un `struct` y por qué existe.
- Cómo declarar un `struct` con sus campos.
- Cómo crear instancias y acceder a sus campos.
- Cómo declarar e inicializar un arreglo de structs.
- Cómo recorrer, buscar y ordenar un arreglo de structs.

> ⚠️ En C# moderno el `struct` debe declararse **al final del archivo**, después de todo el código ejecutable. Si se declara antes, el compilador lanza un error.

---

# 📝 Ejemplos en clase

---

## Ejemplo 1

Declarar un struct `Empleado` con campos `nombre`, `cargo`, `salario` y `aniosExperiencia`. Crear dos instancias. Calcular el salario con bono: si tiene más de 5 años de experiencia recibe un 15% extra. Mostrar el salario original y el salario con bono de cada uno.

```csharp
// Tu solución aquí
```

---

## Ejemplo 2

Declarar un struct `Libro` con campos `titulo`, `autor`, `anioPublicacion`, `numeroPaginas` y `precio`. Crear un arreglo de 5 libros con datos definidos. Mostrarlos en tabla y calcular el precio promedio.

```csharp
// Tu solución aquí
```

---

## Ejemplo 3

Declarar un struct `Vuelo` con campos `codigo`, `origen`, `destino`, `duracionMinutos` y `precio`. Pedir al usuario que ingrese 4 vuelos. Al terminar mostrar el vuelo más barato y el de mayor duración.

```csharp
// Tu solución aquí
```

---

## Ejemplo 4

Declarar un struct `Paciente` con campos `nombre`, `edad`, `diagnostico`, `diasHospitalizado` y `costoPorDia`. Crear un arreglo de 5 pacientes con datos definidos. Pedir al usuario un nombre, buscar el paciente y mostrar todos sus datos junto al costo total de hospitalización (`diasHospitalizado × costoPorDia`).

```csharp
// Tu solución aquí
```

---

## Ejemplo 5

Declarar un struct `Vehiculo` con campos `marca`, `modelo`, `anio`, `kilometraje` y `precio`. Crear un arreglo de 5 vehículos con datos definidos. Ordenarlo de menor a mayor precio con burbuja. Después del ordenamiento mostrar solo los vehículos con kilometraje menor a 50000.

```csharp
// Tu solución aquí
```

---

# 🔰 Ejercicios propuestos

---

## Ejercicios 1 — 4: Struct `Pelicula`

Declarar un struct `Pelicula` con los campos: título (string), director (string), año (int), duración en minutos (int) y calificación (double). Crear un arreglo de 6 películas con los siguientes datos:

| Título | Director | Año | Duración (min) | Calificación |
|--------|----------|-----|----------------|--------------|
| Inception | Nolan | 2010 | 148 | 8.8 |
| El Padrino | Coppola | 1972 | 175 | 9.2 |
| Interstellar | Nolan | 2014 | 169 | 8.6 |
| Pulp Fiction | Tarantino | 1994 | 154 | 8.9 |
| El Gran Gatsby | Luhrmann | 2013 | 143 | 7.2 |
| Joker | Phillips | 2019 | 122 | 8.4 |

---

## Ejercicio 1

Mostrar todas las películas en formato tabla con sus 5 campos.

```csharp
// Tu solución aquí
```

---

## Ejercicio 2

Mostrar solo las películas con calificación mayor a un valor ingresado por el usuario. Indicar cuántas cumplen la condición.

```csharp
// Tu solución aquí
```

---

## Ejercicio 3

Calcular la duración total de todas las películas en minutos y convertirla a horas y minutos. Mostrar también el título de la película más larga y la más corta.

```csharp
// Tu solución aquí
```

---

## Ejercicio 4

Pedir al usuario un director. Mostrar todas sus películas y calcular su calificación promedio.

```csharp
// Tu solución aquí
```

---

## Ejercicios 5 — 7: Struct `Empleado`

Declarar un struct `Empleado` con los campos: nombre (string), departamento (string), salario (double), años de experiencia (int) y horas extras (int). Crear un arreglo de 5 empleados con los siguientes datos:

| Nombre | Departamento | Salario | Años Exp. | Horas Extra |
|--------|-------------|---------|-----------|-------------|
| Ana Flores | Sistemas | 3500.00 | 8 | 12 |
| Carlos Ríos | Contabilidad | 2800.00 | 3 | 5 |
| María López | Sistemas | 4200.00 | 10 | 20 |
| Pedro Vargas | Marketing | 3100.00 | 6 | 8 |
| Laura Chávez | Contabilidad | 2600.00 | 2 | 3 |

---

## Ejercicio 5

Ordenar los empleados de mayor a menor salario con burbuja. Mostrar el arreglo antes y después.

```csharp
// Tu solución aquí
```

---

## Ejercicio 6

Pedir al usuario un departamento. Mostrar todos los empleados de ese departamento y calcular el salario promedio del mismo.

```csharp
// Tu solución aquí
```

---

## Ejercicio 7

Calcular el salario total mensual de cada empleado considerando que cada hora extra se paga a 25.00. Mostrar el nombre, salario base, pago por horas extras y salario total. Al final mostrar el empleado con mayor salario total.

```csharp
// Tu solución aquí
```

---

## Ejercicios 8 — 10: Struct `Producto`

Declarar un struct `Producto` con los campos: nombre (string), categoría (string), precio (double), stock (int) y descuento en porcentaje (double). Crear un arreglo de 6 productos con los siguientes datos:

| Nombre | Categoría | Precio | Stock | Descuento (%) |
|--------|-----------|--------|-------|---------------|
| Laptop | Electronica | 1200.00 | 5 | 10.0 |
| Mouse | Electronica | 25.50 | 40 | 0.0 |
| Escritorio | Muebles | 350.00 | 8 | 15.0 |
| Silla | Muebles | 180.00 | 12 | 5.0 |
| Teclado | Electronica | 45.00 | 25 | 0.0 |
| Lampara | Muebles | 60.00 | 18 | 20.0 |

---

## Ejercicio 8

Calcular el precio final de cada producto después de aplicar su descuento (`precio - precio * descuento / 100`). Mostrar el nombre, precio original, descuento aplicado y precio final. Indicar cuál producto tiene el mayor ahorro en valor absoluto.

```csharp
// Tu solución aquí
```

---

## Ejercicio 9

Pedir al usuario una categoría. Mostrar todos los productos de esa categoría ordenados de menor a mayor precio con burbuja.

```csharp
// Tu solución aquí
```

---

## Ejercicio 10

Calcular el valor total del inventario de cada producto (`precio × stock`) y el valor total general. Identificar el producto con mayor valor en inventario y el de menor valor. Indicar si la diferencia entre ambos supera 5000.

```csharp
// Tu solución aquí
```

---

## 🔗 Repositorio del curso

El material de esta clase está disponible en:
[github.com/orlando-az/programacion-ii](https://github.com/orlando-az/programacion-ii)
