---

copyright:
  years: 2015, 2018
lastupdated: "2018-06-21"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}


# Tomcat
{: #tomcat_runtime}

O tempo de execução do Tomcat no {{site.data.keyword.Bluemix}} foi desenvolvido com o java_buildpack.
{: shortdesc}

Para usar o tempo de execução do Tomcat no {{site.data.keyword.Bluemix_notm}}, deve-se especificar o java_buildpack com a opção -b. Por exemplo:

```
ibmcloud cf push &lt;myApp&gt; -p &lt;pathToMyApp&gt; -b java_buildpack
```

Para obter mais informações sobre o tempo de execução do Tomcat, veja o
[leia-me do java-buildpack](https://github.com/cloudfoundry/java-buildpack/blob/master/README.md).

## Aplicativo iniciador
{: #starter_application}

O {{site.data.keyword.Bluemix_notm}} fornece um aplicativo iniciador do Tomcat.  O aplicativo iniciador do Tomcat é um app Tomcat simples que fornece um modelo que pode ser usado. É possível experimentar o app iniciador, fazendo e enviando mudanças por push para o ambiente
{{site.data.keyword.Bluemix_notm}}. Consulte [Usando os aplicativos iniciadores](../common/starter_app_usage.html) para obter ajuda sobre o uso
do aplicativo iniciador.

## Versões de runtime
{: #runtime_versions}

É possível mudar a versão do Tomcat a ser usada por seu app com a variável de ambiente JBP_CONFIG_TOMCAT.
É possível mudar a versão do Java a ser usada por seu app com a variável de ambiente JBP_CONFIG_OPEN_JDK_JRE.
Ambos podem ser especificados no arquivo manifest do aplicativo.  Por exemplo:
```
    env:
        JBP_CONFIG_TOMCAT: '{tomcat: { version: 8.0.+ }}'
        JBP_CONFIG_OPEN_JDK_JRE: '{jre: { version: 1.8.0_+ }}'
```
{: codeblock}
A versão atual do java_buildpack é v3.19, que contém o Tomcat padrão versão 8.0.45 e a versão Java padrão 1.8.0_141.
Para obter mais informações veja [Liberações do java-buildpack](https://github.com/cloudfoundry/java-buildpack/releases/tag/v3.13).

## Redirecionamento de HTTPS
{: #https_redirect}

O tempo de execução do Tomcat pode ser configurado para confiar em proxies internos do
{{site.data.keyword.Bluemix_notm}} e permitir o redirecionamento de tráfego HTTP para HTTPS (SSL).
Para fazer isso, modifique o arquivo server.xml,
configurando o elemento RemoteIpValve Valve com as opções internalProxies e protocolHeader.

O tempo de execução Tomcat
[server.xml](https://github.com/cloudfoundry/java-buildpack/blob/master/resources/tomcat/conf/server.xml)
incluído no buildpack configura somente o protocolHeader do elemento RemoteIpValve Valve por padrão.  Para redirecionar o tráfego
HTTP para HTTPS no {{site.data.keyword.Bluemix_notm}}, configure o elemento RemoteIpValve no seu server.xml customizado como
segue:

```
 <Valve className='org.apache.catalina.valves.RemoteIpValve' protocolHeader='x-forwarded-proto' internalProxies='.*' />
```
{: codeblock}

Mais opções de configuração para o RemoteIpValve podem ser localizadas na
[documentação do Tomcat ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://tomcat.apache.org/tomcat-8.0-doc/api/org/apache/catalina/valves/RemoteIpValve.html).

# rellinks
{: #rellinks notoc}
## geral
{: #general notoc}
* [java-buildpack](https://github.com/cloudfoundry/java-buildpack)
