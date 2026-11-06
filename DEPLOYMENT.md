# Instrucciones para GitHub Pages

## Opción 1: Deployment automático con GitHub Actions (Recomendado)

Este repositorio incluye un workflow automático que despliega el blog a GitHub Pages cada vez que haces push a `main` o `master`.

### Pasos:

1. **Sube el repositorio a GitHub:**
   ```bash
   git remote add origin https://github.com/TU_USUARIO/my-portfolio.git
   git branch -M main
   git push -u origin main
   ```

2. **Habilita GitHub Pages:**
   - Ve a Settings → Pages
   - En "Build and deployment", selecciona:
     - Source: GitHub Actions
     - (El workflow se ejecutará automáticamente)

3. **Espera a que se complete el workflow:**
   - Ve a la pestaña "Actions"
   - El workflow "Deploy MKDocs to GitHub Pages" debería ejecutarse
   - Una vez que termine, tu blog estará disponible en `https://TU_USUARIO.github.io/my-portfolio/`

## Opción 2: Deployment manual

Si prefieres hacer build y push manualmente:

```bash
# 1. Build el sitio
mkdocs build

# 2. Crea una rama gh-pages
git checkout --orphan gh-pages

# 3. Añade los archivos compilados
git add site/
git commit -m "Deploy to GitHub Pages"

# 4. Push a GitHub
git push -u origin gh-pages
```

## Configuración en GitHub

Después de habilitar GitHub Pages:

1. Ve a Settings → Pages
2. Selecciona la rama de origen (gh-pages si usas Option 2, o GitHub Actions si usas Option 1)
3. Tu blog estará disponible en la URL proporcionada

## Solución de problemas

### El workflow no se ejecuta
- Verifica que tienes permisos de escritura en el repositorio
- Revisa que el archivo `.github/workflows/deploy.yml` existe

### El sitio no se construye
- Ejecuta `mkdocs build` localmente para ver errores
- Verifica que `mkdocs.yml` tiene la configuración correcta

### URL incorrecta
- Si el repo no se llama `my-portfolio`, actualiza `site_url` en `mkdocs.yml`
- O usa la raíz del dominio de usuario sin nombre de repo

---

**Una vez configurado, solo necesitas hacer push de tus cambios y GitHub Pages se actualiza automáticamente.**
