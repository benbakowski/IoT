---

copyright:
  years: 2015, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:important: .important}

# Integrações de serviços externos
{: #ref-index}

<p>Essa coleção de documentação do {{site.data.keyword.Bluemix}} pertence ao plano de precificação Lite do {{site.data.keyword.iot_full}} e inclui informações básicas de introdução, referências de API e informações gerais de resolução de problemas. 
Para a documentação de recurso integral do {{site.data.keyword.iot_short_notm}}, consulte a [documentação do produto do {{site.data.keyword.iot_short_notm}} ![Ícone de link externo](../../../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) no IBM Knowledge Center. Mais informações sobre os vários planos podem ser localizadas em [{{site.data.keyword.iot_short_notm}} planos de serviço](/docs/IoT/plans_overview.html#plans_overview). 
</p>
{: important}

A integração de serviços externos permite acessar dados e operações de terceiros ou serviços externos em sua organização do {{site.data.keyword.iot_full}}.

## Jasper
{: #jasper}

Jasper é uma plataforma de administração e gerenciamento para dispositivos SIM. Jasper está integrado ao painel do {{site.data.keyword.iot_short_notm}}, possibilitando a administração de dispositivos Jasper por meio do painel de sua organização do {{site.data.keyword.iot_short_notm}}.

### Operações suportadas para Jasper

A integração de Jasper integrada fornecida por nossa plataforma fornece suporte para as operações Jasper a seguir:

- Visualizar dados gerais do Jasper
  - Mostra o status, o plano de taxa, o uso de dados de mês a data, uso de SMS de mês a data, uso de voz de mês a data, limites de excesso, data de inclusão e data de modificação.
- Mude o estado de ativação do SIM
  - Selecione por meio de inventário, ativação pronta, ativado, desativado e obsoleto.
- Visualizar uso do SIM
  - Mostra a data de início do ciclo, os dados faturáveis e totais, o SMS faturável e total, a voz faturável e total.
  - A data de início do ciclo pode ser configurada usando um formato de data AAAA-MM-DD.
- Enviar SMS para o SIM
- Alterar o plano de taxa

É possível acessar as operações suportadas no drill down do dispositivo de um dispositivo conectado ao Jasper depois que as etapas de configuração a seguir são concluídas.

### APIs de REST para Jasper
Para acessar a API de REST para Jasper, veja a seção Extensão Jasper na documentação [{{site.data.keyword.iot_short_notm}}API de REST HTTP ![Ícone de link externo](../../../../icons/launch-glyph.svg "Ícone de link externo")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-jasper.html){: new_window}.

### Configuração para Jasper

Para conectar o serviço Jasper à sua organização do {{site.data.keyword.iot_short_notm}}, deve-se concluir dois estágios de configuração. Primeiro, o {{site.data.keyword.iot_short_notm}} deve ser conectado a seu serviço Jasper, em seguida, seus dispositivos {{site.data.keyword.iot_short_notm}} devem ser configurados.


1. Ative a extensão Jasper. Para ativar a integração de Jasper com sua organização do {{site.data.keyword.iot_short_notm}}, conclua as etapas a seguir:
  1. No painel do {{site.data.keyword.iot_short_notm}}, selecione **Extensões**.
  2. Na página **Extensões**, clique em **Incluir extensão**.
  3. Clique em **Incluir** próximo a Jasper.
  4. Insira o nome do usuário, a senha, a chave de acesso e o ID do domínio do Jasper.
  5. Clique em **Pronto**.

2. Configure seus dispositivos.
É possível configurar os dispositivos conectados à sua organização do {{site.data.keyword.iot_short_notm}} e à sua conta do Jasper para exibir dados do Jasper no painel do {{site.data.keyword.iot_short_notm}}.  
**Importante:** a configuração do Jasper não pode ser aplicada como parte do processo Incluir dispositivo. Apenas dispositivos conectados anteriormente podem ser configurados com o Jasper.  
Para configurar seus dispositivos conectados Jasper, conclua as etapas a seguir:
 1. Na página Dispositivos do painel do {{site.data.keyword.iot_short_notm}}, localize o dispositivo conectado por Jasper a ser configurado.
 2. Selecione o dispositivo para abrir a visualização Drilldown do dispositivo.
 3. Role para baixo até a Configuração de extensão.
 4. Insira a configuração de extensão usando o formato de JSON a seguir e, em seguida, clique em **Confirmar mudanças** para salvar a sua configuração.  

```json  
    {
        "jasper": {
            "iccid": "string"
        }
    }

```

Quando a organização estiver configurada com êxito, a seção Extensões será exibida sob a seção Configuração de extensão na visualização Drilldown do dispositivo.

## AT&T
{: #att}

### Operações suportadas para a AT&T

A extensão AT&T permite as operações a seguir da AT&T:

- Visualizar dados gerais da AT&T
  - Mostra o status, o plano de taxa, o uso de dados de mês a data, uso de SMS de mês a data, uso de voz de mês a data, limites de excesso, data de inclusão e data de modificação.
- Mude o estado de ativação do SIM
  - Selecione por meio de inventário, ativação pronta, ativado, desativado e obsoleto.
- Visualizar uso do SIM
  - Mostra: data de início do ciclo, dados faturáveis e totais, SMS faturável e total, voz faturável e total.
  - A data de início do ciclo pode ser configurada usando um formato de data AAAA-MM-DD.
- Enviar SMS para o SIM
- Alterar o plano de taxa

### APIs de REST para AT&T
Para acessar a API de REST para AT&T, veja a seção Extensão AT&T na documentação [{{site.data.keyword.iot_short_notm}}API de REST HTTP ![Ícone de link externo](../../../../icons/launch-glyph.svg "Ícone de link externo")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-atnt.html){: new_window}.

### Configuração para a AT&T

Para conectar sua organização do {{site.data.keyword.iot_short_notm}} ao AT&T, deve-se concluir a configuração da organização e a configuração do dispositivo.

Para configurar sua plataforma {{site.data.keyword.iot_short_notm}}, conclua as etapas a seguir:

1. Ative a extensão da AT&T. Para ativar a integração da AT&T com sua organização do {{site.data.keyword.iot_short_notm}}, conclua as etapas a seguir:
  1. No painel do {{site.data.keyword.iot_short_notm}}, selecione **Extensões**.
  2. Na página **Extensões**, clique em **Incluir extensão**.
  3. Clique em **Incluir** ao lado de AT&T.
  4. Insira seu nome de usuário, sua senha, sua chave de acesso e o ID do domínio do AT&T.
  5. Clique em **Pronto**.

Para conectar sua organização do {{site.data.keyword.iot_short_notm}} à sua conta do AT&T, deve-se concluir dois estágios de configuração. Conclua a configuração da organização e, em seguida, configure seus dispositivos.


2. Configure seus dispositivos
É possível configurar os dispositivos que estão conectados à sua organização do {{site.data.keyword.iot_short_notm}} e à sua conta da AT&T para exibir dados da AT&T no painel do {{site.data.keyword.iot_short_notm}}.  
**Importante:** a configuração do AT&T não pode ser aplicada como parte do processo Incluir dispositivo. Apenas dispositivos conectados anteriormente podem ser configurados com o AT&T.  
Para configurar seus dispositivos conectados ao AT&T, conclua as etapas a seguir:
 1. Na página Dispositivos de seu painel do {{site.data.keyword.iot_short_notm}}, localize o dispositivo conectado ao AT&T a ser configurado.
 2. Selecione o dispositivo para abrir a visualização Drilldown do dispositivo.
 3. Role para baixo até a Configuração de extensão.
 4. Insira a configuração de extensão usando o formato de JSON a seguir e, em seguida, clique em **Confirmar mudanças** para salvar a sua configuração.  

```json  
    {
        "atnt": {
            "iccid": "string"
        }
    }

```

Quando a organização estiver configurada com êxito, a seção Extensões será exibida sob a seção Configuração de extensão na visualização Drilldown do dispositivo.

## Arm Mbed Bridge
{: #arm}

A ponte permite que dispositivos do Arm Mbed se integrem ao {{site.data.keyword.iot_short_notm}} e troquem mensagens bidirecionalmente. Para ativar essa integração, primeiro é necessário inscrever-se para uma conta do Arm Mbed Cloud e, em seguida, fornecer as informações de conexão solicitadas para sua configuração do {{site.data.keyword.iot_short_notm}}.

### Configuração de instalação


1. Ative a extensão Arm Mbed Bridge. Para ativar a extensão, conclua as etapas a seguir:
  1. No painel do {{site.data.keyword.iot_short_notm}}, selecione **Extensões**.
  2. Na página Extensões, clique em **Incluir extensão**.
  3. Clique em **Incluir** próximo à extensão da ponte Arm Mbed.
  4. Insira a chave de acesso Arm Mbed. É possível criá-la usando o portal do Arm Mbed em [https://portal.mbedcloud.com ![Ícone de link externo](../../../../icons/launch-glyph.svg "Ícone de link externo")](https://portal.mbedcloud.com){: new_window}.
  5. Verifique se as credenciais estão corretas clicando no botão **Verificar conexão**.
  6. Clique em **Pronto**.

### Formato da carga útil

A plataforma Arm Mbed usa dois tipos de mensagens recebidas: notificações e respostas assíncronas. O {{site.data.keyword.iot_short_notm}} pode enviar comandos para dispositivos conectados à plataforma Arm Mbed.

#### Notificações

As notificações são geradas por mudanças nos dados do dispositivo ou do sensor. Depois que o {{site.data.keyword.iot_short_notm}} processa a mensagem, ele é enviado para o tópico de evento de dispositivo da mesma maneira que um dispositivo conectado diretamente ao {{site.data.keyword.iot_short_notm}}. O tipo de evento usado para notificações que se originam em dispositivos conectados à plataforma Arm Mbed é `notify`.

A amostra de código a seguir mostra o formato de carga útil para uma notificação enviada pela API da plataforma Arm Mbed:

```
{
  "ep":<endpoint/deviceID>,
  "path":<resource path>,
  "ct":<content type>,
  "payload":<Base64 encoded payload>,
  "max-age":<how long the payload is valid, in seconds>
}
```

#### Respostas assíncronas

Quando o {{site.data.keyword.iot_short_notm}} envia um comando para um dispositivo que está conectado à plataforma Arm Mbed, o dispositivo envia uma mensagem de confirmação de volta para o {{site.data.keyword.iot_short_notm}}. Essa mensagem de confirmação é chamada de _resposta assíncrona_ e usa o tipo de evento `asyncResponse`.

A amostra de código a seguir mostra o formato de carga útil para uma resposta assíncrona que é enviada pelo serviço Arm Mbed Cloud:

```
{
  "id":<transaction id>,
  "status":<200 is command was sucessfully executed. Check other HTTP response codes>,
  "ct":<content type>,
  "max-age":<how long the payload is valid, in seconds>,
  "payload":<base64 encoded payload>,
  "ep":<endpoint/deviceID affected by the command>,
  "path":<resource path affected by the command>
}
```

#### Enviando comandos para a plataforma Arm Mbed

O {{site.data.keyword.iot_short_notm}} pode enviar comandos para dispositivos conectados à plataforma Arm Mbed. Os comandos enviados para a plataforma Arm Mbed devem usar o formato JSON a seguir:

```
{
  "method":<PUT or POST>,
  "deviceId":<endpoint/deviceId>,
  "resourceId":<resource path>,
  "payload": <Base64 encoded payload>
}
```
O método escolhido faz distinção entre maiúsculas e minúsculas. A `/` inicial do caminho de recurso deve ser ignorada.


A carga útil deve ser publicada no tópico a seguir:

```
iot-2/type/<device_type>/id/<deviceId>/cmd/<command_type>/fmt/<command_format>
```


## Orange
{: #orange}

A extensão Orange permite visualizar dados do cartão SIM de dispositivos conectados ao seu {{site.data.keyword.iot_short_notm}} e tem um cartão SIM da Orange instalado.

### Operações suportadas para a Orange

Se você tiver um dispositivo conectado ao serviço {{site.data.keyword.iot_short_notm}} e tiver um cartão SIM da Orange, será possível usar a extensão da Orange para visualizar os dados do cartão SIM a seguir:

- Número de série do SIM
- Activation status
- Última alteração do status
- Última atualização do status
- Status do Local

### APIs de REST para Orange
Para acessar a API de REST para Orange, veja a seção Extensão Orange na documentação [{{site.data.keyword.iot_short_notm}}API de REST HTTP ![Ícone de link externo](../../../../icons/launch-glyph.svg "Ícone de link externo")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-orange.html){: new_window}.

### Configuração para a Orange

Para ativar a extensão da Orange:

1. No painel do {{site.data.keyword.iot_short_notm}}, selecione **Extensões**.
2. Na página **Extensões**, clique em **Incluir extensão**.
3. Clique em **Incluir** ao lado da extensão da Orange.
4. Insira seu nome do usuário e senha da Orange.
6. Clique em **Pronto**.

Após a ativação da extensão da Orange, cada dispositivo que tiver um cartão SIM da Orange deverá ser configurado para exibir dados do SIM da Orange.

1. Na guia de dispositivos do painel do {{site.data.keyword.iot_short_notm}}, localize o dispositivo SIM da Orange a ser configurado.
2. Selecione o dispositivo e role para baixo até **Configuração de extensão**.
3. Insira a configuração de extensão usando o formato de JSON a seguir e, em seguida, clique em **Confirmar mudanças** para salvar a sua configuração.

```json
    {
        "orange": {
            "serialnumber": "<serial number of Orange SIM>"
        }
    }

```
Quando a organização estiver configurada com êxito, a seção Extensões será exibida sob a seção Configuração de extensão na visualização Drilldown do dispositivo.

## Armazenamento de dados históricos
{: #historical_data}

A extensão de armazenamento de dados históricos permite localizar e configurar serviços de armazenamento de mensagens compatíveis, tais como [{{site.data.keyword.cloudantfull}} ![Ícone de link externo](../../../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/cloudant_connector.html){: new_window} ou [{{site.data.keyword.messagehub_full}} ![Ícone de link externo](../../../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/message_hub.html){: new_window} para seus dados do IoT.

## Pacotes de gerenciamento de dispositivo customizado
{: #device_mgmt}

O gerenciamento de dispositivo é um recurso principal do {{site.data.keyword.iot_short_notm}}, no entanto, ele pode ser estendido para desenvolver funcionalidade adicional. Os pacotes de gerenciamento de dispositivo customizado devem consistir em JSON válido e definir pelo menos uma ação de gerenciamento de dispositivo customizado.

Para obter mais informações sobre funções customizadas de gerenciamento de dispositivo, incluindo um exemplo do formato JSON necessário, consulte [extensões customizadas de gerenciamento de dispositivo ![Ícone de link externo](../../../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/devices/device_mgmt/custom_actions.html){: new_window}.

### Incluindo um pacote de gerenciamento de dispositivo customizado

Os pacotes de gerenciamento de dispositivo customizados podem ser incluídos usando o painel do {{site.data.keyword.iot_short_notm}} ou usando a API.

Para incluir um pacote de gerenciamento de dispositivo customizado usando o painel do {{site.data.keyword.iot_short_notm}}:

1. No painel do {{site.data.keyword.iot_short_notm}}, clique em **Configurações** na barra de navegação.
2. Clique em **Pacotes de gerenciamento de dispositivo customizado**.
3. Clique no botão **Incluir pacote**.
4. Selecione seu arquivo de pacote e clique em **Abrir**.

Para incluir um pacote de gerenciamento de dispositivo customizado usando a API, veja a [Documentação da API do {{site.data.keyword.iot_short_notm}}![Ícone de link externo](../../../../icons/launch-glyph.svg "Ícone de link externo")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/orgAdmin.html){: new_window}.

## e-mail
{: #email}

Os usuários podem ser incluídos no {{site.data.keyword.iot_short_notm}} usando convites de e-mail. Para obter informações, veja [Gerenciando o acesso de usuário](/docs/IoT/add_users.html).

Para usar o recurso de convite por e-mail, uma extensão de e-mail deve ser configurada para usar o serviço on-line SendGrid ou um serviço de Protocolo Simples de Transporte de Correio (SMTP). A extensão também pode usar o aplicativo SendGrid {{site.data.keyword.Bluemix_notm}}.

### Serviço on-line SendGrid

Para configurar a extensão de e-mail para uso com o serviço on-line SendGrid, siga estas etapas:

1. Recupere a chave API autorizada da sua conta SendGrid on-line.
2. No painel do {{site.data.keyword.iot_short_notm}}, clique em **Extensões** na barra de navegação.
3. Na seção **E-mail**, clique em **Configurar**.
4. Selecione **SendGrid com a chave API**
5. Insira o nome e o endereço de e-mail do administrador do site e a chave de API autorizada.

### Serviço SMTP

Para configurar a extensão de e-mail para uso com um serviço SMTP, siga estas etapas:

1. No painel do {{site.data.keyword.iot_short_notm}}, clique em **Extensões** na barra de navegação.
2. Na seção **E-mail**, clique em **Configurar**.
3. Selecione **SMTP**.
4. Insira os detalhes de configuração do serviço SMTP.

### Aplicativo SendGrid {{site.data.keyword.Bluemix_notm}}

Para configurar a extensão de e-mail para uso com o aplicativo SendGrid {{site.data.keyword.Bluemix_notm}}, siga estas etapas:

1. Crie um aplicativo simulado e ligue-o ao serviço SendGrid.  
Para recuperar as credenciais de configuração, inclua e ligue o serviço SendGrid a um aplicativo simulado.

 1. No painel do {{site.data.keyword.Bluemix_notm}}, clique em **Criar serviço**.
 2. Selecione o serviço SendGrid no catálogo e clique em **Criar**.
 3. No painel do {{site.data.keyword.Bluemix_notm}}, inclua o aplicativo {{site.data.keyword.runtime_nodejs_full}}.
 4. Clique no aplicativo {{site.data.keyword.runtime_nodejs_notm}} no painel {{site.data.keyword.Bluemix_notm}} e clique em **Ligar um serviço ou API**.
 5. Selecione o serviço SendGrid e clique em **Incluir**.
 6. Remonte o aplicativo {{site.data.keyword.runtime_nodejs_notm}}.
2. Prepare-se para configurar o serviço {{site.data.keyword.iot_short_notm}}.  
O {{site.data.keyword.iot_short_notm}} pode ser configurado usando o painel do {{site.data.keyword.iot_short_notm}} ou usando a API do {{site.data.keyword.iot_short_notm}}.  
 1. Clique no aplicativo {{site.data.keyword.runtime_nodejs_notm}} no painel {{site.data.keyword.Bluemix_notm}}.
 2. Clique em **Variáveis de ambiente** na barra de navegação.
 3. Copie o JSON exibido para um arquivo de texto provisório.  
 O JSON deve ter o formato a seguir:
```
{
  "name": "SendGridServiceName",
  "label": "user-provided",
  "credentials": {
    "password": "xxx",
    "hostname": "smtp.sendgrid.net",
    "username": "username"
  }
}
```
3. Inclua os dados de configuração na organização do {{site.data.keyword.iot_short_notm}}.
 1. Abra o painel {{site.data.keyword.iot_short_notm}}.
 2. Clique em **Extensões** na barra de navegação.
 3. Clique em **Configurar** no ícone **E-mail**.
 4. Selecione **SendGrid com nome do usuário**.
 5. Insira os dados de configuração do arquivo de texto provisório.
 6. Clique em **Pronto**.
