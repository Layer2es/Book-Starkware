# Leve introducción Cairo
Como último apartado para finalizar este documento, antes de adentrarnos en los próximos temas sobre la arquitectura de Starknet y Cairo, haremos una breve introducción a Cairo y su relación con la CVM. En este contexto, es relevante comprender cómo todos los pasos de un cálculo pueden ser representados mediante polinomios, utilizando lo que se conoce como la Representación Algebraica Intermedia (AIR).

Los bloques de cálculo pueden ser representados como AIR y tienen la capacidad de combinarse entre sí, lo que se convierte en la base de Cairo. Para ilustrarlo mediante una analogía con el hardware:

* **ASIC (AIR)**
* **CPU (varias AIR)**

El nombre **Cairo** deriva de una CPU construida a partir de AIRs:

* **(CPU-AIR, Oh genial -> CAIRO)**

Cairo es un lenguaje funcional de alto nivel, no determinista y Turing completo, que cuenta con un modelo de memoria basado en registros y un compilador, el cual  produce una tabla de pasos computacionales llamada traza.

> En los programas escritos en Cairo, se especifican los resultados que se consideran aceptables, no cómo obtenerlos.

Vimos como en el proceso de construcción de pruebas STARK, el prover utiliza esta traza para crear Representaciones Algebraicas Intermedias (AIRs), que luego se combinan y se convierten en pruebas STARK.