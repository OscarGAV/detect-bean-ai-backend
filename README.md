# BeanDetect AI - Backend API

Backend desarrollado con FastAPI, Python y PostgreSQL (Supabase) siguiendo los patrones **CQRS** (Command Query Responsibility Segregation) y **DDD** (Domain-Driven Design).

## Arquitectura

El proyecto sigue una arquitectura hexagonal y cada Bounded Context sigue la estructura DDD:
- **domain/**: Lógica de negocio (aggregates, entities, value objects, commands, queries)
- **application/**: Casos de uso (command services, query services)
- **infrastructure/**: Implementaciones técnicas (repositories, persistencia)
- **interfaces/**: Capa de presentación (REST controllers, resources, transformers)

## Instalación

### Prerrequisitos

- Python 3.13
- PostgreSQL (Supabase)
- pip

### Pasos de instalación

**Clonar el repositorio**
```bash
git clone <repository-url>
cd BeanDetectAI
```

**Instalar dependencias**
```bash
pip install -r requirements.txt
```

**Inicializar el proyecto**
```bash
# Las tablas se crean automáticamente al iniciar la aplicación
python main.py
```

La API estará disponible en:
- **API**: http://localhost:8000
- **Swagger UI**: http://localhost:8000/docs
- **ReDoc**: http://localhost:8000/redoc


## Base de Datos

La aplicación utiliza PostgreSQL en Supabase con las siguientes características:

- **ORM**: SQLAlchemy
- **Migraciones**: Alembic
- **Connection Pooling**: Configurado para pooler de Supabase