# Contexto Actuarial

## <¯ Prima Pura de Riesgo
Monto esperado de siniestros por unidad de exposición, sin incluir gastos, utilidad o impuestos.

## =Ê Coberturas del Producto

| Cobertura | Límite (USD) | Descripción |
|-----------|-------------|-------------|
| Contenidos | 10,000 | Pérdida o daño de pertenencias |
| Gastos Adicionales | 20,000 | Reubicación temporal por siniestro |
| Responsabilidad Civil | 300,000 | Demandas por daños a terceros |
| Gastos Médicos RC | 150,000 | Gastos médicos de terceros sin demanda |

## = Variables Clave para Tarificación

### Alta Importancia
- **Extintor de incendios**: Medida directa de prevención
- **Ubicación** (dentro/fuera campus): Seguridad y supervisión
- **Clase de suscripción**: Evaluación experta previa (1=bajo, 2=medio, 3=alto)

### Media Importancia
- **Múltiples inquilinos**: Mayor exposición al riesgo
- **Año cursado**: Experiencia y madurez del estudiante
- **Distancia al campus**: Relación con seguridad del área

## =È Modelos Actuariales Aplicables

### Frecuencia-Severidad
- **Frecuencia**: Poisson o Binomial Negativa (número de siniestros)
- **Severidad**: Gamma o Log-Normal (monto dado siniestro)

### Pérdida Agregada
- **Tweedie**: Maneja naturalmente exceso de ceros
- **Zero-Inflated**: Para ceros estructurales

## <² Principios de Tarificación
1. **Equidad**: Prima debe reflejar el riesgo real
2. **Suficiencia**: Cubrir siniestros esperados
3. **Estabilidad**: Evitar cambios bruscos
4. **Simplicidad**: Factores explicables

## =Ï Métricas de Evaluación

### Error Absoluto Medio (MAE)
- Promedio de diferencias absolutas entre real y predicho
- Objetivo: Minimizar

### Coeficiente de Gini
- Mide capacidad de ordenar riesgos correctamente
- Rango: 0 (sin discriminación) a 1 (perfecta)
- Objetivo: Maximizar

---
*Contexto actuarial para la Competencia CAS y ACTEX 2025*