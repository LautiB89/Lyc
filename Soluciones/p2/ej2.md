## Ej2
### Item A
$C_s$ es la clase de funciones S-parciales computables:  
Existe un programa P tq:  
$$
f(r1, ..., rm) = \Psi_P^{m}(r_1, ..., r_m)
$$

Como el conjunto PR es la más chica de las clases PRC, si PR está contenida en Cs entonces Cs es PRC.

Para probar Cs es PRC basta ver que para todas las funciones en PR existe un programa P tal que su $\Psi$ es el resultado de la función.

### Inducción estructural

Casos base:  

- s(x) se computa con Y <- X + 1 (del ej 2)
- n(x) se computa con Y <- 0
- u(x_n) se computa con Y <- Xi + 0 (del ej 2)

Para los tres existe un programa tal que su PSI es igual a la función.  

### Paso inductivo:  

Quiero ver que cualquier función en PR que puedo formar a partir de otras funciones en PR (computables) tambien es computable. Puedo formar funciones a partir de otras usando composición o recursión primitiva. 

Composición:  
Sea $f(x1, ..., xn) = h(g1(x1, ..., xn), ..., gk(x1, ..., xn))$ con g y h computables por los programas G y H  
El programa F:

```txt
Z1 <- G1
...
Zk <- Gk
Y <- 0
H
```

Computa f  

Recursión primitiva:
Sea 
$$
f(x1, ..., xn, 0)   =  h(x1, ..., xn) \\
f(x1, ..., xn, t+1) =  g( f(x1, ..., xn,t), x1, ..., xn, t)
$$

Con H y G los programas que computan cada función
Entonces:


        H
        IF X(n+1) = 0 GOTO E
        Z2 <- X(n+1)
        Xn+2 <- 0

    A   Xn+2 <- X(n+2) + 1
        Xn+1 <- Xn
        Xn   <- X(n-1)
        ...
        X2   <- X1
        X1   <- Y
        G
        Z2 <- Z2 - 1
        IF Z2 != 0 GOTO A

### B)

Una función es S-Computable si es Parcial Computable y Total.  
Como sabemos que la función $*(x,y) = x ⋅ y$ es pr, podemos afirmar que está dentro de la clase PRC más chica y esta es un subconjunto de todas las clases PRC.  
Entonces la función \* es S-Computable al estar en Cs por ser Cs subconjunto de PR y por ser total.  

### C)

Toda función primitiva recursiva (pr) es Total.  
Todas las funciones pr estan en Cs (son S-Parciales Computables).  
Usando las dos proposiciones anteriores podemos ver que se implica que todas las funciones pr son S-Computables, ya que son totales (por ser pr) y son Parciales Computables (por estar en PR $\subset$ Cs).
