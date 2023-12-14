1. mkdir django_rest_api_project
2.cd  django_rest_api_project 
3.python -m venv .venv
#Virtual environments are isolated environments that allow you to manage and install dependencies for a specific project without affecting the global Python environment. This is useful for avoiding conflicts between different projects that may have different package requirements.
#When we push the code to github, we don't push the .venv folder, keep that in gitignore
4..venv\Scripts\activate
#to activate the virtual environment. 

Now Check for Necessary Installations
5. pip list
# this will list down the installed packages
(If Django is not installed, install it)
6.pip install Django==4.2.8
# We are installing Django 4.2.8, becuase we faced some issue with Django 5.0 in O-auth implemenetation
7.django-admin startproject myproject
8.cd myproject
9.pip install djangorestframework
10.pip install psycopg2-binary
#for PostgreSQL support

Configure Database Settings
#In psql:-
CREATE DATABASE collection
CREATE USER james WITH PASSWORD helloworld

#Grant the necessary permissions to the user for the newly created database
ALTER ROLE james SET client_encoding TO 'utf8'
ALTER ROLE james SET default_transaction_isolation TO 'read committed'
ALTER ROLE james SET timezone TO 'UTC'
GRANT ALL PRIVILEGES ON DATABASE collection TO james

#Exit the posrgre sql shell
\q 


#Configure Database Settings in myproject ->  setting.py
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'collection',
        'USER': 'james',
        'PASSWORD': 'helloworld',
        'HOST': 'localhost',
        'PORT': '5432',
    }
}
#Create an application authentication in the myproject for authentication
 python manage.py startapp authentication
#Update INSTALLED_APPS in settings.py

#In authentication app:-
Create models and CustomUser class 

python manage.py makemigrations
#this command is used to make migrations from models created in django app to the migrations folders

python manage.py migrate
#this command will be used to reflect the changes in schema or migration folder to the database directly

python manage.py createsuperuser
pip install djangorestframework_simplejwt

Update the urls in app and project as well.

#serializers are a fundamental part of building APIs with Django REST Framework, facilitating data validation, transformation, and simplifying the handling of complex data structures
