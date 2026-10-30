# Análisis de los registros — Hospital San Gabriel

**Alcance:** caso académico con 20 pacientes y datos completamente ficticios. Los resultados describen únicamente esta base simulada y no constituyen conclusiones clínicas.

## Indicadores

| Indicador | Resultado | Interpretación |
|---|---:|---|
| Total de pacientes | **20** | Se estructuraron 20 registros, uno por paciente. |
| Edad promedio | **43 años** | La media aritmética de las edades registradas es 43 años. |
| Temperatura promedio | **37,145 °C** (≈ **37,15 °C**) | Se incluyeron las 20 temperaturas, porque ninguna está ausente. |
| Cantidad por sexo | **F: 10 · M: 10** | La distribución está equilibrada: cada categoría representa el 50 % de los registros. |
| Cantidad por estado de atención | **Finalizada: 9 · En atención: 7 · Pendiente: 4** | La mayoría de los registros figura como finalizada (45 %); el 35 % sigue en atención y el 20 % está pendiente. |
| Saturación mínima registrada | **91 %** | Es el menor valor disponible y corresponde a P009. Las celdas vacías se ignoran en el cálculo. |
| Registros incompletos | **1** | P016 no tiene registrada la saturación de oxígeno. No se imputó ni estimó ese valor. |

## Inconsistencias y decisiones de limpieza

Los registros originales presentaban variaciones de formato que se normalizaron para facilitar el análisis:

- **Fechas:** aparecían como `20/10/2026`, `21 de octubre de 2026`, `2026-10-22`, `22/10/26` y otras variantes. Se convirtieron a fechas reales de Excel y se muestran como `AAAA-MM-DD`.
- **Sexo:** las expresiones `mujer`, `femenino` y `F` se normalizaron como `F`; `hombre`, `masculino` y `M` como `M`.
- **Signos vitales:** se unificaron las etiquetas de temperatura, pulso/frecuencia cardíaca y oxígeno/saturación. Los valores se guardaron como números; las temperaturas con coma decimal se interpretaron con punto decimal.
- **Estado de atención:** expresiones equivalentes como `Atención finalizada` y `Finalizada` se consolidaron en `Finalizada`. Se conservaron las categorías `Pendiente` y `En atención`.
- **Dato ausente:** en P016 no se informó la saturación de oxígeno. La celda correspondiente se dejó vacía, sin asumir un valor. Por ello, el registro cuenta como incompleto; el promedio de temperatura y la saturación mínima no requieren excluir otros datos.

No se añadieron diagnósticos ni mediciones que no estuvieran presentes en los registros suministrados.

## Reflexión sobre privacidad clínica

La información clínica requiere protección incluso cuando se utiliza con fines académicos. Un registro puede revelar aspectos sensibles de una persona al combinar edad, motivo de consulta, signos vitales y diagnóstico, aunque no incluya su nombre. Por eso, los datos deben limitarse a lo necesario, almacenarse en espacios protegidos y estar disponibles solo para quienes tengan autorización. Los códigos de paciente ayudan a reducir la exposición directa de la identidad, pero no sustituyen otras medidas de seguridad ni eliminan el riesgo de reidentificación. También es importante evitar compartir archivos clínicos en canales públicos, revisar los permisos antes de distribuirlos y conservar la trazabilidad de los cambios. En este ejercicio se usan datos ficticios; en un entorno real, estas precauciones son esenciales para respetar la confidencialidad y la confianza del paciente.
