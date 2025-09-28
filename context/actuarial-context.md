# Contexto Actuarial

## <� Prima Pura de Riesgo
Monto esperado de siniestros por unidad de exposici�n, sin incluir gastos, utilidad o impuestos.

## =� Coberturas del Producto

| Cobertura | L�mite (USD) | Descripci�n |
|-----------|-------------|-------------|
| Contenidos | 10,000 | P�rdida o da�o de pertenencias |
| Gastos Adicionales | 20,000 | Reubicaci�n temporal por siniestro |
| Responsabilidad Civil | 300,000 | Demandas por da�os a terceros |
| Gastos M�dicos RC | 150,000 | Gastos m�dicos de terceros sin demanda |

## = Variables Clave para Tarificaci�n

### Alta Importancia
- **Extintor de incendios**: Medida directa de prevenci�n
- **Ubicaci�n** (dentro/fuera campus): Seguridad y supervisi�n
- **Clase de suscripci�n**: Evaluaci�n experta previa (1=bajo, 2=medio, 3=alto)

### Media Importancia
- **M�ltiples inquilinos**: Mayor exposici�n al riesgo
- **A�o cursado**: Experiencia y madurez del estudiante
- **Distancia al campus**: Relaci�n con seguridad del �rea

## =� Modelos Actuariales Aplicables

### Frecuencia-Severidad
- **Frecuencia**: Poisson o Binomial Negativa (n�mero de siniestros)
- **Severidad**: Gamma o Log-Normal (monto dado siniestro)

### P�rdida Agregada
- **Tweedie**: Maneja naturalmente exceso de ceros
- **Zero-Inflated**: Para ceros estructurales

## <� Principios de Tarificaci�n
1. **Equidad**: Prima debe reflejar el riesgo real
2. **Suficiencia**: Cubrir siniestros esperados
3. **Estabilidad**: Evitar cambios bruscos
4. **Simplicidad**: Factores explicables

## =� M�tricas de Evaluaci�n

### Error Absoluto Medio (MAE)
- Promedio de diferencias absolutas entre real y predicho
- Objetivo: Minimizar

### Coeficiente de Gini
- Mide capacidad de ordenar riesgos correctamente
- Rango: 0 (sin discriminaci�n) a 1 (perfecta)
- Objetivo: Maximizar

---
*Contexto actuarial para la Competencia CAS y ACTEX 2025*