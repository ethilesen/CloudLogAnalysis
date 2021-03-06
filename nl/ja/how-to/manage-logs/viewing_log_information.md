---

copyright:
  years: 2017
lastupdated: "2017-07-19"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# ログ情報の表示
{: #viewing_log_status}

収集されて Log Collection に保管されたログに関する情報を取得するには、[cf logging status](/docs/services/CloudLogAnalysis/reference/logging_cli.html#status) コマンドを使用します。
{:shortdesc}

## 特定の期間のログに関する情報の取得
{: #viewing_logs}

Log Collection に保管されたログについて、サイズ、カウント、ログ・タイプ、および、Kibana での分析に使用可能かどうかを表示するには、`cf logging status` コマンドを使用します。 

オプション **-s** で開始日を、**-e** で終了日を設定して、`cf logging status` コマンドを使用します。例えば次のようにします。

* `cf logging status` を使用すると、最近 2 週間の情報が提供されます。
* `cf logging status -s 2017-05-03` を使用すると、2017 年 5 月 3 日から現在日付までの情報が提供されます。
* `cf logging status -s 2017-05-03 -e 2017-05-08` を使用すると、2017 年 5 月 3 日から 2017 年 5 月 8 日までの情報が提供されます。 

1. {{site.data.keyword.Bluemix_notm}} 地域、組織、およびスペースにログインします。 

    例えば、米国南部地域にログインするには、以下のコマンドを実行します。
	
    ```
cf login -a https://api.ng.bluemix.net
```
    {: codeblock}
    
2. *status* コマンドを実行します。

    ```
    $ cf logging status
    ```
    {: codeblock}
    
    以下に例を示します。
    
    ```
    $ cf logging status
    +------------+--------+-------+--------------------+------------+
    |    DATE    |  COUNT | SIZE  |       TYPES        | SEARCHABLE |
    +------------+--------+-------+--------------------+------------+
    | 2017-05-24 |    16  | 3020  |        log         |   None     |
    +------------+--------+-------+--------------------+------------+
    | 2017-05-25 |   1224 | 76115 | linux_syslog,log   |    All     |
    +------------+--------+-------+--------------------+------------+
    ```
    {: screen}


## 特定の期間のログのタイプに関する情報の取得
{: #viewing_logs_by_log_type}

特定の期間のログのタイプに関する情報を取得するには、`cf logging status` コマンドを使用し、その際、オプション **-t** でログのタイプを指定し、**-s** で開始日を、**-e** で終了日を設定します。以下に例を示します。

* `cf logging status -t syslog` を使用すると、タイプ *syslog* の最近 2 週間のログに関する情報が提供されます。
* `cf logging status -s 2017-05-03 -t syslog` を使用すると、タイプ *syslog* の 2017 年 5 月 3 日から現在日付までのログに関する情報が提供されます。
* `cf logging status -s 2017-05-03 -e 2017-05-08 -t syslog` を使用すると、タイプ *syslog* の 2017 年 5 月 3 日から 2017 年 5 月 8 日までのログに関する情報が提供されます。 

1. {{site.data.keyword.Bluemix_notm}} 地域、組織、およびスペースにログインします。 

    例えば、米国南部地域にログインするには、以下のコマンドを実行します。
	
    ```
cf login -a https://api.ng.bluemix.net
```
    {: codeblock}
    
2. *status* コマンドを実行します。

    ```
    $ cf logging status -s YYYY-MM-DD -e YYYY-MM-DD -t *Log_Type*
    ```
    {: codeblock}
    
    各部分の説明:
    
    * *-s* は、開始日を協定世界時 (UTC) で設定するために使用されます: *YYYY-MM-DD*
    * *-e* は、終了日を協定世界時 (UTC) で設定するために使用されます: *YYYY-MM-DD*
    * *-t* は、ログ・タイプを設定するために使用されます。
    
    各タイプをコンマで区切ることによって複数のログ・タイプを指定できます (例: **log_type_1,log_type_2,log_type_3**)。 
    
    以下に例を示します。
    
    ```
    $ cf logging status -s 2017-05-24 -e 2017-05-25 -t log
    +------------+--------+-------+--------------------+------------+
    |    DATE    |  COUNT | SIZE  |       TYPES        | SEARCHABLE |
    +------------+--------+-------+--------------------+------------+
    | 2017-05-24 |    16  | 3020  |        log         |   None     |
    +------------+--------+-------+--------------------+------------+
    | 2017-05-25 |   1224 | 76115 |        log         |    All     |
    +------------+--------+-------+--------------------+------------+
    ```
    {: screen}



## ログに関するアカウント情報の取得
{: #viewing_logs_account}

特定の期間の {{site.data.keyword.Bluemix_notm}} アカウントでのログに関する情報を取得するには、オプション **-a** を指定して `cf logging status` コマンドを使用します。オプション **-t** でログのタイプを指定し、**-s** で開始日を、**-e** で終了日を設定することもできます。 

1. {{site.data.keyword.Bluemix_notm}} 地域、組織、およびスペースにログインします。 

    例えば、米国南部地域にログインするには、以下のコマンドを実行します。
	
    ```
cf login -a https://api.ng.bluemix.net
```
    {: codeblock}
    
2. *status* コマンドを実行します。

    ```
    $ cf logging status -a -s YYYY-MM-DD -e YYYY-MM-DD -t *Log_Type*
    ```
    {: codeblock}
    
    各部分の説明:
    
    * *-a* は、アカウント・レベルの情報を指定するために使用されます。
    * *-s* は、開始日を協定世界時 (UTC) で設定するために使用されます: *YYYY-MM-DD*
    * *-e* は、終了日を協定世界時 (UTC) で設定するために使用されます: *YYYY-MM-DD*
    * *-t* は、ログ・タイプを設定するために使用されます。
    

    各タイプをコンマで区切ることによって複数のログ・タイプを指定できます (例: **log_type_1,log_type_2,log_type_3**)。 
 
    以下に例を示します。
    
    ```
    $ cf logging status -s 2017-05-24 -e 2017-05-25 -t log -a
    +------------+--------+-------+--------------------+------------+
    |    DATE    |  COUNT | SIZE  |       TYPES        | SEARCHABLE |
    +------------+--------+-------+--------------------+------------+
    | 2017-05-24 |    16  | 3020  |        log         |   None     |
    +------------+--------+-------+--------------------+------------+
    | 2017-05-25 |   1224 | 76115 |        log         |    All     |
    +------------+--------+-------+--------------------+------------+
    ```
    {: screen}














