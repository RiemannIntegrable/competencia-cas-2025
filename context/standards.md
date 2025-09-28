# Estándares del Proyecto

## 📝 Convenciones Generales

### Nomenclatura de Archivos
- **Notebooks**: `01_exploracion.ipynb`, `02_modelacion.ipynb`
- **Scripts**: `snake_case.py` (Python), `snake_case.R` (R)
- **Datos**: `YYYY-MM-DD_descripcion.csv`
- **Modelos**: `modelo_tipo_v1.pkl`

### Estructura de Carpetas
```
data/
  input/      # Datos originales (no modificar)
  processed/  # Datos procesados
  output/     # Predicciones

notebooks/    # Análisis exploratorio y pruebas
src/          # Código de producción
models/       # Modelos entrenados
report/       # Documentación y reportes
```

## 🐍 Python

### Estilo de Código
- Seguir PEP 8
- Docstrings para todas las funciones
- Type hints cuando sea posible
- Nombres descriptivos

### Ejemplo de Función
```python
def calcular_prima(frecuencia: float, severidad: float) -> float:
    """
    Calcula la prima pura como frecuencia × severidad.

    Parameters:
        frecuencia: Número esperado de siniestros
        severidad: Costo promedio por siniestro

    Returns:
        Prima pura de riesgo
    """
    return frecuencia * severidad
```

## 📊 R

### Estilo de Código
- Usar tidyverse style guide
- Comentarios en español
- Pipes (`%>%`) para claridad

### Ejemplo de Función
```r
calcular_prima <- function(frecuencia, severidad) {
  # Calcula la prima pura
  # Args:
  #   frecuencia: Número esperado de siniestros
  #   severidad: Costo promedio por siniestro
  # Returns:
  #   Prima pura de riesgo

  prima <- frecuencia * severidad
  return(prima)
}
```

## 📓 Notebooks

### Estructura Recomendada
1. **Título y objetivo**
2. **Imports y configuración**
3. **Carga de datos**
4. **Análisis/Modelación**
5. **Resultados**
6. **Conclusiones**

### Buenas Prácticas
- Limpiar outputs innecesarios antes de commitear
- Numeración secuencial de notebooks
- Markdown para explicaciones
- Gráficos con títulos y etiquetas

## 🔄 Control de Versiones

### Commits
```bash
# Formato: tipo: descripción breve
feat: agregar modelo XGBoost
fix: corregir imputación de faltantes
docs: actualizar README
refactor: simplificar pipeline
```

### Branches
- `main`: Código estable
- `develop`: Desarrollo activo
- `feature/nombre`: Nuevas características
- `fix/nombre`: Correcciones

## 📊 Visualizaciones

### Principios
- Claridad sobre complejidad
- Títulos descriptivos
- Etiquetas en ejes
- Leyendas cuando necesario
- Colores consistentes

### Paleta de Colores
- Principal: `#1f77b4` (azul)
- Secundario: `#ff7f0e` (naranja)
- Éxito: `#2ca02c` (verde)
- Alerta: `#d62728` (rojo)

## 📋 Documentación

### Comentarios en Código
- Explicar el "por qué", no el "qué"
- En español
- Actualizar cuando se modifica código

### README de Carpetas
Cada carpeta principal debe tener un README explicando:
- Propósito
- Contenido
- Cómo usar

## ✅ Checklist Pre-Commit

- [ ] Código ejecuta sin errores
- [ ] Tests pasan (si aplica)
- [ ] Documentación actualizada
- [ ] Sin datos sensibles
- [ ] Notebooks limpios
- [ ] Mensaje de commit descriptivo

---
*Estándares para la Competencia CAS y ACTEX 2025*