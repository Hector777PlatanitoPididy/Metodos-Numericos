# Métodos Explicación 

---

## 1. Método de Un Paso 

Aproxima la solución de \( \frac{dy}{dx} = -2xy, y(0) = 1 \) en \([0, 1]\) con \( h = 0.1 \), usando la derivada en el punto actual para avanzar al siguiente: \( y_{i+1} = y_i + h f(x_i, y_i) \). Es simple pero poco preciso, con error proporcional a \( h \).

---

## 2. Método de Paso Múltiple 

Resuelve \( \frac{dy}{dx} = -2xy, y(0) = 1 \) en \([0, 1]\) con \( h = 0.1 \), usando dos puntos previos para mejorar la aproximación: \( y_{i+1} = y_i + \frac{h}{2} (3 f(x_i, y_i) - f(x_{i-1}, y_{i-1})) \). Inicializa con Euler. Más preciso que Euler, pero requiere valores iniciales.

---

## 3. Método de Euler

Idéntico al Método de Un Paso en este caso, resuelve \( \frac{dy}{dx} = -2xy, y(0) = 1 \) en \([0, 1]\) con \( h = 0.1 \), avanzando con \( y_{i+1} = y_i + h f(x_i, y_i) \). Es fácil de implementar pero tiene baja precisión.

---

## 4. Método de Runge-Kutta 

Resuelve \( \frac{dy}{dx} = -2xy, y(0) = 1 \) en \([0, 1]\) con \( h = 0.1 \), combinando cuatro evaluaciones de la derivada (\( k_1, k_2, k_3, k_4 \)) para calcular \( y_{i+1} \). Muy preciso, con error proporcional a \( h^4 \), y ampliamente usado.

---

## 5. Método de Taylor 

Resuelve \( \frac{dy}{dx} = -2xy, y(0) = 1 \) en \([0, 1]\) con \( h = 0.1 \), usando la serie de Taylor hasta el término de segundo orden: \( y_{i+1} = y_i + h f(x_i, y_i) + \frac{h^2}{2} f'(x_i, y_i) \). Preciso pero requiere derivadas adicionales.
