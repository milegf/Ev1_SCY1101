# SCY1101 — Evaluación Parcial N°1
## Programación para la Ciencia de Datos

**Integrantes:** Milenka Guerra - Fabián Quiñones
**Dataset:** `Food_Preference_raw.csv`

---

## Descripción

Este proyecto corresponde a la Evaluación Parcial N°1 del curso SCY1101. Se realiza un proceso completo de análisis, limpieza, manipulación y transformación del dataset **Food Preference**, que contiene 290 registros sobre preferencias alimentarias de participantes de distintas nacionalidades, recopilados entre mayo y junio de 2019.

---

## Estructura del repositorio

```
SCY1101_EvParc1/
├── Data/
│   ├── raw/
│   │   └── Food_Preference_raw.csv            # Dataset original sin modificaciones (290 filas, 8 columnas)
│   └── processed/
│       └── food_preference_limpio.csv         # Dataset procesado y listo para análisis
├── Notebooks/
│   └── SCY1101_EvParc1_Guerra_Quinones.ipynb  # Notebook principal
├── requirements.txt                           # Dependencias del proyecto
└── README.md
```

---

## Contenido del notebook

El notebook está organizado en las siguientes secciones:

1. **Importación de librerías y configuración del entorno** — carga de dependencias y ajuste de opciones de visualización de pandas
2. **Carga y Exploración Inicial** — revisión general del dataset (dimensiones, tipos, nulos, duplicados), análisis descriptivo por variable y exploración cruzada entre variables
3. **Manipulación de Datos** — selección de columnas con valor analítico, eliminación de duplicados y conversión de tipos de dato
4. **Limpieza de Datos** — tratamiento de outliers en `Age` mediante el método IQR, normalización de texto, corrección manual de categorías inconsistentes e imputación de valores nulos con `SimpleImputer`
5. **Transformación de Datos** — pipeline de preprocesamiento con `StandardScaler` para variables numéricas y `OneHotEncoder` para variables categóricas
6. **Visualizaciones** — comparaciones antes/después de la limpieza para cada variable del dataset procesado
7. **Exportación** — guardado del dataset procesado en `Data/processed/`

---

## Dataset

El dataset original contiene **290 registros** y **8 columnas**:

| Variable | Tipo | Descripción | Observaciones |
|---|---|---|---|
| `Timestamp` | string | Fecha y hora del registro | 285 valores únicos |
| `Participant_ID` | string | Identificador del participante | 288 valores únicos |
| `Gender` | string | Género | 5 categorías (incluye errores), 6 nulos |
| `Nationality` | string | Nacionalidad | 28 variantes (incluye errores tipográficos) |
| `Age` | float | Edad del participante | 2 nulos, valores fuera de rango (-47 a 263) |
| `Food` | string | Preferencia de comida | 7 variantes (incluye duplicados por texto) |
| `Juice` | string | Preferencia de bebestible | 2 categorías limpias |
| `Dessert` | string | Preferencia de postre | 3 categorías limpias |

Tras el preprocesamiento se conservan únicamente las columnas con valor analítico: `Age`, `Gender`, `Nationality`, `Food`, `Juice` y `Dessert`.

---

## Requisitos

- Python 3.10+
- Las dependencias están listadas en `requirements.txt`

```
pandas
numpy
matplotlib
seaborn
scikit-learn
jupyter
```

---

## Instalación y ejecución

```bash
# 1. Clonar el repositorio
git clone https://github.com/<usuario>/SCY1101_EvParc1.git
cd SCY1101_EvParc1

# 2. Crear y activar entorno virtual
python -m venv venv
source venv/bin/activate        # En Windows: venv\Scripts\activate

# 3. Instalar dependencias
pip install -r requirements.txt

# 4. Abrir el notebook
jupyter notebook Notebooks/SCY1101_EvParc1_Guerra_Quinones.ipynb
```

> Asegurarse de que el archivo `Food_Preference_raw.csv` esté en `Data/raw/` antes de ejecutar el notebook.
