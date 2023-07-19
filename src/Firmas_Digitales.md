# Firmas digitales
Los esquemas de firma digital son un tipo de criptografía de clave pública que garantiza la integridad, autenticidad y no repudio de los datos.

Es importante destacar que el esquema de firma digital puede variar dependiendo del algoritmo utilizado, ECDSA, es un ejemplo común de esquema de firma basado en criptografía de curva elíptica. Aquí EC recordemos que representa la curva elíptica utilizada y [**DSA**](https://en.wikipedia.org/wiki/Digital_Signature_Algorithm) (una variante de los esquemas de firma [Schnorr](https://en.wikipedia.org/wiki/Schnorr_signature) y [ElGamal](https://en.wikipedia.org/wiki/ElGamal_signature_scheme)) el algoritmo de firma digital. Cada esquema tiene sus propias características y propiedades de seguridad, y se selecciona según los requisitos y consideraciones específicas de la aplicación.

Cuando se trata de firmas digitales, los pasos generales suelen ser los siguientes:

* **Key generation:** el Generador de Claves es un protocolo o algoritmo que genera **un Keypar**, un par de claves asimétricas como se explicó anteriormente compuestas por una public key y una private key. En el caso de la criptografía de curva elíptica (como ECDSA), se generan los parámetros necesarios para definir la curva y se elige una clave privada aleatoria. A partir de la clave privada, se calcula la clave pública correspondiente utilizando operaciones matemáticas específicas.

* **Hash del mensaje:** antes de firmar el mensaje, se aplica una función hash criptográfica al contenido del mensaje. Esto reduce el mensaje a un valor de longitud fija llamado resumen o hash. El objetivo es garantizar la integridad y eficiencia del proceso de firma, ya que es más rápido firmar y verificar un resumen más corto que el mensaje completo.

* **Digital Signature:** este proceso tiene el propósito de realizar una serie de operaciones matemáticas utilizando la clave privada y el hash del mensaje para generar la firma digital.

* **Verify Signature:** para verificar la autenticidad de la firma, se necesita la clave pública del firmante. Se aplica nuevamente la función hash al mensaje original y se utiliza la clave pública junto con la firma para realizar operaciones matemáticas específicas. Si el resultado coincide con la firma original, se considera que la firma es válida y se confirma la autenticidad del mensaje y del firmante.

El proceso de firma puede considerarse como el cifrado del archivo mediante la clave privada. Para ello, la persona que firma utiliza su clave privada para producir una firma.

Exploraremos a continuación la relevancia de los diversos esquemas de firmas para garantizar la seguridad de nuestros datos, así como la forma en que Starknet usa AA para abstraer la firma de la validación. En este contexto, se pueden diseñar diferentes esquemas o configuraciones, como el `secp256r1`, una variante de STARK Curve, la versión amigable de ECDSA optimizada en Starknet. Este esquema de firma se puede utilizar para incorporar firmas en dispositivos modernos de manera biométrica, aislada y abstraída por naturaleza, lo que mejora significativamente la eficiencia, tal como se discutirá en detalle más adelante.

Por lo tanto, resulta crucial abordar el siguiente apartado relacionado con el uso de Key generation que desempeñan un papel fundamental en este contexto.