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

Donde $\mathcal C$ es $(\mathcal C_1 \cap \dots \cap\mathcal C_k)$ (creo que vale ¿?¡?¡?¡?¡'¿').

## B

Proponer un conjunto que no sea un conjunto de indices de programas y no sea computable.

