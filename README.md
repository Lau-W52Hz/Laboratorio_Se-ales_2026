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

### ALGORITMO 

### CODIGO 

## PARTE C

### ALGORITMO

### CODIGO 
