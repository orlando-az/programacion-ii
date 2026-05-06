# Archivos: persistencia de datos en C#

Hasta ahora todos los datos que se trabajaron en el programa desaparecen cuando este termina. Los arreglos y los structs viven en la memoria del computador — cuando el programa se cierra, esa memoria se libera y los datos se pierden.

Los **archivos** resuelven ese problema. Un archivo guarda los datos en el disco y permanece ahí aunque el programa termine.

---

## 🎯 ¿Qué se aprenderá hoy?

- Cómo crear y escribir un archivo de texto con `StreamWriter`.
- Cómo leer un archivo línea por línea con `StreamReader`.
- Cómo agregar contenido a un archivo existente sin borrar lo anterior (append).
- Cómo verificar si un archivo existe antes de abrirlo con `File.Exists`.
- Cómo guardar y recuperar un arreglo de structs desde un archivo.

> ⚠️ Recordar que en C# moderno el `struct` debe declararse al final del archivo, después de todo el código ejecutable.

---

# 📝 Ejemplos en clase

---

## Ejemplo 1

Pedir al usuario que ingrese 4 nombres. Guardarlos en un archivo llamado `nombres.txt`, uno por línea. Confirmar cuántas líneas se escribieron.

```csharp
StreamWriter datos = new StreamWriter("nombres.txt");
int filas=0;
for (int i = 0; i < 4; i++)
{
    Console.WriteLine("Introduzca un nombre");
    string nombre = Console.ReadLine();
    datos.WriteLine(nombre);
    filas++;
}

datos.Close();

Console.WriteLine($"Lineas escritas: {filas}");
```

---

## Ejemplo 2

Leer el archivo `nombres.txt` creado en el Ejemplo 1 y mostrar cada nombre con su número de línea. Al final mostrar cuántas líneas se leyeron.

```csharp
StreamReader lectura = new StreamReader("nombres.txt");
string linea = lectura.ReadLine()!;
int cont=1;
while(linea != null)
{
    Console.WriteLine($"Número línea: {cont} Contenido: {linea}");
    linea= lectura.ReadLine()!;
    cont++;
}

lectura.Close();
Console.WriteLine($"Líneas leídas:{cont-1}");
```

---

## Ejemplo 3

Verificar si el archivo `nombres.txt` existe. Si existe, agregar 2 nombres más al final sin borrar los anteriores. Si no existe, informarlo. Al terminar mostrar todo el contenido del archivo.

```csharp
// Tu solución aquí
```

---

## Ejemplo 4

Dado un arreglo de 3 productos (nombre, precio, stock), guardarlo en un archivo `productos.txt` con los campos separados por coma. Luego leer el archivo, reconstruir el arreglo y mostrar los datos en tabla.

```csharp
int total=3;

Producto[] productos = new Producto[total];

productos[0]= new Producto{nombre="mouse",precio=50.60,stock=10};
productos[1]= new Producto{nombre="teclado",precio=200,stock=5};
productos[2]= new Producto{nombre="monitor",precio=1200,stock=200};

StreamWriter escrito = new StreamWriter("producto.txt");

for (int i = 0; i < total; i++)
{
    escrito.WriteLine($"{productos[i].nombre},{productos[i].precio},{productos[i].stock}");
}
Console.WriteLine("Datos Guardados");
escrito.Close();

StreamReader lector = new StreamReader("producto.txt");
string linea = lector.ReadLine();
Producto[] recuperar = new Producto[total];
int pos=0;
while(linea!= null)
{
    string[] partes = linea.Split(",");

        recuperar[pos].nombre = partes[0];
        recuperar[pos].precio= double.Parse(partes[1]);
        recuperar[pos].stock= int.Parse(partes[2]);
        pos++;
        linea= lector.ReadLine();
    
}

lector.Close();

for (int i = 0; i < recuperar.Length; i++)
{
    Console.WriteLine($"{recuperar[i].nombre}, {recuperar[i].precio},{recuperar[i].stock}");
}
struct Producto
{
    public string nombre;
    public double precio;
    public int stock;
}
```

---

## Ejemplo 5

Usar el archivo `productos.txt` del Ejemplo 4. Leer y mostrar el stock actual. Pedir al usuario el nombre de un producto y el nuevo stock. Actualizar el arreglo, reescribir el archivo y mostrar el resultado final.

```csharp
int total = 3;
Producto[] recuperados = new Producto[total];

// Leer archivo
StreamReader lector = new StreamReader("productos.txt");
string linea        = lector.ReadLine();
int pos             = 0;

while (linea != null && pos < total)
{
    string[] partes         = linea.Split(',');
    recuperados[pos].nombre = partes[0];
    recuperados[pos].precio = double.Parse(partes[1]);
    recuperados[pos].stock  = int.Parse(partes[2]);
    pos++;
    linea = lector.ReadLine();
}

lector.Close();

// Mostrar stock actual
Console.WriteLine("Stock actual:");
Console.WriteLine($"{"Nombre",-15} {"Precio",-10} {"Stock"}");

for (int i = 0; i < pos; i++)
    Console.WriteLine($"{recuperados[i].nombre,-15} {recuperados[i].precio,-10:F2} {recuperados[i].stock}");

// Actualizar
Console.Write("\n¿Qué producto desea actualizar? ");
string buscar     = Console.ReadLine();
bool   encontrado = false;

for (int i = 0; i < pos; i++)
{
    if (string.Compare(recuperados[i].nombre, buscar, true) == 0)
    {
        Console.Write("¿Nuevo stock? ");
        recuperados[i].stock = int.Parse(Console.ReadLine());
        encontrado = true;
    }
}

if (!encontrado)
{
    Console.WriteLine("Producto no encontrado.");
}
else
{
    // Reescribir archivo
    StreamWriter escritor = new StreamWriter("productos.txt");

    for (int i = 0; i < pos; i++)
        escritor.WriteLine($"{recuperados[i].nombre},{recuperados[i].precio},{recuperados[i].stock}");

    escritor.Close();

    Console.WriteLine("\nStock actualizado:");
    Console.WriteLine($"{"Nombre",-15} {"Precio",-10} {"Stock"}");

    for (int i = 0; i < pos; i++)
        Console.WriteLine($"{recuperados[i].nombre,-15} {recuperados[i].precio,-10:F2} {recuperados[i].stock}");

    Console.WriteLine("\nArchivo actualizado.");
}

struct Producto
{
    public string nombre;
    public double precio;
    public int    stock;
}
```

---

# 🔰 Ejercicios propuestos

---

## Ejercicio 1

Pedir al usuario que ingrese 5 números enteros. Guardarlos en un archivo llamado `numeros.txt`, uno por línea. Luego leer el archivo, calcular la suma y el promedio de los números leídos y mostrarlos en consola.

```csharp
// Tu solución aquí
```

---

## Ejercicio 2

Crear un archivo `tareas.txt` con 3 tareas definidas directamente en el código. Luego pedir al usuario que ingrese 2 tareas adicionales y agregarlas al archivo con append. Mostrar el contenido final del archivo numerando cada tarea.

```csharp
// Tu solución aquí
```

---

## Ejercicio 3

Leer el archivo `nombres.txt` del Ejemplo 1. Contar cuántos nombres tienen más de 4 letras y mostrarlos. Si el archivo no existe mostrar un mensaje apropiado.

```csharp
// Tu solución aquí
```

---

## Ejercicio 4

Crear un archivo `notas.txt` con las siguientes calificaciones, una por línea: 85, 72, 91, 68, 77, 90, 55, 83. Leer el archivo, calcular el promedio y mostrar cuántas notas están por encima y cuántas por debajo del promedio.

```csharp
// Tu solución aquí
```

---

## Ejercicio 5

Leer el archivo `notas.txt` del Ejercicio 4. Reescribir el archivo reemplazando todas las notas menores a 60 por 60. Mostrar el archivo antes y después del cambio.

```csharp
// Tu solución aquí
```

---

## Ejercicio 6

Declarar un struct `Contacto` con campos: nombre (string), teléfono (string) y email (string). Crear un arreglo de 4 contactos con datos definidos. Guardarlos en un archivo `contactos.txt` con los campos separados por punto y coma. Mostrar el contenido del archivo al terminar.

```csharp
// Tu solución aquí
```

---

## Ejercicio 7

Leer el archivo `contactos.txt` del Ejercicio 6. Reconstruir el arreglo de structs y mostrar todos los contactos en formato tabla.

```csharp
// Tu solución aquí
```

---

## Ejercicio 8

Leer el archivo `contactos.txt` del Ejercicio 6. Pedir al usuario un nombre y buscar si existe entre los contactos leídos. Si se encuentra mostrar su teléfono y email. Si no, informarlo.

```csharp
// Tu solución aquí
```

---

## Ejercicio 9

Declarar un struct `Venta` con campos: fecha (string), producto (string), cantidad (int) y precioUnitario (double). Crear un arreglo de 5 ventas con datos definidos. Guardarlas en `ventas.txt`. Luego leer el archivo, calcular el total de cada venta (`cantidad × precioUnitario`) y mostrar la venta con mayor total.

```csharp
// Tu solución aquí
```

---

## Ejercicio 10

Leer el archivo `ventas.txt` del Ejercicio 9. Calcular el ingreso total de todas las ventas. Agregar al final del archivo una línea con el texto `TOTAL,{valor}` indicando ese ingreso total. Verificar leyendo el archivo nuevamente que la línea fue agregada correctamente.

```csharp
// Tu solución aquí
```

---

## 🔗 Repositorio del curso

El material de esta clase está disponible en:
[github.com/orlando-az/programacion-ii](https://github.com/orlando-az/programacion-ii)
