---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-22"

keywords: Cloud IAM Authentication, IAM OAuth token, IBM Watson

subcollection: iot-platform

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:important: .important}


# Autenticação e autorização do {{site.data.keyword.iamshort}} para o {{site.data.keyword.iot_short_notm}} (Beta)
{: #cloud_iam}

<p>Essa coleção de documentação do {{site.data.keyword.cloud}} pertence ao plano de precificação Lite do {{site.data.keyword.iot_full}} e inclui informações básicas de introdução, referências de API e informações gerais de resolução de problemas. 
Para obter a documentação completa do recurso {{site.data.keyword.iot_short_notm}}, consulte a [documentação do produto {{site.data.keyword.iot_short_notm}} ![Ícone de link externo](../../../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) no {{site.data.keyword.IBM_notm}} Knowledge Center. Mais informações sobre os vários planos podem ser localizadas em [{{site.data.keyword.iot_short_notm}} planos de serviço](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview). 
</p>
{: important}

As APIs do {{site.data.keyword.iot_full}} suportam a autenticação e a autorização de usuários usando o {{site.data.keyword.iamshort}} (IAM).

A autenticação e a autorização do {{site.data.keyword.iamlong}} para o {{site.data.keyword.iot_short_notm}} estão disponíveis apenas como parte de um programa beta limitado. Atualizações futuras podem incluir mudanças incompatíveis com a versão atual desse recurso. Experimente e [informe-nos o que acha ![Ícone de link externo](../../../../icons/launch-glyph.svg)](https://developer.ibm.com/answers/smart-spaces/17/internet-of-things.html){: new_window}.
{: important}

O {{site.data.keyword.iamshort}} é desenvolvido no {{site.data.keyword.cloud_notm}} e é usado para autenticar e autorizar usuários administrativos e desenvolvedores que precisam configurar e gerenciar seus serviços da {{site.data.keyword.IBM_notm}}. Os usuários que precisam de acesso ao painel do {{site.data.keyword.iot_short_notm}} são autenticados usando o {{site.data.keyword.iamshort}}. A origem da identidade para o {{site.data.keyword.iamshort}} pode ser usuários IBMid registrados ou um serviço de diretório do cliente que suporta SAML.  

O {{site.data.keyword.iot_short_notm}} também suporta a autenticação de usuários por meio do {{site.data.keyword.appid_short_notm}}. O {{site.data.keyword.appid_short_notm}} é usado para autenticar usuários que precisam de acesso a aplicativos hospedados no {{site.data.keyword.cloud_notm}}. Os usuários do {{site.data.keyword.appid_short_notm}} geralmente não executam atividades administrativas ou de desenvolvimento em um serviço de nuvem. Para obter mais informações, consulte [Autenticação do {{site.data.keyword.appid_short_notm}} para o Watson IoT Platform ![Ícone de link externo](../../../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/app_id.html#app_id){: new_window}.

O IAM permite que os usuários obtenham um token OAuth do IAM e o usem para autenticar chamadas API. Por exemplo, um usuário com a CLI do {{site.data.keyword.containershort_notm}} instalada pode usar o comando a seguir:

` bx iam oauth-tokens `

O comando retorna o token do IAM do usuário com login efetuado no formato a seguir:

`Token do IAM: portador <some token>`

Um usuário também pode usar o terminal do token do IAM para efetuar login e recuperar o token do IAM dele, conforme mostrado no exemplo a seguir:
`curl -s 'https://iam.cloud.ibm.com/identity/token?grant_type=urn:ibm:params:oauth:grant-type:apikey&response_type=cloud_iam&apikey=<apikey>' -H'Content-Type:x-www-form-urlencoded' -XPOST`

Esse exemplo de API usa uma chave de API do IAM para solicitar o token do IAM e retorna o `Bearer <token>`.

Em seguida, quando um usuário chama uma API do {{site.data.keyword.iot_short_notm}}, ele pode fornecer o cabeçalho de autorização `Authorization: Bearer <token>` em suas chamadas de API.

## Gerando um token do IAM
{: #iam_generate}

É possível escolher como automatizar a criação do token do IAM, dependendo do modo de autenticação com o {{site.data.keyword.cloud_notm}} e do tipo de ID do {{site.data.keyword.cloud_notm}} usado.

Se você usar um ID não federado, será possível escolher uma das opções a seguir para criar um token do IAM:
 - **Nome do usuário e senha do {{site.data.keyword.cloud_notm}}:** é possível criar um token para automatizar totalmente a criação de seu token de acesso do IAM.
 - **Gerar uma chave de API do {{site.data.keyword.cloud_notm}}:** use as chaves de API do {{site.data.keyword.cloud_notm}}, que dependem da conta do {{site.data.keyword.cloud_notm}} para a qual são geradas. Não é possível combinar a sua chave API do {{site.data.keyword.cloud_notm}} com um ID da conta diferente no mesmo token do IAM. Para acessar os clusters que foram criados com uma conta diferente daquela na qual a sua chave API do {{site.data.keyword.cloud_notm}} é baseada; deve-se efetuar login na conta para gerar uma nova chave API.

Se você usar um ID federado, será possível escolher uma das opções a seguir para criar um token do IAM:
 - **Gerar uma chave de API do {{site.data.keyword.cloud_notm}}:** as chaves de API do {{site.data.keyword.cloud_notm}} dependem da conta do {{site.data.keyword.cloud_notm}} para a qual são geradas. Não é possível combinar a sua chave API do {{site.data.keyword.cloud_notm}} com um ID da conta diferente no mesmo token do IAM. Para acessar os clusters que foram criados com uma conta diferente daquela na qual a sua chave API do {{site.data.keyword.cloud_notm}} é baseada; deve-se efetuar login na conta para gerar uma nova chave API.
 - **Usar uma senha descartável:** se você se autenticar com o {{site.data.keyword.cloud_notm}} usando uma senha descartável, não será possível automatizar totalmente a criação do token do IAM porque a recuperação da senha descartável requer uma interação manual com o navegador da web. Para automatizar totalmente a criação de seu token do IAM, deve-se criar uma chave API do {{site.data.keyword.cloud_notm}}.

Ao criar seu token de acesso, as informações do corpo incluídas na solicitação variam com base no método de autenticação do {{site.data.keyword.cloud_notm}} usado. Substitua os seguintes valores:
- `<my_username>` = Seu nome de usuário do {{site.data.keyword.cloud_notm}}.
- `<my_password>` = Sua senha do {{site.data.keyword.cloud_notm}}.
- `<my_api_key>` = Sua chave de API do {{site.data.keyword.cloud_notm}}.
- `<my_passcode>` = Sua senha descartável do {{site.data.keyword.cloud_notm}}. Execute `bx login --sso` e siga as instruções em sua saída da CLI para recuperar sua senha única usando seu navegador da web.

Exemplo:
`POST https://iam.<region>.cloud.ibm.com/identity/token`

Para especificar uma região do {{site.data.keyword.cloud_notm}}, revise as abreviações de região usadas nos terminais de API. Consulte [Terminais de API de região do {{site.data.keyword.cloud_notm}} ![Ícone de link externo](../../../../icons/launch-glyph.svg)](https://cloud.ibm.com/docs/containers/cs_regions.html#bluemix_regions){: new_window} para obter mais informações.

Parâmetro de entrada	 | Valores
---------------- | -----------
Header	| Content-Type:application/x-www-form-urlencoded<br>Autorização: Basic Xng7Png=<br>Nota: é fornecido a você `Xng7Png=`, a autorização codificada por URL para o nome de usuário bx e a senha bx.
Corpo para nome do usuário e senha do {{site.data.keyword.cloud_notm}}	|	grant_type: senha<br>response_type: cloud_iam, uaa<br>username:  `<my_username>`<br>senha:  `<my_password>`<br>uaa_client_id: cf<br>uaa_client_Segredo:<br>Nota: inclua a chave uaa_client_secret sem nenhum valor especificado.
Corpo para chaves API do {{site.data.keyword.cloud_notm}}	|	grant_type: urn:ibm:params: oauth:grant-type:apikey<br>response_type: cloud_iam<br>uaa<br>apikey:  `<my_api_key>`<br>uaa_client_id: cf<br>uaa_client_Segredo:<br>Nota: inclua a chave uaa_client_secret sem nenhum valor especificado.
Corpo para senha única do {{site.data.keyword.cloud_notm}}	|	grant_type: urn:ibm:params: oauth:grant-type:passcode<br>response_type: cloud_iam, uaa<br>senha:  `<my_passcode>`<br>uaa_client_id: cf<br>uaa_client_Segredo:<br>Nota: inclua a chave uaa_client_secret sem nenhum valor especificado.

Saída de API de exemplo:

```
{
"access_token": "<iam_token>",
"refresh_token": "<iam_refresh_token>",
"uaa_token": "<uaa_token>",
"uaa_refresh_token": "<uaa_refresh_token>",
"token_type": "Bearer",
"expires_in": 3600,
"expiration": 1493747503
}
```
É possível localizar o token IAM no campo **access_token** de sua saída da API.

O exemplo a seguir mostra como usar o token do IAM ao chamar APIs.

```
GET https://org.domain/api/v0002/bulk/devices
```

Parâmetro de entrada   |	Valores
----------------- | -----------
Cabeçalhos	|	Content-Type: application / json<br>Autorização: bearer  `<iam_token>`
