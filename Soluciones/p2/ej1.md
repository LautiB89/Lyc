### a) Vi <- k
Asumo Vi = 0 o fresca

    Vi <- Vi + 1    \
    .                |
    .                 > k veces
    .                |
    Vi <- Vi + 1    /
    
### Vi <- Vj + k
Asumo Vi = 0 o fresca y la etiqueta A fresca  
Primer intento es destructivo con Vj

        Vi <- k         (del punto anterior)
        IF Vj = 0  GOTO E
    A   Vi <- Vi + 1
        Vj <- Vj - 1
        IF Vj != 0 GOTO A

Segundo intento no destructivo

        Vi <- k             (del punto anterior)
        Z2 <- Z2 + 1        |
        IF Vj != 0 GOTO B   Expansión de
        IF Z2 != 0 GOTO E   if Vj=0 goto E
    B   Z2 <- Z2 - 1        |
    A1  Z1 <- Z1 + 1
        Vi <- Vi + 1
        Vj <- Vj - 1
        IF Vj != 0 GOTO A1
    A2  Vj <- Vj + 1
        Z1 <- Z1 - 1
        IF Z1 != 0 GOTO A2
    

### IF Vi = 0 GOTO L
Asumo Zi fresca y la etiqueta A fresca

        Zi <- Zi + 1
        IF Vi != 0 GOTO A  
        IF Zi != 0 GOTO L
    A   Zi <- Zi - 1
    
### GOTO L
Asumo Zi fresca

    Zi <- Zi + 1
    IF Zi != GOTO L
    
### b) 2 programas que calculan f(x1,x2) = x1 + x2
Primer intento:

        Y  <- X2
        Z1 <- X1
        IF Z1 = 0 GOTO E
    B   Y  <- Y + 1
        Z1 <- Z1 - 1
        IF Z1 != 0 GOTO B
    
Expansión:

        Z2 <- Z2 + 1        |
        IF X2 != 0 GOTO B2  |
        IF Z2 != 0 GOTO E   |
    B2  Z2 <- Z2 - 1        |
    A1  Z1 <- Z1 + 1        | Y <- X2
        Y <- Y + 1          |
        X2 <- X2 - 1        |
        IF X2 != 0 GOTO A1  |
    A2  X2 <- X2 + 1        |
        Z1 <- Z1 - 1        |
        IF Z1 != 0 GOTO A2  |

        Z2 <- Z2 + 1        |
        IF X1 != 0 GOTO B3  |
        IF Z2 != 0 GOTO E   |
    B3  Z2 <- Z2 - 1        |
    A3  Z3 <- Z3 + 1        | Z1 <- X1
        Z1 <- Z1 + 1        |
        X1 <- X1 - 1        |
        IF X1 != 0 GOTO A3  |
    A4  X1 <- X1 + 1        |
        Z3 <- Z3 - 1        |
        IF Z3 != 0 GOTO A4  |

        Z4 <- Z4 + 1        |
        IF Vi != 0 GOTO A5  | IF Z1 = 0 GOTO E
        IF Z4 != 0 GOTO E   |
    A5  Z4 <- Z4 - 1        |

    B1  Y  <- Y + 1
        Z1 <- Z1 - 1
        IF Z1 != 0 GOTO B1

La segunda forma de sumar queda como ejercicio para el lector (es trivial).  

### c)
- $\Psi_{P}^{(1)}(x_1) = x_1$
- $\Psi_{P}^{(2)}(x_1, x_2) = x_1 + x_2$
- $\Psi_{P}^{(3)}(x_1, x_2, x_3) = x_1 + x_2$
