configuration steps for mezzanine
=================================

Development setup
-----------------

create virtualenv, python3 possibly

    python3 -m venv ~/venv/mezza3
    source ~/venv/mezza3/bin/activate

    pip install mezzanine psycopg2
    mezzanine-project pgbrighton

On the postgres database create user and database for mezzanine.

CREATE USER usr_pgb WITH PASSWORD 'foo';

CREATE DATABASE db_pgb WITH OWNER usr_pgb;

edit pgbrighton/pgbrighton/local_settings.py
and configure the default database to use to postgresql

    "ENGINE": "django.db.backends.postgresql_psycopg2",
    "NAME": "db_pgb",
    "USER": "usr_pgb",
    "PASSWORD": "foo",
    "HOST": "localhost",
    "PORT": "5432",
    
initialise the database with

    cd pgbrighton
    python manage.py createdb
    
then run the server with 
    python manage.py runserver