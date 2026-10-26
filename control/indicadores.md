# Indicadores de control

El control cierra el proceso administrativo: se fija un estándar, se mide, se compara y se corrige.

## Indicadores de gestión del proyecto

| Indicador | Fórmula | Fuente | Frecuencia | Meta / umbral | Responsable | Acción si se desvía |
|---|---|---|---|---|---|---|
| Desvío de cronograma | Días hábiles de atraso del hito / duración planificada x 100 | Gantt y milestones de GitHub | En cada hito | ≤ 10 % (alerta si el atraso supera 4 días hábiles) | Dirección General | Reducir el alcance de la versión 1 antes que correr la fecha (Entrega 2). |
| Avance del backlog | Puntos de historias en Hecho / puntos totales de la versión x 100 | GitHub Projects | Semanal | Según el plan de cada iteración (≥ 90 % de lo comprometido) | Desarrollo de Software | Repriorizar historias Could y Should. |
| Ritmo de entrega (velocidad) | Puntos completados por iteración de 2 semanas | GitHub Projects | Por iteración | Estable; se usa para replanificar | Desarrollo de Software | Ajustar el compromiso de la siguiente iteración. |
| Integración controlada | PRs fusionados con descripción e issue vinculado / PRs fusionados x 100 | GitHub (Pull Requests) | Semanal | 100 % | Sistemas y Tecnología | No fusionar sin descripción ni issue. |
| Defectos en aceptación | Defectos encontrados por clientes piloto por historia aceptada | Issues con etiqueta defecto | En la fase de pruebas | ≤ 1 defecto por historia | Sistemas y Tecnología | Agregar casos de prueba antes de corregir. |
| Migración sin pérdida (M2) | Registros migrados / registros de la planilla x 100; duplicados por DNI/CUIT | CLIENTE, POLIZA | Al migrar | 100 % y 0 duplicados | Técnico-Operativa | Revisar el log de rechazos y volver a migrar. |


## Indicadores del sistema en funcionamiento

| Indicador | Fórmula | Fuente (diccionario de datos) | Frecuencia | Meta | Responsable |
|---|---|---|---|---|---|
| Alertas a tiempo (M4) | Pólizas con alerta generada 30 días antes / pólizas vigentes que vencen en el mes x 100 | ALERTA_VENCIMIENTO, POLIZA | Mensual | 100 % | Técnico-Operativa |
| Renovaciones gestionadas a tiempo (M4) | Alertas cerradas antes del vencimiento / alertas del mes x 100 | ALERTA_VENCIMIENTO | Mensual | ≥ 95 % | Técnico-Operativa |
| Tasa de retención | Pólizas renovadas / pólizas vencidas en el período x 100 | POLIZA (estado), ALERTA_VENCIMIENTO | Mensual | ≥ 85 % (línea base a medir el primer trimestre) | Dirección General |
| Bajas por precio | Bajas con motivo Precio / total de bajas x 100 | ALERTA_VENCIMIENTO (motivo_baja) | Trimestral | Seguimiento; si supera 50 % se revisan compañías | Dirección General |
| Registro de consultas (M5) | Consultas de WhatsApp registradas en menos de 1 minuto / mensajes recibidos x 100 | INTERACCION | Mensual | ≥ 90 % | Comercial y Marketing Digital |
| Tiempo de primera respuesta | Promedio entre la consulta y la primera respuesta | INTERACCION (fecha_hora) | Semanal | ≤ 2 horas hábiles | Comercial y Marketing Digital |
| Conversión de cotizaciones | Cotizaciones aceptadas / cotizaciones enviadas x 100, por canal de origen | COTIZACION, CLIENTE (canal_origen) | Mensual | Seguimiento por canal | Comercial y Marketing Digital |
| Control de comisiones (M6) | Liquidaciones conciliadas dentro de 5 días hábiles / liquidaciones recibidas x 100 | COMISION | Mensual | 100 % | Administración y Finanzas |
| Diferencia de comisiones | Suma de (esperado - liquidado) / suma de lo esperado x 100 | COMISION | Mensual | ≤ 2 % | Administración y Finanzas |
| Rendimiento (M3) | Percentil 95 del tiempo de apertura de la ficha | Registro de la aplicación | Mensual | ≤ 2 segundos | Sistemas y Tecnología |
