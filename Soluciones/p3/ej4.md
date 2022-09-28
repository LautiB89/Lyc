# Ejercicio 4

Una función parcial computable f es _extensible_ si existe g computable tal que g(x)=f(x) para todo $x \in \text{Dom}f$.

Qvq existe una función parcial computable que **no es extensible**.

Para probarlo veo:

Dada una funcion f parcial computable, es extensible sii

$\exists g: \forall x \in \text{Dom} f, g(x)=f(x)$

La f que elijo para probar esto está definida como

$$f(x)=\begin{cases}
    \Phi_{x}^{(1)}(x) &\text{si } \Phi_{x}^{(1)}(x)\downarrow \\
    \uparrow &\text{si no}
\end{cases}$$

Pruebo que es computable escribiendo un programa P que la computa, usando $U_1(x,x)$ el programa que computa $\Phi^{(1)}(x,x)$:

```txt
    Y <- Phi_X1(X2)
```

Por inspección se ve que termina sii $\Phi_{x}^{(1)}(x)$ termina su ejecución. Como pudimos escribir un programa tal que:

$$\Psi_{P}^{(1)}(x)=f(x)$$

Queda probado que f es parcial computable. No es total computable ya que la función no es total.

Ahora defino f'(x) como su extensión. Cumple que es total y que tiene el mismo comportamiento que f para el dominio de f. Eso significa que está definida (devuelve algún valor) para la guarda en la que f se colgaba:

$$f'(x)=\begin{cases}
    \Phi_{x}^{(1)}(x) &\text{si } \Phi_{x}^{(1)}(x)\downarrow \\
    h(x) &\text{si no}
\end{cases}$$

Finalmente pruebo que para todo h(x) total, f' no es computable.

## Pruebo f' no computable

Supongo f' computable, entonces existe un programa P que la computa. Escribo el siguiente programa Q:

```txt
    P
A   IF Y = Phi_X(X) GOTO A
```

Por inspección del programa Q se ve que:

$$\Psi_{Q}^{(1)}(x) \downarrow \iff \Psi_{P}^{(1)}(x) \neq \Phi_{x}^{(1)}(x) \iff f'(x) \neq \Phi_{x}^{(1)}(x)$$

Por definición de f':

$$f'(x) \neq \Phi_{x}^{(1)}(x) \iff f'(x) = h(x)\iff \Phi_{x}^{(1)}(x) \uparrow$$

Finalmente $\Psi_{Q}^{(1)}(x) \downarrow \iff \Phi_{x}^{(1)}(x) \uparrow$ y evaluando x en e = #(Q):

$$\Phi_{e}^{(1)}(e) \downarrow \iff \Phi_{e}^{(1)}(e) \uparrow$$

Absurdo que surge de suponer que f' es computable.

## Yo practicando

Supongo f' computable, entonces existe Q un programa que la computa. Llamo Q' al siguiente programa:

```txt
    Q'
A   IF Y = 1 GOTO A
```

Por inspección de Q' y la definición de f:

$\Psi_{Q'}^{(1)}(x)\downarrow \iff \Psi_{Q}^{(1)}(x) \neq 1 \iff f(x) \neq 1 \iff \Phi_{x}^{(1)}(x)\uparrow$

Finalmente $\Psi_{Q'}^{(1)}(x)\downarrow \iff \Phi_{x}^{(1)}(x)\uparrow$ reemplazando x por e = #(Q') nos queda $\Phi_{e}^{(1)}(e)\downarrow \iff \Phi_{e}^{(1)}(e)\uparrow$.
Absurdo que parte de suponer que f era computable.
