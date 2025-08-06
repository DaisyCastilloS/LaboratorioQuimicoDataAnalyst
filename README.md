# Proyecto de Análisis de Datos - Laboratorio Quimico

Este proyecto simula un entorno profesional de análisis de datos en el área de salud. Utiliza Docker para garantizar entornos reproducibles, PostgreSQL como base de datos relacional, y JupyterLab para el análisis interactivo con Python.

---

## 🔹 Estructura del Proyecto

```
iqvia-data-project/
├── data/                      # Datos crudos (ej: produccion_iqvia_sucia.csv)
├── notebooks/                 # Notebooks de análisis (ej: limpieza_analisis.ipynb)
├── docs/                      # Documentación técnica
├── reports/                   # Resultados exportados (CSV limpio, dashboard.pbix)
├── docker-compose.yml         # Orquestación de contenedores
├── Dockerfile                 # Imagen de Python + librerías
└── README.md                  # Este archivo
```

---

## 🔹 Tecnologías Usadas

- Python 3.13
- JupyterLab
- Docker y Docker Compose
- PostgreSQL 16
- pandas, seaborn, matplotlib, sqlalchemy

---

## 🔹 Configuración del Entorno

1. Levanta los servicios con Docker:
```bash
docker compose up --build -d
```

2. Accede a JupyterLab:
👉 http://localhost:8888

---

## 🔹 Flujo de Trabajo

### 1. Cargar datos sucios
Coloca los archivos originales en la carpeta `data/`.  
Ejemplo: `data/produccion_iqvia_sucia.csv`

### 2. Limpieza de datos en Python
Usa el notebook `notebooks/limpieza_analisis.ipynb` para:

- Unificar formatos de fecha
- Normalizar texto
- Eliminar duplicados
- Convertir tipos de datos
- Rellenar nulos

```python
import pandas as pd
df = pd.read_csv('../data/produccion_iqvia_sucia.csv')
df['fecha'] = pd.to_datetime(df['fecha'], errors='coerce')
df['equipo'] = df['equipo'].str.lower().str.strip()
df.drop_duplicates(inplace=True)
```

### 3. Análisis y visualización
```python
df.groupby("equipo")["muestras_procesadas"].mean().sort_values()
```

```python
import seaborn as sns
import matplotlib.pyplot as plt
sns.boxplot(data=df, x="equipo", y="rendimiento")
plt.xticks(rotation=45)
plt.show()
```

### 4. Exportación
Exporta los datos limpios y dashboard:
```python
df.to_csv('../reports/produccion_limpia_final.csv', index=False)
```
Abre en Power BI y guarda como `reports/dashboard.pbix`

---

## 🔹 Documentación

- `README.md`: resumen general del proyecto

---

## 🔹 Autora

Daisy Castillo Sepúlveda  
[GitHub](https://github.com/daisy-castillo-sepulveda)

---

## 🔹 Licencia

MIT License