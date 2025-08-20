# Portafolio Personal - Julián Andrés Montoya

<p align="center">
    <h2 align="center">Desarrollador de Software - <a href="https://andresprogramacion123.github.io">Ver sitio</a></h2>
</p>

<p align="center">Portafolio profesional y blog técnico desarrollado con Jekyll usando el template Indigo.</p>

***

## Estructura del Proyecto

Este sitio está organizado en las siguientes secciones principales:

### 📁 Estructura de Directorios

```
/
├── _config.yml          # Configuración principal del sitio
├── _includes/           # Componentes reutilizables (header, footer, nav)
├── _layouts/            # Plantillas de página (default, post, page)
├── _posts/              # Artículos del blog y proyectos
├── _sass/               # Estilos SCSS organizados por componentes
├── assets/              # Imágenes, archivos estáticos y configuraciones
├── about.md             # Página "Sobre mí"
├── blog.html            # Página del blog
├── projects.html        # Página de proyectos
├── index.html           # Página principal
└── tags.html            # Página de etiquetas
```

### 🎨 Secciones del Sitio

1. **Home (`index.html`)** - Página principal con introducción
2. **About (`about.md`)** - Biografía profesional, experiencia y habilidades
3. **Projects (`projects.html`)** - Portafolio de proyectos técnicos
4. **Blog (`blog.html`)** - Artículos técnicos y tutoriales
5. **Tags (`tags.html`)** - Organización de contenido por etiquetas

### ⚙️ Configuración Principal

El archivo `_config.yml` contiene la configuración del sitio:

- **Información personal**: nombre, bio, imagen de perfil
- **Redes sociales**: enlaces a GitHub, LinkedIn, WhatsApp, email
- **Funcionalidades**: comentarios, SEO, tiempo de lectura, tags
- **Tema**: configurado en modo oscuro por defecto
- **CV**: enlace externo a Google Drive

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

## Cómo Añadir Contenido

### ➕ Agregar Nuevos Proyectos

Para añadir un proyecto al portafolio:

1. **Crear archivo** en `_posts/` con formato: `YYYY-MM-DD-nombre-proyecto.md`

2. **Añadir Front Matter** al inicio del archivo:
```yaml
---
title: "Nombre del Proyecto"
layout: post
date: YYYY-MM-DD HH:MM:SS
tag: 
- tecnologia1
- tecnologia2
- tecnologia3
category: project
author: jamesfoster
description: "Descripción breve del proyecto"
externalLink: false  # true si es un enlace externo
star: true          # true para destacar el proyecto
---
```

3. **Escribir contenido** en Markdown debajo del Front Matter

4. **Ejemplo de archivo de proyecto**:
```markdown
---
title: "Sistema de Gestión de Inventarios"
layout: post
date: 2024-01-15 09:00:00
tag:
- python
- flask
- mysql
- aws
category: project
author: jamesfoster
description: "API REST para gestión de inventarios con integración a AWS"
star: true
---

# Descripción del Proyecto

Contenido del proyecto en Markdown...

## Tecnologías Utilizadas
- Python
- Flask
- MySQL
- AWS EC2/S3

## Características
- API REST completa
- Autenticación JWT
- Base de datos optimizada
```

### 📝 Agregar Artículos al Blog

Para añadir un artículo al blog:

1. **Crear archivo** en `_posts/` con formato: `YYYY-MM-DD-titulo-articulo.md`

2. **Añadir Front Matter**:
```yaml
---
title: "Título del Artículo"
layout: post
date: YYYY-MM-DD HH:MM:SS
tag:
- tutorial
- programacion
- backend
category: blog
author: jamesfoster
description: "Descripción del artículo"
---
```

3. **Ejemplo de artículo**:
```markdown
---
title: "Guía de APIs REST con FastAPI"
layout: post
date: 2024-02-01 10:00:00
tag:
- python
- fastapi
- tutorial
- api
category: blog
author: jamesfoster
description: "Tutorial completo para crear APIs REST con FastAPI"
---

# Introducción

En este tutorial aprenderemos a crear APIs REST...

## Configuración Inicial
...
```

### 🏷️ Sistema de Etiquetas

- Usar etiquetas consistentes para facilitar la navegación
- Ejemplos de etiquetas recomendadas:
  - **Tecnologías**: `python`, `javascript`, `aws`, `docker`
  - **Tipos**: `tutorial`, `proyecto`, `guia`, `tips`
  - **Áreas**: `backend`, `frontend`, `devops`, `ia`

### 📸 Añadir Imágenes

1. **Subir imágenes** a `assets/images/`
2. **Referenciar en Markdown**:
```markdown
![Descripción]({{ site.url }}/assets/images/nombre-imagen.png)
```

### 🔗 Enlaces Externos vs Internos

- **Proyecto interno**: `externalLink: false` (contenido en el sitio)
- **Proyecto externo**: `externalLink: true` + URL en el contenido

## Despliegue

El sitio se despliega automáticamente en **GitHub Pages** desde la rama `gh-pages`. Cualquier commit a esta rama actualizará el sitio en https://andresprogramacion123.github.io

### Proceso de Despliegue
1. Hacer push a la rama `gh-pages`
2. GitHub Pages compilará automáticamente el sitio Jekyll
3. El sitio estará disponible en pocos minutos

---

**Basado en**: [Indigo Template](https://github.com/sergiokopplin/indigo) por Sérgio Kopplin  
**Licencia**: [MIT](https://kopplin.mit-license.org/)
