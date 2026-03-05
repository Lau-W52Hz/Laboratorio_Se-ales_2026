# Laboratorio 2 CONVOLUCION
El procesamiento digital de señales permite analizar, modificar e interpretar diferentes tipos de señales mediante herramientas matemáticas y computacionales. Entre estas herramientas se encuentran la convolución, la correlación cruzada y la transformada de Fourier, las cuales permiten estudiar la relación entre señales y analizar su comportamiento tanto en el dominio del tiempo como en el dominio de la frecuencia.<br>

En este laboratorio se analizaron diferentes señales discretas mediante el uso de Python. Inicialmente se generaron señales sinusoidales y se estudió su correlación cruzada para determinar el grado de similitud entre ellas. Posteriormente se analizó una señal biológica real mediante herramientas estadísticas y espectrales.<br>

## OBJETIVOS
### Objetivo General:
Reconocer la importancia de la aplicación de herramientas
matemáticas como la convolución y correlación en el área de procesamiento de
señales.<br>

### Objetivos Específicos
-Comprender la convolución como una operación que permite obtener la
respuesta de un sistema discreto ante una entrada determinada.<br>
-Analizar la correlación como medida de similitud entre dos señales.<br>
-Aplicar la Transformada de Fourier como herramienta de análisis en el
dominio de la frecuencia.<br> 

## PARTE A
Para la primera parte del laboratorio , teniendo en cuenta el sistema h[n] = {dígitos del código del carnet estudiantil } y la señal x[n] = {dígitos de la cédula de ciudadanía} cada integrante del grupo, realizará lo siguiente:<br>

1.Encontrar la señal 𝑦[𝑛] resultante de la convolución usando sumatorias (a mano).<br>

Para esta parte del laboratorio se juntaron los 2 números de cédula de las dos integrantes de manera consecutiva para la definición de la señal  x[n], de igual manera se realizó el mismo procedimiento con los códigos estudiantiles para los valores de h[n]. <br>

x[n]= {1, 0, 7, 8, 3, 6, 7, 2, 2, 9, 1, 0, 3, 2, 9, 3, 7, 8, 7, 9}<br>
h[n]={5, 6, 0, 0, 8, 5, 4, 5, 6, 0, 0, 5, 9, 2}<br>

El resultado fue el siguiente:

<img width="465" height="853" alt="image" src="https://github.com/user-attachments/assets/5d68136a-fc85-4548-9e7b-9e302f04096e" />



### ALGORITMO 

### CODIGO

## PARTE B
En esta parte de la práctica se trabajará con dos señales discretas definidas mediante funciones trigonométricas: una señal coseno y una señal seno. A partir del período de muestreo dado por la guia, se calcularán los valores de ambas señales para un conjunto determinado de muestras.<br>
Posteriormente, se aplicará la correlación cruzada entre las dos señales con el objetivo de analizar el grado de similitud entre ellas y observar cómo cambia esta relación cuando una señal se desplaza respecto a la otra.<br>
Finalmente, se realizará la representación gráfica de la correlación obtenida y se describirá la secuencia resultante, permitiendo interpretar el comportamiento de las señales y comprender la utilidad de la correlación cruzada en el procesamiento digital de señales.

#### SEÑALES 

```
x1[nTs​]=cos(2π100nTs​)
𝑥2[𝑛𝑇𝑠]=sin(2𝜋100𝑛𝑇𝑠)
```
con 
```
Ts=1.25ms= 0,00125s
0 </= n < 9
```
Sustituyendo el valor de Ts:
```
X1[n]=Cos (2𝜋(100)(0,00125)n)
X2[n]=Sen (2𝜋(100)(0,00125)n)

100.0.00125= 0,125

entonces

X1[n]=Cos (2𝜋(0,125)n) 
X2[n]=Sen (2𝜋(0,125)n)

```
Para n=0,1,2,3,4,5,6,7,8

|n | X1[n] | X2[n] |
|--|-------|-------|
|0 |  1  |  0  |
|1  | 0,707 |  0,707 |
|2  | 0  | 1 |
|3 | -0,707 | 0,707 |
|4 | -1 | 0 |
|5 | -0,707 | -0,707 | 
|6 | 0 | -1 |
|7 | 0,707 | -0,707 |
|8 | 1 | 0 |

#### Correlación Cruzada 
La correlación cruzada permite medir la similitud entre dos señales para diferentes desplazamientos, en este caso se comparan: <br>
una señal coseno <br>
una señal seno <br> 
Ambas tienen la misma frecuencia pero están desfasadas 90°, por lo que la correlación alrededor del origen es pequeña <br>
### ALGORITMO 
<img width="465" height="853" alt="image" src="https://github.com/user-attachments/assets/5d68136a-fc85-4548-9e7b-9e302f04096e" />

### CODIGO 
```
import numpy as np
import matplotlib.pyplot as plt

Ts = 0.00125
n = np.arange(0,9)

x1 = np.cos(2*np.pi*100*n*Ts)
x2 = np.sin(2*np.pi*100*n*Ts)
```
Este código importa las librerías NumPy y Matplotlib, que se usan para hacer cálculos numéricos y graficar señales. Luego se define el tiempo de muestreo (Ts = 0.00125) y un arreglo (n) que representa las muestras de la señal desde 0 hasta 8. Finalmente, se crean dos señales discretas: x1, que es una señal coseno, y x2, que es una señal seno, ambas con una frecuencia de 100 Hz. Estas señales se calculan usando el número de muestras y el tiempo de muestreo para poder analizarlas en forma discreta.<br>

```
plt.figure()
plt.stem(n, x1)
plt.title("Señal x1[n] = cos(2π100nTs)")
plt.xlabel("n")
plt.ylabel("Amplitud")
plt.grid()
plt.show()
```
Este código se utiliza para graficar la señal discreta (x1[n]). Primero se crea una nueva figura con `plt.figure()`. Luego `plt.stem(n, x1)` genera una gráfica de tipo stem, que es la más común para mostrar señales discretas, donde cada muestra aparece como una línea vertical. Después se agrega un título, se nombran los ejes (n para las muestras y amplitud para el valor de la señal) y se activa la cuadrícula para facilitar la visualización. Finalmente, `plt.show()` muestra la gráfica en pantalla.<br>

<img width="402" height="303" alt="image" src="https://github.com/user-attachments/assets/186391fd-5ca5-48aa-b563-ddca2de11389" /><br>

```
plt.figure()
plt.stem(n, x2)
plt.title("Señal x2[n] = sin(2π100nTs)")
plt.xlabel("n")
plt.ylabel("Amplitud")
plt.grid()
plt.show()

```
Este código se utiliza para graficar la señal discreta (x2[n]). Primero se crea una nueva figura con `plt.figure()`. Luego `plt.stem(n, x2)` genera una gráfica de tipo stem, que permite representar cada muestra de la señal de forma discreta. Después se añade un título, se nombran los ejes (n para las muestras y amplitud para el valor de la señal) y se activa la cuadrícula para que la gráfica sea más fácil de interpretar. Finalmente, `plt.show()` muestra la gráfica en pantalla.<br>

<img width="389" height="293" alt="image" src="https://github.com/user-attachments/assets/b5ba9b4d-1f41-4a4d-8c7e-5a494b196b5d" /><br>

```
corr = np.correlate(x1, x2, mode='full')
lags = np.arange(-len(x1)+1, len(x1))

plt.figure()
plt.stem(lags, corr)
plt.title("Correlación cruzada entre x1[n] y x2[n]")
plt.xlabel("Desplazamiento (lag)")
plt.ylabel("Correlación")
plt.grid()
plt.show()
```
Este código calcula y muestra la correlación cruzada entre las señales (x1[n]) y (x2[n]). Primero, con `np.correlate()` se obtiene la correlación usando el modo `"full"`, lo que permite ver todos los posibles desplazamientos entre las dos señales. Luego se crea el arreglo `lags`, que representa los desplazamientos o corrimientos entre las señales. Después se grafica el resultado con `plt.stem()` para visualizar la correlación de forma discreta, se agregan el título, los nombres de los ejes y la cuadrícula, y finalmente `plt.show()` muestra la gráfica en pantalla.<br>

<img width="399" height="313" alt="image" src="https://github.com/user-attachments/assets/a58ae5d3-efc1-4194-bfbe-843cd5fb792d" /><br> 

**La gráfica muestra la **correlación cruzada entre las señales (x1[n]) y (x2[n])** para diferentes desplazamientos (lag). Se puede ver que la correlación tiene **valores positivos y negativos**, lo que significa que en algunos desplazamientos las señales se parecen más y en otros son más diferentes. El **valor máximo aparece cerca de lag = -2**, lo que indica que al desplazar una señal aproximadamente **2 muestras**, se obtiene la mayor similitud entre ambas. Esto ocurre porque la señal seno y la señal coseno tienen un **desfase entre sí**, y la correlación ayuda a identificar ese desfase.**

## PARTE C
En la Parte C se generó una señal biológica tipo EOG (Electrooculografía) utilizando el generador de señales biológicas. Las señales EOG se utilizan para medir los movimientos oculares mediante la diferencia de potencial eléctrico entre la córnea y la retina.se realizó el análisis de la señal muestreada a una frecuencia de 2000 Hz durante 5 segundos, obteniendo un total de 10000 muestras. Primero se representó la señal en el dominio del tiempo y se calcularon diferentes parámetros estadísticos para caracterizar su comportamiento. Posteriormente se aplicó la Transformada de Fourier y el cálculo de la densidad espectral de potencia para analizar las componentes de frecuencia presentes en la señal y observar cómo se distribuye su energía en el espectro.<br>

#### Frecuencia de Nyquist 
La frecuencia de Nyquist corresponde a la mitad de la frecuencia de muestreo y representa la frecuencia máxima que puede representarse correctamente sin producir aliasing.<br>
```
fN​=fs/2​​
```
Teniendo en cuenta que la frecuencia de muestreo utilizada es
```
fs​=2000Hz

fN=2000/2
𝑓𝑁=1000𝐻𝑧

Esto significa que el sistema puede representar correctamente frecuencias de hasta 1000 Hz.
```

### ALGORITMO
<img width="450" height="726" alt="image" src="https://github.com/user-attachments/assets/eb6ec46e-e936-4905-9995-cab73f1acf3c" />

### CODIGO 
```
import numpy as np
import matplotlib.pyplot as plt
from scipy.fft import fft, fftfreq
from scipy.signal import welch

signal = np.loadtxt(r"C:\Users\aleja\Downloads\senal.txt")
```
Este fragmento de código importa las librerías necesarias para el análisis de la señal.NumPy y Matplotlib, fft y fftfreq de SciPy para calcular la ransformada Rápida de Fourier (FFT) y analizar la señal en el dominio de la frecuencia, y `welch` para estimar la densidad espectral de potencia. Finalmente, con np.loadtxt() se carga la señal desde un archivo de texto llamado senal.txt y se guarda en la variable signal para poder analizarla posteriormente.

 ```
fs = 2000  # frecuencia de muestreo (Hz)
N = len(signal)
print("Número de muestras:", N)
f_nyquist = fs / 2
print("Frecuencia de Nyquist:", f_nyquist, "Hz")
```
Este código define la frecuencia de muestreo de la señal en 2000 Hz, luego calcula el número total de muestras usando len(signal) y lo muestra en pantalla. Finalmente, calcula la frecuencia de Nyquist (la mitad de la frecuencia de muestreo) y también la imprime.

```
plt.figure()
plt.plot(signal)
plt.title("Señal EOG en el dominio del tiempo")
plt.xlabel("Muestras")
plt.ylabel("Amplitud")
plt.grid()
plt.show()
media = np.mean(signal)
mediana = np.median(signal)
desv = np.std(signal)
maximo = np.max(signal)
minimo = np.min(signal)

print("\n--- Estadísticos de la señal ---")
print("Media:", media)
print("Mediana:", mediana)
print("Desviación estándar:", desv)
print("Máximo:", maximo)
print("Mínimo:", minimo)
```
Este código primero grafica la señal EOG en el dominio del tiempo para observar cómo cambia la amplitud a lo largo de las muestras. Luego calcula algunos estadísticos de la señal como la media, la mediana, la desviación estándar, el valor máximo y el mínimo utilizando funciones de NumPy. Finalmente, estos valores se imprimen en pantalla para describir el comportamiento de la señal. 

```
fft_signal = fft(signal)
freq = fftfreq(N, 1/fs)

plt.figure()
plt.plot(freq, np.abs(fft_signal))
plt.title("Transformada de Fourier de la señal EOG")
plt.xlabel("Frecuencia (Hz)")
plt.ylabel("Magnitud")
plt.grid()
plt.show()
f, Pxx = welch(signal, fs)

plt.figure()
plt.semilogy(f, Pxx)
plt.title("Densidad espectral de potencia (PSD)")
plt.xlabel("Frecuencia (Hz)")
plt.ylabel("Potencia")
plt.grid()
plt.show()
```
Este código primero calcula la Transformada de Fourier (FFT) de la señal EOG para analizarla en el dominio de la frecuencia. Luego grafica la magnitud de la FFT para observar qué frecuencias están presentes en la señal. Después se utiliza el método de Welch para calcular la densidad espectral de potencia (PSD), que permite ver cómo se distribuye la potencia de la señal en las diferentes frecuencias, y finalmente se muestra su gráfica. 

```
freq_media = np.mean(freq)
freq_mediana = np.median(freq)
freq_std = np.std(freq)

print("\n--- Estadísticos en frecuencia ---")
print("Frecuencia media:", freq_media)
print("Frecuencia mediana:", freq_mediana)
print("Desviación estándar:", freq_std)
plt.figure()
plt.hist(freq, bins=30)
plt.title("Histograma de frecuencias")
plt.xlabel("Frecuencia (Hz)")
plt.ylabel("Cantidad")
plt.show()
```
Este código calcula algunos estadísticos de las frecuencias como la media, la mediana y la desviación estándar usando el vector de frecuencias. Luego imprime estos valores en pantalla. Finalmente, se genera un histograma de las frecuencias para visualizar cómo se distribuyen. <br>

#### RESULTADOS


| Numero de Muestras  |  10000 |
|-----------|---------|
<br>

| Frecuencia de Nyquist | 1000.0 Hz| 
|----------|----------|
<br>

<img width="416" height="307" alt="image" src="https://github.com/user-attachments/assets/bee8dac4-2862-4a0f-b38d-414b489a9bd9" /><br>
La gráfica muestra la señal EOG en el dominio del tiempo, donde se observa cómo cambia la amplitud a lo largo de las muestras. La señal presenta variaciones positivas y negativas alrededor de cero, con algunos picos más altos que pueden estar relacionados con movimientos de los ojos. En general, se ve que la señal no es constante, sino que cambia continuamente, lo cual es normal en este tipo de señales biológicas. <br>

|--- Estadísticos de la señal ---| datos |
|----------------------------------|------|
| Media |-0.04412532893199532 |
| Mediana| -0.04079738832660951 |
| Desviación estándar | 0.1438798131251786 |
| Máximo | 0.39502696579438634 |
| Mínimo | -0.5496883069863543 |
<br>
Los estadísticos de la señal EOG muestran que:<br>
- la media y la mediana son cercanas a cero, lo que indica que la señal oscila alrededor de ese valor.<br>
- La desviación estándar refleja la variabilidad de la señal en el tiempo. <br>
- El valor máximo y mínimo indican los picos de mayor y menor amplitud presentes en la señal, los cuales pueden estar asociados a movimientos oculares o cambios más pronunciados en la actividad registrada.<br>

<img width="422" height="305" alt="image" src="https://github.com/user-attachments/assets/5f977573-4a23-44e3-95a3-d91483fb1776" /><br>
La gráfica muestra la Transformada de Fourier de la señal EOG, donde se observa cómo se distribuyen las frecuencias presentes en la señal. Se puede ver que la mayor magnitud está cerca de 0 Hz, lo que indica que la mayor parte de la energía de la señal se encuentra en frecuencias bajas, algo característico de las señales EOG. A medida que aumenta la frecuencia, la magnitud disminuye, lo que significa que hay menos componentes de alta frecuencia en la señal<br>

<img width="405" height="299" alt="image" src="https://github.com/user-attachments/assets/2ba96fd6-c2c7-4e7b-a599-bf56f093fce4" /><br>
La gráfica muestra cómo se distribuye la potencia de la señal EOG en las diferentes frecuencias. Se observa que la mayor potencia está en las frecuencias bajas, lo que indica que la mayor parte de la información de la señal se encuentra en esa zona. A medida que aumenta la frecuencia, la potencia disminuye, lo que significa que hay menos componentes de alta frecuencia en la señal. Esto es típico en señales EOG, ya que los movimientos oculares suelen generar variaciones lentas en la señal.<br>

|--- Estadísticos en frecuencia ---| Datos|
|----------------------------------|-----|
| Frecuencia media | -0.1 |
| Frecuencia mediana |  -0.1 |
| Desviación estándar | 577.3502663028744 |
<br>
Estos estadísticos en frecuencia muestran cómo están distribuidas las frecuencias de la señal. Que la media y la mediana sean cercanas a 0 Hz indica que la señal está centrada alrededor de esa frecuencia, lo cual es normal cuando se analiza la FFT porque aparecen frecuencias positivas y negativas alrededor de cero. La desviación estándar alta indica que las frecuencias están bastante dispersas en el rango analizado, aunque como se observó en las gráficas, la mayor energía de la señal EOG se concentra en las frecuencias bajas. Esto significa que la señal cambia de forma lenta, algo típico en señales de movimientos oculares.<br>

<img width="404" height="304" alt="image" src="https://github.com/user-attachments/assets/f553b5e3-b9b3-45f7-93e6-b47895ca3a7a" /><br>
El histograma muestra la distribución de las frecuencias obtenidas del análisis. Se observa que las frecuencias están distribuidas a lo largo de todo el rango analizado, lo cual ocurre porque la FFT genera frecuencias positivas y negativas alrededor de 0 Hz. Por eso las barras aparecen de forma uniforme en el histograma. <br>

Trabajado en Jupyter: http://localhost:8888/doc/tree/lab2pds.ipynb 

# PREGUNTAS

## 3. ¿Para qué sirve la correlación cruzada?
La correlación cruzada es una herramienta ampliamente utilizada en el procesamiento digital de señales para analizar la relación entre dos señales. Permite detectar similitudes, identificar retardos temporales, sincronizar señales y reconocer patrones. En aplicaciones biomédicas puede utilizarse para comparar señales fisiológicas como electrocardiogramas, electroencefalogramas o señales musculares.<br>
