# Configuration

Project configuration is loaded using [PyMS](https://github.com/python-microservices/pyms) package based on yml or json file.
Some example files are config.yml, config-docker.yml and tests/config-tests.yml or see [PyMS configuration](configuration.md)

## Documentation
The Microservice create a URL to inspect the Swagger documentation of the api in:

```
localhost:5000/[APPLICATION_ROOT]/ui/
```

This URL is set in your `config.yml`:

```yaml
pyms:
  config:
    DEBUG: false
    TESTING: false
    APP_NAME: Template
    APPLICATION_ROOT : "" <---
```

Our API Rest work with [connexion](http://connexion.readthedocs.io>). You can see connexion docs or the official
[Swagger documentation](https://swagger.io/specification/>) to add the syntax to your APIS and create your Swagger docs