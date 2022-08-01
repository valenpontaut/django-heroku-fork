# DJANGO-HEROKU

## Creamos un entorno virtual
It’s a good habit to start every project by creating an isolated virtual environment that won’t be shared with other projects. This can keep your dependencies organized and help avoid package version conflicts. Some dependency managers and packaging tools like Pipenv or poetry automatically create and manage virtual environments for you to follow best practices. Many IDEs like PyCharm do this by default, too, when you’re starting a new project.

However, the most reliable and portable way of creating a Python virtual environment is to do it manually from the command line. You can use an external tool such as virtualenvwrapper or call the built-in venv module directly. While virtualenvwrapper keeps all environments in a predefined parent folder, venv expects you to specify a folder for every environment separately.

You’ll be using the standard venv module in this tutorial. It’s customary to place the virtual environment in the project root folder, so let’s make one first and change the working directory to it:

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
