# Ejercicio 5

# A

Voy a hacer un (pseudo)programa que compute para probar minimoNAp que es S-Parcial Computable

```txt
    Z1 <- Y
    
A1  IF p(X1, ..., Xn, Z1) GOTO B1
    Z1 <- Z1 + 1
    IF Z1 != Z2 GOTO A1

B1  Y <- Z1
```

## B

Puedo definir $f^{-1}(x)= \text{minimoNA}_p (x, 0)$  
Donde $p(x,y)= (f(x)=y)$  
Por el item anterior $f^{-1}$ es S-Parcial Computable y como es total $\implies$ es S-Computable.  

f(x)
