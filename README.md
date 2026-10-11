# Práctica 1 — Word Count con Hadoop MapReduce en Java (Individual)

## 1. Datos de la entrega

- **Estudiante:** [Nombre y apellidos]
- **Asignatura:** Big Data
- **Práctica:** 1 — Word Count con Hadoop MapReduce
- **Fecha:** [31/10/2026]

## 2. Objetivos

- Comprender las fases Map, Shuffle/Sort y Reduce.
- Implementar Word Count con la API Java de Hadoop MapReduce.
- Compilar el proyecto y ejecutarlo en el entorno Hadoop.
- Validar la salida con casos de prueba reproducibles.

## 3. Enunciado

Implementa un programa que cuente las apariciones de cada palabra de uno o varios ficheros de texto mediante Hadoop MapReduce.

- **Mapper:** normaliza cada token a minúsculas y emite `(palabra, 1)`.
- **Combiner:** realiza una suma local opcional de los conteos para reducir el tráfico de red.
- **Reducer:** suma todos los valores de cada palabra y emite `(palabra, total)`.
- **Driver:** configura el trabajo, sus clases, los tipos de salida y las rutas de entrada/salida.

Documenta la definición de palabra elegida y el tratamiento de puntuación, números, acentos y líneas vacías.

## 4. Entorno

- Ubuntu
- Java 21
- Hadoop 3.5.0
- Local / Stand-alone

## 5. Estructura del proyecto

```text
.
├── README.md
├── pom.xml
├── src/main/java/es/bigdata/wordcount/
│   ├── WordCount.java
│   ├── WordCountMapper.java
│   └── WordCountReducer.java
├── data/
│   └── input.txt
└── docs/
    └── resultados/
```

## 6. Caso de prueba

Entrada (`data/input.txt`):

```text
Hola mundo hola
Big Data, mundo.
```

Salida esperada, sin importar el orden de las claves:

```text
big	1
data,	1
hola	2
mundo	2
```

Nota: el código inicial separa por espacios y elimina puntuación al principio y al final de cada token. Por ello, `Data,` se convierte en `data`. Actualiza el resultado esperado si modificas la tokenización.

Añade más casos: palabras repetidas, líneas vacías, puntuación, números y caracteres acentuados. Incluye los resultados reales en la entrega.

## 7. Análisis

Explica:
- Qué clave y valor emite el mapper.
- Qué función cumple Shuffle/Sort.
- Por qué el reducer recibe una lista de valores por palabra.
- Por qué la suma puede utilizarse como combiner.
- Qué limitaciones tiene la tokenización elegida.

## 8. Resultados

Guarda en `docs/resultados/` capturas o registros de:
- Versiones de Java y Hadoop.
- Compilación correcta con Maven.
- Ejecución del trabajo.
- Contenido de la salida final.

## 9. Conclusiones

[Resume lo aprendido, las dificultades y las soluciones.]

## 10. Fuentes

- [Apache Hadoop — MapReduce Tutorial](https://hadoop.apache.org/docs/stable/hadoop-mapreduce-client/hadoop-mapreduce-client-core/MapReduceTutorial.html)
- [Apache Hadoop — MapReduce API](https://hadoop.apache.org/docs/stable/api/)
