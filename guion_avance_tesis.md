# Guion de exposición – Avance de Tesis 1 (1IBM24)

**Título:** Diseño de un sistema de apoyo basado en deep learning para la detección de patrones de neumonía mediante sonidos respiratorios y radiografías de tórax en zonas rurales
**Autor:** Renzo William Luna Aliaga | **Asesor:** Pedro Crisostomo
**Público:** estudiantes de Ingeniería Biomédica y profesora del curso

**Duración planificada: ~22 min** (límite 25 min, con ~3 min de colchón).
Habla a ~130 palabras por minuto. Los tiempos son referenciales; cada diapositiva indica su tiempo acumulado.

| # | Diapositiva | Tiempo | Acumulado |
|---|---|---|---|
| 1 | Portada | 0:40 | 0:40 |
| 2 | Índice | 0:20 | 1:00 |
| 3 | Introducción: mortalidad global | 1:15 | 2:15 |
| 4 | Introducción: situación en Perú y brecha rural | 1:30 | 3:45 |
| 5 | Pregunta de investigación | 0:50 | 4:35 |
| 6 | Objetivos | 1:15 | 5:50 |
| 7 | Marco teórico: NAC y pruebas de diagnóstico | 1:15 | 7:05 |
| 8 | Marco teórico: sonidos adventicios | 1:15 | 8:20 |
| 9 | Marco teórico: hallazgos auscultatorios | 1:00 | 9:20 |
| 10 | Marco teórico: hallazgos radiográficos | 1:15 | 10:35 |
| 11 | Marco teórico: comparación radiográfica | 0:50 | 11:25 |
| 12 | Marco teórico: establecimientos de salud e IA | 1:30 | 12:55 |
| 13 | Estado del arte: sonidos, comerciales | 1:00 | 13:55 |
| 14 | Estado del arte: sonidos, académicos | 1:30 | 15:25 |
| 15 | Estado del arte: radiografía, comerciales | 0:50 | 16:15 |
| 16 | Estado del arte: radiografía, académicos | 0:50 | 17:05 |
| 17 | Metodología (visión general) | 2:45 | 19:50 |
| 18 | Metodología hasta ahora (datasets) | 1:30 | 21:20 |
| 19 | Bibliografía | 0:15 | 21:35 |
| 20 | Cierre | 0:45 | 22:20 |

> **Si te pasas de tiempo:** acorta primero las diapositivas 9, 11 y 15 (resúmelas en 2 frases cada una). No recortes la 17 ni la 18, que son tu avance real.

---

## Diapositiva 1 – Portada (0:40)

Buenos días/tardes. Mi nombre es Renzo Luna, estudiante de décimo ciclo de Ingeniería Biomédica, y hoy les presento el avance de mi proyecto de tesis, asesorado por Pedro Crisostomo.

El proyecto se titula: *Diseño de un sistema de apoyo basado en deep learning para la detección de patrones de neumonía mediante sonidos respiratorios y radiografías de tórax en zonas rurales*.

En los próximos minutos les voy a contar por qué este problema importa, qué se ha hecho en el mundo para resolverlo, y cuál es la metodología que propongo y en qué punto me encuentro.

---

## Diapositiva 2 – Índice (0:20)

La presentación sigue esta estructura: primero la introducción, luego la pregunta de investigación y los objetivos, después el marco teórico y el estado del arte, y finalmente la metodología, donde voy a mostrar mi avance. Cierro con las referencias.

---

## Diapositiva 3 – Introducción: mortalidad global (1:15)

Empiezo con una definición. La neumonía es una infección pulmonar causada por microorganismos. Además de la infección en sí, puede desencadenar comorbilidades crónicas y un deterioro cognitivo importante, y puede progresar a complicaciones potencialmente mortales.

A nivel global, según el estudio GBD 2023, la neumonía causó **2.5 millones de muertes** en 2023. Y lo que más pesa es que se concentra en los extremos de la vida: **610 mil muertes en menores de 5 años** y **1.2 millones en mayores de 70 años**. Por eso mi proyecto se enfoca en población pediátrica y geriátrica.

Si miramos las tasas de mortalidad según IHME, vemos valores de 50.2 por cada 100 mil habitantes en África y 47.9 en Sudamérica. Es decir, nuestra región no está lejos de las zonas más afectadas del mundo.

Y hay factores que empeoran el riesgo: la contaminación del aire y la baja concientización sobre la vacunación.

---

## Diapositiva 4 – Introducción: situación en Perú y brecha rural (1:30)

Pasando al Perú. En el periodo reportado hubo **84,448 casos** y **2,320 muertes**. Fíjense cómo se distribuye: en menores de 5 años, 24.67% de incidencia y 107 muertes; en mayores de 60 años, **37.67% de incidencia y 1,884 muertes**. El grueso de las muertes está en adultos mayores, pero los niños también son un grupo crítico.

Ahora, ¿por qué las zonas rurales? Porque ahí se junta una brecha de tres tipos.

Primero, **riesgo**: el descenso de cobertura de vacunas se asoció a 75 muertes en menores de cinco años hasta junio de 2024, y esto se agrava en zonas altoandinas y amazónicas.

Segundo, **personal médico**: hay 17.9 médicos por cada 10 mil habitantes y solo 1 tecnólogo radiológico por cada 16.6 mil habitantes. Además, el 76% de los establecimientos reporta problemas de capacitación en el manejo de equipos, específicamente estetoscopio y rayos X.

Tercero, **dispositivos médicos**: hay problemas de conectividad y acceso limitado a equipos de auscultación.

De aquí sale la necesidad: una herramienta confiable que interprete con alta precisión los patrones acústicos y radiográficos asociados a la neumonía. Y mi propuesta de solución es un sistema basado en deep learning.

---

## Diapositiva 5 – Pregunta de investigación (0:50)

Con ese contexto, la pregunta de investigación es:

*¿En qué medida un sistema de apoyo basado en deep learning, que tenga implementados modelos independientes de análisis de sonidos auscultatorios y de radiografía de tórax, permite detectar patrones asociados a neumonía con un desempeño adecuado para su aplicación en zonas rurales con acceso limitado a servicios de salud especializados?*

Quiero resaltar dos palabras: **modelos independientes**, porque un modelo procesa audio y otro procesa imagen, y luego se integran sus salidas; y **desempeño adecuado**, porque lo que voy a medir es si el sistema es lo bastante bueno para un contexto rural, no solo si funciona en laboratorio.

---

## Diapositiva 6 – Objetivos (1:15)

El **objetivo general** es diseñar y validar un sistema de apoyo basado en deep learning para detectar patrones asociados a neumonía, que integre el análisis de sonidos auscultatorios y de radiografía de tórax, enfocado en pacientes pediátricos y geriátricos de zonas rurales con acceso limitado a servicios de salud especializados.

Para lograrlo, planteo cinco **objetivos específicos** que siguen el orden natural del proyecto:

1. Realizar el estudio bibliográfico de la problemática, que es lo que estoy cerrando en esta etapa.
2. Establecer los requerimientos del sistema para el análisis de sonidos y radiografía.
3. Seleccionar datasets confiables, considerando la población etaria a evaluar.
4. Desarrollar el modelo de deep learning para detectar los patrones acústicos y radiográficos.
5. Diseñar un esquema de fusión de las salidas de ambos modelos e implementarlo en una plataforma que funcione con conectividad inestable y que pueda usar personal de salud no especializado.
6. Y finalmente validar el desempeño con métricas de clasificación.

Hoy les voy a mostrar principalmente avance en los tres primeros.

---

## Diapositiva 7 – Marco teórico: neumonía adquirida en la comunidad y pruebas de diagnóstico (1:15)

Entrando al marco teórico. Me enfoco en la **neumonía adquirida en la comunidad**, que es el tipo más común y se adquiere fuera del entorno hospitalario. Los agentes invaden y proliferan en el parénquima pulmonar, generan una respuesta inflamatoria y esto favorece la acumulación de exudado en los alvéolos, que es justamente lo que luego vamos a "ver" en la radiografía y a "escuchar" en la auscultación.

Por agente causal: las **bacterias** explican entre 60 y 70% de los casos, con *Streptococcus pneumoniae*, *Haemophilus influenzae*, *Mycoplasma pneumoniae* y *Staphylococcus aureus*. Los **virus** explican entre 30 y 40%, con VRS, metapneumovirus, rinovirus e influenza. Y los **hongos** son menos del 1.2%.

A la derecha, las pruebas de diagnóstico: radiografía, auscultación, ecografía, tomografía y estudios microbiológicos. Resalté en negrita la **radiografía de tórax** y la **auscultación pulmonar** porque son las dos que uso en mi proyecto: son las más accesibles en un primer nivel de atención, a diferencia de la tomografía o los estudios microbiológicos.

---

## Diapositiva 8 – Marco teórico: sonidos adventicios (1:15)

Pasemos al audio. Los **sonidos adventicios** son sonidos anormales que se escuchan durante la auscultación pulmonar. Hay tres principales.

Las **sibilancias** son sonidos continuos, agudos y musicales. Se producen cuando el aire pasa por vías aéreas muy estrechas u obstruidas, y su frecuencia suele estar por encima de 100 Hz, pudiendo llegar a 1200 Hz o más.

Los **roncus** son continuos pero graves, parecidos a un ronquido. Se deben a obstrucción o secreciones en las vías aéreas grandes, y están generalmente por debajo de 200 Hz.

Los **crepitantes** son discontinuos y cortos, como burbujeo o velcro. Aparecen por la apertura brusca de vías aéreas colapsadas o por líquido en los alvéolos. Los finos están entre 650 y 1000 Hz; los gruesos suelen estar por debajo de 350 Hz.

¿Por qué esto importa para el modelo? Porque estas diferencias de frecuencia y duración son exactamente lo que una red puede aprender a distinguir en un espectrograma. Y también explica por qué más adelante filtro la señal entre 50 y 2000 Hz.

---

## Diapositiva 9 – Marco teórico: comparación de hallazgos auscultatorios (1:00)

Aquí comparo un pulmón sano con uno con neumonía, usando los cuatro componentes de la exploración física.

En el **sonido respiratorio de base**, el pulmón sano tiene murmullo vesicular, de baja intensidad y tono grave. En neumonía hay respiración bronquial sobre la zona consolidada: más intensa y de tono más agudo.

En los **sonidos adventicios**, el pulmón sano no tiene; en neumonía aparecen sobre todo crepitantes finos inspiratorios localizados en la zona afectada, y a veces sibilancias o roncus.

En **frémito y resonancia vocal**, en neumonía el frémito está aumentado, con egofonía y broncofonía positivas. Y en la **percusión**, hay matidez sobre la consolidación.

Lo importante: de estos cuatro hallazgos, el que el audio de un estetoscopio puede capturar es el de los sonidos, y de ahí sale la información que alimenta al modelo de audio.

---

## Diapositiva 10 – Marco teórico: hallazgos radiográficos (1:15)

Ahora la parte de imagen. Un hallazgo radiográfico es un patrón visual que puede describirse, medirse y cuantificarse de manera automática, y eso es lo que lo hace candidato para deep learning.

Los principales son:

- **Radiodensidad de los campos pulmonares**: cuántos rayos X atraviesan el pulmón. El pulmón sano es oscuro y homogéneo; en neumonía aumenta la radiodensidad y se ve más claro.
- **Patrón de la opacidad**: la distribución y forma del aumento de densidad, que puede ser alveolar, como en una consolidación lobar, o intersticial.
- **Broncograma aéreo**: bronquios llenos de aire dentro de la zona de consolidación.
- **Vasculatura pulmonar**: deformación de las marcas vasculares en la zona afectada.
- **Signo de la silueta**: pérdida del borde de un tejido adyacente cuando entra en contacto con otro tejido.
- **Volumen pulmonar** y **otros hallazgos**, como atelectasia o derrame pleural.

---

## Diapositiva 11 – Marco teórico: comparación de hallazgos radiográficos (0:50)

Esta diapositiva resume visualmente esas diferencias. A la izquierda tenemos el pulmón sano, con campos radiolúcidos, marcas vasculares nítidas, volumen normal y sin hallazgos asociados. A la derecha, el pulmón con neumonía: opacidad más radiodensa, consolidación lobar u opacidades parcheadas, broncograma aéreo, pérdida del borde de estructuras adyacentes, marcas vasculares borradas y, en algunos casos, derrame pleural.

Estas imágenes también muestran la dificultad del problema: el patrón no siempre es igual de claro, y por eso en zonas rurales, sin un radiólogo disponible, se necesita una herramienta de apoyo.

---

## Diapositiva 12 – Marco teórico: establecimientos de salud e inteligencia artificial (1:30)

Esta diapositiva conecta dos ideas.

A la izquierda, la **pirámide de establecimientos de salud**: primer, segundo y tercer nivel. Mi proyecto apunta al **primer nivel**, resaltado en rojo en el nivel I-4, que es donde está la población rural y donde faltan especialistas y equipos. *(Completa aquí tu justificación de por qué I-4, si la tienes.)*

A la derecha, el marco de **inteligencia artificial**. El procesamiento de datos tiene cuatro etapas: dataset, preprocesamiento, **extracción de características** y división de datos. Resalté la extracción de características porque es donde ambos tipos de dato se transforman.

Para **sonidos respiratorios**, las técnicas más usadas son coeficientes cepstrales en las frecuencias mel (MFCC), la no gaussianidad, la transformada de Fourier y la transformada wavelet. Para **radiografías**, se usan también MFCC, Fourier y wavelet, además de la matriz de ocurrencia de niveles de gris y el histograma de gradientes orientados. Estas técnicas son la base de la metodología que voy a mostrar más adelante.

---

## Diapositiva 13 – Estado del arte: sistemas de sonidos respiratorios, antecedentes comerciales (1:00)

Pasemos al estado del arte, empezando por los sistemas basados en sonidos respiratorios. Primero los comerciales, que muestran que esta idea ya es viable.

**ResApp Dx** es una aplicación móvil que usa machine learning sobre el sonido de la tos para distinguir entre neumonía, asma, bronquitis y bronquiolitis.

**TytoCare** combina un dispositivo portátil con una plataforma de IA para auscultación pulmonar, detectando crepitantes, sibilancias y roncus. Reporta un AUC de 95.85% con 1.8 millones de grabaciones. Además, ya se comercializa en Perú, como figura en mi bibliografía.

**Stethome AI** usa un estetoscopio digital conectado al celular, con una red neuronal convolucional que analiza el espectrograma y entrega probabilidades por tipo de sonido, y cuenta con certificación CE.

La lección: la tecnología existe, pero son soluciones propietarias y de costo, y no necesariamente adaptadas a las condiciones rurales del Perú.

---

## Diapositiva 14 – Estado del arte: sistemas de sonidos respiratorios, antecedentes académicos (1:30)

Ahora lo académico, donde está la parte más cercana a mi propuesta.

**DeepBreath (Heitmann et al., 2023)**: un estudio multicéntrico, con datos de Brasil y Suiza y validación externa en África, en población pediátrica. Recolectan 8 sitios torácicos por paciente, preprocesan con filtro pasa-banda, log-mel y aumento de datos, clasifican con una CNN, agregan los resultados por sitio y predicen por paciente con regresión logística. Para neumonía alcanzan un **AUC-ROC de 0.75 interno y 0.74 externo**. Es un buen ejemplo de validación externa, pero el desempeño es moderado.

**Hoekstra (2025)**: usa estetoscopio digital y un algoritmo de IA que clasifica sonidos como normales o anormales. Logra sensibilidad de 80.3% por posición y 87.2% por paciente, pero tiene una limitación: **no distingue entre sibilancias y crepitantes**.

**Vidhya et al. (2022)**: graban audio, lo limpian con Audacity, extraen 13 coeficientes MFCC, normalizan y clasifican con Gradient Boosting, alcanzando **97% de precisión**. Es un resultado alto, pero con un modelo clásico y un conjunto de datos más controlado.

Lo que me llevo: los resultados en entornos más realistas son más modestos que los reportados en estudios controlados, y casi ninguno integra audio con imagen. Ese es el espacio de mi proyecto.

---

## Diapositiva 15 – Estado del arte: sistemas de radiografía, antecedentes comerciales (0:50)

En radiografía, los sistemas comerciales están más maduros.

**qXR de Qure.ai** combina CNN con procesamiento de lenguaje natural para generar informes, detecta consolidación, opacidad y nódulos, con sensibilidad de 91% y especificidad de 84%.

**Insight CXR de Lunit** procesa una imagen en 10 segundos, detecta 11 hallazgos, con AUC de 0.923, sensibilidad de 95.4% y especificidad de 66%.

**Med-Chest X-ray de Vuno** detecta cinco hallazgos principales, entre ellos consolidación y derrame pleural, y se presenta explícitamente como apoyo al diagnóstico, que no reemplaza al médico, que es el mismo enfoque que adopto.

---

## Diapositiva 16 – Estado del arte: sistemas de radiografía, antecedentes académicos (0:50)

En lo académico hay dos referentes.

**CheXNet (Rajpurkar et al., 2017)** usa una DenseNet de 121 capas para clasificar radiografías de tórax y detectar neumonía, y se volvió la referencia del campo.

**Pneumo.AI (Schneider y Sifa, 2024)** usa una red convolucional que clasifica como tejido sano o sospecha de neumonía y genera un mapa de calor de las zonas afectadas. Procesa en tiempo real y tiene una interfaz explicable.

Las dos ideas que rescato son: arquitecturas preentrenadas tipo DenseNet como base, y la **explicabilidad** con mapas de calor, importante para que el personal no especializado confíe en la herramienta.

---

## Diapositiva 17 – Metodología: visión general (2:45)

Llegamos a la metodología, que tiene tres bloques.

### Bloque 1: procesamiento de datos

**Adquisición.** Para audio uso la base ICBHI-2017. Para imagen, uso dos datasets según la población: *Chest X-Ray Images (Pneumonia)* para pediatría y *3 kinds pneumonia* para geriatría. Las etiquetas son neumonía / no neumonía y, en imagen, también normal / bacteriana / viral. Registro como metadatos el grupo etario, el sitio de auscultación y el dispositivo.

**Preprocesamiento.** En audio: remuestreo a 4–8 kHz, filtro pasa-banda de 50 a 2000 Hz, reducción de ruido, y normalización y segmentación. En imagen: redimensionado a 224–512 píxeles, normalización de intensidad, CLAHE con recorte pulmonar, y aumentos de datos como rotación, brillo y contraste.

**Extracción de características.** En audio: MFCC, DFT y DWT. En imagen: características de textura y de frecuencia, con DFT y DWT.

**División de datos.** Aquí tengo un signo de interrogación: es una decisión pendiente, que voy a definir en la siguiente etapa. Mi criterio será dividir por paciente para evitar fuga de datos, y mantener balance por clase y grupo etario.

### Bloque 2: desarrollo del modelo

La arquitectura tiene una **rama de audio** y una **rama de imagen**, cada una con su modelo, que se combinan en un módulo de **fusión** para una clasificación final. Hoy, la arquitectura exacta de cada rama y el método de fusión están marcados con interrogante porque **todavía los estoy definiendo**. Como mi pregunta de investigación habla de modelos independientes, la fusión sería a nivel de decisión, combinando las probabilidades de cada modelo.

Luego, el ciclo estándar de entrenamiento: función de pérdida, retropropagación, ajuste de hiperparámetros y evaluación con métricas de clasificación.

### Bloque 3: implementación

El sistema se desplegaría como app móvil o página web, con procesamiento local o en la nube, una guía de captura para quien no es especialista, y una alerta de referencia a un centro de mayor nivel. Recalco que es un **sistema de apoyo y no reemplaza el diagnóstico médico**. Después, monitoreo del desempeño en campo, de la calidad de los datos, y reentrenamiento con datos nuevos.

---

## Diapositiva 18 – Metodología hasta ahora (1:30)

Esta diapositiva muestra el **avance concreto** hasta hoy: la parte de procesamiento de datos, con los datasets ya seleccionados.

Para **audio**, elegí la *Respiratory Sound Database* de ICBHI-2017, disponible en Kaggle. Es una base pública muy usada en la literatura de sonidos respiratorios, lo que me permite comparar con trabajos previos.

Para **imagen**, elegí dos datasets, también de Kaggle, para cubrir las dos poblaciones del objetivo: *Chest X-Ray Images (Pneumonia)* para el grupo pediátrico y *3 kinds pneumonia* para el grupo geriátrico.

Con esto cumplo el tercer objetivo específico, seleccionar datasets considerando la población etaria. Aun así, soy consciente de limitaciones que quiero abordar en la siguiente etapa: estos datos no fueron capturados necesariamente con smartphone, y los datos de audio e imagen provienen de **pacientes distintos**, lo que justifica trabajar con modelos independientes y fusionar a nivel de decisión.

**Próximos pasos:** implementar el preprocesamiento y la extracción de características, definir la división de datos, y entrenar los primeros modelos de línea base.

---

## Diapositiva 19 – Bibliografía (0:15)

Esta es la bibliografía que sustenta el trabajo hasta ahora: fuentes epidemiológicas, guías clínicas, revisiones sistemáticas y los trabajos de sonidos respiratorios y radiografía que comenté. Quedo atento a sugerencias de fuentes adicionales.

---

## Diapositiva 20 – Cierre (0:45)

Para cerrar, tres ideas.

Primero, la neumonía sigue siendo una causa importante de muerte en niños y adultos mayores, y la brecha en zonas rurales del Perú es real: faltan especialistas, equipos y conectividad.

Segundo, el estado del arte muestra que la IA funciona tanto en audio como en radiografía, pero casi no hay sistemas que integren ambas modalidades pensados para el contexto rural.

Tercero, mi avance es el diseño de la metodología y la selección de datasets, y los próximos pasos son preprocesar, extraer características, definir la arquitectura y la fusión, y entrenar los primeros modelos.

Muchas gracias. Quedo atento a sus preguntas y comentarios.

---

# Anexo A – Posibles preguntas del jurado y cómo responder

**1. ¿Por qué modelos independientes y no un solo modelo multimodal?**
Porque los datasets de audio e imagen provienen de pacientes distintos; no existe un conjunto emparejado paciente por paciente. Con modelos independientes puedo entrenar cada uno con su dataset y fusionar a nivel de decisión.

**2. ¿ICBHI sirve para detectar neumonía?** *(verifica los números antes de exponer)*
ICBHI está etiquetado por diagnóstico del paciente y tiene pocos casos de neumonía en relación con otras patologías. Es una limitación que debes reconocer: por eso conviene plantear un enfoque de línea base, técnicas de balanceo y, a futuro, datos propios o con smartphone.

**3. ¿Cómo garantizas que "3 kinds pneumonia" representa población geriátrica?**
Es un punto débil si no puedes sustentarlo. Revisa la documentación del dataset para ver si trae edad o fuente. Si no la trae, preséntalo como "dataset de neumonía en adultos" y declara la limitación.

**4. ¿Cómo manejarás el desbalance de clases?**
Ponderación de la función de pérdida o focal loss, aumento de datos y métricas robustas al desbalance (sensibilidad, especificidad, F1, AUC).

**5. ¿Qué métricas priorizas?**
Sensibilidad, porque en un contexto de tamizaje rural es peor perder un caso que generar una falsa alarma; también especificidad, F1 y AUC-ROC, reportadas por grupo etario y por modalidad.

**6. ¿Cómo funcionará sin internet?**
Modelo liviano (cuantizado) ejecutado localmente en el teléfono, con sincronización cuando haya conexión para monitoreo y reentrenamiento.

**7. ¿Por qué el nivel I-4?**
Prepara tu justificación para esta pregunta (capacidad resolutiva, disponibilidad de equipos, volumen de referencia).

# Anexo B – Correcciones sugeridas en las diapositivas antes de exponer

- Diap. 4: "Acceso **ilimitado** de equipos de auscultación" → debería decir **limitado**.
- Diap. 8: "WHEEZLES" → **Wheezes**; "RONCUS" → **Rhonchi/Roncus** consistente con el texto.
- Diap. 10: "interticial" → **intersticial**; "Precencia" → **Presencia**.
- Diap. 16: "DenseNet-21 (121 capas)" → **DenseNet-121**.
- Diap. 13: los títulos y siglas de las diapositivas de sistemas deberían llevar la cita de fuente (ResApp Dx, Stethome AI, qXR, Lunit, Vuno) en bibliografía; hoy solo aparece TytoCare.
- Diap. 18: el enlace del dataset pediátrico apunta a la URL del dataset de audio (`.../vbookshelf/respiratory-sound-database`); corrígelo al de *Chest X-Ray Images (Pneumonia)*.
- Diap. 17: dos diapositivas distintas con "Metodología" y "Metodología (hasta ahora)"; asegúrate de que el título deje claro qué es propuesta y qué es avance.
