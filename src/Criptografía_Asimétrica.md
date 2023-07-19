# Criptografía Asimétrica
Ahora hablemos como el concepto de algoritmos criptográficos de clave asimétrica, fue un enfoque revolucionario que introdujo un concepto completamente diferente, **el uso de un par de claves complementarias, una pública y una privada**, para asegurar la confidencialidad de los datos. Cada clave del par tenía una función específica:

* **Public key**: esta clave pública se compartía abiertamente y se utilizaba para cifrar la información.
* **Private key:** esta clave privada se guardaba cuidadosamente y se utilizaba para descifrarla.

Con la criptografía de clave pública, los mensajes cifrados podían ser transmitidos a través de redes inseguras sin el temor de que fueran interceptados y descifrados por personas no autorizadas, pero en este caso diferenciándose de la simétrica en que estos mensajes requerían un Private key y una Public key. Era como si se hubiera descubierto una nueva forma de comunicación secreta y segura en el mundo digital, fue un avance revolucionario en el campo de la criptografía.

![graph](./assets/asimetrico.gif)
<div align="center">
<em>Criptografía Asimétrica - Creación de PK y PB</em>
</div>

Algunos de los más destacados y utilizados son los siguiente:

* **RSA -** [**Rivest-Shamir-Adleman:**](https://es.wikipedia.org/wiki/RSA) es un sistema criptográfico asimétrico de clave pública desarrollado en 1979. Su seguridad radica en el problema de la factorización de números enteros y se utiliza en diversos ámbitos de la transmisión de datos en Internet debido a su facilidad de uso. Este sistema consta de una clave pública RSA y una clave privada RSA.

* **ECC -** [**Elliptic Curve Cryptography:**](https://es.wikipedia.org/wiki/Criptograf%C3%ADa_de_curva_el%C3%ADptica) en la década de 1980 se desarrolló este enfoque de curva elíptica criptográfica, una variante de la criptografía asimétrica o de clave pública basada en las matemáticas de las curvas elípticas que proporciona niveles de seguridad similares o superiores a RSA pero con claves más cortas.

* **ECDSA -** [**Elliptic Curve Digital Signature Algorithm:**](https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.186-4.pdf) en los Años 1990 nació ECDSA, un algoritmo de firma digital y autenticación en criptografía asimétrica, basado en curvas elípticas. Se utiliza en criptografía para garantizar la autenticidad, integridad de los datos. ECDSA se basa en la dificultad computacional de resolver el problema del logaritmo discreto en curvas elípticas.