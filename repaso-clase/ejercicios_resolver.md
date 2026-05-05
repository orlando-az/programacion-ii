# C# — Matrices, Struct y Archivos
· 9 ejercicios

---

## Ejercicio 1 — Ordenar filas de una matriz por su suma

Pide al usuario una matriz de 4×4. Calcula la suma de cada fila y ordénalas de menor a mayor usando burbuja (intercambiando filas completas). Muestra la matriz resultante.

```csharp
int[,] mat = new int[4, 4];
int[] sumFila = new int[4];

// 1. Llenar mat desde teclado
// 2. Calcular sumFila[i] con for interno
// 3. Burbuja: si sumFila[j] > sumFila[j+1],
//    intercambia TODA la fila j con j+1 columna a columna
// 4. Mostrar matriz ordenada
```

---

## Ejercicio 2 — Matriz de frecuencias de un arreglo

Pide 20 números enteros entre 1 y 5. Construye una matriz de 5×2 donde la columna 0 es el número (1–5) y la columna 1 es cuántas veces apareció. Muéstrala como tabla y di cuál fue el más frecuente.

```csharp
int[,] freq = new int[5, 2];
for (int i = 0; i < 5; i++)
    freq[i, 0] = i + 1; // valor

// Leer 20 números y contar en freq[i,1]
// Mostrar tabla y encontrar el más frecuente
```

---

## Ejercicio 3 — Espiral de una matriz cuadrada

Dado un entero N (3 ≤ N ≤ 5) ingresado por el usuario, llena una matriz N×N con los números del 1 al N² recorriéndola en espiral (izquierda→derecha, arriba→abajo, derecha→izquierda, abajo→arriba). Muéstrala formateada.

```csharp
int n = int.Parse(Console.ReadLine());
int[,] mat = new int[n, n];
int top = 0, bot = n - 1, left = 0, right = n - 1, num = 1;

while (num <= n * n)
{
    // fila superior: left → right
    // col derecha:   top  → bot
    // fila inferior: right → left
    // col izquierda: bot  → top
    // ajusta top++, bot--, left++, right--
}
```

---

## Ejercicio 4 — Suma de dos matrices con validación de rango

Pide el tamaño N (máx 5) y dos matrices N×N de enteros. Valida que cada valor esté entre –100 y 100; si no, vuelve a pedirlo. Calcula la suma elemento a elemento y muestra la matriz resultado.

```csharp
int n = int.Parse(Console.ReadLine());
int[,] a = new int[n, n];
int[,] b = new int[n, n];
int[,] c = new int[n, n];

// Llenar a y b validando rango [-100, 100] con do-while
// Calcular c[i,j] = a[i,j] + b[i,j]
// Mostrar c
```

---

## Ejercicio 5 — Inventario con struct: búsqueda y actualización (menú)

Define un struct `Producto` con `codigo` (int), `nombre` (string) y `stock` (int). Carga 5 productos desde teclado. Luego entra en un menú do-while: (1) buscar por código y mostrar, (2) agregar stock a un producto, (3) salir.

```csharp
struct Producto
{
    public int    codigo;
    public string nombre;
    public int    stock;
}

Producto[] inv = new Producto[5];
int op;

do
{
    // mostrar menú, leer op
    // case 1: buscar por código con for
    // case 2: buscar y sumar stock
} while (op != 3);
```

---

## Ejercicio 6 — Struct Alumno con matriz de calificaciones

Define un struct `Alumno` con `nombre` (string) y `notas` (int[,] de 3 materias × 3 parciales). Carga 4 alumnos desde teclado. Para cada alumno calcula el promedio por materia y el promedio general. Muestra quién reprobó (promedio general < 51) y quién obtuvo la nota más alta de todo el grupo.

```csharp
struct Alumno
{
    public string nombre;
    public int[,] notas; // [materia, parcial]
}

Alumno[] grupo = new Alumno[4];

// Para cada alumno:
//   grupo[i].notas = new int[3, 3];
//   Llenar, calcular promedios con for,
//   detectar reprobados y nota máxima global
```

---

## Ejercicio 7 — Registro persistente con append y conteo de líneas

El programa debe permitir agregar nombres a `registro.txt` (modo append) en cada ejecución sin borrar lo anterior. Al iniciar, lee el archivo, cuenta cuántas entradas hay y las muestra numeradas. Luego pide N nombres nuevos y los agrega.

```csharp
int total = 0;
if (File.Exists("registro.txt"))
{
    using (StreamReader sr = new StreamReader("registro.txt"))
    {
        string linea = sr.ReadLine();
        while (linea != null)
        {
            Console.WriteLine(++total + ". " + linea);
            linea = sr.ReadLine();
        }
    }
}

// Agregar nuevas entradas en modo append:
using (StreamWriter sw = new StreamWriter("registro.txt", true))
{
    // leer N y escribir N nombres
}
```

---

## Ejercicio 8 — Guardar structs en archivo con validación de datos

Usa el struct `Producto` (código, nombre, stock). Pide 5 productos validando que el stock sea ≥ 0 y el código sea único (busca duplicados antes de aceptar). Guárdalos en `productos.txt` (un campo por línea). Vuelve a leerlos, muéstralos y calcula el stock total.

```csharp
struct Producto
{
    public int    codigo;
    public string nombre;
    public int    stock;
}

Producto[] inv = new Producto[5];

// Al pedir código: verificar unicidad con for
// Al pedir stock:  do-while hasta stock >= 0
// Guardar: 3 WriteLine por producto
// Leer: 3 ReadLine por producto + parse
```

---

## Ejercicio 9 — Integrador: matriz desde archivo, estadísticas y reescritura

Lee `datos.txt` que contiene una matriz de 4×4 (cada fila en una línea, valores separados por espacio). Cárgala en un arreglo 2D. Calcula: suma, promedio, mínimo, máximo y la fila con mayor suma. Luego reescribe el archivo reemplazando cada valor negativo por 0.

```csharp
int[,] mat = new int[4, 4];

using (StreamReader sr = new StreamReader("datos.txt"))
{
    for (int i = 0; i < 4; i++)
    {
        string[] partes = sr.ReadLine().Split(' ');
        for (int j = 0; j < 4; j++)
            mat[i, j] = int.Parse(partes[j]);
    }
}

// Calcular estadísticas con doble for
// Reemplazar negativos: if (mat[i,j] < 0) mat[i,j] = 0;
// Reescribir con StreamWriter (mismo formato)
```

---
