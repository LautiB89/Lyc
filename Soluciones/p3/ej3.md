
# Ejercicio 3

$$g_3'(x,y,z)=
\begin{cases}
    z &\text{si } \Phi_{x}^{(1)}(y)\downarrow \land\ \Phi_{x}^{(1)}(y) \neq z \\
    0 &\text{si no}
\end{cases}$$

La reducción es $f_4(x)= (g_3'(x,x,x)=x \land\ x > 0)$:

$$\begin{cases}
    1 &\text{si } \Phi_{x}^{(1)}(x)\downarrow \land\ \Phi_{x}^{(1)}(x) \neq x \land\ x > 0\\
    0 &\text{si no}
\end{cases}$$

Vemos que en el caso de f4(0) = 0 ya que $\Phi_0(0)=0$ por ser el programa vacío así que lo "hardcodeamos".

Sea Q el programa que computa g3', voy a escribir P usando todas funciones computables (=, $\land$ y $>$ son p.r.) :

```txt
    X2 <- X1
    X3 <- X1
    Q
    Y <- (Y = X1) && X1 > 0
```

Por inspección:

$\Psi_{P}^{(1)}(x)=(\Psi_{Q}^{(3)}(x,x,x)=x \land\ x > 0) = (g_3'(x,x,x)=x \land\ x > 0) = f_4(x)$

Por transitividad queda un absurdo $\Psi_{P}^{(1)}(x)= f_4(x)$ ya que f4 no es computable.