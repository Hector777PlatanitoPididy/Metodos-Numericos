# Métodos T5

---

## 1. Interpolación Lineal

```java
public class InterpolacionLineal {
    public static double interpolarLineal(double x, double[] xDatos, double[] yDatos) {
        int n = xDatos.length;
        for (int i = 0; i < n - 1; i++) {
            if (x >= xDatos[i] && x <= xDatos[i + 1]) {
                double m = (yDatos[i + 1] - yDatos[i]) / (xDatos[i + 1] - xDatos[i]);
                return yDatos[i] + m * (x - xDatos[i]);
            }
        }
        System.out.println("El valor x está fuera del rango de los datos");
        return Double.NaN;
    }

    public static void main(String[] args) {
        double[] xDatos = {0, 1, 2, 3};
        double[] yDatos = {1, 3, 5, 7};
        double x = 1.5;
        double y = interpolarLineal(x, xDatos, yDatos);
        System.out.printf("Interpolación Lineal en x=%.1f: y=%.6f%n", x, y);
    }
}
```

---

## 2. Interpolación Polinómica (Método de Lagrange)

```java
public class InterpolacionPolinomica {
    public static double interpolarLagrange(double x, double[] xDatos, double[] yDatos) {
        int n = xDatos.length;
        double suma = 0;
        for (int i = 0; i < n; i++) {
            double termino = yDatos[i];
            for (int j = 0; j < n; j++) {
                if (j != i) {
                    termino *= (x - xDatos[j]) / (xDatos[i] - xDatos[j]);
                }
            }
            suma += termino;
        }
        return suma;
    }

    public static void main(String[] args) {
        double[] xDatos = {0, 1, 2, 3};
        double[] yDatos = {1, 3, 5, 7};
        double x = 1.5;
        double y = interpolarLagrange(x, xDatos, yDatos);
        System.out.printf("Interpolación Polinómica en x=%.1f: y=%.6f%n", x, y);
    }
}
```

---

## 3. Método de Regresión (Lineal)

```java
public class RegresionLineal {
    public static double[] regresionLineal(double[] xDatos, double[] yDatos) {
        int n = xDatos.length;
        double sumX = 0, sumY = 0, sumXY = 0, sumX2 = 0;
        for (int i = 0; i < n; i++) {
            sumX += xDatos[i];
            sumY += yDatos[i];
            sumXY += xDatos[i] * yDatos[i];
            sumX2 += xDatos[i] * xDatos[i];
        }
        double m = (n * sumXY - sumX * sumY) / (n * sumX2 - sumX * sumX);
        double b = (sumY - m * sumX) / n;
        return new double[]{m, b}; // Retorna [pendiente, intercepto]
    }

    public static void main(String[] args) {
        double[] xDatos = {0, 1, 2, 3};
        double[] yDatos = {1, 3, 5, 7};
        double[] coeficientes = regresionLineal(xDatos, yDatos);
        System.out.printf("Regresión Lineal: y = %.6fx + %.6f%n", coeficientes[0], coeficientes[1]);
    }
}
```

---

## 4. Método de Correlación

```java
public class Correlacion {
    public static double coeficienteCorrelacion(double[] xDatos, double[] yDatos) {
        int n = xDatos.length;
        double sumX = 0, sumY = 0, sumXY = 0, sumX2 = 0, sumY2 = 0;
        for (int i = 0; i < n; i++) {
            sumX += xDatos[i];
            sumY += yDatos[i];
            sumXY += xDatos[i] * yDatos[i];
            sumX2 += xDatos[i] * xDatos[i];
            sumY2 += yDatos[i] * yDatos[i];
        }
        double numerador = n * sumXY - sumX * sumY;
        double denominador = Math.sqrt((n * sumX2 - sumX * sumX) * (n * sumY2 - sumY * sumY));
        if (denominador == 0) {
            System.out.println("División por cero en el cálculo de correlación");
            return Double.NaN;
        }
        return numerador / denominador;
    }

    public static void main(String[] args) {
        double[] xDatos = {0, 1, 2, 3};
        double[] yDatos = {1, 3, 5, 7};
        double r = coeficienteCorrelacion(xDatos, yDatos);
        System.out.printf("Coeficiente de Correlación: r = %.6f%n", r);
    }
}
```

---

## 5. Método de Mínimos Cuadrados (Lineal)

```java
public class MinimosCuadrados {
    public static double[] minimosCuadrados(double[] xDatos, double[] yDatos) {
        int n = xDatos.length;
        double sumX = 0, sumY = 0, sumXY = 0, sumX2 = 0;
        for (int i = 0; i < n; i++) {
            sumX += xDatos[i];
            sumY += yDatos[i];
            sumXY += xDatos[i] * yDatos[i];
            sumX2 += xDatos[i] * xDatos[i];
        }
        double m = (n * sumXY - sumX * sumY) / (n * sumX2 - sumX * sumX);
        double b = (sumY - m * sumX) / n;
        return new double[]{m, b}; // Retorna [pendiente, intercepto]
    }

    public static void main(String[] args) {
        double[] xDatos = {0, 1, 2, 3};
        double[] yDatos = {1, 3, 5, 7};
        double[] coeficientes = minimosCuadrados(xDatos, yDatos);
        System.out.printf("Mínimos Cuadrados: y = %.6fx + %.6f%n", coeficientes[0], coeficientes[1]);
    }
}
```
