# Ejemplos de Errores Numéricos en Java

Este repositorio muestra ejemplos de diferentes tipos de **errores numéricos** comunes en la materia de **métodos numéricos**, implementados en Java.

---

## 🔹 1. Error de Truncamiento

Aproximación de una derivada usando diferencias finitas.

```java
public class ErrorTruncamiento {
    public static void main(String[] args) {
        double h = 0.1;
        double x = 1.0;

        double derivadaAprox = (Math.sin(x + h) - Math.sin(x)) / h;
        double derivadaExacta = Math.cos(x);

        double errorTruncamiento = Math.abs(derivadaExacta - derivadaAprox);

        System.out.println("Derivada aproximada: " + derivadaAprox);
        System.out.println("Derivada exacta: " + derivadaExacta);
        System.out.println("Error de truncamiento: " + errorTruncamiento);
    }
}
```

---

## 🔹 2. Error de Redondeo

Suma repetida de valores muy pequeños.

```java
public class ErrorRedondeo {
    public static void main(String[] args) {
        double suma = 0.0;
        for (int i = 0; i < 1000000; i++) {
            suma += 1e-10;
        }

        System.out.println("Suma esperada: 0.1");
        System.out.println("Suma real: " + suma);
    }
}
```

---

## 🔹 3. Error Absoluto y Relativo

Comparación entre valor real y aproximado.

```java
public class ErrorAbsolutoRelativo {
    public static void main(String[] args) {
        double valorReal = Math.PI;
        double valorAprox = 3.14;

        double errorAbsoluto = Math.abs(valorReal - valorAprox);
        double errorRelativo = errorAbsoluto / Math.abs(valorReal);

        System.out.println("Error absoluto: " + errorAbsoluto);
        System.out.println("Error relativo: " + errorRelativo);
    }
}
```

---

## 🔹 4. Error de Cancelación

Restar números muy cercanos entre sí.

```java
public class ErrorCancelacion {
    public static void main(String[] args) {
        double a = 1.0000001;
        double b = 1.0000000;

        double resultado = a - b;
        System.out.println("Resultado esperado: 0.0000001");
        System.out.println("Resultado real: " + resultado);
    }
}
```

---

## 🔹 5. Error por Criterio de Parada Inadecuado

Uso de un mal criterio de parada en un método iterativo (Newton-Raphson).

```java
public class ErrorCriterioParada {
    public static void main(String[] args) {
        double x = 1.0;
        int iteraciones = 0;

        while (iteraciones < 1000) { // Criterio malo: solo número de iteraciones
            double fx = x * x - 2;
            double dfx = 2 * x;

            x = x - fx / dfx;
            iteraciones++;
        }

        System.out.println("Raíz aproximada: " + x);
    }
}
```

---
