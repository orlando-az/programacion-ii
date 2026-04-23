# Ordenamiento por Selección

Hasta ahora se aprendió a ordenar un arreglo con el algoritmo de **Burbuja**, que funciona comparando e intercambiando elementos vecinos en varias pasadas. Hoy se conocerá otro enfoque: el **ordenamiento por Selección**.

La idea de Selección es diferente y, en cierto sentido, más intuitiva: en lugar de ir "burbujeando" elementos, se **busca el menor** de todo el arreglo y se lo coloca directamente en su posición final. Luego se busca el siguiente menor, y así sucesivamente.

---

## 🎯 ¿Qué se aprenderá hoy?

- La lógica del algoritmo de **Selección** paso a paso.
- Cómo se diferencia de Burbuja.
- Cómo implementarlo en C# con dos ciclos `for`.
- Cuántos intercambios realiza en comparación con Burbuja.

---

# PARTE 1 — La idea detrás de Selección

## Pensando "a mano"

Imagine que se tiene un arreglo desordenado y se desea ordenarlo de menor a mayor. ¿Qué haría una persona de forma natural?

1. Mirar **todo** el arreglo y encontrar el número más pequeño.
2. Ponerlo en la **primera posición**.
3. Mirar el resto del arreglo (desde la posición 1 en adelante) y encontrar el siguiente más pequeño.
4. Ponerlo en la **segunda posición**.
5. Repetir hasta que todo esté ordenado.

Eso es exactamente lo que hace el algoritmo de **Selección**: en cada pasada, **selecciona** el menor elemento del segmento no ordenado y lo coloca en su lugar definitivo.

---

## Ejemplo con `{ 5, 2, 8, 1, 4 }`

### Pasada 1: buscar el menor de todo el arreglo

Se recorre desde la posición 0 hasta la 4. El menor es **1**, que está en la posición 3.

Se intercambia `numeros[0]` con `numeros[3]`:

| Antes               | Acción                           | Después             |
| ------------------- | -------------------------------- | ------------------- |
| `{ 5, 2, 8, 1, 4 }` | Se intercambian posiciones 0 y 3 | `{ 1, 2, 8, 5, 4 }` |

👉 El **1** ya quedó en su posición definitiva.

### Pasada 2: buscar el menor desde la posición 1

Se recorre desde la posición 1 hasta la 4. El menor es **2**, que ya está en la posición 1.

No se necesita intercambio.

| Antes               | Acción                   | Después             |
| ------------------- | ------------------------ | ------------------- |
| `{ 1, 2, 8, 5, 4 }` | El 2 ya está en su lugar | `{ 1, 2, 8, 5, 4 }` |

### Pasada 3: buscar el menor desde la posición 2

Se recorre desde la posición 2 hasta la 4. El menor es **4**, que está en la posición 4.

Se intercambia `numeros[2]` con `numeros[4]`:

| Antes               | Acción                           | Después             |
| ------------------- | -------------------------------- | ------------------- |
| `{ 1, 2, 8, 5, 4 }` | Se intercambian posiciones 2 y 4 | `{ 1, 2, 4, 5, 8 }` |

### Pasada 4: buscar el menor desde la posición 3

Se recorre desde la posición 3 hasta la 4. El menor es **5**, que ya está en la posición 3.

No se necesita intercambio. El arreglo queda ordenado. 🎉

| Resultado final     |
| ------------------- |
| `{ 1, 2, 4, 5, 8 }` |

---

## 🔑 Aspectos importantes a notar

- En cada pasada se hace **un solo intercambio** (como máximo). Esto es una diferencia importante con Burbuja, que puede hacer muchos intercambios por pasada.
- Para un arreglo de **N elementos**, se necesitan **N - 1 pasadas** (igual que Burbuja).
- En cada pasada se busca el **mínimo** del segmento no ordenado. Para eso se necesita una variable que guarde la **posición** del menor encontrado.

---

# PARTE 2 — El código de Selección

## La estructura

El algoritmo necesita dos ciclos:

- El **ciclo externo (`i`)** controla las pasadas: va desde la posición 0 hasta `Length - 2`.
- El **ciclo interno (`j`)** busca el menor elemento desde `i + 1` hasta el final del arreglo.

Además, se necesita una variable `posMinimo` que guarde **en qué posición** se encontró el menor valor.

```csharp
int[] numeros = { 5, 2, 8, 1, 4 };

Console.WriteLine($"Antes:   {string.Join(" ", numeros)}");

for (int i = 0; i < numeros.Length - 1; i++)
{
    int posMinimo = i;

    for (int j = i + 1; j < numeros.Length; j++)
    {
        if (numeros[j] < numeros[posMinimo])
        {
            posMinimo = j;
        }
    }

    // Intercambio: solo si el menor no está ya en la posición i
    if (posMinimo != i)
    {
        int temp = numeros[i];
        numeros[i] = numeros[posMinimo];
        numeros[posMinimo] = temp;
    }
}

Console.WriteLine($"Después: {string.Join(" ", numeros)}");
```

---

## Análisis del código paso a paso

### El ciclo externo

```csharp
for (int i = 0; i < numeros.Length - 1; i++)
```

La variable `i` representa la posición que se está "llenando" en esta pasada. En la pasada 0, se busca el menor de todo el arreglo para ponerlo en la posición 0. En la pasada 1, se busca el menor del resto para ponerlo en la posición 1. Y así sucesivamente.

### La variable `posMinimo`

```csharp
int posMinimo = i;
```

Al inicio de cada pasada, se **asume** que el menor está en la posición `i`. Luego el ciclo interno verifica si hay alguno más pequeño.

### El ciclo interno

```csharp
for (int j = i + 1; j < numeros.Length; j++)
{
    if (numeros[j] < numeros[posMinimo])
    {
        posMinimo = j;
    }
}
```

Este ciclo recorre las posiciones restantes. Si encuentra un valor menor que el actual mínimo, **actualiza** `posMinimo`. No intercambia nada todavía — solo busca.

### El intercambio

```csharp
if (posMinimo != i)
{
    int temp = numeros[i];
    numeros[i] = numeros[posMinimo];
    numeros[posMinimo] = temp;
}
```

Después de buscar, se hace **un único intercambio**: se pone el menor encontrado en la posición `i`. La condición `posMinimo != i` evita un intercambio innecesario cuando el menor ya estaba en su lugar.

---

## ¿Y para ordenar de mayor a menor?

Se cambia `<` por `>` en la comparación del ciclo interno, y la variable pasa a llamarse conceptualmente "posición del máximo":

```csharp
if (numeros[j] > numeros[posMinimo])  // buscar el mayor
```

---

## Burbuja vs Selección

| Aspecto                   | Burbuja                                                    | Selección                                |
| ------------------------- | ---------------------------------------------------------- | ---------------------------------------- |
| ¿Qué hace en cada pasada? | Compara e intercambia vecinos                              | Busca el menor y lo coloca               |
| Intercambios por pasada   | Muchos (potencialmente)                                    | Máximo uno                               |
| Número de comparaciones   | Similar                                                    | Similar                                  |
| ¿Cuándo conviene?         | Cuando el arreglo está casi ordenado (con la optimización) | Cuando se quieren minimizar intercambios |

Ambos algoritmos son sencillos y tienen un rendimiento similar para arreglos pequeños. La diferencia principal está en la cantidad de intercambios: Selección siempre hace **como máximo N - 1 intercambios** en total, mientras que Burbuja puede hacer muchos más.

---

## 🔰 Ejercicios para practicar

### Ejercicio 1 — Ordenar de menor a mayor con Selección `Simple`

Dado el siguiente arreglo:

```csharp
int[] numeros = { 29, 10, 14, 37, 13 };
```

Implementar el algoritmo de Selección para ordenarlo de menor a mayor. Mostrar el arreglo antes y después.

**Salida esperada:**

```
Antes:    29 10 14 37 13
Después:  10 13 14 29 37
```

```csharp
// Solución aquí
```

---

### Ejercicio 2 — Selección con datos del usuario y dirección de orden `Avanzado`

Realizar un programa que:

1. Pregunte al usuario cuántos números desea ingresar.
2. Cree un arreglo de ese tamaño.
3. Pida los números uno por uno.
4. Pregunte si desea ordenar de **menor a mayor** o de **mayor a menor**.
5. Ordene con Selección según la opción elegida.
6. Muestre el arreglo original y el ordenado.

> 💡 **Pista:** para mostrar el arreglo original después de ordenar, se necesita guardar una copia antes de modificarlo. Se puede copiar así:
>
> ```csharp
> int[] copia = new int[numeros.Length];
> for (int i = 0; i < numeros.Length; i++)
>     copia[i] = numeros[i];
> ```

**Ejemplo de interacción:**

```
¿Cuántos números desea ingresar? 5
Número 1: 14
Número 2: 3
Número 3: 27
Número 4: 8
Número 5: 19

¿Ordenar de menor a mayor (1) o de mayor a menor (2)? 1

Arreglo original:  14 3 27 8 19
Arreglo ordenado:  3 8 14 19 27
```

```csharp
// Solución aquí
```

---

### Ejercicio 3 — Pares primero, impares después, con orden personalizado `Avanzado`

Realizar un programa que:

1. Pida al usuario cuántos números desea ingresar.
2. Cree un arreglo de ese tamaño y pida los números uno por uno.
3. Pregunte en qué orden desea los **pares**: menor a mayor (1) o mayor a menor (2).
4. Pregunte en qué orden desea los **impares**: menor a mayor (1) o mayor a menor (2).
5. Separe los pares y los impares en dos arreglos auxiliares.
6. Ordene cada grupo con **Selección** según la dirección elegida por el usuario.
7. Una ambos grupos en un solo arreglo resultado: **pares primero, impares después**.
8. Muestre el arreglo original, la cantidad de pares e impares encontrados, y el arreglo resultado.

**Ejemplo de interacción:**

```
¿Cuántos números desea ingresar? 10
Número 1: 9
Número 2: 2
Número 3: 7
Número 4: 4
Número 5: 1
Número 6: 8
Número 7: 3
Número 8: 6
Número 9: 5
Número 10: 10

¿Orden de los pares? Menor a mayor (1) o Mayor a menor (2): 1
¿Orden de los impares? Menor a mayor (1) o Mayor a menor (2): 2

Arreglo original: 9 2 7 4 1 8 3 6 5 10
Pares encontrados: 5
Impares encontrados: 5
Resultado: 2 4 6 8 10 9 7 5 3 1
```

> 💡 **Pista:** este ejercicio se puede resolver en varias etapas. Primero, contar cuántos pares e impares hay para crear los arreglos auxiliares del tamaño correcto. Luego, separar los elementos. Después, aplicar Selección sobre cada grupo cambiando la comparación (`<` o `>`) según la opción del usuario. Finalmente, copiar ambos arreglos en secuencia al arreglo resultado.

```csharp
// Solución aquí
```

---
