---
title: "🤖 Motor de Búsqueda de Emails"
layout: post
date: 2025-01-30
tag: 
- go
- vue3
- zincsearch
- docker
- fulltext-search
- concurrency
- vite
- tailwindcss
image: ../assets/images/EmailsZincSearch.png
headerImage: true
projects: true
hidden: false
description: "Sistema de búsqueda full-text sobre 517K correos con indexación concurrente en Go, motor ZincSearch y frontend Vue 3 + Vite 💪"
category: project
author: julianmontoya
externalLink: false
---

## Contexto

Motor de búsqueda full-text que indexa y permite buscar en el histórico completo del **dataset público Enron** (517,424 correos electrónicos).

Implementa búsqueda de alta performance con **resaltado de coincidencias**, indexación concurrente optimizada, y frontend responsive moderno.

🔗 **Demo en vivo:** [https://frontend.juliandeveloper.dev](https://frontend.juliandeveloper.dev)

---

## Stack Técnico

**Backend:**
- Go 1.20+ (API REST con concurrency nativa)
- Chi v5.0.8 (router HTTP minimalista)
- ZincSearch (motor de búsqueda full-text)

**Frontend:**
- Vue 3.2 + TypeScript + Composition API
- Vite 4.3 (build tool de próxima generación)
- Tailwind CSS 3.3 + Tailwind Forms
- Lucide Vue (iconografía)

**Infraestructura:**
- Docker + Docker Compose (orquestación multi-servicio)
- Traefik (proxy reverso con SSL automático)
- AWS EC2 (producción)

---

## Arquitectura del Sistema

### Arquitectura de 3 Capas

```
┌─────────────┐     ┌─────────────┐     ┌──────────────┐
│   Frontend  │─────▶│   API Go    │─────▶│  ZincSearch  │
│    Vue 3    │◀─────│  (Backend)  │◀─────│  (Search DB) │
└─────────────┘     └─────────────┘     └──────────────┘
     (SPA)          (REST /search)      (Full-text index)
```

### Componentes del Sistema

1. **Indexer (Go):** Herramienta CLI que procesa 517K correos y los indexa en ZincSearch
2. **API Backend (Go):** Servidor REST que expone endpoint de búsqueda
3. **Frontend (Vue 3):** SPA que consume la API y presenta resultados
4. **ZincSearch:** Motor de búsqueda ligero con índices invertidos

---

## Funcionalidades Principales

### 1. Indexación Masiva Concurrente

**Indexer CLI en Go** que procesa el dataset completo de Enron:

- **Lectura paralela** de archivos con `goroutines` + `sync.WaitGroup`
- **Procesamiento por lotes:** Agrupa 100 correos por request a ZincSearch API
- **Parsing de emails:** Usa el paquete `net/mail` estándar de Go
- **Limpieza de headers malformados:** Regex para sanitizar correos corruptos
- **Profiling de performance:** Genera archivos `.prof` (CPU y memoria) con `pprof`

**Métricas:**
- Indexa 517,424 correos en minutos (tiempo depende del hardware)
- Batch size optimizado (100 registros/request)
- Manejo de concurrencia con mutex para evitar race conditions

### 2. Búsqueda Full-Text con Highlight

**Endpoint POST `/search`:**

```json
// Request:
{
  "searchTerm": "energy trading"
}

// Response:
{
  "emails": [
    {
      "id": "...",
      "from": "jeff.skilling@enron.com",
      "to": "kenneth.lay@enron.com",
      "subject": "Q4 Energy Trading Results",
      "date": "2001-12-05",
      "content": "...",
      "highlight": "Summary of <strong>energy trading</strong> performance..."
    }
  ]
}
```

**Features técnicas:**

- **Match phrase query:** Búsqueda de frases exactas (no solo palabras sueltas)
- **Highlight automático:** Términos encontrados envueltos en `<strong>` tags
- **Límite de 200 resultados** por query
- **Búsqueda en campo "content"** (cuerpo del email)

### 3. Frontend Moderno y Responsive

**SPA Vue 3 con Composition API:**

- **TypeScript** para type safety
- **Tailwind CSS** para diseño utility-first responsive
- **Vite** como build tool (HMR ultra-rápido en desarrollo)
- **Lucide Vue** para iconografía consistente
- **Manejo de estados** de carga y errores

### 4. Profiling y Optimización

**Herramientas de análisis de rendimiento:**

```bash
go tool pprof cpu.prof    # Análisis de uso de CPU
go tool pprof mem.prof    # Análisis de memoria
```

- Perfiles generados automáticamente durante indexación
- Identificación de bottlenecks en procesamiento concurrente
- Optimización de garbage collection con liberación explícita (`batch = nil`)

---

## Highlights Técnicos

### Concurrencia con Goroutines

Procesamiento paralelo de archivos usando goroutines:

```go
var wg sync.WaitGroup
filepath.Walk("./maildir", func(path string, info os.FileInfo, err error) error {
    wg.Add(1)
    go func() {
        defer wg.Done()
        processFile(path)  // Procesa en paralelo
    }()
    return nil
})
wg.Wait()  // Espera a que todos terminen
```

**Ventajas:**

- Aprovecha múltiples cores de CPU
- Reducción significativa del tiempo de indexación
- Sincronización segura con mutex para acceso al slice compartido

### Batching para Eficiencia de Red

Agrupa registros antes de enviar a ZincSearch:

- **Batch size:** 100 correos por request HTTP
- **Reducción de latencia:** De 517K requests a ~5,174 requests
- **Endpoint bulk:** `/api/_bulkv2` de ZincSearch
- **Liberación de memoria:** `batch = nil` después de cada envío

### Búsqueda Optimizada con ZincSearch

ZincSearch es un motor de búsqueda ligero (alternativa a Elasticsearch):

- Índices invertidos para búsqueda O(1)
- Menor footprint de memoria vs Elasticsearch
- API REST simple compatible con búsquedas complejas
- Highlight automático de términos encontrados

### Clean Architecture en Go

Separación clara de responsabilidades:

```
server/
├── main.go          # Entry point
├── controllers/     # HTTP handlers (routes, search)
├── models/          # Data layer (emails)
└── utils/           # Helpers (JSON writer)
```

- **Chi router:** Middlewares para logging, CORS, panic recovery
- **Inyección de dependencias:** Fácil testing y modularidad
- **Standard library:** Usa paquetes nativos de Go (`net/mail`, `net/http`)

---

## Desafíos Técnicos Resueltos

1. **Parsing de Emails Corruptos:** Dataset Enron contiene headers malformados que rompen el parser estándar `net/mail`. **Solución:** Regex de limpieza previa (`cleanMalformedHeaders()`)

2. **Race Conditions en Concurrencia:** Múltiples goroutines escribiendo al mismo slice. **Solución:** `sync.Mutex` para sincronización segura

3. **Optimización de Memoria:** Indexación de 517K correos consumía GB de RAM. **Solución:** Procesamiento por lotes + liberación explícita de memoria

4. **CORS para SPA:** Frontend en dominio diferente al backend. **Solución:** Middleware CORS de Chi con configuración permisiva en desarrollo

5. **Highlight de Resultados:** Resaltar términos buscados en el contenido. **Solución:** Configuración de ZincSearch query con parámetros de highlight (`<strong>` tags)

---

## Infraestructura y DevOps

### Docker Compose Multi-Servicio

Orquestación de 3 servicios:

```yaml
services:
  zincsearch:    # Motor de búsqueda (puerto 4080)
  backend:       # API Go (puerto 8080)
  frontend:      # Vue 3 SPA (puerto 5173 dev / 80 prod)
```

**Volúmenes persistentes:**

- `./data:/data` → Almacena índices de ZincSearch

### Despliegue en AWS EC2

**Configuración de producción:**

- **Traefik** como proxy reverso
- **SSL/HTTPS** automático con Let's Encrypt
- **Backup** con rsync para replicar datos entre servidores
- **Variables de entorno** para credenciales (`ZINC_USER`, `ZINC_PASSWORD`, `HOST`)

### Script de Descarga Automática

`download_data.sh` descarga el dataset completo de Enron:

```bash
./indexer/download_data.sh  # Descarga y descomprime 517K correos
```

---

## Impacto y Métricas

| Métrica | Valor |
|---------|-------|
| Dataset procesado | 517,424 correos electrónicos del caso Enron |
| Performance | Búsquedas full-text en <100ms (promedio) |
| Frontend moderno | SPA con HMR en <50ms (Vite) |
| Profiling completo | CPU y memoria analizados con pprof |
| Producción | Desplegado en AWS con HTTPS y alta disponibilidad |

---

## Repositorio

🔗 **GitHub:** [https://github.com/andresprogramacion123/emails_zincsearch](https://github.com/andresprogramacion123/emails_zincsearch)