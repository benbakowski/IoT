---

copyright:

years: 2017, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:important: .important}


# APIs
{: #api_overview}

<p>Essa coleção de documentação do {{site.data.keyword.Bluemix}} pertence ao plano de precificação Lite do {{site.data.keyword.iot_full}} e inclui informações básicas de introdução, referências de API e informações gerais de resolução de problemas. 
Para a documentação de recurso integral do {{site.data.keyword.iot_short_notm}}, consulte a [documentação do produto do {{site.data.keyword.iot_short_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) no IBM Knowledge Center. Mais informações sobre os vários planos podem ser localizadas em [{{site.data.keyword.iot_short_notm}} planos de serviço](/docs/IoT/plans_overview.html#plans_overview). 
</p>
{: important}

Várias APIs estão disponíveis para desenvolver código para dispositivos, gateways e aplicativos que se conectam ao {{site.data.keyword.iot_full}}.

As APIs HTTP são protegidas com autenticação básica HTTP. Quando você gera uma chave API usando o painel, são apresentados uma chave e um token de autenticação. Para obter mais informações sobre chaves de API e tokens, consulte [Conexão de chave de API ![Ícone de link externo](../../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/platform_authorization.html#api-key).


## Sobre APIs HTTP
{: #api_about}

Após o registro para sua própria organização, é fornecido um ID da organização de 6 caracteres a você, que é necessário no nome do host para quaisquer chamadas de API HTTP. A URL base para sua organização pode ser acessada no endereço a seguir:

https://<**orgId**>.internetofthings.ibmcloud.com/api/v0002

Para autenticar solicitações para a API do aplicativo, configure o nome do usuário para a chave API e a senha para o token de autenticação.

Para APIs do sistema de mensagens, use o endereço a seguir:

https://<**orgId**>.messaging.internetofthings.ibmcloud.com/api/v0002

## APIs HTTP
{: #api_http}

API do                     | Use para...       
------------- | -------------
[Administração da organização ![Ícone de link externo](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/orgAdmin.html){: new_window} | Configure uma organização (incluindo a criação e a exclusão de dispositivos), verifique o uso, consulte o status do serviço e diagnostique problemas de conexão do dispositivo.
[Segurança ![Ícone de link externo](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/security.html){: new_window} | Gerencie a autenticação e a autorização de usuários, chaves API e dispositivos.
[Gerenciamento de informações ![Ícone de link externo](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/info-mgmt.html){: new_window} |  Acessar dados do evento de dispositivo e também obter e atualizar a localização de dispositivo e obter informações meteorológicas para esse local.
[Gerenciamento de dados ![Ícone de link externo](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/state-mgmt.html){: new_window}   |   Organizar e integrar dados entrando e saindo do {{site.data.keyword.iot_short_notm}}.
[Gerenciamento de dispositivo ![Ícone de link externo](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/deviceMgmt.html){: new_window} | Interagir com dispositivos gerenciados usando o protocolo de gerenciamento de dispositivo.
[Sistema de mensagens ![Ícone de link externo](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/http-messaging.html){: new_window}   | Publicar eventos e enviar comandos usando HTTP.
[Gerenciamento de risco ![Ícone de link externo](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/riskmgmt.html){: new_window}   | Gerenciar as políticas e os relatórios de gerenciamento de risco.

## APIs HTTP de extensão
{: #api_extension}

API do                     | Use para...       
------------- | -------------
[Extensão AT&T ![Ícone de link externo](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-atnt.html){: new_window} | Administrar dispositivos AT&.
[Extensão Jasper  ![Ícone de link externo](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-jasper.html){: new_window} | Administrar dispositivos Jasper.
[Extensão Orange ![Ícone de link externo](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-orange.html){: new_window} | Visualizar dados do cartão SIM de dispositivos que estão conectados à sua organização do {{site.data.keyword.iot_short_notm}} e têm um cartão SIM da Orange instalado.

## APIs HTTP Beta
{: #api_beta}

API do                     | Use para...       
------------- | -------------
[ Restaurar dispositivos excluídos ![Ícone de link externo](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002-beta/restore-device-beta.html){: new_window}   | Se um dispositivo é excluído por engano, é possível restaurá-lo dentro de 14 dias.
