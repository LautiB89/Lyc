
# Ejercicio 7

# A

Usando STP y SNAP, mostrar que las funciones son S-Parciales Computables:  
## 1)
$$f_1(x,y)=
\begin{cases}
1 &\text{si }y\in\text{Dom}\Psi_{x}^{(1)}\\
\uparrow &\text{si no}
\end{cases}$$  
Si uso un predicado computable con la minimización no acotada sabemos que nos da una función parcial computable. Voy a hacerlo con STP (función pr -> computable), entonces nuestra f1 se puede escribir como algo parcial computable de la siguiente forma:  
$$f_1(x,y)=\text{min}_{t}(STP^{(1)}(y, x, t))\geq 0$$
Devuelve el minimo t tal que STP es verdadero si existe tal t, si no existe se cuelga ($\uparrow$). Veo si existe una cantidad de pasos para la cual el programa x con la entrada y termina.  

## 2)
f2 se fija si un programa esta definido para alguna de sus posibles entradas. Como la decodificación de pares forma una biyección con los naturales, puedo recorrer todas las tuplas y tarde o temprano deberia darme verdadero si alguna tupla cumple STP.  

$$f_2(x)=
\begin{cases}
1 &\text{si } \text{Dom}\Psi_{x}^{(1)} \neq \emptyset\\
\uparrow &\text{si no}
\end{cases}=\text{min}_{t}(STP^{(1)}(l(t), x, r(t)))\geq 0 $$
Como STP, l y r son funciones computables y min t es minimización no acotada, tenemos una función parcial computable.  

## 3)

$$f_3(x,y)=
\begin{cases}
1 &\text{si }y\in\text{Im}\Psi_{x}^{(1)}\\
\uparrow &\text{si no}
\end{cases}
=\text{min}_{t}(\Psi_{x}^{1}(t)=y)\geq 0$$

Acá lo defino de una manera mas acorde a lo que me piden:  

$$f_3(x,y)=
\text{min}_{t}(\text{STP}^{(1)}(y, x, t) \land r(\text{SNAP}^{(1)}(y, x, t))[Y] = y)\geq 0$$
$$f_3(x,y)=
\exist_{(t)}\ \Big(\text{STP}^{(1)}(y, x, t) \land r(\text{SNAP}^{(1)}(y, x, t))[Y] = y\Big)$$

## 4)


$$f_4(x,y)=
\begin{cases}
1 &\text{si }\text{Dom}\Psi_{x}^{(1)}\cap \text{Im}\Psi_{y}^{(1)} \neq \emptyset\\
\uparrow &\text{si no}
\end{cases}$$

$f_4(x,y) = \exist_{(t,j, i)}\Big( \text{STP}^{(1)}(l(j), x, t) \land 
\text{STP}^{(1)}(r(j), y, i) \land 
l(j) = r(\text{SNAP}^{(1)}(r(j), y, i))[Y] \Big)$
