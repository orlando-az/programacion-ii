# Ordenamiento por Inserción

En las clases anteriores se aprendieron dos algoritmos de ordenamiento: **Burbuja** (comparar vecinos e intercambiar) y **Selección** (buscar el menor y colocarlo). Hoy se completará el conjunto con un tercer método: el **ordenamiento por Inserción**.

Este algoritmo se inspira en algo que todos hacen de forma natural: **ordenar cartas en la mano**. Cuando se recibe una carta nueva, no se reordena todo el mazo; simplemente se la desliza hasta la posición correcta entre las que ya están ordenadas.

---

## 🎯 ¿Qué se aprenderá hoy?

- La lógica del algoritmo de **Inserción** paso a paso.
- Cómo se diferencia de Burbuja y Selección.
- Cómo implementarlo en C# con dos ciclos.
- Por qué es especialmente eficiente cuando el arreglo ya está casi ordenado.

---

# PARTE 1 — La idea detrás de Inserción

## La analogía de las cartas

Imagine que se tienen cartas en la mano, ordenadas de menor a mayor. Se recibe una nueva carta. ¿Qué se hace?

1. Se la compara con las cartas que ya se tienen, de derecha a izquierda.
2. Se desplazan hacia la derecha las cartas que sean **mayores** que la nueva.
3. Cuando se encuentra una carta menor (o se llega al inicio), se inserta la nueva carta en ese hueco.

Eso es exactamente lo que hace el algoritmo: se toma cada elemento del arreglo (uno por uno, de izquierda a derecha) y se lo **inserta** en la posición correcta dentro del segmento que ya está ordenado.

---

## Ejemplo con `{ 5, 2, 8, 1, 4 }`

Al inicio, se considera que el primer elemento (`5`) ya está "ordenado" por sí solo. El proceso comienza desde la posición 1.

### Pasada 1: insertar el `2`

Se toma el valor `2` (posición 1). Se compara con los elementos a su izquierda.

- ¿`5 > 2`? Sí. Se desplaza el `5` una posición a la derecha.
- Se llegó al inicio. Se inserta el `2` en la posición 0.

| Antes               | Acción                      | Después             |
| ------------------- | --------------------------- | ------------------- |
| `{ 5, 2, 8, 1, 4 }` | El 2 se inserta antes del 5 | `{ 2, 5, 8, 1, 4 }` |

Segmento ordenado: `{ 2, 5 }`

### Pasada 2: insertar el `8`

Se toma el valor `8` (posición 2). Se compara con los elementos a su izquierda.

- ¿`5 > 8`? No. El `8` ya está en su lugar correcto.

| Antes               | Acción                    | Después             |
| ------------------- | ------------------------- | ------------------- |
| `{ 2, 5, 8, 1, 4 }` | El 8 ya está bien ubicado | `{ 2, 5, 8, 1, 4 }` |

Segmento ordenado: `{ 2, 5, 8 }`

### Pasada 3: insertar el `1`

Se toma el valor `1` (posición 3). Se compara con los elementos a su izquierda.

- ¿`8 > 1`? Sí. Se desplaza el `8` a la derecha.
- ¿`5 > 1`? Sí. Se desplaza el `5` a la derecha.
- ¿`2 > 1`? Sí. Se desplaza el `2` a la derecha.
- Se llegó al inicio. Se inserta el `1` en la posición 0.

| Antes               | Acción                    | Después             |
| ------------------- | ------------------------- | ------------------- |
| `{ 2, 5, 8, 1, 4 }` | El 1 se inserta al inicio | `{ 1, 2, 5, 8, 4 }` |

Segmento ordenado: `{ 1, 2, 5, 8 }`

### Pasada 4: insertar el `4`

Se toma el valor `4` (posición 4). Se compara con los elementos a su izquierda.

- ¿`8 > 4`? Sí. Se desplaza el `8` a la derecha.
- ¿`5 > 4`? Sí. Se desplaza el `5` a la derecha.
- ¿`2 > 4`? No. Se inserta el `4` en la posición 2.

| Antes               | Acción                            | Después             |
| ------------------- | --------------------------------- | ------------------- |
| `{ 1, 2, 5, 8, 4 }` | El 4 se inserta entre el 2 y el 5 | `{ 1, 2, 4, 5, 8 }` |

Arreglo ordenado. 🎉

---

## 🔑 Aspectos importantes a notar

- No se hacen intercambios como en Burbuja o Selección. En su lugar, se hacen **desplazamientos**: los elementos mayores se mueven una posición a la derecha para "hacer espacio".
- Se necesita una variable (`valorActual`) para guardar temporalmente el valor que se está insertando, porque se sobrescribirá durante los desplazamientos.
- Si el arreglo ya está ordenado, el ciclo interno **no se ejecuta** en ninguna pasada, lo que hace al algoritmo muy rápido en ese caso.

---

# PARTE 2 — El código de Inserción

```csharp
int[] numeros = { 5, 2, 8, 1, 4 };

Console.WriteLine($"Antes:   {string.Join(" ", numeros)}");

for (int i = 1; i < numeros.Length; i++)
{
    int valorActual = numeros[i];
    int j = i - 1;

    while (j >= 0 && numeros[j] > valorActual)
    {
        numeros[j + 1] = numeros[j];   // desplazar a la derecha
        j--;
    }

    numeros[j + 1] = valorActual;       // insertar en su lugar
}

Console.WriteLine($"Después: {string.Join(" ", numeros)}");
```

---

## Análisis del código paso a paso

### El ciclo externo

```csharp
for (int i = 1; i < numeros.Length; i++)
```

Se empieza desde la posición **1** (no desde 0), porque el primer elemento ya está "ordenado" por sí solo. En cada iteración, `i` indica cuál es el elemento que se va a insertar.

### Guardar el valor actual

```csharp
int valorActual = numeros[i];
int j = i - 1;
```

Se guarda el valor que se desea insertar en `valorActual`. La variable `j` apunta al último elemento del segmento ya ordenado (la posición inmediatamente anterior a `i`).

### El ciclo interno (desplazamiento)

```csharp
while (j >= 0 && numeros[j] > valorActual)
{
    numeros[j + 1] = numeros[j];
    j--;
}
```

Este `while` recorre el segmento ordenado **de derecha a izquierda**. Mientras el elemento en `j` sea mayor que `valorActual`, lo desplaza una posición a la derecha. El ciclo se detiene cuando:

- Se encuentra un elemento menor o igual a `valorActual`, o
- Se llega al inicio del arreglo (`j < 0`).

**Nota importante:** aquí se utiliza un `while` en lugar de un `for` porque no se sabe de antemano cuántas posiciones se retrocederá. El `while` es ideal cuando la condición de parada depende de los datos.

### La inserción

```csharp
numeros[j + 1] = valorActual;
```

Cuando el `while` termina, `j + 1` es la posición correcta para el valor que se está insertando. Se coloca ahí.

---

## ¿Por qué se usa `while` y no `for`?

Hasta ahora, todos los algoritmos de ordenamiento vistos usaron `for` en ambos ciclos. Inserción utiliza un `while` en el ciclo interno porque la cantidad de desplazamientos **no se conoce de antemano**: puede ser cero (si el elemento ya está en su lugar), uno, o hasta `i` desplazamientos (si el elemento es el menor de todos).

El `while` permite expresar esta lógica de forma más clara: "mientras haya elementos mayores a mi izquierda, seguir desplazando".

---

## ¿Y para ordenar de mayor a menor?

Se cambia `>` por `<` en la condición del `while`:

```csharp
while (j >= 0 && numeros[j] < valorActual)  // orden descendente
```

---

## Comparación de los tres algoritmos

| Aspecto           | Burbuja                       | Selección                          | Inserción                            |
| ----------------- | ----------------------------- | ---------------------------------- | ------------------------------------ |
| ¿Qué hace?        | Compara e intercambia vecinos | Busca el menor y lo coloca         | Inserta cada elemento en su posición |
| Intercambios      | Muchos                        | Máximo N - 1                       | Usa desplazamientos, no intercambios |
| Mejor caso        | Con optimización: 1 pasada    | Siempre hace todas las pasadas     | Muy rápido (casi no desplaza)        |
| ¿Cuándo conviene? | Arreglos casi ordenados       | Cuando importan pocos intercambios | Arreglos pequeños o casi ordenados   |

Los tres algoritmos son **cuadráticos** (su tiempo crece proporcionalmente al cuadrado del tamaño del arreglo), lo que significa que ninguno es ideal para arreglos muy grandes. Sin embargo, para los tamaños que se manejan en este curso, los tres funcionan bien y cada uno enseña un enfoque diferente de resolución.

---

## 🔰 Ejercicios para practicar

### Ejercicio 1 — Ordenar de menor a mayor con Inserción `Simple`

Dado el siguiente arreglo:

```csharp
int[] numeros = { 15, 3, 9, 22, 7, 1 };
```

Implementar el algoritmo de Inserción para ordenarlo de menor a mayor. Mostrar el arreglo antes y después.

**Salida esperada:**

```
Antes:    15 3 9 22 7 1
Después:  1 3 7 9 15 22
```

```csharp
// Solución aquí
```

---

### Ejercicio 2 — Ordenar por criterio elegido por el usuario `Avanzado`

Dado el siguiente arreglo de nombres:

```csharp
string[] nombres = { "Valentina", "Ed", "Omar", "Ana", "Alejandro", "Luis", "Beatriz" };
```

Realizar un programa que pregunte al usuario cómo desea ordenar los nombres:

1. **Alfabéticamente** (usando `string.Compare`)
2. **Por longitud** (del más corto al más largo)
3. **Por longitud invertida** (del más largo al más corto)

Según la opción elegida, ordenar el arreglo con **Inserción** y mostrar el resultado. Si el usuario ingresa una opción inválida, mostrar un mensaje de error y no ordenar.

**Ejemplo de interacción:**

```
Nombres: Valentina Ed Omar Ana Alejandro Luis Beatriz

¿Cómo desea ordenar?
  1. Alfabéticamente
  2. Por longitud (corto a largo)
  3. Por longitud (largo a corto)
Opción: 2

Resultado: Ed Ana Omar Luis Beatriz Valentina Alejandro
```

> 💡 **Pista:** la variable `valorActual` debe ser `string`. Lo que cambia según la opción es la **condición** dentro del `while`. Para la opción 1 se compara con `string.Compare`. Para las opciones 2 y 3 se compara `.Length` con `<` o `>`.

```csharp
// Solución aquí
```

---

### Ejercicio 3 — Separar negativos y positivos, ordenar e intercalar `Avanzado`

Realizar un programa que:

1. Pida al usuario cuántos números desea ingresar (pueden ser positivos, negativos o cero).
2. Cree un arreglo de ese tamaño y pida los números uno por uno.
3. Separe los **negativos** y los **positivos** en dos arreglos auxiliares. Los ceros se consideran positivos.
4. Ordene los negativos de **menor a mayor** con Inserción (por ejemplo: -20, -8, -3).
5. Ordene los positivos de **menor a mayor** con Inserción (por ejemplo: 1, 5, 12).
6. Construya un arreglo final **intercalando** un negativo y un positivo alternadamente: negativo, positivo, negativo, positivo... Si un grupo se agota antes que el otro, los elementos restantes se agregan al final.
7. Muestre el arreglo original, ambos grupos ordenados, y el arreglo intercalado final.

**Ejemplo de interacción:**

```
¿Cuántos números desea ingresar? 8
Número 1: 5
Número 2: -3
Número 3: 12
Número 4: -20
Número 5: 1
Número 6: -8
Número 7: 0
Número 8: 7

Arreglo original:  5 -3 12 -20 1 -8 0 7
Negativos ordenados: -20 -8 -3
Positivos ordenados: 0 1 5 7 12
Resultado intercalado: -20 0 -8 1 -3 5 7 12
```

> 💡 **Pista:** para la intercalación se necesitan dos índices (uno para negativos y otro para positivos) y un ciclo que vaya alternando. Cuando uno de los grupos se termina, se copian los restantes del otro grupo al final del arreglo resultado.

```csharp
// Solución aquí
```

---
