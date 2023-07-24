# Headers Store
El contrato HeadersStore refleja los encabezados de las cadenas admitidas en el almacenamiento del state de este contrato. Estos encabezados solo pueden agregarse si el del encabezado `parentHash` ya ha sido pasado al `CommitmentsInbox`.

Cualquier persona puede enviar encabezados, pero un encabezado solo es válido si su hash calculado en la cadena coincide con el hash certificado previamente por el `CommitmentsInbox`.

Cada vez que se procesa un encabezado, se guarda el hash de su encabezado padre en el estado del contrato para permitir que el encabezado anterior en la cadena se procese de la misma manera.

Al procesar un bloque, sus parámetros pueden guardarse en el estado inteligente de los contratos. Cada cadena blockchain contiene diferentes parámetros en su encabezado. Por ejemplo, un encabezado de EVM en Ethereum L1 contiene las siguientes propiedades:

* [**baseFeePerGas**](https://ethereum.org/en/developers/docs/gas/#base-fee)
* [**difficulty**](https://ethereum.org/en/glossary/#difficulty)
* [**extraData**]()
* [**gasLimit**](https://ethereum.org/en/glossary/#gas-limit)
* [**gasUsed**]()
* [**parentHash**]()
* [**receiptsRoot**]()
* [**transactionsRoot**]()
* [**stateRoot**]()
* [**timestamp**]()
* [**logsBloom**]()
* [**nonce**]()
* [**miner**]()
* [**mixHash**]()
* [**sha3Uncles**]()
* [**number**]()
* [**extraData**]()

La especificación de los parámetros que deben guardarse se realiza mediante un valor entero que codifica un mapa desde el índice del parámetro hasta si debe guardarse o no. Los índices para cada parámetro son:

* `PARENT_HASH = 0`
* `UNCLES_HASH = 1`
* `MINER = 2`
* `STATE_ROOT = 3`
* `TRANSACTION_ROOT = 4`
* `RECEIPTS_ROOT = 5`
* `LOGS_BLOOM = 6`
* `DIFFICULTY = 7`
* `BLOCK_NUMBER = 8`
* `GAS_LIMIT = 9`
* `GAS_USED = 10`
* `TIMESTAMP = 11`
* `EXTRA_DATA = 12`
* `MIX_HASH = 13`
* `NONCE = 14`
* `BASE_FEE = 15`

Por ejemplo, para establecer solo la `STATE_ROOT`, el valor para ese parámetro sería 8, ya que su representación binaria es `000000000001000`, lo cual es igual a `2^3`, donde `3` es el índice de la `STATE_ROOT`.