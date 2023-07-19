# Aritmetización
Tenemos dos pasos principales en este proceso:

1. Generación de una traza de ejecución y restricciones polinómicas.
2. Transformar estos dos objetos en un único polinomio de bajo grado.

En términos de interacción prover-verifier, realmente lo que ocurre es que entre ambos acuerdan de antemano cuáles son las restricciones polinómicas.

A continuación, el prover genera una traza de ejecución y, en la interacción posterior, intenta convencer al verificador de que las restricciones polinómicas se cumplen en esta traza de ejecución, sin que el verificador lo vea.

La traza de ejecución es una tabla que representa los pasos del cálculo subyacente, donde cada fila representa un único paso y el tipo de traza de ejecución que buscamos generar debe tener la característica especial de ser sucintamente comprobable:

* Cada fila puede ser verificada basándose sólo en las filas que están cerca de ella en la traza, y el mismo procedimiento de verificación se aplica a cada par de filas.

Por ejemplo, imaginemos que nuestra traza representa un total en ejecución, con cada paso de la siguiente manera.

```bash
                    ╔════════╦═══════════╦═══════╗
                    ║  PASO  ║  IMPORTE  ║ TOTAL ║
                    ╠════════╬═══════════╬═══════╣
                    ║   0    ║     0     ║   0   ║
                    ╠════════╬═══════════╬═══════╣
                    ║   1    ║     5     ║   5   ║
                    ╠════════╬═══════════╬═══════╣
                    ║   2    ║     2     ║   7   ║
                    ╠════════╬═══════════╬═══════╣
                    ║   3    ║     2     ║   9   ║
                    ╠════════╬═══════════╬═══════╣
                    ║   4    ║     3     ║   12  ║
                    ╠════════╬═══════════╬═══════╣
                    ║   5    ║     6     ║   18  ║
                    ╚════════╩═══════════╩═══════╝
```

Si representamos la fila como `i` , y la columna como `j` , y los valores como `Aᵢ,ⱼ` , podríamos escribir algunas restricciones sobre esto de la siguiente manera:

* `A₀,₂=0`
* `∀1 >= i <= 5 : Aᵢ,₂ − Aᵢ,₁ − Aᵢ-₁,₂ = 0`
* `A₅,₂ = 18`

Se trata de restricciones polinómicas lineales en `Aᵢ,ⱼ`

Nótese que aquí estamos consiguiendo cierta concisión porque podríamos representar un número mucho mayor de filas con sólo estas 3 restricciones.

El sistema de restricciones aritméticas define al menos dos tipos de restricciones sobre la traza de ejecución algebraica:

1. **Restricciones de contorno:** al principio o al final del cálculo, un registro indicado tiene un valor determinado.
2. **Restricciones de transición:** dos tuplas de estado consecutivas cualesquiera evolucionan de acuerdo con la función de transición de estado. En conjunto, estas restricciones se conocen como representación algebraica intermedia o AIR.

Las STARKs avanzadas pueden definir más tipos de restricciones para tratar con la memoria o con la consistencia de los registros dentro de un ciclo.