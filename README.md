# kafka-client-events-stream-learning
# MuleSoft Smart Client Profile Gateway – PoC

## 📌 Descripción

Este repositorio contiene un **Proof of Concept (PoC) de aprendizaje** para entender cómo se utiliza **MuleSoft como capa de integración y orquestación**, y no como un microservicio tradicional.

El proyecto expone una **API unificada de perfil de cliente** que compone información procedente de varios sistemas externos simulados, devolviendo una vista única y orientada al consumidor.

---

## 🎯 Objetivos del proyecto

- Comprender el rol de MuleSoft en arquitecturas enterprise
- Aprender conceptos básicos:
  - Flows
  - HTTP Listener
  - HTTP Request
  - DataWeave
  - Orquestación de servicios
- Aplicar principios de **API‑led connectivity**
- Construir un PoC pequeño, realista y explicable

---

## 💡 Idea central

Este proyecto implementa un **Smart Client Profile Gateway**:

- Ningún sistema tiene la información completa del cliente
- MuleSoft construye el perfil **en tiempo de petición**
- La respuesta está pensada para consumo, no para reflejar modelos internos

---

## 🏗️ Arquitectura General

```mermaid
flowchart LR
    A[Cliente API]
    B[MuleSoft<br/>Experience API]
    C[API Cliente Core]
    D[API Riesgo / Segmentación]
    E[DataWeave<br/>Transformación]
    F[Perfil Unificado<br/>Cliente]

    A -->|GET /client-profile/{id}| B
    B --> C
    B --> D
    C --> B
    D --> B
    B --> E
    E --> F
