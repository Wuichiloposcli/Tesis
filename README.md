# Teoría del Riesgo y Probabilidad de Ruina: Una Aproximación vía Procesos de Lévy

**Tesis de Licenciatura** — Universidad de las Américas Puebla  
**Autor:** Luis Alvarez  
**Director:** Dr. Freddy Palma Mancilla  
**Departamento:** Actuaría, Física y Matemáticas  
**Fecha:** Mayo 2026

---

## Descripción

Este repositorio contiene el código fuente y los datos utilizados en la tesis *Teoría del Riesgo y Probabilidad de Ruina: Una Aproximación vía Procesos de Lévy*. El trabajo estudia la probabilidad de ruina de una aseguradora bajo distintos modelos estocásticos, partiendo del modelo clásico de Cramér-Lundberg y generalizando hacia procesos de Lévy de actividad infinita.

La tesis aborda tres preguntas concretas:
1. ¿Qué tan bien describe el modelo clásico de Cramér-Lundberg la dinámica de una cartera real multi-ramo?
2. ¿Qué ocurre con la desigualdad de Lundberg cuando la distribución de severidad tiene cola pesada?
3. ¿Cómo se comporta la probabilidad de ruina cuando el proceso de reclamaciones tiene actividad infinita?

## Estructura del repositorio

```
├── seccion3_CL.ipynb               # Verificación numérica del modelo de Cramér-Lundberg
├── seccion4_distribuciones.ipynb    # Ajuste de distribuciones y coeficiente de ajuste
├── seccion5_gamma.ipynb             # Proceso gamma (actividad infinita) con datos simulados
├── insurance_data.csv               # Conjunto de datos (reclamaciones de seguros multi-ramo)
└── README.md
```

## Contenido de cada notebook

### `seccion3_CL.ipynb` — Modelo Clásico
- Análisis exploratorio de la severidad de siniestros
- Prueba de bondad de ajuste de Poisson para la frecuencia diaria (chi-cuadrada)
- Prueba de bondad de ajuste exponencial para los tiempos entre llegadas (Kolmogorov-Smirnov)
- Estimación de parámetros por máxima verosimilitud
- Cálculo del coeficiente de ajuste y la probabilidad de ruina exacta
- Simulación Monte Carlo del proceso de superávit

### `seccion4_distribuciones.ipynb` — Distribuciones No Exponenciales
- Ajuste de distribuciones Exponencial, Gamma, Weibull y Lognormal por MLE
- Selección de modelo por AIC/BIC
- Análisis de la existencia de la función generadora de momentos (MGF)
- Coeficiente de ajuste para distribuciones con MGF finita (Exponencial y Gamma)
- Aproximación por difusión como alternativa cuando la MGF no existe
- Simulación Monte Carlo con severidad Weibull y Gamma

### `seccion5_gamma.ipynb` — Proceso Gamma
- Calibración del proceso gamma como modelo de reclamaciones
- Comparación visual de trayectorias: Cramér-Lundberg vs proceso gamma
- Ecuación de Lundberg para el proceso gamma (solución numérica)
- Simulación Monte Carlo de la probabilidad de ruina
- Comparación de cotas de Lundberg y aproximación por difusión

## Datos

El archivo `insurance_data.csv` contiene 10,000 registros de reclamaciones de una cartera multi-ramo (Property, Mobile, Health, Life, Travel, Motor). Se utilizan únicamente las reclamaciones aprobadas (`CLAIM_STATUS = 'A'`), lo que deja 9,497 observaciones en un horizonte de 407.6 días.

## Requisitos

```
python >= 3.9
numpy
scipy
pandas
matplotlib
```

Instalación:
```bash
pip install numpy scipy pandas matplotlib
```

## Resultados principales

- Los supuestos del modelo clásico (frecuencia Poisson, tiempos exponenciales) son rechazados por las pruebas de bondad de ajuste.
- Las distribuciones con mejor AIC (Weibull con k = 0.699 y Lognormal) no tienen MGF finita, lo que invalida la desigualdad de Lundberg.
- El proceso gamma demuestra que actividad infinita y existencia del coeficiente de ajuste son compatibles: su medida de Lévy diverge en el origen pero tiene cola exponencial.

## Referencia

```
Alvarez, L. (2026). Teoría del Riesgo y Probabilidad de Ruina: 
Una Aproximación vía Procesos de Lévy. Tesis de licenciatura, 
Universidad de las Américas Puebla.
```

## Licencia

Este código se distribuye con fines académicos. El conjunto de datos se utiliza exclusivamente para los fines de esta tesis.
