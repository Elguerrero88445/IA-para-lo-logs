# Sistema SIEM de Nueva Generación con Machine Learning

**Detección y priorización automatizada de amenazas en tiempo real mediante Random Forest Classifier**

![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-Random%20Forest-orange?logo=scikitlearn&logoColor=white)
![FastAPI](https://img.shields.io/badge/Backend-FastAPI-009688?logo=fastapi&logoColor=white)
![React](https://img.shields.io/badge/Frontend-React-61DAFB?logo=react&logoColor=black)
![OpenSearch](https://img.shields.io/badge/Storage-OpenSearch-005EB8?logo=opensearch&logoColor=white)
![Status](https://img.shields.io/badge/Estado-En%20desarrollo-yellow)

---

## Tabla de contenidos

- [Resumen](#-resumen)
- [1. Problema](#1-problema)
- [2. Objetivos](#2-objetivos)
- [3. Alcance](#3-alcance)
- [4. Fuera de alcance](#4-fuera-de-alcance)
- [5. Producto Mínimo Viable (MVP)](#5-producto-mínimo-viable-mvp)
- [Arquitectura del pipeline](#-arquitectura-del-pipeline)
- [Stack tecnológico](#-stack-tecnológico)
- [Referencias](#-referencias)

---

## Resumen

Este proyecto propone el desarrollo de un **módulo especializado para un sistema SIEM** (Security Information and Event Management), respaldado por un algoritmo de aprendizaje automático supervisado: **Random Forest Classifier**. El módulo procesa logs de autenticación y red en tiempo real, extrae características comportamentales de usuarios y entidades (UEBA) y asigna un **puntaje de riesgo (Risk Score)** para automatizar el triage de incidentes, reduciendo la fatiga de alertas en los equipos de un SOC (Security Operations Center).

---

## 1. Problema

Los equipos de un **Centro de Operaciones de Seguridad (SOC)** sufren de una agobiante **fatiga de alertas** (*alert fatigue*): procesan diariamente miles de eventos de seguridad, de los cuales hasta un **80% son falsos positivos** o actividad benigna generada por los sistemas SIEM tradicionales basados en reglas estáticas.

Esto ocurre porque los SIEM convencionales dependen de firmas y umbrales fijos (p. ej. *"alertar si ocurren más de N intentos fallidos en T segundos"*), lo cual los vuelve estructuralmente incapaces de detectar ataques de día cero y variaciones sutiles de un patrón de ataque.

**Consecuencia:** ciberataques reales y sigilosos —movimientos laterales, exfiltración paulatina de datos, fuerza bruta distribuida— pasan desapercibidos en medio del ruido digital, derivando en filtraciones de información sensible, interrupción de operaciones y pérdidas económicas significativas, especialmente en PyMEs que no cuentan con personal especializado suficiente para auditar manualmente millones de registros.

---

## 2. Objetivos

### Objetivo general

Desarrollar un módulo SIEM impulsado por Machine Learning mediante el algoritmo **Random Forest Classifier** para la detección, correlación y priorización automatizada de amenazas de seguridad en tiempo real.

### Objetivos específicos

1. **Diseñar e implementar** un pipeline de ingestión y normalización de datos capaz de procesar eventos de autenticación (Active Directory / Sysmon) y tráfico de red (Syslog / JSON).
2. **Desarrollar** un componente de ingeniería de características (*Feature Engineering*) que transforme logs crudos en vectores numéricos comportamentales dentro de ventanas temporales definibles.
3. **Entrenar, optimizar y evaluar** el modelo Random Forest Classifier utilizando conjuntos de datos de ciberseguridad reconocidos (CSE-CIC-IDS2018 / Kaggle), alcanzando un **F1-Score superior al 92%**.
4. **Construir** un dashboard web interactivo para visualizar incidentes priorizados, líneas de tiempo de eventos y mapas de calor de riesgo en tiempo real.

---

## 3. Alcance

El proyecto contempla:

- ✅ Ingesta y preprocesamiento de logs estructurados (JSON / Syslog), en tiempo real o por lotes.
- ✅ Extracción de métricas comportamentales (UEBA) dentro de ventanas temporales definidas.
- ✅ Inferencia analítica mediante un modelo Random Forest previamente entrenado.
- ✅ Asignación automatizada de un **puntaje de riesgo (Risk Score)** en escala de 0 a 100.
- ✅ Indexación de eventos y alertas en OpenSearch / Elasticsearch.
- ✅ Interfaz web interactiva (dashboard) para visualización y filtrado de alertas por nivel de criticidad.

---

## 4. Fuera de alcance

Explícitamente **no** forman parte de este proyecto:

- ❌ Módulos automatizados de respuesta ante incidentes (SOAR) — p. ej. bloqueo automático de IPs o aislamiento de hosts en el firewall.
- ❌ Desarrollo de agentes recolectores de logs propietarios para endpoints (se asume la recepción vía API REST o archivos JSON cargados).
- ❌ Procesamiento de logs no estructurados o en formatos propietarios sin especificación estándar.
- ❌ Despliegue en clústeres de alta disponibilidad o arquitecturas multi-región en la nube.

---

## 5. Producto Mínimo Viable (MVP)

El MVP consiste en un **prototipo funcional** capaz de:

1. Recibir o cargar un conjunto de registros de autenticación en formato JSON.
2. Procesar sus características mediante un script de backend en Python (*feature engineering*).
3. Clasificar la amenaza y asignar un **Risk Score** mediante el modelo Random Forest ya entrenado.
4. Mostrar las alertas resultantes, ordenadas por criticidad, en un **dashboard web interactivo**.

---

## 🔄 Arquitectura del pipeline

```
1. Ingesta de Logs  →  2. Feature Engineering  →  3. Inferencia ML  →  4. Indexación  →  5. Dashboard SOC
   (Syslog / JSON)      (extracción de métricas)    (Random Forest)     (OpenSearch)      (alertas y triage)
```

---

## 🛠 Stack tecnológico

| Capa | Tecnología |
|---|---|
| Procesamiento de datos y ML | Python (pandas, numpy, scikit-learn) |
| Motor de inferencia | `RandomForestClassifier` (scikit-learn) con persistencia en Joblib |
| Almacenamiento e indexación | OpenSearch / Elasticsearch |
| Backend / API REST | FastAPI (Python) |
| Frontend / Dashboard | React.js + TailwindCSS |

---

## 📚 Referencias

1. I. Sharafaldin, A. H. Lashkari, and A. A. Ghorbani, "Toward Generating a Dataset for Security Analysis to Support Machine Learning Applications," *ICISSP*, Funchal, Madeira, Portugal, 2018, pp. 108–116.
2. L. Breiman, "Random Forests," *Machine Learning*, vol. 45, no. 1, pp. 5–32, Oct. 2001.
3. A. L. Buczak and E. Guven, "A Survey of Data Mining and Machine Learning Methods for Cyber Security Intrusion Detection," *IEEE Communications Surveys & Tutorials*, vol. 18, no. 2, pp. 1153–1176, 2016.
4. Elastic, "What is SIEM? Security Information and Event Management guide," *Elastic Security Labs*, 2026.
