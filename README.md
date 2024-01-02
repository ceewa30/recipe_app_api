docker-compose run --rm app sh -c "flake8"

docker-compose run --rm app sh -c "django-admin startproject app ."

docker-compose run --rm app sh -c "python manage.py startapp core" 

docker-compose run --rm app sh -c "python manage.py test"

docker-compose run --rm app sh -c "python manage.py wait_for_db"

# Database
# https://docs.dhjangoproject.com/en/3.2/reg/settings/#databases

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'HOST' : os.environ.get('DB_HOST'),
        'NAME': os.environ.get('DB_NAME'),
        'USER': os.environ.get('DB_USER'),
        'PASSWORD': os.environ.get('DB_PASS'),
    }
}