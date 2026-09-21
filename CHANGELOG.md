commit 706053b685172ccf5a202e44d860138f4624ee22
Author: BUHOdeb <ismaelguzver01@gmail.com>
Date:   Mon Sep 21 20:08:44 2026 -0300

    primera ruta

diff --git a/CHANGELOG.md b/CHANGELOG.md
new file mode 100644
index 0000000..e69de29
diff --git a/config/__pycache__/__init__.cpython-314.pyc b/config/__pycache__/__init__.cpython-314.pyc
new file mode 100644
index 0000000..3461adf
Binary files /dev/null and b/config/__pycache__/__init__.cpython-314.pyc differ
diff --git a/config/__pycache__/settings.cpython-314.pyc b/config/__pycache__/settings.cpython-314.pyc
new file mode 100644
index 0000000..2f84591
Binary files /dev/null and b/config/__pycache__/settings.cpython-314.pyc differ
diff --git a/config/__pycache__/urls.cpython-314.pyc b/config/__pycache__/urls.cpython-314.pyc
new file mode 100644
index 0000000..533e00e
Binary files /dev/null and b/config/__pycache__/urls.cpython-314.pyc differ
diff --git a/config/__pycache__/wsgi.cpython-314.pyc b/config/__pycache__/wsgi.cpython-314.pyc
new file mode 100644
index 0000000..98634dd
Binary files /dev/null and b/config/__pycache__/wsgi.cpython-314.pyc differ
diff --git a/config/settings.py b/config/settings.py
index 057abf7..5c3a1dd 100644
--- a/config/settings.py
+++ b/config/settings.py
@@ -37,6 +37,7 @@ INSTALLED_APPS = [
     'django.contrib.sessions',
     'django.contrib.messages',
     'django.contrib.staticfiles',
+    'myApp'
 ]
 
 MIDDLEWARE = [
@@ -54,7 +55,7 @@ ROOT_URLCONF = 'config.urls'
 TEMPLATES = [
     {
         'BACKEND': 'django.template.backends.django.DjangoTemplates',
-        'DIRS': [],
+        'DIRS': [BASE_DIR / 'templates'],
         'APP_DIRS': True,
         'OPTIONS': {
             'context_processors': [
diff --git a/config/urls.py b/config/urls.py
index 77ff5bd..87f0c82 100644
--- a/config/urls.py
+++ b/config/urls.py
@@ -15,8 +15,9 @@ Including another URLconf
     2. Add a URL to urlpatterns:  path('blog/', include('blog.urls'))
 """
 from django.contrib import admin
-from django.urls import path
+from django.urls import path, include
 
 urlpatterns = [
     path('admin/', admin.site.urls),
+    path('', include('myApp.urls')),
 ]
diff --git a/db.sqlite3 b/db.sqlite3
new file mode 100644
index 0000000..e69de29
diff --git a/myApp/__pycache__/__init__.cpython-314.pyc b/myApp/__pycache__/__init__.cpython-314.pyc
new file mode 100644
index 0000000..2696e81
Binary files /dev/null and b/myApp/__pycache__/__init__.cpython-314.pyc differ
diff --git a/myApp/__pycache__/admin.cpython-314.pyc b/myApp/__pycache__/admin.cpython-314.pyc
new file mode 100644
index 0000000..e6caab6
Binary files /dev/null and b/myApp/__pycache__/admin.cpython-314.pyc differ
diff --git a/myApp/__pycache__/apps.cpython-314.pyc b/myApp/__pycache__/apps.cpython-314.pyc
new file mode 100644
index 0000000..3fdee6c
Binary files /dev/null and b/myApp/__pycache__/apps.cpython-314.pyc differ
diff --git a/myApp/__pycache__/models.cpython-314.pyc b/myApp/__pycache__/models.cpython-314.pyc
new file mode 100644
index 0000000..f1bd7b0
Binary files /dev/null and b/myApp/__pycache__/models.cpython-314.pyc differ
diff --git a/myApp/__pycache__/urls.cpython-314.pyc b/myApp/__pycache__/urls.cpython-314.pyc
new file mode 100644
index 0000000..242efee
Binary files /dev/null and b/myApp/__pycache__/urls.cpython-314.pyc differ
diff --git a/myApp/__pycache__/views.cpython-314.pyc b/myApp/__pycache__/views.cpython-314.pyc
new file mode 100644
index 0000000..1e61898
Binary files /dev/null and b/myApp/__pycache__/views.cpython-314.pyc differ
diff --git a/myApp/migrations/__pycache__/__init__.cpython-314.pyc b/myApp/migrations/__pycache__/__init__.cpython-314.pyc
new file mode 100644
index 0000000..e842f4a
Binary files /dev/null and b/myApp/migrations/__pycache__/__init__.cpython-314.pyc differ
diff --git a/myApp/urls.py b/myApp/urls.py
new file mode 100644
index 0000000..e43bf74
--- /dev/null
+++ b/myApp/urls.py
@@ -0,0 +1,7 @@
+from django.urls import path
+
+from . import views
+
+urlpatterns = [
+    path('',views.home, name='home')
+]
\ No newline at end of file
diff --git a/myApp/views.py b/myApp/views.py
index 91ea44a..5768df1 100644
--- a/myApp/views.py
+++ b/myApp/views.py
@@ -1,3 +1,5 @@
 from django.shortcuts import render
 
 # Create your views here.
+def home(request):
+    return render(request, 'index.html')
\ No newline at end of file
diff --git a/templates/index.html b/templates/index.html
new file mode 100644
index 0000000..14a3ce6
--- /dev/null
+++ b/templates/index.html
@@ -0,0 +1,61 @@
+<!DOCTYPE html>
+<html lang="es">
+<head>
+    <meta charset="UTF-8">
+    <meta name="viewport" content="width=device-width, initial-scale=1.0">
+    <title>Bitácora de Aprendizaje - Django</title>
+    <!-- Tailwind CSS CDN para un diseño rápido y moderno -->
+    <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
+</head>
+<body class="bg-slate-950 text-slate-100 min-h-screen flex flex-col justify-between font-sans selection:bg-indigo-500 selection:text-white">
+
+    <!-- Header / Navbar -->
+    <header class="w-full max-w-5xl mx-auto px-6 py-6 flex justify-between items-center border-b border-slate-800/80">
+        <div class="flex items-center space-x-3">
+            <span class="inline-block w-3 h-3 bg-emerald-500 rounded-full animate-pulse"></span>
+            <span class="font-bold tracking-wide text-lg text-slate-200">BitácoraApp</span>
+        </div>
+        <nav class="text-sm text-slate-400 space-x-6">
+            <span class="hover:text-slate-200 transition-colors cursor-pointer">Django 5.x</span>
+            <span class="hover:text-slate-200 transition-colors cursor-pointer">Backend Dev</span>
+        </nav>
+    </header>
+
+    <!-- Main Content -->
+    <main class="max-w-4xl mx-auto px-6 py-16 text-center">
+        <div class="inline-block mb-4 px-3 py-1 bg-indigo-500/10 border border-indigo-500/30 text-indigo-400 text-xs font-semibold rounded-full uppercase tracking-wider">
+            Entorno de Pruebas Activo
+        </div>
+        
+        <h1 class="text-4xl sm:text-6xl font-extrabold tracking-tight text-white mb-6">
+            Construyendo el <span class="text-transparent bg-clip-text bg-gradient-to-r from-indigo-400 to-cyan-400">Backend</span> paso a paso.
+        </h1>
+        
+        <p class="text-lg text-slate-400 max-w-2xl mx-auto mb-10 leading-relaxed">
+            Proyecto base configurado correctamente. Estructurando modelos, controlando rutas dinámicas y registrando cada avance en el código.
+        </p>
+
+        <!-- Tarjetas de estado rápido -->
+        <div class="grid grid-cols-1 sm:grid-cols-3 gap-4 text-left max-w-3xl mx-auto mb-12">
+            <div class="bg-slate-900/60 border border-slate-800 p-5 rounded-xl hover:border-slate-700 transition-all">
+                <h3 class="text-xs font-semibold text-indigo-400 uppercase tracking-wider mb-1">Capa de Datos</h3>
+                <p class="text-slate-200 font-medium text-sm">Modelos configurados y migrados.</p>
+            </div>
+            <div class="bg-slate-900/60 border border-slate-800 p-5 rounded-xl hover:border-slate-700 transition-all">
+                <h3 class="text-xs font-semibold text-cyan-400 uppercase tracking-wider mb-1">Enrutamiento</h3>
+                <p class="text-slate-200 font-medium text-sm">URLs y vistas conectadas.</p>
+            </div>
+            <div class="bg-slate-900/60 border border-slate-800 p-5 rounded-xl hover:border-slate-700 transition-all">
+                <h3 class="text-xs font-semibold text-emerald-400 uppercase tracking-wider mb-1">Control de Versiones</h3>
+                <p class="text-slate-200 font-medium text-sm">Git & Repositorio sincronizados.</p>
+            </div>
+        </div>
+    </main>
+
+    <!-- Footer -->
+    <footer class="w-full max-w-5xl mx-auto px-6 py-6 border-t border-slate-900 text-center text-xs text-slate-500">
+        <p>© 2026 • Desarrollado con enfoque analítico y backend robusto.</p>
+    </footer>
+
+</body>
+</html>
\ No newline at end of file

commit 8bbc37b76b265cbc6f8185b6f4f27ad53f06192d
Author: BUHOdeb <ismaelguzver01@gmail.com>
Date:   Mon Sep 21 19:19:24 2026 -0300

    primer commit: estructura base de django y configuracion

diff --git a/config/__init__.py b/config/__init__.py
new file mode 100644
index 0000000..e69de29
diff --git a/config/asgi.py b/config/asgi.py
new file mode 100644
index 0000000..33a47a1
--- /dev/null
+++ b/config/asgi.py
@@ -0,0 +1,16 @@
+"""
+ASGI config for config project.
+
+It exposes the ASGI callable as a module-level variable named ``application``.
+
+For more information on this file, see
+https://docs.djangoproject.com/en/6.1/howto/deployment/asgi/
+"""
+
+import os
+
+from django.core.asgi import get_asgi_application
+
+os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'config.settings')
+
+application = get_asgi_application()
diff --git a/config/settings.py b/config/settings.py
new file mode 100644
index 0000000..057abf7
--- /dev/null
+++ b/config/settings.py
@@ -0,0 +1,127 @@
+"""
+Django settings for config project.
+
+Generated by 'django-admin startproject' using Django 6.1.1.
+
+For more information on this file, see
+https://docs.djangoproject.com/en/6.1/topics/settings/
+
+For the full list of settings and their values, see
+https://docs.djangoproject.com/en/6.1/ref/settings/
+"""
+
+from pathlib import Path
+
+# Build paths inside the project like this: BASE_DIR / 'subdir'.
+BASE_DIR = Path(__file__).resolve().parent.parent
+
+
+# Quick-start development settings - unsuitable for production
+# See https://docs.djangoproject.com/en/6.1/howto/deployment/checklist/
+
+# SECURITY WARNING: keep the secret key used in production secret!
+SECRET_KEY = 'django-insecure-7fuxr5u19z_s_3bu3g0#9!vlxibv0h@uur(og3l1y(_4lv0mbr'
+
+# SECURITY WARNING: don't run with debug turned on in production!
+DEBUG = True
+
+ALLOWED_HOSTS = []
+
+
+# Application definition
+
+INSTALLED_APPS = [
+    'django.contrib.admin',
+    'django.contrib.auth',
+    'django.contrib.contenttypes',
+    'django.contrib.sessions',
+    'django.contrib.messages',
+    'django.contrib.staticfiles',
+]
+
+MIDDLEWARE = [
+    'django.middleware.security.SecurityMiddleware',
+    'django.contrib.sessions.middleware.SessionMiddleware',
+    'django.middleware.common.CommonMiddleware',
+    'django.middleware.csrf.CsrfViewMiddleware',
+    'django.contrib.auth.middleware.AuthenticationMiddleware',
+    'django.contrib.messages.middleware.MessageMiddleware',
+    'django.middleware.clickjacking.XFrameOptionsMiddleware',
+]
+
+ROOT_URLCONF = 'config.urls'
+
+TEMPLATES = [
+    {
+        'BACKEND': 'django.template.backends.django.DjangoTemplates',
+        'DIRS': [],
+        'APP_DIRS': True,
+        'OPTIONS': {
+            'context_processors': [
+                'django.template.context_processors.request',
+                'django.contrib.auth.context_processors.auth',
+                'django.contrib.messages.context_processors.messages',
+            ],
+        },
+    },
+]
+
+WSGI_APPLICATION = 'config.wsgi.application'
+
+
+# Database
+# https://docs.djangoproject.com/en/6.1/ref/settings/#databases
+
+DATABASES = {
+    'default': {
+        'ENGINE': 'django.db.backends.sqlite3',
+        'NAME': BASE_DIR / 'db.sqlite3',
+    }
+}
+
+
+# Password validation
+# https://docs.djangoproject.com/en/6.1/ref/settings/#auth-password-validators
+
+AUTH_PASSWORD_VALIDATORS = [
+    {
+        'NAME': 'django.contrib.auth.password_validation.UserAttributeSimilarityValidator',
+    },
+    {
+        'NAME': 'django.contrib.auth.password_validation.MinimumLengthValidator',
+    },
+    {
+        'NAME': 'django.contrib.auth.password_validation.CommonPasswordValidator',
+    },
+    {
+        'NAME': 'django.contrib.auth.password_validation.NumericPasswordValidator',
+    },
+]
+
+
+# Internationalization
+# https://docs.djangoproject.com/en/6.1/topics/i18n/
+
+LANGUAGE_CODE = 'en-us'
+
+TIME_ZONE = 'UTC'
+
+USE_I18N = True
+
+USE_TZ = True
+
+
+# Static files (CSS, JavaScript, Images)
+# https://docs.djangoproject.com/en/6.1/howto/static-files/
+
+STATIC_URL = 'static/'
+
+
+# Email
+# https://docs.djangoproject.com/en/6.1/topics/email/#topic-email-configuration
+
+MAILERS = {
+    'default': {
+        'BACKEND': 'django.core.mail.backends.console.EmailBackend',
+    },
+}
diff --git a/config/urls.py b/config/urls.py
new file mode 100644
index 0000000..77ff5bd
--- /dev/null
+++ b/config/urls.py
@@ -0,0 +1,22 @@
+"""
+URL configuration for config project.
+
+The `urlpatterns` list routes URLs to views. For more information please see:
+    https://docs.djangoproject.com/en/6.1/topics/http/urls/
+Examples:
+Function views
+    1. Add an import:  from my_app import views
+    2. Add a URL to urlpatterns:  path('', views.home, name='home')
+Class-based views
+    1. Add an import:  from other_app.views import Home
+    2. Add a URL to urlpatterns:  path('', Home.as_view(), name='home')
+Including another URLconf
+    1. Import the include() function: from django.urls import include, path
+    2. Add a URL to urlpatterns:  path('blog/', include('blog.urls'))
+"""
+from django.contrib import admin
+from django.urls import path
+
+urlpatterns = [
+    path('admin/', admin.site.urls),
+]
diff --git a/config/wsgi.py b/config/wsgi.py
new file mode 100644
index 0000000..1b4cc01
--- /dev/null
+++ b/config/wsgi.py
@@ -0,0 +1,16 @@
+"""
+WSGI config for config project.
+
+It exposes the WSGI callable as a module-level variable named ``application``.
+
+For more information on this file, see
+https://docs.djangoproject.com/en/6.1/howto/deployment/wsgi/
+"""
+
+import os
+
+from django.core.wsgi import get_wsgi_application
+
+os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'config.settings')
+
+application = get_wsgi_application()
diff --git a/manage.py b/manage.py
new file mode 100644
index 0000000..8e7ac79
--- /dev/null
+++ b/manage.py
@@ -0,0 +1,22 @@
+#!/usr/bin/env python
+"""Django's command-line utility for administrative tasks."""
+import os
+import sys
+
+
+def main():
+    """Run administrative tasks."""
+    os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'config.settings')
+    try:
+        from django.core.management import execute_from_command_line
+    except ImportError as exc:
+        raise ImportError(
+            "Couldn't import Django. Are you sure it's installed and "
+            "available on your PYTHONPATH environment variable? Did you "
+            "forget to activate a virtual environment?"
+        ) from exc
+    execute_from_command_line(sys.argv)
+
+
+if __name__ == '__main__':
+    main()
diff --git a/myApp/__init__.py b/myApp/__init__.py
new file mode 100644
index 0000000..e69de29
diff --git a/myApp/admin.py b/myApp/admin.py
new file mode 100644
index 0000000..8c38f3f
--- /dev/null
+++ b/myApp/admin.py
@@ -0,0 +1,3 @@
+from django.contrib import admin
+
+# Register your models here.
diff --git a/myApp/apps.py b/myApp/apps.py
new file mode 100644
index 0000000..faed11d
--- /dev/null
+++ b/myApp/apps.py
@@ -0,0 +1,5 @@
+from django.apps import AppConfig
+
+
+class MyappConfig(AppConfig):
+    name = 'myApp'
diff --git a/myApp/migrations/__init__.py b/myApp/migrations/__init__.py
new file mode 100644
index 0000000..e69de29
diff --git a/myApp/models.py b/myApp/models.py
new file mode 100644
index 0000000..71a8362
--- /dev/null
+++ b/myApp/models.py
@@ -0,0 +1,3 @@
+from django.db import models
+
+# Create your models here.
diff --git a/myApp/tests.py b/myApp/tests.py
new file mode 100644
index 0000000..7ce503c
--- /dev/null
+++ b/myApp/tests.py
@@ -0,0 +1,3 @@
+from django.test import TestCase
+
+# Create your tests here.
diff --git a/myApp/views.py b/myApp/views.py
new file mode 100644
index 0000000..91ea44a
--- /dev/null
+++ b/myApp/views.py
@@ -0,0 +1,3 @@
+from django.shortcuts import render
+
+# Create your views here.
diff --git a/requirements.txt b/requirements.txt
new file mode 100644
index 0000000..e69de29
