# Ejercicio 5

## A)

$$
g_1(x)=
\begin{cases}
    1 &\text{si HALT}(1337,x) \\
    0 &\text{si no}
\end{cases}
\hspace{10pt}
\text{HALT}(x,y)=
\begin{cases}
    1 &\text{si } \Phi_{y}^{(1)}(x)\downarrow \\
    0 &\text{si no}
\end{cases}
$$

Voy a convertirlo a f1 del ej 1 y despues en otra f1(x,x) que es mas facil:

tomo e una cte que voy a definir despues. Hago el $S_{1}^{1}(u, e)$...

Reduzco a

$$
f_1(x,y)=
\begin{cases}
    1 &\text{si } \Phi_{x}^{(1)}(y)\downarrow \\
    0 &\text{si no}
\end{cases}
$$

Para esto primero reescribo g1 usando la definición de HALT:

$$
g_1(x)=
\begin{cases}
    1 &\text{si }\Phi_{x}^{(1)}(1337)\downarrow \\
    0 &\text{si no}
\end{cases}
$$

Vemos que ahora son muy parecidas. Necesitamos darle a g1 el numero de un programa que usa la X2 y X3 para ejecutar algo parecido a f1, lo construimos usando la S del teorema del párametro.

$$
g_1(S_1^2(u,v,e))
=
\begin{cases}
    1 &\text{si }\Phi_{S_1^2(u,v,e)}^{(1)}(1337)\downarrow \\
    0 &\text{si no}
\end{cases} \\
=
\begin{cases}
    1 &\text{si }\Phi_{e}^{(3)}(1337, u, v)\downarrow\\
    0 &\text{si no}
\end{cases}
=
\begin{cases}
    1 &\text{si }\Phi_{u}^{(1)}(v)\downarrow \\
    0 &\text{si no}
\end{cases}=f_1(u,v)
$$

Si g1 es computable y Q1 es su programa entonces puedo hacer un programa P1 con numero e cuya salida es el resultado de ignorar la primera variable y usar las siguientes dos para "ejecutar" f1:

```txt
    Z1 <- X2
    Z2 <- X3
    Y  <- U_n(Z1, Z2)
```

Si el numero de este programa es e, podemos construir el numero de otro programa que hardcodea X2 y X3 adentro del codigo y podemos hacer lo que queríamos

$$\Phi_{e}^{(3)}(x, u, v) = \Phi_{S_1^2(u,v,e)}^{(1)}(x)$$

Ademas vemos por inspección que:

$$\Phi_{u}^{(1)}(v)\downarrow \iff \Phi_{e}^{(3)}(x, u, v)\downarrow \iff \Phi_{S_1^2(u,v,e)}^{(1)}(x) \downarrow$$

g1 es una función que toma el numero de un programa y te dice si este termina o no con una entrada fija 1337. La idea es aprovechar que toma el numero de un programa y mostrar que adentro del numero de un programa podemos codificar variables extra, que nosotros decidimos sus valores (teo parametro).

De esta forma usando una función que nos dice si un programa x termina para cierta entrada, podemos ver si un programa u termina para cualquier entrada v dada. En este numero de programa vamos a querer agregar dos variables para hacer la reducción a f1 del ej1, asi que primero hacemos el programa que copia el comportamiento de $\Phi_{x2}^{(1)}(x3)$ y conseguimos su numero de programa.

Despues usamos ese numero y la función $S_1^2$ para transformar este programa de 3 variables a uno de 1 variable con las otras dos fijas dentro del codigo. Como S es pr y nuestro programa de recien existe, nada nos impide en darle este programa como entrada a g1.

Construyo programa P tq $\Psi_{P}^{(3)}(x1,x2,x3)=\Phi_{x2}^{(1)}(x3)$ (ignoramos la primera variable)

```txt
    Y <- Phi_X2(X3)
```

Como pudimos escribir el programa, podemos saber su numero y lo llamamos e = #(P).

Por teo del parametro hay una función p.r. tq

$$
\Phi_{e}^{(3)}(x_1,x_2,x_3)
=
\Phi_{S_1^{2}(x_2,x_3,e)}^{(1)}(x_1)
$$

Por transitividad de la igualdad vemos que

$$
\Phi_{S_1^{2}(x_2,x_3,e)}^{(1)}(x_1)
=
\Phi_{x2}^{(1)}(x3)
$$

Ahora podemos componer esta función con g1.

Supongo g1 computable y Q1 el programa que la computa, entonces puedo pasarle el numero del programa que acabo de construir.

$$
g_1(S_1^2(u,v,e))
=
\begin{cases}
    1 &\text{si }\Phi_{S_1^2(u,v,e)}^{(1)}(1337)\downarrow \\
    0 &\text{si no}
\end{cases} \\
=
\begin{cases}
    1 &\text{si }\Phi_{u}^{(1)}(v)\downarrow \\
    0 &\text{si no}
\end{cases}=f_1(u,v)
$$

Pero si

- e es un numero de programa valido (existe xq lo escribí)
- S es pr $\implies$ S es computable
- g1 es computable

Esto implica que la composición $g_1 \circ S$ es computable, lo cual es un absurdo ya que $g_1 \circ S = f_1$ que **no es computable**.

## B)

$$
g_2(x,y,z)=
\begin{cases}
    1 &\text{si }
    \Phi_{x}^{(1)}(z)\downarrow \land\
    \Phi_{y}^{(1)}(z)\downarrow \land\
    \Phi_{x}^{(1)}(z) > \Phi_{y}^{(1)}(z) \\
    0 &\text{si no}
\end{cases}
$$

Primero evalúo y en $i = \#(Id)$

$$
g_2(x,i,z)=
\begin{cases}
    1 &\text{si }
    \Phi_{x}^{(1)}(z)\downarrow \land\
    \Phi_{x}^{(1)}(z) > z \\
    0 &\text{si no}
\end{cases}
$$

Ahora defino un programa que recibe tres variables (x1,x2,x3) (ignora la primera) y computa $\Phi_{x_2}^{(1)}(x_3)$. Llamo P a este programa y e a su número.

```txt
    Y <- Phi_X2(X3)
```

Por el teorema del parámetro $\Phi_{e}^{(3)}(z,x,y)=\Phi_{S_1^2(x,y,e)}^{1}(z)$ que por inspección del programa y transitividad nos queda:

$$\Phi_{S_1^2(x,y,e)}^{1}(z) = \Phi_{x}^{(1)}(y)$$

Finalmente hago la reducción usando esta S:

Supongo g2 computable.

$$
g_2(S_1^2(x,y,e), i, z) =
\begin{cases}
    1 &\text{si } \Phi_{S_1^2(x,y,e)}^{(1)}(z)\downarrow \land\ \Phi_{S_1^2(x,y,e)}^{(1)}(z) > x \\
    0 &\text{si no}
\end{cases}=\\
\begin{cases}
    1 &\text{si } \Phi_{x}^{(1)}(y)\downarrow \land\ \Phi_{x}^{(1)}(y) > z \\
    0 &\text{si no}
\end{cases} = f_3(x,y,z)
$$

Entonces la composición g2 y S es computable.

Absurdo ya que la composición da una f que no es computable.

## C)

$$
g_3(x)=
\begin{cases}
    13 &\text{si } \Phi_{x}^{(1)} \text{ es la constante }7 \\
    0 &\text{si no}
\end{cases}
$$

Hago un programa que cumple que es la constante 7 pero que solo termina sii $\Phi_{x_2}^{(1)}(x_2)\downarrow$, lo llamo P3.

```txt
    Z1 <- Phi_X2(X2)
    Y  <- 7
```

Por inspección de P3: $\Psi_{P3}^{(2)}(x_1,x_2)$ es cte 7 $\iff \Phi_{x_2}^{(1)}(x_2)\downarrow$

Sea e = #(P3), puedo usar el teorema del parametro para fijar x2 y tener el numero de un programa nuevo en función de x2.

$$\Phi_{e}^{(2)}(x_1,x_2) = \Psi_{S_1^1(x_2,e)}^{(1)}(x_1)$$

Supongo g3 computable. Sabiendo que $S_1^1$ es pr (entonces computable) puedo componerlas para formar algo computable:

$$
g_3(S_1^1(x_2,e)) =
\begin{cases}
    13 &\text{si } \Phi_{S_1^1(x_2,e)}^{(1)} \text{ es la constante }7 \\
    0 &\text{si no}
\end{cases} \\
=\begin{cases}
    13 &\text{si } \Phi_{e}^{(2)} \text{ es la constante }7 \\
    0 &\text{si no}
\end{cases}
=\begin{cases}
    13 &\text{si } \Phi_{x_2}^{(1)}(x_2)\downarrow \\
    0 &\text{si no}
\end{cases}
$$

Absurdo, ya que la ultima función es una que sabemos que no es computable.

## D)

$$
g_4(x,y)=
\begin{cases}
    1 &\text{si } \Phi_{x}^{(1)}(y)\downarrow \land\ \Phi_{y}^{(1)}(x)\downarrow \land\ \Phi_{x}^{(1)}(y) \neq \Phi_{y}^{(1)}(x) \\
    0 &\text{si no}
\end{cases}
$$

Voy a reducir g4 para llegar a f4 del ejercicio 1.

Quiero meter en x el numero de un programa que toma otra variable (una mas) y que computa $\Phi_{x_2}^{(1)}(x_2)$. Defino el programa P4 como:

```txt
    Y <- Phi_X2(X2)
```

Sea e = #(P4) el numero de este programa. Por el teorema del parametro existe una $S_1^1$:

$$\Phi_{e}^{(2)}(x,y) = \Phi_{S_1^1(y,e)}^{(1)}(x)$$

Y como nuestro programa e computa $\Phi_{x_2}^{(1)}(x_2)$ nos queda que:

$$\Phi_{y}^{(1)}(y) = \Phi_{S_1^1(y,e)}^{(1)}(x)$$

Evaluando la x de g4 en $S_1^1(x,e)$:

$$
g_4(S_1^1(x,e),y)=
\begin{cases}
    1 &\text{si } \Phi_{S_1^1(x,e)}^{(1)}(y)\downarrow \land\ \Phi_{y}^{(1)}(S_1^1(x,e))\downarrow \land\ \Phi_{S_1^1(x,e)}^{(1)}(y) \neq \Phi_{y}^{(1)}(S_1^1(x,e))\downarrow \\
    0 &\text{si no}
\end{cases}
$$

Reemplazando $\Phi_{S_1^1(x,e)}^{(1)}(y)$ por $\Phi_{x}^{(1)}(x)$

$$
g_4(S_1^1(x,e),y)=
\begin{cases}
    1 &\text{si } \Phi_{x}^{(1)}(x)\downarrow \land\ \Phi_{y}^{(1)}(S_1^1(x,e))\downarrow \land\ \Phi_{x}^{(1)}(x) \neq \Phi_{y}^{(1)}(S_1^1(x,e))\downarrow \\
    0 &\text{si no}
\end{cases}
$$

Ahora tengo que ver que programa darle a y para que se cumpla $\Phi_{y}^{(1)}(S_1^1(x,e)) =x$, lo hago definiendo un programa que ignora la primera variable y devuelve siempre la segunda.

Defino un programa con numero k que cumple $\Phi_{k}^{(2)}(x_1,x_2) = x_2$

```txt
    Y <- X2
```

Ahora uso el teorema del parametro para encontrar una funcion p.r. $S_1^{1'}$ tal que
$\Phi_k^{(2)}(x,y)=\Phi_{S_1^{1'}(y,k)}^{(1)}(x)=y$

$$
g_4(S_1^1(x,e),S_1^{1'}(x,k))=\\
\begin{cases}
    1 &\text{si } \Phi_{x}^{(1)}(x)\downarrow \land\ \Phi_{S_1^{1'}(x,k)}^{(1)}(S_1^1(x,e))\downarrow \land\ \Phi_{x}^{(1)}(x) \neq \Phi_{S_1^{1'}(x,k)}^{(1)}(S_1^1(x,e))\\
    0 &\text{si no}
\end{cases} \\
= \begin{cases}
    1 &\text{si } \Phi_{x}^{(1)}(x)\downarrow \land\ \Phi_{x}^{(1)}(x) \neq x \\
    0 &\text{si no}
\end{cases}
$$

Para cerrar

- Tomo la primera variable como $S_1^1(x,e)$, ya que $\Phi_{S_1^1(x,e)}^{(1)}(y)=\Phi_{x}^{(1)}(x)$.
- Tomo la segunda variable como $S_1^{1'}(x,k)$, ya que $\Phi_{S_1^{1'}(x,k)}^{(1)}(y)=x$.

Supongo g4 computable, como las dos S son pr ($\implies$ computables) y la composicion es computable entonces la siguiente función es computable:

$$
\begin{cases}
    1 &\text{si } \Phi_{x}^{(1)}(x)\downarrow \land\ \Phi_{x}^{(1)}(x) \neq x \\
    0 &\text{si no}
\end{cases}
$$

Pero es la función f4 que ya probamos que no es computable en el ejercicio 1. Faltaría ver que la reducción es computable.
