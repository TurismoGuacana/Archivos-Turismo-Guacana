# Propuesta de base de datos y automatizacion

Empresa: Turismo Guacana  
Responsables operativos: Luis Alberto Duarte Molina y Alejandra  
Fecha: junio de 2026

## Diagnostico

Turismo Guacana ya tiene datos valiosos, pero estan dispersos en archivos de clientes, viajeros frecuentes, comisionistas, listados por viaje, seguros Magenta, acomodaciones, pagos y liquidaciones.

El problema principal no es falta de informacion. El problema es que el mismo cliente se vuelve a escribir en cada viaje, los pagos quedan separados de la reserva, los listados Magenta se preparan manualmente y no hay una vista clara de ventas, saldos, clientes frecuentes o comisiones.

## Objetivo

Crear una base de datos unica para que cada cliente exista una sola vez y cada viaje tenga reservas, pagos, seguros, acomodacion y comisiones conectadas.

La meta no es volver complejo el negocio. La meta es que Luis y Alejandra puedan responder rapido:

- Quien viaja.
- Quien debe saldo.
- Quien ya pago.
- Quien falta por enviar a seguro.
- Que comisionista vendio.
- Que clientes son frecuentes.
- Que destino se vende mejor.
- A quien escribirle por WhatsApp para vender, recordar pagos o confirmar datos.

## Recomendacion por fases

### Fase 1: ordenar en Excel maestro

Crear un archivo llamado:

`BASE_DATOS_TURISMO_GUACANA.xlsx`

Hojas recomendadas:

- `CLIENTES`
- `VIAJES`
- `RESERVAS`
- `PAGOS`
- `COMISIONISTAS`
- `PROVEEDORES`
- `SEGUROS`
- `ACOMODACION`

Esta fase sirve para limpiar nombres, documentos duplicados y datos incompletos sin gastar en tecnologia todavia.

### Fase 2: pasar a Supabase

Cuando el Excel maestro este limpio, mi recomendacion es pasar a Supabase.

Supabase es buena opcion porque usa PostgreSQL, permite tener base de datos real, autenticacion, almacenamiento de archivos, funciones de servidor y actualizaciones en tiempo real. Esto permitiria construir una app sencilla para la empresa sin depender eternamente de hojas de calculo.

Ventajas para Turismo Guacana:

- Una sola base de datos para clientes, viajes, reservas y pagos.
- Acceso desde celular o computador.
- Roles: Luis puede ver todo, Alejandra puede operar viajes, comisionistas pueden consultar solo sus clientes si se decide.
- Historial de viajes por cliente.
- Reportes automaticos.
- Guardar comprobantes, documentos y archivos asociados.
- Preparar listados Magenta automaticamente.
- Conectar WhatsApp de forma ordenada.

Riesgos:

- Requiere una configuracion inicial bien hecha.
- Hay que cuidar datos personales y permisos.
- No conviene automatizar WhatsApp de forma agresiva.
- Debe existir copia/exportacion de seguridad.

Mi opinion: Supabase si tiene sentido para Turismo Guacana, pero no como primer paso. Primero hay que limpiar y definir el modelo de datos. Despues Supabase puede ser el corazon del sistema.

## Modelo de datos recomendado

### CLIENTES

Cada persona debe estar una sola vez.

Campos:

- `id_cliente`
- `nombre_completo`
- `tipo_documento`
- `numero_documento`
- `fecha_nacimiento`
- `celular`
- `whatsapp`
- `correo`
- `municipio`
- `contacto_emergencia`
- `telefono_emergencia`
- `restricciones_alimentarias`
- `condiciones_medicas`
- `autoriza_tratamiento_datos`
- `observaciones`
- `fecha_creacion`
- `fecha_actualizacion`

### VIAJES

Cada salida o producto turistico.

Campos:

- `id_viaje`
- `nombre_viaje`
- `destino`
- `fecha_salida`
- `fecha_regreso`
- `tipo_viaje`: pasadia, terrestre, aereo, nacional, internacional
- `estado`: planeado, abierto, cerrado, realizado, cancelado
- `cupo_total`
- `valor_por_persona`
- `responsable`
- `observaciones`

### RESERVAS

Relaciona cliente con viaje. Esta es la tabla mas importante.

Campos:

- `id_reserva`
- `id_cliente`
- `id_viaje`
- `fecha_reserva`
- `estado`: interesado, reservado, abonado, pagado, cancelado
- `valor_total`
- `saldo`
- `municipio_salida`
- `bus`
- `silla`
- `habitacion`
- `comisionista`
- `seguro_enviado`
- `datos_confirmados`
- `observaciones`

### PAGOS

Cada abono debe ser un registro separado.

Campos:

- `id_pago`
- `id_reserva`
- `fecha_pago`
- `valor`
- `metodo_pago`
- `recibido_por`
- `comprobante`
- `observaciones`

### COMISIONISTAS

Campos:

- `id_comisionista`
- `nombre`
- `celular`
- `municipio`
- `tipo_comision`
- `valor_comision`
- `estado`
- `observaciones`

### SEGUROS

Campos:

- `id_seguro`
- `id_reserva`
- `aseguradora`
- `fecha_envio`
- `estado`
- `archivo_soporte`
- `observaciones`

### ACOMODACION

Campos:

- `id_acomodacion`
- `id_reserva`
- `hotel`
- `habitacion`
- `tipo_habitacion`
- `acompanantes`
- `observaciones`

## WhatsApp: que automatizar y que no

WhatsApp puede ser una herramienta poderosa, pero debe usarse con cuidado. No recomiendo enviar mensajes masivos sin control ni usar herramientas no oficiales que puedan poner en riesgo el numero de la empresa.

La ruta seria usar WhatsApp Business Platform / Cloud API de Meta o un proveedor autorizado conectado a esa API.

Automatizaciones utiles:

- Confirmar datos del cliente.
- Enviar recordatorio de saldo.
- Enviar itinerario antes del viaje.
- Confirmar punto y hora de salida.
- Avisar que el seguro fue gestionado.
- Enviar mensaje de agradecimiento despues del viaje.
- Preguntar por interes en proximos destinos.
- Enviar promociones solo a clientes que autoricen recibir mensajes.

Ejemplos de mensajes:

`Hola {{nombre}}, desde Turismo Guacana te recordamos que tu saldo para {{viaje}} es de {{saldo}}. Fecha limite sugerida: {{fecha}}.`

`Hola {{nombre}}, confirmamos tu reserva para {{viaje}}. Salida: {{fecha_salida}}. Municipio de salida: {{municipio_salida}}.`

`Hola {{nombre}}, gracias por viajar con Turismo Guacana. Queremos saber como fue tu experiencia.`

Lo que no recomiendo:

- Comprar bases de datos externas.
- Enviar promociones a personas que no autorizaron.
- Usar bots no oficiales que controlen WhatsApp Web.
- Enviar demasiados mensajes de marketing.
- Reemplazar totalmente la atencion humana.

## Arquitectura futura recomendada

Una version profesional podria ser:

```text
Formulario web o app interna
        |
        v
Supabase PostgreSQL
        |
        +--> Panel interno para Luis y Alejandra
        +--> Reportes de viajes, pagos y comisiones
        +--> Generador de listados Magenta
        +--> Automatizacion WhatsApp
        +--> Copias de seguridad y exportacion Excel
```

## Orden de trabajo recomendado

1. Consolidar todos los archivos actuales de base de datos en un Excel maestro.
2. Eliminar duplicados por numero de documento.
3. Normalizar nombres, telefonos, municipios y fechas de nacimiento.
4. Crear la tabla de viajes historicos y viajes futuros.
5. Crear reservas usando los listados recientes.
6. Definir estados: interesado, reservado, abonado, pagado, cancelado.
7. Probar el sistema con un viaje nuevo.
8. Solo despues, construir Supabase.
9. Conectar WhatsApp primero para recordatorios y confirmaciones, no para marketing masivo.

## Decision recomendada

Mi recomendacion concreta es:

Primero crear `BASE_DATOS_TURISMO_GUACANA.xlsx` en esta carpeta y usarlo como fuente limpia. Cuando ya tengamos clientes, viajes, reservas y pagos ordenados, migramos a Supabase.

Supabase debe verse como el sistema operativo del negocio turistico: clientes, reservas, pagos, comisiones, documentos y mensajes conectados.

WhatsApp debe verse como el canal de comunicacion, no como la base de datos. La base manda; WhatsApp solo comunica.

## Fuentes consultadas

- Supabase Docs: https://supabase.com/docs/
- Supabase Edge Functions: https://supabase.com/docs/guides/functions
- Meta WhatsApp Business Platform / Cloud API: https://developers.facebook.com/docs/whatsapp/
