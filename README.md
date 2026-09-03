# Sistema SIEM con Machine Learning para la Detección y Priorización de Amenazas

Módulo de Inteligencia Artificial para la detección, correlación y priorización automatizada de incidentes de seguridad en tiempo real utilizando el algoritmo **Random Forest Classifier**.

---

## 1. Problema
Los equipos de respuesta ante incidentes (SOC) sufren de una agobiante **fatiga de alertas** debido al alto volumen de registros de red e intensos niveles de falsos positivos (hasta un 80%) generados por los sistemas SIEM tradicionales basados en reglas estáticas. Esto provoca que ciberataques reales y sigilosos (como movimientos laterales o fuerza bruta distribuida) pasen desapercibidos, exponiendo a las organizaciones a filtraciones de información y pérdidas económicas.

---

## 2. Objetivos

### Objetivo General
Desarrollar un módulo SIEM impulsado por Machine Learning mediante el algoritmo **Random Forest Classifier** para la detección, correlación y priorización automatizada de amenazas de seguridad en tiempo real.

### Objetivos Particulares
1. **Diseñar** e implementar un pipeline de ingestión y normalización de datos para procesar eventos de autenticación y tráfico de red en formatos JSON/Syslog.
2. **Construir** un componente de ingeniería de características (*Feature Engineering*) para transformar registros crudos en vectores numéricos comportamentales dentro de ventanas temporales.
3. **Entrenar** y evaluar el modelo Random Forest Classifier utilizando conjuntos de datos de ciberseguridad reconocidos (CSE-CIC-IDS2018), alcanzando un F1-Score superior al 92%.
4. **Implementar** un dashboard web interactivo para visualizar incidentes priorizados, métricas del sistema y mapas de calor de riesgo en tiempo real.

---

## 3. Alcance
* Ingesta y preprocesamiento de logs estructurados (JSON / Syslog) en tiempo real o por lotes.
* Extracción de métricas comportamentales en ventanas temporales definidas.
* Inferencia analítica mediante un modelo Random Forest preentrenado.
* Asignación automatizada de puntaje de riesgo (*Risk Score* en escala de 0 a 100).
* Interfaz web interactiva (Dashboard) para la visualización de alertas y filtrado según nivel de criticidad.

---

## 4. Fuera de Alcance
* Módulos automatizados de respuesta directa ante incidentes (SOAR) como bloqueo automático de direcciones IP o aislamiento de hosts en el Firewall.
* Desarrollo de agentes recolectores de logs propietarios en endpoints (se asumirá recepción mediante API REST o archivos JSON cargados).
* Procesamiento de logs no estructurados o formatos propietarios sin especificación estándar.
* Despliegue en clusters con alta disponibilidad o arquitecturas multi-region en la nube.

---

## 5. Producto Mínimo Viable (MVP)
Un prototipo funcional capaz de recibir o cargar un conjunto de registros de autenticación en formato JSON, procesar sus características mediante un script de backend en Python, realizar la clasificación de la amenaza asignando un *Risk Score* mediante el modelo Random Forest, y mostrar las alertas resultantes ordenadas por criticidad en un dashboard web interactivo.
