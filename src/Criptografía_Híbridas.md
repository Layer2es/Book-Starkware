# Criptografía Híbrida
El [**cifrado híbrido**](https://es.wikipedia.org/wiki/Criptograf%C3%ADa_h%C3%ADbrida) utiliza las propiedades únicas de la criptografía de clave pública para intercambiar información secreta a través de un canal no confiable, combinando la eficacia del cifrado simétrico. Esto proporciona una solución práctica de extremo a extremo para garantizar la privacidad de los datos.

Aunque los algoritmos de clave pública, como RSA-OAEP, son menos eficientes que los algoritmos simétricos, generalmente no se utilizan directamente para cifrar los datos. Sin embargo, desempeñan un papel importante en el ecosistema criptográfico al permitir el intercambio seguro de claves.

Para utilizar el cifrado simétrico, las partes deben compartir una clave. Si ya existe un canal seguro, se puede enviar la clave a través de él. Sin embargo, si no hay un canal seguro disponible, se resuelve el problema del intercambio de claves utilizando la criptografía de clave pública.

* **DH -** [**Diffie–Hellman:**](https://en.wikipedia.org/wiki/Diffie%E2%80%93Hellman_key_exchange) el intercambio de claves DH es un algoritmo criptográfico de clave pública diseñado específicamente para acordar una clave simétrica en ausencia de un canal seguro.
La combinación de criptografía de clave pública para el intercambio de claves y el cifrado simétrico para el cifrado de datos en masa se conoce como cifrado híbrido.

El cifrado híbrido se utiliza ampliamente en los protocolos de transferencia de datos para la web, como en la capa de seguridad de transporte [(TLS)](https://en.wikipedia.org/wiki/Transport_Layer_Security). Cuando te conectas a un sitio web que utiliza [HTTPS](https://en.wikipedia.org/wiki/HTTPS) (HTTP seguro con TLS), tu navegador negocia los algoritmos criptográficos que aseguran la conexión. Estos algoritmos incluyen métodos para el intercambio de claves, cifrado simétrico y firmas digitales.