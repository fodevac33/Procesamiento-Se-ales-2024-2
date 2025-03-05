# Representación Matricial de la Transformada de Fourier

## Forma Matricial de la DFT

La Transformada Discreta de Fourier (DFT) puede expresarse de manera elegante mediante una representación matricial. Esta formulación nos permite visualizar la transformación como una simple operación de multiplicación matriz-vector:

$$\mathbf{X} = \mathbf{W}_N \cdot \mathbf{x}$$

Donde:
- $\mathbf{X}$ es un vector columna que contiene los coeficientes de la DFT: $X[0], X[1], \ldots, X[N-1]$
- $\mathbf{x}$ es el vector de la señal original en el dominio del tiempo
- $\mathbf{W}_N$ es la matriz de transformación de dimensión $N \times N$

La matriz de transformación $$\mathbf{W}_N$$ tiene elementos $W_{jk} = \omega_N^{jk}$, donde $\omega_N = e^{-i2\pi/N}$ es la raíz N-ésima de la unidad. Explícitamente:

$$\mathbf{W}_N = 
\begin{pmatrix}
\omega_N^{0 \cdot 0} & \omega_N^{0 \cdot 1} & \omega_N^{0 \cdot 2} & \cdots & \omega_N^{0 \cdot (N-1)} \\
\omega_N^{1 \cdot 0} & \omega_N^{1 \cdot 1} & \omega_N^{1 \cdot 2} & \cdots & \omega_N^{1 \cdot (N-1)} \\
\omega_N^{2 \cdot 0} & \omega_N^{2 \cdot 1} & \omega_N^{2 \cdot 2} & \cdots & \omega_N^{2 \cdot (N-1)} \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
\omega_N^{(N-1) \cdot 0} & \omega_N^{(N-1) \cdot 1} & \omega_N^{(N-1) \cdot 2} & \cdots & \omega_N^{(N-1) \cdot (N-1)}
\end{pmatrix}$$

Esta matriz es simétrica y contiene todos los factores de fase necesarios para descomponer la señal en sus componentes de frecuencia.

## Matrices No Cuadradas en la Transformada de Fourier

Cuando utilizamos una matriz de transformación no cuadrada de dimensión $M \times N$ (donde $M \neq N$), estamos modificando la relación entre los dominios de tiempo y frecuencia. Este enfoque tiene importantes implicaciones:

### Transformación No Invertible

Una matriz rectangular no posee una inversa exacta. Esto significa que no podemos recuperar perfectamente la señal original a partir de su transformada, lo que introduce cierta irreversibilidad en el proceso.

### Casos Específicos

#### Sobremuestreo ($M > N$)

Cuando tenemos más filas que columnas en la matriz de transformación:
- Se produce un **sobremuestreo** en el dominio de la frecuencia
- Se genera redundancia en la representación espectral
- Mejora la resolución en frecuencia (similar al efecto del zero-padding)
- Se utiliza para análisis espectral de alta precisión

#### Submuestreo ($M < N$)

Cuando tenemos menos filas que columnas:
- Ocurre un **submuestreo** en el dominio frecuencial
- Se produce pérdida de información (no toda la información original puede ser representada)
- Se utiliza comúnmente en técnicas de compresión de datos
- Puede causar aliasing o solapamiento espectral si no se aplica correctamente

### Aplicaciones Prácticas

Las transformaciones con matrices rectangulares tienen aplicaciones específicas:

1. **Compresión de datos**: Reduciendo el número de coeficientes ($M < N$) para representar la señal de manera más eficiente.

2. **Análisis espectral mejorado**: Aumentando la resolución frecuencial ($M > N$) para identificar componentes espectrales cercanos.

3. **Zero-padding**: Técnica donde se añaden ceros a la señal original para aumentar artificialmente su longitud, resultando en una matriz de transformación donde $M > N$.

4. **Bancos de filtros**: Diseño de sistemas de procesamiento multirate donde diferentes resoluciones tiempo-frecuencia son necesarias.

La representación matricial no cuadrada de la transformada de Fourier ofrece flexibilidad para adaptar el análisis espectral a necesidades específicas, equilibrando la precisión en frecuencia, la eficiencia computacional y los requisitos de almacenamiento según la aplicación.