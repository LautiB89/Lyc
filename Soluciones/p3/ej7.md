# Ejercicio 7

Probar que no son computables usando Teorema de la Recursión.

## h1

$$
h_1(x)=
\begin{cases}
    1 &\text{si } x \in \text{Im }\Phi_x^1 \\
    0 &\text{si no}
\end{cases}
$$

Supongo h1 computable y defino la siguiente función:

$$
g_1(x, y)=
\begin{cases}
    \uparrow &\text{si } h_1(x) \\
    x &\text{si no}
\end{cases}
$$

Observar que es igual a:

$$
g_1(x, y)=
\begin{cases}
    \uparrow &\text{si } x \in \text{Im }\Phi_x^1 \\
    x &\text{si no}
\end{cases}
$$

Como g1 está definida por composición de funciones computables (h1 incluida) y es parcial, es parcial computable. Puedo usar el teorema de la recursión.

Por TDR existe un programa con numero e tal que $\Phi_e^{(1)}(y)=g(e,y)$, veamos que implica:

$$
\Phi_e^{(1)}(y)=
\begin{cases}
    \uparrow &\text{si } e \in \text{Im }\Phi_e^1 \\
    e &\text{si no}
\end{cases}
$$

Acá llegamos a un absurdo:

Supongo $e \in \text{Im }\Phi_e^1$, entonces:

$e \in \text{Im }\Phi_e^1 \iff \Phi_e^{(1)}(y)\uparrow\ \forall y \iff \text{Im }\Phi_e^1 = \emptyset \iff e \not\in \text{Im }\Phi_e^1$

Supongo $e \not\in \text{Im }\Phi_e^1$, entonces:

$e \not\in \text{Im }\Phi_e^1 \iff \Phi_e^{(1)}(y) = e\ \forall y \iff e \in \text{Im }\Phi_e^1$

### Comentario de la función a elegir

No necesitaba que el programa se cuelgue, solo necesitaba que implique que e no esta en la imagen para todo y.

Tampoco necesitaba definir la segunda guarda como e, necesitaba que haya algun valor que devuelve e. Otra opción podría haber sido

$$
g_1(x, y)=
\begin{cases}
    0 &\text{si } x \in \text{Im }\Phi_x^1 \\
    y &\text{si no}
\end{cases}
$$

Que reemplazando nos queda:

$$
\Phi_e^{(1)}(y)=
\begin{cases}
    0 &\text{si } e \in \text{Im }\Phi_e^1 \\
    y &\text{si no}
\end{cases}
$$

Entonces el absurdo surge de que:

- En la primera guarda la imagen es 0, y el programa e no es vacio.
- En la segunda guarda se implica que existe un y = e tq Phi(e)=e entonces e SI pertenece a la imagen.

## h2

$$
h_2(x,y)=
\begin{cases}
    1 &\text{si } \Phi_x^{(1)}(y)\downarrow \land\ \Phi_x^{(1)}(y) > x \\
    0 &\text{si no}
\end{cases}
$$

Lo voy a llevar a un programa de una sola entrada (que es y) y quiero que

- el programa se cuelgue sii la nueva función no se cuelga (absurdo)
- el programa termina sii la nueva función se cuelga

La negación de la guarda es $\Phi_x^{(1)}(y)\uparrow \lor\ \Phi_x^{(1)}(y) \leq x$ asi que si el programa termina tambien quiero que contradiga la otra parte del or. Devuelvo una salida mayor a x. Finalmente defino:

$$
g_2(x,y)=
\begin{cases}
    \uparrow &\text{si } h_2(x,y)\\
    x+1&\text{si no}
\end{cases}
$$

Como g2 es una función parcial y composición de funciones computables (y una parcial computable) sabemos que es parcial computable.

Viendo la función h2 podemos ver que g2 es igual a:

$$
g_2(x,y)=
\begin{cases}
    \uparrow &\text{si } \Phi_x^{(1)}(y)\downarrow \land\ \Phi_x^{(1)}(y) > x \\
    x+1 &\text{si no}
\end{cases}
$$

Como g2 es parcial computable podemos usar el TDR sobre ella: existe un programa con numero e tal que $\Phi_e^{(1)}(y)=g_2(e,y)$, entonces

$$
\Phi_e^{(1)}(y)=
\begin{cases}
    \uparrow &\text{si } \Phi_e^{(1)}(y)\downarrow \land\ \Phi_e^{(1)}(y) > e \\
    e+1 &\text{si no}
\end{cases}
$$

Divido en dos casos distintos:

Supongo que $\Phi_e^{(1)}(y)\uparrow$:

$\Phi_e^{(1)}(y)\uparrow \iff \Phi_e^{(1)}(y)\downarrow \land\ \Phi_e^{(1)}(y) > e$

Supongo que $\Phi_e^{(1)}(y)\downarrow$:

$\Phi_e^{(1)}(y)\downarrow \iff \Phi_e^{(1)}(y) = e+1 \iff \Phi_e^{(1)}(y)\uparrow \lor\ \Phi_e^{(1)}(y) \leq e$

Los dos casos dan absurdo que surge de suponer h2 computable.

## h3

$$
h_3(x)=
\begin{cases}
    1 &\text{si Im} \Phi_x^{(1)} \text{es infinita} \\
    0 &\text{si no}
\end{cases}
$$

Supongo h3 computable, defino la siguiente función g3:

$$
g_3(x,y)=
\begin{cases}
    0 &\text{si } h_3(x)\\
    y &\text{si no}
\end{cases} =
\begin{cases}
    0 &\text{si Im} \Phi_x^{(1)} \text{es infinita} \\
    y &\text{si no}
\end{cases}
$$

Como g3 es parcial computable, por TDR $\Phi_e^{(1)}(y)=g_3(e,y)$

$$
\Phi_e^{(1)}(y)=
\begin{cases}
    0 &\text{si Im} \Phi_e^{(1)} \text{es infinita} \\
    y &\text{si no}
\end{cases}
$$

$$\Phi_e^{(1)}(y)=0 \iff \text{Im} \Phi_x^{(1)} \text{es infinita}$$

$$\Phi_e^{(1)}(y)=y \iff \text{Im} \Phi_x^{(1)} \text{es finita}$$

Los dos absurdos

## h4

$$
h_4(x)=
\begin{cases}
    1 &\text{si } |\text{Dom} \Phi_x^{(1)}|=x\\
    0 &\text{si no}
\end{cases}
$$

Supongo h4 computable. Defino g4 en función de esta de forma tal que g4 sea parcial computable.

$$
g_4(x,y)=
\begin{cases}
    \uparrow &\text{si } h_4(x) \\
    p(y) &\text{si no}
\end{cases}
=\begin{cases}
    \uparrow &\text{si } |\text{Dom} \Phi_x^{(1)}|=x\\
    p(x, y) &\text{si no}
\end{cases}
$$

Y defino p(x, y) de forma tal que | Dom(p) | = x :

$$
p(x,y)=
\begin{cases}
    1 &\text{si } y < x\\
    \uparrow &\text{si no}
\end{cases}
$$

Finalmente, por TDR se existe un e tal que $\Phi_e^{(1)}(y)=g_4(e,y)$ entonces

$$
\Phi_e^{(1)}(y)=
\begin{cases}
    \uparrow &\text{si } |\text{Dom} \Phi_e^{(1)}|=e\\
    p(e, y) &\text{si no}
\end{cases}
$$

Analizo cada guarda por separado:

- $|\text{Dom} \Phi_e^{(1)}|=e \iff \Phi_e^{(1)}(y)\uparrow \forall y\iff |\text{Dom} \Phi_e^{(1)}|=0$

Absurdo ya que e != 0 (el programa es no nulo)

- $|\text{Dom} \Phi_e^{(1)}|\neq e \iff \Phi_e^{(1)}(y) = p(e,y)\ \forall y\iff |\text{Dom} \Phi_e^{(1)}|=e$

Absurdo
