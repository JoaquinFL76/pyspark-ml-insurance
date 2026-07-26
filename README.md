# Práctica de PySpark ML: Insurance

Entrega en castellano sobre el dataset público `insurance.csv`. El objetivo es
explorar los datos mediante la API de pandas de PySpark y predecir los gastos
médicos (`charges`) con una regresión lineal de `pyspark.ml`.

## Archivos

- `practica_pyspark_ml_insurance.ipynb`: entrega principal, explicada paso a paso.
- `insurance.csv`: copia local del dataset original para una ejecución reproducible.
- `requirements.txt`: versiones recomendadas para una ejecución local opcional.

Fuente del dataset:
<https://raw.githubusercontent.com/stedy/Machine-Learning-with-R-datasets/master/insurance.csv>

## Contenido de la entrega

### Parte 1 (6 puntos): EDA con `pyspark.pandas`

- estructura, tipos y dimensiones;
- estadísticos descriptivos, nulos y duplicados;
- frecuencias y porcentajes de variables categóricas;
- análisis de `charges` por fumador, región y sexo;
- correlaciones, asimetría, cuantiles y visualizaciones;
- conclusiones razonadas y limitaciones del análisis.

### Parte 2 (4 puntos): regresión lineal con `pyspark.ml`

- conversión a un DataFrame normal de Spark;
- limpieza y conversión explícita de tipos;
- división reproducible en entrenamiento y prueba;
- `StringIndexer`, `OneHotEncoder`, `VectorAssembler` y `StandardScaler` dentro
  de un `Pipeline` ajustado únicamente con entrenamiento;
- regresión lineal y evaluación con RMSE, MAE y R²;
- comparación con un modelo base y análisis de residuos.

## Ejecución en Google Colab

1. Sube el notebook. El CSV se descargará automáticamente si no está en la
   misma carpeta.
2. Si Spark no está instalado, ejecuta la celda opcional de instalación.
3. Reinicia el entorno si Colab lo solicita y ejecuta todas las celdas en orden.

La celda incluida instala Java 17 y `pyspark==3.5.1`, tal como indica el
enunciado.

## Ejecución local

Con Java 17 y Python instalados:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
export JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64
export PYARROW_IGNORE_TIMEZONE=1
jupyter notebook practica_pyspark_ml_insurance.ipynb
```

El notebook no guarda un modelo ni modifica el dataset original. Se fija
`seed=42` para que la división sea reproducible.
