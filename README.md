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

## migrations
If in manager 

	python manage.py db init
	
	python manage.py db migrate 
	
	python manage.py db upgrade
  
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

Clean up:
- Remove stopped containers: docker-compose rm -f
- Remove dangling images (every week or so): docker rmi -f $(docker images -qf dangling=true)
