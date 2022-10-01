# Ejercicio 6

Demostrar que existe un programa p tal que $\Psi_p^{(1)}(x)\downarrow \iff x=\#p$

Defino una función g : $\N^2 \to \N$ como:

$$
g(x,y)=
\begin{cases}
    42 &\text{si } x = y \\
    \uparrow &\text{si no}
\end{cases}
$$

Es trivial ver que es parcial computable. Sabiendo esto podemos usar el teorema del parametro sobre g:

Por el teo sabemos que existe un programa con numero e tal que $\Phi_e^{(1)}(y)=g(e,y)$, finalmente:

$$
\Phi_e^{(1)}(x)=
\begin{cases}
    42 &\text{si } x = e \\
    \uparrow &\text{si no}
\end{cases}
$$

Por la definición de $\Phi$ se ve que $\Phi_e^{(1)}(x)\downarrow \iff x = e$ como queriamos probar.
