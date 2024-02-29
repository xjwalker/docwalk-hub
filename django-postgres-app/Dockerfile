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
