# Métodos Seudocódigo 

---

## 1. Método de Un Paso 

```pseudocode
FUNCIÓN f(x, y)
    RETORNAR -2 * x * y
FIN FUNCIÓN

ALGORITMO MetodoUnPaso(x0, y0, xf, h)
    n ← ENTERO((xf - x0) / h) + 1
    x ← vector de tamaño n
    y ← vector de tamaño n
    x[1] ← x0
    y[1] ← y0
    PARA i DESDE 1 HASTA n-1 HACER
        x[i+1] ← x[i] + h
        y[i+1] ← y[i] + h * f(x[i], y[i])
    FIN PARA
    RETORNAR y
FIN ALGORITMO

// Ejemplo de uso
x0 ← 0
y0 ← 1
xf ← 1
h ← 0.1
IMPRIMIR "Método de Un Paso (Euler Explícito):"
PARA i DESDE 1 HASTA n HACER
    IMPRIMIR "x=", x0 + (i-1) * h, ", y=", MetodoUnPaso(x0, y0, xf, h)[i]
FIN PARA
```

---

## 2. Método de Paso Múltiple 

```pseudocode
FUNCIÓN f(x, y)
    RETORNAR -2 * x * y
FIN FUNCIÓN

ALGORITMO MetodoAdamsBashforth(x0, y0, xf, h)
    n ← ENTERO((xf - x0) / h) + 1
    x ← vector de tamaño n
    y ← vector de tamaño n
    x[1] ← x0
    y[1] ← y0
    // Primer paso con Euler
    x[2] ← x0 + h
    y[2] ← y[1] + h * f(x[1], y[1])
    // Adams-Bashforth de 2 pasos
    PARA i DESDE 2 HASTA n-1 HACER
        x[i+1] ← x[i] + h
        y[i+1] ← y[i] + h / 2 * (3 * f(x[i], y[i]) - f(x[i-1], y[i-1]))
    FIN PARA
    RETORNAR y
FIN ALGORITMO

// Ejemplo de uso
x0 ← 0
y0 ← 1
xf ← 1
h ← 0.1
IMPRIMIR "Método de Paso Múltiple (Adams-Bashforth 2 pasos):"
PARA i DESDE 1 HASTA n HACER
    IMPRIMIR "x=", x0 + (i-1) * h, ", y=", MetodoAdamsBashforth(x0, y0, xf, h)[i]
FIN PARA
```

---

## 3. Método de Euler

```pseudocode
FUNCIÓN f(x, y)
    RETORNAR -2 * x * y
FIN FUNCIÓN

ALGORITMO MetodoEuler(x0, y0, xf, h)
    n ← ENTERO((xf - x0) / h) + 1
    x ← vector de tamaño n
    y ← vector de tamaño n
    x[1] ← x0
    y[1] ← y0
    PARA i DESDE 1 HASTA n-1 HACER
        x[i+1] ← x[i] + h
        y[i+1] ← y[i] + h * f(x[i], y[i])
    FIN PARA
    RETORNAR y
FIN ALGORITMO

// Ejemplo de uso
x0 ← 0
y0 ← 1
xf ← 1
h ← 0.1
IMPRIMIR "Método de Euler:"
PARA i DESDE 1 HASTA n HACER
    IMPRIMIR "x=", x0 + (i-1) * h, ", y=", MetodoEuler(x0, y0, xf, h)[i]
FIN PARA
```

---

## 4. Método de Runge-Kutta 

```pseudocode
FUNCIÓN f(x, y)
    RETORNAR -2 * x * y
FIN FUNCIÓN

ALGORITMO MetodoRungeKutta(x0, y0, xf, h)
    n ← ENTERO((xf - x0) / h) + 1
    x ← vector de tamaño n
    y ← vector de tamaño n
    x[1] ← x0
    y[1] ← y0
    PARA i DESDE 1 HASTA n-1 HACER
        x[i+1] ← x[i] + h
        k1 ← f(x[i], y[i])
        k2 ← f(x[i] + h/2, y[i] + h * k1 / 2)
        k3 ← f(x[i] + h/2, y[i] + h * k2 / 2)
        k4 ← f(x[i] + h, y[i] + h * k3)
        y[i+1] ← y[i] + h / 6 * (k1 + 2 * k2 + 2 * k3 + k4)
    FIN PARA
    RETORNAR y
FIN ALGORITMO

// Ejemplo de uso
x0 ← 0
y0 ← 1
xf ← 1
h ← 0.1
IMPRIMIR "Método de Runge-Kutta (Orden 4):"
PARA i DESDE 1 HASTA n HACER
    IMPRIMIR "x=", x0 + (i-1) * h, ", y=", MetodoRungeKutta(x0, y0, xf, h)[i]
FIN PARA
```

---

## 5. Método de Taylor 

```pseudocode
FUNCIÓN f(x, y)
    RETORNAR -2 * x * y
FIN FUNCIÓN

FUNCIÓN df(x, y)
    RETORNAR -2 * y + 4 * x^2 * y
FIN FUNCIÓN

ALGORITMO MetodoTaylor(x0, y0, xf, h)
    n ← ENTERO((xf - x0) / h) + 1
    x ← vector de tamaño n
    y ← vector de tamaño n
    x[1] ← x0
    y[1] ← y0
    PARA i DESDE 1 HASTA n-1 HACER
        x[i+1] ← x[i] + h
        f1 ← f(x[i], y[i])
        f2 ← df(x[i], y[i])
        y[i+1] ← y[i] + h * f1 + (h^2 / 2) * f2
    FIN PARA
    RETORNAR y
FIN ALGORITMO

// Ejemplo de uso
x0 ← 0
y0 ← 1
xf ← 1
h ← 0.1
IMPRIMIR "Método de Taylor (Orden 2):"
PARA i DESDE 1 HASTA n HACER
    IMPRIMIR "x=", x0 + (i-1) * h, ", y=", MetodoTaylor(x0, y0, xf, h)[i]
FIN PARA
```
