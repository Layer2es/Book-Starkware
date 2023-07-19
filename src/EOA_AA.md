# EOA y AA - Firmantes
Las cuentas de EOA [**(Externally Owned Accounts)**](https://ethereum.org/en/whitepaper/#ethereum-accounts) en Ethereum, al igual que muchas otras criptomonedas, utilizan el algoritmo ECDSA que aprendimos antes para generar claves y firmar transacciones digitalmente. Esto les permite participar de manera segura en la red y realizar operaciones. Las EOA son cuentas que pertenecen a usuarios externos a la cadena de bloques.

En Ethereum, el estado de una cuenta solo puede ser modificado a través de transacciones, las cuales deben ser iniciadas por una EOA. sin embargo, no cualquier persona puede activar una transacción desde cualquier EOA, aquí es donde entra en juego el concepto de firmante.

Cada cuenta en Ethereum está asociada con un objeto criptográfico llamado keypair, como aprendimos antes.

La clave privada, se utiliza para firmar mensajes digitales, mientras que la clave pública permite que cualquiera pueda verificar que una firma en particular fue generada por la clave privada correspondiente.

La asociación entre una cuenta y un firmante se realiza mediante la dirección de la cuenta. La dirección de un EOA se deriva de la clave pública del firmante, específicamente, **la dirección se obtiene tomando los últimos 20 bytes del hash Keccak-256 de la clave pública.**

El propietario de una cuenta puede autorizar una transacción desde su cuenta firmando los parámetros de la transacción con la clave privada correspondiente.

La [**curva elíptica secp256k1**](https://ethereum.org/en/whitepaper/#ethereum-accounts)  es una de las curvas elípticas más utilizadas en criptografía, especialmente en el contexto de criptomonedas como Bitcoin o Ethereum. Esto ha permitido establecer esquemas de firmas digitales que garantizan la integridad de las transacciones al asegurar la autenticidad de las claves.

La abstracción de firma y clave privada es una propiedad presente en algunos sistemas criptográficos, como ciertos esquemas de firmas digitales basados en identidad. Sin embargo, en el caso del algoritmo ECDSA utilizado en Ethereum y muchas otras blockchain, la firma está inherentemente vinculada a la clave privada de la cuenta y no es posible separarlas o abstraerlas, como podría ser el caso en otros esquemas diseñados con estos principios.

Ahora que ya hemos adquirido los conceptos básicos y hemos prestado atención para adquirir la formación adecuada y avanzada, podemos sumergirnos en el apasionante ecosistema de StarkWare, Starknet, StarkEx y STARKs. Nuestra mente está mejor preparada para embarcarnos en el viaje que nos espera en el resto del documento y en las futuras series.