# Panel Web de Gestión y Automatización de Contactos E-commerce / Retail

Aplicación web *client-side* ligera diseñada para optimizar los circuitos de seguimiento, reposición de productos y atención postventa en operaciones de retail y e-commerce.

Permite cargar bases de datos desordenadas desde archivos Excel (`.xlsx`, `.xls`, `.csv`) o sincronizar en vivo con enlaces públicos de Google Sheets, normalizando datos operativos en el navegador y generando dinámicamente enlaces parametrizados para la API de WhatsApp Business.

---

## 🚀 Problema de Negocio Resuelto

En entornos operativos de retail y marketplace, las bases de ventas y vencimientos suelen exportarse con múltiples inconsistencias:
* Teléfonos con prefijos heterogéneos (`15`, `011`, código de país faltante).
* Nombres estructurados de forma inconsistente (en ocasiones `Apellido Nombre`, en otras `Nombre Apellido` o nombres de fantasía).
* Descripciones de producto con ruido administrativo (precios unitarios, códigos de barras largos, descuentos o servicios como fletes).
* Carga manual lenta de contactos en agendas móviles, ralentizando el flujo de mensajes de reposición y seguimiento.

Esta herramienta centraliza la ingesta, limpieza algorítmica y activación de contactos en una interfaz unificada sin necesidad de software externo ni instalación de servidores locales.

---

## Características Principales

* **Ingesta flexible de datos:**
  * Sincronización directa con Google Sheets mediante consulta en vivo (`gviz/tq?tqx=out:csv`).
  * Carga local arrastrando y soltando archivos (`.xlsx`, `.xls`, `.csv`) procesados en memoria mediante **SheetJS**.
* **Detección dinámica de cabeceras:** Analiza heurísticamente las primeras filas del documento para mapear columnas de identificación, cliente, teléfono, fecha y producto sin requerir un orden estricto de columnas.
* **Limpieza y normalización algorítmica:**
  * **Teléfonos:** Normalización al estándar internacional argentino (`+54 9 11...`), eliminando ceros, prefijos `15` y caracteres no numéricos.
  * **Catálogo:** Limpieza de texto en descripciones (remoción de `P.Unit`, descuentos, códigos de barra y duplicación de ítems repetidos).
  * **Fechas:** Conversión universal compatible con números de serie de Excel, formato ISO (`YYYY-MM-DD`) y formato estándar (`DD/MM/YYYY`).
* **Motor de plantillas dinámico:** Editor de mensajes de WhatsApp con variables interpretadas en tiempo real (`{nombre}`, `{lista_productos}`, `{producto}`, `{fecha}`, `{vendedor}`) y vista previa interactiva.
* **Gestión operativa:** Filtros por vendedor, estado de contacto (pendientes / enviados / válidos), métricas en tiempo real y persistencia local de URLs frecuentes (`localStorage`).

---

## Stack Tecnológico

* **Frontend:** HTML5 semántico, CSS3 moderno (Variables CSS, Flexbox, CSS Grid).
* **Lógica:** JavaScript nativo (Vanilla JS, ES6+).
* **Procesamiento de datos:** SheetJS (xlsx.full.min.js via CDN).
* **Integraciones:** Google Sheets Visualization API, WhatsApp Click to Chat API.

---

## Uso Local

1. Clonar el repositorio:
   ```bash
   git clone [https://github.com/juanda22/nombre-del-repo.git](https://github.com/juanda22/nombre-del-repo.git)
   ```
2. Abrir el archivo `index.html` en cualquier navegador moderno (no requiere Node.js ni servidor backend).
3. Cargar un archivo Excel de prueba o ingresar el enlace de un Google Sheet público.

---

## 🗺️ Roadmap de Mejoras

- [ ] Exportación directa de listas procesadas a formato `.csv` estandarizado.
- [ ] Incorporación de métricas de conversión y tasa de respuesta estimada.
- [ ] Parametrización avanzada de mensajes con reglas condicionales según antigüedad de compra.
