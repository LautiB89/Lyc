
# Ejercicio 6

# A

Un programa es optimista si para cada instrucción en la lista se cumple que: 
- Para cada instrucción de salto a una etiqueta L  
- No existe ninguna instrucción con un indice menor que tenga esa misma etiqueta L

$(\forall i \leq \#L)(L[i].b > 2 \implies$  
- $(\forall j \leq \#L)(j\leq i \implies L[j][a] \neq L[i][b]-2)\ )$

Son dos existenciales acotados, con predicados que son p.r. ya que son composiciones de p.r.

$(\forall i)_{\leq \#(L)}\ \bigg(L[i].b > 2 \implies (\forall j)_{\leq \#(L)}\ \big( j\leq i \implies L[j].a \neq L[i].b-2\ \big)\bigg)$  
Puedo reescribirlo como:  
$(\forall i)_{\leq \#(L)}\ \bigg(L[i].b > 2 \implies (\forall j)_{\leq i}\ \big(L[j].a \neq L[i].b-2\ \big)\bigg)$  

Como el predicado se puede escribir como una función p.r, podemos afirmar que es primitivo recursivo.  
