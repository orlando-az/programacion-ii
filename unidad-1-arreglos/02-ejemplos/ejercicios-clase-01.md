---
## 🔰 Ejercicios

### Ejercicio 1: Creación básica
Crear un arreglo de 5 números enteros, asignar valores manualmente y mostrar todo el arreglo en pantalla.
---
```csharp
int [] numeros = new int[5];

numeros[0]=14;
numeros[1]=20;
numeros[2]=5;
numeros[3]=6;
numeros[4]=45;
```
### Ejercicio 2: Acceso por índice

Dado un arreglo de 4 números, mostrar:

- El primer elemento
- El segundo elemento
- El último elemento

---
```csharp
int[] vector = new int[3];

vector[0]=10;
vector[1]=11;
vector[2]=12;

Console.WriteLine($"Primer elemento valor: {vector[0]}");
```

### Ejercicio 3: Arreglo de texto

Crear un arreglo con 3 nombres y mostrar cada uno utilizando su posición (sin usar ciclos).

---
```csharp
string[] nombres = new string[4];

nombres[0]="Juan Carlos";
nombres[1]="Felipe";
nombres[2]="Victor";

Console.WriteLine($"En la posicion 1: {nombres[0]}" );
Console.WriteLine($"En la posicion 2: {nombres[1]}" );
Console.WriteLine($"En la posicion 3: {nombres[2]}" );
Console.WriteLine($"En la posicion 4: {nombres[3]}" );
```

### Ejercicio 4: Identificación de posiciones

Crear un arreglo de 5 números y mostrar un mensaje como:

- Elemento en posición 0: \_\_\_
- Elemento en posición 1: \_\_\_
- Elemento en posición 2: \_\_\_

---

### Ejercicio 5: Modificación de valores

Crear un arreglo de 3 números, luego:

- Cambiar el valor del segundo elemento
- Mostrar el arreglo actualizado
```csharp
int[] numeros = new int[3];

numeros[0]=5;
numeros[1]=-10;
numeros[2]=20;

int cont=1;

for (int i=0; i < numeros.Length; i++)
{
    if(cont==2)
    {
        Console.WriteLine($"Segundo Elemento {numeros[i]}");
    }
    cont++;
}
```
---

### Ejercicio 6: Comparación simple

Crear un arreglo con 2 números y mostrar cuál es mayor accediendo a sus posiciones.

---

### Ejercicio 7: Primer y último elemento

Crear un arreglo de 5 elementos y mostrar únicamente:

- El primer valor
- El último valor

💡 Pista: usa la longitud del arreglo para obtener el último elemento.

---

### Ejercicio 8: Arreglo mixto (conceptual)

Crear un arreglo con:

- Un número
- Un nombre
- Un valor booleano

Mostrar cada elemento.

---

### Ejercicio 9: Verificación de valor

Crear un arreglo de 3 números y:

- Mostrar si el primer elemento es mayor que el tercero

---

### Ejercicio 10: Mini reto guiado

Crear un arreglo de 4 números y mostrar:

- La suma del primer y último elemento

---
