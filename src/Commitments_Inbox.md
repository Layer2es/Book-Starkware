# Commitments Inbox
Cada vez que se accede a datos provenientes de un dominio diferente en otro dominio, se requiere un compromiso para asegurar su corrección criptográfica. Estos compromisos pueden ser:

1. State root
2. Block hash
3. Transactions root
4. Receipts root

El contrato `CommitmentsInbox` se encarga de recibir y gestionar estos compromisos. Los compromisos pueden entregarse de diversas formas, como:

1. Recibir mensajes asíncronos.
2. Validar el consenso de la red de manera verificable (disponible solo para L2 descentralizados).
3. Utilizar relayers optimistas.

Una vez que un compromiso es aceptado por el `CommitmentsInbox`, se pasa al `HeadersStore`.
