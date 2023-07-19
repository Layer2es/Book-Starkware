# Patricia Merkle Trie
La especificación de Ethereum define el [**Modified Merkle Patricia Trie**](https://ethereum.org/en/developers/docs/data-structures-and-encoding/patricia-merkle-trie/) (también conocido como MPT) este método se utiliza para guardar estados. Básicamente, el MPT es una combinación del Patricia trie y el Merkle tree, con algunas optimizaciones adicionales adaptadas a las características de Ethereum.

Patricia trie, [(Radix tree o Radix trie)](https://en.wikipedia.org/wiki/Radix_tree), árbol de prefijos compacto **(compact prefix tree)** o árbol de prefijos comprimido **(compressed trie)**, es una sofisticada estructura de datos que ofrece una optimización espacial en la representación de [Tries] (árboles de prefijos). Una de las características clave de este tipo de árbol es la fusión de nodos cuando un nodo es hijo único de su padre, lo que contribuye a una mayor eficiencia y rendimiento.

Esta estructura es un tipo de **árbol de búsqueda k-ary**, siendo un [m-ary tree](https://en.wikipedia.org/wiki/M-ary_tree) (también conocido como `n-ary tree`, `k-ary tree` o `k-way tree`) un árbol raíz en el cual cada nodo tiene como máximo m hijos. Ambas estructuras de datos se utilizan para localizar claves específicas dentro de un conjunto.

Estos árboles son completamente deterministas, lo que significa que aquellos con las mismas asociaciones de (clave, valor) están garantizados de ser idénticos, hasta el último byte. Esto asegura que tengan el mismo hash raíz, lo que proporciona la deseada eficiencia de `O(log(n))` para inserciones, búsquedas y eliminaciones. Además, son más fáciles de entender y programar que alternativas más complejas basadas en comparaciones, como los [red-black tree.](https://en.wikipedia.org/wiki/Red%E2%80%93black_tree)

El Patricia Merkle Trie combina la estructura de un árbol de búsqueda binario con la estructura de árbol de Merkle, lo cual permite verificar eficientemente la integridad de los datos y proporciona una representación compacta del estado completo de la cadena.

El uso del Patricia Merkle Trie en Ethereum ofrece ventajas significativas en términos de eficiencia y escalabilidad. Permite realizar consultas rápidas sobre el estado de las cuentas y los contratos, evitando la necesidad de recorrer todo el estado completo. En cambio, solo es necesario verificar y acceder a los nodos relevantes en el árbol, lo que ahorra tiempo y recursos.

Además, esta estructura de árbol facilita la implementación de funciones de snapshot y revert en Ethereum. Estas funciones permiten crear instantáneas del estado del sistema en momentos específicos y revertir cambios en caso de errores o ataques, brindando una capa adicional de seguridad y confiabilidad a la red blockchain.

![graph]()
<div align="center">
<em></em>
</div>

La comprensión de los Merkle Trees y el MPT resulta especialmente relevante al explorar otras estructuras de datos criptográficas, como las Merkle Mountain Ranges (MMRs) en Herodotus para las Storage Proof. Las MMRs pueden considerarse una lista de Árboles de Merkle, donde cada árbol se representa como una montaña y la lista completa forma el rango. La utilización de funciones hash específicas y sus características de seguridad se explorarán para comprender cómo crear estos árboles de manera eficiente y óptima.

Por lo tanto, es crucial comprender a fondo las diferentes funciones hash y sus propiedades para tomar decisiones informadas sobre la selección y optimización de las mismas en la construcción de estructuras de datos criptográficas más eficientes y seguras en los Árboles de Merkle.

Las funciones hash desempeñan un papel fundamental en garantizar la integridad y la seguridad de los datos almacenados en los árboles de Merkle, ya que se utilizan para calcular los hashes de los nodos y verificar su integridad durante la construcción y la verificación del árbol.