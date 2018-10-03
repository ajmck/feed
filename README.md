# AskOtago

Critic is fortunate enough to own the domain name for askotago.com and 
askotago.co.nz. So, we chucked a few questions up, but wouldn't it be far more
fun if you could Ask Otago anything...?

We've got text posts, comments, votes, and that's it.

This also doubles as a research project for SURV319 Geospatial Analysis and
Programming; by adding a location to a post, we can answer some important
questions. Which street has better chat, Castle or Hyde? Is AskOtago most
active during a long lecture? Is everything on this site fabricated in the
Critic office?

![](documentation/homepage.png)



# Project architecture

AskOtago is a Django project within a Docker container, to be run
with PostgresQL with GIS extensions. Currently the development version is
hosted on Heroku, at https://askotagodev.herokuapp.com

After the Django project has been set up to use a REST API, the site will be
accessed through a React frontend.

# Features

As of writing, we've got text posts, comments, voting, and location.

To flesh out the project (time pending), it should be converted to a REST API
(django-rest-framework) with a React (etc) frontend, with live updating (AJAX)
, spam filtering (see Azure Cognitive Library), and votes should be extended
to reacting with any emoji, and activity should be displayed on a map of
locations and landmarks (so raw point data isn't available to the end user).

To continue the project after the paper ends, picture uploading, a group
mechanism, and a native mobile app can be added, and the project can be
rebranded as the Otago Computer Science Society Feed.


# Build Instructions

(may not apply now it's a project with submodules)

* Install `docker-ce` and `docker-compose`
* Clone this repository
* Run `docker-compose build`
* Run `docker-compose up` - this will fail on the first run as the web
    container starts while Postgres is still initialising
* Run `docker-compose up -d` from repo directory
* Visit `127.0.0.1:8080/`
* Run `docker-compose down` to stop containers

If you need to exec in to the container, to run a command such as
`python3 manage.py createsuperuser`, gather the container ID with `docker ps`
(first few characters will do), and run `docker exec -it <container ID> sh`.

# IDE

* Set up Windows Subsystem for Linux
* Clone repository on to Windows drive so IDE can access files.
* (WSL) Create python virtualenv, and install pip requirements
* (WSL) Install libgdal-dev
* Connect PyCharm using virtualenv python as remote interpreter
* Set dockerfile as PyCharm's build configuration

# WDB debugger

To run docker-compose in a way that loads the WDB web debugger, changes will be required to the codebase first, but in principle it's a matter of running the command `docker-compose -f docker-compose.wdb.yml up`
