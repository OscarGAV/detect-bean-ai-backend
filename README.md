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

**1. Clonar el repositorio**
```bash
git clone <repository-url>
cd BeanDetectAI
```

**2. Instalar dependencias**
```bash
pip install -r requirements.txt
```

**3. Configurar variables de entorno**

Crea un archivo `.env` en la raíz del proyecto con las siguientes variables:

```env
CLOUDINARY_CLOUD_NAME="your-cloud-name"
CLOUDINARY_API_KEY="your-api-key"
CLOUDINARY_API_SECRET="your-api-secret"
SMTP_SERVER=smtp.gmail.com
SMTP_PORT=587
SMTP_USERNAME=yoursender@gmail.com
SMTP_PASSWORD='abcd altn rqur wxaw'
SMTP_SENDER_EMAIL=yoursender@gmail.com

# Database configuration
DATABASE_HOST="db-host-address"
DATABASE_PORT=5432
DATABASE_NAME="db-name"
DATABASE_USER="db-username"
DATABASE_PASSWORD="db-password"
```

---

## Guía para Obtener Credenciales

### Base de Datos - Supabase

A. **Crear cuenta en Supabase**
   - Ve a https://supabase.com
   - Crea una cuenta gratuita
   - Click en "New Project"

B. **Obtener credenciales de conexión**
   - En tu proyecto, ve a **Settings** (⚙️) → **Database**
   - Busca la sección **Connection string** de tipo **JDBC**
   - Selecciona **"Session pooler"** (NO "Direct connection")
   - Copia los valores:
     ```
     DATABASE_HOST=aws-0-us-west-2.pooler.supabase.com
     DATABASE_PORT=5432
     DATABASE_NAME=postgres
     DATABASE_USER=postgres.xxxxxxxxxxxxxxxxxx
     DATABASE_PASSWORD=tu-contraseña-de-proyecto
     ```

---

### SMTP - Gmail (para notificaciones por email)

A. **Habilitar verificación en 2 pasos**
   - Crea una nueva cuenta de Gmail 
   - Dirígete a la opción de seguridad luego de hacer click en `Administrar tu Cuenta de Google`
   - Busca **Verificación en 2 pasos**
   - Actívala siguiendo las instrucciones

B. **Generar contraseña de aplicación**
   - Luego en la barra de búsqueda escribe `Contraseñas de Aplicaciones`
   - En "Seleccionar app", ingresa el nombre que desees como por ejemplo `BeanDetect SMTP API`
   - Haz click en **"Generar"**
   - Copia la contraseña de 16 caracteres (formato: `xxxx xxxx xxxx xxxx`)

C. **Configurar en `.env`**
   ```env
   SMTP_SERVER=smtp.gmail.com
   SMTP_PORT=587
   SMTP_USERNAME=tu-email@gmail.com
   SMTP_PASSWORD='xxxx xxxx xxxx xxxx'
   SMTP_SENDER_EMAIL=tu-email@gmail.com
   ```

⚠️ **Notas sobre SMTP:**
- Las contraseñas de aplicación solo funcionan si tienes verificación en 2 pasos activada
- No uses tu contraseña normal de Gmail, usa la contraseña de aplicación generada
- Mantén los espacios en la contraseña tal como te los proporciona Google

---

### Cloudinary (para almacenamiento de imágenes)

A. **Crear cuenta en Cloudinary**
   - Ve a https://cloudinary.com
   - Crea una cuenta gratuita
   - Verifica tu email

B. **Obtener credenciales**
   - En el Dashboard, verás tu **"Product Environment Credentials"**
   - Copia los siguientes valores:
     ```
     Cloud name: tu-cloud-name
     API Key: 123456789012345
     API Secret: abcdefghijklmnopqrstuvwxyz12
     ```

C. **Configurar en `.env`**
   ```env
   CLOUDINARY_CLOUD_NAME=tu-cloud-name
   CLOUDINARY_API_KEY=123456789012345
   CLOUDINARY_API_SECRET=abcdefghijklmnopqrstuvwxyz12
   ```

⚠️ **Nota**: Cloudinary ofrece 25GB de almacenamiento gratis al mes.

---

**4. Inicializar el proyecto**
```bash
# Las tablas se crean automáticamente al iniciar la aplicación
python main.py
```

La API estará disponible en:
- **Swagger UI**: http://localhost:8000/docs
- **ReDoc**: http://localhost:8000/redoc

---
