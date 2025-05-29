# Métodos Seudocódigo

---

## 1. Interpolación Lineal

```pseudocode
ALGORITMO InterpolacionLineal(x, xDatos, yDatos, n)
    PARA i DESDE 1 HASTA n-1 HACER
        SI x ≥ xDatos[i] Y x ≤ xDatos[i+1] ENTONCES
            m ← (yDatos[i+1] - yDatos[i]) / (xDatos[i+1] - xDatos[i])
            RETORNAR yDatos[i] + m * (x - xDatos[i])
        FIN SI
    FIN PARA
    IMPRIMIR "El valor x está fuera del rango de los datos"
    RETORNAR NULL
FIN ALGORITMO

// Ejemplo de uso
xDatos ← [0, 1, 2, 3]
yDatos ← [1, 3, 5, 7]
x ← 1.5
IMPRIMIR "Interpolación Lineal en x=1.5: ", InterpolacionLineal(x, xDatos, yDatos, 4)
```

---

## 2. Interpolación Polinómica (Método de Lagrange)

```pseudocode
ALGORITMO InterpolacionLagrange(x, xDatos, yDatos, n)
    suma ← 0
    PARA i DESDE 1 HASTA n HACER
        termino ← yDatos[i]
        PARA j DESDE 1 HASTA n HACER
            SI j ≠ i ENTONCES
                termino ← termino * (x - xDatos[j]) / (xDatos[i] - xDatos[j])
            FIN SI
        FIN PARA
        suma ← suma + termino
    FIN PARA
    RETORNAR suma
FIN ALGORITMO

// Ejemplo de uso
xDatos ← [0, 1, 2, 3]
yDatos ← [1, 3, 5, 7]
x ← 1.5
IMPRIMIR "Interpolación Polinómica en x=1.5: ", InterpolacionLagrange(x, xDatos, yDatos, 4)
```

---

## 3. Método de Regresión (Lineal)

```pseudocode
ALGORITMO RegresionLineal(xDatos, yDatos, n)
    sumX ← 0
    sumY ← 0
    sumXY ← 0
    sumX2 ← 0
    PARA i DESDE 1 HASTA n HACER
        sumX ← sumX + xDatos[i]
        sumY ← sumY + yDatos[i]
        sumXY ← sumXY + xDatos[i] * yDatos[i]
        sumX2 ← sumX2 + xDatos[i] * xDatos[i]
    FIN PARA
    m ← (n * sumXY - sumX * sumY) / (n * sumX2 - sumX * sumX)
    b ← (sumY - m * sumX) / n
    RETORNAR [m, b]
FIN ALGORITMO

// Ejemplo de uso
xDatos ← [0, 1, 2, 3]
yDatos ← [1, 3, 5, 7]
[m, b] ← RegresionLineal(xDatos, yDatos, 4)
IMPRIMIR "Regresión Lineal: y = ", m, "x + ", b
```

---

## 4. Método de Correlación

```pseudocode
ALGORITMO CoeficienteCorrelacion(xDatos, yDatos, n)
    sumX ← 0
    sumY ← 0
    sumXY ← 0
    sumX2 ← 0
    sumY2 ← 0
    PARA i DESDE 1 HASTA n HACER
        sumX ← sumX + xDatos[i]
        sumY ← sumY + yDatos[i]
        sumXY ← sumXY + xDatos[i] * yDatos[i]
        sumX2 ← sumX2 + xDatos[i] * xDatos[i]
        sumY2 ← sumY2 + yDatos[i] * yDatos[i]
    FIN PARA
    numerador ← n * sumXY - sumX * sumY
    denominador ← RAÍZ((n * sumX2 - sumX * sumX) * (n * sumY2 - sumY * sumY))
    SI denominador = 0 ENTONCES
        IMPRIMIR "División por cero en el cálculo de correlación"
        RETORNAR NULL
    FIN SI
    RETORNAR numerador / denominador
FIN ALGORITMO

// Ejemplo de uso
xDatos ← [0, 1, 2, 3]
yDatos ← [1, 3, 5, 7]
IMPRIMIR "Coeficiente de Correlación: r = ", CoeficienteCorrelacion(xDatos, yDatos, 4)
```

---

## 5. Método de Mínimos Cuadrados (Lineal)

```pseudocode
ALGORITMO MinimosCuadrados(xDatos, yDatos, n)
    sumX ← 0
    sumY ← 0
    sumXY ← 0
    sumX2 ← 0
    PARA i DESDE 1 HASTA n HACER
        sumX ← sumX + xDatos[i]
        sumY ← sumY + yDatos[i]
        sumXY ← sumXY + xDatos[i] * yDatos[i]
        sumX2 ← sumX2 + xDatos[i] * xDatos[i]
    FIN PARA
    m ← (n * sumXY - sumX * sumY) / (n * sumX2 - sumX * sumX)
    b ← (sumY - m * sumX) / n
    RETORNAR [m, b]
FIN ALGORITMO

// Ejemplo de uso
xDatos ← [0, 1, 2, 3]
yDatos ← [1, 3, 5, 7]
[m, b] ← MinimosCuadrados(xDatos, yDatos, 4)
IMPRIMIR "Mínimos Cuadrados: y = ", m, "x + ", b
```
