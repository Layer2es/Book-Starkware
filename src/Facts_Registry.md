# Facts Registry
Este es el último contrato en la pila básica de Herodotus y optimiza el proceso de acceso a las propiedades de una cuenta, como:

Nonces (si están disponibles).

Saldos (si están disponibles).

Storage hash.

Code hash.

El primer nivel de almacenamiento en las blockchains basadas en cuentas son las propias cuentas. Para probarlas, es necesario tener acceso a la stateRoot, cuya corrección se verifica mediante el contrato HeadersStore. Con dicha raíz del estado, se puede verificar una prueba de MPT que demuestra las propiedades mencionadas de una cuenta.

Estas propiedades, de manera similar a HeadersStore, se pueden guardar en el estado para reducir la cantidad de cálculos necesarios cada vez que se accede al almacenamiento del contrato inteligente.

Acceso al almacenamiento del contrato

Como se mencionó anteriormente, el primer nivel de almacenamiento son las cuentas. El segundo nivel es el almacenamiento real del contrato. Este almacenamiento se guarda en un árbol Merkle Patricia Tree, donde la raíz es el StorageHash de la cuenta. Al ser un árbol Merkle Patricia, se puede probar cualquier cosa incluida en él.

Esto permite que Herodotus habilite el acceso al almacenamiento de los contratos inteligentes. El almacenamiento de los contratos inteligentes es una base de datos de clave-valor donde cada clave corresponde a 32 bytes de datos.

Para obtener más información sobre cómo asignar un nombre de variable a su clave de almacenamiento, consulte la documentación de Solidity. Recomendamos encarecidamente utilizar esta guía cuando se trabaja con el diseño del almacenamiento de contratos inteligentes en Solidity.