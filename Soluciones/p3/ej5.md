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
