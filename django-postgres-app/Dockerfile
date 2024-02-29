FROM python:3.9-alpine

# Set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# First time comment this line
COPY ./my_project /app/my_project
COPY ./requirements.txt /app/requirements.txt

# Set work directory
WORKDIR /app/my_project

# Install dependencies
RUN apk add --no-cache --virtual .build-deps gcc musl-dev postgresql-dev libpq && apk add --no-cache bash
RUN pip install -r /app/requirements.txt

# First time script to create a new project
#CMD test -d /app/my_project/ && rmdir /app/my_project || echo 'Directory does not exist'; django-admin startproject my_project && python my_project/manage.py runserver

# Run the application
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
