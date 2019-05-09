---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-05"

keywords: user access, Add function, members dashboard

subcollection: iot-platform

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:important: .important}

# ユーザーのアクセス権限の管理
{: #managing-user-access}

<p>この {{site.data.keyword.cloud}} 資料コレクションは、{{site.data.keyword.iot_full}} ライトの料金プランが対象になっていて、基本的な入門情報や、API リファレンス、一般的なトラブルシューティング情報が含まれています。
全ての {{site.data.keyword.iot_short_notm}} 機能の資料については、IBM Knowledge Center 上の [{{site.data.keyword.iot_short_notm}} 製品資料 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) を参照してください。 各種プランの詳細については、[{{site.data.keyword.iot_short_notm}} のサービス・プラン](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview)を参照してください。 
</p>
{: important}

ダッシュボードの「メンバー」ページから、{{site.data.keyword.iot_full}} 組織に対するアクセス権限を制御したり管理したりできます。 ユーザーを追加する方法には、追加、招待、インポートがあります。 また、役割の割り当てによって、さまざまなレベルのアクセス権限をユーザーに付与できます。
{:shortdesc}

## ユーザーの追加
{: #adding-new-users}

ダッシュボードの**「メンバー」**ページで、「追加」機能を使用してメンバーを個別に追加できます。 また、「インポート」機能を使用して、同時に複数のメンバーを追加することも可能です。

デフォルトでは、メンバー・アカウントに有効期限はありません。 ユーザーを {{site.data.keyword.iot_short_notm}} 組織に追加するときに、オプションでユーザー・アカウントの有効期限日付を設定できます。

### {{site.data.keyword.iot_short_notm}} 組織へのメンバーの追加

組織にメンバーを追加するには、メンバーの IBMid が必要です。 メンバーを追加するときに、そのメンバーからの確認は不要です。

1 人のメンバーを {{site.data.keyword.iot_short_notm}} 組織に追加するには、次の手順を実行します。
1. {{site.data.keyword.iot_short_notm}} ダッシュボードのナビゲーション・バーから**「メンバー」**をクリックします。
2. **「メンバーの追加」**をクリックし、**「追加」**タブを選択します。
3. メンバーの IBMid を入力します。
4. メンバーの役割を選択します。
5. オプション: 有効期限日付を設定します。
6. **「追加」**をクリックします。

複数のメンバーを同時に追加するには、各メンバーの IBMid、役割、(オプションの) 有効期限日付が含まれた `.csv` ファイルをアップロードする必要があります。 詳しくは、[CSV ファイルの作成](#constructing-your-csv)を参照してください。
1. {{site.data.keyword.iot_short_notm}} ダッシュボードのナビゲーション・バーから**「メンバー」**をクリックします。
2. **「メンバーの追加」**をクリックし、**「インポート」**タブを選択します。
3. ファイルを参照するか、`.csv` ファイルを**「CSV のアップロード (Upload CSV)」**ウィンドウにドラッグします。
4. CSV ファイルで指定されている役割が認識されない場合に使用する、デフォルトの役割を選択します。
5. CSV ファイル内の列番号を、対応する IBMid、役割、有効期限日付 (オプション) のエントリーにマップします。
6. `.csv` ファイルで使用されている列区切り文字と一致する区切り文字 (コンマまたはセミコロン) を選択します。
7. **「インポート」**をクリックして IBMids をインポートし、メンバーを作成します。


### CSV ファイルの作成
{: #constructing-your-csv}

複数のメンバーを組織にインポートするために CSV ファイルを作成するときには、使用する方式に応じて必要な情報を含めてください。 列の区切りには、コンマまたはセミコロンを使用します。  
**重要:** CSV ファイルをアップロードするときに、**「CSV 設定 (CSV settings)」**で、列の区切り文字として正しいものを選択してください。

コンマ区切りのサンプル CSV ファイル:  
```
user1@sample.com,PD_DEVELOPER_USER,2018-03-13
user2@sample.com,PD_OPERATOR_USER,2018-03-13
user3@sample.com,PD_ADMIN_USER,2018-03-13
```
ここでは次の列エントリーが使用されています。  
- 1 列目: ユーザーの E メール・アドレス。  
メンバーを追加する場合は、有効な IBMid に対応する E メール・アドレスを使用していることを確認してください。 メンバーを招待する場合は、任意の有効な E メール・アドレスを使用できます。
- 2 列目: ユーザーに割り当てられる役割。  
以下のいずれかの役割を入力します。
 - PD_ADMIN_USER
 - PD_OPERATOR_USER
 - PD_DEVELOPER_USER
 - PD_ANALYST_USER
 - PD_READER_USER  
 ユーザー役割について詳しくは、[ユーザー、アプリケーション、ゲートウェイの役割 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/roles_index.html#user_roles){: new_window} を参照してください。
- 3 列目: ユーザーの有効期限日付に対応する ISO 6801 日付 (例: `2018-03-13`)。

## ユーザーの編集
{: #editing-users}

ユーザーを編集して、役割の変更、アクセス権限の有効期限の追加、削除、変更、または組織へのアクセス権限の追加、削除を行うことができます。

1. {{site.data.keyword.iot_short_notm}} ダッシュボードのナビゲーション・バーから**「メンバー」**をクリックします。
2. 編集するユーザーの横にある**「編集」**アイコンをクリックします。
3. ユーザーに対して必要な変更を行います。
4. **「保存」**をクリックします。

## ユーザー・アクセスのブロック
{: #blocking-users}

組織のメンバーシップは保持したままで、ユーザーによる {{site.data.keyword.iot_short_notm}} 組織へのアクセスをブロックすることができます。

1. {{site.data.keyword.iot_short_notm}} ダッシュボードのナビゲーション・バーから**「メンバー」**をクリックします。
2. {{site.data.keyword.iot_short_notm}} 組織へのアクセスをブロックするユーザーの横にあるトグルをクリックします。

## ユーザー・アクセスの制限
{: #limiting-users}

リソース・レベル・アクセス制御を行うことによって、組織内のデバイスへのアクセスを制限できます。 リソース・グループを使用して、各ユーザーまたは API キーが管理できるデバイスを指定できます。 リソース・レベル・アクセス制御の構成方法については、 [リソース・レベル・アクセス制御の構成 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/reference/rlac.html#configure_RLAC){: new_window} を参照してください。

## ユーザーの削除
{: #removing-users}

ユーザーを {{site.data.keyword.iot_short_notm}} 組織から完全に削除することができます。 ユーザーを削除すると、元に戻すことはできません。アクセス権限を復元するためには、ユーザーを[プラットフォームに追加する](#adding-new-users)必要があります。

1. {{site.data.keyword.iot_short_notm}} ダッシュボードのナビゲーション・バーから**「メンバー」**をクリックします。
2. 削除するユーザーの横にある**「削除」**アイコンをクリックします。
3. 確認のダイアログ・ボックスで**「削除」**をクリックします。
