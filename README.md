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
LASK_APP=app
FLASK_ENV=development (run development)
Flask run

---
## VS code
Code -n . —> opens directory on vscode
Code -r filename.ext to open file in vscode
