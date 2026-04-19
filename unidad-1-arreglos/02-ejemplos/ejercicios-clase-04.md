# Ordenamiento: del "a mano" al algoritmo Burbuja

Bienvenidos a la clase de hoy. Hasta ahora se vio cómo crear arreglos, recorrerlos con `for`, modificarlos y buscar valores dentro de ellos. Hoy se dará un paso importante: se aprenderá a **ordenar un arreglo**.

Ordenar parece simple, pero no es tan fácil como aparenta. Y justamente por eso, hoy se hará algo distinto: antes de presentar un algoritmo con nombre, cada estudiante intentará **ordenar un arreglo a mano** utilizando únicamente lo que ya conoce. Así, cuando se presente el algoritmo de Burbuja, se comprenderá desde adentro y no como una receta mágica.

Comencemos.

---

## 🎯 ¿Qué se aprenderá hoy?

- Cómo ordenar un arreglo pequeño usando solo `if` e intercambios.
- Por qué ese método deja de funcionar cuando el arreglo crece.
- Cómo resolver el problema de forma **sistemática** con el algoritmo **Burbuja**.
- Cómo intercambiar dos valores usando una variable auxiliar.

---

# PARTE 1 — Ordenar un arreglo "a mano"

## El desafío

Se tiene el siguiente arreglo con **3 números**:

```csharp
int[] numeros = { 8, 3, 5 };
```

El objetivo es dejarlo ordenado de **menor a mayor**, es decir: `{ 3, 5, 8 }`.

La pregunta es: **¿cómo se lograría esto usando solamente lo que ya se conoce?** Sin ciclos, sin algoritmos complejos. Únicamente con `if` e intercambios.

Se recomienda pensar la solución un momento antes de continuar.

---

## La lógica paso a paso

Primero es importante entender una cosa: **¿qué significa intercambiar dos valores?** Si se desea poner el contenido de la posición 0 en la posición 1, y viceversa, no se puede hacer de esta forma:

```csharp
numeros[0] = numeros[1];       // ❌ se pierde el valor original de numeros[0]
numeros[1] = numeros[0];       // ❌ ahora ambos tienen el mismo valor
```

Por esa razón se necesita una **variable auxiliar** que guarde temporalmente uno de los valores:

```csharp
int temp = numeros[0];         // se guarda el valor original
numeros[0] = numeros[1];       // posición 0 recibe lo de la posición 1
numeros[1] = temp;             // posición 1 recibe lo que se guardó
```

Este patrón se utilizará **toda la vida** en programación. Es importante recordarlo: **para intercambiar dos variables, se necesita una tercera**.

---

## Ahora sí, se ordena a mano

Arreglo: `{ 8, 3, 5 }`

### Comparación 1: posiciones 0 y 1

¿Es `numeros[0]` mayor que `numeros[1]`? Sí, `8 > 3`. Se intercambian.

```csharp
if (numeros[0] > numeros[1])
{
    int temp = numeros[0];
    numeros[0] = numeros[1];
    numeros[1] = temp;
}
```

Arreglo ahora: `{ 3, 8, 5 }`

### Comparación 2: posiciones 1 y 2

¿Es `numeros[1]` mayor que `numeros[2]`? Sí, `8 > 5`. Se intercambian.

```csharp
if (numeros[1] > numeros[2])
{
    int temp = numeros[1];
    numeros[1] = numeros[2];
    numeros[2] = temp;
}
```

Arreglo ahora: `{ 3, 5, 8 }`

### ¿Se terminó?

No tan rápido. Observe que cuando el 8 se movió a la última posición, quedó bien, pero... ¿el arreglo está totalmente ordenado? Sí, por suerte. Veamos un caso donde **no** alcanzan dos comparaciones.

### Probemos con `{ 5, 8, 3 }`

Arreglo inicial: `{ 5, 8, 3 }`

**Comparación 1:** `numeros[0] > numeros[1]`? `5 > 8`? No. Queda igual.
Arreglo: `{ 5, 8, 3 }`

**Comparación 2:** `numeros[1] > numeros[2]`? `8 > 3`? Sí. Se intercambian.
Arreglo: `{ 5, 3, 8 }`

¿Terminó el proceso? **No.** El 5 y el 3 todavía están mal. Se necesita **otra comparación más**:

**Comparación 3:** `numeros[0] > numeros[1]`? `5 > 3`? Sí. Se intercambian.
Arreglo: `{ 3, 5, 8 }` ✅

Ahora sí.

### 🔑 La conclusión de este ejemplo

Para ordenar 3 elementos no alcanza con **2 comparaciones**. Se necesitan **varias pasadas** hasta que todo quede en su lugar. En el peor caso, para 3 elementos se necesitan hasta **3 comparaciones**.

## Código completo ordenando a mano 3 elementos

```csharp
int[] numeros = { 5, 8, 3 };

Console.WriteLine($"Antes: {string.Join(" ", numeros)}");

// Primera pasada
if (numeros[0] > numeros[1])
{
    int temp = numeros[0];
    numeros[0] = numeros[1];
    numeros[1] = temp;
}

if (numeros[1] > numeros[2])
{
    int temp = numeros[1];
    numeros[1] = numeros[2];
    numeros[2] = temp;
}

// Segunda pasada (por si quedó algún desorden)
if (numeros[0] > numeros[1])
{
    int temp = numeros[0];
    numeros[0] = numeros[1];
    numeros[1] = temp;
}

Console.WriteLine($"Después: {string.Join(" ", numeros)}");
```

---

## 🧩 Mini-desafío: ordenar 5 elementos a mano

El siguiente desafío consiste en ordenar este arreglo usando **solo `if` e intercambios**, sin ciclos:

```csharp
int[] numeros = { 5, 2, 8, 1, 4 };
```

Se recomienda tomarse 10 minutos. Anotar cuántos bloques `if` se necesitaron escribir.

... ... ...

### ¿Cómo resultó?

Si se hizo correctamente, probablemente se escribieron entre **8 y 12 bloques `if`**. Cada uno comparando dos posiciones vecinas.

Ahora una reflexión importante:

- ¿Y si el arreglo tuviera **10 elementos**? ¿Cuántos `if` serían necesarios?
- ¿Y con **100 elementos**?
- ¿Y con **1000**?

Imposible. Nadie va a escribir mil `if`.

---

## 💡 La observación clave

Observe detenidamente lo que se estaba haciendo una y otra vez:

```csharp
if (numeros[X] > numeros[Y])
{
    int temp = numeros[X];
    numeros[X] = numeros[Y];
    numeros[Y] = temp;
}
```

**Se repitió el mismo patrón muchas veces**, cambiando solo los índices.

Y cuando en programación se repite un patrón muchas veces... ¿qué se utiliza?

> **Un ciclo.** 🎯

Eso es exactamente lo que hace el algoritmo de **Burbuja**: automatizar con ciclos lo que se acaba de hacer a mano.

---

# PARTE 2 — Ordenamiento Burbuja

## ¿Por qué se llama "burbuja"?

Porque los elementos más grandes del arreglo van "subiendo" hacia el final, como burbujas de aire que suben en un vaso de agua. En el ejemplo se verá cómo el número más grande "burbujea" hasta la última posición en cada pasada.

## La idea (es la misma que se hizo a mano)

Comparar **pares de elementos vecinos** y, si están en el orden incorrecto, intercambiarlos. Repetir el proceso varias pasadas hasta que el arreglo quede ordenado.

## Ejemplo con el mismo arreglo: `{ 5, 2, 8, 1, 4 }`

### Primera pasada

| Paso | Comparación | Acción                      | Arreglo resultante  |
| ---- | ----------- | --------------------------- | ------------------- |
| 1    | `5 vs 2`    | 5 es mayor, se intercambian | `{ 2, 5, 8, 1, 4 }` |
| 2    | `5 vs 8`    | 5 es menor, queda igual     | `{ 2, 5, 8, 1, 4 }` |
| 3    | `8 vs 1`    | 8 es mayor, se intercambian | `{ 2, 5, 1, 8, 4 }` |
| 4    | `8 vs 4`    | 8 es mayor, se intercambian | `{ 2, 5, 1, 4, 8 }` |

👉 Observe cómo el **8 "burbujeó"** hasta el final. Esa es la clave del algoritmo.

### Segunda pasada

| Paso | Comparación | Acción                      | Arreglo resultante  |
| ---- | ----------- | --------------------------- | ------------------- |
| 1    | `2 vs 5`    | 2 es menor, queda igual     | `{ 2, 5, 1, 4, 8 }` |
| 2    | `5 vs 1`    | 5 es mayor, se intercambian | `{ 2, 1, 5, 4, 8 }` |
| 3    | `5 vs 4`    | 5 es mayor, se intercambian | `{ 2, 1, 4, 5, 8 }` |

Ahora el 5 también quedó en su posición final. Por eso **en cada pasada se hace una comparación menos**: los últimos ya están ordenados.

### Tercera pasada

| Paso | Comparación | Acción                      | Arreglo resultante  |
| ---- | ----------- | --------------------------- | ------------------- |
| 1    | `2 vs 1`    | 2 es mayor, se intercambian | `{ 1, 2, 4, 5, 8 }` |
| 2    | `2 vs 4`    | 2 es menor, queda igual     | `{ 1, 2, 4, 5, 8 }` |

### Cuarta pasada

| Paso | Comparación | Acción                  | Arreglo resultante  |
| ---- | ----------- | ----------------------- | ------------------- |
| 1    | `1 vs 2`    | 1 es menor, queda igual | `{ 1, 2, 4, 5, 8 }` |

Arreglo ordenado. 🎉

### Aspectos importantes a notar

- Para un arreglo de **N elementos**, se necesitan hasta **N - 1 pasadas**.
- En cada pasada, el mayor elemento del pedazo "no ordenado" va a parar al final.
- Por esa razón, en cada pasada se puede hacer **una comparación menos** que en la anterior.

---

## El código de Burbuja

```csharp
int[] numeros = { 5, 2, 8, 1, 4 };

for (int i = 0; i < numeros.Length - 1; i++)
{
    for (int j = 0; j < numeros.Length - 1 - i; j++)
    {
        if (numeros[j] > numeros[j + 1])
        {
            // intercambio con variable auxiliar
            int temp = numeros[j];
            numeros[j] = numeros[j + 1];
            numeros[j + 1] = temp;
        }
    }
}

Console.WriteLine("Arreglo ordenado:");
Console.WriteLine(string.Join(", ", numeros));
```

## Comparación con el trabajo hecho a mano

Observe bien el `if` del código:

```csharp
if (numeros[j] > numeros[j + 1])
{
    int temp = numeros[j];
    numeros[j] = numeros[j + 1];
    numeros[j + 1] = temp;
}
```

**Es el mismo `if` que se escribió a mano.** La única diferencia es que ahora `j` es una variable que cambia dentro de un ciclo. Antes se escribía `numeros[0] > numeros[1]`, después `numeros[1] > numeros[2]`, y así sucesivamente. Ahora el ciclo se encarga de todo eso.

## Análisis de los dos ciclos

Este es el primer algoritmo que utiliza **dos ciclos `for` anidados**. Es importante prestar atención:

- El **`for` externo (`i`)** controla las pasadas. Va desde 0 hasta `Length - 2`. Es decir: **N - 1 pasadas**.
- El **`for` interno (`j`)** hace las comparaciones dentro de cada pasada. Va hasta `Length - 1 - i` porque en cada pasada hay una comparación menos (el final ya está ordenado).

Con el arreglo `{ 5, 2, 8, 1, 4 }` (5 elementos):

- Pasada 1 (`i = 0`): `j` va de 0 a 3 → 4 comparaciones.
- Pasada 2 (`i = 1`): `j` va de 0 a 2 → 3 comparaciones.
- Pasada 3 (`i = 2`): `j` va de 0 a 1 → 2 comparaciones.
- Pasada 4 (`i = 3`): `j` va de 0 a 0 → 1 comparación.

**Total: 10 comparaciones** para ordenar 5 elementos. Es exactamente lo mismo que se hizo a mano, pero escrito en 5 líneas en vez de 40.

## ¿Y para ordenar de mayor a menor?

Solamente se cambia el `>` por `<` en la comparación:

```csharp
if (numeros[j] < numeros[j + 1])  // orden descendente
```

Así de simple.

---

## 🔰 Ejercicios para practicar

### Ejercicio 1 — Ordenar de menor a mayor `Simple`

Dado el siguiente arreglo:

```csharp
int[] numeros = { 7, 3, 9, 1, 5, 8, 2 };
```

Implementar el algoritmo de burbuja para ordenarlo de menor a mayor. Mostrar el arreglo antes y después.

**Salida esperada:**

```
Antes:    7 3 9 1 5 8 2
Después:  1 2 3 5 7 8 9
```

```csharp
// Solución aquí
```

---

### Ejercicio 2 — Ordenar de mayor a menor `Simple`

Dado el siguiente arreglo:

```csharp
int[] numeros = { 14, 22, 5, 38, 17, 9 };
```

Ordenarlo de mayor a menor con burbuja.

**Salida esperada:**

```
Antes:    14 22 5 38 17 9
Después:  38 22 17 14 9 5
```

```csharp
// Solución aquí
```

---

### Ejercicio 3 — Ordenar nombres por su primera letra `Medio`

Dado el siguiente arreglo:

```csharp
string[] nombres = { "Carlos", "Ana", "Pedro", "Luis", "Bruno", "Sofía" };
```

Ordenar los nombres alfabéticamente comparando **solamente la primera letra** de cada nombre.

> 💡 **Pista:** para acceder a la primera letra de un string se usa la posición `[0]`. Por ejemplo, `"Carlos"[0]` devuelve el carácter `'C'`. Los caracteres se pueden comparar directamente con `<` y `>` porque C# los compara por su valor Unicode (`'A' < 'B' < 'C'...`).

**Salida esperada:**

```
Antes:    Carlos Ana Pedro Luis Bruno Sofía
Después:  Ana Bruno Carlos Luis Pedro Sofía
```

```csharp
// Solución aquí
```

---

### Ejercicio 4 — Ordenar por longitud `Medio`

Dado el siguiente arreglo:

```csharp
string[] nombres = { "Alejandro", "Ana", "Luis", "Valentina", "Omar", "Ed" };
```

Ordenar los nombres según su **longitud**, de menor a mayor cantidad de letras.

**Salida esperada:**

```
Ordenados por longitud: Ed, Ana, Luis, Omar, Alejandro, Valentina
```

```csharp
// Solución aquí
```

---

### Ejercicio 5 — Contar intercambios `Medio`

Dado el siguiente arreglo:

```csharp
int[] numeros = { 8, 3, 1, 7, 5, 2, 6, 4 };
```

Implementar burbuja, pero llevando la cuenta de **cuántos intercambios** se hicieron durante todo el proceso. Mostrar el arreglo ordenado y el total de intercambios.

**Salida esperada:**

```
Arreglo ordenado: 1 2 3 4 5 6 7 8
Intercambios realizados: 15
```

```csharp
// Solución aquí
```

---

### Ejercicio 6 — Ordenar solo la primera mitad `Avanzado`

Dado el siguiente arreglo:

```csharp
int[] numeros = { 9, 4, 7, 1, 8, 3, 6, 2 };
```

Ordenar **solamente la primera mitad** del arreglo (las primeras 4 posiciones), de menor a mayor. La segunda mitad debe quedar exactamente como estaba.

**Salida esperada:**

```
Antes:    9 4 7 1 8 3 6 2
Después:  1 4 7 9 8 3 6 2
```

> 💡 **Pista:** los ciclos de burbuja deben recorrer solo hasta `numeros.Length / 2`, no hasta el final.

```csharp
// Solución aquí
```

---

### Ejercicio 7 — Burbuja optimizada `Avanzado`

Este ejercicio consiste en mejorar el algoritmo. Considere lo siguiente: si en una pasada completa **no se hizo ningún intercambio**, significa que el arreglo ya está ordenado y no tiene sentido seguir haciendo pasadas.

La tarea es agregar una variable booleana `huboIntercambio`. Si al terminar una pasada sigue siendo `false`, se debe salir del ciclo con `break`.

Probar con este arreglo (que ya está ordenado):

```csharp
int[] numeros = { 1, 2, 3, 4, 5, 6, 7 };
```

Mostrar cuántas pasadas se hicieron en total. Si el algoritmo funciona correctamente, debería ser **una sola pasada** y listo.

```csharp
// Solución aquí
```

---

### Ejercicio 8 — Ordenar pidiendo datos al usuario `Avanzado`

Realizar un programa que:

1. Pregunte al usuario cuántos números desea ingresar.
2. Cree un arreglo de ese tamaño.
3. Pida al usuario que ingrese los números uno por uno.
4. Muestre el arreglo original.
5. Lo ordene con burbuja.
6. Muestre el arreglo ordenado.

**Ejemplo de interacción:**

```
¿Cuántos números desea ingresar? 5
Número 1: 14
Número 2: 3
Número 3: 27
Número 4: 8
Número 5: 19

Arreglo original:  14 3 27 8 19
Arreglo ordenado:  3 8 14 19 27
```

```csharp
// Solución aquí
```

---

### Ejercicio 9 — Ordenar nombres completos alfabéticamente `Avanzado` (opcional)

Este ejercicio es un **desafío adicional** para quienes deseen profundizar. En el ejercicio 3 se ordenaron nombres comparando solo la primera letra, pero eso no funciona cuando dos nombres empiezan con la misma letra (por ejemplo "Ana" y "Andrés").

Dado el siguiente arreglo:

```csharp
string[] nombres = { "Ana", "Andrés", "Alberto", "Bruno", "Alicia", "Beatriz" };
```

Ordenar los nombres **alfabéticamente considerando todas las letras**, no solamente la primera.

> 💡 **Pista:** para comparar dos nombres completos, C# ofrece el método `string.Compare(a, b)`. Este método devuelve un número **negativo** si `a` va antes que `b` alfabéticamente, **positivo** si `a` va después, y **cero** si son iguales. Se usa dentro del `if` de burbuja de la siguiente manera: `if (string.Compare(nombres[j], nombres[j + 1]) > 0)`.

**Salida esperada:**

```
Antes:    Ana Andrés Alberto Bruno Alicia Beatriz
Después:  Alberto Alicia Ana Andrés Beatriz Bruno
```

```csharp
// Solución aquí
```

---

## ✅ Algunas soluciones

A continuación se presentan algunas soluciones para comparar con las propias. Se recomienda intentar primero antes de revisar.

### Solución Ejercicio 1

```csharp
int[] numeros = { 7, 3, 9, 1, 5, 8, 2 };

Console.WriteLine($"Antes:   {string.Join(" ", numeros)}");

for (int i = 0; i < numeros.Length - 1; i++)
{
    for (int j = 0; j < numeros.Length - 1 - i; j++)
    {
        if (numeros[j] > numeros[j + 1])
        {
            int temp = numeros[j];
            numeros[j] = numeros[j + 1];
            numeros[j + 1] = temp;
        }
    }
}

Console.WriteLine($"Después: {string.Join(" ", numeros)}");
```

---

### Solución Ejercicio 3

```csharp
string[] nombres = { "Carlos", "Ana", "Pedro", "Luis", "Bruno", "Sofía" };

Console.WriteLine($"Antes:   {string.Join(" ", nombres)}");

for (int i = 0; i < nombres.Length - 1; i++)
{
    for (int j = 0; j < nombres.Length - 1 - i; j++)
    {
        if (nombres[j][0] > nombres[j + 1][0])
        {
            string temp = nombres[j];
            nombres[j] = nombres[j + 1];
            nombres[j + 1] = temp;
        }
    }
}

Console.WriteLine($"Después: {string.Join(" ", nombres)}");
```

**Explicación:**

- La expresión `nombres[j][0]` accede al **primer carácter** del nombre en la posición `j`.
- Los caracteres se comparan directamente con `>` porque C# utiliza su valor Unicode (`'A' = 65`, `'B' = 66`, `'C' = 67`, y así sucesivamente).
- El resto del algoritmo es idéntico a burbuja con números: solo cambió qué se compara.

**Limitación conocida:** este algoritmo no diferencia entre nombres que empiezan con la misma letra (por ejemplo "Ana" y "Andrés"). Para ese caso se necesita una comparación más completa, como la que se verá en el ejercicio avanzado 9.

---

### Solución Ejercicio 5

```csharp
int[] numeros = { 8, 3, 1, 7, 5, 2, 6, 4 };
int intercambios = 0;

for (int i = 0; i < numeros.Length - 1; i++)
{
    for (int j = 0; j < numeros.Length - 1 - i; j++)
    {
        if (numeros[j] > numeros[j + 1])
        {
            int temp = numeros[j];
            numeros[j] = numeros[j + 1];
            numeros[j + 1] = temp;
            intercambios++;
        }
    }
}

Console.WriteLine($"Arreglo ordenado: {string.Join(" ", numeros)}");
Console.WriteLine($"Intercambios realizados: {intercambios}");
```

---

### Solución Ejercicio 7

```csharp
int[] numeros = { 1, 2, 3, 4, 5, 6, 7 };
int pasadas = 0;

for (int i = 0; i < numeros.Length - 1; i++)
{
    bool huboIntercambio = false;
    pasadas++;

    for (int j = 0; j < numeros.Length - 1 - i; j++)
    {
        if (numeros[j] > numeros[j + 1])
        {
            int temp = numeros[j];
            numeros[j] = numeros[j + 1];
            numeros[j + 1] = temp;
            huboIntercambio = true;
        }
    }

    if (!huboIntercambio)
        break;
}

Console.WriteLine($"Arreglo: {string.Join(" ", numeros)}");
Console.WriteLine($"Pasadas realizadas: {pasadas}");
```

---

### Solución Ejercicio 8

```csharp
Console.Write("¿Cuántos números desea ingresar? ");
int cantidad = int.Parse(Console.ReadLine());

int[] numeros = new int[cantidad];

for (int i = 0; i < cantidad; i++)
{
    Console.Write($"Número {i + 1}: ");
    numeros[i] = int.Parse(Console.ReadLine());
}

Console.WriteLine($"\nArreglo original:  {string.Join(" ", numeros)}");

// Ordenar con burbuja
for (int i = 0; i < numeros.Length - 1; i++)
{
    for (int j = 0; j < numeros.Length - 1 - i; j++)
    {
        if (numeros[j] > numeros[j + 1])
        {
            int temp = numeros[j];
            numeros[j] = numeros[j + 1];
            numeros[j + 1] = temp;
        }
    }
}

Console.WriteLine($"Arreglo ordenado:  {string.Join(" ", numeros)}");
```

---

### Solución Ejercicio 9 (opcional)

Para comparar nombres completos de forma alfabética, se utiliza el método `string.Compare(a, b)` dentro del `if` del algoritmo de burbuja. Este método se encarga internamente de recorrer los caracteres y determinar cuál nombre va antes.

```csharp
string[] nombres = { "Ana", "Andrés", "Alberto", "Bruno", "Alicia", "Beatriz" };

Console.WriteLine($"Antes:   {string.Join(" ", nombres)}");

for (int i = 0; i < nombres.Length - 1; i++)
{
    for (int j = 0; j < nombres.Length - 1 - i; j++)
    {
        if (string.Compare(nombres[j], nombres[j + 1]) > 0)
        {
            string temp = nombres[j];
            nombres[j] = nombres[j + 1];
            nombres[j + 1] = temp;
        }
    }
}

Console.WriteLine($"Después: {string.Join(" ", nombres)}");
```

**Explicación de la lógica:**

- `string.Compare(a, b)` devuelve un valor numérico que indica el orden alfabético:
  - **Negativo** si `a` va antes que `b`
  - **Cero** si son iguales
  - **Positivo** si `a` va después que `b`
- En el `if` se usa `> 0` porque significa que `nombres[j]` va después que `nombres[j + 1]`, y por lo tanto hay que intercambiarlos.
- El método se encarga automáticamente de los casos especiales como nombres con prefijo común (por ejemplo, "Ana" antes que "Andrés").

**Dato técnico:** por dentro, `string.Compare` recorre los caracteres de ambos strings hasta encontrar una diferencia, exactamente como se haría a mano con un tercer ciclo. La ventaja es que evita escribir ese código repetitivo y lo deja más legible.

---
