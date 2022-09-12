# Ejercicio 3
# A
Demostrar que todo programa P tiene un programa autocontenido P' equivalente.  
(P y P' son programas equivalentes si $\Psi_{P}^{(n)} = \Psi_{P'}^{(n)} \  ∀ n \geq 1$).  

Sea el programa P = [#(I1), ..., #(In)], puedo definir P' = P * $\prod⟨\#L, 0⟩$ donde la productoria multiplica una vez por cada etiqueta que no esté definida.  
De esta forma, nunca hacemos ningun cambio a nuestras variables (hacemos Y ← Y muchas veces).  

