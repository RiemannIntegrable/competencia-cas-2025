# Metodología del Proyecto

## 📋 Framework CRISP-DM

### 1. Comprensión del Negocio
- **Objetivo**: Reemplazar tarifa única por tarificación individualizada
- **Métricas de éxito**: MAE bajo, Gini > 0.35
- **Restricciones**: Solo datos históricos de 1 año

### 2. Comprensión de los Datos
- **Volumen**: 10,000 pólizas
- **Variables**: 20+ predictoras, 4 targets de siniestros
- **División**: ~80% entrenamiento, ~20% validación
- **Análisis necesarios**: Distribuciones, correlaciones, valores faltantes

### 3. Preparación de Datos
- **Limpieza**: Tratamiento de faltantes y outliers
- **Transformación**: Codificación de categóricas
- **Feature Engineering**: Crear variables derivadas relevantes
- **Normalización**: Según requerimientos del modelo

### 4. Modelación
- **Baseline**: GLM (Poisson/Gamma/Tweedie)
- **Machine Learning**: XGBoost, Random Forest
- **Ensemble**: Combinación de mejores modelos
- **Validación cruzada**: 5-fold estratificado

### 5. Evaluación
- **Métricas principales**: MAE y Coeficiente de Gini
- **Métricas secundarias**: RMSE, R², Deviance
- **Diagnóstico**: Análisis de residuos
- **Comparación**: Entre modelos candidatos

### 6. Despliegue
- **Predicciones**: Archivo CSV para validación
- **Documentación**: Reporte de 1 página
- **Presentación**: Si clasificamos a segunda fase

## 🔧 Flujo de Trabajo

### Sprint 1: Exploración (Semana 1)
- [ ] EDA completo
- [ ] Identificación de patrones
- [ ] Hipótesis iniciales

### Sprint 2: Modelación Base (Semana 2)
- [ ] GLM baseline
- [ ] Primeros modelos ML
- [ ] Validación inicial

### Sprint 3: Optimización (Semana 3)
- [ ] Feature engineering avanzado
- [ ] Hyperparameter tuning
- [ ] Ensemble

### Sprint 4: Finalización (Semana 4)
- [ ] Predicciones finales
- [ ] Documentación
- [ ] Preparación presentación

## 📊 Estrategias de Modelación

### Enfoque por Cobertura
- Modelo separado para cada cobertura
- Mayor precisión pero más complejidad

### Enfoque Global
- Un modelo para suma total de siniestros
- Más simple pero menos granular

### Enfoque Híbrido
- Modelos para coberturas principales
- Agregación para total

## 🎯 Consideraciones Importantes

### Desafíos Esperados
- Exceso de ceros en siniestros
- Desbalance de clases
- Correlación entre coberturas
- Límites de cobertura (censura)

### Estrategias de Mitigación
- Modelos zero-inflated o Tweedie
- Validación cruzada cuidadosa
- Regularización
- Ensemble para robustez

---
*Metodología para la Competencia CAS y ACTEX 2025*