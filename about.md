---
title: Sobre mí
layout: page
slug: about
---

<div class="about-profile-section" markdown="1">
![Profile Image]({% if site.external-image %}{{ site.picture }}{% else %}{{ site.url }}/{{ site.picture }}{% endif %})
</div>

<div class="about-intro-section" markdown="1">
Soy desarrollador de software con más de 3 años de experiencia en el diseño e implementación de soluciones tecnológicas enfocadas en backend. Mi trayectoria abarca sectores académicos y corporativos, donde he creado sistemas robustos, desde APIs REST eficientes hasta algoritmos avanzados de IA y machine learning.

Destaco por mi capacidad para diseñar bases de datos relacionales y no relacionales, optimizando la gestión de información y asegurando la escalabilidad de las aplicaciones. He trabajado en proyectos que integran servicios en la nube de AWS, logrando implementaciones ágiles y efectivas. Mis logros incluyen la creación de aplicaciones web y el desarrollo de algoritmos de machine learning para Procesamiento de Lenguaje Natural (NLP), destacándome en retos como el Datatón Bancolombia 2022.

Tengo un fuerte compromiso con el aprendizaje continuo y la innovación. Además, aplico metodologías ágiles como Scrum para asegurar una gestión eficiente de proyectos. Mis objetivos profesionales incluyen contribuir al desarrollo de soluciones backend que transformen procesos y generen valor.
</div>

<div class="about-experience-section">
<h2>Trayectoria profesional</h2>
{% include experience-timeline.html %}
</div>

<div class="about-skills-section">
<h2>Habilidades Técnicas y Herramientas</h2>
{% include skills-grid.html %}
</div>

<div class="about-awards-section">
<h2>Reconocimientos y premios 👏🎉</h2>
{% include awards-grid.html %}
</div>

<div class="about-publications-section">
<h2>Colaboracion en publicaciones 📚🧠</h2>
{% include publications-grid.html %}
</div>


<div class="about-soft-skills-section">
<h2>Skills 😎</h2>
{% include soft-skills-grid.html %}
</div>


