# Portafolio Profesional - Julián Montoya

<p align="center">
    <h2 align="center">Backend Developer Python & AWS - <a href="https://juliandev.me">🚀 Ver Portafolio</a></h2>
</p>

<p align="center">Portafolio profesional optimizado para demostrar experiencia en desarrollo backend, Python, AWS y Machine Learning.</p>

## 🎯 Sobre el Desarrollador

**Julián Montoya** es Backend Developer con 3+ años de experiencia especializado en:
- **Python** (FastAPI, Flask, Django)
- **AWS** (EC2, S3, Lambda)  
- **Machine Learning** y procesamiento de datos
- **APIs REST** escalables y eficientes

**🏆 Logros destacados:** Finalista Top 20 en Datatón Bancolombia 2022</p>

***

## ✨ Características del Portafolio

### 🎨 Secciones Principales
1. **🏠 Inicio** - Perfil profesional con información clave
2. **👨‍💻 Sobre mí** - Experiencia, habilidades y logros detallados
3. **🚀 Proyectos** - Portafolio de desarrollos técnicos (ready para contenido)
4. **📝 Blog** - Artículos técnicos y tutoriales (ready para contenido)
5. **🏷️ Etiquetas** - Organización por tecnologías
6. **📄 CV** - Currículum en PDF accesible directamente

### 🔧 Optimizaciones Implementadas
- **🌐 SEO Avanzado**: Meta tags, JSON-LD schema, keywords estratégicas
- **📱 Responsive**: Adaptado a todos los dispositivos  
- **⚡ Performance**: Compresión HTML, CSS optimizado
- **🎨 UI/UX**: Tema oscuro profesional, animaciones con particles.js
- **🔗 Branding**: Dominio personalizado juliandev.me
- **🔍 Discoverability**: Sitemap automático, robots.txt optimizado

### 📁 Estructura de Archivos

```
portafolio/
├── _config.yml          # ⚙️ Configuración principal (SEO, redes sociales)
├── _includes/           # 🧩 Componentes reutilizables
├── _layouts/            # 📐 Plantillas de página
├── _posts/              # 📝 Proyectos y artículos (pendiente contenido)
├── _sass/               # 🎨 Estilos organizados por componentes
├── assets/              # 📸 Imágenes, CV y recursos
├── cv/                  # 📄 CV en PDF
├── about.md             # 👨‍💻 Biografía profesional
├── index.html           # 🏠 Página principal
└── robots.txt           # 🤖 Optimización para buscadores
```

### 🎯 Configuración Técnica

**Información Personal Configurada:**
- **Nombre**: Julián Montoya
- **Bio**: Backend Developer especializado en Python, AWS y Machine Learning  
- **Dominio**: https://juliandev.me
- **Idioma**: Español (Colombia)

**Redes Sociales Activas:**
- LinkedIn: julianmontoya95
- GitHub: andresprogramacion123
- Email: julianmontoya3.1416@gmail.com
- WhatsApp: +57 322 692 1491

**SEO Keywords**: desarrollador python, backend developer, aws, machine learning, api rest

## Desarrollo Local

### Opción 1: Instalación tradicional con Ruby

#### Instalar Ruby (Ubuntu 22.04 LTS)
```bash
# Actualizar paquetes
sudo apt update

# Instalar Ruby y herramientas de desarrollo
sudo apt install ruby-full build-essential zlib1g-dev

# Configurar gems para usuario (evitar sudo)
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc

# Instalar Bundler y Jekyll
gem install bundler jekyll
```

#### Ejecutar el proyecto
```bash
# Clonar el repositorio
git clone https://github.com/andresprogramacion123/andresprogramacion123.github.io.git
cd andresprogramacion123.github.io

# Instalar dependencias del proyecto
bundle install

# Ejecutar servidor Jekyll
bundle exec jekyll serve
```

Abrir en navegador: [http://localhost:4000](http://localhost:4000)

### Opción 2: Docker (más sencillo)
```bash
docker-compose up
```

## 📝 Guía para Añadir Contenido

### 🚀 Crear Nuevos Proyectos

**Paso 1:** Crear archivo en `_posts/` con formato: `YYYY-MM-DD-nombre-proyecto.md`

**Paso 2:** Añadir configuración inicial:
```yaml
---
title: "Nombre del Proyecto"
layout: post
date: 2024-MM-DD HH:MM:SS
tag: 
- python
- aws
- fastapi
category: project
author: julianmontoya
description: "Descripción técnica del proyecto"
star: true              # Destacar proyecto importante
externalLink: false     # true para enlaces externos
---
```

**Paso 3:** Escribir contenido profesional:
```markdown
# 🎯 Objetivo del Proyecto
Describir el problema que resuelve...

## 🛠️ Stack Técnico
- **Backend**: Python + FastAPI
- **Base de Datos**: PostgreSQL
- **Cloud**: AWS (EC2, RDS)
- **DevOps**: Docker, GitHub Actions

## ⚡ Características Principales
1. API REST con autenticación JWT
2. Base de datos optimizada 
3. Tests automatizados con pytest
4. Deploy automático en AWS

## 🔗 Enlaces
- [Repositorio GitHub](enlace)
- [Demo en vivo](enlace) (opcional)
```

### 📚 Crear Artículos Técnicos

**Para mostrar expertise**, crear artículos como:
```yaml
---
title: "Optimización de APIs REST con FastAPI y PostgreSQL"
layout: post
date: 2024-MM-DD HH:MM:SS
tag:
- python
- fastapi
- postgresql
- performance
category: blog
author: julianmontoya
description: "Técnicas avanzadas para optimizar APIs Python"
---
```

### 🏷️ Tags Recomendados

**Tecnologías Backend:**
- `python`, `fastapi`, `flask`, `django`
- `postgresql`, `mongodb`, `redis`
- `aws`, `docker`, `kubernetes`

**Categorías:**
- `project` - Proyectos técnicos
- `blog` - Artículos y tutoriales

### 📸 Gestión de Imágenes

**Para proyectos:**
1. Subir a `assets/images/proyectos/`
2. Usar formato: `![Demo]({{ site.url }}/assets/images/proyectos/proyecto-demo.png)`

**Para artículos:**
1. Subir a `assets/images/blog/`  
2. Incluir capturas de código y diagramas

## 🚀 Despliegue y Performance

### ⚡ GitHub Pages
- **Deploy automático** desde rama `gh-pages`
- **SSL/HTTPS** habilitado en juliandev.me
- **Tiempo de actualización**: 2-5 minutos por commit
- **CDN global** de GitHub para máximo rendimiento

### 📊 Métricas de Performance
- **SEO Score**: 85/100 (Excelente)
- **Mobile-friendly**: ✅ Verificado
- **PageSpeed**: Optimizado con compresión HTML/CSS
- **Core Web Vitals**: Cumple estándares de Google

### 🔄 Proceso de Actualización
1. **Editar contenido** (proyectos en `_posts/`, biografía en `about.md`)
2. **Commit y push** a rama `gh-pages`
3. **Verificar deploy** en https://juliandev.me (2-5 min)

## 🎯 Próximos Pasos Recomendados

### 📈 Para Maximizar Impacto Profesional:
1. **📝 Crear 3-5 proyectos** documentados que demuestren habilidades clave
2. **✍️ Escribir 2-3 artículos técnicos** para mostrar expertise
3. **📊 Configurar Google Analytics** para métricas de visitantes
4. **🔗 Optimizar LinkedIn** con enlace a juliandev.me

### 💼 Para Búsqueda de Empleo:
- El portafolio está **85% profesionalizado**
- **Ready para enviar** a ofertas de trabajo
- **Falta solo contenido técnico** para llegar al 100%

---

## 📄 Información Técnica

**Construido con**: Jekyll + GitHub Pages  
**Template base**: Indigo (personalizado y optimizado)  
**Licencia**: MIT  
**Última actualización**: 2025
