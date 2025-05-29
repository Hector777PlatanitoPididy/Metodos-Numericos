# Seudocódigo de Métodos Numéricos para Encontrar Raíces

---

## 1. Método de Bisección

El método de Bisección encuentra una raíz dividiendo repetidamente un intervalo por la mitad y seleccionando el subintervalo donde la función cambia de signo.

```pseudocode
FUNCIÓN f(x)
    RETORNAR x^3 - x - 2
FIN FUNCIÓN

ALGORITMO Bisección(a, b, tol, maxIter)
    SI f(a) * f(b) >= 0 ENTONCES
        IMPRIMIR "No hay raíz o hay múltiples raíces en el intervalo"
        RETORNAR NULL
    FIN SI
    PARA i DESDE 1 HASTA maxIter HACER
        c ← (a + b) / 2
        SI f(c) = 0 O (b - a) / 2 < tol ENTONCES
            RETORNAR c
        FIN SI
        SI f(c) * f(a) > 0 ENTONCES
            a ← c
        SINO
            b ← c
        FIN SI
    FIN PARA
    RETORNAR (a + b) / 2
FIN ALGORITMO

// Ejemplo de uso
IMPRIMIR "Raíz por Bisección: ", Bisección(1, 2, 10^-6, 100)
```

---

## 2. Método de Regla Falsa

El método de Regla Falsa utiliza interpolación lineal entre dos puntos para estimar la raíz, actualizando el intervalo según el signo de la función.

```pseudocode
FUNCIÓN f(x)
    RETORNAR x^3 - x - 2
FIN FUNCIÓN

ALGORITMO ReglaFalsa(a, b, tol, maxIter)
    SI f(a) * f(b) >= 0 ENTONCES
        IMPRIMIR "No hay raíz o hay múltiples raíces en el intervalo"
        RETORNAR NULL
    FIN SI
    PARA i DESDE 1 HASTA maxIter HACER
        c ← b - f(b) * (b - a) / (f(b) - f(a))
        SI |f(c)| < tol ENTONCES
            RETORNAR c
        FIN SI
        SI f(c) * f(a) > 0 ENTONCES
            a ← c
        SINO
            b ← c
        FIN SI
    FIN PARA
    RETORNAR b - f(b) * (b - a) / (f(b) - f(a))
FIN ALGORITMO

// Ejemplo de uso
IMPRIMIR "Raíz por Regla Falsa: ", ReglaFalsa(1, 2, 10^-6, 100)
```

---

## 3. Método de Interpolación Lineal

La Interpolación Lineal estima la raíz conectando dos puntos con una línea recta y encontrando dónde cruza el eje x. (Nota: Similar a Regla Falsa, pero incluido para claridad).

```pseudocode
FUNCIÓN f(x)
    RETORNAR x^3 - x - 2
FIN FUNCIÓN

ALGORITMO InterpolacionLineal(a, b, tol, maxIter)
    SI f(a) * f(b) >= 0 ENTONCES
        IMPRIMIR "No hay raíz o hay múltiples raíces en el intervalo"
        RETORNAR NULL
    FIN SI
    PARA i DESDE 1 HASTA maxIter HACER
        x ← b - f(b) * (b - a) / (f(b) - f(a))
        SI |f(x)| < tol ENTONCES
            RETORNAR x
        FIN SI
        SI f(x) * f(a) > 0 ENTONCES
            a ← x
        SINO
            b ← x
        FIN SI
    FIN PARA
    RETORNAR b - f(b) * (b - a) / (f(b) - f(a))
FIN ALGORITMO

// Ejemplo de uso
IMPRIMIR "Raíz por Interpolación Lineal: ", InterpolacionLineal(1, 2, 10^-6, 100)
```

---

## 4. Método de la Secante

El método de la Secante utiliza dos aproximaciones iniciales y aproxima la derivada con una línea secante para encontrar la raíz de forma iterativa.

```pseudocode
FUNCIÓN f(x)
    RETORNAR x^3 - x - 2
FIN FUNCIÓN

ALGORITMO Secante(x0, x1, tol, maxIter)
    PARA i DESDE 1 HASTA maxIter HACER
        SI |f(x1)| < tol ENTONCES
            RETORNAR x1
        FIN SI
        denominador ← f(x1) - f(x0)
        SI denominador = 0 ENTONCES
            IMPRIMIR "Secante: División por cero encontrada"
            RETORNAR NULL
        FIN SI
        x2 ← x1 - f(x1) * (x1 - x0) / denominador
        x0 ← x1
        x1 ← x2
    FIN PARA
    RETORNAR x1
FIN ALGORITMO

// Ejemplo de uso
IMPRIMIR "Raíz por Secante: ", Secante(1, 2, 10^-6, 100)
```

---

## 5. Método de Punto Fijo

El método de Punto Fijo transforma la ecuación \( f(x) = 0 \) en \( x = g(x) \) e itera hasta la convergencia.

```pseudocode
FUNCIÓN f(x)
    RETORNAR x^3 - x - 2
FIN FUNCIÓN

FUNCIÓN g(x)
    // Reescribe f(x) = x^3 - x - 2 = 0 como x = (x^3 - 2)^(1/3)
    RETORNAR (x^3 - 2)^(1/3)
FIN FUNCIÓN

ALGORITMO PuntoFijo(x0, tol, maxIter)
    PARA i DESDE 1 HASTA maxIter HACER
        x1 ← g(x0)
        SI |x1 - x0| < tol ENTONCES
            RETORNAR x1
        FIN SI
        x0 ← x1
    FIN PARA
    RETORNAR x0
FIN ALGORITMO

// Ejemplo de uso
IMPRIMIR "Raíz por Punto Fijo: ", PuntoFijo(1.5, 10^-6, 100)
```

---

## 6. Método de Newton-Raphson

El método de Newton-Raphson utiliza la función y su derivada para encontrar la raíz de forma iterativa usando la fórmula \( x_{n+1} = x_n - f(x_n) / f'(x_n) \).

```pseudocode
FUNCIÓN f(x)
    RETORNAR x^3 - x - 2
FIN FUNCIÓN

FUNCIÓN df(x)
    // Derivada de f(x) = x^3 - x - 2
    RETORNAR 3 * x^2 - 1
FIN FUNCIÓN

ALGORITMO NewtonRaphson(x0, tol, maxIter)
    PARA i DESDE 1 HASTA maxIter HACER
        SI |f(x0)| < tol ENTONCES
            RETORNAR x0
        FIN SI
        dfx ← df(x0)
        SI dfx = 0 ENTONCES
            IMPRIMIR "Newton-Raphson: Derivada es cero"
            RETORNAR NULL
        FIN SI
        x0 ← x0 - f(x0) / dfx
    FIN PARA
    RETORNAR x0
FIN ALGORITMO

// Ejemplo de uso
IMPRIMIR "Raíz por Newton-Raphson: ", NewtonRaphson(1.5, 10^-6, 100)
```

---
