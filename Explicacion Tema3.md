# Métodos Explicación

---

## 1. Eliminación Gaussiana

Transforma la matriz aumentada del sistema \(3x_1 + x_2 + x_3 = 5\), \(x_1 + 4x_2 - x_3 = 6\), \(x_1 - x_2 + 5x_3 = 7\) en forma triangular superior mediante operaciones de fila, luego resuelve por sustitución hacia atrás. Es eficiente pero sensible a pivotes cercanos a cero.

---

## 2. Gauss-Jordan

Extiende la Eliminación Gaussiana para convertir la matriz aumentada en la matriz identidad, resolviendo directamente \(x_1, x_2, x_3\) del sistema dado. Requiere más operaciones que la Eliminación Gaussiana pero obtiene la solución sin sustitución hacia atrás.

---

## 3. Gauss-Seidel

Método iterativo que despeja cada variable del sistema y actualiza los valores inmediatamente, partiendo de \(x_1 = x_2 = x_3 = 0\). Itera hasta que la diferencia entre iteraciones sea menor a \(10^{-6}\) o se alcancen 100 iteraciones. Requiere diagonal dominante para converger.

---

## 4. Jacobi

Método iterativo que despeja cada variable del sistema pero actualiza todas al final de cada iteración, desde \(x_1 = x_2 = x_3 = 0\). Itera hasta que la diferencia entre iteraciones sea menor a \(10^{-6}\) o se alcancen 100 iteraciones. Necesita diagonal dominante para converger.
