# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

# Competencia de Casos CAS y ACTEX 2025
## Modelo Predictivo para Tarificación de Seguros de Inquilinos

## 🎯 Contexto del Proyecto

### Descripción General
Estamos participando en la **Competencia de Casos CAS y ACTEX 2025**, desarrollando un modelo predictivo para **Sigma Seguros**, una aseguradora de líneas personales que busca optimizar su tarificación en el mercado de seguros para inquilinos residenciales, específicamente para estudiantes universitarios con su producto "Póliza para Dormitorios".

### Objetivo Principal
Desarrollar un **modelo predictivo actuarialmente sólido** que utilice tanto el historial de siniestros como los datos demográficos para determinar una **prima pura de riesgo** individualizada para cada asegurado, reemplazando el actual sistema de prima única para todos.

### Responsables del Proyecto

- Estudiantes de Maestría en Actuaría y Finanzas (UNAL)

**José Miguel Acuña Hernández**
**Guillermo Murillo Tirado**
**Yeferson Fabian Rubio**
**Sergio Diaz Vera**
**Andres Steven Puertas Londoño**

- Docente del departamento de Estadistica (UNAL)

**Mario Enrique Arrieta**

## 📊 Estructura de Datos

### Dataset Principal
- **Archivo**: `data/input/Competencia de Casos CAS y ACTEX - Datos - datos.csv`
- **Registros**: 10,000 pólizas con diferentes grados de riesgo
- **Período**: Un año de siniestralidad histórica

### Variables Disponibles

#### Variables Demográficas
- `estudiante_id`: Identificador único
- `nombre`: Nombre del asegurado
- `año_cursado`: 1er año, 2do año, 3er año, 4to año, posgrado
- `estudios_area`: Administración, Ciencias, Humanidades, Otro
- `calif_promedio`: Promedio académico (escala 0-10)
- `genero`: Masculino, Femenino, Otro, No respuesta
- `2_o_mas_inquilinos`: Si/No - Múltiples inquilinos en la vivienda

#### Variables de Ubicación
- `en_campus`: Dentro de campus / Fuera de campus
- `distancia_al_campus`: Distancia en unidades (0 si está dentro del campus)

#### Variables de Riesgo
- `extintor_incendios`: Si/No - Presencia de extintor
- `clase_suscripcion`: Clase1, Clase2, Clase3 - Asignada por departamento de suscripción
- `retencion`: entrenamiento/validacion - División del dataset

#### Variables de Siniestralidad (4 coberturas)
1. **Contenidos** (límite USD 10,000)
   - `Contenidos_siniestros_num`: Número de siniestros
   - `Contenidos_siniestros_monto`: Monto total de siniestros

2. **Gastos Adicionales de Vivienda** (límite USD 20,000)
   - `Gastos_Adicionales_siniestros_num`: Número de siniestros
   - `Gastos_Adicionales_siniestros_monto`: Monto total de siniestros

3. **Responsabilidad Civil** (límite USD 300,000)
   - `Resp_Civil_siniestros_num`: Número de siniestros
   - `Resp_Civil_siniestros_monto`: Monto total de siniestros

4. **Gastos Médicos RC** (límite USD 150,000)
   - `Gastos_Medicos_RC_siniestros_num`: Número de siniestros
   - `Gastos_Medicos_RC_siniestros_monto`: Monto total de siniestros

### División de Datos
- **Entrenamiento**: Registros con `retencion = "entrenamiento"` - Incluyen todas las variables
- **Validación**: Registros con `retencion = "validacion"` - Sin información de siniestralidad (holdout)

## 🎯 Métricas de Evaluación

### Primera Fase - Clasificación
Los equipos serán rankeados por el promedio de dos métricas:

1. **Error Absoluto Medio (EAM)**
   - Fórmula: `EAM = (1/N) * Σ|Y_k - Ŷ_k|`
   - Objetivo: **Minimizar** (menor es mejor)

2. **Coeficiente de Gini**
   - Mide la capacidad del modelo para diferenciar riesgos
   - Objetivo: **Maximizar** (mayor es mejor)
   - Archivo de referencia: `gini_coef_ilustracion.xlsm`

**Ranking final**: Promedio de las posiciones en ambas métricas
**Clasificados**: Los 5 mejores equipos pasan a la segunda fase

### Variable Objetivo
**Monto total de siniestros** para la suma de las cuatro coberturas

## 📋 Entregables de la Competencia

1. **Archivo de predicciones**:
   - Formato: `Competencia de Casos CAS y ACTEX - Hoja de Predicciones.xlsx`
   - Una predicción por cada registro de validación
   - Columna: `prediccion monto total siniestro`

2. **Documento explicativo** (1 página):
   - Proceso de modelación
   - Modelos considerados
   - Justificación del modelo seleccionado

### Segunda Fase (Final)
Presentación ante jueces abordando:
- Análisis de datos y transformaciones
- Técnicas de modelación evaluadas
- Validación y evidencia del modelo
- Consideraciones de negocio
- Estrategia de tarificación a mediano plazo

## 🔧 Metodología Recomendada

### Modelos Sugeridos
- **GLMs (Modelos Lineales Generalizados)**: Estándar de la industria
- **Árboles de Decisión**: Para capturar interacciones no lineales
- **Gradient Boosting Models**: Para optimización de predicciones
- **Ensambles**: Combinación de múltiples modelos

### Consideraciones Técnicas

#### Estructura de Prima de Riesgo
1. Definir clase base de referencia
2. Calcular prima base
3. Aplicar factores multiplicativos relativos: `prima_riesgo = prima_base × (1 ± X%)`

#### Decisiones de Modelación
- ¿Un modelo global o modelos separados por cobertura?
- ¿Modelar frecuencia y severidad por separado o pérdida agregada?
- ¿Cómo manejar el desbalance de clases (muchos ceros en siniestros)?

### Proceso CRISP-DM Recomendado
1. **Comprensión del Negocio**: Contexto de seguros para estudiantes
2. **Comprensión de Datos**: EDA exhaustivo de las 10,000 pólizas
3. **Preparación de Datos**:
   - Tratamiento de valores faltantes
   - Codificación de variables categóricas
   - Feature engineering
4. **Modelación**: Desarrollo y comparación de modelos
5. **Evaluación**: Métricas EAM y Gini
6. **Despliegue**: Predicciones finales

## 📁 Estructura del Proyecto

```
competencia_cas/
│
├── CLAUDE.md                    # Este archivo - Contexto del proyecto
├── README.md                    # Documentación general
├── LICENSE                      # Licencia del proyecto
├── environmet.yml               # Configuración del entorno conda
│
├── .claude/                     # Configuración de Claude Code
│   └── settings.local.json
│
├── context/                     # Contexto detallado para Claude Code
│   ├── actuarial-context.md     # Fundamentos actuariales y de tarificación
│   ├── methodology.md           # Metodología CRISP-DM y técnicas
│   ├── project-overview.md      # Vista general del proyecto
│   └── standards.md             # Estándares de código y documentación
│
├── data/
│   ├── input/                   # Datos originales de la competencia
│   │   ├── Competencia de Casos CAS y ACTEX - Descripción.pdf
│   │   ├── Competencia de Casos CAS y ACTEX - Datos - datos.csv
│   │   ├── Competencia de Casos CAS y ACTEX - Hoja de Predicciones.xlsx - Predicciones.csv
│   │   └── [1-4].jpg            # Diapositivas de presentación
│   ├── processed/               # Datos procesados y transformados
│   └── output/                  # Predicciones generadas
│
├── notebooks/                   # Jupyter notebooks para análisis
│   └── exploracion.ipynb        # Análisis exploratorio inicial
│
├── src/                         # Código fuente Python/R
│   ├── data/                    # Módulos de procesamiento de datos
│   ├── test/                    # Tests unitarios
│   └── utils/                   # Funciones utilitarias
│
├── models/                      # Modelos entrenados serializados
│
├── report/                      # Documentación LaTeX del proyecto
│   ├── main.tex                 # Documento principal
│   ├── referencias.bib          # Referencias bibliográficas
│   ├── config/                  # Configuración LaTeX
│   │   ├── commands.tex         # Comandos personalizados
│   │   ├── doc_style.tex        # Estilos del documento
│   │   └── packages.tex         # Paquetes LaTeX
│   ├── content/                 # Contenido del reporte
│   └── images/                  # Imágenes para el reporte
│
├── output/                      # Salidas finales y entregables
│
└── images/                      # Gráficos y visualizaciones del proyecto

```

## 📚 Archivos de Contexto Detallado

Para información más específica, consultar:

- **[`context/project-overview.md`](context/project-overview.md)**: Vista general resumida del proyecto y equipo
- **[`context/actuarial-context.md`](context/actuarial-context.md)**: Conceptos actuariales, coberturas y métricas
- **[`context/methodology.md`](context/methodology.md)**: Framework CRISP-DM y plan de trabajo
- **[`context/standards.md`](context/standards.md)**: Estándares de código y documentación

---

## 🛠️ Configuración del Entorno

### Entornos Conda

El proyecto usa dos entornos conda separados:

**Python (Principal)**:
```bash
conda env create -f environmet_python.yml
conda activate competencia_cas_python
```

**R (Análisis complementario)**:
```bash
conda env create -f environment_r.yml
conda activate competencia_cas_r
```

### Jupyter Notebooks

Todos los notebooks están en `notebooks/`. Para iniciar Jupyter:
```bash
jupyter notebook notebooks/
# o
jupyter lab
```

## 📂 Arquitectura de Datos

### Pipeline de Procesamiento

1. **Datos crudos**: `data/input/input.csv` (10,000 registros totales)
   - 7,999 registros de entrenamiento (`retencion == "entrenamiento"`)
   - 2,001 registros de validación (`retencion == "validacion"`)

2. **Notebook de preprocesamiento**: `notebooks/tratamiento_data.ipynb`
   - Elimina columnas: `nombre`, `estudiante_id`, `clase_suscripcion`, `en_campus`, `retencion`
   - Genera 8 datasets procesados en `data/processed/`:

**Por cada cobertura se generan 2 datasets**:
- `{cobertura}_full.csv`: Todos los registros (para modelos de clasificación)
- `{cobertura}_siniestrados.csv`: Solo registros con siniestros (para frecuencia/severidad)

**Coberturas**:
- `contenidos_*` (743 siniestrados de 7,999)
- `adicionales_*` (416 siniestrados de 7,999)
- `medicos_*` (183 siniestrados de 7,999)
- `rc_*` (67 siniestrados de 7,999)

3. **Datos de validación final**: `data/input/test.csv`
   - 2,001 IDs de estudiantes para predicción final

## 🔬 Metodología de Modelación

### Estrategia de Modelación por Cobertura

Para cada una de las 4 coberturas desarrollamos **3 modelos**:

1. **Clasificación** (`clasificacion_{cobertura}.ipynb`):
   - Input: `{cobertura}_full.csv`
   - Target: Binario (siniestrado vs no siniestrado)
   - Optimización: F1-score (dataset muy desbalanceado)

2. **Frecuencia** (`frecuencia_{cobertura}.ipynb`):
   - Input: `{cobertura}_siniestrados.csv`
   - Target: `{Cobertura}_siniestros_num` (conteo)
   - Optimización: MAE

3. **Severidad** (`severidad_{cobertura}.ipynb`):
   - Input: `{cobertura}_siniestrados.csv`
   - Target: `{Cobertura}_siniestros_monto` (monto)
   - Optimización: MAE

### Pipeline Estándar de Cada Notebook

**Fase 1: Preparación y GLM Baseline**
1. Estandarizar variables numéricas (StandardScaler)
2. One-hot encoding de variables categóricas
3. Split train/test 80/20
4. GLM con selección backward de variables
   - Clasificación: Logistic Regression
   - Frecuencia: Poisson/Negative Binomial GLM
   - Severidad: Gamma/Inverse Gaussian GLM
5. Si un nivel de variable categórica es seleccionado, incluir **todos** los niveles
6. Con variables seleccionadas, correr LazyPredict para identificar top algoritmos

**Fase 2: Optimización de Top 5 Modelos**
1. Tomar los 5 mejores modelos de LazyPredict
2. GridSearchCV con validación cruzada sobre train set
   - Parámetros de regularización para evitar overfitting
   - Métrica de optimización:
     - Regresión (frecuencia/severidad): `scoring='neg_mean_absolute_error'`
     - Clasificación: `scoring='f1'`
3. Para clasificación: optimizar threshold de probabilidad (no usar default 0.5)
4. Evaluar modelos optimizados en test set
5. Imprimir métricas:
   - **Regresión**: MAE, GINI, R²
   - **Clasificación**: MAE, GINI, R², Accuracy

**Fase 3: Exportación**
1. El modelo seleccionado se exporta a `models/` (se indicará cuál exportar)
2. Usar joblib o pickle para serialización

### Notebooks Existentes

```
notebooks/
├── tratamiento_data.ipynb          # Preprocesamiento inicial
├── clasificacion_contenidos.ipynb  # Clasificación Contenidos
├── frecuencia_contenidos.ipynb     # Frecuencia Contenidos
├── severidad_contenidos.ipynb      # Severidad Contenidos (modificado)
├── clasificacion_adicionales.ipynb # Clasificación Gastos Adicionales
├── frecuencia_adicionales.ipynb    # Frecuencia Gastos Adicionales
├── severidad_adicionales.ipynb     # Severidad Gastos Adicionales
├── clasificacion_medicos.ipynb     # Clasificación Gastos Médicos RC
├── frecuencia_medicos.ipynb        # Frecuencia Gastos Médicos RC
├── severidad_medicos.ipynb         # Severidad Gastos Médicos RC
├── clasificacion_rc.ipynb          # Clasificación Resp. Civil
├── frecuencia_rc.ipynb             # Frecuencia Resp. Civil
└── severidad_rc.ipynb              # Severidad Resp. Civil
```

## 📊 Variables del Dataset

### Variables Predictoras Disponibles

Después de eliminar ID y columnas redundantes, quedan:

- `año_cursado`: 1er año, 2do año, 3er año, 4to año, posgrado (categórica)
- `estudios_area`: Administración, Ciencias, Humanidades, Otro (categórica)
- `calif_promedio`: Promedio académico 0-10 (numérica)
- `genero`: Masculino, Femenino, Otro, No respuesta (categórica)
- `2_o_mas_inquilinos`: Si/No (categórica)
- `distancia_al_campus`: Distancia en unidades (numérica, 0 si dentro campus)
- `extintor_incendios`: Si/No (categórica)

### Variables Target por Tipo de Modelo

| Cobertura | Clasificación | Frecuencia | Severidad |
|-----------|--------------|------------|-----------|
| Contenidos | `Contenidos_siniestros_num > 0` | `Contenidos_siniestros_num` | `Contenidos_siniestros_monto` |
| Gastos Adicionales | `Gastos_Adicionales_siniestros_num > 0` | `Gastos_Adicionales_siniestros_num` | `Gastos_Adicionales_siniestros_monto` |
| Resp. Civil | `Resp_Civil_siniestros_num > 0` | `Resp_Civil_siniestros_num` | `Resp_Civil_siniestros_monto` |
| Gastos Médicos RC | `Gastos_Medicos_RC_siniestros_num > 0` | `Gastos_Medicos_RC_siniestros_num` | `Gastos_Medicos_RC_siniestros_monto` |

## 🎯 Consideraciones Actuariales Clave

### Desbalance de Clases

Los datasets están **muy desbalanceados**:
- Contenidos: 9.3% siniestros (743/7999)
- Gastos Adicionales: 5.2% siniestros (416/7999)
- Gastos Médicos: 2.3% siniestros (183/7999)
- Resp. Civil: 0.8% siniestros (67/7999)

**Implicaciones**:
- Usar F1-score (no accuracy) para clasificación
- Considerar técnicas de balanceo si es necesario (SMOTE, class_weight)
- Optimizar threshold de clasificación para balance precision/recall

### Familias de Distribución para GLMs

**Clasificación**: Binomial (link=logit)
**Frecuencia**: Poisson o Negative Binomial (sobredispersión)
**Severidad**: Gamma (montos positivos, asimétricos) o Inverse Gaussian

## 🚀 Comandos Comunes

### Git
```bash
# Ver estado
git status

# Commit de cambios
git add .
git commit -m "Descripción del cambio"
git push
```

### Gestión de Modelos
```bash
# Los modelos se guardan en models/
ls -lh models/

# Exportar modelo desde notebook:
# import joblib
# joblib.dump(modelo, '../models/nombre_modelo.pkl')
```

---

*Última actualización: 2025-10-10*