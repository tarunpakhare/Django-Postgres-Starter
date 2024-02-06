# Django-Postgres-Starter
Starter Code for Django-Postgres Connection

Django-Postgres Connection

#In Django
In settings.py file make this change:
   DATABASES = {
    "default": {
        "ENGINE": "django.db.backends.postgresql",
        "NAME": "databaseName",
        "USER": "username",
        "PASSWORD": "password",
        "HOST": "127.0.0.1",
        "PORT": "5432",
    }
}

#In Postgres Shell
\l- to check the databases of superuser

CREATE DATABASE db_name;

CREATE USER userName WITH PASSWORD 'password';

\c db_name; #To switch to the database we made.

CREATE SCHEMA schema_name AUTHORIZATION username;

ALTER ROLE username SET client_encoding TO 'utf8';

ALTER ROLE username SET default_transaction_isolation TO 'read committed';

ALTER ROLE username SET timezone to 'UTC';

\dt - to see relations

#After this, we usually try migrating, but it will return a Permission Denied Error. To fix this run this command:

ALTER ROLE username IN DATABASE db_name set search_path=schema_name;

#Now makemigrations and migrate, it should work.
#/dt will not show any relations, we should therefore create a new session.
#To verify if the tables have been created, now we shall logout off the superuser using \q.
#Login again, this time in Database[postgres]: enter db_name, Username[postgres]: enter your username and password in password
\dt to view all the tables made in the db.
