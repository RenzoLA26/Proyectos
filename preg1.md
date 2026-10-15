Aquí tienes el desarrollo paso a paso y la resolución completa de la *Pregunta 1*:

---

### *Parámetros del Sistema y Geometría del Transductor*

1. *Transductor Curvo (Convex Array)*:
   * *Número de elementos*: \\(N = 13\\) (índices \\(n \in \{-6, -5, -4, -3, -2, -1, 0, 1, 2, 3, 4, 5, 6\}\\)).
   * *Radio de curvatura*: \\(R = 40\text{ cm} = 400\text{ mm}\\).
   * *Pitch (separación de elementos)*: \\(d = 0.3\text{ mm}\\).
   * *Elemento central (\\(n = 0\\))*: Ubicado en el origen \\((x_0, z_0) = (0, 0)\text{ mm}\\).
   * *Frecuencia central*: \\(f_0 = 3\text{ MHz}\\) (período \\(T_0 = 1/f_0 = 0.3333\ \mu\text{s} = 333.33\text{ ns}\\)).
   * *Frecuencia de muestreo*: \\(f_s = 60\text{ MHz}\\) (período de muestreo \\(T_s = 1/f_s = 0.01667\ \mu\text{s} = 16.67\text{ ns}\\)).
   * *Velocidad del sonido*: \\(c = 1540\text{ m/s} = 1.54\text{ mm/}\mu\text{s}\\).

2. *Coordenadas de cada elemento \\((x_n, z_n)\\)*:
   * *Separación angular*: \\(\Delta \theta = \frac{d}{R} = \frac{0.3\text{ mm}}{400\text{ mm}} = 0.00075\text{ rad} = 0.04297^\circ\\).
   * Para el elemento \\(n\\):
     \\[x_n = R \cdot \sin(n \cdot \Delta \theta)\\]
     \\[z_n = R \cdot \cos(n \cdot \Delta \theta) - R \approx -\frac{x_n^2}{2R}\\]

   * *Ubicación de los elementos extremos (\\(n = \pm 6\\))*:
     * \\(x_{\pm 6} = 400 \cdot \sin(\pm 6 \times 0.00075) = \pm 1.799994\text{ mm} \approx \mathbf{\pm 1.80\text{ mm}}\\).
     * \\(z_{\pm 6} = 400 \cdot \cos(\pm 6 \times 0.00075) - 400 = -0.004050\text{ mm} = \mathbf{-4.05\ \mu\text{m}}\\).

---

### *a) Enfoque en \\((x, z) = (0, 8)\text{ cm} = (0, 80)\text{ mm}\\)*

1. *Distancia de cada elemento al punto focal \\((x_f, z_f) = (0, 80)\text{ mm}\\)*:
   \\[D_n = \sqrt{(x_f - x_n)^2 + (z_f - z_n)^2} = \sqrt{(0 - x_n)^2 + (80 - z_n)^2}\\]

   * *Elemento central (\\(n = 0\\))* (mínima distancia):
     \\[D_0 = \sqrt{0^2 + (80 - 0)^2} = \mathbf{80.000000\text{ mm}}\\]
     \\[\text{TOF}_{\text{mín}} = \frac{80.000000\text{ mm}}{1.54\text{ mm/}\mu\text{s}} = \mathbf{51.948052\ \mu\text{s}}\\]

   * *Elementos extremos (\\(n = \pm 6\\))* (máxima distancia):
     \\[D_{\pm 6} = \sqrt{(0 - (-1.800))^2 + (80 - (-0.00405))^2} = \sqrt{1.800^2 + 80.00405^2} = \mathbf{80.024296\text{ mm}}\\]
     \\[\text{TOF}_{\text{máx}} = \frac{80.024296\text{ mm}}{1.54\text{ mm/}\mu\text{s}} = \mathbf{51.963829\ \mu\text{s}}\\]

2. *Diferencia entre el retardo máximo y mínimo*:
   Para enfocar el haz en transmisión, la onda emitida por el elemento más lejano debe ser disparada primero (\\(\text{retardo} = 0\\)), mientras que el elemento más cercano recibe el *retardo máximo*:
   \\[\Delta \tau = \text{TOF}{\text{máx}} - \text{TOF}{\text{mín}} = \frac{D_{\text{máx}} - D_{\text{mín}}}{c}\\]
   \\[\Delta \tau = 51.963829\ \mu\text{s} - 51.948052\ \mu\text{s} = 0.015777\ \mu\text{s} = \mathbf{15.78\text{ ns}}\\]

3. *Expresado en periodos/muestras del sistema*:
   * *En muestras digitales (\\(f_s = 60\text{ MHz}\\))*:
     \\[N_{\text{muestras}} = 0.015777\ \mu\text{s} \times 60\text{ MHz} = \mathbf{0.95\text{ muestras}} \approx \mathbf{1\text{ muestra de reloj}}\\]
   * *En ciclos de onda (\\(f_0 = 3\text{ MHz}\\))*:
     \\[N_{\text{ciclos}} = 0.015777\ \mu\text{s} \times 3\text{ MHz} = \mathbf{0.047\text{ ciclos}}\\]

---

### *b) Enfoque en \\((x, z) = (-3, 10)\text{ cm} = (-30, 100)\text{ mm}\\)*

1. *Distancia de cada elemento al punto focal steered \\((-30, 100)\text{ mm}\\)*:
   \\[D_n = \sqrt{(-30 - x_n)^2 + (100 - z_n)^2}\\]

   * *Elemento más cercano (\\(n = -6\\))*:
     \\[D_{-6} = \sqrt{(-30 - (-1.799994))^2 + (100 - (-0.004050))^2} = \sqrt{(-28.200006)^2 + 100.004050^2} = \mathbf{103.904044\text{ mm}}\\]
     \\[\text{TOF}_{\text{mín}} = \frac{103.904044\text{ mm}}{1.54\text{ mm/}\mu\text{s}} = \mathbf{67.470158\ \mu\text{s}}\\]

   * *Elemento más lejano (\\(n = +6\\))*:
     \\[D_{+6} = \sqrt{(-30 - 1.799994)^2 + (100 - (-0.004050))^2} = \sqrt{(-31.799994)^2 + 100.004050^2} = \mathbf{104.938313\text{ mm}}\\]
     \\[\text{TOF}_{\text{máx}} = \frac{104.938313\text{ mm}}{1.54\text{ mm/}\mu\text{s}} = \mathbf{68.141762\ \mu\text{s}}\\]

2. *Diferencia entre el retardo máximo y mínimo*:
   \\[\Delta \tau = \text{TOF}{\text{máx}} - \text{TOF}{\text{mín}} = \frac{104.938313 - 103.904044}{1.54} = \frac{1.034269\text{ mm}}{1.54\text{ mm/}\mu\text{s}}\\]
   \\[\Delta \tau = 0.671604\ \mu\text{s} = \mathbf{671.60\text{ ns}}\\]

3. *Expresado en periodos/muestras del sistema*:
   * *En muestras digitales (\\(f_s = 60\text{ MHz}\\))*:
     \\[N_{\text{muestras}} = 0.671604\ \mu\text{s} \times 60\text{ MHz} = \mathbf{40.30\text{ muestras}} \approx \mathbf{40\text{ muestras de reloj}}\\]
   * *En ciclos de onda (\\(f_0 = 3\text{ MHz}\\))*:
     \\[N_{\text{ciclos}} = 0.671604\ \mu\text{s} \times 3\text{ MHz} = \mathbf{2.01\text{ ciclos}}\\]

---

### *c) Tasa Máxima de Cuadros por Segundo (*Maximum Frame Rate)**

1. *Tiempo de viaje ida y vuelta por línea de escaneo (\\(T_{\text{línea}}\\))*:
   La profundidad máxima de escaneo es \\(z_{\text{máx}} = 100\text{ mm} = 0.10\text{ m}\\).
   \\[T_{\text{línea}} = \frac{2 \cdot z_{\text{máx}}}{c} = \frac{2 \times 0.10\text{ m}}{1540\text{ m/s}} = 1.2987 \times 10^{-4}\text{ s} = \mathbf{129.87\ \mu\text{s}}\\]

2. *Frecuencia Máxima de Repetición de Pulsos (\\(PRF_{\text{máx}}\\))*:
   \\[PRF_{\text{máx}} = \frac{1}{T_{\text{línea}}} = \frac{1540}{0.20} = \mathbf{7700\text{ Hz}} \quad (7.7\text{ kHz})\\]

3. *Tiempo total por cuadro B-mode (\\(T_{\text{cuadro}}\\))* para \\(N_{\text{líneas}} = 40\\) transmisiones:
   \\[T_{\text{cuadro}} = N_{\text{líneas}} \times T_{\text{línea}} = 40 \times 129.87\ \mu\text{s} = \mathbf{5.1948\text{ ms}}\\]

4. *Tasa máxima de cuadros por segundo (\\(FR_{\text{máx}}\\))*:
   \\[FR_{\text{máx}} = \frac{1}{T_{\text{cuadro}}} = \frac{c}{2 \cdot z_{\text{máx}} \cdot N_{\text{líneas}}} = \frac{1540\text{ m/s}}{2 \times 0.10\text{ m} \times 40} = \frac{1540}{8} = \mathbf{192.5\text{ cuadros/segundo (fps)}}\\]

---

### *Resumen de Resultados*

| Inciso | Parámetro Solicitado | Valor Numérico en Tiempo | En Muestras (\\(f_s=60\text{ MHz}\\)) | En Ciclos (\\(f_0=3\text{ MHz}\\)) |
| :---: | :--- | :---: | :---: | :---: |
| *a)* | Retardo Máximo vs. Mínimo en \\((0, 8)\text{ cm}\\) | *15.78 ns* (0.0158 \\(\mu\\)s) | ~1 muestra | 0.047 ciclos |
| *b)* | Retardo Máximo vs. Mínimo en \\((-3, 10)\text{ cm}\\) | *671.60 ns* (0.6716 \\(\mu\\)s) | ~40 muestras | 2.01 ciclos |
| *c)* | Tasa Máxima de Cuadros (Frame Rate) | *192.5 fps* | \\(T_{\text{línea}} = 129.87\ \mu\text{s}\\) | \\(T_{\text{cuadro}} = 5.19\text{ ms}\\) |