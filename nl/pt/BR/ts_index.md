---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:important: .important}

# Resolução de problemas do {{site.data.keyword.iot_short_notm}}
{: #ts}

<p>Essa coleção de documentação do {{site.data.keyword.Bluemix}} pertence ao plano de precificação Lite do {{site.data.keyword.iot_full}} e inclui informações básicas de introdução, referências de API e informações gerais de resolução de problemas. 
Para a documentação de recurso integral do {{site.data.keyword.iot_short_notm}}, consulte a [documentação do produto do {{site.data.keyword.iot_short_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) no IBM Knowledge Center. Mais informações sobre os vários planos podem ser localizadas em [{{site.data.keyword.iot_short_notm}} planos de serviço](/docs/IoT/plans_overview.html#plans_overview). 
</p>
{: important}

Aqui estão as respostas às perguntas comuns de resolução de problemas sobre o
uso do {{site.data.keyword.iot_full}} no
{{site.data.keyword.Bluemix_notm}}.
{:shortdesc}

## Problema ao acessar a organização do {{site.data.keyword.iot_short_notm}}
{: #access-expiry-problem}

Não é possível efetuar login em uma organização do {{site.data.keyword.iot_short_notm}} de sua propriedade.
{:shortdesc}

Não é possível efetuar login em sua organização do {{site.data.keyword.iot_short_notm}} diretamente usando a URL da organização ou usando `https://internetofthings.ibmcloud.com`.
{: tsSymptoms}

Seu acesso à organização do {{site.data.keyword.iot_short_notm}} pode ter expirado. As organizações do {{site.data.keyword.iot_short_notm}} que foram criadas usando o {{site.data.keyword.Bluemix}} usam perfis de usuário temporários por padrão.
{: tsCauses}

É possível resolver esse problema acessando sua organização do {{site.data.keyword.iot_short_notm}} usando o {{site.data.keyword.Bluemix_notm}} e mudando a configuração de expiração de seu perfil do usuário. Para mudar as configurações de expiração do usuário:

1. No painel do {{site.data.keyword.Bluemix_notm}}, abra o serviço {{site.data.keyword.iot_short_notm}}.
2. Clique em **Membros** na barra de navegação.
3. Clique no ícone **Editar**.
4. Limpe a caixa de seleção **O acesso expira** e clique em **Salvar**.
{: tsResolve}

## Problema ao se conectar ao {{site.data.keyword.iot_short_notm}}
{: #connection_problem}

Sua conexão com o {{site.data.keyword.iot_short_notm}} cai ou desconecta inesperadamente.
{:shortdesc}

Ao tentar se conectar ao {{site.data.keyword.iot_short_notm}}, seu dispositivo ou aplicativo recebe um erro.
{: tsSymptoms}

Talvez haja mais de um dispositivo tentando se conectar ao mesmo identificador de cliente e credenciais. Apenas uma conexão exclusiva é permitida por identificador de cliente. Não é possível ter múltiplas conexões simultâneas usando o mesmo ID. Os aplicativos podem compartilhar a mesma chave API, mas o MQTT requer que o identificador de cliente seja sempre exclusivo.
{: tsCauses}

É possível descartar essa razão verificando se você não tem múltiplos dispositivos tentando se conectar usando as mesmas credenciais.
{: tsResolve}

## O dispositivo desconecta-se de forma intermitente do {{site.data.keyword.iot_short_notm}}
{: #disconnection_problem}

Sua conexão de dispositivo com o {{site.data.keyword.iot_short_notm}} cai de forma intermitente inesperadamente.
{:shortdesc}

Um dispositivo que está conectado ao serviço do {{site.data.keyword.iot_short_notm}} é desconectado de forma intermitente. O dispositivo reconecta-se, mas é desconectado inesperadamente mais uma vez após algum tempo.
{: tsSymptoms}

Pode ser que ao conectar-se você esteja usando um valor para uma opção de ping MQTT que é muito baixa, o que faz parecer que a conexão atingiu o tempo limite. Por exemplo, se o cliente MQTT estiver configurado incorretamente, os pings não serão recebidos em tempo hábil e a conexão é fechada.
{: tsCauses}

É possível corrigir este problema, confirmando se você configurou corretamente o ping e os parâmetros de KeepAlive para sua conexão.   
{: tsResolve}
