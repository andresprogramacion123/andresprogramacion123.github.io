# Análisis del Proyecto - Portafolio Jekyll

## Descripción General

Este es un proyecto de portafolio personal desarrollado para **Julián Andrés Montoya**, un desarrollador de software con más de 3 años de experiencia especializado en backend. El sitio está basado en el template **Indigo**, un tema minimalista para Jekyll desarrollado por Sérgio Kopplin.

## Características del Proyecto

### Tecnologías Utilizadas
- **Jekyll** - Generador de sitios estáticos
- **Sass/SCSS** - Preprocesador CSS con arquitectura RSCSS
- **GitHub Pages** - Hosting y despliegue automático
- **Ruby Gems** - Gestión de dependencias

### Estructura de Navegación
El sitio incluye las siguientes secciones principales:
1. **Home** (`index.html`) - Página principal con información básica
2. **About** (`about.md`) - Biografía profesional detallada
3. **Projects** (`projects.html`) - Portafolio de proyectos
4. **Blog** (`blog.html`) - Artículos y posts técnicos
5. **Tags** (`tags.html`) - Organización por etiquetas

### Funcionalidades Implementadas
- **Tema oscuro** por defecto (`dark-theme: true`)
- **CV integrado** con enlace externo a Google Drive
- **Redes sociales** configuradas (WhatsApp, LinkedIn, GitHub, Email)
- **Sistema de comentarios** con Disqus
- **SEO optimizado** con jekyll-seo-tag
- **Tiempo de lectura** para posts
- **Posts relacionados**
- **Análíticas** preparadas para Google Analytics
- **Animaciones CSS**

### Configuración del Sitio

#### Información Personal
- **Nombre:** Julián Andrés Montoya
- **Profesión:** Desarrollador de Software
- **URL:** https://andresprogramacion123.github.io
- **Imagen de perfil:** `assets/images/FondoBlanco.png`

#### Características Habilitadas
```yaml
projects: true
about: true
blog: true
read-time: true
show-tags: true
related: true
show-author: true
animation: true
```

## Contenido Actual

### Página About
Incluye información profesional completa:
- **Experiencia laboral** (2016-2024)
- **Habilidades técnicas** (Python, PHP, Node.js, AWS, etc.)
- **Reconocimientos** (Datatón Bancolombia 2022)
- **Publicaciones** (Manual GUMELAB)
- **Hobbies personales** (Trekking, familia)

### Assets e Imágenes
El proyecto incluye:
- Favicon completo para múltiples dispositivos
- Imágenes de proyectos (BancolombiaDataton.png, Gumelab.png)
- Fotos personales (perfil, familia, trekking)
- Configuración de particles.js para efectos visuales

## Estado del Despliegue

El sitio está:
- ✅ **Desplegado** en GitHub Pages
- ✅ **Accesible** públicamente en internet
- ✅ **Configurado** para despliegue automático desde branch `gh-pages`

## Arquitectura Jekyll

### Layouts Disponibles
- `default.html` - Layout base
- `page.html` - Para páginas estáticas
- `post.html` - Para artículos y proyectos
- `compress.html` - Optimización HTML

### Sistema de Includes
- `header.html`, `footer.html`, `nav.html` - Estructura básica
- `author.html` - Información del autor
- `blog-post.html` - Formato de posts del blog
- `social-links.html` - Enlaces sociales
- `analytics-google.html` - Google Analytics

### Organización SCSS
```
_sass/
├── base/ (variables, normalize, syntax highlighting)
├── components/ (header, footer, nav, author, etc.)
└── pages/ (estilos específicos por página)
```

## Observaciones de Desarrollo

1. **Posts vacíos**: Actualmente no hay contenido en `_posts/`, por lo que las secciones de Blog y Projects muestran mensajes de "ningún contenido publicado"

2. **Template base**: El proyecto mantiene la estructura original del tema Indigo con personalizaciones específicas para el perfil profesional

3. **Optimización**: Configurado para compresión HTML y optimización de assets

4. **Internacionalización**: Todo el contenido está en español, adaptado al mercado latinoamericano

Este proyecto representa un portafolio profesional completo y funcional, listo para mostrar proyectos y artículos técnicos del desarrollador.