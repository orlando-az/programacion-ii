# Práctico C# — Arreglos

---

## Ejercicio 1 — Inicial y última letra `string[]`

Dado el siguiente arreglo de nombres:

```csharp
string[] nombres = { "Alejandro", "Iris", "Omar", "Valentina", "Lu", "Carlos" };
```

Recorré el arreglo y para cada nombre mostrá:

- La **inicial** en mayúscula
- La **última letra** en minúscula
- Un mensaje indicando si ambas letras son **iguales o no**

**Restricciones:**

- No usar `Substring()`, `Contains()`, `char.ToLower()` ni `char.ToUpper()`
- Podés usar `ToLower()` y `ToUpper()` sobre strings
- Accedé a los caracteres usando índices

**Ejemplo de salida:**

```
Alejandro:
  Inicial: A | Última: o | ¿Iguales? No
Iris:
  Inicial: I | Última: s | ¿Iguales? No
```

---

## Ejercicio 2 — Reemplazar nombres cortos `string[]`

Dado el siguiente arreglo de nombres:

```csharp
string[] nombres = { "Ana", "Alejandro", "Lu", "Valentina", "Ed", "Carlos", "Iris" };
```

Creá un segundo arreglo llamado `censurado` del mismo tamaño. Recorré el arreglo original y:

- Si el nombre tiene **3 letras o menos**, guardá `"***"` en el arreglo censurado
- Si tiene **más de 3 letras**, copiá el nombre tal cual

Al final mostrá ambos arreglos en una sola línea cada uno, separados por coma.

**Restricciones:**

- No modificar el arreglo original
- No usar `Substring()`, `Contains()` ni `string.Equals()`
- Podés usar `string.Join()`

**Ejemplo de salida:**

```
Original:  Ana, Alejandro, Lu, Valentina, Ed, Carlos, Iris
Censurado: ***, Alejandro, ***, Valentina, ***, Carlos, Iris
```

---

## Ejercicio 3 — Calificar notas `int[]`

Dado el siguiente arreglo de notas enteras:

```csharp
int[] notas = { 95, 83, 72, 65, 47, 88, 91 };
```

Recorré el arreglo y asigná una letra a cada nota según esta escala:
| Rango | Letra |
|-------|-------|
| 90 – 100 | A |
| 80 – 89 | B |
| 70 – 79 | C |
| 60 – 69 | D |
| 0 – 59 | F |

Mostrá cada nota con su letra correspondiente. Al final mostrá cuántas notas hay de cada letra.

**Pista:** Usá `switch` con la división entera `notas[i] / 10` para obtener la decena.

**Ejemplo de salida:**

```
Nota 95: A
Nota 83: B
...
A: 2 | B: 2 | C: 1 | D: 1 | F: 1
```

---

## Ejercicio 4 — Censurar con criterio múltiple `string[]`

Dado el siguiente arreglo de nombres:

```csharp
string[] nombres = { "Ana", "Luis", "Alejandro", "Ed", "Sofia", "Valentina", "Omar" };
```

Creá un segundo arreglo `censurado` y aplicá estas reglas según la longitud de cada nombre:

- **3 letras o menos** → reemplazar por `"***"`
- **4 o 5 letras** → mostrar solo la inicial seguida de `"****"`
- **Más de 5 letras** → mostrar el nombre completo

Mostrá ambos arreglos, uno debajo del otro, un nombre por línea.

**Restricciones:**

- No modificar el arreglo original

**Ejemplo de salida:**

```
Original:        Censurado:
  Ana              ***
  Luis             L****
  Alejandro        Alejandro
```

---

## Ejercicio 5 — Arreglo espejo `int[]`

Dado el siguiente arreglo:

```csharp
int[] arreglo = { 5, 12, 8, 9, 8, 12, 5, 3 };
```

Determiná si el arreglo es un **palíndromo**, es decir, si se lee igual de izquierda a derecha que de derecha a izquierda.

Mostrá el arreglo y luego un mensaje indicando si ES o NO ES un espejo.

**Restricciones:**

- No crear un segundo arreglo
- Solo recorrer hasta la mitad del arreglo
- Detener la búsqueda en cuanto se encuentre un par que no coincida

**Ejemplo de salida:**

```
Original: 5 12 8 9 8 12 5 3
El arreglo NO es un espejo.
```

---

## Ejercicio 6 — Promedio sin extremos `int[]`

Dado el siguiente arreglo:

```csharp
int[] numeros = { 15, 42, 8, 73, 29, 61, 37, 10 };
```

Calculá el promedio del arreglo **excluyendo el valor mayor y el valor menor**.

El programa debe:

1. Encontrar el mayor y el menor en una primera pasada
2. En una segunda pasada, sumar solo los elementos que no sean ni el mayor ni el menor
3. Calcular y mostrar el promedio con 2 decimales

Mostrá también cuáles fueron el mayor y el menor excluidos.

**Ejemplo de salida:**

```
Mayor excluido: 73
Menor excluido: 8
Promedio sin extremos: 30.80
```

---

## Ejercicio 7 — Buscar letra en nombres `string[]`

Dado el siguiente arreglo:

```csharp
string[] nombres = { "Ana", "Alejandro", "Luis", "Valentina", "Omar", "Iris", "Ed", "Carolina" };
```

Pedile al usuario que ingrese una letra. Recorré cada nombre y determiná si contiene esa letra (sin distinguir mayúsculas). Mostrá los nombres que la contienen y al final el total.

**Restricciones:**

- No usar `Contains()`
- Buscar la letra recorriendo carácter por carácter con un ciclo
- Usar `ToLower()` para ignorar mayúsculas
- En cuanto encontrés la letra en un nombre, no seguir buscando en ese mismo nombre

**Ejemplo de salida (letra = "a"):**

```
  'Ana' contiene 'a'
  'Alejandro' contiene 'a'
  ...
Total: 5 nombre(s) contienen la letra 'a'.
```

---

## Ejercicio 8 — Intersección de dos arreglos `string[]`

Dados estos dos arreglos:

```csharp
string[] arreglo1 = { "Ana", "Luis", "María", "Carlos", "Sofia" };
string[] arreglo2 = { "Pedro", "María", "Luis", "Valeria", "Omar" };
```

Mostrá los nombres que aparecen en **ambos arreglos** (intersección). La comparación no debe distinguir entre mayúsculas y minúsculas.

Si no hay nombres en común, mostrá `"Ninguno."`.

**Restricciones:**

- No usar `string.Equals()` ni `Contains()`
- Usar `ToLower()` para comparar
- Si un nombre aparece duplicado en `arreglo2`, contarlo una sola vez

**Ejemplo de salida:**

```
Nombres en ambos arreglos (intersección):
  Luis
  María
```

---

## Ejercicio 9 — Contar vocales totales `string[]`

Dado el siguiente arreglo:

```csharp
string[] nombres = { "Alejandro", "Iris", "Omar", "Valentina", "Lu" };
```

Contá cuántas vocales tiene cada nombre y mostralo. Al final mostrá el total general de vocales en todo el arreglo.

Considerá como vocales: `a e i o u á é í ó ú` (en minúscula).

**Restricciones:**

- No usar `Contains()`
- Buscar cada vocal comparando carácter por carácter con un tercer ciclo
- Usar `ToLower()` sobre el nombre antes de buscar

**Ejemplo de salida:**

```
Alejandro: 4 vocal(es)
Iris: 2 vocal(es)
...
Total de vocales en el arreglo: 15
```

---

## Ejercicio 10 — Pares e impares con estadísticas `int[]`

Pedile al usuario que ingrese la cantidad de números y luego cada número. Almacená los valores en un arreglo.

Luego calculá por separado para los números **pares** y los **impares**:

- Cantidad
- Suma
- Promedio
- El valor mayor

Si no hay números de algún grupo, mostrá un mensaje indicándolo en lugar de intentar calcular.

**Ejemplo de salida:**

```
¿Cuántos números vas a ingresar? 6
Número 1: 4
...
--- Pares ---
Cantidad: 3
Suma:     34
Promedio: 11.33
Mayor:    18

--- Impares ---
Cantidad: 3
Suma:     19
Promedio: 6.33
Mayor:    9
```

---

## Ejercicio 11 — Múltiplos de N `int[]`

Dado el siguiente arreglo:

```csharp
int[] numeros = { 9, 4, 15, 7, 6, 11, 21, 8, 18, 3 };
```

Pedile al usuario que ingrese un número **N**. Recorré el arreglo y mostrá cuáles elementos son múltiplos de N. Al final mostrá la cantidad total y la suma de esos múltiplos.

**Ejemplo de salida (N = 3):**

```
  9 es múltiplo de 3
  15 es múltiplo de 3
  ...
Cantidad: 6
Suma:     72
```

---

## Ejercicio 12 — Reemplazar negativos por el promedio `int[]`

Dado el siguiente arreglo:

```csharp
int[] numeros = { 5, -3, 8, -1, 10, -7, 4, 2 };
```

El programa debe:

1. En una **primera pasada**, calcular el promedio de los valores **no negativos** (cero y positivos)
2. En una **segunda pasada**, reemplazar cada valor negativo por ese promedio (entero)

Mostrá el arreglo antes y después, y el promedio que se usó para reemplazar.

**Ejemplo de salida:**

```
Antes:   5 -3 8 -1 10 -7 4 2
Después: 5 5 8 5 10 5 4 2
Promedio usado: 5
```

---
