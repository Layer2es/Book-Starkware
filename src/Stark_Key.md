# Creación de una Stark Key en StarkEx
Es importante comprender cómo [StarkEx](https://mirror.xyz/dashboard/edit/KJVQJ6X6wvbf6ps1oy96zpE3TztWyhSIDZd2IHu5NuI) se comunica con otras billeteras en términos de firmas, y cómo mantiene todo el motor de transacciones y pruebas STARKs en su interior.

StarkEx ofrece soluciones altamente especializadas para diferentes aplicaciones que deseen construir sobre su servicio, y esto es parte de lo que StarkWare, como compañía, proporciona a grandes empresas o cualquier otra entidad que desee aprovechar su conjunto de profesionales y servicios adaptables.

Aplicaciones populares como Sorare, Rhino y Apex Pro, por ejemplo, aprovechan las soluciones ofrecidas por StarkWare. Estas aplicaciones específicas se construyen sobre el marco de Starknet. Si bien no profundizaremos en los detalles específicos de estas aplicaciones aquí, se recomienda visitar la [Biblioteca de Layer 2 en Español](https://layer2es.notion.site/39d63a8af9ca4524a7237b1f2456e745) para obtener información más detallada sobre cada una de ellas y comprender mejor cómo se integran en las soluciones de escalado de capa 2 de Ethereum.

Para utilizar StarkEx y asociar tu cuenta de MetaMask u otra billetera a Starknet, es necesario crear una Stark Key. StarkEx admite diferentes tipos de billeteras y métodos para crear esta clave, dependiendo de cómo se utilizará posteriormente. A continuación, se detallan las opciones disponibles:

## Billeteras compatibles con BIP32
Si estás utilizando una billetera compatible con [**BIP32**](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki), como Ledger, se recomienda seguir el EIP-2645. Este estándar describe una ruta denominada `starkPath` y un algoritmo de derivación de clave que utiliza esta ruta para obtener la `starkPrivateKey`.

La `starkPath` está compuesta por cuatro parámetros pasados y dos parámetros internos, y sigue la siguiente estructura:

`m/purpose'/layer'/application'/ethAddress1'/ethAddress2'/index`

Los parámetros externos pasados son los siguientes:

* **Purpose:** el número de EIP correspondiente (en este caso, 2645).
* **Layer:** se utiliza para diferenciar entre tecnologías y se calcula como `sha256(layer) & ((1 << 31) - 1))`. En el contexto de StarkEx, el valor es `579218131` según lo descrito en el EIP-2645.
* **Application:** sirve para diferenciar entre aplicaciones y se calcula como: `sha256(application_name) & ((1 << 31) - 1))`.
* **Index:** permite tener múltiples claves por dirección de Ethereum.

Los parámetros internos usados son los siguientes:

* **ethAddress1:** Los 31 LSB de la dirección Ethereum del usuario, es decir, `(ethAddress & 1 << 31) - 1`
* **ethAddress2:** Los 31 LSB siguientes de la dirección Ethereum del usuario, es decir, `(ethAddress >> 31) & 1 << 31) - `.

Además, es importante que las billeteras compatibles con BIP32 mantengan un estado persistente en relación con su propia dirección de Ethereum.

## Billeteras NO compatibles con BIP32

Si estás utilizando una billetera que no es compatible con BIP32, como MetaMask, se recomienda seguir el siguiente proceso:

1. El usuario firma un mensaje utilizando su clave privada de Ethereum a través de MetaMask u otra billetera similar. Se recomienda utilizar el estándar  IP-712 para brindar transparencia al usuario durante el proceso de firma. Es importante que el mensaje incluya una advertencia, indicando al usuario que so1lo debe firmarlo si proviene de un dominio específico.
2. La firma `(r, s, v)` se utiliza como entrada para el algoritmo de derivación de clave, que generará la `starkPrivateKey`. Para realizar este cálculo, puedes utilizar la biblioteca [StarkEx Crypto SDK](https://www.npmjs.com/package/@starkware-industries/starkware-crypto-utils). Primero, llama a la función `getPrivateKeyFromEthSignature` para obtener la clave privada a partir de la firma, y luego utiliza la función `privateToStarkKey` para calcular la `StarkKey`.

Al seguir estos pasos, podrás crear una Stark Key asociada a tu cuenta de MetaMask u otra billetera compatible. Esta clave te permitirá interactuar con StarkEx y otras aplicaciones dentro del ecosistema de Starknet, realizar transacciones seguras y aprovechar las funcionalidades ofrecidas por esta plataforma.

![graph](./assets/Stark_Key.gif)
<div align="center">
<em></em>
</div>