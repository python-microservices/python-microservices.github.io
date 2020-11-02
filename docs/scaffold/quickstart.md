# Installation

### Clone the repository

```bash
git clone git@github.com:purwowd/microservices-scaffold.git
cd microservices-scaffold
```

### Install with virtualenv
```bash
virtualenv --python=python[3.6|3.7|3.8] venv
source venv/bin/activate
pip install -r requirements.txt
```

### Install with pipenv
```bash
pip install pipenv
pipenv install
```

### Install on MacOS
```bash
virtualenv -p python3 venv
source venv/bin/activate
pip3 install -r requirements.txt
python manage.py runserver
```

#### Advantages over plain pip and requirements.txt
[Pipenv](https://pipenv.readthedocs.io/en/latest/) generates two files: a `Pipfile`and a `Pipfile.lock`.
* `Pipfile`: Is a high level declaration of the dependencies of your project. It can contain "dev" dependencies (usually test related stuff) and "standard" dependencies which are the ones you'll need for your project to function
* `Pipfile.lock`: Is the "list" of all the dependencies your Pipfile has installed, along with their version and their hashes. This prevents two things: Conflicts between dependencies and installing a malicious module.

For a more in-depth explanation please refer to  the [official documentation](https://pipenv.readthedocs.io/en/latest/).

## Run your python script
```bash
python manage.py runserver
```

## Check the result

Your default endpoints will be in this url:
```bash
http://127.0.0.1:5000/films
http://127.0.0.1:5000/actors
```

This URL is set in your `config.yml`:

```yaml
pyms:
  config:
    DEBUG: false
    TESTING: false
    APP_NAME: Template
    APPLICATION_ROOT : "" # <!---
```

You can acceded to a [swagger ui](https://swagger.io/tools/swagger-ui/) in the next url:
```bash
http://127.0.0.1:5000/ui/
```

This PATH is set in your `config.yml`:

```yaml
pyms:
  services:
    swagger:
      path: "swagger"
      file: "swagger.yaml"
      url: "/ui/" # <!---
```

## Template

You can create your own project from template: [github.com/python-microservices/microservices-template](https://github.com/python-microservices/microservices-template)