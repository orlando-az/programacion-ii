# Matrices — Día 2: operaciones sobre filas, columnas y elementos

En la clase anterior se aprendió a declarar matrices, recorrerlas con el doble `for`, calcular sumas por fila, consultar columnas fijas, filtrar con condiciones y encontrar el máximo entre filas. Hoy se aplicarán operaciones que ya se conocen de arreglos — separar grupos, suma acumulada, contar sobre el promedio y construir arreglos a partir de la matriz — pero ahora sobre una estructura de dos dimensiones.

---

## 🎯 ¿Qué se trabajará hoy?

- Separar todos los elementos de una matriz en dos grupos.
- Mostrar la suma acumulada paso a paso dentro de cada fila.
- Calcular el promedio general y contar cuántos elementos lo superan.
- Construir un arreglo con información extraída fila por fila.

---

# 📝 Ejemplos en clase

---

## Ejemplo 1 — Separar pares e impares de toda la matriz

Dada la siguiente matriz:

```csharp
int[,] numeros = {
    {  3, 8, 15,  4 },
    { 12, 7,  6, 11 },
    {  5, 2, 18,  9 }
};
```

Recorrer la matriz completa y construir dos arreglos separados: uno con todos los valores pares y otro con los impares. Mostrar ambos al final.

**Salida esperada:**

```
Pares:   8 4 12 6 2 18
Impares: 3 15 7 11 5 9
```

> 💡 Se necesitan dos pasadas. La primera cuenta cuántos pares e impares hay para saber el tamaño de cada arreglo. La segunda los distribuye. Es el mismo patrón del Ejercicio 3 de la Clase 2 de arreglos, ahora con doble `for`.

```csharp
// Tu solución aquí
```

---

## Ejemplo 2 — Suma acumulada paso a paso por fila

Dada la siguiente matriz:

```csharp
int[,] datos = {
    { 4, 7, 2, 5 },
    { 3, 8, 6, 1 },
    { 9, 2, 4, 7 }
};
```

Para cada fila mostrar cómo crece la suma columna por columna.

**Salida esperada:**

```
Fila 0 — Paso 1: 4   Paso 2: 11   Paso 3: 13   Paso 4: 18
Fila 1 — Paso 1: 3   Paso 2: 11   Paso 3: 17   Paso 4: 18
Fila 2 — Paso 1: 9   Paso 2: 11   Paso 3: 15   Paso 4: 22
```

```csharp
// Tu solución aquí
```

> 💡 La variable `suma` se reinicia en `0` al inicio de cada fila y se actualiza antes de imprimirse en cada paso — igual que con arreglos. El ciclo externo simplemente repite ese proceso para cada fila.

---

## Ejemplo 3 — Contar elementos sobre el promedio general

Dada la siguiente matriz:

```csharp
int[,] notas = {
    { 75, 88, 45, 60 },
    { 90, 55, 80, 72 },
    { 40, 95, 78, 66 }
};
```

Calcular el promedio general de toda la matriz y luego contar cuántos elementos lo superan.

**Salida esperada:**

```
Promedio general: 70.33
Elementos sobre el promedio: 7
```

```csharp
// Tu solución aquí
```

> 💡 El promedio debe estar completamente calculado antes de poder comparar cualquier elemento. Por eso se necesitan dos pasadas separadas — no es posible fusionarlas en un solo doble `for`.

---

## Ejemplo 4 — Contar pares por fila y guardar en un arreglo

Dada la siguiente matriz:

```csharp
int[,] valores = {
    {  4,  7,  2,  8, 11 },
    {  3,  6, 10,  5,  8 },
    { 14,  9,  3, 12,  7 }
};
```

Construir un arreglo donde cada posición contenga la cantidad de números pares que hay en esa fila. Mostrar ese arreglo al final.

**Salida esperada:**

```
Fila 0: 3 pares
Fila 1: 3 pares
Fila 2: 2 pares
Arreglo resultado: 3 3 2
```

```csharp
// Tu solución aquí
```

> 💡 El arreglo resultado tiene el mismo tamaño que la cantidad de filas. Cada posición `i` del arreglo corresponde a la fila `i` de la matriz. Este patrón — extraer un dato por fila y guardarlo en un arreglo — aparece en varios de los ejercicios propuestos.

---

# 🔰 Ejercicios propuestos

---

## Ejercicio 1

Dada la siguiente matriz de registros de altitud en cuatro ciudades durante cuatro semanas:

```csharp
int[,] alturas = {
    { 1200,  850, 1500,  920 },
    {  780, 1100,  650, 1350 },
    { 1600,  430,  980, 1250 },
    {  560, 1400,  820, 1100 }
};
```

Determinar si la suma de la mitad superior (filas 0 y 1) es mayor, menor o igual a la suma de la mitad inferior (filas 2 y 3). Mostrar ambas sumas y la diferencia entre ellas.

---

## Ejercicio 2

Dada la siguiente matriz de temperaturas (filas = días, columnas = ciudades):

```csharp
int[,] temperaturas = {
    { 22, 35, 18, 29, 31, 24 },
    { 41, 29, 33, 25, 19, 38 },
    { 15, 38, 26, 31, 42, 20 },
    { 28, 22, 40, 19, 35, 27 },
    { 33, 41, 21, 44, 28, 16 },
    { 19, 27, 36, 22, 38, 30 }
};
```

Calcular el promedio de cada ciudad (columna). Recopilar en un arreglo todos los valores de toda la matriz que superen el promedio de su ciudad. Ordenar ese arreglo de mayor a menor con burbuja. Mostrar el promedio de cada ciudad, los valores que superaron su promedio y el arreglo ordenado.

---

## Ejercicio 3

Dada la siguiente matriz de precios:

```csharp
int[,] precios = {
    { 120,  85, 200, 150 },
    { 310,  95, 175,  60 },
    { 430, 220, 310, 180 }
};
```

Pedir al usuario un precio umbral. Reemplazar todos los valores que lo superen por `0` directamente en la matriz. Mostrar la matriz antes y después, informar cuántos valores fueron reemplazados y cuál era el mayor de ellos antes del reemplazo.

---

## Ejercicio 4

Dada la siguiente matriz de ventas (filas = vendedores, columnas = meses):

```csharp
int[,] ventas = {
    { 400, 320, 510, 290 },
    { 350, 410, 300, 520 },
    { 500, 450, 470, 380 }
};
```

Para cada vendedor determinar si vendió más en la primera mitad de meses (columnas 0 y 1) o en la segunda (columnas 2 y 3). Al final indicar cuántos vendedores tuvieron mejor primera mitad y cuántos mejor segunda mitad.

---

## Ejercicio 5

Dada la siguiente matriz de calificaciones (filas = estudiantes, columnas = materias):

```csharp
int[,] calificaciones = {
    { 85, 72, 91, 68, 77 },
    { 60, 88, 74, 95, 82 },
    { 78, 65, 83, 71, 90 },
    { 92, 79, 68, 85, 73 }
};
```

Para cada estudiante calcular cuántas materias superaron su propio promedio. Construir un arreglo con esos conteos, encontrar el valor máximo de ese arreglo e indicar qué estudiante tuvo más materias sobre su promedio.

---
