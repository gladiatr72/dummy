web: gunicorn config.wsgi:application
worker: celery worker --app=dummy.taskapp --loglevel=info
