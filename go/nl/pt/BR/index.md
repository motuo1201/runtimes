---

copyright:
  years: 2015, 2018
lastupdated: "2017-06-21"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}


# Ir
{: #go_runtime}

O tempo de execução Go no {{site.data.keyword.Bluemix}} foi desenvolvido com o go_buildpack.
O go_buildpack fornece um ambiente de tempo de execução completo para apps Go.
{: shortdesc}

O go_buildpack é usado se seu aplicativo contém um arquivo chamado *.go.

## Aplicativo iniciador
{: #starter_application}

O {{site.data.keyword.Bluemix_notm}} fornece um aplicativo iniciador do Go.  O aplicativo iniciador do Go é um app Go simples que fornece
um modelo que você pode usar para seu app. É possível experimentar o app iniciador e fazer e enviar mudanças por push para o ambiente do {{site.data.keyword.Bluemix_notm}}. Veja [Usando os aplicativos iniciadores](../common/starter_app_usage.html) para obter ajuda sobre o uso do aplicativo iniciador.

## Versões de runtime
{: #runtime_versions}

É possível especificar a versão do Go a ser usada por seu app, configurando a propriedade GoVersion no arquivo
Godeps/Godeps.json na raiz de seu aplicativo. Por exemplo:

```
{
	"ImportPath": "gohelloworld",
	"GoVersion": "go1.8.3",
	"Deps": []
}
```
{: codeblock}
Para obter mais informações, veja [godep](https://github.com/tools/godep){: new_window}.

Quando uma versão não for especificada, a versão 1.8.3 será escolhida por padrão.

### Versões disponíveis:
{: #available_versions}

As seguintes versões do Go estão disponíveis no [buildpack Go](https://github.com/cloudfoundry/go-buildpack/releases/tag/v1.8.6){: new_window}
atualmente instalado no {{site.data.keyword.Bluemix_notm}}:

* 1.6.3
* 1.6.4
* 1.7.5
* 1.7.6
* 1.8.1
* 1.8.3

Se o seu app requer uma versão do Go não listada,
é possível usar um [buildpack Go](https://github.com/cloudfoundry/go-buildpack.git){: new_window} externo para implementar o aplicativo.

# rellinks
{: #rellinks notoc}
## geral
{: #general notoc}

* [GoLang](http://golang.org/){: new_window}
* [Buildpack do Cloud Foundry para Go](https://github.com/cloudfoundry/go-buildpack){: new_window}
