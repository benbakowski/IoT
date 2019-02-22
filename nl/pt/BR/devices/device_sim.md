---

copyright:
  years: 2017, 2019
lastupdated: "2019-02-13"
---

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

<p>Essa coleção de documentação do {{site.data.keyword.Bluemix}} pertence ao plano de precificação Lite do {{site.data.keyword.iot_full}} e inclui informações básicas de introdução, referências de API e informações gerais de resolução de problemas. 
Para a documentação de recurso integral do {{site.data.keyword.iot_short_notm}}, consulte a [documentação do produto do {{site.data.keyword.iot_short_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) no IBM Knowledge Center. Mais informações sobre os vários planos podem ser localizadas em [{{site.data.keyword.iot_short_notm}} planos de serviço](/docs/IoT/plans_overview.html#plans_overview). 
</p>
{: important}

Usando o simulador de configurar do {{site.data.keyword.iot_full}}, é
possível configurar eventos simulados para dispositivos. É possível usar os dados do
evento simulados para conhecer, testar e demonstrar os recursos do
{{site.data.keyword.iot_short_notm}} totalmente funcionais.
{: shortdesc}

É possível usar tipos de dispositivo e dispositivos existentes e o simulador permitirá gerar novos dispositivos para tipos existentes. Você pode configurar os detalhes
do evento para cada dispositivo ou definir uma configuração padrão que é aplicada a
todos os dispositivos. É possível exportar uma configuração do evento simulada para que
ela possa ser reutilizada ou compartilhada para configurar outras simulações.

Para simular dados do dispositivo:

1. Efetue login no {{site.data.keyword.iot_short_notm}}.
2. Na área de janela de navegação principal, selecione **Configurações**.
3. Na seção **Dados e dispositivos**, ative o simulador de dispositivo.
4. Na área de janela de navegação principal, selecione **Dispositivos**. Uma
mensagem no canto inferior direito da tela indica que nenhuma simulação está em execução.
5. Clique na mensagem "0 simulações em execução".
6. Na janela pop-up **Simulações**, clique em **Criar simulação**.
7. Selecione um tipo de dispositivo existente para o qual você deseja simular dados ou crie um novo tipo de dispositivo digitando o nome do tipo de dispositivo.
8. Clique em **Importar/Exportar simulação** para usar uma configuração existente ou configure manualmente os detalhes da simulação para o tipo de dispositivo:
   1. Clique em **+ Novo tipo de evento** para incluir um tipo de evento no tipo de dispositivo.
   2. Insira um nome para o tipo de evento.
   3. Em **Planejamento**, configure a frequência do evento.
   3. Edite os detalhes do tipo de evento no formato JSON e salve o tipo de evento atualizado.

   <p> É possível usar as variáveis especiais a seguir ao configurar eventos:  
        - `range`: essa variável é substituída por um número aleatório que está entre os dois valores fornecidos, por exemplo: `{"random": range(300, 100)}`  
        - `$counter`: essa variável é substituída pelo número de dispositivos incluídos no simulador do tipo atual, por exemplo: `{"total": $counter}`  
        - `increment`: essa variável indica o número inicial e o incremento pelo qual ele aumenta, por exemplo, `{"myNumber": increment(10, 1)}`. Nesse caso, `myNumber` se inicia em 10 e aumenta em 1 cada vez que uma carga útil é enviada (10, 11, 12 e assim por diante).</p>
   {: tip}

9. Selecione um dispositivo registrado para a simulação ou crie um novo dispositivo digitando o nome do dispositivo.
10. Para criar mais simulações, clique em **Nova simulação** e repita as etapas de configuração para cada dispositivo ao qual você deseja aplicar configurações customizadas. A mensagem na parte inferior direita da tela mostra o número de simulações ativas.
11. **Opcional:** Depois de configurar simulações para
dispositivos, exporte os detalhes de simulação para que eles possam ser reutilizados ou
compartilhados:
    1. Na janela pop-up **Simulações**, clique em **Importar/Exportar**.
    2. Selecione a guia **Exportar**.
    3. Copie os detalhes da simulação para a área de transferência ou faça download deles em um arquivo JSON.
12. Na página **Dispositivos**, navegue para um dos
dispositivos simulados e selecione a guia **Eventos recentes** para
verificar se os eventos simulados estão funcionando.
