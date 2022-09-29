# Ejercicio 4

# A

Demostrar con inducción estructural sobre estados y el salto es sobre numero de linea (primer componente de la descripción instantanea).

## $S_1$: Igual que $S$ pero sin la instrucción V <- V + 1

Para probar que hay una función $S$-Parcial Computable pero no $S_1$-Computable voy a probar que todas las funciones (que están definidas) devuelven 0. En especial existe la función f(x)=1 que es pr y entonces computable en S.

Quiero probar que:  
Dado cualquier $x\in \mathbb N$ tal que $\Psi_{P}^{1}(x)\downarrow$, el computo $d_1, \dots, d_k$ (con $d_1 = (1, \sigma_1)$ ) del programa P con la entrada x cumple que $\Psi_{P}^{1}(x)=0,\ \forall x\in\mathbb N$. Vamos a ver que Y vale 0 en todas las descripciones instantáneas de P.  
Llamo $d_i=(j_i, \sigma_i)$ a la i-ésima descripción instantánea de P.

### Caso Base

Pruebo para el caso $d_1$ que el valor de Y es 0.  
Se cumple ya que en todos los estados iniciales de cualquier programa Y = 0.

### Paso inductivo

Quiero ver que $d_{i+1}[Y]=0$ sabiendo que $d_i[Y]=0$.

El valor del par $d_{i+1}$ depende de la instrucción indicada por $j_i$.

- Si la $j_i$-ésima instrucción es V <- V - 1  
  El valor de $j_{i+1}=j_i + 1$ y

  - Si V es Y, $d_{i+1}[Y]=\max\{d_i[Y]-1, 0\}=\max\{-1, 0\}=0$
  - Si V no es Y, $d_{i+1}[Y]=d_{i}[Y]=0$

- Si la $j_i$-ésima instrucción es
  IF V $\neq$ 0 GOTO L:  
  El estado no cambia: $d_{i+1}=d_i$ e Y sigue siendo 0.

Pudimos ver que en todos los casos el valor de Y es siempre 0, probando que todas las funciones de S1, si están definidas, devuelven 0.

## $S_2$: Igual que $S$ pero sin la instrucción IF V $\neq$ 0 GOTO L

Voy a probar que la función $f(x)=\ \uparrow$ no es computable en el lenguaje S2. Claramente es parcial computable en S, usamos un GOTO que vaya a su propia etiqueta.  
Puedo probar que dado un programa de k instrucciones, paso una unica vez por cada instrucción, haciendo que mi cantidad de descripciones instantánteas también sea k (finito).  
Tambien puedo suponer que $\Psi_P$ se indefine para cualquier programa P de k instrucciones, para llegar a la conclusión de que cada descripción instantánea apunta a una dirección diferente a las demás, haciendo que sea imposible...

Dado un programa P cualquiera en $S_2$ con k instrucciones, voy a probar que nunca se cuelga y que pasa una unica vez por instrucción.

Voy a probar que dado un computo $d_1, \dots, d_k$ para todo $i\in[1,k)$ se cumple que $j_i < j_{i+1}$.

### Caso Base

Como i es 1, la descripción $d_1$ es $(1, \sigma_1)$ y el indice $j_{i+1}$ depende de la i-ésima instrucción.
Como no existe la instrucción IF..., en todos los casos $j_{i+1}=1 + 1=2 \implies j_i < j_{i+1}$ ya que 1 < 2.

### Paso inductivo

Suponiendo $j_i < j_{i+1}$ quiero ver que $j_{i+1} < j_{i+2}$.
Vemos que $j_{i+1}=j_i + 1$ para cualquier instrucción y lo mismo para el caso de i+2. Finalmente la desigualdad queda como  
$$j_i < j_i+1 < j_i+2$$
Lo cual es verdadero para todo $j_i$.

## $S_3$: Igual que $S$ pero sin la instrucción V <- V - 1

Mostrar que todos los programas en este lenguaje forman funciones con cierto esquema, y que existen otras que no cumplen ese esquema:

$$
f(x) =
\begin{cases}
k &\text{si } x_i \neq 0 \\
m &\text{si } x_i =0
\end{cases}
$$

Con k,m constantes fijas.

# B

Podría probar que cada instrucción de S' se puede se puede escribir como otras instrucciones de S.  
V <- V' es una macro que ya conocemos  
V <- V+1 es una de las intrucciones basicas  
IF V != V' GOTO L

Voy a ver que las funciones de S' se pueden programar usando S y viceversa.

Sabemos por la teorica que la asignación de variables es S-Computable.  
La de incrementar tambien se puede hacer en S (trivial).
Un posible programa en S que computa IF V != V' GOTO L es:

```txt
    Z1 <- V
    Z2 <- V'
    Z3 <- Z1 - Z2
    Z4 <- Z2 - Z1
    IF Z3 != 0 GOTO L   ; salta sii Z1 > Z2
    IF Z4 != 0 GOTO L   ; llegamos aca sii Z2 >= Z1 entonces salta sii Z1 != Z2
```

Ahora trato de programar las funciones basicas de S usando las de S':  
Uso la macro GOTO L:

```txt
    Z3 <- Z4
    Z3 <- Z3 + 1
    IF Z3 != Z4 GOTO L
```

Ahora puedo programar V <- V - 1:

```txt
A   Z1 <- Z1 + 1
    IF Z1 != V GOTO B
    GOTO C
B   Z2 <- Z2 + 1
    GOTO A
C   V <- Z2
```

Puedo programar IF V != 0 GOTO L como:

```txt
    ; uso Zi una variable fresca
    IF V != Zi GOTO L
```
