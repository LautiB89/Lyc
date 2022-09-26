# Ejercicio 2

Idea general de la reducción:
Partimos con una función (f) que sabemos que no es computable, queremos probar que g tampoco lo es.
- Suponemos f computable
- Vemos como podemos escribir g en función de f
- Escribimos un programa que use el paso anterior
- Hacemos el $\Psi$ del programa de g igual a la reducción con el $\Psi$ del programa de f
- Reemplazamos el $\Psi$ con f, deberia quedar la reducción que hicimos antes
- Reemplazamos la reducción con g.
- Por transitividad de igualdad nos quedó que $\Psi_f$ es igual a g, que no es computable. Absurdo

## A)

$$
g_1(x, y)=
\begin{cases}
1 &\text{si } \Phi_{x}(y)\uparrow \\
0 &\text{si no} \\
\end{cases}
$$

Podemos hacer una reducción a f1 (ej1) : $f_1(x, y) = 1 - g_1(x,y)$

Supongo g1 computable, existe un programa Q1 que la computa. Llamo Q1' al siguiente programa:

```txt
    Q1
    Y <- 1 - Y
```

Por inspección:

$\Psi_{Q1'}^{(1)}(x,y)=1-\Psi_{Q1}^{(1)}(x,y)=1-g_1(x,y)=f_1(x,y)$

Por transitividad nos queda que:

$\Psi_{Q1'}^{(1)}(x,y)=f_1(x,y)$

Absurdo ya que f1 no es computable. Surge de suponer que g1 era computable.

## B)

$$g_2(x, y, z, w)=
\begin{cases}
1 &\text{si } \Phi_{x}^{(1)}(z)\downarrow \land\ \Phi_{y}^{(1)}(w)\downarrow \land\ \Phi_{x}^{(1)}(z) > \Phi_{y}^{(1)}(w) \\
0 &\text{si no} \\
\end{cases}$$

Sea k el numero del programa que computa la función identidad (sabemos que existe ya que Id es p.r.). La reducción se puede hacer con f3 del ej1:

$$f_3(x,y,z)=g_2(x,k,y,z)=
\begin{cases}
1 &\text{si } \Phi_{x}^{(1)}(y)\downarrow \land\ \Phi_{k}^{(1)}(z)\downarrow \land\ \Phi_{x}^{(1)}(y) > \Phi_{k}^{(1)}(z) \\
0 &\text{si no} \\
\end{cases}$$

Como la función identidad es total: $\Phi_{k}^{(1)}(z)\downarrow, \forall z$ y ademas es igual a z, entonces

$$f_3(x,y,z)=g_2(x,k,y,z)=
\begin{cases}
1 &\text{si } \Phi_{x}^{(1)}(y)\downarrow \land\ \Phi_{x}^{(1)}(y) > z \\
0 &\text{si no} \\
\end{cases}$$

Falta probar que es una reducción válida, para eso suponemos g2 computable y Q2 el programa que la computa, definimos el programa Q2' como:

```txt
    X4 <- X3
    X3 <- X2
    X2 <- K
    Q2
```

Por inspección vemos que:

$$\Psi_{Q2'}^{(3)}(x,y,z)=\Psi_{Q2}^{(4)}(x,k,y,z)= g_2(x,k,y,z)=f_3(x,y,z)$$

Pero por transitividad implica que $\Psi_{Q2'}^{(3)}(x,y,z)=f_3(x,y,z)$, lo cual es un absurdo ya que f3 no es computable.

## C)

Reducción que encontré:

$$f_4(x)=g_3(x,x,x)\ \dot{-}\ x=
\begin{cases}
    (x+1)\ \dot{-}\ x &\text{si } \Phi_{x}^{(1)}(x)\downarrow \land\ \Phi_{x}^{(1)}(x) \neq x \\
    0\ \dot{-}\ x &\text{si no}
\end{cases}$$

Resolviendo cada caso:

$$f_4(x)=g_3(x,x,x)\ \dot{-}\ x=
\begin{cases}
    1 &\text{si } \Phi_{x}^{(1)}(x)\downarrow \land\ \Phi_{x}^{(1)}(x) \neq x \\
    0 &\text{si no}
\end{cases}$$

Falta ver que es una reducción válida:

Supongo g3 computable. Sea Q3 el programa que la computa y Q3' el siguiente programa:

```txt
    X2 <- X1
    X3 <- X1
    Q3
    Y  <- Y - X
```

Por inspección del programa se ve:

$$\Psi_{Q3'}^{(1)}(x)=\Psi_{Q3}^{(3)}(x,x,x)\ \dot{-}\ x= g_3(x,x,x)\ \dot{-}\ x=f_4(x)$$

Por transitividad:

$$\Psi_{Q3'}^{(1)}(x)=f_4(x)$$

Absurdo ya que f4 no es computable.

## D)

**Todo**