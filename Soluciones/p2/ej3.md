# Ejercicio 3

# A

Demostrar que todo programa P tiene un programa autocontenido P' equivalente.  
(P y P' son programas equivalentes si $\Psi_{P}^{(n)} = \Psi_{P'}^{(n)} \  ∀ n \geq 1$).

Sea el programa P = [#(I1), ..., #(In)], puedo definir:

$$
P' = P * \prod⟨\#(L), 0⟩
$$

Donde la productoria multiplica una vez por cada etiqueta que no esté definida.  
De esta forma, nunca hacemos ningun cambio a nuestras variables (hacemos Y ← Y muchas veces).

# B

Sean P y Q dos programas autocontenidos con etiquetas disjuntas y sea $r : \mathbb N^n → \{0, 1\}$ un
predicado primitivo recursivo.  
Definir macros para las siguientes pseudo-instrucciones (con su
interpretación natural):

- IF r(V1 , . . . , Vn ) GOTO L

```txt
    Z1 <- r(V1, ..., Vn)
    IF Z1 != 0 GOTO A1
    GOTO L
A1  Z1 <- 0
```

- IF r(V1 , . . . , Vn ) THEN P ELSE Q

```txt
    Z1 <- r(V1, ..., Vn)
    IF Z1 != 0 GOTO A1

A1  P (primera linea)
    ... todo el codigo de P
    GOTO E

A2  Q (primera linea)
    ... todo el codigo de Q

E   Z1 <- 0

```

- WHILE r(V1 , . . . , Vn ) P

```txt
A1  Z1 <- r(V1, ..., Vn)
    IF Z1 = 0 GOTO A2

    P

    GOTO A1
A2  Z1 <- 0
```

# C

$$
f(x) = \begin{cases}
1   &\text{si }x=3 \\
↑ &\text{en otro caso}
\end{cases}
\hspace{15pt}\text{y}\hspace{15pt}
g(x)=2x
\\
h(x) = \begin{cases}
f(x)   &\text{si }x\geq5 ∨ x=3 \\
g(x) &\text{en otro caso}
\end{cases}
$$

Mostrar que h(x) es S-Parcial Computable:

Sabemos que:  
Existe un programa G que computa g(x) ya que g es una función pr.  
Como f(x) no es total, no puede ser pr. Esto implica que todavía no sabemos si es computable, muestro que existe un programa en S que lo computa para mostrarlo.  
Llamo F al programa que computa f(x):

```txt
A1  IF X1 != 3 GOTO A1
    Y <- 1
```

Como existen programas F y G que computan f(x) y g(x), sabemos por el item a que existen F' y G' programas autocontenidos y con etiquetas disjuntas.  
Como $r(x)=(x\geq5 \lor x=3)$ y su negación son composición de pr, entonces r es pr.  
Finalmente, existe un programa que computa h(x) definido como una de las macros del item b:

```txt
    IF r(X1) THEN F' ELSE Q'
```
