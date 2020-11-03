# Installation

## Python Version
We recommend using the latest version of Python 3. PyMS supports Python 3.6 and newer and PyPy.

## Install PyMS

**Installing pyms with all dependencies**
```
pip install py-ms[all]
```
* Installing minimun dependencies
```
pip install py-ms
```
* Installing request dependencies
```
pip install py-ms[request]
```
* Installing swagger dependencies
```
pip install py-ms[swagger]
```
* Installing metrics dependencies
```
pip install py-ms[metrics]
```
* Installing trace dependencies
```
pip install py-ms[trace]
```

## Install with virtualenv and requirements.txt

Create a [virtualenv](https://virtualenv.pypa.io/en/latest/)

```
virtualenv --python=python[3.6|3.7|3.8] venv
source venv/bin/activate
```

Add in your requirements.txt:

```
py-ms[all|metrics|trace]==[VERSION]
```

In example:

```
py-ms[all]>=2.7.0
```

and then install with

```
pip install -r requirements.txt
```

## Install with pipenv and Pipfile

Create a [pipenv](https://pipenv-es.readthedocs.io/) environment

```
pipenv install
```

Or install PyMS with the command:

```
pipenv install py-ms[all]>=2.7.0
```

Or add PyMS in your Pipfile:

```toml
[[source]]
name = "pypi"
url = "https://pypi.org/simple"
verify_ssl = true

[dev-packages]

[packages]
py-ms = {extras = ["all"],version = "==2.6.1"}
```

## Next Steps

See [Quickstart](quickstart.md) to continue with this tutorial