# Service Discovery

PyMS support at this moment this service discovery

- Consul
- Eureka (TODO)
- Kubernetes (TODO)


## Consul
This service use [Consul Client
Library](https://github.com/python-microservices/consulate) to connect to [Consul](https://www.consul.io/)

```yaml
pyms:
  services:
    service_discovery:
      service: "consul"
      host: "localhost"
      autoregister: true
  config:
    DEBUG: true
    TESTING: false
    APP_NAME: "Python Microservice"
    APPLICATION_ROOT: ""
```

Check your local configuration with Docker. Run:

```shell
docker run -d --net=host -e 'CONSUL_LOCAL_CONFIG={"leave_on_terminate": true, "enable_script_checks": true}' consul
```

Open `http://localhost:8500/` to check if Consul is up. If it's ok, when you run your microservice with
`autoregister: true` parameter, you will see in Consul your microservice like this image:

![Consul](/imgs/consul_example.png)

## Consulate client

You can use all [consulate](https://github.com/python-microservices/consulate) options with 
`ms.service_discovery.client` or `current_app.ms.service_discovery.client`. In example:

```python
ms.service_discovery.client.agent.checks()
```

See [official docs](https://consulate.readthedocs.io/) for more information.

## Create your own Service Discovery

Instead of define a service keyword, you can point to a class in your proyect that inherit from ServiceDiscoveryBase 
(see example above)

```yaml
pyms:
  services:
    service_discovery:
      service: "myproject.servicesdiscovery_file.MySvcDiscovery"
      host: "localhost"
      autoregister: true
  config:
    DEBUG: true
    TESTING: false
    APP_NAME: "Python Microservice"
    APPLICATION_ROOT: ""
```


Under `myproject/servicesdiscovery_file.py`:

```python
from pyms.flask.services.service_discovery import ServiceDiscoveryBase


class ServiceDiscoveryConsulBasic(ServiceDiscoveryBase):
    def register_service(self, id_app, host, port, healtcheck_url, app_name):
        headers = {"Content-Type": "application/json; charset=utf-8"}
        data = {
            "id": app_name + "-" + id_app,
            "name": app_name,
            "check": {"name": "ping check", "http": healtcheck_url, "interval": "30s", "status": "passing"},
        }
        response = requests.put(
            "http://{host}:{port}/v1/agent/service/register".format(host=host, port=port),
            data=json.dumps(data),
            headers=headers,
        )
        if response.status_code != 200:
            raise Exception(response.content)
```
