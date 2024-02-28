FROM python:3.9-alpine

# Set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# First time comment this line
#COPY ./my_project /app/my_project

# Set work directory
WORKDIR /app

# Install dependencies
COPY ./requirements.txt /app/requirements.txt

RUN apk add --no-cache --virtual .build-deps gcc musl-dev postgresql-dev && apk add --no-cache bash
RUN pip install -r requirements.txt

# First time script to create a new project
#RUN test -d /app/my_project/ && rmdir /app/my_project || echo 'Directory does not exist'
#CMD django-admin startproject my_project
CMD test -d /app/my_project/ && rmdir /app/my_project || echo 'Directory does not exist'; django-admin startproject my_project && python my_project/manage.py runserver

# Run the application
#CMD ["python", "my_project/manage.py", "runserver"]
