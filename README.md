# djangorestframework quickstart
In this repository, I followed a Django full tutorial from the official site. Here is the link: https://www.django-rest-framework.org/tutorial/1-serialization/

This README provides the log what I've done with this repository. This repository also the result of my study in that tutorial.

**Table of Content**
- [Initial Steps](#initial-steps)
  - [1. Create and run a Virtual Environment into your terminal](#1-create-and-run-a-virtual-environment-into-your-terminal)
  - [2. Install packages](#2-install-packages)
  - [3. Create a Django Project](#3-create-a-django-project)
  - [4. Create an App inside the project](#4-create-an-app-inside-the-project)
  - [5. Migrate your database for the first time](#5-migrate-your-database-for-the-first-time)
  - [6. Create an initial user](#6-create-an-initial-user)
- [Reconfigure the project](#reconfigure-the-project)
  - [1. Create Virtual Environment](#1-create-virtual-environment)
  - [2. Install The Packages in `requirement.txt`](#2-install-the-packages-in-requirementtxt)
  - [3. Start The Development by Creating a New App](#3-start-the-development-by-creating-a-new-app)
  - [4. Register the Packages and the Applications](#4-register-the-packages-and-the-applications)
  - [5. Migrate the Database](#5-migrate-the-database)
  - [6. Create a New Initial User](#6-create-a-new-initial-user)
- [Models and Migrations](#models-and-migrations)
- [Serializer Class](#serializer-class)
- [Model Serializer](#model-serializer)
- [Regular Djago Views using our Serializer](#regular-djago-views-using-our-serializer)

## Initial Steps
The initial steps is the same as my [quickstart repository](https://github.com/ryumada/python-djangorestframework-quickstart).

### 1. Create and run a Virtual Environment into your terminal
Let's start this learn by creating your virtual environment (venv). Please refer to this link to learn how to make one: https://gist.github.com/ryumada/c22133988fd1c22a66e4ed1b23eca233

### 2. Install packages
Install these packages below using this command:
```bash
pip install package-name
```

**Required Packages**
- Python (3.6, 3.7, 3.8, 3.9, 3.10)
- Django (2.2, 3.0, 3.1, 3.2, 4.0)
- DjangoRESTframework

**Optional Packages:**
- PyYAML, uritemplate (5.1+, 3.0.0+) - Schema generation support.
- Markdown (3.0.0+) - Markdown support for the browsable API.
- Pygments (2.4.0+) - Add syntax highlighting to Markdown processing.
- django-filter (1.0.1+) - Filtering support.
- django-guardian (1.1.1+) - Object level permissions support.

### 3. Create a Django Project
create a project called **tutorial**, with this command:

```bash
django-admin startproject tutorial .
```

> In this repository I'm not using the last dot (.) syntax, so it'll create the project inside **tutorial** directory. But in the future, you should create the project inside the root repository.

### 4. Create an App inside the project
Go inside the project directory.
```bash
cd tutorial
```

Then create an app called **quickstart**.
```bash
django-admin startapp quickstart
```

Then get back to **tutorial**'s directory.
```bash
cd ..
```

### 5. Migrate your database for the first time
```bash
python3 manage.py migrate
```

### 6. Create an initial user
```bash
python3 manage.py createsuperuser --email admin@example.com --username admin
```

## Reconfigure the project
If you have clone a djangorestframework project, and want to continue the development. You can do these initial steps instead:
### 1. Create Virtual Environment
Let's start this learn by creating your virtual environment (venv). Please refer to this link to see how to make it: https://gist.github.com/ryumada/c22133988fd1c22a66e4ed1b23eca233

### 2. Install The Packages in `requirement.txt`
```bash
pip install -r requirement.txt
```

### 3. Start The Development by Creating a New App
```bash
django-admin startapp app-name
```

### 4. Register the Packages and the Applications
Register the package you want to use and the application you've created on `settings.py` inside the `_main` directory. Then find the `INSTALLED_APPS` variable and insert the package name as the value.

### 5. Migrate the Database
```bash
python3 manage.py migrate
```

### 6. Create a New Initial User
```bash
python3 manage.py createsuperuser --email admin@example.com --username admin
```

## Models and Migrations
Create a model. This model is used to create a table in the database. The model I created is in: `snippets/models.py`

We use `makemigrations` and `migrate`. We will run this command to make the migration and migrate it:
```bash
python manage.py makemigrations snippets # this will create a migration file (snippets/migrations/0001_initial.py), the migration file generated from snippets/models.py
python manage.py migrate snippets # this will run the migration file
```

## Serializer Class
The documentation says that the **Serializer** is like **Django form** class. It creates a structure of data, provides a common data validation, and controls how the serializer should be displayed (such as `{'base_template': textarea.html}`).

> The path for a serializer I create `snippets/serializers.py`

## Model Serializer
`ModelSerializer` creates a shortcut to create serializer from a model. It set:
- An automatically determined set of fields.
- Simple default implementation for the `create()` and `update()` methods.

## Regular Djago Views using our Serializer
This will create API interface where we can access it in curl or web browser.
- I create a snippet views in `snippets/views.py`
- wire the views (routing) by creating `snippets/urls.py`
- wire up the root urlcof (routing) in the `tutorial/urls.py`, to include our snippet app's URLs.

> PS: See commit changes to learn more about this repository
