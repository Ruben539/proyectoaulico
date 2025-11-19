# Educación Financiera - Prototipo de Aplicación

**Diseño y validación de un prototipo de aplicación como apoyo a la educación financiera de adultos jóvenes paraguayos (2024–2025), con énfasis en usabilidad y análisis de datos**

Aplicación web desarrollada con Django (backend/API) y Streamlit (frontend) para la gestión y educación financiera personal.

## 🎯 Objetivo del Proyecto

Este prototipo tiene como objetivo apoyar la educación financiera de adultos jóvenes paraguayos mediante:
- **Gestión de finanzas personales**: Control de ingresos, gastos y presupuestos
- **Metas financieras**: Establecimiento y seguimiento de objetivos de ahorro
- **Educación financiera**: Contenido educativo adaptado a diferentes niveles
- **Análisis de datos**: Visualizaciones y reportes para entender el comportamiento financiero
- **Usabilidad**: Interfaz intuitiva y accesible para jóvenes

## 🚀 Características Principales

### Backend Django (API REST)
- **Modelos financieros completos**: Categorías, Presupuestos, Transacciones, Metas Financieras, Lecciones Educativas
- **API REST completa**: Endpoints para todas las operaciones CRUD
- **Análisis de datos**: Endpoints especializados para análisis y estadísticas
- **Panel de administración**: Gestión completa desde Django Admin

### Frontend Streamlit
- **Dashboard financiero**: Vista general con métricas clave y visualizaciones
- **Gestión de transacciones**: Registro de ingresos y gastos con categorización
- **Presupuestos**: Creación y seguimiento de presupuestos mensuales por categoría
- **Metas financieras**: Establecimiento y seguimiento de objetivos de ahorro
- **Lecciones educativas**: Contenido educativo sobre finanzas personales
- **Análisis avanzado**: Gráficos y tendencias para análisis de comportamiento financiero

### Análisis y Visualizaciones
- Gráficos interactivos con Plotly
- Análisis de tendencias mensuales
- Distribución de gastos por categoría
- Progreso de metas financieras
- Resúmenes y reportes personalizados

## 📋 Requisitos

- Python 3.8 o superior (recomendado 3.10 o 3.11)
- pip (gestor de paquetes de Python)
- 4GB RAM mínimo (8GB recomendado)
- 500MB espacio en disco

**📚 Documentación de Instalación Completa:**
- **Guía detallada:** Ver [INSTALACION.md](INSTALACION.md) - Instrucciones paso a paso completas
- **Guía rápida:** Ver [INSTALACION_RAPIDA.md](INSTALACION_RAPIDA.md) - Solo comandos esenciales
- **Guía para Windows:** Ver [INSTALACION_WINDOWS.md](INSTALACION_WINDOWS.md) - Instalación específica para Windows

## 🔧 Instalación Rápida

> **💡 Para una guía completa con solución de problemas, consulta [INSTALACION.md](INSTALACION.md)**

1. **Navegar al directorio del proyecto:**
```bash
cd proyectoaulico
```

2. **Crear un entorno virtual (recomendado):**
```bash
python -m venv venv
source venv/bin/activate  # En Windows: venv\Scripts\activate
```

3. **Instalar dependencias:**
```bash
pip install -r requirements.txt
```

4. **Configurar variables de entorno:**
```bash
cp .env.example .env
# Editar .env y configurar SECRET_KEY si es necesario
```

5. **Aplicar migraciones de Django:**
```bash
python manage.py migrate
```

6. **Crear datos iniciales (opcional):**
```bash
python manage.py shell
```
```python
from tareas.models import Categoria

# Crear categorías de ejemplo
Categoria.objects.create(nombre="Salario", tipo="ingreso", icono="💼", color="#2ecc71")
Categoria.objects.create(nombre="Alimentación", tipo="gasto", icono="🍔", color="#e74c3c")
Categoria.objects.create(nombre="Transporte", tipo="gasto", icono="🚗", color="#3498db")
Categoria.objects.create(nombre="Entretenimiento", tipo="gasto", icono="🎮", color="#9b59b6")
Categoria.objects.create(nombre="Educación", tipo="gasto", icono="📚", color="#f39c12")
```

7. **Crear un superusuario (para acceder al admin):**
```bash
python manage.py createsuperuser
```

## 🏃 Ejecución

La aplicación requiere ejecutar dos servidores simultáneamente:

### Terminal 1 - Servidor Django (API)
```bash
python manage.py runserver
```
O usando el script:
```bash
./run_django.sh
```

El servidor Django estará disponible en: `http://localhost:8000`

### Terminal 2 - Aplicación Streamlit
```bash
streamlit run app_streamlit.py
```
O usando el script:
```bash
./run_streamlit.sh
```

La aplicación Streamlit estará disponible en: `http://localhost:8501`

## 📚 Uso de la Aplicación

### Dashboard Principal
- Vista general de tu situación financiera
- Métricas clave: ingresos, gastos, balance del mes
- Progreso de metas financieras
- Estado de presupuestos

### Gestión de Transacciones
1. **Agregar transacciones**: Registra tus ingresos y gastos
2. **Categorizar**: Asigna cada transacción a una categoría
3. **Filtrar**: Visualiza transacciones por tipo, categoría o fecha
4. **Analizar**: Revisa gráficos de tus transacciones

### Presupuestos
1. **Crear presupuestos**: Establece límites mensuales por categoría
2. **Seguimiento**: Visualiza cuánto has gastado vs. tu presupuesto
3. **Alertas**: El sistema te indica cuando te acercas o excedes tu presupuesto

### Metas Financieras
1. **Establecer metas**: Define objetivos de ahorro con monto y fecha
2. **Seguimiento**: Agrega dinero a tus metas y visualiza el progreso
3. **Motivación**: Ve cuánto falta para alcanzar cada meta

### Lecciones Educativas
- Contenido educativo sobre finanzas personales
- Niveles: Básico, Intermedio, Avanzado
- Consejos prácticos adaptados al contexto paraguayo

### Análisis Financiero
- **Resumen mensual**: Ingresos, gastos y balance por mes
- **Tendencias**: Análisis de comportamiento a lo largo del tiempo
- **Gastos por categoría**: Visualización de distribución de gastos
- **Gráficos interactivos**: Explora tus datos financieros

## 🔌 API REST de Django

La API está disponible en `http://localhost:8000/api/`

### Endpoints Disponibles:

#### Categorías
- `GET /api/categorias/` - Listar categorías
- `POST /api/categorias/` - Crear categoría
- `GET /api/categorias/{id}/` - Obtener categoría
- `PATCH /api/categorias/{id}/` - Actualizar categoría
- `DELETE /api/categorias/{id}/` - Eliminar categoría

#### Transacciones
- `GET /api/transacciones/` - Listar transacciones
- `POST /api/transacciones/` - Crear transacción
- `GET /api/transacciones/resumen_mensual/` - Resumen del mes
- `GET /api/transacciones/tendencias/` - Tendencias de meses anteriores

#### Presupuestos
- `GET /api/presupuestos/` - Listar presupuestos
- `POST /api/presupuestos/` - Crear presupuesto
- `GET /api/presupuestos/{id}/` - Obtener presupuesto con estadísticas

#### Metas Financieras
- `GET /api/metas/` - Listar metas
- `POST /api/metas/` - Crear meta
- `POST /api/metas/{id}/agregar_monto/` - Agregar monto a una meta

#### Lecciones Educativas
- `GET /api/lecciones/` - Listar lecciones activas
- `GET /api/lecciones/{id}/` - Obtener lección

#### Análisis
- `GET /api/analisis/dashboard/` - Dashboard con estadísticas generales

### Ejemplo de Uso de la API:

```bash
# Crear una transacción
curl -X POST http://localhost:8000/api/transacciones/ \
  -H "Content-Type: application/json" \
  -d '{
    "descripcion": "Salario mensual",
    "monto": 3000000,
    "tipo": "ingreso",
    "fecha": "2024-12-01"
  }'

# Obtener resumen mensual
curl http://localhost:8000/api/transacciones/resumen_mensual/?mes=12&año=2024
```

## 🏗️ Estructura del Proyecto

```
proyectoaulico/
├── proyectoaulico/          # Configuración principal de Django
│   ├── settings.py          # Configuración del proyecto
│   ├── urls.py              # URLs principales
│   └── ...
├── tareas/                  # Aplicación Django para finanzas
│   ├── models.py            # Modelos: Categoria, Presupuesto, Transaccion, MetaFinanciera, LeccionEducativa
│   ├── views.py             # ViewSets de la API
│   ├── serializers.py       # Serializadores REST
│   ├── urls.py              # URLs de la API
│   └── admin.py             # Configuración del admin
├── app_streamlit.py         # Aplicación Streamlit principal
├── requirements.txt         # Dependencias del proyecto
├── manage.py               # Script de gestión de Django
└── README.md               # Este archivo
```

## 🎯 Modelos de Datos

### Categoria
Clasifica transacciones en ingresos o gastos con iconos y colores.

### Presupuesto
Presupuesto mensual por categoría con seguimiento de gastos y porcentaje usado.

### Transaccion
Registra ingresos y gastos con descripción, monto, categoría y fecha.

### MetaFinanciera
Objetivos de ahorro con monto objetivo, progreso y fecha límite.

### LeccionEducativa
Contenido educativo sobre finanzas personales con diferentes niveles.

## 📊 Análisis de Datos

La aplicación incluye múltiples funcionalidades de análisis:

1. **Análisis temporal**: Tendencias de ingresos y gastos a lo largo del tiempo
2. **Análisis por categoría**: Distribución de gastos e ingresos
3. **Análisis de presupuestos**: Comparación de gastos reales vs. presupuestados
4. **Análisis de metas**: Progreso y proyecciones de metas financieras
5. **Visualizaciones interactivas**: Gráficos de barras, líneas, pastel y medidores

## 🎨 Usabilidad

El diseño de la aplicación se enfoca en:

- **Interfaz intuitiva**: Navegación clara y sencilla
- **Visualizaciones claras**: Gráficos y métricas fáciles de entender
- **Feedback inmediato**: Confirmaciones y mensajes de error claros
- **Responsive**: Adaptable a diferentes tamaños de pantalla
- **Accesible**: Colores y contrastes adecuados
- **Contexto paraguayo**: Moneda en Guaraníes (₲) y contenido relevante

## 🔒 Seguridad

- En producción, cambia `SECRET_KEY` en el archivo `.env`
- Configura `DEBUG = False` en `settings.py`
- Ajusta `ALLOWED_HOSTS` según tu dominio
- Considera agregar autenticación para la API
- Implementa validación de datos en el frontend

## 📝 Notas para Desarrollo

- Asegúrate de que Django esté corriendo antes de usar Streamlit
- La aplicación Streamlit se conecta a `http://localhost:8000` por defecto
- Si cambias el puerto de Django, actualiza `API_BASE_URL` en `app_streamlit.py`
- Los datos se almacenan en SQLite por defecto (db.sqlite3)
- Para producción, considera usar PostgreSQL o MySQL

## 🛠️ Tecnologías Utilizadas

- **Django 4.2**: Framework web de Python
- **Django REST Framework**: Para crear la API REST
- **Streamlit**: Framework para aplicaciones web interactivas
- **Plotly**: Visualizaciones interactivas
- **Pandas**: Análisis y manipulación de datos
- **SQLite**: Base de datos (por defecto en Django)

## 📈 Validación y Usabilidad

Este prototipo está diseñado para:

1. **Validación de usabilidad**: Probar la interfaz con usuarios reales
2. **Análisis de datos**: Recopilar información sobre el uso y comportamiento
3. **Mejora continua**: Iterar basándose en feedback de usuarios
4. **Educación financiera**: Medir el impacto en el conocimiento financiero

## 📄 Licencia

Este es un proyecto académico para el diseño y validación de un prototipo de aplicación de educación financiera.

## 👨‍💻 Autor

Proyecto de facultad - Sistemas  
**Objetivo**: Diseño y validación de un prototipo de aplicación como apoyo a la educación financiera de adultos jóvenes paraguayos (2024–2025), con énfasis en usabilidad y análisis de datos
