# Métodos Código T6

---

## 1. Método de Un Paso (Euler Explícito)

```java
public class MetodoUnPaso {
    public static double f(double x, double y) {
        return -2 * x * y; // dy/dx = -2xy
    }

    public static double[] metodoUnPaso(double x0, double y0, double xf, double h) {
        int n = (int) ((xf - x0) / h) + 1;
        double[] x = new double[n];
        double[] y = new double[n];
        x[0] = x0;
        y[0] = y0;
        for (int i = 0; i < n - 1; i++) {
            x[i + 1] = x[i] + h;
            y[i + 1] = y[i] + h * f(x[i], y[i]);
        }
        return y;
    }

    public static void main(String[] args) {
        double x0 = 0, y0 = 1, xf = 1, h = 0.1;
        double[] y = metodoUnPaso(x0, y0, xf, h);
        System.out.println("Método de Un Paso (Euler Explícito):");
        for (int i = 0; i < y.length; i++) {
            System.out.printf("x=%.1f, y=%.6f%n", x0 + i * h, y[i]);
        }
    }
}
```

---

## 2. Método de Paso Múltiple (Adams-Bashforth de 2 Pasos)

```java
public class MetodoPasoMultiple {
    public static double f(double x, double y) {
        return -2 * x * y; // dy/dx = -2xy
    }

    public static double[] metodoAdamsBashforth(double x0, double y0, double xf, double h) {
        int n = (int) ((xf - x0) / h) + 1;
        double[] x = new double[n];
        double[] y = new double[n];
        x[0] = x0;
        y[0] = y0;

        // Primer paso con Euler para inicializar
        x[1] = x0 + h;
        y[1] = y[0] + h * f(x[0], y[0]);

        // Adams-Bashforth de 2 pasos
        for (int i = 1; i < n - 1; i++) {
            x[i + 1] = x[i] + h;
            y[i + 1] = y[i] + h / 2.0 * (3 * f(x[i], y[i]) - f(x[i - 1], y[i - 1]));
        }
        return y;
    }

    public static void main(String[] args) {
        double x0 = 0, y0 = 1, xf = 1, h = 0.1;
        double[] y = metodoAdamsBashforth(x0, y0, xf, h);
        System.out.println("Método de Paso Múltiple (Adams-Bashforth 2 pasos):");
        for (int i = 0; i < y.length; i++) {
            System.out.printf("x=%.1f, y=%.6f%n", x0 + i * h, y[i]);
        }
    }
}
```

---

## 3. Método de Euler

```java
public class MetodoEuler {
    public static double f(double x, double y) {
        return -2 * x * y; // dy/dx = -2xy
    }

    public static double[] metodoEuler(double x0, double y0, double xf, double h) {
        int n = (int) ((xf - x0) / h) + 1;
        double[] x = new double[n];
        double[] y = new double[n];
        x[0] = x0;
        y[0] = y0;
        for (int i = 0; i < n - 1; i++) {
            x[i + 1] = x[i] + h;
            y[i + 1] = y[i] + h * f(x[i], y[i]);
        }
        return y;
    }

    public static void main(String[] args) {
        double x0 = 0, y0 = 1, xf = 1, h = 0.1;
        double[] y = metodoEuler(x0, y0, xf, h);
        System.out.println("Método de Euler:");
        for (int i = 0; i < y.length; i++) {
            System.out.printf("x=%.1f, y=%.6f%n", x0 + i * h, y[i]);
        }
    }
}
```

---

## 4. Método de Runge-Kutta (Orden 4)

```java
public class RungeKutta {
    public static double f(double x, double y) {
        return -2 * x * y; // dy/dx = -2xy
    }

    public static double[] metodoRungeKutta(double x0, double y0, double xf, double h) {
        int n = (int) ((xf - x0) / h) + 1;
        double[] x = new double[n];
        double[] y = new double[n];
        x[0] = x0;
        y[0] = y0;
        for (int i = 0; i < n - 1; i++) {
            x[i + 1] = x[i] + h;
            double k1 = f(x[i], y[i]);
            double k2 = f(x[i] + h / 2, y[i] + h * k1 / 2);
            double k3 = f(x[i] + h / 2, y[i] + h * k2 / 2);
            double k4 = f(x[i] + h, y[i] + h * k3);
            y[i + 1] = y[i] + h / 6.0 * (k1 + 2 * k2 + 2 * k3 + k4);
        }
        return y;
    }

    public static void main(String[] args) {
        double x0 = 0, y0 = 1, xf = 1, h = 0.1;
        double[] y = metodoRungeKutta(x0, y0, xf, h);
        System.out.println("Método de Runge-Kutta (Orden 4):");
        for (int i = 0; i < y.length; i++) {
            System.out.printf("x=%.1f, y=%.6f%n", x0 + i * h, y[i]);
        }
    }
}
```

---

## 5. Método de Taylor (Orden 2)

```java
public class MetodoTaylor {
    public static double f(double x, double y) {
        return -2 * x * y; // dy/dx = -2xy
    }

    public static double df(double x, double y) {
        // Derivada segunda: d^2y/dx^2 = d/dx(-2xy) = -2y - 2x*dy/dx = -2y - 2x(-2xy) = -2y + 4x^2y
        return -2 * y + 4 * x * x * y;
    }

    public static double[] metodoTaylor(double x0, double y0, double xf, double h) {
        int n = (int) ((xf - x0) / h) + 1;
        double[] x = new double[n];
        double[] y = new double[n];
        x[0] = x0;
        y[0] = y0;
        for (int i = 0; i < n - 1; i++) {
            x[i + 1] = x[i] + h;
            double f1 = f(x[i], y[i]);
            double f2 = df(x[i], y[i]);
            y[i + 1] = y[i] + h * f1 + (h * h / 2) * f2;
        }
        return y;
    }

    public static void main(String[] args) {
        double x0 = 0, y0 = 1, xf = 1, h = 0.1;
        double[] y = metodoTaylor(x0, y0, xf, h);
        System.out.println("Método de Taylor (Orden 2):");
        for (int i = 0; i < y.length; i++) {
            System.out.printf("x=%.1f, y=%.6f%n", x0 + i * h, y[i]);
        }
    }
}
```
