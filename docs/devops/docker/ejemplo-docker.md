# Docker: Containerización para Principiantes

Aprende cómo containerizar tus aplicaciones con Docker y simplifica el deployment.

## 📌 Resumen

- **Dificultad**: Intermedio
- **Tiempo de lectura**: 15 minutos
- **Requisitos**: Docker instalado

## ¿Qué es Docker?

[Docker](../../otro/conceptos-tecnicos.md#docker) es una plataforma que permite empaquetar tus aplicaciones en [contenedores](../../otro/conceptos-tecnicos.md#container-contenedor) independientes. Estos contenedores incluyen todo lo necesario: código, dependencias, y configuración.

### Ventajas de Docker

✅ Consistencia entre desarrollo y producción  
✅ Aislamiento de aplicaciones  
✅ Escalabilidad fácil  
✅ Deployment rápido  

## Conceptos básicos

### Imágenes
Una imagen es una plantilla que define cómo debe ser tu [contenedor](../../otro/conceptos-tecnicos.md#container-contenedor).

### Contenedores
Un [contenedor](../../otro/conceptos-tecnicos.md#container-contenedor) es una instancia en ejecución de una imagen.

### Registros
Repositorios centralizados de imágenes ([Container Registry](../../otro/conceptos-tecnicos.md#container-registry), [Docker Hub](../../otro/conceptos-tecnicos.md#docker), GitHub Container Registry).

## Tu primer Dockerfile

```dockerfile
# Usar una imagen base
FROM python:3.11-slim

# Establecer directorio de trabajo
WORKDIR /app

# Copiar archivos
COPY requirements.txt .

# Instalar dependencias
RUN pip install --no-cache-dir -r requirements.txt

# Copiar código de la aplicación
COPY . .

# Exponer puerto
EXPOSE 5000

# Comando para ejecutar la aplicación
CMD ["python", "app.py"]
```

## Construir y ejecutar

```bash
# Construir la imagen
docker build -t mi-aplicacion:1.0 .

# Ejecutar un contenedor
docker run -p 5000:5000 mi-aplicacion:1.0

# Ver contenedores activos
docker ps

# Detener un contenedor
docker stop <container_id>
```

## Docker Compose para múltiples servicios

```yaml
version: '3.8'

services:
  web:
    build: .
    ports:
      - "5000:5000"
    environment:
      - DATABASE_URL=postgresql://user:password@db:5432/mydb
    depends_on:
      - db
  
  db:
    image: postgres:15
    environment:
      - POSTGRES_USER=user
      - POSTGRES_PASSWORD=password
      - POSTGRES_DB=mydb
    volumes:
      - postgres_data:/var/lib/postgresql/data

volumes:
  postgres_data:
```

Ejecuta con:
```bash
docker-compose up
```

## Mejores prácticas

!!! tip "Optimización"
    - Usa imágenes base ligeras (alpine, slim)
    - Minimiza capas en el Dockerfile
    - Usa .dockerignore para excluir archivos innecesarios

## Ejemplo completo: API Flask

```dockerfile
FROM python:3.11-alpine

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

EXPOSE 8000

CMD ["gunicorn", "--bind", "0.0.0.0:8000", "app:app"]
```

```python
# app.py
from flask import Flask, jsonify

app = Flask(__name__)

@app.route('/api/articulos', methods=['GET'])
def articulos():
    return jsonify([
        {"id": 1, "titulo": "Introducción a Docker"},
        {"id": 2, "titulo": "Mejores prácticas"}
    ])

if __name__ == '__main__':
    app.run()
```

## Conclusión

Docker es esencial en el desarrollo moderno. Aprende a containerizar tus aplicaciones y simplifica toda tu pipeline de deployment.

---

**Recursos adicionales:**
- [Documentación oficial de Docker](https://docs.docker.com/)
- [Docker Hub](https://hub.docker.com/)
- [Play with Docker](https://www.docker.com/play-with-docker)
