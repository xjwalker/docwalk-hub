#

docker-compose up -d


docker exec -it <container-id> bash -c "django-admin startproject myproject"

docker exec -it <container-id> bash -c "pip install Django"

