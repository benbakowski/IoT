---

copyright:

years: 2017, 2019
lastupdated: "2019-04-16"

keywords: own organization, Extension HTTP APIs, API Use, AT&T Extension, Administer AT&T

subcollection: iot-platform

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:tip: .tip}
{:pre: .pre}
{:important: .important}


# APIs
{: #api_overview}

<p>Essa coleção de documentação do {{site.data.keyword.cloud}} pertence ao plano de precificação Lite do {{site.data.keyword.iot_full}} e inclui informações básicas de introdução, referências de API e informações gerais de resolução de problemas. 
Para a documentação de recurso integral do {{site.data.keyword.iot_short_notm}}, consulte a [documentação do produto do {{site.data.keyword.iot_short_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) no IBM Knowledge Center. Mais informações sobre os vários planos podem ser localizadas em [{{site.data.keyword.iot_short_notm}} planos de serviço](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview). 
</p>
{: important}

Várias APIs estão disponíveis para desenvolver código para dispositivos, gateways e aplicativos que se conectam ao {{site.data.keyword.iot_full}}.

As APIs de HTTP são protegidas pela autenticação básica de HTTP. Quando você gera uma chave API usando o painel, são apresentados uma chave e um token de autenticação. Para obter mais informações sobre chaves de API e tokens, consulte [Conexão de chave de API ![Ícone de link externo](../../../icons/launch-glyph.svg)](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/platform_authorization.html#api-key){: new_window}.


## Sobre APIs HTTP
{: #api_about}

Cada organização do {{site.data.keyword.iot_short_notm}} é identificada por um ID de organização de 6 caracteres, necessário no nome do host para qualquer chamada de API de HTTP.   

### Docs API
{: #api_docs}

Para visualizar docs de API, acesse a página [APIs de REST do IBM Watson IoT Platform ![Ícone de link externo](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/index.html){: new_window}. Nessa página inicial, é possível acessar a documentação das APIs disponíveis do {{site.data.keyword.iot_short_notm}}.

### Docs da API interativa

Para visualizar e usar os docs da API interativa, a URL base da sua organização pode ser acessada no seguinte endereço:

`https://<orgId>.internetofthings.ibmcloud.com/docs/index.html`

Nessa página inicial, é possível acessar a documentação das APIs disponíveis do {{site.data.keyword.iot_short_notm}}. Para ter acesso para executar as chamadas de API diretamente da documentação, deve-se estar autorizado.

Para ser autorizado automaticamente, conclua as etapas a seguir:

1. Efetue login no painel do {{site.data.keyword.iot_short_notm}}.
2. No mesmo navegador, abra uma nova guia e acesse a página inicial dos docs da API interativa.

Se não efetuou login no painel do {{site.data.keyword.iot_short_notm}}, conclua as etapas a seguir:

1. Acesse a página inicial dos docs da API interativa.
2. Selecione `Autorizar`.
3. Na caixa `Autorizações disponíveis`, configure o nome de usuário para a chave de API e a senha para o token de autenticação. Selecione `Autorizar`.
4. Feche a caixa `Autorizações disponíveis`. **Importante:** não selecione `Efetuar logout`.

Depois de estar autorizado, acesse chamadas de API específicas e use o botão `Experimentar` para executar as chamadas de API diretamente da documentação.

<!-- To authenticate requests to the application API, set the username to the API key and the password to the authentication token. -->
