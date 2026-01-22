---
title: "🚀 Plataforma de programación académica"
layout: post
date: 2024-10-30
tag: 
- python
- fastapi
- postgresql
- sqlalchemy
- docker
- jwt
- alembic
- async
image: ../assets/images/ProgramacionAcademica.png
headerImage: true
projects: true
hidden: false
description: "API asíncrona con FastAPI para gestión de planes de estudio, syllabus y documentación académica oficial con exportación PDF/Word 💪"
category: project
author: julianmontoya
externalLink: false
---

## Contexto

Sistema backend desarrollado para la **Facultad de Medicina - Universidad de Antioquia** que digitaliza y centraliza la gestión de programación académica: planes de estudio, syllabus de cursos, y documentación curricular oficial.

Reemplaza procesos manuales de documentación académica por un **sistema estructurado con flujo de aprobación de cambios**, **generación automática de documentos oficiales** en PDF/Word, y **control de versiones** de planes curriculares.

---

## Stack Técnico

- **Backend:** Python 3.10 + FastAPI 0.104 (async/await)
- **Servidor ASGI:** Uvicorn (alta concurrencia)
- **Base de Datos:** PostgreSQL 14 + SQLAlchemy + SQLModel
- **Autenticación:** JWT (python-jose) + bcrypt + OAuth2
- **Templates:** Jinja2 (server-side rendering)
- **Documentos:** WeasyPrint (PDF) + python-docx (Word)
- **Migraciones:** Alembic (versionamiento de BD)
- **Testing:** pytest
- **DevOps:** Docker Compose + Traefik (proxy reverso con SSL automático)

---

## Arquitectura y Patrones

### Clean Architecture - Separación en Capas

Arquitectura de 5 capas con separación clara de responsabilidades:


Request → Router → Schema (validación) → Service → CRUD → Model → PostgreSQL


| Capa          | Ubicación   | Responsabilidad                          |
|---------------|-------------|------------------------------------------|
| Presentación  | `routers/`  | Endpoints HTTP REST                      |
| Validación    | `schemas/`  | Pydantic models (type-safe)              |
| Negocio       | `services/` | Lógica de negocio y reglas académicas    |
| Acceso Datos  | `crud/`     | Operaciones CRUD reutilizables           |
| Persistencia  | `models/`   | Modelos SQLModel/SQLAlchemy              |

### Type Safety Completo

Uso exhaustivo de **Python type hints** en todas las capas, aprovechando Pydantic para validación automática de datos de entrada/salida.

---

## Funcionalidades Principales

### 1. Gestión Jerárquica de Programas Académicos

Modelo de datos académico completo:

Programa Académico (Medicina, Enfermería, etc.)
└── Plan de Estudio (versión curricular 2020, 2023, etc.)
└── Curso
└── Programa de Curso (Syllabus)
├── Información General
├── Información Específica
├── Metodología
└── Profesores


Control de versiones de planes curriculares con historial completo.

### 2. Sistema de Syllabus Completo

Diseño de programas de curso (syllabus) con 4 componentes estructurados:

- **Información General:** Datos básicos, créditos, horas teóricas/prácticas (cálculo automático)
- **Información Específica:** Objetivos de aprendizaje, competencias, contenidos temáticos
- **Metodología:** Estrategias pedagógicas, evaluación, recursos bibliográficos
- **Profesores:** Asignación de docentes con perfiles académicos

### 3. Workflow de Solicitudes de Cambio

Sistema de aprobación para modificaciones a syllabus existentes:

- Solicitud de cambio por componente (general/específico/metodología/profesores)
- Flujo de aprobación según jerarquía organizacional
- Historial auditable de cambios con usuario y timestamp
- Notificaciones por email en cada transición de estado

### 4. Generación de Documentación Oficial

**PDFs dinámicos:**
- Syllabus completos con formato institucional oficial
- Generación desde templates HTML/CSS con WeasyPrint
- Logos, encabezados y pie de página institucionales
- Exportación lista para impresión

**Documentos Word:**
- Formatos editables con python-docx
- Tablas estructuradas con contenidos temáticos
- Imágenes y formato institucional

### 5. Control de Acceso por Roles

Sistema RBAC con **10 roles institucionales**:
- Administrador
- Gestor académico
- Decano / Vicedecano
- Coordinador de programa / pregrado / curso / flexibles
- Jefe de educación médica / oficina posgrados

Autorización granular: usuarios solo ven/editan programas de su ámbito de responsabilidad.

---

## Highlights Técnicos

### Asincronía con FastAPI

API completamente **asíncrona (async/await)** para máximo rendimiento:
- Operaciones de BD no bloqueantes
- Concurrencia alta con Uvicorn
- Mejor uso de recursos en operaciones I/O intensivas (generación PDFs, emails)

### Validación Automática con Pydantic

Todos los requests/responses validados con **Pydantic schemas**:
- Type checking en tiempo de ejecución
- Validación automática de datos de entrada
- Documentación OpenAPI generada automáticamente
- Coerción de tipos y mensajes de error descriptivos

### Migraciones con Alembic

Control de versiones de base de datos:
- Migraciones versionadas y reversibles
- Historial completo de cambios de esquema
- Despliegues consistentes entre ambientes

### Templates Server-Side con Jinja2

Renderizado híbrido (API + Web):
- Endpoints REST para frontend desacoplado
- Vistas HTML renderizadas server-side para admin
- Templates reutilizables para PDFs y emails

### Docker con Traefik + HTTPS Automático

Infraestructura lista para producción:
- **3 servicios:** PostgreSQL + pgAdmin + FastAPI
- **Traefik** como proxy reverso
- **SSL/HTTPS automático** con Let's Encrypt
- Configuración multi-ambiente (dev/test/prod)

### Testing Automatizado

Suite de tests con **pytest**:
- Tests unitarios por capa (CRUD, services)
- Tests de integración de endpoints
- Fixtures para datos de prueba

---

## Desafíos Técnicos Resueltos

1. **Modelo Académico Complejo:** Diseño de esquema relacional que modela correctamente la jerarquía Programa → Plan → Curso → Syllabus, manteniendo integridad referencial y permitiendo versiones múltiples

2. **Generación de PDFs con Calidad Profesional:** Implementación de WeasyPrint para convertir HTML/CSS en PDFs con formato institucional, preservando tablas complejas, imágenes y estilos

3. **Cálculo Automático de Créditos Académicos:** Lógica para calcular automáticamente créditos según normativa colombiana (horas teóricas, prácticas, trabajo independiente)

4. **Autorización Jerárquica:** Sistema de permisos que combina roles con estructura organizacional (Facultad → Programa → Curso) para controlar acceso granular

5. **Workflow de Aprobaciones:** Máquina de estados para gestionar el ciclo de vida de solicitudes de cambio con notificaciones automáticas según rol del aprobador

---

## Impacto

- **Centralización** de información curricular de ~50 programas académicos
- **Estandarización** de formatos de syllabus según lineamientos institucionales
- **Automatización** de generación de documentos oficiales (antes manuales en Word)
- **Trazabilidad** completa de cambios curriculares con historial auditable
- **Reducción de tiempos** de documentación de semanas a días

---

## Documentación Técnica

- **OpenAPI/Swagger** generado automáticamente por FastAPI
- **167 endpoints** documentados con ejemplos de request/response
- **62 dependencias** Python gestionadas con requirements.txt
- **18 módulos** organizados por dominio académico

---

## Código

🔒 Proyecto privado institucional - Universidad de Antioquia

---
