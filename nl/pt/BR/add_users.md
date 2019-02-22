---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:important: .important}

# Gerenciando o acesso de usuário
{: #managing-user-access}

<p>Essa coleção de documentação do {{site.data.keyword.Bluemix}} pertence ao plano de precificação Lite do {{site.data.keyword.iot_full}} e inclui informações básicas de introdução, referências de API e informações gerais de resolução de problemas. 
Para a documentação de recurso integral do {{site.data.keyword.iot_short_notm}}, consulte a [documentação do produto do {{site.data.keyword.iot_short_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) no IBM Knowledge Center. Mais informações sobre os vários planos podem ser localizadas em [{{site.data.keyword.iot_short_notm}} planos de serviço](/docs/IoT/plans_overview.html#plans_overview). 
</p>
{: important}

Na página Membros do painel, é possível controlar e gerenciar o acesso à organização do {{site.data.keyword.iot_full}}. É possível adicionar usuários incluindo-os, convidando-os ou importando-os. Também é possível fornecer diferentes níveis de acesso a seus usuários, designando funções.
{:shortdesc}

## Adicionando usuários
{: #adding-new-users}

Na página **Membros** do painel, é possível incluir membros individuais usando a função Incluir. Também é possível incluir membros simultaneamente
usando a função Importar.

Por padrão, contas dos membros não expiram. Ao incluir usuários na organização do {{site.data.keyword.iot_short_notm}}, é possível opcionalmente configurar uma data de expiração para sua conta.

### Incluindo membros em sua organização do {{site.data.keyword.iot_short_notm}}

Para incluir um membro em sua organização, você precisará do IBMid do membro. Para incluir um membro, você não precisa de confirmação do membro.

Para incluir um único membro em sua organização do {{site.data.keyword.iot_short_notm}}:
1. Em seu painel do {{site.data.keyword.iot_short_notm}}, clique em **Membros** na barra de navegação.
2. Clique em **Incluir membros** e selecione a guia **Incluir**.
3. Insira o IBMid do membro.
4. Selecione uma função para o membro.
5. Opcional: configure uma data de expiração.
6. Clique em **Incluir**.

Para incluir vários membros simultaneamente, deve-se fazer upload de um arquivo `.csv` que contenha o IBMid, a função e a data de expiração opcional de cada membro. Para obter informações, veja [Construindo seu arquivo CSV](#constructing-your-csv).
1. Em seu painel do {{site.data.keyword.iot_short_notm}}, clique em **Membros** na barra de navegação.
2. Clique em **Incluir membros** e selecione a guia **Importar**.
3. Procure seus arquivos ou arraste o arquivo `.csv` para a janela **Fazer upload do CSV**.
4. Selecione uma função padrão para usar se uma função especificada no arquivo CSV não for reconhecida.
5. Mapeie os números de coluna em seu arquivo CSV para as entradas de IBMid, função e data de expiração opcionais correspondentes.
6. Selecione o separador de colunas de vírgula ou ponto-e-vírgula apropriado para corresponder ao separador usado no arquivo `.csv`.
7. Clique em **Importar** para importar os IBMids e criar os membros.


### Construindo seu arquivo CSV
{: #constructing-your-csv}

Ao construir um arquivo CSV para importar membros para sua organização, assegure que sejam incluídas as informações necessárias para o método que você está usando. Use vírgulas ou pontos e vírgulas para separar colunas.  
**Importante:** ao fazer upload do arquivo CSV, em **Configurações de CSV**, assegure-se de selecionar o separador de colunas correto.

Arquivo de CSV de amostra com delimitação por vírgula:  
```
user1@sample.com,PD_DEVELOPER_USER,2018-03-13
user2@sample.com,PD_OPERATOR_USER,2018-03-13
user3@sample.com,PD_ADMIN_USER,2018-03-13
```
Em que as entradas de coluna a seguir são usadas:  
- Coluna 1: o endereço de e-mail do usuário.  
Se você estiver incluindo membros, certifique-se de usar o endereço de e-mail correspondente a um IBMid válido. Se você estiver convidando membros, será possível usar qualquer endereço de e-mail válido.
- Coluna 2: a função a ser designada ao usuário.  
Insira uma das funções a seguir:
 - PD_ADMIN_USER
 - PD_OPERATOR_USER
 - PD_DEVELOPER_USER
 - PD_ANALYST_USER
 - PD_READER_USER  
 Para obter mais informações sobre funções de usuário, consulte [Funções de usuário, de aplicativo e de gateway ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/roles_index.html#user_roles){: new_window}.
- Coluna 3: a data ISO 6801 (por exemplo, `2018-03-13`) que corresponde
à data de expiração do usuário.

## Editando usuários
{: #editing-users}

Os usuários podem ser editados para mudar sua função, incluir, remover ou mudar uma data de expiração de acesso ou incluir ou remover o acesso à organização.

1. Em seu painel do {{site.data.keyword.iot_short_notm}}, clique em **Membros** na barra de navegação.
2. Clique no ícone **Editar** próximo ao usuário que você deseja editar.
3. Faça as mudanças desejadas no usuário.
4. Clique em **Salvar**.

## Bloqueando o acesso de usuário
{: #blocking-users}

Os usuários podem ser bloqueados contra o acesso à organização do {{site.data.keyword.iot_short_notm}}, enquanto ainda mantêm a associação à organização.

1. Em seu painel do {{site.data.keyword.iot_short_notm}}, clique em **Membros** na barra de navegação.
2. Clique na alternância próxima ao usuário que você deseja bloquear contra o acesso à organização do {{site.data.keyword.iot_short_notm}}.

## Limitando o acesso de usuário
{: #limiting-users}

O controle de acesso no nível de recursos permite limitar o acesso a dispositivos em uma organização. É possível usar grupos de recursos para especificar os
dispositivos que cada usuário ou chave API pode gerenciar. Para obter informações sobre como configurar o controle de acesso no nível de recursos, consulte [Configurando o controle de acesso no nível de recursos ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/reference/rlac.html#configure_RLAC){: new_window}.

## Removendo usuários
{: #removing-users}

Os usuários podem ser removidos completamente da organização do {{site.data.keyword.iot_short_notm}}. A remoção dos usuários não pode ser desfeita e os usuários devem ser [incluídos na plataforma](#adding-new-users) para restaurar o acesso.

1. Em seu painel do {{site.data.keyword.iot_short_notm}}, clique em **Membros** na barra de navegação.
2. Clique no ícone **Excluir** ao lado do usuário a ser removido.
3. Clique em **Excluir** na caixa de diálogo de confirmação.
