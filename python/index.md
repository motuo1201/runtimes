---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-21"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}

# Python
{: #python_runtime}

The Python runtime on {{site.data.keyword.Bluemix}} is powered by the python_buildpack.
The python_buildpack provides a complete runtime environment for both Python 2 and Python 3 apps.
{: shortdesc}

The python_buildpack will be used if your app's root directory contains a requirements.txt file or a setup.py file.

## Starter application
{: #starter_application}

{{site.data.keyword.Bluemix_notm}} provides a Python starter application.  The Python starter application is a simple Python app that provides a template that you can use for your app. You can experiment with the starter app, and make and push changes to the {{site.data.keyword.Bluemix_notm}}
environment.  See [Using the starter applications](../common/starter_app_usage.html) for help with using the starter application.

## Runtime versions
{: #runtime_versions}

You can specify the version of Python to be used by your app by setting python-versionnumber in the runtime.txt file in the root of your application. For example:

```
python-3.6.1
```
{: codeblock}

When a version is not specified, version 2.7.14 is chosen by default.

### Available versions:
{: #available_versions}

The following Python versions are available in the
[Python buildpack](https://github.com/cloudfoundry/python-buildpack/releases/tag/v1.6.11)
currently installed in {{site.data.keyword.Bluemix_notm}}:

* 2.7.13
* 2.7.14
* 3.3.6
* 3.3.7
* 3.4.7
* 3.4.8
* 3.5.4
* 3.5.5
* 3.6.3
* 3.6.4

If your application requires a Python version that is not listed,
you can use the external
[Python buildpack](https://github.com/cloudfoundry/python-buildpack) to
deploy the app.

# rellinks
{: #rellinks notoc}
## general
{: #general notoc}
* [Cloud Foundry buildpack for Python](https://github.com/cloudfoundry/python-buildpack)
