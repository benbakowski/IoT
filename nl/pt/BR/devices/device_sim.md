---

copyright:
  years: 2017, 2019
lastupdated: "2019-04-05"

keywords: device simulator, devices

subcollection: iot-platform

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:important: .important}


# Simulando dados do dispositivo
{: #sim_device_data}

<p>Essa coleção de documentação do {{site.data.keyword.cloud}} pertence ao plano de precificação Lite do {{site.data.keyword.iot_full}} e inclui informações básicas de introdução, referências de API e informações gerais de resolução de problemas. 
Para a documentação de recurso integral do {{site.data.keyword.iot_short_notm}}, consulte a [documentação do produto do {{site.data.keyword.iot_short_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) no IBM Knowledge Center. Mais informações sobre os vários planos podem ser localizadas em [{{site.data.keyword.iot_short_notm}} planos de serviço](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview). 
</p>
{: important}

Use o simulador de dispositivo do {{site.data.keyword.iot_full}} para configurar eventos simulados para dispositivos para aprender, testar e demonstrar recursos do {{site.data.keyword.iot_short_notm}} em completo funcionamento, sem precisar registrar e conectar dispositivos reais.
{: shortdesc}

Usando o simulador de dispositivos, é possível criar dispositivos simulados para os tipos de dispositivos existentes ou novos dispositivos e tipos de dispositivos. Cada dispositivo simulado pode usar detalhes de evento exclusivos, mas também é possível criar uma configuração padrão aplicada a todos os dispositivos.

## Antes de iniciar
{: #byb-simulation .sectiontitle}
Ative a simulação de dispositivo para o seu ID de usuário.
1. Efetue login no {{site.data.keyword.iot_short_notm}}.
2. Na área de janela de navegação principal, selecione **Configurações**.
3. Na seção **Dados e dispositivos**, ative o simulador de dispositivo.

Se a simulação de dispositivo estiver ativada para seu ID de usuário, todos os dispositivos simulados ativados serão iniciados automaticamente quando você efetuar login no painel do {{site.data.keyword.iot_short_notm}}.

## Simulando dispositivos
{: #process-simulation .sectiontitle}
Quando ativado, o simulador de dispositivos está disponível em todas as páginas do painel. Uma mensagem no canto inferior direito da tela indica o número de simulações em execução.

**Importante:** os dispositivos simulados e os tipos de dispositivos que você define para seu ID de usuário estão disponíveis para outros usuários da organização do {{site.data.keyword.iot_short_notm}}. No entanto, para gerar dados simulados para os seus dispositivos, você deve ter efetuado login no painel do {{site.data.keyword.iot_short_notm}}em uma sessão ativa do usuário.

Para simular dados do dispositivo:
1. No painel do {{site.data.keyword.iot_short_notm}}, clique na mensagem "0 Simulações em execução".
3. Na janela de configuração **Simulações** que é aberta, clique em **Criar simulação**.
4. Configure os detalhes da simulação.  
Clique em **Importar/Exportar simulação** para importar uma [configuração existente](#reuse) ou configure manualmente os detalhes:
   1. Selecione um tipo de dispositivo existente para o qual você deseja simular dados ou crie um novo tipo de dispositivo digitando o nome do tipo de dispositivo.
   2. Modifique o nome padrão para o tipo de evento.
   3. Em **Planejamento**, configure a frequência do evento.
   4. Edite a carga útil do evento.  
   Edite a carga útil JSON de amostra incluindo propriedades e seus valores correspondentes ou use [funções](#functions) para incluir pontos de dados gerados dinamicamente.  
   Também é possível fazer upload de um [arquivo CSV de carga útil de evento](#csv) para configurar a carga útil.  
   {: tip}
5. Clique em **Novo tipo de evento** para incluir e configurar mais tipos de evento para o tipo de dispositivo.
5. Ative **Salvar eventos como dados históricos** para disponibilizar os dados do estado do dispositivo simulado para acesso posterior.  
Com os dados históricos ativados, os componentes do gerenciamento de dados do {{site.data.keyword.iot_short_notm}} [![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/GA_information_management/ga_im_definitions.html){: new_window} são criados e o estado do dispositivo simulado pode ser acessado por meio da interface lógica associada.  
**Importante:** depois de ativar o tipo de dispositivo para salvar dados históricos, não será possível incluir ou remover tipos de eventos ou modificar os campos presentes nas cargas úteis de eventos.
5. Clique em **Salvar**para criar o tipo de dispositivo.  
Agora, você está pronto para criar um ou mais dispositivos simulados.
6. Clique em **Criar dispositivo simulado** para criar um dispositivo e começar a enviar dados.  
**Dica:** para criar mais de um dispositivo, clique em **1 x** e selecione o número de dispositivos a serem criados.  
7. Para criar mais simulações, clique em **Nova simulação** e repita as etapas de configuração para cada dispositivo ao qual você deseja aplicar configurações customizadas.   
A mensagem no canto inferior direito da tela mostra o número de simulações ativas.
8. Na página **Dispositivos**, navegue para um dos
dispositivos simulados e selecione a guia **Eventos recentes** para
verificar se os eventos simulados estão funcionando.

É possível [exportar suas configurações de evento simulado](#reuse) para reutilização ou compartilhamento.

## Funções de tipo de evento
{: #functions .sectiontitle}

É possível usar diversas funções especiais para criar dados dinâmicos para seus tipos de evento.

Função | Uso | Exemplo  
:--- | :---  | :--  
`random(lower, upper)`  | Gera um número aleatório no intervalo especificado.  | `{ "random": aleatório (0, 100) }`  
`$counter` | Exibe o número de dispositivos simulados do tipo atual. | `{"total": $counter}`  
`increment(start, increment)` | Especifica o valor inicial e o incremento pelo qual ele aumenta. |`{ "myNumber": increment (10, 1) }`</br>Neste exemplo, `myNumber`inicia em 10 e aumenta em 1 cada vez que uma carga útil é enviada.


## Arquivo CSV de carga útil do evento
{: #csv .sectiontitle}

Se desejar criar dados de eventos controlados para determinados cenários, é possível configurar o fluxo de dados em um arquivo de entrada CSV.

### requisitos
O arquivo CSV deve atender aos requisitos a seguir:
- Cada valor é uma [primitiva JSON válida ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://json.org){: new_window}, exceto conforme observado:
  - :   
  Exemplo: "Hello world"
  - número:  
  Exemplo: 0, 0,1, -22, -2,43
  - booleano:  
  verdadeiro ou falso
  - nulo:  
  null
  - **Não suportado:**
    - objetos  
    Exemplo: {}
    - matrizes  
    Exemplo: []
- Os valores devem ser delimitados por vírgulas.
- As linhas devem ser delimitadas usando um caractere de nova linha (`\n`).
- A linha do cabeçalho deve consistir apenas em valores de sequência.


### Arquivo CSV de amostra
```
"temperature", "confidence","status"
1, 0.1, "normal"
2, 0.2, "normal"
3, 0.3, "error"
4, 0.4, "normal"
```

A primeira linha ou "linha de cabeçalho" determina as propriedades incluídas no JSON do dispositivo em todos os objetos de evento JSON do dispositivo gerados.
Cada linha subsequente ou "linha de dados" configura o valor dessas propriedades em cada objeto de evento JSON do dispositivo gerado.

**Dica:** ao importar o arquivo CSV, é possível selecionar **Loop de dados simulados do arquivo** para percorrer as linhas de dados em sequência para obter um feed de dados contínuo. Se essa alternância não for configurada, cada linha de dados no CSV será enviada uma vez na frequência configurada pelo planejamento.

O arquivo CSV de amostra resulta em cargas úteis de evento do tipo a seguir:
```JSON
{
  "temperature": 1,
  "confidence": 0.1,
  "status": "normal"
}
```

## Compartilhando e reutilizando simulações
{: #reuse .sectiontitle}

É possível exportar os detalhes de sua simulação para reutilização ou compartilhamento:
1. Na janela **Simulações**, clique em **Importar/Exportar**.
2. Selecione a guia **Exportar**.
3. Copie os detalhes da simulação para a área de transferência ou faça download deles em um arquivo JSON.
