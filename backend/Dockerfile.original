FROM python:3-slim
LABEL authors="Undervis, Thinker90"
ENV PYTHONUNBUFFERED 1
EXPOSE 8000

COPY requirements.txt requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

ENV MONGODB_HOST 0
ENV DJANGO_SUPERUSER_USERNAME admin
ENV DJANGO_SUPERUSER_EMAIL example@mail.ru
ENV DJANGO_SUPERUSER_PASSWORD 1234

COPY . /museum_quiz_backend
WORKDIR /museum_quiz_backend

RUN ["python", "manage.py", "makemigrations"]
RUN ["python", "manage.py", "migrate"]
RUN ["python", "manage.py", "createsuperuser", "--noinput"]

CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]