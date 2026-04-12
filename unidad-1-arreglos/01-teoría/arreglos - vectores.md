# 📘 Teoría Aplicada: Arreglos (Vectores)

## 🎯 Objetivo

Comprender el uso de arreglos para almacenar y procesar múltiples datos de forma eficiente.

---

## ❓ ¿Por qué necesitamos arreglos?

En programación, muchas veces necesitamos trabajar con varios datos del mismo tipo.

👉 Ejemplo: Guardar las notas de 5 estudiantes

❌ Forma no eficiente:

```csharp
int nota1 = 10;
int nota2 = 20;
int nota3 = 30;
int nota4 = 40;
int nota5 = 50;
```

🔴 Problemas:

- Mucho código
- Difícil de mantener
- No es escalable

---

## 📌 ¿Qué es un arreglo?

Un **arreglo (vector)** es una estructura que permite almacenar varios valores del mismo tipo en una sola variable.

👉 Ejemplo:

```csharp
int[] notas = new int[5];
```

---

## 🔹 Características

- Almacena múltiples datos
- Todos del mismo tipo
- Tiene tamaño fijo
- Se accede mediante índices

---

## 🔢 Índices

Los arreglos comienzan desde la posición **0**

| Índice | Valor |
| ------ | ----- |
| 0      | 10    |
| 1      | 20    |
| 2      | 30    |
| 3      | 40    |
| 4      | 50    |

👉 Ejemplo:

```csharp
notas[0] = 10;
```

---

## 🔁 Recorrido de un arreglo

Para recorrer un arreglo se utiliza un ciclo `for`:

```csharp
for(int i = 0; i < notas.Length; i++)
{
    Console.WriteLine(notas[i]);
}
```

---

## 📏 Propiedad Length

Permite conocer la cantidad de elementos del arreglo.

```csharp
notas.Length
```

---

## 💡 Aplicaciones

Los arreglos se utilizan en:

- Notas de estudiantes
- Edades
- Listas de nombres
- Ventas
- Datos numéricos en general

---

## 🧠 Idea clave

👉 Un arreglo permite organizar múltiples datos y trabajarlos de forma eficiente.

---
