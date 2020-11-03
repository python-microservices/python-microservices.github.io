# Tutorial 3: Testing with Pytest and PyMS

Testing a microservice with PyMS is very similar to a Flask Application.

## Create App Pattern

The recommended way to start is using [Create App Pattern](https://flask.palletsprojects.com/en/1.1.x/patterns/appfactories/).
 Using PyMS is like Flask:

```python
from pyms.flask.app import Microservice

def create_app():
    ms = Microservice(path=__file__)
    return ms.create_app()
```

## Conftest.py and Pytest

Then, you can use these functions in your conftest.py with Pytest:

### Config environment

PyMS needs the environment variable `PYMS_CONFIGMAP_FILE` to look for the configuration file, is recommended
to create a specific config file to testing:

```python
import os
def conf_environment():
    if not os.environ.get("PYMS_CONFIGMAP_FILE", False):
        os.environ["PYMS_CONFIGMAP_FILE"] = os.path.join(os.path.dirname(os.path.abspath(__file__)), "config-tests.yml")
```

### Initialize Flask

Create an app object to use in tests

```python
import pytest
@pytest.fixture(scope="session")
def app():
    conf_environment()
    app = create_app()
    return app
```

### Initialize Flask

Create Flask testing client

```python
@pytest.fixture(scope="module")
def client(app, db):
    """A test client for the app."""
    return app.test_client()
```

### Extra: url of your tests

Get the url to use in tests

```python
@pytest.fixture(scope="module")
def base_url(app):
    """Base url of the service."""
    return app.config["APPLICATION_ROOT"]()
```

### Ready to testing your code

With this configuration, you are ready to create your own tests with PyMS:

```python
def test_list_actors(client, base_url):
    response = client.get('{base_url}healthcheck'.format(base_url=base_url))
    assert 200 == response.status_code
```

As you can see, is very similar to a normal Flask application :)