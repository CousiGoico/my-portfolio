# Mi Blog de Programación

Un blog completamente configurado con MKDocs y Material theme para compartir artículos sobre programación, DevOps y desarrollo web.

## 🚀 Características

- **Tema Material para MKDocs**: Interfaz moderna y responsiva
- **Búsqueda integrada**: Encuentra fácilmente artículos
- **Modo oscuro/claro**: Experiencia cómoda de lectura
- **Categorías organizadas**: Backend, Frontend, DevOps, Tutoriales y más
- **Markdown puro**: Escribe contenido en formato markdown
- **Deployable en GitHub Pages**: Automatiza el deployment

## 📋 Requisitos

- Python 3.8+
- pip

## 🛠️ Instalación

1. **Instala las dependencias:**
   ```bash
   pip install -r requirements.txt
   ```

2. **Sirve localmente:**
   ```bash
   mkdocs serve
   ```
   El blog estará disponible en `http://localhost:8000`

3. **Construye para producción:**
   ```bash
   mkdocs build
   ```

## 📝 Cómo añadir artículos

Consulta el archivo `GUIA.md` para instrucciones detalladas sobre cómo escribir nuevos artículos.

**Resumen rápido:**
1. Crea un archivo `.md` en la carpeta correspondiente (backend/, frontend/, devops/, tutoriales/, otro/)
2. Usa el template con frontmatter y estructura adecuada
3. Actualiza `mkdocs.yml` si necesitas agregar el artículo a la navegación

## 🚀 Deployment en GitHub Pages

1. Pushea el repositorio a GitHub
2. Habilita GitHub Pages en Settings (rama: main, carpeta: / o /docs)
3. Configura el flujo de trabajo automático en `.github/workflows/`

## 📚 Estructura

```
my-portfolio/
├── docs/
│   ├── index.md           # Página de inicio
│   ├── backend/           # Artículos de backend
│   ├── frontend/          # Artículos de frontend
│   ├── devops/            # Artículos de DevOps
│   ├── tutoriales/        # Tutoriales paso a paso
│   ├── otro/              # Otros temas
│   └── assets/
│       └── images/        # Imágenes para artículos
├── mkdocs.yml             # Configuración de MKDocs
├── requirements.txt       # Dependencias Python
└── README.md             # Este archivo
```

## 📄 Licencia

Este proyecto es de código abierto. Siéntete libre de personalizar y compartir tus artículos.

---

Hecho con ❤️ usando [MKDocs](https://www.mkdocs.org/) y [Material Theme](https://squidfunk.github.io/mkdocs-material/)
