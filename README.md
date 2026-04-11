# Métodos Estadísticos en Hidrología con Python
### Análisis de Precipitaciones Extremas

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange)](https://jupyter.org/)
[![License: CC BY-NC 4.0](https://img.shields.io/badge/License-CC%20BY--NC%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc/4.0/)

Repositorio oficial del **Capítulo VI** del libro *Métodos estadísticos en hidrología con Python: análisis de precipitaciones extremas*. Contiene el Jupyter Notebook interactivo y los datos de entrada necesarios para reproducir el análisis estadístico completo de precipitaciones extremas para cualquier estación hidrometeorológica.

---

## 📁 Estructura del repositorio
```
├── CÓDIGO/
│   └── Análisis_Estadístico.ipynb     # Notebook principal
├── ESTACIONES_PROCESADAS/             # Archivos Excel de entrada por estación
│   ├── ESTACION_1_PP.xlsx
│   ├── ESTACION_2_PP.xlsx
│   └── ...
├── OUTPUTS/                           # Resultados generados por el notebook
│   ├── ANALISIS_ESTACION_1_PP/
│   │   ├── ANALISIS_ESTADISTICO_ESTACION_1.xlsx
│   │   ├── Distribucion_Normal.pdf
│   │   ├── Curvas_IDF.pdf
│   │   └── ...
│   └── ...
└── README.md
```

---

## ⚙️ Requisitos

### Instalación de dependencias

Antes de ejecutar el notebook por primera vez, instala las bibliotecas necesarias ejecutando el siguiente comando en tu terminal:
```bash
pip install numpy matplotlib scipy pandas openpyxl
```

### Entorno recomendado

Se recomienda usar **Visual Studio Code** con la extensión de Jupyter:

1. Descarga VS Code: https://code.visualstudio.com/
2. Instala la extensión **Jupyter** desde el Marketplace
3. Abre el archivo `Análisis_Estadístico.ipynb` desde la carpeta `CÓDIGO/`

---

## 🚀 Cómo usar el notebook

El notebook está diseñado para ejecutarse **celda por celda de forma secuencial**. Los únicos parámetros que debes modificar antes de ejecutar son:

| Variable | Descripción | Ejemplo (Windows) |
|---|---|---|
| `direccion` | Ruta de la carpeta `ESTACIONES_PROCESADAS` | `'C:/Users/TuNombre/Desktop/ESTACIONES_PROCESADAS'` |
| `carpeta_salida` | Ruta de la carpeta `OUTPUTS` | `'C:/Users/TuNombre/Desktop/OUTPUTS'` |
| `n_obs` | Número de observaciones diarias del pluviómetro | `1` |
| `nivel_significacion` | Nivel de significación para la prueba K-S | `0.05` |

> 💡 **Tip:** Clona o descarga este repositorio completo y apunta `direccion` y `carpeta_salida` a las carpetas `ESTACIONES_PROCESADAS/` y `OUTPUTS/` descargadas.

---

## 📊 ¿Qué hace el notebook?

El notebook automatiza el flujo completo del análisis estadístico de precipitaciones extremas:

| Etapa | Descripción |
|---|---|
| 1. Importación y depuración | Carga archivos Excel, reemplaza valores faltantes (`S/D`) y calcula máximos anuales |
| 2. Corrección de precipitación | Aplica factores de ajuste según observaciones diarias |
| 3. Datos dudosos | Detecta y elimina valores atípicos |
| 4. Distribuciones de probabilidad | Ajusta Normal, Log-Normal 2P, Log-Normal 3P, Pearson III, Log-Pearson III y Gumbel |
| 5. Bondad de ajuste | Aplica la prueba de Kolmogorov-Smirnov y selecciona la mejor distribución |
| 6. Precipitaciones de diseño | Calcula precipitaciones para periodos de retorno de 5 a 500 años |
| 7. Curvas IDF | Genera curvas Intensidad-Duración-Frecuencia (método de Dick y Peschke) |
| 8. Ecuación IDF | Ajusta `I = K · Tr^m / t^n` por regresión lineal múltiple |
| 9. Exportación | Guarda todos los resultados en un archivo `.xlsx` multihoja y gráficos en PDF/PNG |

---

## 📂 Formato de los datos de entrada

Cada estación debe estar en un archivo `.xlsx` dentro de la carpeta `ESTACIONES_PROCESADAS/` con el siguiente formato:

| Año | Enero | Febrero | ... | Diciembre |
|-----|-----|-----|-----|-----|
| 2006 |   | 28.0 | ... | 40.0 |
| 2007 | 33.0 | 35.0 | ... | 28.0 |

> Los valores no disponibles deben registrarse como ``.  
> El nombre del archivo debe seguir el formato: `NOMBRE_CATEGORIA.xlsx`  
> Ejemplo: `OXAPAMPA_CO.xlsx`, `YANTAC_CO.xlsx`

---

## 📂 Resultados generados (`OUTPUTS/`)

Por cada estación analizada, el notebook genera automáticamente una subcarpeta con:

- `ANALISIS_ESTADISTICO_[ESTACION].xlsx` — archivo Excel multihoja con todos los resultados
- `Distribucion_Normal.pdf / .png`
- `Log_Normal_2_Parametros.pdf / .png`
- `Log_Normal_3_Parametros.pdf / .png`
- `Pearson_III.pdf / .png`
- `Log_Pearson_Tipo_III.pdf / .png`
- `Gumbel.pdf / .png`
- `Curvas_IDF.pdf / .png`
- `Curvas_IDF_ajustadas.pdf / .png`

---

## 📚 Referencia bibliográfica

Este repositorio es el material complementario del libro:

> **Joseph Ruben Francisco Huanay Perez** (2026). *Métodos estadísticos en hidrología con Python: análisis de precipitaciones extremas*. CAPÍTULO VI: AUTOMATIZACIÓN DEL ANÁLISIS HIDROLÓGICO CON PYTHON.

---

## 📬 Contacto y soporte

¿Tienes dudas o encontraste algún error? Abre un [Issue](https://github.com/josephrub/Metodos-estadisticos-en-hidrologia-con-Python/issues) en este repositorio.

---

## 📄 Licencia

Este material está publicado bajo la licencia **Creative Commons Atribución-NoComercial 4.0 Internacional (CC BY-NC 4.0)**.

Esto significa que puedes:
- ✅ Usar y ejecutar el notebook libremente
- ✅ Compartir y redistribuir el material
- ✅ Adaptar y modificar el código para tus propios análisis

Siempre que:
- 📌 Cites al autor original
- 🚫 No uses el material con fines comerciales sin autorización expresa

Más información: https://creativecommons.org/licenses/by-nc/4.0/deed.es
