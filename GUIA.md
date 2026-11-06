# 📖 Guía: Cómo escribir artículos en el blog

Esta guía te explica cómo crear y publicar nuevos artículos en tu blog MKDocs.

## 📁 Estructura de directorios

Los artículos están organizados por categoría:

```
docs/
├── backend/          # Artículos sobre backend
├── frontend/         # Artículos sobre frontend
├── devops/           # Artículos sobre DevOps
├── tutoriales/       # Tutoriales paso a paso
└── otro/             # Otros temas
```

## ✍️ Crear un nuevo artículo

### Paso 1: Elegir la categoría

Decide en qué categoría encaja tu artículo:

- **Backend**: APIs, bases de datos, arquitectura de servidor
- **Frontend**: HTML, CSS, JavaScript, React, Vue, Angular
- **DevOps**: Docker, Kubernetes, CI/CD, infraestructura
- **Tutoriales**: Guías paso a paso sobre cualquier tema
- **Otro**: Temas que no encajen en las otras categorías

### Paso 2: Crear el archivo markdown

Crea un nuevo archivo `.md` en la carpeta correspondiente:

```bash
# Ejemplo: crear artículo sobre Node.js en backend
touch docs/backend/nodejs-guia-completa.md
```

**Reglas de nombre de archivo:**
- Usa minúsculas
- Usa guiones `-` para separar palabras
- Extensión `.md`
- Ejemplos válidos: `guia-react.md`, `docker-basico.md`, `api-rest.md`

### Paso 3: Escribir el contenido

Usa esta estructura de plantilla como base:

```markdown
# Título del artículo

Una línea de resumen que explique de qué trata.

## 📌 Resumen

- **Dificultad**: Principiante / Intermedio / Avanzado
- **Tiempo de lectura**: XX minutos
- **Última actualización**: 2024

## Introducción

Explica qué aprenderá el lector y por qué es importante.
Introduce el problema que vas a resolver.

## Conceptos básicos

Explica los conceptos fundamentales que necesita conocer.

## Desarrollo principal

Desarrolla tu tema en secciones claras con subsecciones.

### Subsección importante
Contenido aquí...

## Ejemplos prácticos

Incluye ejemplos de código reales y funcionales.

\`\`\`python
# Código de ejemplo
def saludar():
    print("¡Hola!")
\`\`\`

## Conclusión

Resumen breve de los puntos clave.

---

**Recursos adicionales:**
- [Enlace 1](https://ejemplo.com)
- [Enlace 2](https://ejemplo.com)
```

## 📝 Mejores prácticas de escritura

### Encabezados

Usa una jerarquía clara de encabezados:

```markdown
# Título principal (solo uno por artículo)

## Secciones principales

### Subsecciones

#### Subsecciones menores (usar con moderación)
```

### Código

Usa bloques de código resaltados con el lenguaje:

````markdown
```python
# Python
def ejemplo():
    return "código"
```

```javascript
// JavaScript
function ejemplo() {
    return "código";
}
```

```bash
# Bash/Shell
echo "Ejemplo"
```
````

**Lenguajes soportados:** python, javascript, bash, java, go, rust, cpp, sql, html, css, xml, yaml, json, markdown, y más.

### Énfasis

```markdown
**Texto en negrita** para lo importante
*Texto en itálica* para énfasis suave
`código inline` para código dentro del texto
```

### Listas

```markdown
# Lista sin orden
- Item 1
- Item 2
  - Subitem 2.1
  - Subitem 2.2
- Item 3

# Lista ordenada
1. Primero
2. Segundo
   1. Subsegundo
   2. Subitem
3. Tercero
```

### Cajas de información

```markdown
!!! tip "Consejo"
    Este es un consejo útil

!!! warning "Advertencia"
    Algo importante que debes saber

!!! danger "Peligro"
    Algo crítico que no debes hacer

!!! success "Éxito"
    Un resultado positivo

!!! info "Información"
    Información general
```

### Enlaces

```markdown
# Enlaces internos a otros artículos
[Ver artículo de Python](../backend/ejemplo-python.md)

# Enlaces externos
[Documentación oficial](https://docs.python.org)
```

### Imágenes

```markdown
# Mostrar una imagen
![Descripción de la imagen](../assets/images/mi-imagen.png)

# Imagen con enlace
[![Descripción](../assets/images/mi-imagen.png)](https://enlace.com)
```

Guarda las imágenes en `docs/assets/images/`

### Tablas

```markdown
| Encabezado 1 | Encabezado 2 | Encabezado 3 |
|--------------|--------------|--------------|
| Dato 1       | Dato 2       | Dato 3       |
| Dato 4       | Dato 5       | Dato 6       |
```

### Citas

```markdown
> Esta es una cita importante

> Puedes usar múltiples líneas
> en una cita
```

## 🔄 Actualizar la navegación

Si crear un artículo nuevo, actualiza `mkdocs.yml` para agregarlo a la navegación:

```yaml
nav:
  - Inicio: index.md
  - Backend:
      - Python: backend/ejemplo-python.md
      - Node.js: backend/nodejs-guia-completa.md  # ← Nuevo
  - Frontend:
      - React: frontend/ejemplo-react.md
  # ... más categorías
```

**Nota:** Los artículos de ejemplo ya están en la navegación. Puedes dejarlos o eliminarlos cuando agregues los tuyos.

## 🚀 Vista previa local

Antes de publicar, visualiza tu artículo localmente:

```bash
# Instala dependencias (si no lo has hecho)
pip install -r requirements.txt

# Sirve el sitio localmente
mkdocs serve
```

Abre `http://localhost:8000` en tu navegador y verifica que tu artículo se ve correctamente.

## 🔍 Checklist antes de publicar

Antes de hacer commit a tu artículo, verifica:

- [ ] **Título claro**: El título es descriptivo y atractivo
- [ ] **Estructura**: Tiene resumen, introducción, desarrollo y conclusión
- [ ] **Ortografía**: Sin errores de tipografía
- [ ] **Código**: Los ejemplos de código son válidos y se entienden
- [ ] **Enlaces**: Todos los enlaces funcionan
- [ ] **Imágenes**: Si usa imágenes, están en `docs/assets/images/`
- [ ] **Navegación**: El archivo está listado en `mkdocs.yml`
- [ ] **Vista previa**: Lo viste localmente y se ve bien

## 📤 Publicar el artículo

Cuando tu artículo esté listo:

```bash
# Ver cambios
git status

# Agregar archivos
git add docs/ mkdocs.yml

# Hacer commit
git commit -m "Agregar artículo: Título del artículo"

# Push a GitHub
git push origin main
```

Si tienes GitHub Pages configurado, tu blog se actualizará automáticamente.

## 💡 Tips y trucos

### Reutilizar contenido
Puedes referenciar otros artículos dentro del tuyo:

```markdown
[Como se vio en el artículo de Docker](../devops/ejemplo-docker.md)
```

### Mantener consistencia
- Usa siempre el mismo formato para resúmenes
- Mantén un tono consistente (formal pero accesible)
- Agrupa contenido relacionado en subsecciones

### Ejemplos efectivos
- Código que se puede copiar y pegar
- Explicaciones paso a paso
- Casos de uso reales
- Errores comunes y cómo evitarlos

### Meta datos útiles en el resumen

```markdown
## 📌 Resumen

- **Dificultad**: Principiante / Intermedio / Avanzado
- **Tiempo de lectura**: 15 minutos
- **Requisitos previos**: Conocimiento de X
- **Última actualización**: 2024
- **Autor**: Tu nombre (opcional)
```

## 🐛 Resolver problemas

### El artículo no aparece en el blog
- Verifica que el archivo está en la carpeta correcta
- Revisa que está listado en `mkdocs.yml`
- Ejecuta `mkdocs build` para ver si hay errores

### El código no se resalta
- Asegúrate de usar bloques de código con triple backtick
- Especifica el lenguaje: ````python`, ````javascript`, etc.

### Las imágenes no se muestran
- Verifica la ruta relativa: `../assets/images/imagen.png`
- Asegúrate que la imagen está en `docs/assets/images/`
- Usa solo caracteres alfanuméricos, guiones y puntos en nombres

### El sitio no se construye
- Ejecuta `mkdocs build` y revisa los errores
- Verifica que no hay errores de sintaxis en `mkdocs.yml`
- Busca caracteres especiales en nombres de archivo

## 📚 Ejemplos de referencia

En la carpeta `docs/` encontrarás estos ejemplos:

- `backend/ejemplo-python.md` - Estructura de artículo técnico
- `frontend/ejemplo-react.md` - Artículo con múltiples ejemplos
- `devops/ejemplo-docker.md` - Artículo paso a paso

Úsalos como referencia para escribir los tuyos.

## 🆘 ¿Necesitas ayuda?

Si tienes dudas:

1. Revisa los artículos de ejemplo
2. Lee la [documentación de Markdown](https://www.markdownguide.org/)
3. Consulta la [guía de Material for MKDocs](https://squidfunk.github.io/mkdocs-material/)

---

**¡Feliz escritura! 🎉**

Recuerda: El mejor artículo es uno que has escrito. Empieza simple y mejora con el tiempo.
