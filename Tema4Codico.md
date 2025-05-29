# Métodos T4

---

## 1. Regla del Trapecio

```java
public class ReglaTrapecio {
    public static double f(double x) {
        return x * x + 2 * x + 1; // f(x) = x^2 + 2x + 1
    }

    public static double reglaTrapecio(double a, double b, int n) {
        double h = (b - a) / n;
        double suma = (f(a) + f(b)) / 2.0;
        for (int i = 1; i < n; i++) {
            suma += f(a + i * h);
        }
        return h * suma;
    }

    public static void main(String[] args) {
        double a = 0, b = 2;
        int n = 10;
        double resultado = reglaTrapecio(a, b, n);
        System.out.printf("Integral por Regla del Trapecio: %.6f%n", resultado);
    }
}
```

---

## 2. Regla de Simpson

```java
public class ReglaSimpson {
    public static double f(double x) {
        return x * x + 2 * x + 1; // f(x) = x^2 + 2x + 1
    }

    public static double reglaSimpson(double a, double b, int n) {
        if (n % 2 != 0) {
            System.out.println("El número de subintervalos debe ser par");
            return Double.NaN;
        }
        double h = (b - a) / n;
        double suma = f(a) + f(b);
        for (int i = 1; i < n; i++) {
            double x = a + i * h;
            suma += (i % 2 == 0) ? 2 * f(x) : 4 * f(x);
        }
        return h * suma / 3.0;
    }

    public static void main(String[] args) {
        double a = 0, b = 2;
        int n = 10;
        double resultado = reglaSimpson(a, b, n);
        System.out.printf("Integral por Regla de Simpson: %.6f%n", resultado);
    }
}
```

---

## 3. Cuadratura Gaussiana

```java
public class CuadraturaGaussiana {
    public static double f(double x) {
        return x * x + 2 * x + 1; // f(x) = x^2 + 2x + 1
    }

    public static double cuadraturaGaussiana(double a, double b, int n) {
        double[] puntos = {-0.7745966692414834, 0, 0.7745966692414834}; // Puntos de Gauss para n=3
        double[] pesos = {0.5555555555555556, 0.8888888888888888, 0.5555555555555556}; // Pesos para n=3
        if (n != 3) {
            System.out.println("Solo se implementa para n=3 puntos");
            return Double.NaN;
        }
        double suma = 0;
        for (int i = 0; i < n; i++) {
            double x = ((b - a) * puntos[i] + (b + a)) / 2.0; // Cambio de variable
            suma += pesos[i] * f(x);
        }
        return (b - a) / 2.0 * suma;
    }

    public static void main(String[] args) {
        double a = 0, b = 2;
        int n = 3;
        double resultado = cuadraturaGaussiana(a, b, n);
        System.out.printf("Integral por Cuadratura Gaussiana: %.6f%n", resultado);
    }
}
```
