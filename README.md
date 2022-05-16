# notes
---
## Postgres server: 
Start | Stop | Status postres db

pg_ctl -D /usr/local/var/postgres start

Kill PID ps -fA | grep python

---
## psql DB
Createdb name

\L list databases

\q exit (quit)

## DB
docker-compose exec website longfields db
docker-compose exec website longfields db reset --with-testdb

## migrations
If in manager 

	python manage.py db init
	
	python manage.py db migrate 
	
	python manage.py db upgrade

docker-compose exec website alembic current
docker-compose exec website alembic revision -m "create foo table"
docker-compose exec website alembic upgrade head (last one)
docker-compose exec website alembic downgrade -1 (to previous state)
docker-compose exec website alembic history --verbose
  
---
## Requirements
install requirements:

pip install -r requirements.txt

Create requirements:
pip freeze > requirements.txt

---
## Environments
Create env

python3 -m venv env

Activate env

source fyyur_env/bin/activate

Deactivate …deactivate

---
## Flask app
FLASK_APP=app

FLASK_ENV=development (run development)

Flask run

---
## VS code
Code -n . —> opens directory on vscode

Code -r filename.ext to open file in vscode

---
## Heroku deployment
make sure to:

	have setup.sh (touch setup.sh)
	
	install gunicorn (pip install gunicorn)
	
	create Procfile (touch Procfile) --> web: gunicorn app:app
	
	run migrations

heroku create name_of_your_app

git remote add heroku heroku_git_url

heroku addons:create heroku-postgresql:hobby-dev --app name_of_your_application

heroku config --app name_of_your_application

git push heroku master

heroku run python manage.py db upgrade --app name_of_your_application

---
Access heroku db for direct changes
heroku pg:psql

---
# DOCKER

DOCKER: (docker needs to be started)
- Build image: docker-compose up --build
- Stop app: docker-compose stop (also stops containers)
- Start it again: docker-compose up

CLI:
- testing: docker-compose exec website longfields test
- coverage testing: docker-compose exec website longfields cov
- styling check: docker-compose exec website longfields flake8

Clean up:
- Remove stopped containers: docker-compose rm -f
- Remove dangling images (every week or so): docker rmi -f $(docker images -qf dangling=true)

Remove volumes:
- docker-compose down --volumes 

Postgres:
	if: PostgreSQL Database directory appears to contain a database; Skipping initialization
		- : docker-compose down --volumes
