# Determinantes del gasto monetario de los hogares  
## Proyecto Final de Econometría I

Este repositorio contiene el código, la base de datos, los resultados y la documentación del proyecto final de Econometría I. El objetivo del trabajo es estimar, comparar y defender un modelo econométrico para explicar el gasto monetario de los hogares de la zona oriente del país, usando una submuestra construida a partir de la ENIGH 2024.

La narrativa central del proyecto es la selección de un modelo log-log estimado mediante WLS, con pesos derivados de una modelación auxiliar de la varianza y errores estándar robustos HC3. También se estiman modelos alternativos por MCO, modelos logarítmicos, modelos winsorizados, IV/2SLS y ecuaciones simultáneas como ejercicios de sensibilidad.

---

## 1. Instrucciones de ejecución

### 1.1. Abrir el notebook en Google Colab

El notebook principal puede ejecutarse directamente desde Google Colab:

[Notebook principal en Google Colab](https://colab.research.google.com/drive/1LMh7UtLNNIov2gDvmLMK5904wMIF4tn8?usp=sharing)

Para reproducir el análisis en Colab:

1. Abrir el enlace del notebook.
2. Montar Google Drive cuando el notebook lo solicite.
3. Verificar que el archivo de datos esté disponible en la ruta indicada dentro del notebook.
4. Ejecutar las celdas en orden, desde la carga de datos hasta los diagnósticos finales.
5. Revisar las tablas de resultados, diagnósticos y comparaciones de modelos.

---

### 1.2. Ejecutar el proyecto localmente

Para ejecutar el proyecto en una computadora local, se recomienda crear un entorno virtual.

#### Crear entorno virtual

```bash
python -m venv .venv
```

#### Activar entorno virtual

En macOS o Linux:

```bash
source .venv/bin/activate
```

En Windows:

```bash
.venv\Scripts\activate
```

#### Instalar dependencias

```bash
pip install -r requirements.txt
```

#### Abrir Jupyter Notebook

```bash
jupyter notebook
```

o, si se usa JupyterLab:

```bash
jupyter lab
```

Después se debe abrir el notebook principal y ejecutar las celdas en orden.

---

### 1.3. Archivos necesarios

Para reproducir el análisis se requiere:

- El notebook principal del proyecto.
- La base de datos `concentradohogar_ORIENTE.xlsx`.
- El archivo `requirements.txt`.
- Las carpetas de trabajo definidas en la estructura del repositorio.

La base de datos final utilizada puede consultarse aquí:

[Base de datos: concentradohogar_ORIENTE.xlsx](https://docs.google.com/spreadsheets/d/1w-VnuwikP9IE3PQYjZaKgwiHP6JUpmC9/edit?usp=share_link&ouid=109933105368325552169&rtpof=true&sd=true)

---

## 2. Estructura del proyecto

Una estructura recomendada para el repositorio es la siguiente:

```text
proyecto-econometria-gasto-hogares/
│
├── README.md
├── requirements.txt
│
├── data/
│   ├── raw/
│   │   └── bases_originales_enigh_2024/
│   │
│   ├── processed/
│   │   └── concentradohogar_ORIENTE.xlsx
│   │
│   └── README_data.md
│
├── notebooks/
│   └── Notebook_Reformulacion_MRLM_Gasto_Eco1.ipynb
│
├── src/
│   ├── 01_limpieza_datos.py
│   ├── 02_eda.py
│   ├── 03_modelos_mco.py
│   ├── 04_modelo_wls_hc3.py
│   ├── 05_diagnosticos.py
│   └── 06_iv_2sls_simultaneas.py
│
├── outputs/
│   ├── tablas/
│   ├── graficos/
│   └── modelos/
│
├── report/
│   ├── informe_final.tex
│   ├── informe_final.pdf
│   └── referencias.bib
│
└── video/
    └── guion_video.md
```

---

## 3. Descripción de carpetas

### `data/`

Contiene los datos utilizados en el proyecto.

- `data/raw/`: bases originales descargadas de la ENIGH 2024.
- `data/processed/`: base final depurada y utilizada en los modelos.
- `README_data.md`: documentación de la construcción de la base de datos.

La base final corresponde a una submuestra de hogares de la zona oriente del país.

---

### `notebooks/`

Contiene el notebook principal del proyecto. En este archivo se desarrolla el flujo completo:

1. Carga de datos.
2. Exploración inicial.
3. Transformaciones logarítmicas.
4. Estimación de modelos MCO.
5. Diagnósticos econométricos.
6. Winsorización y observaciones influyentes.
7. Modelo WLS con errores robustos HC3.
8. IV/2SLS.
9. Ecuaciones simultáneas.
10. Comparación y conclusiones.

---

### `src/`

Contiene scripts modulares en Python. Estos scripts permiten organizar el proyecto fuera del notebook y facilitar su reproducibilidad.

---

### `outputs/`

Contiene los resultados generados por el análisis:

- Tablas de coeficientes.
- Tablas comparativas de modelos.
- Gráficos exploratorios.
- Resultados de pruebas de diagnóstico.
- Salidas de modelos.

---

### `report/`

Contiene el informe final escrito en LaTeX y su versión PDF. El informe incluye las secciones requeridas por el proyecto:

1. Introducción.
2. Pregunta de investigación y objetivos.
3. Marco teórico y revisión breve de literatura.
4. Hipótesis.
5. Datos.
6. Metodología.
7. Resultados.
8. Validación y diagnóstico.
9. Conclusiones.
10. Referencias en formato APA 7.
11. Anexos.

---

### `video/`

Contiene el guion, materiales o recursos usados para la presentación en video.

---

## 4. Modelos estimados

El notebook compara distintas especificaciones econométricas:

1. Modelo MCO en niveles.
2. Modelo con variable dependiente logarítmica.
3. Modelo log-log.
4. Modelo log-log con errores estándar robustos HC3.
5. Modelo sin observaciones influyentes.
6. Modelo winsorizado.
7. Modelo WLS simple.
8. Modelo WLS con varianza modelada y errores robustos HC3.
9. Modelo IV/2SLS.
10. Sistema exploratorio de ecuaciones simultáneas.

El modelo final seleccionado es el modelo log-log estimado mediante WLS, con pesos derivados de una modelación auxiliar de la varianza y errores estándar robustos HC3.

---

## 5. Diagnósticos realizados

Se realizaron los siguientes diagnósticos econométricos:

- Multicolinealidad mediante VIF.
- Heterocedasticidad mediante Breusch-Pagan.
- Normalidad de residuos mediante Jarque-Bera y Shapiro-Wilk.
- Especificación funcional mediante Ramsey RESET.
- Influencia de observaciones mediante distancia de Cook.
- Robustez frente a winsorización y exclusión de observaciones influyentes.
- Posible endogeneidad mediante IV/2SLS, Wu-Hausman y Durbin.
- Exploración de simultaneidad mediante un sistema estimado por 2SLS.

---

## 6. Roles del equipo

### Líder de proyecto y metodología  
**Responsable:** Ingrid  

Funciones principales:

- Diseñar la pregunta de investigación.
- Definir la hipótesis general e hipótesis individuales.
- Proponer la especificación base del modelo.
- Coordinar la coherencia metodológica del proyecto.
- Verificar que la selección del modelo final responda al objetivo del trabajo.

---

### Data Engineer  
**Responsable:** Diego  

Funciones principales:

- Adquirir las bases originales de la ENIGH 2024.
- Documentar la elaboración de la base de datos final.
- Filtrar la muestra a la zona oriente del país.
- Limpiar, renombrar y estructurar variables.
- Preparar la base `concentradohogar_ORIENTE.xlsx`.
- Verificar consistencia, tipos de datos y valores faltantes.

---

### Modelador/a  
**Responsables:** Sari, Diego, Cristina, Ingrid, Joshua y Yazmin  

Funciones principales:

- Estimar el modelo base por MCO.
- Probar especificaciones alternativas.
- Implementar transformaciones logarítmicas.
- Comparar modelos en niveles, logarítmicos, winsorizados y ponderados.
- Estimar el modelo WLS-HC3 final.
- Explorar modelos IV/2SLS y ecuaciones simultáneas.
- Revisar la interpretación económica de los coeficientes.

---

### Validación y diagnóstico  
**Responsable:** Cristina  

Funciones principales:

- Evaluar multicolinealidad mediante VIF.
- Aplicar pruebas de heterocedasticidad.
- Revisar especificación funcional mediante Ramsey RESET.
- Analizar normalidad de residuos.
- Identificar observaciones influyentes mediante distancia de Cook.
- Documentar limitaciones del modelo final.

---

### Visualización y narrativa  
**Responsable:** Yazmin  

Funciones principales:

- Elaborar gráficos exploratorios.
- Organizar tablas de resultados.
- Desarrollar la narrativa del documento final.
- Preparar materiales visuales para la presentación.
- Cuidar la claridad del storytelling econométrico.
- Traducir resultados técnicos a interpretación económica.

---

### Reproducibilidad y QA  
**Responsable:** Joshua  

Funciones principales:

- Organizar la estructura del repositorio.
- Revisar el estilo del código.
- Verificar versiones y dependencias.
- Mantener actualizado el archivo `requirements.txt`.
- Probar que el notebook pueda ejecutarse correctamente.
- Apoyar la ejecución “one-click” del análisis.

---

## 7. Reproducibilidad

Para asegurar la reproducibilidad del proyecto:

1. Se conserva la base final utilizada en las estimaciones.
2. Se documenta el proceso de construcción de la base.
3. Se incluye un archivo `requirements.txt`.
4. Se mantiene el notebook principal con las celdas ordenadas.
5. Se reportan los modelos y diagnósticos utilizados para seleccionar la especificación final.

---

## 8. Notas metodológicas

El análisis utiliza datos de corte transversal y no incorpora dependencia temporal. Por tanto, no se emplean modelos dinámicos, VAR, AR, ACF/PACF ni pruebas asociadas a series de tiempo.

Los resultados se interpretan como asociaciones condicionadas dentro de la submuestra de hogares de la zona oriente del país. No se afirma causalidad estricta, debido a la posible presencia de endogeneidad, variables omitidas y relación contable entre el gasto total y algunos de sus componentes.

---

## 9. Autores

Proyecto elaborado para el curso de Econometría I, Primavera 2026.

Integrantes:

- Ingrid Aguilar Ríos
- Yazmin Calderón Hernández
- Sari Andrea Estrella Segura
- Cristina Gil Torres
- Diego Juárez Jácome
- Joshua Ortega Fabian
