# DJANGO-HEROKU

## Creamos un entorno virtual

Necesitamos crear un entorno virtual para encapsular todas las librerias que vamos a usar para nuestro sitio.

```
mkdir primer_proyecto
cd primer_proyecto
```

Con el parametro prompt le damos nombre al enviroment:

```
python3 -m venv ./venv --prompt primer_proyecto
```

Luego vemos lo siguiente:

```
primer_proyecto/
│
└── venv/
```

Activamos el enviromente:

```
source venv/bin/activate
```

Instalamos django y gunicorn todas las librerias que vayamos a necesitar en nuestro proyecto.


```
pip3 install django
pip3 install gunicorn
python3 -m pip freeze > requirements.txt
```

Por ultimo cambiamos en `settings.py`

```python
##primer_proyecto\settings.py
ALLOWED_HOSTS = ['*']
```

## Agregamos 3 archivos:

#### `requirements.txt`

Usamos el siguiente comando:

```
python3 -m pip freeze > requirements.txt
```

Nos deberia quedar algo similar:

```
asgiref==3.5.2
backports.zoneinfo==0.2.1
Django==4.0.6
gunicorn==20.1.0
sqlparse==0.4.2
``` 
#### `Procfile`

Ingresamos la siguiente linea:

```
web: gunicorn primer_proyecto.wsgi --log-file -
```

#### `runtime.txt`

Debemos agregar la version de python de nuestro venv, podemos saber cual es usando `python3 --version`.

```
python-3.8.10
```

Finalmente deberiamos tener la siguiente estructura:

```
primer_proyecto/
├─ venv
├─ manage.py
├─ app_prueba/
│  ├─ __init__.py
│  ├─ views.py
│  ├─ tests.py
│  ├─ models.py
│  ├─ apps.py
│  ├─ admin.py
│  ├─ migrations/
├─ primer_proyecto/
│  ├─ __init__.py
│  ├─ asgi.py
│  ├─ settings.py
│  ├─ urls.py
│  ├─ wsgi.py
├─ requirements.txt
├─ Procfile
├─ runtime.txt
```
