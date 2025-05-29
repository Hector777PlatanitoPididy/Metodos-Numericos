# Seudocódigo de Ejemplos de Errores Numéricos

---

## 🔹 1. Error de Truncamiento

**Descripción:** Se usa una fórmula de diferencias finitas para derivada.

```
Inicio
    Definir h = 0.1
    Definir x = 1.0

    derivadaAprox ← (sen(x + h) - sen(x)) / h
    derivadaExacta ← cos(x)

    errorTruncamiento ← valor absoluto de (derivadaExacta - derivadaAprox)

    Imprimir derivadaAprox, derivadaExacta, errorTruncamiento
Fin
```

---

## 🔹 2. Error de Redondeo

**Descripción:** Suma repetida de un número muy pequeño.

```
Inicio
    suma ← 0.0

    Repetir 1,000,000 veces:
        suma ← suma + 1e-10

    Imprimir "Suma esperada: 0.1"
    Imprimir "Suma real:", suma
Fin
```

---

## 🔹 3. Error Absoluto y Relativo

**Descripción:** Se compara un valor aproximado con el valor real.

```
Inicio
    valorReal ← π
    valorAprox ← 3.14

    errorAbsoluto ← valor absoluto de (valorReal - valorAprox)
    errorRelativo ← errorAbsoluto / valor absoluto de (valorReal)

    Imprimir errorAbsoluto, errorRelativo
Fin
```

---

## 🔹 4. Error de Cancelación

**Descripción:** Resta de números muy cercanos.

```
Inicio
    a ← 1.0000001
    b ← 1.0000000

    resultado ← a - b

    Imprimir "Resultado esperado: 0.0000001"
    Imprimir "Resultado real:", resultado
Fin
```

---

## 🔹 5. Error por Criterio de Parada Inadecuado

**Descripción:** Método de Newton-Raphson sin criterio de error, solo límite de iteraciones.

```
Inicio
    x ← 1.0
    iteraciones ← 0

    Mientras iteraciones < 1000 hacer:
        fx ← x^2 - 2
        dfx ← 2 * x

        x ← x - fx / dfx
        iteraciones ← iteraciones + 1

    Imprimir "Raíz aproximada:", x
Fin
```

---
