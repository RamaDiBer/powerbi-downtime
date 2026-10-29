# ⏱️ Downtime de sistemas en planta

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-1557b0?style=for-the-badge)
![Power Query](https://img.shields.io/badge/Power%20Query%20(M)-217346?style=for-the-badge)
![SharePoint](https://img.shields.io/badge/SharePoint-0078D4?style=for-the-badge&logo=microsoftsharepoint&logoColor=white)

> Tablero para medir el **tiempo de parada no productivo** causado por fallas de sistemas (caídas de servidores, aplicaciones, red, PLC) en distintos sitios y unidades de negocio.

## 📌 Qué responde

- ¿Cuántas horas y minutos de **downtime** hubo en el mes y cómo se compara con el **mes anterior**?
- ¿Qué **motivos** generan más tiempo de parada?
- ¿Qué **sitios** y **unidades de negocio** son los más afectados?
- ¿Cuántos incidentes hubo y cuál es el downtime promedio por incidente?

## 🔄 Flujo de datos

1. El registro de incidentes se carga en un Excel en **SharePoint**: fecha, motivo, sitio, turno, unidad de negocio, ticket y duración.
2. **Power Query** lee el archivo con `SharePoint.Files`, quita filas vacías y convierte las duraciones (`hh:mm`) a **minutos** para poder sumarlas.
3. El modelo agrega columnas de Mes y Año, y una tabla `TablaMeses` para ordenar.

## 📐 Medidas

| Medida | Qué mide |
|---|---|
| Total Downtime (min) / (hs) | Tiempo total de parada |
| Cantidad Incidentes | Eventos registrados |
| % Downtime | Minutos de parada sobre un día completo (1.440 min) |
| Downtime Mes Anterior | Comparación mes contra mes con `PREVIOUSMONTH` |
| Downtime por Sitio | Tiempo de parada por sitio |
| … Visual | Versiones formateadas para tarjetas y etiquetas |

## 🔒 Datos

El repositorio incluye **solo el modelo y el diseño del informe**, sin el Excel ni el `.pbix`. El registro original tiene información interna y nombres de personas.

## ▶️ Cómo abrirlo

1. Abrir `Downtime.pbip` con Power BI Desktop.
2. Apuntar la consulta `Downtime` a un Excel con la misma estructura (hoja `Downtime`).
3. Actualizar.
