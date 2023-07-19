# Bases Criptográficas
La [**criptografía**](https://en.wikipedia.org/wiki/Cryptography) es el campo de estudio y desarrollo de técnicas y algoritmos para asegurar la confidencialidad, integridad y autenticidad de la información. Utilizando claves secretas o públicas, **la criptografía transforma los datos en un formato incomprensible para terceros no autorizados**, garantizando que solo los destinatarios legítimos puedan acceder a la información original. La criptografía desempeña un papel vital en la seguridad de las comunicaciones y el almacenamiento de datos, protegiendo la privacidad y la confianza en diversos ámbitos de la vida moderna.

* **Encryption:** [el cifrado](https://en.wikipedia.org/wiki/Encryption) es el proceso de convertir información legible en un formato ilegible llamado texto cifrado, mediante el uso de algoritmos y una clave. El objetivo principal del cifrado es proteger la confidencialidad de los datos, asegurando que solo las personas autorizadas puedan acceder y comprender la información cifrada. Para ello, se aplica una serie de transformaciones matemáticas al texto original, lo que dificulta su interpretación sin la clave correspondiente.

* **Cryptographic protocol:** [un protocolo criptográfico](https://en.wikipedia.org/wiki/Cryptographic_protocol) o protocolo de seguridad (también llamado protocolo de cifrado) es un protocolo abstracto o concreto que realiza funciones relacionadas con la seguridad, aplicando métodos criptográficos.​ Un protocolo describe la forma en que un algoritmo debe usarse.

* **Algorithm:** [un algoritmo](https://es.wikipedia.org/wiki/Algoritmo) de cifrado es un procedimiento que convierte un mensaje de texto plano en un texto cifrado. Los algoritmos modernos utilizan matemáticas avanzadas y una o varias claves de cifrado. Esto hace que sea relativamente fácil cifrar un mensaje, pero prácticamente imposible descifrarlo sin conocer las claves requeridas.

## Esquema de cifrado
Estos esquemas definen cómo se realiza la transformación de los datos originales en texto cifrado y cómo se realiza la operación inversa para recuperar los datos originales a partir del texto cifrado. Un esquema de cifrado generalmente consta de los siguientes elementos:

* **Encryption Algorithm:** vimos que es el conjunto de operaciones matemáticas utilizadas para cifrar los datos en texto cifrado.

* **Decryption Algorithm:** es el conjunto de operaciones matemáticas inversas utilizadas para descifrar el texto cifrado y recuperar los datos originales.

* **Key:** conocida como clave, es un valor secreto que se utiliza como entrada para el algoritmo de cifrado. La key determina cómo se realiza la transformación de los datos y es esencial para descifrar el texto cifrado.

* **Protocols:** establecen cómo se utiliza el esquema de cifrado, incluyendo la generación y distribución segura de claves, el manejo de errores y la gestión de la seguridad.

Existen varios tipos de esquemas de cifrado:

1. El [**cifrado simétrico**](https://academy.bit2me.com/que-es-criptografia-simetrica/) (donde se utiliza una sola clave tanto para cifrar como para descifrar),

2. El [**cifrado asimétrico**](https://es.wikipedia.org/wiki/Criptograf%C3%ADa_asim%C3%A9trica) o de clave pública (donde se utilizan pares de claves pública y privada)

3. Otras variantes de esquemas de cifrados como de [flujo](https://es.wikipedia.org/wiki/Cifrador_de_flujo) y de [bloque](https://es.wikipedia.org/wiki/Cifrado_por_bloques). Cada esquema tiene sus propias características y se utiliza en diferentes contextos según los requisitos de seguridad y las necesidades específicas de la aplicación, pero nos centraremos en las principales para entender su funcionamiento antes de pasar a la evolución de las STARKs.