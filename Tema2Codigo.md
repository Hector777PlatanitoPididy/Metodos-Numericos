## 1. Método de Bisección

El método de Bisección encuentra una raíz dividiendo repetidamente un intervalo por la mitad y seleccionando el subintervalo donde la función cambia de signo.

```java
public class Biseccion {
    // Define la función f(x) = x^3 - x - 2
    public static double f(double x) {
        return x * x * x - x - 2;
    }

    public static double biseccion(double a, double b, double tol, int maxIter) {
        if (f(a) * f(b) >= 0) {
            System.out.println("Bisección: No hay raíz o hay múltiples raíces en el intervalo");
            return Double.NaN;
        }
        for (int i = 0; i < maxIter; i++) {
            double c = (a + b) / 2;
            if (f(c) == 0 || (b - a) / 2 < tol) {
                return c;
            }
            if (f(c) * f(a) > 0) {
                a = c;
            } else {
                b = c;
            }
        }
        return (a + b) / 2;
    }

    public static void main(String[] args) {
        double raiz = biseccion(1, 2, 1e-6, 100);
        System.out.println("Raíz por Bisección: " + raiz);
    }
}
```

---

## 2. Método de Regla Falsa

El método de Regla Falsa utiliza interpolación lineal entre dos puntos para estimar la raíz, actualizando el intervalo según el signo de la función.

```java
public class ReglaFalsa {
    public static double f(double x) {
        return x * x * x - x - 2;
    }

    public static double reglaFalsa(double a, double b, double tol, int maxIter) {
        if (f(a) * f(b) >= 0) {
            System.out.println("Regla Falsa: No hay raíz o hay múltiples raíces en el intervalo");
            return Double.NaN;
        }
        for (int i = 0; i < maxIter; i++) {
            double c = b - f(b) * (b - a) / (f(b) - f(a));
            if (Math.abs(f(c)) < tol) {
                return c;
            }
            if (f(c) * f(a) > 0) {
                a = c;
            } else {
                b = c;
            }
        }
        return b - f(b) * (b - a) / (f(b) - f(a));
    }

    public static void main(String[] args) {
        double raiz = reglaFalsa(1, 2, 1e-6, 100);
        System.out.println("Raíz por Regla Falsa: " + raiz);
    }
}
```

---

## 3. Método de Interpolación Lineal

La Interpolación Lineal estima la raíz conectando dos puntos con una línea recta y encontrando dónde cruza el eje x. (Nota: Similar a Regla Falsa, pero incluido para mayor claridad).

```java
public class InterpolacionLineal {
    public static double f(double x) {
        return x * x * x - x - 2;
    }

    public static double interpolacionLineal(double a, double b, double tol, int maxIter) {
        if (f(a) * f(b) >= 0) {
            System.out.println("Interpolación Lineal: No hay raíz o hay múltiples raíces en el intervalo");
            return Double.NaN;
        }
        for (int i = 0; i < maxIter; i++) {
            double x = b - f(b) * (b - a) / (f(b) - f(a));
            if (Math.abs(f(x)) < tol) {
                return x;
            }
            if (f(x) * f(a) > 0) {
                a = x;
            } else {
                b = x;
            }
        }
        return b - f(b) * (b - a) / (f(b) - f(a));
    }

    public static void main(String[] args) {
        double raiz = interpolacionLineal(1, 2, 1e-6, 100);
        System.out.println("Raíz por Interpolación Lineal: " + raiz);
    }
}
```

---

## 4. Método de la Secante

El método de la Secante utiliza dos aproximaciones iniciales y aproxima la derivada con una línea secante para encontrar la raíz de forma iterativa.

```java
public class Secante {
    public static double f(double x) {
        return x * x * x - x - 2;
    }

    public static double secante(double x0, double x1, double tol, int maxIter) {
        for (int i = 0; i < maxIter; i++) {
            if (Math.abs(f(x1)) < tol) {
                return x1;
            }
            double denominador = f(x1) - f(x0);
            if (denominador == 0) {
                System.out.println("Secante: División por cero encontrada");
                return Double.NaN;
            }
            double x2 = x1 - f(x1) * (x1 - x0) / denominador;
            x0 = x1;
            x1 = x2;
        }
        return x1;
    }

    public static void main(String[] args) {
        double raiz = secante(1, 2, 1e-6, 100);
        System.out.println("Raíz por Secante: " + raiz);
    }
}
```

---

## 5. Método de Punto Fijo

El método de Punto Fijo transforma la ecuación \( f(x) = 0 \) en \( x = g(x) \) e itera hasta la convergencia.

```java
public class PuntoFijo {
    public static double f(double x) {
        return x * x * x - x - 2;
    }

    // Reescribe f(x) = x^3 - x - 2 = 0 como x = (x^3 - 2)^(1/3)
    public static double g(double x) {
        return Math.pow(x * x * x - 2, 1.0 / 3.0);
    }

    public static double puntoFijo(double x0, double tol, int maxIter) {
        for (int i = 0; i < maxIter; i++) {
            double x1 = g(x0);
            if (Math.abs(x1 - x0) < tol) {
                return x1;
            }
            x0 = x1;
        }
        return x0;
    }

    public static void main(String[] args) {
        double raiz = puntoFijo(1.5, 1e-6, 100);
        System.out.println("Raíz por Punto Fijo: " + raiz);
    }
}
```

---

## 6. Método de Newton-Raphson

El método de Newton-Raphson utiliza la función y su derivada para encontrar la raíz de forma iterativa usando la fórmula \( x_{n+1} = x_n - f(x_n) / f'(x_n) \).

```java
public class NewtonRaphson {
    public static double f(double x) {
        return x * x * x - x - 2;
    }

    // Derivada de f(x) = x^3 - x - 2
    public static double df(double x) {
        return 3 * x * x - 1;
    }

    public static double newtonRaphson(double x0, double tol, int maxIter) {
        for (int i = 0; i < maxIter; i++) {
            if (Math.abs(f(x0)) < tol) {
                return x0;
            }
            double dfx = df(x0);
            if (dfx == 0) {
                System.out.println("Newton-Raphson: Derivada es cero");
                return Double.NaN;
            }
            x0 = x0 - f(x0) / dfx;
        }
        return x0;
    }

    public static void main(String[] args) {
        double raiz = newtonRaphson(1.5, 1e-6, 100);
        System.out.println("Raíz por Newton-Raphson: " + raiz);
    }
}
```

---
