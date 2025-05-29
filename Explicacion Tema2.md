# ExplicaciónTema2
---

## 1. Método de Bisección

Divide un intervalo [1, 2] por la mitad, evalúa la función \( f(x) = x^3 - x - 2 \) en el punto medio y selecciona el subintervalo donde la función cambia de signo. Repite hasta que el intervalo sea menor a \( 10^{-6} \) o se alcance un máximo de 100 iteraciones. Es robusto pero lento.

---

## 2. Método de Regla Falsa

Usa interpolación lineal en el intervalo [1, 2] para estimar la raíz de \( f(x) = x^3 - x - 2 \). Calcula un nuevo punto con la fórmula de la secante y actualiza el intervalo según el signo de la función. Itera hasta que \( |f(x)| < 10^{-6} \) o se alcancen 100 iteraciones. Más rápido que Bisección, pero puede ser lento en algunos casos.

---

## 3. Método de Interpolación Lineal

Similar a Regla Falsa, estima la raíz de \( f(x) = x^3 - x - 2 \) en [1, 2] mediante una línea recta entre dos puntos y encuentra su intersección con el eje x. Actualiza el intervalo según el signo y repite hasta que \( |f(x)| < 10^{-6} \) o se alcancen 100 iteraciones. Equivalente a Regla Falsa en este contexto.

---

## 4. Método de la Secante

Usa dos puntos iniciales (\( x_0 = 1 \), \( x_1 = 2 \)) y aproxima la derivada de \( f(x) = x^3 - x - 2 \) con una línea secante. Calcula un nuevo punto y actualiza los puntos anteriores. Itera hasta que \( |f(x)| < 10^{-6} \) o se alcancen 100 iteraciones. Es rápido pero requiere dos puntos iniciales.

---

## 5. Método de Punto Fijo

Transforma \( f(x) = x^3 - x - 2 = 0 \) en \( x = g(x) = (x^3 - 2)^{1/3} \). Desde \( x_0 = 1.5 \), itera aplicando \( g(x) \) hasta que la diferencia entre iteraciones sea menor a \( 10^{-6} \) o se alcancen 100 iteraciones. Converge si \( g(x) \) es adecuada, pero puede divergir.

---

## 6. Método de Newton-Raphson

Usa la fórmula \( x_{n+1} = x_n - f(x_n)/f'(x_n) \) con \( f(x) = x^3 - x - 2 \), \( f'(x) = 3x^2 - 1 \), y \( x_0 = 1.5 \). Itera hasta que \( |f(x)| < 10^{-6} \) o se alcancen 100 iteraciones. Es muy rápido (convergencia cuadrática) pero requiere la derivada y una buena aproximación inicial.
