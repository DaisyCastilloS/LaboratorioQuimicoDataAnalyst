# 🧪 Proyecto de Análisis de Datos - Laboratorio Químico

Este proyecto simula un entorno profesional de análisis de datos en el área de salud y laboratorio químico. Utiliza Docker para garantizar entornos reproducibles, PostgreSQL como base de datos relacional, Python y JupyterLab para el análisis interactivo, y Power BI para la visualización final.

---

## 📁 Estructura del Proyecto

laboratorioquimicodataanalyst/
├── data/ # Datos crudos (ej: produccion_iqvia_sucia.csv)
├── notebooks/ # Notebooks de análisis (ej: limpieza_analisis.ipynb)
├── docs/ # Documentación técnica
├── reports/ # Resultados exportados (CSV limpio, dashboard.pbix)
│ └── capturas_dashboard/ # Capturas del dashboard (PNG)
├── docker-compose.yml # Orquestación de contenedores
├── Dockerfile # Imagen de Python + librerías
└── README.md # Este archivo


---

## 🧰 Tecnologías Usadas

- 🐍 Python 3.13
- 📊 Power BI
- 📚 JupyterLab
- 🐘 PostgreSQL 16
- 🐳 Docker & Docker Compose
- 📦 pandas, seaborn, matplotlib, SQLAlchemy

---

## ⚙️ Configuración del Entorno

1. Levanta los servicios con Docker:
```bash
docker compose up --build -d

Accede a JupyterLab desde tu navegador:
👉 http://localhost:8888🔄 Flujo General del Proyecto



Flujo General del Proyecto
📂 CSV sucio → 🧹 Limpieza en Python → 📁 CSV limpio → 📊 Power BI → 🖼️ Dashboard final

Flujo de Trabajo Detallado
1. Cargar datos sucios
Coloca los archivos originales en la carpeta data/.
Ejemplo: data/produccion_iqvia_sucia.csv

2. Limpieza de datos en Python
Abre el notebook notebooks/limpieza_analisis.ipynb para:

Unificar formatos de fecha

Normalizar texto

Eliminar duplicados

Convertir tipos de datos

Rellenar nulos

import pandas as pd
df = pd.read_csv('../data/produccion_iqvia_sucia.csv')
df['fecha'] = pd.to_datetime(df['fecha'], errors='coerce')
df['equipo'] = df['equipo'].str.lower().str.strip()
df.drop_duplicates(inplace=True)


3. Análisis exploratorio y visualización

df.groupby("equipo")["muestras_procesadas"].mean().sort_values()

import seaborn as sns
import matplotlib.pyplot as plt
sns.boxplot(data=df, x="equipo", y="rendimiento")
plt.xticks(rotation=45)
plt.show()

4. Exportación de resultados

df.to_csv('../reports/produccion_limpia_final.csv', index=False)

Abre el CSV limpio en Power BI para crear tu dashboard, y guarda como .pbix:

reports/informe de datos de laboratorio.pbix

🧾 Diccionario de Datos

| Campo                 | Tipo   | Descripción                                          |
| --------------------- | ------ | ---------------------------------------------------- |
| `fecha`               | date   | Fecha de procesamiento                               |
| `equipo`              | string | Nombre del equipo utilizado                          |
| `turno`               | string | Turno de trabajo (mañana, tarde, noche)              |
| `muestras_procesadas` | int    | Cantidad de muestras procesadas                      |
| `rendimiento`         | float  | Indicador de eficiencia (procesadas / unidad tiempo) |
| `comentario`          | string | Observaciones registradas manualmente                |




🧠 Lecciones aprendidas

Automatización de limpieza de datos en pandas
Visualización profesional con Power BI
Buenas prácticas en estructura de proyectos
Orquestación de entorno de análisis reproducible con Docker
Documentación técnica clara para proyectos de portafolio

👩‍💻 Autora
Daisy Castillo Sepúlveda
Desarrolladora Full Stack & Analista de Datos en formación
🔗 [LinkedIn](https://www.linkedin.com/in/daisy-castillo-sepulveda)
📁 [GitHub](https://github.com/daisy-castillo-sepulveda)

