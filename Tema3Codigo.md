# Métodos T3

---

## 1. Eliminación Gaussiana

```java
public class EliminacionGaussiana {
    public static double[] gaussianElimination(double[][] A, double[] b) {
        int n = b.length;
        double[][] augmented = new double[n][n + 1];
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                augmented[i][j] = A[i][j];
            }
            augmented[i][n] = b[i];
        }

        for (int i = 0; i < n - 1; i++) {
            if (augmented[i][i] == 0) {
                System.out.println("Pivote cero detectado");
                return null;
            }
            for (int k = i + 1; k < n; k++) {
                double factor = augmented[k][i] / augmented[i][i];
                for (int j = i; j <= n; j++) {
                    augmented[k][j] -= factor * augmented[i][j];
                }
            }
        }

        double[] x = new double[n];
        for (int i = n - 1; i >= 0; i--) {
            if (augmented[i][i] == 0) {
                System.out.println("Sistema no tiene solución única");
                return null;
            }
            x[i] = augmented[i][n] / augmented[i][i];
            for (int k = i - 1; k >= 0; k--) {
                augmented[k][n] -= augmented[k][i] * x[i];
            }
        }
        return x;
    }

    public static void main(String[] args) {
        double[][] A = {{3, 1, 1}, {1, 4, -1}, {1, -1, 5}};
        double[] b = {5, 6, 7};
        double[] x = gaussianElimination(A, b);
        if (x != null) {
            System.out.println("Solución por Eliminación Gaussiana:");
            for (int i = 0; i < x.length; i++) {
                System.out.printf("x%d = %.6f%n", i + 1, x[i]);
            }
        }
    }
}
```

---

## 2. Gauss-Jordan

```java
public class GaussJordan {
    public static double[] gaussJordan(double[][] A, double[] b) {
        int n = b.length;
        double[][] augmented = new double[n][n + 1];
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                augmented[i][j] = A[i][j];
            }
            augmented[i][n] = b[i];
        }

        for (int i = 0; i < n; i++) {
            if (augmented[i][i] == 0) {
                System.out.println("Pivote cero detectado");
                return null;
            }
            double pivot = augmented[i][i];
            for (int j = 0; j <= n; j++) {
                augmented[i][j] /= pivot;
            }
            for (int k = 0; k < n; k++) {
                if (k != i) {
                    double factor = augmented[k][i];
                    for (int j = 0; j <= n; j++) {
                        augmented[k][j] -= factor * augmented[i][j];
                    }
                }
            }
        }

        double[] x = new double[n];
        for (int i = 0; i < n; i++) {
            x[i] = augmented[i][n];
        }
        return x;
    }

    public static void main(String[] args) {
        double[][] A = {{3, 1, 1}, {1, 4, -1}, {1, -1, 5}};
        double[] b = {5, 6, 7};
        double[] x = gaussJordan(A, b);
        if (x != null) {
            System.out.println("Solución por Gauss-Jordan:");
            for (int i = 0; i < x.length; i++) {
                System.out.printf("x%d = %.6f%n", i + 1, x[i]);
            }
        }
    }
}
```

---

## 3. Gauss-Seidel

```java
public class GaussSeidel {
    public static double[] gaussSeidel(double[][] A, double[] b, double tol, int maxIter) {
        int n = b.length;
        double[] x = new double[n];
        double[] xOld = new double[n];
        for (int iter = 0; iter < maxIter; iter++) {
            for (int i = 0; i < n; i++) {
                xOld[i] = x[i];
                double sum = b[i];
                for (int j = 0; j < n; j++) {
                    if (j != i) {
                        sum -= A[i][j] * x[j];
                    }
                }
                if (A[i][i] == 0) {
                    System.out.println("División por cero en diagonal");
                    return null;
                }
                x[i] = sum / A[i][i];
            }
            double maxDiff = 0;
            for (int i = 0; i < n; i++) {
                maxDiff = Math.max(maxDiff, Math.abs(x[i] - xOld[i]));
            }
            if (maxDiff < tol) {
                return x;
            }
        }
        System.out.println("No convergió en el máximo de iteraciones");
        return x;
    }

    public static void main(String[] args) {
        double[][] A = {{3, 1, 1}, {1, 4, -1}, {1, -1, 5}};
        double[] b = {5, 6, 7};
        double[] x = gaussSeidel(A, b, 1e-6, 100);
        if (x != null) {
            System.out.println("Solución por Gauss-Seidel:");
            for (int i = 0; i < x.length; i++) {
                System.out.printf("x%d = %.6f%n", i + 1, x[i]);
            }
        }
    }
}
```

---

## 4. Jacobi

```java
public class Jacobi {
    public static double[] jacobi(double[][] A, double[] b, double tol, int maxIter) {
        int n = b.length;
        double[] x = new double[n];
        double[] xOld = new double[n];
        for (int iter = 0; iter < maxIter; iter++) {
            for (int i = 0; i < n; i++) {
                xOld[i] = x[i];
            }
            for (int i = 0; i < n; i++) {
                double sum = b[i];
                for (int j = 0; j < n; j++) {
                    if (j != i) {
                        sum -= A[i][j] * xOld[j];
                    }
                }
                if (A[i][i] == 0) {
                    System.out.println("División por cero en diagonal");
                    return null;
                }
                x[i] = sum / A[i][i];
            }
            double maxDiff = 0;
            for (int i = 0; i < n; i++) {
                maxDiff = Math.max(maxDiff, Math.abs(x[i] - xOld[i]));
            }
            if (maxDiff < tol) {
                return x;
            }
        }
        System.out.println("No convergió en el máximo de iteraciones");
        return x;
    }

    public static void main(String[] args) {
        double[][] A = {{3, 1, 1}, {1, 4, -1}, {1, -1, 5}};
        double[] b = {5, 6, 7};
        double[] x = jacobi(A, b, 1e-6, 100);
        if (x != null) {
            System.out.println("Solución por Jacobi:");
            for (int i = 0; i < x.length; i++) {
                System.out.printf("x%d = %.6f%n", i + 1, x[i]);
            }
        }
    }
}
```
