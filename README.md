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
- comparación con un modelo base y análisis de residuos;
- pruebas de humo sobre la limpieza, la división y las predicciones;
- registro de versiones para facilitar la reproducibilidad de la corrección.

## Ejecución en Google Colab

1. Sube el notebook. El CSV se descargará automáticamente si no está en la
   misma carpeta.
2. Ejecuta la celda de comprobación del entorno: sólo instalará Java 17 y
   PySpark 3.5.1 si PySpark no está disponible.
3. Ejecuta todas las celdas en orden.

Se indican Java 17 y `pyspark==3.5.1` porque son exactamente las versiones
propuestas en el enunciado de la práctica, no una elección arbitraria. El
notebook también desactiva explícitamente el modo ANSI para seguir funcionando
si Colab ya incluye una versión 4.x de Spark.

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
