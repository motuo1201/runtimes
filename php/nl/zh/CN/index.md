---

copyright:
  years: 2015, 2018
lastupdated: "2018-06-21"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}

# PHP
{: #php_runtime}

{{site.data.keyword.Bluemix}} 上的 PHP 运行时由 php_buildpack 提供支持。php_buildpack 为 PHP 应用程序提供了一个完整的运行时环境。
{: shortdesc}

在以下情况下，将使用 php_buildpack：
* 您的应用程序包含 composer.json 文件，或者
* 您的应用程序包含 *.php 文件，或者
* 您的应用程序在其 [options.json](https://docs.cloudfoundry.org/buildpacks/php/gsg-php-config.html) 文件中定义了 ${WEBDIR} 变量，该变量设置为您应用程序内的一个现有目录。

## 入门模板应用程序
{: #starter_application}

{{site.data.keyword.Bluemix}} 提供了 PHP 入门模板应用程序。PHP 入门模板应用程序是一个简单的 PHP 应用程序，它提供了一个可供您的应用程序使用的模板。您可以尝试使用该入门模板应用程序来进行更改并将更改推送到 {{site.data.keyword.Bluemix}} 环境。有关使用入门模板应用程序的帮助，请参阅[使用入门模板应用程序](../common/starter_app_usage.html)。

## 在应用程序的所有页面上强制实施 HTTPS
{: #enforce_https}

当应用程序使用 Apache 在 {{site.data.keyword.Bluemix_notm}} 上运行时，要在应用程序的所有页面上强制使用 HTTPS 而非 HTTP，需要对“.htaccess”文件进行如下更改。仅当在 {{site.data.keyword.Bluemix_notm}} 中运行时，此规则适用于不是使用 HTTPS 发出的所有请求。

```
RewriteCond %{HTTP:X-Forwarded-Proto} !=https [NC]
RewriteCond %{ENV:BLUEMIX_REGION} !^$
RewriteRule (.*) https://%{HTTP_HOST}%{REQUEST_URI} [R=301,L]
```

## 运行时版本
{: #runtime_versions}

您可以在 composer.json 文件中为您的应用程序指定要使用的 PHP 版本。例如：

```
{
    "require": {
        "php": "7.0.*"
    }
}
```
{: codeblock}
有关更多信息，请参阅 [Composer Package links ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://getcomposer.org/doc/04-schema.md#package-links)。


如果未指定版本，缺省情况下会选择 V5.6.31。

### 可用版本：
{: #available_versions}

{{site.data.keyword.Bluemix}} 中当前安装的 [PHP buildpack](https://github.com/cloudfoundry/php-buildpack/releases/tag/v4.3.27) 内提供了以下 PHP 版本：

* 5.6.30
* 5.6.31
* 7.0.20
* 7.0.21
* 7.1.6
* 7.1.7

如果您应用程序所需的 PHP 版本没有列在上述列表中，那么可以使用外部 [PHP buildpack](https://github.com/cloudfoundry/php-buildpack.git) 来部署应用程序。
