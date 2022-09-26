# Ejercicio 1

Probar que no son computables usando diagonalización.

## A)

Pruebo que la función f no es computable:

$$
f(x)=
\begin{cases}
1 &\text{si } \Phi_{x}(x)\downarrow \\
0 &\text{si no} \\
\end{cases}
$$

Supongo que f es computable para llegar a un absurdo. Sea P el programa que computa f.
Defino otro programa usando P llamado P':

```txt
    P
A   IF Y != 0 GOTO A
```

Lo defino de forma tal que cuando P dice que el programa X se define, entonces P' se indefine. Sea e el numero del programa P'
$$\Psi_{P'}(x)\downarrow \iff \Psi_{P}(x) = 0 \iff f(x) = 0$$
Por definicion de f1:  
$$f(x) = 0 \iff \Phi_{x}(x)\uparrow$$
Entonces tenemos que para todo x:  
$$\Psi_{P'}(x)\downarrow \iff \Phi_{x}(x)\uparrow$$
Tomando x = e = #P':  
$$\Phi_{e}(e)\downarrow \iff \Psi_{P'}(e)\downarrow \iff \Phi_{e}(e)\uparrow$$

Absurdo por suponer que f es computable.

Ahora va el ejercicio de verdad:

$$
f_1(x, y)=
\begin{cases}
1 &\text{si } \Phi_{x}(y)\downarrow \\
0 &\text{si no} \\
\end{cases}
$$

Usando esto voy a ver que f(x) es una reducción de f1(x, y) usando f(x) = f1(x, x).  
Supongo f1 computable y sea Q1 un programa que lo computa. Usando Q1 escribo Q1':

```txt
    X2 <- X1
    Q1
```

Entonces vemos que $\Psi_{Q1'}^{(1)}(x) = \Psi_{Q1}^{(2)}(x, x)$  
Por hipotesis: $\Psi_{Q1}^{(2)}(x, x) = f1(x, x) = f(x)$  
Finalmente, por la transitividad de la igualdad tenemos que: $\Psi_{Q1'}^{(1)}(x) = f(x)$  
Absurdo ya que la función que da la salida de un programa ( $\Psi$ ) no puede ser una función no computable ( $f$ ).  
Surge de suponer que f1 es computable.

## B)

$$
f_2(x, y)=
\begin{cases}
1 &\text{si } \Phi_{x}(y) = 0 \\
0 &\text{si no} \\
\end{cases}=
\begin{cases}
1 &\text{si } \Phi_{x}(y) = 0 \\
0 &\text{si } \Phi_{x}(y)\uparrow \lor\ \Phi_{x}(y) \neq 0\\
\end{cases}
$$

### Sin usar reducción (dudosa)

Hago todo el versito de suponer f computable, con P el programa que la computa y otro programa P' que usa la salida de P...

```txt
    P
A   IF Y != 0 GOTO A
    Y <- 1
```

$\Psi_{P'}(x,y)\downarrow \iff \Psi_{P}(x,y)=1\iff f_2(x,y)=1 \iff \Phi_x(y)= 0$

Queda como:

$\Psi_{P'}(x,y)\downarrow \iff \Phi_e^2(x,y)\downarrow \iff \Phi_e^2(x,y)= 1 \iff \Phi_x^1(y)=0$

Asi de una yo se que las $\Phi^1$ son funciones donde todos los parametros $x_i, i>1$ estan definidos como 0. Puedo reemplazarlas por una $\Phi^2$ que tenga la segunda variable en 0.

$\Phi_e^2(x,y) = 1 \iff \Phi_x^2(y, 0)=0$

evaluando x = e = #(P'):

$\Phi_e^2(e,y)=1 \iff \Phi_e^2(y, 0)=0$

Puedo escribir el programa de forma tal que la salida siempre sea 1, lo cual me lleva a un absurdo.

Voy a demostrar un caso mas simple para después demostrar la reducción.

### Primera forma (galerazo?)

$$
f(x)=
\begin{cases}
1 &\text{si } \Phi_{x}(x) = 0 \\
0 &\text{si no} \\
\end{cases}
$$

Para probar que f no es computable, primero supongo que **si** lo es. Por ser computable, existe un programa P que la computa: $\Psi_{P}(x)=f(x)$. Como P existe, puedo definir otro programa que lo use y lo llamo P':

```txt
    P
A   IF Y = 0 GOTO A
    Y <- 1
```

$$\Psi_{P'}(x)\downarrow \iff \Psi_{P}(x)\downarrow \land\ \Psi_{P}(x) \neq 0$$

Como las unicas salidas del programa P son 1 o 0, estamos pidiendo que la salida sea 1:

$$\Psi_{P}(x)\downarrow \land\ \Psi_{P}(x) \neq 0 \iff \Psi_{P}(x)=1 \iff f(x)=1$$

Por definición de f, solo se cumple si estamos en la primera guarda:

$$f(x)=1 \iff \Phi_x(x)=0$$

Por transitividad, finalmente llegamos a:

$$\Psi_{P'}(x)\downarrow \iff \Phi_{x}(x)=0$$

Pero por inspección de P' podemos ver que $\Psi_{P'}(x)=1$ siempre que termine la ejecución del programa. Como P' existe a partir de lo que supusimos, entonces también podemos calcular su numero de programa. Llamamos e = #(P').

$$\Psi_{P'}(x)\downarrow \iff \Psi_{P'}(x)=1 \iff \Phi_{x}(x)=0$$
$$ \Phi*{e}(e)=1 \iff \Phi*{e}(e)=0$$

Absurdo que parte de suponer que la función f es computable.

### Segunda forma

$$
f(x)=
\begin{cases}
1 &\text{si } \Phi_{x}(x) = 0 \\
0 &\text{si no} \\
\end{cases}
$$

Supongo f computable. Sea P el programa que la computa, voy a escribir una P' con la intención de que esté definida sii la universal se indefina. Para que se indefina la universal necesito que el programa se cuelgue sii la salida es 1 (analizando la guarda de f).

```txt
    P
A   IF Y != 0 GOTO A
    Y <- ¿?
```

$$\Psi_{P'}(x)\downarrow \iff \Psi_{P}(x) = 0 \iff f(x)= 0 \\ \text{Por definición: }\iff \Phi_{x}(x)\uparrow \lor\ \Phi_{x}(x) \neq 0$$

Mas o menos quedó lo que quería, estaría bueno no tener el $\Phi_{P}(x) \neq 0$ que no me permite llegar directo a la contradicción. Sabiendo que para la contradiccción voy a evaluar x = e = #(P') puedo modificar P' para que dé una salida 0 y que solo "sobreviva" la primera parte del $\lor$.

```txt
    P
A   IF Y != 0 GOTO A
    Y <- 0
```

$$\Psi_{P'}(x)\downarrow \iff \Phi_{x}(x)\uparrow $$

Evaluando x = e:

$$\Phi_{e}(e)\downarrow \iff \Phi_{e}(e)\uparrow $$

Absurdo, por suponer que f era computable.

### Reducción

Usando esto voy a ver que f(x) es una reducción de f2(x, y) usando f(x) = f2(x, x).  
Supongo f2 computable y sea Q2 un programa que lo computa. Usando Q2 escribo Q2':

```txt
    X2 <- X1
    Q2
```

Entonces vemos que $\Psi_{Q2'}^{(1)}(x) = \Psi_{Q2}^{(2)}(x, x)$  
Por hipotesis: $\Psi_{Q2}^{(2)}(x, x) = f_2(x, x) = f(x)$  
Finalmente, por la transitividad de la igualdad tenemos que: $\Psi_{Q2'}^{(1)}(x) = f(x)$  
Absurdo ya que la función que da la salida de un programa ( $\Psi$ ) no puede ser una función no computable ( $f$ ).  
Surge de suponer que f2 es computable.

## C)

$$
f_3(x,y,z)=
\begin{cases}
    1 &\text{si } \Phi_{x}^{(1)}(y)\downarrow \land\ \Phi_{x}^{(1)}(y) > z \\
    0 &\text{si } \Phi_{x}^{(1)}(y)\uparrow \lor\ \Phi_{x}^{(1)}(y) \leq z
\end{cases}
$$

Hago P3' un programa que usa P3 (el programa de f3):

Quiero que:
$\Psi_{P3'}(x,y,z)\downarrow \iff \Phi_{x}^{(1)}(y)\uparrow \lor\ \Phi_{x}^{(1)}(y) \leq z \iff \Phi_{x}^{(3)}(y, 0, 0)\uparrow \lor\ \Phi_{x}^{(3)}(y, 0, 0) \leq z$  
$\Phi_{e}^{(3)}(x,y,z)\downarrow \iff \Phi_{x}^{(3)}(y, 0, 0)\uparrow \lor\ \Phi_{x}^{(3)}(y, 0, 0) \leq z$  
$\Phi_{e}^{(3)}(e,y,z)\downarrow \iff \Phi_{e}^{(3)}(y, 0, 0)\uparrow \lor\ \Phi_{e}^{(3)}(y, 0, 0) \leq z$  
$\Phi_{e}^{(3)}(e,y,z)\downarrow \iff \Phi_{e}^{(3)}(y, 0, 0)\uparrow \lor\ \Phi_{e}^{(3)}(y, 0, 0) \leq z$  
No se cerrarlo

Pruebo el caso mas simpĺe:

$$
g_3(x)=
\begin{cases}
1 &\text{si } \Phi_{x}^{(1)}(x)\downarrow \land\ \Phi_{x}^{(1)}(x) > x \\
0 &\text{si } \Phi_{x}^{(1)}(x)\uparrow \lor\ \Phi_{x}^{(1)}(x) \leq x
\end{cases}
$$

Hago un programa Q3' con Q3:

```txt
    Q3
A   IF Y != 0 GOTO A
    Y <- X + 1
```

$$\Psi_{Q3'}(x)\downarrow \iff \Psi_{Q3}(x) = 0 \iff g_3(x)=0 \\\iff \Phi_{x}^{(1)}(x)\uparrow \lor\ \Phi_{x}^{(1)}(x) \leq x$$

Por la cadena de sii:

$$\Psi_{Q3'}(x)\downarrow \iff \Phi_{x}^{(1)}(x)\uparrow \lor\ \Phi_{x}^{(1)}(x) \leq x $$

Evaluando x = e = #(Q3')

$$\Phi_{e}(e)\downarrow \iff \Phi_{e}^{(1)}(e)\uparrow \lor\ \Phi\_{e}^{(1)}(e) \leq e $$

Vemos que la salida del programa con numero e siempre es x+1, asi que $\Phi_{e}^{(1)}(e) \leq e$ es siempre falso.

$$\Phi_{e}(e)=e+1 \iff \Phi_{e}^{(1)}(e)\uparrow \lor\ \Phi_{e}^{(1)}(e) \leq e $$

### Reducción f3

Voy a usar g3 (no es computable) para probar que f3 no es computable mostrando que g3 es una reducción de f3. Quiero ver que si f3(x,y,z) es computable entonces hay un caso especial (la reducción) g3(x) que tambien es computable, lo hago usando g3(x) = f3(x,y,z).

Supongo que f3(x,y,z) es computable, entonces existe un programa P3 que la computa. Hago un programa P3':

```txt
    X2 <- X1
    X3 <- X1
    P3
```

Por inspección este programa se comporta como P3 con las 3 variables iguales a la primera:  

$$\Psi_{P3'}^{(1)}(x) = \Psi_{P3}^{(3)}(x,x,x) = f_3(x,x,x)$$

Por definición de g3 sabemos que $g_3(x)=f_3(x,x,x)$ entonces:  

$$\Psi_{P3'}^{(1)}(x) = g3(x)$$

Pero esto implicaría que g3 es computable, cuando sabemos que no lo es. Absurdo, no existe ningun programa Q tal que $\Psi_{Q}^{(1)}(x)=g3(x)$ (no es computable).  
Surge de suponer que f3 es computable.  

## D)

$$f_4(x)=
\begin{cases}
    1 &\text{si } \Phi_{x}^{(1)}(x)\downarrow \land\ \Phi_{x}^{(1)}(x) \neq x \\
    0 &\text{si } \Phi_{x}^{(1)}(x)\uparrow \lor\ \Phi_{x}^{(1)}(x) = x \\
\end{cases}
$$

Supongo f4 computable, entonces existe un programa P4 que lo computa. Llamo P4' al siguiente programa:

```txt
    P4
A   IF Y != 0 GOTO A
    Y <- 0
```

Por inspección vemos que el programa termina siempre en 0 y termina sii la salida de P4 es igual a 0.

$\Psi_{P3'}^{(1)}(x) \downarrow \iff \Psi_{P3}^{(1)}(x) = 0 \iff f_4(x)=0 \iff \Phi_{x}^{(1)}(x)\uparrow \lor\ \Phi_{x}^{(1)}(x) = x$

Por transitividad nos queda:

$\Psi_{P3'}^{(1)}(x) \downarrow \iff \Phi_{x}^{(1)}(x)\uparrow \lor\ \Phi_{x}^{(1)}(x) = x$

Sea e = #(P4') y evaluando x en e:

$\Phi_{e}^{(1)}(e) \downarrow \iff \Phi_{e}^{(1)}(e)\uparrow \lor\ \Phi_{e}^{(1)}(e) = e$

La segunda parte del $\lor$ es siempre falsa ya que $\Phi_{x}^{(1)}(x) = 0,\ \forall x$ y como e no es el programa vacio entonces $\Phi_{e}^{(1)}(e) = 0 \neq e$. Finalmente:

$\Phi_{e}^{(1)}(e) \downarrow \iff \Phi_{e}^{(1)}(e)\uparrow$

Absurdo, surge de suponer que f4 es computable.

