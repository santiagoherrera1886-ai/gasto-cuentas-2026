# Gasto por plataformas · 2026

Dashboard estático para revisar inversión en **Meta Ads, Google Ads y TikTok Ads**, usando los **9 archivos proporcionados**, con corte del **1 de enero al 30 de septiembre de 2026**.

## Funciones

- Resumen de inversión por plataforma, cliente y cuenta.
- Filtros por plataforma, cliente, archivo fuente, moneda y búsqueda.
- Tabla de 23 registros consolidados de cuentas y descarga en CSV.
- Consulta de 195 campañas con gasto positivo procedentes de Google y TikTok. Campañas sin gasto excluidas del explorador.
- Auditoría con diferencias entre total de cuenta y campañas visibles.
- Monedas COP y MXN separadas, sin conversiones automáticas.
- Sin base de datos, tokens ni instalación de dependencias.

## Cifras acumuladas enero–septiembre 2026

| Plataforma | Importe |
| --- | ---: |
| Meta Ads | COP 5.320.591.534 |
| Google Ads | COP 1.389.881.387,34 |
| TikTok Ads | COP 175.642.338,53 |
| **Total COP** | **COP 6.886.115.259,87** |
| Meta Ads · México | MXN 2.020.928,11 (separado) |

## Metodología y límites

1. Se ignoran filas de totales como campañas, resúmenes globales sin nombre y presupuestos (que no equivalen al gasto).
2. Meta Ads: se usa "Monto gastado" por cuenta y moneda, sin sumar el resumen global.
3. TikTok Ads: se suma "Spend" de campañas; concilia con los totales del reporte.
4. Google Ads: el resumen usa el **total de cuenta** cuando las campañas visibles difieren. Las filas "Total: Campañas" con campaña "--" no se suman otra vez.
5. No se calcula gasto mensual porque los archivos originales son acumulados. No se incluye octubre-diciembre.
6. El reporte Google de "Informe de campaña (1).xlsx" no identifica la cuenta, por lo que COP 148.263.323,23 permanece en "Otros / sin identificar".
7. Las cuentas de Meta con nombres parecidos no se fusionan sin IDs verificados.

## Discrepancias Google Ads

| Fuente | Total de cuenta | Campañas visibles | Diferencia (COP) |
| --- | ---: | ---: | ---: |
| Informe de campaña (1).xlsx | 148.263.323,23 | 148.263.323,21 | 0,02 |
| Informe de campaña (2).xlsx | 405.953.038,73 | 403.668.502,18 | 2.284.536,55 |
| Informe de campaña (8).csv | 621.962.020,13 | 466.826.363,07 | 155.135.657,06 |
| Informe de campaña.xlsx | 213.703.005,25 | 48.618.877,34 | 165.084.127,91 |

Estas diferencias se muestran en la sección de auditoría y **no se asignan a campañas ficticias**.

## Estructura

- index.html: interfaz y filtros, exploración y descarga CSV.
- data.packed.js: datos derivados de los archivos; comprimidos en zlib/deflate y codificados en base64 para cargarse desde el navegador.
- Los XLSX y CSV originales no se publicaron en el repositorio.

## Despliegue en Vercel

Proyecto previsto: sa-ntiago/gasto-cuentas-2026. Sitio estático: Framework Preset **Other**, Root Directory **/**, sin comandos de build ni variables de entorno. Conectar el repositorio santiagoherrera1886-ai/gasto-cuentas-2026 a este proyecto. Branch de producción: main.

Para actualizar con otros meses de 2026, volver a consolidar el rango completo o incorporar solo períodos sin solapamiento; nunca sumar dos exportaciones acumuladas con fechas coincidentes.

**Atención:** el repositorio GitHub es público. Los montos consolidados incluidos en él también son públicos.
