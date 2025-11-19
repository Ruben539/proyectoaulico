# ⚡ Instalación Rápida - Comandos Esenciales

Guía rápida con solo los comandos necesarios para instalar y ejecutar el sistema.

## 📋 Requisitos Previos

- Python 3.8 o superior
- pip (gestor de paquetes de Python)

**Verificar instalación:**
```bash
python3 --version
pip3 --version
```

## 🚀 Instalación en 5 Pasos

### 1. Crear Entorno Virtual
```bash
python3 -m venv venv
```

### 2. Activar Entorno Virtual

**macOS/Linux:**
```bash
source venv/bin/activate
```

**Windows:**
```bash
venv\Scripts\activate
```

### 3. Instalar Dependencias
```bash
pip install -r requirements.txt
```

### 4. Configurar Base de Datos
```bash
# Aplicar migraciones
python manage.py makemigrations
python manage.py migrate

# Crear categorías de ejemplo (opcional)
python manage.py shell
```
```python
from tareas.models import Categoria
Categoria.objects.get_or_create(nombre="Salario", defaults={'tipo': 'ingreso', 'icono': '💼', 'color': '#2ecc71'})
Categoria.objects.get_or_create(nombre="Alimentación", defaults={'tipo': 'gasto', 'icono': '🍔', 'color': '#e74c3c'})
Categoria.objects.get_or_create(nombre="Transporte", defaults={'tipo': 'gasto', 'icono': '🚗', 'color': '#3498db'})
Categoria.objects.get_or_create(nombre="Entretenimiento", defaults={'tipo': 'gasto', 'icono': '🎮', 'color': '#9b59b6'})
Categoria.objects.get_or_create(nombre="Educación", defaults={'tipo': 'gasto', 'icono': '📚', 'color': '#f39c12'})
exit()
```

### 5. Ejecutar la Aplicación

**Abre DOS terminales:**

**Terminal 1 - Django:**
```bash
cd /ruta/al/proyecto
source venv/bin/activate  # macOS/Linux
# .\venv\Scripts\Activate.ps1  # Windows PowerShell
python manage.py runserver
```

**Terminal 2 - Streamlit:**
```bash
cd /ruta/al/proyecto
source venv/bin/activate  # macOS/Linux
# .\venv\Scripts\Activate.ps1  # Windows PowerShell
streamlit run app_streamlit.py
```

## 🌐 Acceder

- **Aplicación:** http://localhost:8501
- **API:** http://localhost:8000/api/
- **Admin:** http://localhost:8000/admin

## 📦 Dependencias Instaladas

El archivo `requirements.txt` instala:

- **Django 4.2.7** - Framework web backend
- **Django REST Framework 3.14.0** - API REST
- **django-cors-headers 4.3.1** - CORS para Streamlit
- **Streamlit 1.28.1** - Framework frontend
- **pandas >=2.2.0** - Análisis de datos (compatible Python 3.13)
- **plotly 5.18.0** - Visualizaciones
- **requests 2.31.0** - Cliente HTTP
- **python-dotenv 1.0.0** - Variables de entorno

## ⚠️ Problemas Comunes

**Error: "ModuleNotFoundError"**
```bash
# Asegúrate de activar el entorno virtual
source venv/bin/activate
pip install -r requirements.txt
```

**Error: "Port already in use"**
```bash
# Cambiar puerto Django
python manage.py runserver 8001

# Cambiar puerto Streamlit
streamlit run app_streamlit.py --server.port 8502
```

**Error: "No migrations to apply"**
```bash
python manage.py makemigrations
python manage.py migrate
```

## 📚 Documentación Completa

Para más detalles, consulta `INSTALACION.md`

