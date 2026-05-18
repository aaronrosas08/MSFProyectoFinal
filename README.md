 [![Open in MATLAB Online]

# Proyecto Final: Sistema nervioso

## Información del estudiante

Aaron Raul Rosas Montoya \[23210716]; l23210716@tectijuana.edu.mx

Modelado de Sistemas Fisiológicos

Ingeniería Biomédica

## Docente

Dr. Paul Antonio Valle Trujillo; paul.valle@tectijuana.edu.mx

Departamento de Ingeniería Eléctrica y Electrónica, Tecnológico Nacional de México/IT Tijuana, Blvd. Alberto Limón Padilla s/n, Tijuana, C.P. 22454, B.C., México.

## Descripción de la asignatura

El modelizado de sistemas fisiológicos es una herramienta importante en Ingeniería Biomédica, permite comprender el funcionamiento del cuerpo humano, así como diseñar y evaluar terapias y dispositivos médicos; se define como el proceso de formular modelos matemáticos o computacionales que representan el comportamiento y la interacción de los sistemas biológicos y fisiológicos. Esta asignatura pretende aportar al perfil del Ingeniero Biomédico la capacidad de realizar investigación científica en el área de Biología de Sistemas con la finalidad de dirigir y participar en equipos de trabajo interdisciplinarios en contextos nacionales e internacionales, así como de proporcionar soluciones informáticas para resolver problemas en el campo de la Ingeniería Biomédica con ética profesional; lo anterior al proporcionar al estudiante bases sólidas para modelizar sistemas y diseñar controladores para la solución de problemas en las áreas de atención médica y del sector industrial médico. La construcción de analogías entre circuitos eléctricos y sistemas fisiológicos para la formulación de modelos matemáticos y el diseño de controladores mediante la experimentación in silico brindan herramientas de gran aplicación en el quehacer profesional del Ingeniero Biomédico.

La asignatura de Modelado de Sistemas Fisiológicos forma parte del plan de estudios de la carrera en Ingeniería Biomédica con la siguiente competencia general del curso: Utiliza las propiedades de los circuitos RLC para describir la dinámica de sistemas fisiológicos, obtener modelos matemáticos y aplicar el control clásico, esto con el objetivo de integrar los principios de la Ingeniería de Control, la Electrónica Analógica y las Ciencias de la Computación con la Anatomía y Fisiología del cuerpo humano para proporcionar descripciones cuantitativas y cualitativas de sistemas fisiológicos complejos con el objetivo de modelizar, analizar, controlar, ilustrar y predecir su dinámica tanto en el corto como en el largo plazo.

## Objetivos

1. Transformar el modelo fisiológico de transmisión neuronal a un circuito eléctrico usando la analogía tensión-corriente: Ve(t) ↔ potencial de acción, Ie(t) ↔ corriente de conducción axónica, Is(t) ↔ corriente de absorción sináptica, resistencias (R1, R2), capacitor (C), inductor (L).
2. Determinar el modelo de ecuaciones integro-diferenciales.
3. Determinar el error en estado estacionario y la estabilidad del sistema.
4. Construir el diagrama de bloques del sistema en Simulink.
5. Diseñar y sintonizar las ganancias kP, kI y kD con el bloque *PID Controller* y la herramienta *Tune* de Simulink.
6. Obtener la respuesta en lazo abierto y cerrado usando Simulink.
7. Elaborar el diagrama del sistema con BioRender.com.
8. Elaborar un ensayo gráfico.

## Descripción detallada del sistema

El sistema nervioso periférico (SNP) es el conjunto de nervios y ganglios que conectan el sistema nervioso central (SNC) con los órganos, músculos y tejidos del cuerpo. Su función principal es transmitir información sensorial hacia el SNC y llevar respuestas motoras desde este hacia los efectores. La dinámica de transmisión neuronal puede representarse mediante un circuito eléctrico de segundo orden, modelando los procesos de generación, conducción y recepción del impulso nervioso bajo las siguientes suposiciones:
 
1. La generación del potencial de acción en el soma se modela mediante una fuente de voltaje de entrada **Ve(t)**, que representa el estímulo inicial que supera el umbral de despolarización (~−55 mV) y desencadena la apertura masiva de canales de Na⁺.
2. La resistencia axoplasmática al flujo de iones a lo largo del axón se modela con una resistencia **R1**, asociada a la oposición al desplazamiento iónico durante la conducción saltatoria entre nodos de Ranvier.
3. La capacitancia de la membrana axónica se representa con un capacitor **C**, que modela el almacenamiento de carga en la bicapa lipídica y regula la velocidad de cambio del potencial de membrana.
4. La respuesta en la terminal sináptica se modela mediante una segunda rama con un inductor **L** y una resistencia **R2**, representando la inercia iónica en los canales de Na⁺/K⁺ y la resistencia a la despolarización en el nodo receptor, respectivamente.
5. Se identifican los siguientes dos flujos en el sistema: la corriente de conducción axónica **Ie(t)** y la corriente de absorción sináptica **Is(t)**.

## Descripción del circuito RLC
 
1. El circuito está formado por una malla principal que contiene la fuente **Ve(t)** y el resistor **R1**, donde se manifiesta la corriente de conducción axónica **Ie(t)**, mientras que la segunda malla está conformada por un capacitor **C** (membrana axónica) en paralelo con un arreglo en serie del inductor **L** y el resistor **R2** (inercia y resistencia sináptica), por donde circula **Is(t)**.
2. La señal de entrada **Ve(t)** es un escalón unitario, simulando un potencial de acción sostenido ante una alteración fisiológica o patológica.
3. La señal de salida **Vs(t)** se obtiene en el nodo de unión entre ambas mallas, representando el potencial postsináptico efectivo observado en la neurona receptora o en el órgano efector.
4. El sistema presenta una respuesta típica de segundo orden, en donde la rapidez, estabilidad y precisión dependerán de los valores de **R2** y **C**. Para modelar la esclerosis múltiple, **R2** disminuye drásticamente (membrana desmielinizada más permeable) y **C** aumenta considerablemente (mayor área de membrana expuesta), generando un sistema subamortiguado con respuesta neuronal lenta y degradada, reproduciendo clínicamente la fatiga, debilidad muscular y lentitud de reflejos.

## Valores de los componentes
 
| Parámetro | Control (neurona sana) | Caso (esclerosis múltiple) | Componente neuronal | Unidad fisiológica |
|-----------|----------------------|---------------------------|--------------------|--------------------|
| R1 | 1 kΩ | 1 kΩ | Resistencia axoplasmática | K/W |
| R2 | 10 kΩ | 500 Ω | Resistencia de la membrana terminal | K/W |
| L | 10 mH | 10 mH | Inercia iónica | s |
| C | 1 µF | 470 µF | Capacitancia de la bicapa lipídica | J/K |
 
*Palabras clave:* Sistema nervioso periférico; Circuito RLC; Potencial de acción; Conducción saltatoria; Esclerosis múltiple; Desmielinización; Segundo orden; Sinapsis.

## Lista de archivos incluidos en el repositorio

1. Cuaderno computacional de MATLAB \[.mlx].
2. Modelo de Simulink \[.slx].
3. Imagen con los parámetros del controlador.
4. Imágenes de las simulaciones \[.pdf].
5. Evidencia del análisis matemático: función de transferencia, modelo de ecuaciones integro-diferenciales, error en estado estacionario y estabilidad en lazo abierto.
6. Modelo fisiológico en Biorender o BioArt.
7. Ensayo gráfico.
8. Propuesta de proyecto

## Referencias

[1] P. A. Valle, Syllabus para Modelado de Sistemas Fisiológicos, Tecnológico Nacional de México / Instituto Tecnológico de Tijuana, Tijuana, B.C., México, 2025. Permalink: https://biomath.xyz/course/
