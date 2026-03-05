# Laboratorio 2 CONVOLUCION
Objetivo General: Reconocer la importancia de la aplicación de herramientas
matemáticas como la convolución y correlación en el área de procesamiento de
señales.


Objetivos Específicos

*Comprender la convolución como una operación que permite obtener la
respuesta de un sistema discreto ante una entrada determinada.

*Analizar la correlación como medida de similitud entre dos señales.


*Aplicar la Transformada de Fourier como herramienta de análisis en el
dominio de la frecuencia.
## PARTE A

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
X2[n]=Cos (2𝜋(0,125)n)

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

### ALGORITMO

### CODIGO 
