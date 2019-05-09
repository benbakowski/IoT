---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-05"

keywords: Lite plan, migrate, Watson IoT Platform

subcollection: iot-platform

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:important: .important}

# Migrando o {{site.data.keyword.iot_short_notm}} Lite para o {{site.data.keyword.iot_short_notm}} Non-production ou Production
{: #org_migration}

<p>Essa coleção de documentação do {{site.data.keyword.cloud}} pertence ao plano de precificação Lite do {{site.data.keyword.iot_full}} e inclui informações básicas de introdução, referências de API e informações gerais de resolução de problemas. 
Para obter a documentação completa do recurso {{site.data.keyword.iot_short_notm}}, consulte a [documentação do produto {{site.data.keyword.iot_short_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) no {{site.data.keyword.IBM}} Knowledge Center. Mais informações sobre os vários planos podem ser localizadas em [{{site.data.keyword.iot_short_notm}} planos de serviço](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview). 
</p>
{: important}

Depois de obter informações sobre a qualidade do produto do Watson IoT Platform Lite e ter um bom entendimento de como ele se ajusta ao ambiente do IoT, é possível fazer upgrade para o [Watson IoT Platform Non-production ou para um dos planos de produção ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html){: new_window}.
{:shortdesc}

**Nota:** este documento é destinado apenas para usuários que têm uma instância Lite. Se anteriormente você criou instâncias do IoT Platform com os planos Padrão ou Segurança avançada, o {{site.data.keyword.IBM}} trabalhará com você para migrar sua instância existente do {{site.data.keyword.iot_short_notm}} para os novos planos de não produção ou de produção.

## Visão geral do processo de migração
{: #org_migration_overview}

Ao migrar para o {{site.data.keyword.iot_short_notm}}, você remove os limites do plano Lite de 500 dispositivos e o consumo de dados mensal.

Os planos do {{site.data.keyword.iot_short_notm}} incluem os componentes adicionais a seguir para suportar a arquitetura do aplicativo IoT de ponta a ponta:

- {{site.data.keyword.messagehub}} - uma versão hospedada da {{site.data.keyword.IBM_notm}} da plataforma de fluxo Kafka que seus aplicativos podem usar para receber dados do IoT.
- {{site.data.keyword.dashdbshort}} para armazenamento de dados analíticos.
- BD do {{site.data.keyword.cloudantfull}} para dados de série temporal.
- {{site.data.keyword.cos_full}} para retenção de dados de longo prazo.

Este documento descreve os tipos de dados que você pode desejar migrar de uma instância existente do Lite para uma versão integral.

**Nota:** geralmente, é mais fácil configurar o ambiente de não produção ou de produção do {{site.data.keyword.iot_short_notm}} do zero, uma vez que inclui componentes e recursos além do serviço {{site.data.keyword.iot_short_notm}} Lite. Além disso, os dispositivos e os usuários criados para teste na versão Lite provavelmente não serão os mesmos que você usará para produção.

Se, no entanto, você desejar transferir algumas de suas configurações existentes do Lite, as seções a seguir fornecerão orientação durante o processo.

A documentação sobre as [APIs do {{site.data.keyword.iot_short_notm}}]/docs/services/IoT?topic=iot-platform-api_overview#api_overview) fornece instruções sobre como chamar as APIs e seu conjunto completo de parâmetros.


## Antes de iniciar
{: #org_migration_byb}

Antes de ser possível iniciar o processo de migração, deve-se comprar o {{site.data.keyword.iot_short_notm}} (Production ou Non-production). Na compra, a equipe de operações do {{site.data.keyword.IBM_notm}} provisionará uma nova instância do {{site.data.keyword.iot_short_notm}} para você. Isso incluirá um novo ID alfanumérico com seis caracteres da organização.


## Migrando usuários
{: #user_migration}

As [APIs de gerenciamento do usuário ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/security.html#!/Authorization_-_User_Management){: new_window} fornecem exportação e importação em massa de usuários do {{site.data.keyword.iot_short_notm}} e podem ser usadas para exportar e importar os usuários que você deseja preservar na nova organização.

1. Exporte os usuários da organização Lite.  
Use o comando `GET /authorization/users` para exportar todos os usuários de sua organização de conta Lite como um objeto JSON.
2. Limpe a lista de usuários.  
Se necessário, edite a estrutura JSON para remover quaisquer usuários que você não queira migrar para a nova organização.
3. Importe os usuários para a nova organização.  
Use o comando `POST /authorization/users/multiple` para importar para a lista de usuários JSON editada para a nova organização.

Os usuários agora têm acesso à nova organização, que será exibida no seletor de organização no painel do {{site.data.keyword.iot_short_notm}}.

##  Migrando dispositivos  
{: #device_migration}

A migração de dispositivos pode ser realizada nestas etapas:  
1. Migre os Tipos de dispositivo que você deseja preservar para a nova organização.  
2. Migre os próprios dispositivos para a nova organização.  
3. Atualize o nome do host usado pelos dispositivos para se conectar ao {{site.data.keyword.cloud_notm}} para iniciar com seu novo ID da organização.
4. Migre quaisquer informações de Gerenciamento de dados criadas na plataforma Lite.   
Isso pode incluir as Interfaces físicas e lógicas do dispositivo, as Coisas e as Regras.

<p>Os Tipos de dispositivo e os Dispositivos podem ser migrados em massa com as APIs a seguir:
<table>
<tr>
<th> Documentação da API </th>
<th> Exportar API </th>
<th> Importar API </th>
</tr>
<tr>
<td> [API do tipo de dispositivo ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/org-admin.html) </td>
<td> `GET /device/types` </td>
<td> `POST /device/types` </td>
</tr>
<tr>
<td>  [API do dispositivo ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/org-admin.html#!/Device_Bulk_Configuration) </td>
<td> `GET /bulk/devices` </td>
<td>  `POST /bulk/devices/add`</td>
</tr>
</table>
</p>
{: tip}


**Importante:** o {{site.data.keyword.iot_short_notm}} não armazena tokens de autenticação de dispositivo, apenas a versão salt deles. A chamada `GET /bulk/devices` não é, portanto, capaz de retornar os tokens de autenticação para dispositivos armazenados. Se você tiver um registro dos tokens de autenticação de dispositivo, será possível incluí-los no objeto JSON antes de executar o carregamento em massa. Caso contrário, deve-se gerar novos tokens de autenticação de dispositivo para cada dispositivo e copiá-los para os dispositivos.  

Se você estiver usando certificados do lado do dispositivo para autenticar dispositivos, em vez de tokens de autenticação, não será necessário fazer isso. No entanto, caso você esteja usando certificados do lado do dispositivo, deve-se fazer upload dos certificados que foram usados para inscrevê-los na nova organização.


## Atualizando dispositivos
{: #update_devices}

Quando seus dispositivos são registrados na nova organização, deve-se atualizar a configuração ou o código presente em cada um dos dispositivos existentes para usar o nome do host da nova organização.

Para clientes do sistema de mensagens MQTT e HTTP, use o nome do host a seguir:  
`<orgId>.messaging.internetofthings.ibmcloud.com`

Aponte os clientes da API de REST no nome de host a seguir:  
`<orgId>.internetofthings.ibmcloud.com`

**Importante:** se você gerou novos tokens de autenticação para seus dispositivos, deve-se copiá-los para cada dispositivo.


## Migração de gerenciamento de dispositivo
{: #device_management}

As [APIs de gerenciamento de dados ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/state-mgmt.html){: new_window} incluem APIs para exportar e importar interfaces físicas e lógicas de dispositivo, definições de coisas e regras.

**Importante:** o {{site.data.keyword.iot_short_notm}} não suporta atualmente o conceito de ativos gêmeos para ingestão de dados.

## Placas e cartões
{: #boards_cards}

O {{site.data.keyword.iot_short_notm}} não inclui APIs para importar e exportar definições e customizações de placas e cartões. Deve-se recriá-las manualmente na nova organização.

## Ativar quaisquer extensões necessárias
{: #extensions}

Deve-se recriar quaisquer extensões que você tenha ativado na plataforma Lite, como links para o {{site.data.keyword.messagehub}}, o {{site.data.keyword.cloudant_short_notm}} e o Jasper na nova organização.

## Migrando aplicativos
{: #application_migration}

Se você tiver desenvolvido aplicativos que chamam as APIs oferecidas com o serviço {{site.data.keyword.iot_short_notm}} Lite para, por exemplo, enviar ou receber dados, ou para administrar o serviço, deverá atualizá-los para usar sua nova instância do {{site.data.keyword.iot_short_notm}} Production ou Non-Production. Isso também se aplica a quaisquer fluxos Node-RED que você possa estar usando.
A migração envolve:
- Atualização de aplicativos para usar um novo ID da organização com seis caracteres.
- Atualização de aplicativos para usar a chave de API e as credenciais de token criadas para sua nova instância de serviço.

**Importante:** se você está usando uma ligação do Cloud Foundry para passar o ID da organização e as credenciais para o aplicativo, deve-se usar um mecanismo diferente, pois a nova instância do {{site.data.keyword.iot_short_notm}} não é provisionada para execução no espaço do Cloud Foundry.

### Gerando credenciais de conexão de API

O processo de migração a ser seguido depende da natureza de seu aplicativo. Geralmente, para todos os casos, a primeira etapa é adquirir uma Chave de API e um Token de autenticação para seu aplicativo usar.

1. Efetue login no painel de nível superior de seu novo serviço {{site.data.keyword.iot_short_notm}}.
2. Selecione a guia **Uso**.
3. Clique no link **Visualizar detalhes** para trazer as informações do serviço {{site.data.keyword.iot_short_notm}}.  
As informações a seguir são exibidas:
   - O orgID de seis caracteres
   - Chave de API e Token.  
   É necessário gerar novas Chaves de API para cada um de seus aplicativos, em vez de usar a Chave de API mostrada aqui. Isso permite configurar permissões apropriadas para cada aplicativo.
   - URL do host.
4. Crie uma combinação de chave de API e token de autenticação para seu aplicativo.  
Eles serão necessários quando você configurar o aplicativo para se conectar à sua organização.   
   1.  Clique em `Ativar`.  
   Isso o levará ao painel de serviço subjacente usado para administrar o serviço {{site.data.keyword.iot_short_notm}} Lite.
   2. Selecione **Aplicativos**.
   3. Clique em **Gerar Chave API**
   4. Copie os valores de chave API e token de autenticação que são listados.
   5. Selecione uma função apropriada para seu aplicativo.   
   6. Inclua um comentário para que possa identificar facilmente essa combinação de chave API e token de autenticação.
   7. Clique em **Gerar**.
   8. **Importante:** faça uma cópia local do token de autenticação. Não será possível recriá-la depois de fechar a janela.


### Atualizando aplicativos Node-RED
Será necessário configurar os nós Node-RED para se conectar à nova instância do {{site.data.keyword.iot_short_notm}}. Seus nós `ibmiot` não poderão mais usar a opção de autenticação `BluemixService`, portanto, é necessário selecionar a opção `API Key` como alternativa.
1. Abra o nó `ibmiot` para edição.
2. Em propriedades do nó, selecione **Chave de API**.
3. Para o campo Chave de API, clique no ícone de edição e, em seguida, insira a Chave de API e o Token de autenticação salvos na etapa anterior.
4. Salve suas mudanças e reimplemente o fluxo de Node-RED.

### Atualizando um aplicativo que não usa uma ligação do Cloud Foundry
Identifique o local no qual seu aplicativo armazena o ID da organização, a chave de API e o token de autorização e substitua-os pelos valores salvos anteriormente.

Se o seu aplicativo usar um dos SDKs do {{site.data.keyword.iot_short_notm}}, esses valores provavelmente serão mantidos em um arquivo de Propriedades.
{: tip}

### Atualizando um aplicativo que usa uma ligação do Cloud Foundry

O {{site.data.keyword.cloud_notm}} fornece um mecanismo para ligar aplicativos Cloud Foundry a um ou mais serviços do Cloud Foundry. As ligações podem ser estabelecidas usando a CLI do {{site.data.keyword.cloud_notm}} ou criando uma `Connection` entre o Aplicativo e o Serviço no painel do {{site.data.keyword.cloud_notm}}.

Quando um Aplicativo é ligado a um serviço, as credenciais de serviço Chave de API e Token de autenticação são copiadas para a variável de ambiente `VCAP_SERVICES`, de onde o aplicativo pode recuperá-las.

**Importante:** esse mecanismo de ligação não pode ser usado com o novo serviço {{site.data.keyword.iot_short_notm}}. Deve-se localizar o código no aplicativo que estiver lendo em `VCAP_SERVICES` e substituí-lo pelo código que lê os valores de um local no qual você agora armazena a chave de API e o token de autorização. Para concluir a atualização, deve-se reconstruir e reimplementar o aplicativo.
