# 📦 Lista de Dependencias del Proyecto

Documentación detallada de todas las dependencias del sistema de educación financiera.

## 📋 Archivo requirements.txt

```
Django==4.2.7
djangorestframework==3.14.0
django-cors-headers==4.3.1
streamlit==1.28.1
requests==2.31.0
python-dotenv==1.0.0
pandas>=2.2.0
plotly==5.18.0
```

## 🔍 Descripción de Dependencias

### Backend (Django)

#### Django 4.2.7
- **Propósito**: Framework web principal para el backend
- **Uso**: Gestión de modelos, vistas, URLs, administración
- **Documentación**: https://docs.djangoproject.com/en/4.2/
- **Tamaño**: ~8MB
- **Dependencias**: asgiref, sqlparse

#### Django REST Framework 3.14.0
- **Propósito**: Crear API REST para comunicación con el frontend
- **Uso**: Serializadores, ViewSets, endpoints API
- **Documentación**: https://www.django-rest-framework.org/
- **Tamaño**: ~1.1MB
- **Dependencias**: django, djangorestframework

#### django-cors-headers 4.3.1
- **Propósito**: Permitir solicitudes CORS desde Streamlit
- **Uso**: Configuración de CORS en settings.py
- **Documentación**: https://github.com/adamchainz/django-cors-headers
- **Tamaño**: ~12KB
- **Dependencias**: django

### Frontend (Streamlit)

#### Streamlit 1.28.1
- **Propósito**: Framework para crear la interfaz de usuario
- **Uso**: Dashboard, formularios, visualizaciones
- **Documentación**: https://docs.streamlit.io/
- **Tamaño**: ~8.4MB
- **Dependencias**: altair, blinker, cachetools, click, pillow, protobuf, pyarrow, tornado, y muchas más

### Análisis de Datos

#### pandas >=2.2.0
- **Propósito**: Manipulación y análisis de datos
- **Uso**: Procesamiento de transacciones, análisis financiero
- **Documentación**: https://pandas.pydata.org/
- **Tamaño**: ~10.7MB (con dependencias)
- **Nota**: Versión >=2.2.0 es compatible con Python 3.13
- **Dependencias**: numpy, python-dateutil, pytz, tzdata

#### plotly 5.18.0
- **Propósito**: Crear gráficos interactivos
- **Uso**: Visualizaciones en el dashboard y análisis
- **Documentación**: https://plotly.com/python/
- **Tamaño**: ~15.6MB
- **Dependencias**: tenacity, packaging

### Utilidades

#### requests 2.31.0
- **Propósito**: Realizar peticiones HTTP a la API de Django
- **Uso**: Comunicación entre Streamlit y Django
- **Documentación**: https://requests.readthedocs.io/
- **Tamaño**: ~62KB
- **Dependencias**: certifi, charset-normalizer, idna, urllib3

#### python-dotenv 1.0.0
- **Propósito**: Cargar variables de entorno desde archivo .env
- **Uso**: Configuración de SECRET_KEY y otras variables
- **Documentación**: https://github.com/theskumar/python-dotenv
- **Tamaño**: ~19KB
- **Dependencias**: ninguna

## 📊 Resumen de Tamaños

| Paquete | Tamaño Aproximado | Tipo |
|---------|-------------------|------|
| Django | ~8MB | Backend |
| Django REST Framework | ~1.1MB | Backend |
| django-cors-headers | ~12KB | Backend |
| Streamlit | ~8.4MB | Frontend |
| pandas | ~10.7MB | Análisis |
| plotly | ~15.6MB | Visualización |
| requests | ~62KB | Utilidad |
| python-dotenv | ~19KB | Utilidad |
| **Total** | **~44MB** | |

## 🔄 Dependencias Transitivas (Instaladas Automáticamente)

Al instalar las dependencias principales, también se instalan:

### Dependencias de Django
- asgiref 3.10.0
- sqlparse 0.5.3

### Dependencias de Streamlit
- altair 5.5.0
- blinker 1.9.0
- cachetools 5.5.2
- click 8.3.1
- pillow 10.4.0
- protobuf 4.25.8
- pyarrow 22.0.0
- tornado 6.5.2
- rich 13.9.4
- pydeck 0.9.1
- gitpython 3.1.45
- Y muchas más...

### Dependencias de pandas
- numpy 1.26.4
- python-dateutil 2.9.0
- pytz 2025.2
- tzdata 2025.2

### Dependencias de requests
- certifi 2025.11.12
- charset-normalizer 3.4.4
- idna 3.11
- urllib3 2.5.0

## 🎯 Compatibilidad de Versiones

### Python
- **Mínimo**: Python 3.8
- **Recomendado**: Python 3.10 o 3.11
- **Probado**: Python 3.13 (con pandas >=2.2.0)

### Django
- **Versión**: 4.2.7 (LTS)
- **Soporte**: Hasta abril 2026
- **Python**: 3.8 - 3.12

### Streamlit
- **Versión**: 1.28.1
- **Python**: 3.8 - 3.11 (oficialmente)
- **Nota**: Funciona con Python 3.13

## 🔧 Instalación de Dependencias

### Instalación Normal
```bash
pip install -r requirements.txt
```

### Instalación sin Cache (si hay problemas)
```bash
pip install --no-cache-dir -r requirements.txt
```

### Instalación en Modo Desarrollo
```bash
pip install -r requirements.txt --upgrade
```

### Verificar Instalación
```bash
pip list | grep -E "(Django|streamlit|pandas|plotly)"
```

## ⚠️ Notas Importantes

1. **pandas >=2.2.0**: Necesario para compatibilidad con Python 3.13
2. **Django 4.2.7**: Versión LTS (Long Term Support)
3. **Streamlit 1.28.1**: Versión estable, compatible con las dependencias actuales
4. **plotly 5.18.0**: Versión estable para visualizaciones interactivas

## 🔄 Actualización de Dependencias

### Verificar Versiones Instaladas
```bash
pip list
```

### Actualizar Todas las Dependencias
```bash
pip install --upgrade -r requirements.txt
```

### Actualizar una Dependencia Específica
```bash
pip install --upgrade django
```

## 📝 Generar requirements.txt Actualizado

Si instalas nuevas dependencias:
```bash
pip freeze > requirements.txt
```

## 🐛 Solución de Problemas de Dependencias

### Error: "No matching distribution found"
- Verifica tu versión de Python: `python --version`
- Actualiza pip: `pip install --upgrade pip`

### Error: "Failed building wheel for pandas"
- Instala herramientas de compilación
- O usa versión precompilada: `pip install pandas --only-binary :all:`

### Conflicto de Versiones
- Usa entorno virtual para aislar dependencias
- Verifica compatibilidad en la documentación oficial

## 📚 Referencias

- [PyPI - Python Package Index](https://pypi.org/)
- [Django Packages](https://djangopackages.org/)
- [Awesome Python](https://github.com/vinta/awesome-python)

---

**Última actualización**: Noviembre 2024

