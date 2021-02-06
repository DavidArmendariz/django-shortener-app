# Django shortener app

This is a simple app that shortens urls. What I learned so far here:

Commands learned:

* `django-admin startproject <project>`
* `django-admin startapp <app>`
* `python manage.py runserver`
* `python manage.py makemigrations`
* `python manage.py migrate`
* `python manage.py createsuperuser`

Other things learned:

## Include an app in `settings.py`

```python
INSTALLED_APPS = [
    "django.contrib.admin",
    "django.contrib.auth",
    "django.contrib.contenttypes",
    "django.contrib.sessions",
    "django.contrib.messages",
    "django.contrib.staticfiles",
    "shortener",
]
```

## Creating `urls.py`

```python
from django.urls import path
from . import views

urlpatterns = [path("", views.index, name="index")]
```

## Include the app's urls in `settings.py`

```python
urlpatterns = [path("admin/", admin.site.urls), path("", include("shortener.urls"))]
```

## Creating a view

```python
from django.shortcuts import render

def index(request):
    return render(request, "index.html")
```

## Creating a model

```python
from django.db import models

class Url(models.Model):
    link = models.CharField(max_length=10000)
    uuid = models.CharField(max_length=10)
```

## Register models in the admin site

```python
from django.contrib import admin
from .models import Url

admin.site.register(Url)
```
