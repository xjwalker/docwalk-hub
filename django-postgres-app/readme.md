# Django app without installing Django/python on your local machine

## Define a dockerfile with the following content
```dockerfile
FROM python:3.9-alpine

# Set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

WORKDIR /app
COPY ./requirements.txt /app/requirements.txt

# Install dependencies
RUN apk add --no-cache --virtual .build-deps gcc musl-dev postgresql-dev libpq && apk add --no-cache bash
RUN pip install -r /app/requirements.txt

 First time script to create a new project
CMD test -d /app/my_project/ && rmdir /app/my_project || echo 'Directory does not exist'; django-admin startproject my_project && python my_project/manage.py runserver 0.0.0.0:8000
```

### then run
this command to build the image, create a django project using the container interpreter and run the server.

```bash
docker-compose up --build
```

### You will see new files 
now we update the docker file to use these new files instead of creating them every time we run the container

```dockerfile
FROM python:3.9-alpine

# Set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

COPY ./my_project /app/my_project
COPY ./requirements.txt /app/requirements.txt
WORKDIR /app/my_project

# Install dependencies
RUN apk add --no-cache --virtual .build-deps gcc musl-dev postgresql-dev libpq && apk add --no-cache bash
RUN pip install -r /app/requirements.txt

# Run the application
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
```

### And we rebuild the image
```bash
docker-compose up --build
```

### Last steps
In order to run the image we need 
- edit the setting.py to connect to postgres
- add '*' to the allowed hosts
- create a user model
- create a migration
- run the migrations
