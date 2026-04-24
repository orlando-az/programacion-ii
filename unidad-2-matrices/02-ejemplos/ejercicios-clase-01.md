# Matrices: del arreglo de una fila a la tabla de filas y columnas

Hasta ahora se trabajó con arreglos de una sola dimensión: una lista de valores, uno detrás del otro. Hoy se da el siguiente paso natural: ¿qué pasa cuando los datos no se organizan en una lista, sino en una **tabla**?

Una tabla tiene filas y columnas. Y eso es exactamente una **matriz**.

---

## 🎯 ¿Qué se aprenderá hoy?

- Qué es una matriz y cómo se diferencia de un arreglo.
- Cómo declarar e inicializar una matriz en C#.
- Cómo acceder a un elemento por su posición `[fila, columna]`.
- Cómo recorrer toda una matriz con un doble `for`.
- Cómo mostrar una matriz en forma de tabla en consola.
- Cómo calcular sumas, filtrar elementos y encontrar el máximo.

---

# PARTE 1 — ¿Qué es una matriz?

## Del arreglo a la tabla

Un arreglo de 5 números se puede imaginar como una fila:

```
Posición:   0    1    2    3    4
Valor:     10   20   30   40   50
```

Una **matriz** agrega una segunda dimensión: ahora hay filas **y** columnas.

```
           Col 0  Col 1  Col 2
Fila 0:     10     20     30
Fila 1:     40     50     60
Fila 2:     70     80     90
```

Para llegar a cualquier elemento ya no alcanza con un índice solo. Se necesitan **dos**: el número de fila y el número de columna.

Por ejemplo, el valor `60` está en la fila 1, columna 2. En C# se escribe: `matriz[1, 2]`.

---

## 📖 Concepto clave: la posición `[fila, columna]`

En C#, las matrices usan una **coma** para separar los dos índices dentro de los corchetes. El primero siempre indica la **fila**, el segundo la **columna**.

```
matriz[0, 0] → fila 0, columna 0 → primer elemento (esquina superior izquierda)
matriz[0, 2] → fila 0, columna 2 → tercer elemento de la primera fila
matriz[2, 2] → fila 2, columna 2 → último elemento (esquina inferior derecha)
```

> 💡 Una forma de recordarlo: primero se indica en qué **fila** está el dato (como el piso de un edificio) y luego en qué **columna** (como el apartamento en ese piso).

---

# PARTE 2 — Declarar e inicializar una matriz en C#

## Declaración con tamaño fijo

```csharp
int[,] matriz = new int[filas, columnas];
```

Por ejemplo, una matriz de 3 filas y 4 columnas:

```csharp
int[,] matriz = new int[3, 4];
```

Esto reserva espacio para 12 elementos (3 × 4), todos inicializados en `0` por defecto.

## Inicialización con valores directos

```csharp
int[,] matriz = {
    { 10, 20, 30 },
    { 40, 50, 60 },
    { 70, 80, 90 }
};
```

Cada fila de la tabla se escribe entre llaves `{ }`, separada por comas. La cantidad de elementos en cada fila debe ser igual.

## Acceder y modificar elementos

```csharp
int[,] notas = {
    { 85, 90, 78 },
    { 60, 72, 88 },
    { 95, 100, 91 }
};

Console.WriteLine(notas[0, 1]);   // muestra 90
Console.WriteLine(notas[2, 0]);   // muestra 95

notas[1, 2] = 99;                 // modifica el elemento en fila 1, columna 2
```

---

## 📖 GetLength: obtener filas y columnas

Con arreglos se usaba `Length` para saber el tamaño. Con matrices se usa `GetLength(dimensión)`:

```csharp
int filas    = matriz.GetLength(0);   // cantidad de filas
int columnas = matriz.GetLength(1);   // cantidad de columnas
```

El `0` representa la primera dimensión (filas) y el `1` la segunda (columnas).

---

# PARTE 3 — Recorrer una matriz con doble `for`

Con un arreglo bastaba un solo `for`. Con una matriz se necesitan **dos `for` anidados**:

- El `for` **externo** recorre las **filas**.
- El `for` **interno** recorre las **columnas** de cada fila.

```csharp
for (int i = 0; i < filas; i++)        // recorre cada fila
{
    for (int j = 0; j < columnas; j++) // recorre cada columna de esa fila
    {
        // aquí se accede a matriz[i, j]
    }
}
```

Por cada fila, el ciclo interno recorre todas sus columnas. Cuando termina, pasa a la siguiente fila y repite.

| i (fila) | j (columna) | Elemento           |
| -------- | ----------- | ------------------ |
| 0        | 0           | `matriz[0,0]` = 10 |
| 0        | 1           | `matriz[0,1]` = 20 |
| 0        | 2           | `matriz[0,2]` = 30 |
| 1        | 0           | `matriz[1,0]` = 40 |
| 1        | 1           | `matriz[1,1]` = 50 |
| ...      | ...         | ...                |

---

# 📝 Ejemplos en clase

---

## Ejemplo 1 — Declarar y mostrar una matriz

Declarar la siguiente matriz e imprimirla en consola en forma de tabla:

```csharp
int[,] numeros = {
    { 1, 2, 3 },
    { 4, 5, 6 },
    { 7, 8, 9 }
};
```

**Salida esperada:**

```
1       2       3
4       5       6
7       8       9
```
```csharp
int [,] numeros = new int [5,4];

int filas= numeros.GetLength(0);
int columnas= numeros.GetLength(1);


Console.WriteLine($"Filas:{filas}");
Console.WriteLine($"Columnas:{columnas}");
Console.WriteLine($"Matriz:{numeros.Length}");

Ejercicio 1

int [,] numeros =
{
    {1,2,3,5},
    {4,5,6,6},
    {7,8,9,7},
    {7,8,9,7},
    {7,8,9,7}
};

int filas=numeros.GetLength(0);
int columnas= numeros.GetLength(1);

for (int i = 0; i < filas; i++)
{
    for (int j = 0; j < columnas; j++)
    {
        Console.Write($"{numeros[i,j]} ");
    }
    Console.WriteLine();
}

```
---

## Ejemplo 2 — Suma de cada fila

Dada la siguiente matriz de temperaturas registradas durante 3 días en 4 ciudades:

```csharp
int[,] temperaturas = {
    { 22, 25, 19, 30 },
    { 18, 21, 16, 27 },
    { 30, 28, 24, 29 }
};
```

Calcular e imprimir la suma de temperaturas de cada día (cada fila).

**Salida esperada:**

```
Suma del dia 0: 96
Suma del dia 1: 82
Suma del dia 2: 111
```
```csharp
int [,] temperaturas =
{ //Ciudades
    {24,22,30,40}, //Dias
    {31,25,27,35},
    {41,30,25,27}
};

int filas = temperaturas.GetLength(0);
int columnas = temperaturas.GetLength(1);

for (int i = 0; i < filas; i++)
{
    int suma=0;
    for (int j = 0; j < columnas; j++)
    {
        suma= suma + temperaturas[i,j];
    }
    Console.WriteLine($"La suma de temperaturas es {suma} Dia {i}");
}
```
---

## Ejemplo 3 — Ingresar valores y mostrar la matriz

Crear una matriz de 3 filas y 3 columnas. Pedir al usuario que ingrese los 9 valores uno por uno. Al terminar, mostrar la matriz en forma de tabla.

**Ejemplo de interacción:**

```
Ingrese el valor para [0,0]: 5
Ingrese el valor para [0,1]: 3
Ingrese el valor para [0,2]: 8
...

Matriz ingresada:
5       3       8
...
```csharp

int[,] numeros = new int[3,3];

int filas= numeros.GetLength(0);
int columnas= numeros.GetLength(1);

for (int i = 0; i < filas; i++)
{
    for (int j = 0; j < columnas; j++)
    {
        Console.WriteLine($"Ingrese el valor para la posición [{i},{j}]");
        numeros[i,j]= int.Parse(Console.ReadLine());
    }
}

for (int i = 0; i < filas; i++)
{
    for (int j = 0; j < columnas; j++)
    {
        Console.Write($"{numeros[i,j]} \t");
    }
    Console.WriteLine();
}
```

---

## Ejemplo 4 — Mostrar una columna elegida por el usuario

Dada la siguiente matriz:

```csharp
int[,] ventas = {
    { 400, 320, 510 },
    { 350, 410, 300 },
    { 500, 450, 470 },
    { 290, 520, 380 }
};
```

Cada fila es un mes y cada columna es un vendedor. Pedir al usuario el número de un vendedor (columna 0, 1 o 2) y mostrar todas sus ventas mes a mes.

**Ejemplo de interacción:**

```
¿Qué vendedor desea consultar? 2
Ventas del vendedor 2:
Mes 0: 510
Mes 1: 300
Mes 2: 470
Mes 3: 380
```

---

## Ejemplo 5 — Contar elementos que cumplen una condición

Dada la siguiente matriz de notas:

```csharp
int[,] notas = {
    { 75, 88, 45, 60 },
    { 90, 55, 80, 72 },
    { 40, 95, 78, 66 }
};
```

Contar cuántas notas son menores a `60` (reprobadas) e indicar en qué posición se encuentra cada una.

**Salida esperada:**

```
Reprobado en [0,2]: 45
Reprobado en [1,1]: 55
Reprobado en [2,0]: 40
Total reprobados: 3
```

---

## Ejemplo 6 — Vendedor con mayor total de ventas

Dada la siguiente matriz de ventas:

```csharp
int[,] ventas = {
    { 400, 320, 510, 290, 480 },
    { 350, 410, 300, 520, 390 },
    { 500, 450, 470, 380, 430 }
};
```

Cada fila es un vendedor y cada columna es un mes. Calcular el total de cada vendedor y determinar cuál tuvo el mayor total.

**Salida esperada:**

```
Total vendedor 0: 2000
Total vendedor 1: 1970
Total vendedor 2: 2230
El vendedor con mayor total es el vendedor 2 con 2230.
```

---

# 🔰 Ejercicios propuestos

---

## Ejercicio 1

Dado el siguiente arreglo de precios de tres productos en cuatro tiendas distintas:

```csharp
int[,] precios = {
    {  50,  45,  60,  55 },
    {  30,  35,  28,  40 },
    {  90, 100,  85,  95 }
};
```

Mostrar todos los precios en forma de tabla.

---

## Ejercicio 2

Crear una matriz de 2 filas y 4 columnas con los valores que se desee. Mostrar cada elemento junto a su posición.

**Salida esperada (ejemplo):**

```
Posicion [0,0]: 5
Posicion [0,1]: 8
...
```

---

## Ejercicio 3

Dada la siguiente matriz:

```csharp
int[,] datos = {
    {  3,  6,  9 },
    { 12, 15, 18 },
    { 21, 24, 27 }
};
```

Mostrar únicamente los elementos de la **última columna**.

**Salida esperada:**

```
9
18
27
```

---

## Ejercicio 4

Usar la misma matriz de temperaturas del Ejemplo 2. Pedir al usuario el número de una ciudad (columna 0, 1, 2 o 3) y mostrar todas las temperaturas registradas para esa ciudad.

**Ejemplo de interacción:**

```
¿Qué ciudad desea consultar? 1
Temperaturas de la ciudad 1:
Dia 0: 25
Dia 1: 21
Dia 2: 28
```

---

## Ejercicio 5

Crear una matriz de 4 filas y 4 columnas. Pedir al usuario que ingrese los 16 valores. Luego mostrar la matriz y calcular la suma total de todos los elementos.

---

## Ejercicio 6

Dada la siguiente matriz de notas:

```csharp
int[,] notas = {
    { 75, 88, 92, 60 },
    { 55, 70, 80, 95 },
    { 90, 85, 78, 66 }
};
```

Cada fila es un estudiante con 4 notas. Calcular y mostrar el promedio de cada estudiante.

**Salida esperada:**

```
Promedio estudiante 0: 78.75
Promedio estudiante 1: 75.00
Promedio estudiante 2: 79.75
```

> 💡 Usar `double` para el resultado del promedio.

---

## Ejercicio 7

Dada la siguiente matriz:

```csharp
int[,] inventario = {
    { 10, 0, 5,  8 },
    {  0, 3, 0, 12 },
    {  7, 0, 0,  4 }
};
```

Contar cuántos elementos son iguales a `0` e indicar en qué posiciones se encuentran.

**Salida esperada:**

```
Posicion [0,1]: 0
Posicion [1,0]: 0
Posicion [1,2]: 0
Posicion [2,1]: 0
Posicion [2,2]: 0
Total de ceros: 5
```

---

## Ejercicio 8

Dada la siguiente matriz:

```csharp
int[,] cuadro = {
    {  2,  4,  6,  8 },
    { 10, 12, 14, 16 },
    { 18, 20, 22, 24 },
    { 26, 28, 30, 32 }
};
```

Calcular por separado la suma de los elementos en filas **pares** (fila 0 y fila 2) y en filas **impares** (fila 1 y fila 3). Indicar cuál de las dos sumas es mayor.

**Salida esperada:**

```
Suma de filas pares:   120
Suma de filas impares: 168
La mayor suma es la de las filas impares.
```

---

## Ejercicio 9

Dada la siguiente matriz de notas (misma del Ejercicio 6). Además del promedio de cada estudiante, identificar cuál estudiante tiene el promedio más alto y mostrarlo.

**Salida esperada:**

```
Promedio estudiante 0: 78.75
Promedio estudiante 1: 75.00
Promedio estudiante 2: 79.75
El estudiante con mayor promedio es el estudiante 2 con 79.75.
```

---

## Ejercicio 10

Dado el siguiente registro de producción de 3 máquinas durante 6 turnos:

```csharp
int[,] produccion = {
    { 120, 95, 110, 130, 100, 115 },
    {  80, 90, 105,  95, 110,  85 },
    { 140, 125, 130, 120, 135, 145 }
};
```

Cada fila es una máquina y cada columna es un turno. Se pide:

1. Calcular el total producido por cada máquina.
2. Calcular el promedio de producción por turno de cada máquina.
3. Identificar qué máquina tuvo el mayor total y mostrar su número y su total.

**Salida esperada:**

```
Maquina 0 — Total: 670  Promedio por turno: 111.67
Maquina 1 — Total: 565  Promedio por turno: 94.17
Maquina 2 — Total: 795  Promedio por turno: 132.50
La maquina con mayor produccion es la maquina 2 con 795.
```

---
