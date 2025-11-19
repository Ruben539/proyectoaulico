# 📦 Guía de Instalación - Sistema de Educación Financiera

Documentación completa para instalar y configurar el sistema de educación financiera desarrollado con Django y Streamlit.

## 📋 Requisitos del Sistema

### Requisitos Mínimos
- **Sistema Operativo**: macOS, Linux o Windows
- **Python**: 3.8 o superior (recomendado 3.10 o 3.11)
- **RAM**: Mínimo 4GB (recomendado 8GB)
- **Espacio en disco**: 500MB libres
- **Conexión a Internet**: Para descargar dependencias

### Software Necesario

#### 1. Python 3.8+
Verifica si tienes Python instalado:
```bash
python3 --version
# o
python --version
```

**Si no tienes Python instalado:**

- **macOS**: 
  ```bash
  # Usando Homebrew (recomendado)
  brew install python@3.11
  
  # O descarga desde: https://www.python.org/downloads/
  ```

- **Linux (Ubuntu/Debian)**:
  ```bash
  sudo apt update
  sudo apt install python3 python3-pip python3-venv
  ```

- **Windows**:
  - Descarga desde: https://www.python.org/downloads/
  - Asegúrate de marcar "Add Python to PATH" durante la instalación

#### 2. pip (Gestor de Paquetes de Python)
Normalmente viene con Python. Verifica:
```bash
pip3 --version
# o
pip --version
```

Si no está instalado:
```bash
# macOS/Linux
python3 -m ensurepip --upgrade

# Windows
python -m ensurepip --upgrade
```

#### 3. Git (Opcional, para clonar el repositorio)
```bash
# macOS
brew install git

# Linux
sudo apt install git

# Windows: Descarga desde https://git-scm.com/download/win
```

## 🚀 Instalación Paso a Paso

### Paso 1: Obtener el Código del Proyecto

Si tienes el proyecto en una carpeta local, navega a ella:
```bash
cd /Users/mambo/Desktop/Sistemas/proyectoaulico
```

Si necesitas clonar desde un repositorio:
```bash
git clone <url-del-repositorio>
cd proyectoaulico
```

### Paso 2: Crear Entorno Virtual

**¿Por qué un entorno virtual?**
- Aísla las dependencias del proyecto
- Evita conflictos con otros proyectos Python
- Facilita la gestión de versiones

**Crear el entorno virtual:**

```bash
# macOS/Linux
python3 -m venv venv

# Windows
python -m venv venv
```

Esto creará una carpeta `venv` en tu proyecto.

### Paso 3: Activar el Entorno Virtual

**macOS/Linux:**
```bash
source venv/bin/activate
```

**Windows:**
```bash
venv\Scripts\activate
```

**Verificación:** Deberías ver `(venv)` al inicio de tu línea de comandos:
```
(venv) usuario@computadora:~/proyectoaulico$
```

### Paso 4: Instalar Dependencias

Con el entorno virtual activado, instala todas las dependencias:

```bash
pip install -r requirements.txt
```

**Dependencias que se instalarán:**
- Django 4.2.7 - Framework web backend
- Django REST Framework 3.14.0 - API REST
- django-cors-headers 4.3.1 - Permite CORS para Streamlit
- Streamlit 1.28.1 - Framework frontend
- pandas >=2.2.0 - Análisis de datos
- plotly 5.18.0 - Visualizaciones interactivas
- requests 2.31.0 - Cliente HTTP
- python-dotenv 1.0.0 - Variables de entorno

**Tiempo estimado:** 2-5 minutos dependiendo de tu conexión.

### Paso 5: Configurar Variables de Entorno

Crea un archivo `.env` en la raíz del proyecto:

```bash
# macOS/Linux
cp .env.example .env

# Windows
copy .env.example .env
```

Edita el archivo `.env` y configura:
```env
SECRET_KEY=tu-clave-secreta-aqui-cambiar-en-produccion
```

**Nota:** Para desarrollo, puedes dejar la clave por defecto. En producción, genera una clave segura.

### Paso 6: Aplicar Migraciones de Base de Datos

Las migraciones crean las tablas en la base de datos:

```bash
# Crear migraciones (si es necesario)
python manage.py makemigrations

# Aplicar migraciones
python manage.py migrate
```

Esto creará el archivo `db.sqlite3` con todas las tablas necesarias.

### Paso 7: Crear Datos Iniciales (Opcional pero Recomendado)

Crea categorías de ejemplo para poder usar el sistema:

```bash
python manage.py shell
```

Dentro del shell de Python:
```python
from tareas.models import Categoria

# Crear categorías de ingresos
Categoria.objects.get_or_create(nombre="Salario", defaults={'tipo': 'ingreso', 'icono': '💼', 'color': '#2ecc71'})
Categoria.objects.get_or_create(nombre="Freelance", defaults={'tipo': 'ingreso', 'icono': '💻', 'color': '#27ae60'})
Categoria.objects.get_or_create(nombre="Inversiones", defaults={'tipo': 'ingreso', 'icono': '📈', 'color': '#16a085'})

# Crear categorías de gastos
Categoria.objects.get_or_create(nombre="Alimentación", defaults={'tipo': 'gasto', 'icono': '🍔', 'color': '#e74c3c'})
Categoria.objects.get_or_create(nombre="Transporte", defaults={'tipo': 'gasto', 'icono': '🚗', 'color': '#3498db'})
Categoria.objects.get_or_create(nombre="Entretenimiento", defaults={'tipo': 'gasto', 'icono': '🎮', 'color': '#9b59b6'})
Categoria.objects.get_or_create(nombre="Educación", defaults={'tipo': 'gasto', 'icono': '📚', 'color': '#f39c12'})
Categoria.objects.get_or_create(nombre="Salud", defaults={'tipo': 'gasto', 'icono': '🏥', 'color': '#e67e22'})
Categoria.objects.get_or_create(nombre="Servicios", defaults={'tipo': 'gasto', 'icono': '💡', 'color': '#f1c40f'})

print("✅ Categorías creadas exitosamente!")
exit()
```

### Paso 8: Crear Superusuario (Opcional)

Para acceder al panel de administración de Django:

```bash
python manage.py createsuperuser
```

Sigue las instrucciones para crear un usuario administrador.

## 🏃 Ejecutar el Sistema

El sistema requiere **DOS terminales** corriendo simultáneamente.

### Terminal 1: Servidor Django (Backend/API)

```bash
# 1. Navega al directorio del proyecto
cd /Users/mambo/Desktop/Sistemas/proyectoaulico

# 2. Activa el entorno virtual
source venv/bin/activate  # macOS/Linux
# o
venv\Scripts\activate  # Windows

# 3. Inicia el servidor Django
python manage.py runserver
```

**Salida esperada:**
```
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
```

**Verificación:** Abre `http://localhost:8000/api/` en tu navegador. Deberías ver la lista de endpoints.

### Terminal 2: Aplicación Streamlit (Frontend)

```bash
# 1. Navega al directorio del proyecto (en una nueva terminal)
cd /Users/mambo/Desktop/Sistemas/proyectoaulico

# 2. Activa el entorno virtual
source venv/bin/activate  # macOS/Linux
# o
venv\Scripts\activate  # Windows

# 3. Inicia Streamlit
streamlit run app_streamlit.py
```

**Salida esperada:**
```
You can now view your Streamlit app in your browser.

Local URL: http://localhost:8501
Network URL: http://192.168.x.x:8501
```

**Verificación:** Abre `http://localhost:8501` en tu navegador. Deberías ver la aplicación.

## 🌐 Acceder a la Aplicación

Una vez que ambos servidores estén corriendo:

| Servicio | URL | Descripción |
|----------|-----|-------------|
| **Aplicación Principal** | http://localhost:8501 | Interfaz de usuario Streamlit |
| **API REST** | http://localhost:8000/api/ | Endpoints de la API |
| **Panel Admin Django** | http://localhost:8000/admin | Panel de administración |

## 📦 Resumen de Instalación Rápida

```bash
# 1. Crear entorno virtual
python3 -m venv venv

# 2. Activar entorno virtual
source venv/bin/activate  # macOS/Linux
# venv\Scripts\activate  # Windows

# 3. Instalar dependencias
pip install -r requirements.txt

# 4. Configurar variables de entorno
cp .env.example .env

# 5. Aplicar migraciones
python manage.py makemigrations
python manage.py migrate

# 6. Crear datos iniciales (opcional)
python manage.py shell
# (ejecutar código Python para crear categorías)

# 7. En Terminal 1: Iniciar Django
python manage.py runserver

# 8. En Terminal 2: Iniciar Streamlit
streamlit run app_streamlit.py
```

## 🔧 Solución de Problemas Comunes

### Error: "python3: command not found"
**Solución:** Instala Python 3.8 o superior. Ver sección "Requisitos del Sistema".

### Error: "pip: command not found"
**Solución:**
```bash
python3 -m ensurepip --upgrade
```

### Error: "ModuleNotFoundError: No module named 'django'"
**Solución:** 
1. Verifica que el entorno virtual esté activado (deberías ver `(venv)` en tu terminal)
2. Instala las dependencias: `pip install -r requirements.txt`

### Error: "Port 8000 already in use"
**Solución:** 
- Cierra el proceso que está usando el puerto 8000
- O cambia el puerto: `python manage.py runserver 8001`
- Luego actualiza `API_BASE_URL` en `app_streamlit.py` a `http://localhost:8001`

### Error: "Port 8501 already in use"
**Solución:**
- Cierra el proceso que está usando el puerto 8501
- O cambia el puerto: `streamlit run app_streamlit.py --server.port 8502`

### Error al instalar pandas (Python 3.13)
**Solución:** Ya está resuelto. El `requirements.txt` usa `pandas>=2.2.0` que es compatible con Python 3.13.

### Error: "No migrations to apply"
**Solución:** Esto es normal si ya aplicaste las migraciones. Si es la primera vez:
```bash
python manage.py makemigrations
python manage.py migrate
```

### La aplicación Streamlit no se conecta a Django
**Solución:**
1. Verifica que Django esté corriendo: abre `http://localhost:8000/api/`
2. Verifica que `API_BASE_URL` en `app_streamlit.py` sea `http://localhost:8000`
3. Asegúrate de que ambos servidores estén corriendo

### Error: "db.sqlite3: Permission denied"
**Solución:**
```bash
chmod 664 db.sqlite3  # macOS/Linux
```

## 📝 Notas Importantes

1. **Siempre activa el entorno virtual** antes de ejecutar comandos Python
2. **Mantén ambas terminales abiertas** mientras uses la aplicación
3. **Django debe estar corriendo antes** de abrir Streamlit
4. **Los datos se guardan en `db.sqlite3`** (base de datos SQLite local)
5. **Para producción**, considera usar PostgreSQL o MySQL en lugar de SQLite

## 🎯 Verificación Final

Ejecuta estos comandos para verificar que todo está instalado correctamente:

```bash
# Activar entorno virtual
source venv/bin/activate

# Verificar Python
python --version

# Verificar Django
python manage.py check

# Verificar dependencias instaladas
pip list | grep -E "(Django|streamlit|pandas|plotly)"

# Verificar base de datos
python manage.py shell -c "from tareas.models import Categoria; print(f'Categorías: {Categoria.objects.count()}')"
```

## 📚 Recursos Adicionales

- **Documentación Django**: https://docs.djangoproject.com/
- **Documentación Streamlit**: https://docs.streamlit.io/
- **Documentación Django REST Framework**: https://www.django-rest-framework.org/
- **Guía de inicio rápido**: Ver `GUIA_INICIO.md`

## ✅ Checklist de Instalación

- [ ] Python 3.8+ instalado
- [ ] pip instalado y funcionando
- [ ] Entorno virtual creado
- [ ] Entorno virtual activado
- [ ] Dependencias instaladas (`pip install -r requirements.txt`)
- [ ] Archivo `.env` creado
- [ ] Migraciones aplicadas (`python manage.py migrate`)
- [ ] Datos iniciales creados (categorías)
- [ ] Django corriendo en puerto 8000
- [ ] Streamlit corriendo en puerto 8501
- [ ] Aplicación accesible en http://localhost:8501

## 🆘 Soporte

Si encuentras problemas durante la instalación:

1. Revisa la sección "Solución de Problemas Comunes"
2. Verifica que cumplas todos los requisitos del sistema
3. Asegúrate de seguir los pasos en orden
4. Verifica los logs de error para más detalles

---

**¡Listo!** Una vez completados todos los pasos, tu sistema de educación financiera estará funcionando. 🎉

