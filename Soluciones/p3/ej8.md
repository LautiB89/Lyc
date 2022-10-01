# Ejercicio 8

Sean $C_1, \dots, C_k$ conjuntos de indices de programas y sea $C = C_1 \cap \dots \cap C_k$.

## A

Probar que C es un conjunto de indices de programas.

Como C1, ..., Ck son conjuntos de indices de programas se cumple que:

$$
\forall i\in [1,k],\ C_i = \{x: \Phi_x \in \mathcal C_i\} \\
(\mathcal C_i \ \text{siendo una clase de funciones})
$$

Puedo reescribir a C usando la definición de conjuntos de indices de programas:

$$
C=\{x: \Phi_x \in \mathcal C_1 \land\ \dots \land\ \Phi_x\in \mathcal C_k \}=\\
\{x: \Phi_x \in (\mathcal C_1 \cap \dots \cap\mathcal C_k) \}=
\{x: \Phi_x \in \mathcal C \}
$$

Donde $\mathcal C$ es $(\mathcal C_1 \cap \dots \cap\mathcal C_k)$ (creo que vale).

## B

Proponer un conjunto que no sea un conjunto de indices de programas y no sea computable.

Un ejemplo facil es $K= \{ x:\Phi_x(x) \downarrow \}$.

### No es un conjunto de indices de programas (prueba):

Supongo que K es un cip:

Sea p el numero de un programa tal que $\Phi_p(x) \downarrow \iff x = p$ (se que existe por el ejercicio 6). Entonces pertenece a K ya que

Por definición de K:  $p \in D \iff \Phi_p(p) \downarrow$

Defino otro programa con numero q tal que $\Phi_p = \Phi_q$:

```txt
A   IF X != p GOTO A
```

Usando la equivalencia del 9, como K es un cip entonces se cumple que

$$
p \in D \land\ \Phi_p = \Phi_q \implies q \in D
$$

Pero por definición de q y K:  $(\Phi_q(x) \downarrow \iff x = p) \implies \Phi_q(q)\uparrow \implies q \notin K$

Absurdo por suponer que K era un cip.

### K no es computable ya que su indicadora no es computable
