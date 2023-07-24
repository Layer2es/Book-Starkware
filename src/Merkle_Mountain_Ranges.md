# Merkle Mountain Ranges en Cairo
Herodotus ha implementado una nueva estructura de datos criptográfica llamada Merkle Mountain Ranges (MMR) en Cairo. Las MMR son una lista de Árboles de Merkle, donde cada árbol se representa como una montaña y la lista completa forma el rango.

Las MMR comparten las propiedades comunes de los Árboles de Merkle, como el almacenamiento eficiente de datos y la capacidad de generar pruebas de Merkle para demostrar la existencia de un elemento en el árbol. Sin embargo, también ofrecen ventajas adicionales, como la eficiencia en la adición y actualización de elementos, detallemos algunas:

*  La adición de un elemento a un MMR es mucho más eficiente, ya que en la mayoría de los casos no es necesario recorrer todo el árbol. La complejidad subyacente es log2(n) `puntas de montaña`.
* Las pruebas de Merkle en un MMR se realizan mediante pruebas de tamaño log2(n) que consisten en una ruta Merkle hasta la punta del árbol.
* La actualización de un elemento también se puede realizar de manera eficiente.
* Es posible optimizar aún más al comparar inserciones y actualizaciones.
* Tanto las inserciones como las actualizaciones se pueden implementar en cadena, lo que garantiza una total transparencia sobre cómo se actualiza el árbol.

Con esta nueva estructura de datos en Cairo, buscamos mejorar la eficiencia y verificabilidad del almacenamiento de datos en la plataforma, haciéndola útil para diversas aplicaciones que requieren almacenamiento y verificación de datos en la cadena.

## Esquema de firma ECDSA con umbral
Algunas innovaciones que se irán tratando como el esquema de firma ECDSA con umbral en bandeja de entrada de compromisos optimistas. 

Para acceder al estado de diferentes cadenas, necesitamos acceder a las cabeceras de bloque, de las que podemos recuperar todo tipo de información (incluido el estado). Tenemos varias estrategias para obtener las cabeceras de bloque de diferentes cadenas, una de las cuales es un protocolo MPC que ejecuta un algoritmo de firma ECDSA de umbral. La salida del protocolo es una única firma que se validará en la cadena. Esto es mejor que tener una firma por parte, lo que es posible gracias a una ceremonia DKG (generación de clave distribuida).