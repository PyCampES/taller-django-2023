# Taller Django PyCamp 2023

## Participantes

- Juan Luis
- Jorge Martinez
- Alex
- Sergio
- David
- Wen
- Jordi H
- Unai
- Ángel Guinot
- Manuel
- Inna
- Nekmo
- Samuel
- Yohan

## Preparación

Requisitos: Python 3.6+

Instalación:

```
$ python -m venv .venv
$ source .venv/bin/activate  # Linux & macOS
$ .venv\Scripts\activate.bat  # Windows
(.venv) $ pip install "django==4.2.*"
```

## Notas

1. Abrir este documento
2. Instalar Django (la última versión es la 4.2) en un entorno virtual (ver arriba)
3. Abrir el tutorial oficial, parte 1 https://docs.djangoproject.com/es/4.2/intro/tutorial01/
4. Llegar hasta la parte 4

## Resumen

### Parte 1

- Comandos

```
django-admin startproject mysite
cd mysite

python manage.py runserver  # Para probar el servidor de desarrollo

python manage.py startapp polls
```

- Crear primera vista en `polls/views.py`
- Asignar URLs de la app en `polls/urls.py` (hay que crearlo)
- Asignar URLs globales en `mysite/urls.py`
- Abrir http://127.0.0.1:8000/polls :tada: 

### Parte 2

- Comandos del API

```
Question.objects.all()
Question.objects.filter(id=1)
Question.objects.filter(question_text__startswith="What")
Question.objects.get(pub_date__year=timezone.now().year)
Question.objects.get(id=1) OR Question.objects.get(pk=1)

q = Question.objects.get(pk=1)
q.choice_set.all()
            .create(choice_text="Not much", votes=0)
            .count()
```

- (Opcional) Instalar otra base de datos y modificar `DATABASES` en `mysite/settings.py`
- (Opcional) Modificar `TIME_ZONE` en `mysite/settings.py`
- Correr `python manage.py migrate`
- Añadir modelos a `polls/models.py`
- Añadir la app `polls` a `INSTALLED_APPS` en `mysite/settings.py`
- Correr `python manage.py makemigrations polls`
- Correr `python manage.py migrate`
- Instalar IPython con `pip install ipython`
- Lanzar la shell `python manage.py shell`
- Registrar modelo en `polls/admin.py`

### Parte 3

- Crear `polls/templates/polls/index.html`
- Añadir más vistas en `polls/views.py`
- Agregar URLs correspondientes en `polls/urls.py`

## Dudas

- ¿Por qué aparece un warning que dice `You have unapplied 18 migrations; your app may not work properly until they are applied.`?
  - ...
- ¿Dónde se tiene que crear el directorio `polls`?
  - Al mismo nivel que `manage.py`
- ¿Por qué `http://127.0.0.1:8000/` da error 404 nada más crear la primera vista?
  - Porque tienes que abrir `http://127.0.0.1:8000/polls`!
- ¿Por qué `INSTALLED_APPS` no contiene la app que acabamos de definir?
  - Hay que añadirla manualmente.
- ¿De dónde ha salido `Question.choice_set`?

## Sugerencias

- A mitad de la parte 2 dice "este [comando] se denomina migrate, y hablaremos de ello en un momento", pero en realidad se mencionó arriba

## Recursos

**Tutorial oficial, parte 1**: https://docs.djangoproject.com/es/4.2/intro/tutorial01/

Otros:
- https://docs.djangoproject.com/es/4.2/intro/overview/
- https://docs.djangoproject.com/en/4.2/#first-steps
- https://www.django-rest-framework.org/
- https://tutorial.djangogirls.org/es/
- https://github.com/HackSoftware/Django-Styleguide # Recurso avanzado
