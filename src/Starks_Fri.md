# FRI
FRI son las siglas de [Fast Reed-Solomon IOP of Proximity](https://eccc.weizmann.ac.il/report/2017/134/), es un protocolo que establece que un polinomio comprometido tiene un grado limitado.

El [**FRI**](https://book.starknet.io/chapter_10/fri.html) es complejo y gran parte del procesamiento que lo compone está diseñado para que las pruebas sean factibles y sucintas. También hay mucho procesamiento involucrado con la protección contra diversos tipos de ataques que podrían ser realizados por el prover, y garantizar que todo se lleva a cabo en el conocimiento cero.

Su objetivo es encontrar si un conjunto de puntos se encuentran mayoritariamente en un polinomio de bajo grado y puede alcanzar una complejidad de prueba lineal y una complejidad de verificación logarítmica.

En general, hay 2 etapas : commit y query, contenidas en los siguientes pasos repetidos.

1. El verifier envía un número aleatorio al prover.
2. El prover genera un nuevo polinomio.
3. El verifier genera los conjuntos puntuales de consultas y los envía al prover.
4. El prover evalúa los valores polinómicos correspondientes.
5. El verifier realiza una comprobación de validez.

Aprendamos como FRI es un protocolo entre un probador y un verificador, que establece que una codeword dada pertenece a un polinomio de grado bajo.

El prover conoce explícitamente este codeword, mientras que el verificador sólo conoce su raíz Merkle y las hojas de su elección, suponiendo la validación satisfactoria de las rutas de autenticación que establecen la pertenencia de las hojas al Merkle Tree.

Una de las grandes ideas para los sistemas de pruebas de los últimos años ha sido la técnica de dividir y doblar. La idea es reducir una afirmación a dos afirmaciones de la mitad de tamaño. A continuación, ambas afirmaciones se fusionan en una sola utilizando pesos aleatorios proporcionados por el verificador.

Después de muchos pasos, la afirmación se ha reducido a una de tamaño trivial que es verdadera si y sólo si (modulo alguna degradación de seguridad insignificante) la afirmación original era verdadera.

El verfier inspecciona los Merkle Tree (en concreto: pide al prover que proporcione las hojas indicadas con sus rutas de autenticación) de rondas consecutivas para comprobar una relación lineal simple.

Para los provers honestos, el grado de los polinomios representados también se reduce a la mitad en cada ronda y, por tanto, es mucho menor que la longitud de la codeword. Sin embargo, para los provers maliciosos, este grado es uno menos que la longitud de la codeword. En el último paso, el prover envía una codeword no trivial correspondiente a un polinomio constante.

Después de explorar los diferentes pasos en la creación detrás de un STARKs y la importancia de las pruebas de integridad, es evidente que estas pruebas son fundamentales para garantizar la seguridad y confiabilidad de los sistemas del Futuro.