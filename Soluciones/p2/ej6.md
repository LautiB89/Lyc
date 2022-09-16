
# Ejercicio 6

# A

Un programa es optimista si para cada instrucción en la lista:
    Para cada instrucción de salto a una etiqueta L
    No existe ninguna instrucción con un indice menor que tenga esa misma etiqueta L

$$(\forall i \leq \#L)(L[i][b] > 2 \implies \\
(\forall j \leq \#L)(j\leq i \implies L[j][a] \neq L[i][b]-2) 
\\
)$$