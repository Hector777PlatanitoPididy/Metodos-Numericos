# Métodos Seudocódigo

---

## 1. Eliminación Gaussiana

```pseudocode
ALGORITMO EliminacionGaussiana(A, b, n)
    // Crear matriz aumentada [A|b]
    augmented ← matriz n x (n+1)
    PARA i DESDE 1 HASTA n HACER
        PARA j DESDE 1 HASTA n HACER
            augmented[i][j] ← A[i][j]
        FIN PARA
        augmented[i][n+1] ← b[i]
    FIN PARA

    // Eliminación hacia adelante
    PARA i DESDE 1 HASTA n-1 HACER
        SI augmented[i][i] = 0 ENTONCES
            IMPRIMIR "Pivote cero detectado"
            RETORNAR NULL
        FIN SI
        PARA k DESDE i+1 HASTA n HACER
            factor ← augmented[k][i] / augmented[i][i]
            PARA j DESDE i HASTA n+1 HACER
                augmented[k][j] ← augmented[k][j] - factor * augmented[i][j]
            FIN PARA
        FIN PARA
    FIN PARA

    // Sustitución hacia atrás
    x ← vector de tamaño n
    PARA i DESDE n HASTA 1 HACER
        SI augmented[i][i] = 0 ENTONCES
            IMPRIMIR "Sistema no tiene solución única"
            RETORNAR NULL
        FIN SI
        x[i] ← augmented[i][n+1] / augmented[i][i]
        PARA k DESDE i-1 HASTA 1 HACER
            augmented[k][n+1] ← augmented[k][n+1] - augmented[k][i] * x[i]
        FIN PARA
    FIN PARA
    RETORNAR x
FIN ALGORITMO

// Ejemplo de uso
A ← [[3, 1, 1], [1, 4, -1], [1, -1, 5]]
b ← [5, 6, 7]
IMPRIMIR EliminacionGaussiana(A, b, 3)
```

---

## 2. Gauss-Jordan

```pseudocode
ALGORITMO GaussJordan(A, b, n)
    // Crear matriz aumentada [A|b]
    augmented ← matriz n x (n+1)
    PARA i DESDE 1 HASTA n HACER
        PARA j DESDE 1 HASTA n HACER
            augmented[i][j] ← A[i][j]
        FIN PARA
        augmented[i][n+1] ← b[i]
    FIN PARA

    // Eliminación completa
    PARA i DESDE 1 HASTA n HACER
        SI augmented[i][i] = 0 ENTONCES
            IMPRIMIR "Pivote cero detectado"
            RETORNAR NULL
        FIN SI
        pivote ← augmented[i][i]
        PARA j DESDE 1 HASTA n+1 HACER
            augmented[i][j] ← augmented[i][j] / pivote
        FIN PARA
        PARA k DESDE 1 HASTA n HACER
            SI k ≠ i ENTONCES
                factor ← augmented[k][i]
                PARA j DESDE 1 HASTA n+1 HACER
                    augmented[k][j] ← augmented[k][j] - factor * augmented[i][j]
                FIN PARA
            FIN SI
        FIN PARA
    FIN PARA

    // Extraer solución
    x ← vector de tamaño n
    PARA i DESDE 1 HASTA n HACER
        x[i] ← augmented[i][n+1]
    FIN PARA
    RETORNAR x
FIN ALGORITMO

// Ejemplo de uso
A ← [[3, 1, 1], [1, 4, -1], [1, -1, 5]]
b ← [5, 6, 7]
IMPRIMIR GaussJordan(A, b, 3)
```

---

## 3. Gauss-Seidel

```pseudocode
ALGORITMO GaussSeidel(A, b, n, tol, maxIter)
    x ← vector de ceros de tamaño n
    xOld ← vector de ceros de tamaño n
    PARA iter DESDE 1 HASTA maxIter HACER
        PARA i DESDE 1 HASTA n HACER
            xOld[i] ← x[i]
            suma ← b[i]
            PARA j DESDE 1 HASTA n HACER
                SI j ≠ i ENTONCES
                    suma ← suma - A[i][j] * x[j]
                FIN SI
            FIN PARA
            SI A[i][i] = 0 ENTONCES
                IMPRIMIR "División por cero en diagonal"
                RETORNAR NULL
            FIN SI
            x[i] ← suma / A[i][i]
        FIN PARA
        maxDiff ← 0
        PARA i DESDE 1 HASTA n HACER
            maxDiff ← MÁXIMO(maxDiff, |x[i] - xOld[i]|)
        FIN PARA
        SI maxDiff < tol ENTONCES
            RETORNAR x
        FIN SI
    FIN PARA
    IMPRIMIR "No convergió en el máximo de iteraciones"
    RETORNAR x
FIN ALGORITMO

// Ejemplo de uso
A ← [[3, 1, 1], [1, 4, -1], [1, -1, 5]]
b ← [5, 6, 7]
IMPRIMIR GaussSeidel(A, b, 3, 10^-6, 100)
```

---

## 4. Jacobi

```pseudocode
ALGORITMO Jacobi(A, b, n, tol, maxIter)
    x ← vector de ceros de tamaño n
    xOld ← vector de ceros de tamaño n
    PARA iter DESDE 1 HASTA maxIter HACER
        PARA i DESDE 1 HASTA n HACER
            xOld[i] ← x[i]
        FIN PARA
        PARA i DESDE 1 HASTA n HACER
            suma ← b[i]
            PARA j DESDE 1 HASTA n HACER
                SI j ≠ i ENTONCES
                    suma ← suma - A[i][j] * xOld[j]
                FIN SI
            FIN PARA
            SI A[i][i] = 0 ENTONCES
                IMPRIMIR "División por cero en diagonal"
                RETORNAR NULL
            FIN SI
            x[i] ← suma / A[i][i]
        FIN PARA
        maxDiff ← 0
        PARA i DESDE 1 HASTA n HACER
            maxDiff ← MÁXIMO(maxDiff, |x[i] - xOld[i]|)
        FIN PARA
        SI maxDiff < tol ENTONCES
            RETORNAR x
        FIN SI
    FIN PARA
    IMPRIMIR "No convergió en el máximo de iteraciones"
    RETORNAR x
FIN ALGORITMO

// Ejemplo de uso
A ← [[3, 1, 1], [1, 4, -1], [1, -1, 5]]
b ← [5, 6, 7]
IMPRIMIR Jacobi(A, b, 3, 10^-6, 100)
```
