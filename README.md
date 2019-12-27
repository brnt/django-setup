# django-setup
Scripts to automate common Django setup tasks

## custom_django_project
This script sets up a Django project according to a few conventions, largely
based on the recommendations found here:

https://github.com/rdegges/deploydjango.com/blob/master/source/django_project_structure/setup.rst

Some of the conventions have emerged through my own trial-and-error over time.
The project structure is Heroku-centric. The script generates a folder structure and set of config files for a Django project. The resulting file tree looks like this:

	Procfile
	README.md
	bin
	└── runserver
	env
	└── {virtualenv stuff}
	requirements
	├── common.txt
	├── dev.txt
	├── prod.txt
	└── test.txt
	requirements.txt
	web
	├── .env
	├── manage.py
	└── {project name}
		├── __init__.py
		├── apps
		│   └── __init__.py
		├── asgi.py
		├── libs
		│   └── __init__.py
		├── middleware
		│   └── __init__.py
		├── settings
		│   ├── __init__.py
		│   ├── common.py
		│   ├── dev.py
		│   ├── prod.py
		│   └── test.py
		├── static
		├── urls.py
		└── wsgi.py

To set up Git and do initial push:

	git init
	git add .gitignore README.md web
	git commit -m 'Initial import'
	git remote add origin {URL}
	git push -u origin master

To push this project to Heroku, run the following command
from this folder (assuming you've already got the heroku remote set up:

	git subtree push --prefix web heroku master
