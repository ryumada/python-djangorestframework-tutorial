# djangorestframework quickstart
In this repository, I followed a Django full tutorial from the official site. Here is the link: https://www.django-rest-framework.org/tutorial/1-serialization/

This README provides the log what I've done with this repository. This repository also the result of my study in that tutorial.

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

## Models and Migrations
Create a model. This model is used to create a table in the database. The model I created is in: `snippets/models.py`

We use `makemigrations` and `migrate`. We will run this command to make the migration and migrate it:
```bash
python manage.py makemigrations snippets # this will create a migration file (snippets/migrations/0001_initial.py), the migration file generated from snippets/models.py
python manage.py migrate snippets # this will run the migration file
```
