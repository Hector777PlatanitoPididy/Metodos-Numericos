# Métodos Seudocódigo

---

## 1. Regla del Trapecio

```pseudocode
FUNCIÓN f(x)
    RETORNAR x^2 + 2*x + 1
FIN FUNCIÓN

ALGORITMO ReglaTrapecio(a, b, n)
    h ← (b - a) / n
    suma ← (f(a) + f(b)) / 2
    PARA i DESDE 1 HASTA n-1 HACER
        x ← a + i * h
        suma ← suma + f(x)
    FIN PARA
    RETORNAR h * suma
FIN ALGORITMO

// Ejemplo de uso
a ← 0
b ← 2
n ← 10
IMPRIMIR "Integral por Regla del Trapecio: ", ReglaTrapecio(a, b, n)
```

---

## 2. Regla de Simpson

```pseudocode
FUNCIÓN f(x)
    RETORNAR x^2 + 2*x + 1
FIN FUNCIÓN

ALGORITMO ReglaSimpson(a, b, n)
    SI n MOD 2 ≠ 0 ENTONCES
        IMPRIMIR "El número de subintervalos debe ser par"
        RETORNAR NULL
    FIN SI
    h ← (b - a) / n
    suma ← f(a) + f(b)
    PARA i DESDE 1 HASTA n-1 HACER
        x ← a + i * h
        SI i MOD 2 = 0 ENTONCES
            suma ← suma + 2 * f(x)
        SINO
            suma ← suma + 4 * f(x)
        FIN SI
    FIN PARA
    RETORNAR h * suma / 3
FIN ALGORITMO

// Ejemplo de uso
a ← 0
b ← 2
n ← 10
IMPRIMIR "Integral por Regla de Simpson: ", ReglaSimpson(a, b, n)
```

---

## 3. Cuadratura Gaussiana

```pseudocode
FUNCIÓN f(x)
    RETORNAR x^2 + 2*x + 1
FIN FUNCIÓN

ALGORITMO CuadraturaGaussiana(a, b, n)
    SI n ≠ 3 ENTONCES
        IMPRIMIR "Solo se implementa para n=3 puntos"
        RETORNAR NULL
    FIN SI
    puntos ← [-0.7745966692414834, 0, 0.7745966692414834]
    pesos ← [0.5555555555555556, 0.8888888888888888, 0.5555555555555556]
    suma ← 0
    PARA i DESDE 1 HASTA n HACER
        x ← ((b - a) * puntos[i] + (b + a)) / 2
        suma ← suma + pesos[i] * f(x)
    FIN PARA
    RETORNAR (b - a) / 2 * suma
FIN ALGORITMO

// Ejemplo de uso
a ← 0
b ← 2
n ← 3
IMPRIMIR "Integral por Cuadratura Gaussiana: ", CuadraturaGaussiana(a, b, n)
```
