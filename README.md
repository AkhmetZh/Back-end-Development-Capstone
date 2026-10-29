# Back-end-Development-Capstone

Django main application for the Static Hearts band website. It shows songs
and photos fetched from two microservices and concerts stored in its own database.

## Pages

- / : home page
- /songs/ : list of songs with a lyrics modal dialog
- /photos/ : photo gallery (with a page for a single photo)
- /concerts/ : concert dates
- /admin/ : Django admin

## Related services

- Songs service: https://github.com/AkhmetZh/Back-End-Development-Songs
- Pictures service: https://github.com/AkhmetZh/Back-End-Development-Pictures

## Configuration

Service addresses are set with environment variables:

- SONGS_SVC (default: http://localhost:5000)
- PICTURES_SVC (default: http://localhost:3000)

## Run locally

    python -m venv venv
    venv\Scripts\Activate.ps1
    pip install -r requirements.txt
    python manage.py makemigrations songs photos concerts
    python manage.py migrate
    python manage.py loaddata concerts
    python manage.py createsuperuser
    python manage.py runserver 0.0.0.0:8000

## Docker and Kubernetes

    docker build -t djangoserver:1 .
    kubectl apply -f deployment.yaml
    kubectl port-forward deployment.apps/djangoserver 8000:8000
