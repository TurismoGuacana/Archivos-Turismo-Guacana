# Guia de estructura de carpetas - Turismo Guacana

Esta guia explica donde guardar y buscar documentos dentro de la carpeta `EMPRESA`.

Regla principal: cada archivo debe guardarse segun su funcion, no segun quien lo creo.

## Estructura principal

```text
EMPRESA
  00_ADMINISTRACION_EMPRESA
  01_BASE_DE_DATOS_CLIENTES
  02_COTIZACIONES
  03_VIAJES
  04_CONTABILIDAD
  06_MARKETING_E_ITINERARIOS
  07_LEGAL_CONTRATOS_RNT
  08_ARCHIVO_HISTORICO
  99_POR_CLASIFICAR
```

## 00_ADMINISTRACION_EMPRESA

Usar para documentos internos de la empresa que no pertenecen a un viaje especifico.

Ejemplos:

- Cartas administrativas.
- Solicitudes ante alcaldia u otras entidades.
- Documentos del local/oficina.
- Documentos legales personales o patrimoniales relacionados con Luis Alberto Duarte Molina.
- Documentos que deben revisarse antes de decidir si pertenecen a turismo o a otra actividad.

Subcarpeta importante:

`DOCUMENTOS_POR_REVISAR_LEGALES_PERSONALES`

Aqui van documentos que pueden ser utiles, pero que no son operativos de turismo. No se deben borrar sin autorizacion de Luis.

## 01_BASE_DE_DATOS_CLIENTES

Usar para bases de datos, clientes, viajeros frecuentes, comisionistas, deudores y archivos relacionados con informacion maestra.

Subcarpetas:

- `CLIENTES_Y_VIAJEROS`: bases de clientes y viajeros frecuentes.
- `COMISIONISTAS`: comisionistas, comisiones y aliados de venta.
- `COBROS_Y_DEUDORES`: deudas, saldos, morosos o cobros pendientes.

Regla: los listados de pasajeros de un viaje no deben guardarse aqui, salvo que sean usados para consolidar la base maestra.

## 02_COTIZACIONES

Usar para cotizaciones vigentes o recientes.

Regla recomendada:

```text
02_COTIZACIONES
  2025_2026_POR_CLASIFICAR
  COTIZACIONES
  COTIZACIONES (1)
```

Cuando se trabaje con nuevas cotizaciones, crear carpetas por ano y destino:

```text
02_COTIZACIONES
  2026
    2026-07_SAN_ANDRES
    2026-08_EJE_CAFETERO
```

Cotizaciones antiguas de 2024 hacia atras no deben volver a mezclarse en carpetas activas.

## 03_VIAJES

Esta es la carpeta operativa principal.

Usar para viajes reales, salidas, pasajeros, seguros, acomodacion, transporte, listados, liquidaciones y documentos asociados a una fecha de viaje.

Estructura recomendada:

```text
03_VIAJES
  2026
    2026-05_SAN_ANDRES
      01_PASAJEROS
      02_SEGUROS_MAGENTA
      03_ACOMODACION
      04_TRANSPORTE
      05_PAGOS_Y_ABONOS
      06_LIQUIDACION
      07_ITINERARIO_Y_PUBLICIDAD
```

Regla de nombres:

```text
AAAA-MM_DESTINO
```

Ejemplos:

- `2026-05_MEDELLIN`
- `2025-12_MEDELLIN`
- `2025-11_UKUMARI`
- `2025-08_ZIPAQUIRA`

Si no se conoce el mes:

```text
AAAA_DESTINO
```

Si no se conoce el destino:

```text
AAAA-MM_DESTINO_PENDIENTE
```

Subcarpeta especial:

`00_LISTADOS_SUELTOS`

Usar solo para listados que aun no se han podido asociar a un viaje concreto.

## 04_CONTABILIDAD

Usar para cuentas de cobro, liquidaciones generales, ingresos, gastos, soportes y archivos contables que no pertenecen claramente a un viaje especifico.

Subcarpeta:

`CUENTAS_DE_COBRO`

Si una liquidacion pertenece a un viaje especifico, debe ir dentro del viaje en `03_VIAJES`, no aqui.

## 06_MARKETING_E_ITINERARIOS

Usar para itinerarios, volantes, textos promocionales, piezas de impresion y documentos que sirven para vender o comunicar viajes.

Subcarpeta:

`ITINERARIOS_Y_VOLANTES_POR_CLASIFICAR`

Aqui estan los itinerarios y volantes que todavia no se han organizado por destino o ano.

## 07_LEGAL_CONTRATOS_RNT

Usar para documentos legales de Turismo Guacana:

- RUT.
- RNT.
- Camara de comercio.
- Certificados.
- Contratos principales de la empresa.
- Documentos legales que prueban existencia o cumplimiento de la agencia.

## 08_ARCHIVO_HISTORICO

Usar para archivos que no deben estar activos, pero que conviene conservar.

Subcarpetas:

- `00_CUARENTENA_ELIMINAR`: duplicados, cotizaciones antiguas y archivos que salieron de circulacion.
- `ACCESOS_DIRECTOS`: accesos directos `.lnk`.
- `COPIAS_HEREDADAS_POR_REVISAR`: copias anidadas o estructuras antiguas que confundian el archivo principal.
- `RECUPERADOS_AUTOMATICOS_POR_REVISAR`: archivos recuperados automaticamente por Office.

Regla: no borrar nada de archivo historico sin autorizacion.

## 99_POR_CLASIFICAR

Debe permanecer casi vacia.

Usar solo como bandeja temporal cuando no se sabe donde guardar un archivo.

Regla: revisar esta carpeta una vez por semana y mover todo a su carpeta correcta.

## Como guardar un viaje nuevo

1. Crear carpeta dentro del ano correspondiente.
2. Usar formato `AAAA-MM_DESTINO`.
3. Crear subcarpetas internas si el viaje ya esta confirmado:

```text
01_PASAJEROS
02_SEGUROS_MAGENTA
03_ACOMODACION
04_TRANSPORTE
05_PAGOS_Y_ABONOS
06_LIQUIDACION
07_ITINERARIO_Y_PUBLICIDAD
```

## Como nombrar archivos

Formato recomendado:

```text
AAAA-MM-DD_TIPO_DESTINO_DETALLE.ext
```

Ejemplos:

- `2026-05-13_LISTADO_SAN_ANDRES_EMPRESA.xlsx`
- `2026-05-13_MAGENTA_SAN_ANDRES.xlsx`
- `2026-05-13_ACOMODACION_SAN_ANDRES.xlsx`
- `2026-05-13_LIQUIDACION_SAN_ANDRES.xlsx`
- `2026-05-13_ITINERARIO_SAN_ANDRES.docx`

## Que no hacer

- No crear carpetas llamadas `Nueva carpeta`.
- No guardar documentos de un viaje dentro de otro destino.
- No guardar bases de datos en carpetas de viajes.
- No guardar cotizaciones viejas en carpetas activas.
- No guardar archivos personales mezclados con pasajeros o seguros.
- No duplicar carpetas completas.

## Pendientes de orden fino

- Revisar `SIN_FECHA_LEGADO` y asignar ano/mes cuando Luis o Alejandra lo confirmen.
- Revisar `00_LISTADOS_SUELTOS` para asociar cada archivo a un viaje.
- Revisar `DOCUMENTOS_POR_REVISAR_LEGALES_PERSONALES` para decidir si algunos documentos deben salir de la carpeta de empresa.
- Definir una base maestra de clientes para evitar repetir datos.
