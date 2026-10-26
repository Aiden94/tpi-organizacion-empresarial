# Diccionario de datos inicial del CRM (Entrega 3)

Tipos: `Integer`, `String(n)`, `Decimal(p,s)`, `Date`, `DateTime`, `Boolean`, `Enum`. PK = clave primaria, FK = clave foránea.

## CLIENTE (crítica)

| Campo | Tipo de dato | Clave | Descripción funcional |
|---|---|---|---|
| id_cliente | Integer | PK | Identificador único generado por el sistema. |
| tipo_persona | Enum (Física, Jurídica) |  | Define qué datos son obligatorios y qué productos corresponden. |
| nombre_razon_social | String(120) |  | Nombre y apellido, o razón social de la empresa. |
| dni_cuit | String(13) | Único | Documento o CUIT sin guiones. Se usa para evitar duplicados (meta M2). |
| telefono_whatsapp | String(20) | Único | Número en formato internacional. Vincula las conversaciones del asistente con la ficha. |
| email | String(100) |  | Correo para envío de pólizas y documentación. |
| localidad | String(60) |  | Localidad de residencia o de la actividad. Influye en la tarifa de varios ramos. |
| estado_relacion | Enum (Prospecto, Cliente, Ex cliente) |  | Ubica a la persona en el embudo comercial. |
| canal_origen | Enum (WhatsApp, Instagram, Web, Referido, LinkedIn, Otro) |  | Canal por el que llegó. Permite medir qué canal trae clientes que renuevan. |
| fecha_alta | Date |  | Fecha del primer contacto registrado. |
| consentimiento_datos | Boolean |  | Indica si el titular autorizó el tratamiento de sus datos (Ley 25.326). Sin consentimiento no se envían mensajes automáticos. |
| fecha_consentimiento | Date |  | Fecha en que se otorgó el consentimiento, como respaldo ante un reclamo. |

## COMPANIA_ASEGURADORA (crítica)

| Campo | Tipo de dato | Clave | Descripción funcional |
|---|---|---|---|
| id_compania | Integer | PK | Identificador único de la compañía. |
| razon_social | String(120) |  | Nombre legal de la aseguradora. |
| cuit | String(11) | Único | CUIT de la compañía, para conciliar liquidaciones y facturas. |
| codigo_productor | String(20) |  | Código que la compañía asignó al productor. Aparece en cada liquidación. |
| porcentaje_comision_base | Decimal(5,2) |  | Porcentaje de comisión general pactado. Se usa si la póliza no tiene uno propio. |
| tiene_integracion | Boolean |  | Indica si la compañía permite descargar la cartera en forma automática o si se carga a mano. |
| activa | Boolean |  | Permite dejar de operar con una compañía sin borrar su historial. |

## POLIZA (crítica)

| Campo | Tipo de dato | Clave | Descripción funcional |
|---|---|---|---|
| id_poliza | Integer | PK | Identificador interno de la póliza. |
| id_cliente | Integer | FK | Cliente asegurado (CLIENTE). |
| id_compania | Integer | FK | Compañía emisora (COMPANIA_ASEGURADORA). |
| numero_poliza | String(30) |  | Número asignado por la compañía. Puede incluir letras y barras. |
| ramo | Enum (Automotor, Hogar, Vida, Accidentes personales, Integral de comercio, RC, ART, Otro) |  | Tipo de seguro. Permite analizar la cartera por línea de producto. |
| bien_asegurado | String(150) |  | Descripción breve del riesgo cubierto (patente, domicilio, actividad). |
| suma_asegurada | Decimal(14,2) |  | Monto máximo cubierto. Se revisa en cada renovación por la inflación. |
| premio | Decimal(12,2) |  | Precio total que paga el cliente por el período. |
| moneda | Enum (ARS, USD) |  | Moneda de la póliza. |
| fecha_inicio_vigencia | Date |  | Inicio de la cobertura. |
| fecha_fin_vigencia | Date |  | Fin de la cobertura. Es el dato que dispara la alerta de vencimiento. |
| porcentaje_comision | Decimal(5,2) |  | Comisión pactada para esta póliza. Si se deja vacío se usa la de la compañía. |
| estado | Enum (Vigente, Renovada, Vencida, Anulada) |  | Situación actual de la póliza en la cartera. |
| id_poliza_anterior | Integer | FK | Póliza que esta renueva (referencia a la misma entidad). Arma la historia del cliente. |

## INTERACCION

| Campo | Tipo de dato | Clave | Descripción funcional |
|---|---|---|---|
| id_interaccion | Integer | PK | Identificador del contacto. |
| id_cliente | Integer | FK | Cliente o prospecto involucrado. |
| fecha_hora | DateTime |  | Momento del contacto. Permite medir el tiempo de respuesta. |
| canal | Enum (WhatsApp, Instagram, Email, Teléfono, Presencial) |  | Medio por el que se produjo. |
| tipo | Enum (Consulta, Cotización, Aviso de vencimiento, Siniestro, Reclamo, Seguimiento) |  | Motivo del contacto. |
| resumen | String(500) |  | Síntesis del contenido, cargada por el usuario o generada por el asistente. |
| origen_registro | Enum (Automático, Manual) |  | Indica si lo registró el flujo de n8n o una persona (meta M5). |
| id_conversacion_externa | String(64) |  | Identificador de la conversación en WhatsApp, para volver al mensaje original. |

## COTIZACION

| Campo | Tipo de dato | Clave | Descripción funcional |
|---|---|---|---|
| id_cotizacion | Integer | PK | Identificador de la cotización. |
| id_cliente | Integer | FK | Cliente o prospecto que pidió la cotización. |
| id_compania | Integer | FK | Compañía cotizada. Una consulta genera varias cotizaciones, una por compañía. |
| ramo | Enum (mismos valores que POLIZA) |  | Tipo de seguro cotizado. |
| premio_cotizado | Decimal(12,2) |  | Precio ofrecido. |
| fecha_envio | Date |  | Fecha en que se envió la propuesta al cliente. |
| resultado | Enum (Pendiente, Aceptada, Rechazada) |  | Resultado comercial de la propuesta. |
| motivo_rechazo | String(200) |  | Motivo informado por el cliente si no aceptó. Es retroalimentación para la Dirección. |
| id_poliza_generada | Integer | FK | Póliza emitida a partir de esta cotización, si fue aceptada. |

## COMISION

| Campo | Tipo de dato | Clave | Descripción funcional |
|---|---|---|---|
| id_comision | Integer | PK | Identificador del registro. |
| id_poliza | Integer | FK | Póliza que genera la comisión. |
| periodo | String(7) |  | Mes de la liquidación en formato AAAA-MM. |
| importe_esperado | Decimal(12,2) |  | Calculado por el sistema: premio cobrado por porcentaje de comisión. |
| importe_liquidado | Decimal(12,2) |  | Importe que informó la compañía en su liquidación. |
| fecha_liquidacion | Date |  | Fecha en que se recibió la liquidación. |
| conciliada | Boolean |  | Indica si se revisó la diferencia entre lo esperado y lo liquidado (meta M6). |
| fecha_conciliacion | Date |  | Fecha de la revisión. Junto con la fecha de liquidación mide el plazo de control. |

## ALERTA_VENCIMIENTO

| Campo | Tipo de dato | Clave | Descripción funcional |
|---|---|---|---|
| id_alerta | Integer | PK | Identificador de la alerta. |
| id_poliza | Integer | FK | Póliza próxima a vencer. |
| fecha_generacion | Date |  | Fecha en que el sistema creó la alerta. |
| dias_anticipacion | Integer |  | Días entre la alerta y el vencimiento. Por defecto 30 (meta M4). |
| cliente_notificado | Boolean |  | Indica si se envió el aviso al cliente por WhatsApp. |
| estado | Enum (Pendiente, En gestión, Renovada, Baja) |  | Avance de la gestión de la renovación. |
| motivo_baja | Enum (Precio, Cambio de compañía, Venta del bien, Sin respuesta, Otro) |  | Causa de la baja. Alimenta el análisis de retención de la Dirección. |

## Relaciones

| Relación | Cardinalidad | Lectura |
|---|---|---|
| CLIENTE - POLIZA | 1 a N | Un cliente puede tener muchas pólizas; cada póliza pertenece a un solo cliente. |
| COMPANIA_ASEGURADORA - POLIZA | 1 a N | Una compañía emite muchas pólizas; cada póliza es de una compañía. |
| POLIZA - POLIZA | 1 a 1 | Cada renovación apunta a la póliza que reemplaza (id_poliza_anterior). |
| CLIENTE - INTERACCION | 1 a N | Todos los contactos quedan asociados a la ficha del cliente. |
| CLIENTE - COTIZACION | 1 a N | Una consulta puede generar varias cotizaciones (una por compañía). |
| COTIZACION - POLIZA | 1 a 0..1 | Una cotización aceptada genera una póliza; una rechazada no. |
| POLIZA - COMISION | 1 a N | Una póliza genera una comisión por cada período liquidado. |
| POLIZA - ALERTA_VENCIMIENTO | 1 a N | Una póliza genera una alerta en cada vencimiento a lo largo de los años. |
