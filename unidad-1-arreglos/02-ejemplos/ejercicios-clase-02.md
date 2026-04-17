# Ejercicios de Arreglos con ciclo `for` — C#
### Segunda clase de arreglos

---

## Ejercicio 1 — Mostrar elementos en orden inverso `Simple`

Crear un arreglo de 5 números enteros. Usando un ciclo `for`, mostrar los elementos desde el último hasta el primero.

> 💡 Pista: el ciclo debe comenzar en el índice más alto y decrementar en cada iteración.

```csharp
int [] numeros = {10,8,9,4,3,7,6};

int [] invertido = new int[numeros.Length];

for(int i= numeros.Length-1 ; i>=0;i--)
{
    invertido[i]=numeros[i];
    Console.WriteLine(invertido[i]);
}
```

---

## Ejercicio 2 — Multiplicar arreglo por un factor `Simple`

Crear un arreglo de 4 números. Con un ciclo, mostrar cada elemento multiplicado por 3, sin modificar el arreglo original.

```csharp
int [] numeros = {6,4,5,7,10};
int multiplo=0;

for(int i =0; i< numeros.Length-1;i++)
{
    multiplo= numeros[i] * 3;
    Console.Writeline($"El valor de arreglo es igual:{multiplo}");
}
```

---

## Ejercicio 3 — Separar en dos grupos `Medio`

Crear un arreglo de 8 números (mezcla de pares e impares). Usando un ciclo, construir dos arreglos separados: uno con los pares y otro con los impares. Mostrar ambos.

> 💡 Pista: necesitarás dos arreglos auxiliares y dos contadores para saber en qué posición insertar cada elemento.

```csharp
int [] principal = {7,5,4,10,12,8,9};
int cont_p=0;
int cont_ip=0;

for(int i=0; i < principal.Length; i++)
{
    if(principal[i] % 2==0)
        cont_p++;
    else
        cont_ip++;
}

int [] pares = new int[cont_p];
int [] impares = new int[cont_ip];

int pos_p=0;
int pos_imp=0;
for (int i = 0; i < principal.Length; i++)
{
    if (principal[i]%2==0)
    {
        pares[pos_p]=principal[i];
        pos_p++;
    }
    else
    {
        impares[pos_imp]=principal[i];
        pos_imp++;
    }
}

Console.Write($"Arreglo de pares: {String.Join(" ",pares)}");
Console.WriteLine(" ");
Console.Write($"Arreglo de impares: {String.Join(" ", impares)} ");

// TOMA EL TAMAÑO DEL PRIMER ARREGLO
int[] numeros = { 1, 2, 3, 4, 5, 6, 7 };
int[] pares = new int[numeros.Length];
int[] impares = new int[numeros.Length];
int p = 0;
int imp = 0;
for (int s = 0; s < numeros.Length; s++)
{
    if (numeros[s] % 2 == 0) {
        
        pares[p] = numeros[s];
        p++;
    }
    else {
        
        impares[imp] = numeros[s];
        imp++;
    }
}
Console.WriteLine("PARES: ");
           
for (int s = 0;s < p; s++)
{
    Console.WriteLine(pares [s]);
}
Console.WriteLine("IMPARES : ");
for (int s = 0;s<imp; s++)
{
    Console.WriteLine(impares[s]);
}
```

---

## Ejercicio 4 — Reemplazar negativos por cero `Medio`

Crear un arreglo de 7 números (algunos negativos). Con un ciclo, reemplazar cada número negativo por `0` directamente en el arreglo. Mostrar el arreglo antes y después del cambio.

```csharp
int [] numeros = {1,-10,0,-82,5,6-7};

for (int i = 0; i < numeros.Length; i++)
{
    if (numeros[i]<0)
    {
        numeros[i]=0;
    }
}

Console.Write(String.Join(" ",numeros));
```

---

## Ejercicio 5 — Suma acumulada paso a paso `Avanzado`

Crear un arreglo de 6 números. Con un ciclo, mostrar en cada paso la suma acumulada hasta ese índice.

Ejemplo con `{ 3, 5, 2, 8, 1, 4 }`:
```
Paso 1: 3
Paso 2: 8
Paso 3: 10
...
```

> 💡 Pista: necesitas una variable que guarde la suma y se actualice en cada iteración antes de mostrarla.

```csharp
int [] numeros = {3,7,6,7};
int sumatoria=0;

for (int i = 0; i < numeros.Length; i++)
{
    sumatoria= sumatoria + numeros[i];
    Console.WriteLine($"El valor de la suma es: {sumatoria}");
}
```

---

## Ejercicio 6 — Comparar primera y segunda mitad `Avanzado`

Crear un arreglo de 6 números. Con dos ciclos separados, calcular la suma de la primera mitad y la suma de la segunda mitad. Mostrar cuál mitad tiene mayor suma.

> 💡 Pista: usa `Length / 2` para dividir el arreglo sin hardcodear el índice.

```csharp
// Tu solución aquí
```

---

## Ejercicio 7 — Cuántos están por encima del promedio `Avanzado`

Dado un arreglo de 7 números, calcular el promedio con un primer ciclo y luego, con un segundo ciclo, contar cuántos elementos superan ese promedio. Mostrar el promedio y el conteo.

> 💡 Pista: el promedio debe estar calculado completo antes de poder comparar. Necesitas dos pasadas separadas.

```csharp
// Tu solución aquí
```

---

## Ejercicio 8 — Mayor de la primera mitad vs menor de la segunda `Avanzado`

Crear un arreglo de 8 números. Usando dos ciclos:

- Encontrar el valor mayor dentro de la primera mitad
- Encontrar el valor menor dentro de la segunda mitad
- Mostrar ambos valores e indicar cuál es mayor entre los dos

```csharp
// Tu solución aquí
```

---
