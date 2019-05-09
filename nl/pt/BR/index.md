---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-05"

keywords: Watson IoT Platform, gateway devices, Watson IoT Platform service plans

subcollection: iot-platform

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:important: .important}


# Tutorial Introdução
{: #getting-started-with-iotp .task}

<p>Essa coleção de documentação do {{site.data.keyword.cloud}} pertence ao plano de precificação Lite do {{site.data.keyword.iot_full}} e inclui informações básicas de introdução, referências de API e informações gerais de resolução de problemas. 
Para a documentação de recurso integral do {{site.data.keyword.iot_short_notm}}, consulte a [documentação do produto do {{site.data.keyword.iot_short_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) no IBM Knowledge Center. Mais informações sobre os vários planos podem ser localizadas em [{{site.data.keyword.iot_short_notm}} planos de serviço](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview). 
</p>
{: important}

Neste tutorial de introdução do {{site.data.keyword.iot_full}}, conectamos
um dispositivo IoT ao {{site.data.keyword.iot_short_notm}}.
{:shortdesc}

## Sobre essa Tarefa
{: #index-about .sectiontitle}  

Para poder iniciar o recebimento de dados de seus dispositivos IoT, deve-se
conectá-los ao {{site.data.keyword.iot_full}}. A conexão de um dispositivo ao {{site.data.keyword.iot_short_notm}} envolve registrar o dispositivo com o {{site.data.keyword.iot_short_notm}} e, em seguida, usar as informações de registro para configurar o dispositivo para se conectar ao {{site.data.keyword.iot_short_notm}}.

## Antes de iniciar
{: #index-byb .sectiontitle}  

Antes de poder começar a usar o {{site.data.keyword.iot_short_notm}}, você precisará do seguinte:  
* Uma [conta do IBM Cloud ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://cloud.ibm.com/registration/){: new_window}.
* Uma instância do {{site.data.keyword.iot_short_notm}}.  
É possível criar uma instância do {{site.data.keyword.iot_short_notm}} diretamente na [página do {{site.data.keyword.iot_short_notm}} no Catálogo de serviços do IBM Cloud ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/catalog/services/internet-of-things-platform/){:new_window}.  
* Um dispositivo que atende aos requisitos a seguir:  
  *	Seu dispositivo deve poder se comunicar usando os protocolos HTTP ou MQTT.
  * As mensagens do dispositivo devem se adequar aos requisitos de carga útil da mensagem do {{site.data.keyword.iot_short_notm}}.  
Para obter mais informações, consulte [Desenvolvendo dispositivos no Watson IoT Platform ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/devices/device_dev_index.html){: new_window}.

Explore as opções a seguir, dependendo de sua situação:

 |  |   O serviço é implementado | O serviço não é implementado
 | -------------| ------------- | -------------
  |**Eu tenho um dispositivo para conectar** | Siga o processo que está descrito neste tópico. | Explore a conexão de dispositivo no [Play
com o {{site.data.keyword.iot_short_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo") ](http://discover-iot.eu-gb.mybluemix.net/?cm_mc_uid=44491599487314618721024&cm_mc_sid_50200000=1462798151#/play){:new_window}.
  |**Eu não tenho um dispositivo para conectar** | [Simular dados do dispositivo](/docs/services/IoT?topic=iot-platform-sim_device_data#sim_device_data) ou [Conectar seu smartphone ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://discover-iot.eu-gb.mybluemix.net/?cm_mc_uid=44491599487314618721024&cm_mc_sid_50200000=1462798151#/play/device/smartphone){:new_window}. | Introdução ao [Watson IoT Platform Starter](https://cloud.ibm.com/docs/IoT-starter?topic=iot-starter-gettingstartedtemplate#gettingstartedtemplate){:new_window}.



## Etapa 1: registrar seu dispositivo
{: #index-step1 .sectiontitle}  
O registro de um dispositivo envolve classificar o dispositivo como um tipo de dispositivo, dando ao dispositivo um nome e fornecendo informações do dispositivo. Em seguida, você fornece um token de conexão ou aceita um token que é gerado pelo {{site.data.keyword.iot_short_notm}}.

**Dica:** é possível registrar seus dispositivos, um de cada vez, por meio do [painel do {{site.data.keyword.iot_short_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://internetofthings.ibmcloud.com){: new_window} ou usar a [API do Watson IoT Platform ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/org-admin.html#!/Device_Bulk_Configuration/post_bulk_devices_add){: new_window} para incluir vários dispositivos.

Para incluir um dispositivo a partir do painel do {{site.data.keyword.iot_short_notm}}:
1. No console do {{site.data.keyword.cloud_notm}}, clique em **Ativar** na página de detalhes do serviço {{site.data.keyword.iot_short_notm}}.

    O console da web do {{site.data.keyword.iot_short_notm}} é aberto em uma nova guia do navegador na URL a seguir:

    ```
    https://org_id.internetofthings.ibmcloud.com/dashboard/#/overview
    ```

    Em que *org_id* é o ID de sua organização do {{site.data.keyword.iot_short_notm}}.

2. No painel Visão geral, na área de janela de menu, selecione **Dispositivos** e, em seguida, clique em **Incluir dispositivo**.

3. Crie um tipo de dispositivo para o dispositivo que você está incluindo.

    Cada dispositivo conectado ao {{site.data.keyword.iot_short_notm}} deve estar associado a um tipo de dispositivo. Tipos de dispositivos são grupos de dispositivos que compartilham características.

    1. Clique em **Criar tipo de dispositivo**.
    2. Insira um nome de dispositivo, como `my_device_type`, e uma descrição para o tipo de dispositivo.

        > ** Nota:** o nome do tipo de dispositivo não deve ter mais de 36 caracteres e pode conter somente caracteres alfanuméricos (a-z, A-Z, 0-9) e qualquer um dos caracteres a seguir: `_`, `.` e `-`.

    3. Opcional: insira atributos e metadados de tipo de dispositivo.

        Será possível incluir e editar atributos e metadados posteriormente.
        {: tip}

4. Clique em **Avançar** para iniciar o processo de incluir seu dispositivo com o tipo de dispositivo selecionado.

5. Insira um ID do dispositivo, por exemplo `my_first_device`.

    O ID do dispositivo é usado para identificar o dispositivo no painel do {{site.data.keyword.iot_short_notm}} e também é um parâmetro necessário para conectar seu dispositivo ao {{site.data.keyword.iot_short_notm}}.

    > ** Nota:** o nome do tipo de dispositivo não deve ter mais de 36 caracteres e pode conter somente caracteres alfanuméricos (a-z, A-Z, 0-9) e qualquer um dos caracteres a seguir: `_`, `.` e `-`.

    Para dispositivos conectados à rede, o ID do dispositivo poderia ser o endereço MAC do dispositivo sem dois-pontos separando.

5. Clique em **Avançar** para concluir o processo.

6. Forneça um token de autenticação ou aceite um token gerado automaticamente. Se você optar por criar seu próprio token, certifique-se de que ele tenha entre 8 e 36 caracteres e consista apenas em caracteres alfanuméricos e os seguintes caracteres: `_`, `.`, `!`, `&`, `a`, `?`, `\ *`, `+`, `(`, `)` e `-`.

    O token não deve conter sequências de caracteres repetidos, palavras de dicionário, nomes de usuário ou outras sequências predefinidas.

7. Verifique se as informações de resumo estão corretas e, em seguida, clique em **Incluir** para incluir a conexão.

8. Na página de informações sobre o dispositivo, copie e salve os detalhes a seguir:

    * ID de Organização
    * Tipo do Dispositivo
    * ID do dispositivo
    * Método de Autenticação
    * Token de Autenticação

    Você precisará do ID da organização, Tipo de Dispositivo, ID do dispositivo e Token de autenticação para configurar seu dispositivo para se conectar ao {{site.data.keyword.iot_short_notm}}.

## Etapa 2: conectar seu dispositivo ao {{site.data.keyword.iot_short_notm}}
{: #index-step2 .sectiontitle}  

Após registrar um dispositivo com o {{site.data.keyword.iot_short_notm}}, será possível usar as informações de registro para conectar o dispositivo e iniciar o recebimento de dados do dispositivo.

**Dica:** há orientações de conexão disponíveis para alguns dispositivos comumente usados em [Orientações de conexão do dispositivo ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://developer.ibm.com/recipes/tutorials/category/internet-of-things-iot/){: new_window} em IBM.com.

Para conectar um dispositivo ao {{site.data.keyword.iot_short_notm}}:
1. Configure seu dispositivo para o sistema de mensagens MQTT e autentique usando o ID da organização, Tipo de dispositivo, ID do dispositivo e Token de autenticação.

2. Envie mensagens do dispositivo para sua organização do {{site.data.keyword.iot_short_notm}} usando o protocolo MQTT.

    As informações a seguir são necessárias ao conectar seu dispositivo:

    * URL: *org_id*.messaging.internetofthings.ibmcloud.com

      Em que *org_id* é o ID de sua organização do {{site.data.keyword.iot_short_notm}}.

    * 1Port:
      * 1883
      * 8883 (criptografada)
      * 443 (soquetes da web)
    * ID do dispositivo: d:_org_id:device_type:device_id_
    * Nome do usuário: use-token-auth
    * Senha: _Token de autenticação_
    * Formato do tópico de evento: iot-2/evt/_event_id/fmt/format_string_

      Em que _event_id_ especifica o nome do evento que é mostrado no {{site.data.keyword.iot_short_notm}} e _format_string_ é o formato do evento, como JSON.

    * Formato da mensagem: JSON

  Para obter mais informações, consulte [Conectividade do MQTT para dispositivos ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/devices/mqtt.html){:new_window}.


## O que vem a seguir  
{: #index-related .sectiontitle}

Estenda os recursos de análise de dados criando e conectando os seus próprios apps para consumir dados do dispositivo.
- Para obter mais informações sobre como conectar tipos de dispositivo específicos ao {{site.data.keyword.iot_short_notm}}, veja [Orientações do developerWorks ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://developer.ibm.com/recipes/tutorials/category/internet-of-things-iot/){:new_window}.
- Verifique as [bibliotecas do cliente ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/iot_platform_client_lib.html){:new_window} para ferramentas para construir código para integrar e conectar os seus dispositivos e apps.
- Explore a [Documentação da API do {{site.data.keyword.iot_short_notm}} ](/docs/services/IoT?topic=iot-platform-api_overview#api_overview).
- [Conecte um serviço {{site.data.keyword.cloudantfull}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/cloudant_connector.html){:new_window} ao {{site.data.keyword.iot_short_notm}} para armazenar dados históricos do dispositivo.
- Para se aproveitar do [conjunto de recursos integral do {{site.data.keyword.iot_short_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html){:new_window}, é possível comprar um dos planos do Connection and Analytics Service e, em seguida, migrar o seu ambiente existente.

Para migrar planos, entre em contato com seu representante {{site.data.keyword.IBM}} ou levante um chamado de suporte.

Um conjunto mais detalhado de guias de introdução e aplicativos de amostra que demonstram os conceitos básicos de desenvolvimento de um sistema de protótipo IoT de ponta a ponta e pronto para produção com o {{site.data.keyword.iot_short_notm}} também está disponível na documentação do produto {{site.data.keyword.iot_short_notm}} no IBM Knowledge Center. Se você for um desenvolvedor que é novo para trabalhar com o {{site.data.keyword.iot_short_notm}}, use os processos passo a passo na seção [Guias de introdução ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/getting_started/getting-started-iot-overview.html#getting-started){:new_window}.
