# Métodos Explicación 

---

## 1. Regla del Trapecio

Aproxima la integral de \( f(x) = x^2 + 2x + 1 \) en [0, 2] dividiendo el intervalo en 10 subintervalos y sumando las áreas de trapecios formados por la función en los extremos de cada subintervalo. Es simple pero menos preciso, con error proporcional a \( h^2 \).

---

## 2. Regla de Simpson

Aproxima la integral de \( f(x) = x^2 + 2x + 1 \) en [0, 2] con 10 subintervalos, ajustando parábolas a grupos de tres puntos consecutivos y sumando sus áreas. Requiere un número par de subintervalos y es más preciso que el Trapecio, con error proporcional a \( h^4 \).

---

## 3. Cuadratura Gaussiana

Aproxima la integral de \( f(x) = x^2 + 2x + 1 \) en [0, 2] usando 3 puntos de Gauss-Legendre y sus pesos asociados. Evalúa la función en puntos óptimos para maximizar la precisión, logrando exactitud para polinomios de grado hasta 5 con solo 3 puntos.
