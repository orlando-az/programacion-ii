# Ejercicios de clase — Lógica y Ordenamiento

## PARTE 1

---

### 1 · Elección estudiantil: ganador por votos

En una elección estudiantil votaron 10 estudiantes. Cada voto es un número del 1 al 3 que representa al candidato elegido. Los votos en blanco se registran como 0.

**Dado el siguiente arreglo de votos, mostrar:**
- Cuántos votos obtuvo cada candidato
- Cuántos votos en blanco hubo
- Quién ganó (si hay empate, indicarlo)

```csharp
int[] votos = { 1, 3, 2, 1, 3, 1, 0, 2, 3, 1 };
```

```csharp
// Tu solución aquí
```
**Salida esperada:**
```
Candidato 1: 4 votos
Candidato 2: 2 votos
Candidato 3: 3 votos
Votos en blanco: 1
Ganador: Candidato 1 con 4 votos
```
---

### 2 · Asistencia: racha más larga

Un arreglo de 1s y 0s representa la asistencia diaria de un alumno durante 10 clases (1 = presente, 0 = ausente).

**Calcular:**
- La racha más larga de asistencia consecutiva
- El porcentaje total de asistencia

```csharp
int[] asistencia = { 1, 1, 0, 1, 1, 1, 0, 1, 1, 1 };
```
```csharp
// Tu solución aquí
```
**Salida esperada:**
```
Racha más larga: 3 clases consecutivas
Asistencia total: 80.0%
```
---

### 3 · tabla de posiciones

En un torneo hay 4 equipos. Para cada equipo el usuario ingresa cuántos partidos ganó, empató y perdió.

**Puntuación:** victoria = 3 pts · empate = 1 pt · derrota = 0 pts

**El programa debe:**
- Pedir nombre, victorias, empates y derrotas de cada equipo
- Mostrar la tabla con puntos de cada equipo
- Indicar el líder sin ordenar el arreglo

```csharp
// Tu solución aquí
```
**Salida esperada:**
```
Equipo           Pts  V  E  D
------------------------------
Rayos              9  3  0  1
Tormentas          7  2  1  1
...
Líder: Rayos con 9 puntos
```
---

### 4 · Ranking de facultad: aprobados por carrera

Una facultad tiene estudiantes de 2 carreras: 1 = Sistemas, 2 = Diseño. Aprobado = nota ≥ 60.

**Dado los siguientes arreglos, calcular:**
- Cuántos estudiantes hay por carrera
- Cuántos aprobaron en cada carrera
- El porcentaje de aprobación por carrera
- Cuál carrera tiene la mayor tasa de aprobación

```csharp
int[] carreras = { 1, 2, 1, 2, 1, 1, 2, 1, 2, 2 };
int[] notas    = { 75, 45, 88, 60, 35, 91, 83, 67, 77, 55 };
```

> 💡 Pista: recorré los dos arreglos con el mismo índice i. El valor `carreras[i]` te dice en qué posición del arreglo acumulador sumar.

```csharp
// Tu solución aquí
```
**Salida esperada:**
```
Sistemas: 4/5 aprobados (80.0%)
Diseño: 2/5 aprobados (40.0%)
 
Mayor tasa de aprobación: Sistemas (80.0%)
```
---

### 5 · Clasificados a la siguiente ronda

El usuario ingresa N equipos con su puntaje y el puntaje mínimo para clasificar.

**El programa debe:**
- Construir un arreglo con solo los equipos clasificados
- Construir un arreglo con los eliminados
- Mostrar ambos grupos y cuántos pasaron de ronda

> 💡 Pista: dos pasadas — la primera cuenta para crear los arreglos del tamaño exacto, la segunda separa.


```csharp
// Tu solución aquí
```
**Salida esperada:**
```
Clasificados (3): Halcones (82pts), Cóndores (91pts), Tigres (75pts)
Eliminados   (2): Pumas (58pts), Lobos (43pts)
```
---

### 6 · Promedio móvil de rendimiento

Un equipo jugó 6 partidos. Se quiere ver la tendencia calculando el promedio de cada grupo de 3 partidos consecutivos.

**El programa debe:**
- Mostrar cada ventana con los 3 valores y su promedio
- Indicar si la tendencia es ASCENDENTE, DESCENDENTE o ESTABLE comparando el primer y el último promedio

```csharp
double[] rendimiento = { 60.0, 70.0, 65.0, 75.0, 80.0, 78.0 };
```

> 💡 Pista: el número de ventanas es `Length - 2`. Para cada ventana `i` accedés a `rend[i]`, `rend[i+1]` y `rend[i+2]`.

```csharp
// Tu solución aquí
```

---

### 7 · Alto — Sistema de becas simplificado

Una universidad otorga becas con estas reglas:
- Solo clasifican estudiantes con promedio ≥ 70
- Hay un cupo máximo (ingresado por el usuario)
- Se asigna por orden de mayor a menor promedio

**El programa debe:**
1. Pedir N estudiantes con nombre y promedio
2. Pedir el cupo de becas
3. Filtrar los que tienen promedio ≥ 70
4. Ordenarlos de mayor a menor con Selección
5. Mostrar quiénes reciben beca y quiénes no clasifican

> 💡 Pista: guardá los índices de los clasificados en un arreglo auxiliar `idxClasif[]` y aplicá Selección sobre esos índices.

```csharp
// Datos ingresados por el usuario
```

```csharp
// Tu solución aquí
```

---

## PARTE 2 — Ordenamiento

---

### O1 · Simple — Ordenar notas de menor a mayor con Burbuja

El profesor registró las notas finales de 6 estudiantes. Ordenarlas de menor a mayor con Burbuja y mostrar el arreglo antes y después.

```csharp
int[] notas = { 72, 45, 88, 61, 53, 79 };
```

**Salida esperada:**
```
Antes:   72 45 88 61 53 79
Después: 45 53 61 72 79 88
```

```csharp
// Tu solución aquí
```

---

### O2 · Simple — Ordenar puntajes de mayor a menor con Selección

En un torneo los equipos terminaron con los siguientes puntajes. Ordenarlos de mayor a menor con Selección y mostrar el ranking final.

```csharp
string[] equipos  = { "Rayos", "Tigres", "Cóndores", "Pumas", "Halcones" };
int[]    puntajes = { 34, 51, 28, 47, 39 };
```

> 💡 Pista: cuando el swap mueve `puntajes[i]`, también tiene que mover `equipos[i]`.

**Salida esperada:**
```
Ranking final:
  1. Tigres       51 pts
  2. Pumas        47 pts
  3. Halcones     39 pts
  4. Rayos        34 pts
  5. Cóndores     28 pts
```

```csharp
// Tu solución aquí
```

---

### O3 · Simple — Ordenar nombres de alumnos alfabéticamente con Inserción

Una lista de alumnos llegó en desorden. Ordenarla alfabéticamente con Inserción y mostrar la lista antes y después.

```csharp
string[] alumnos = { "Valentina", "Bruno", "Ana", "Martina", "Carlos", "Lucía" };
```

> 💡 Pista: para comparar strings usá `string.Compare(a, b)`. Devuelve positivo si `a` va después que `b` alfabéticamente.

**Salida esperada:**
```
Antes:   Valentina, Bruno, Ana, Martina, Carlos, Lucía
Después: Ana, Bruno, Carlos, Lucía, Martina, Valentina
```

```csharp
// Tu solución aquí
```

---

*C# · Arreglos y ordenamiento — clase de retroalimentación*
