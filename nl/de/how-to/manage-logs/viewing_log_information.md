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

# Protokollinformationen anzeigen
{: #viewing_log_status}

Mit dem Befehl [cf logging status](/docs/services/CloudLogAnalysis/reference/logging_cli.html#status) können Sie Informationen zu den Protokollen abrufen, die in 'Log Collection' erfasst und gespeichert werden.
{:shortdesc}

## Informationen zu Protokollen über einen Zeitraum abrufen
{: #viewing_logs}

Mit dem Befehl `cf logging status` können Sie für die in 'Log Collection' gespeicherten Protokolle die Größe, die Anzahl und die Protokolltypen anzeigen - und Sie können ermitteln, ob die Protokolle für die Analyse in Kibana verfügbar sind oder nicht. 

Verwenden Sie den Befehl `cf logging status` mit der Option **-s**, um den Starttag festzulegen, oder mit der Option **-e**, um den Endtag festzulegen. Beispiel:

* `cf logging status` stellt Informationen für die letzten zwei Wochen bereit.
* `cf logging status -s 2017-05-03` stellt Informationen vom 3. Mai 2017 bis zum aktuellen Datum bereit.
* `cf logging status -s 2017-05-03 -e 2017-05-08` stellt Informationen für den Zeitraum vom 3. Mai 2017 bis zum 8. Mai 2017 bereit. 

1. Melden Sie sich unter {{site.data.keyword.Bluemix_notm}} an einer Region, einer Organisation und einem Bereich an. 

    Führen Sie zum Beispiel den folgenden Befehl aus, um sich an der Region 'USA (Süden)' anzumelden: 
	
    ```
    cf login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. Führen Sie den Befehl *status* aus.

    ```
    $ cf logging status
    ```
    {: codeblock}
    
    Beispiel:
    
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


## Informationen zu einem Protokolltyp über einen Zeitraum abrufen
{: #viewing_logs_by_log_type}

Um Informationen zu einem Protokolltyp über eine bestimmten Zeitraum zu erhalten, verwenden Sie den Befehl `cf logging status`  und legen Sie die Option **-t** für den Protokolltyp, **-s** für das Startdatum und **-e** für das Enddatum fest. Beispiel:

* `cf logging status -t syslog` stellt Informationen zu Protokollen des Typs *syslog* für die beiden letzten Wochen bereit.
* `cf logging status -s 2017-05-03 -t syslog` stellt Informationen zu Protokollen des Typs *syslog* vom 3. Mai 2017 bis zum aktuellen Datum bereit.
* `cf logging status -s 2017-05-03 -e 2017-05-08 -t syslog` stellt Informationen zu Protokollen des Typs *syslog* für den Zeitraum vom 3. Mai 2017 bis zum 8. Mai 2017 bereit. 

1. Melden Sie sich unter {{site.data.keyword.Bluemix_notm}} an einer Region, einer Organisation und einem Bereich an. 

    Führen Sie zum Beispiel den folgenden Befehl aus, um sich an der Region 'USA (Süden)' anzumelden: 
	
    ```
    cf login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. Führen Sie den Befehl *status* aus.

    ```
    $ cf logging status -s JJJJ-MM-TT -e JJJJ-MM-TT -t *Log_Type*
    ```
    {: codeblock}
    
    Dabei gilt:
    
    * *-s* wird verwendet, um das Startdatum in Universal Coordinated Time (UTC) festzulegen: *JJJJ-MM-TT*
    * *-e* wird verwendet, um das Enddatum in Universal Coordinated Time (UTC) festzulegen: *JJJJ-MM-TT*
    * *-t* wird verwendet, um den Protokolltyp festzulegen.
    
    Sie können mehrere Protokolltypen angeben, indem Sie die einzelnen Typen durch Kommas trennen. Beispiel: **Protokolltyp_1,Protokolltyp_2,Protokolltyp_3**. 
    
    Beispiel:
    
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



## Kontoinformationen zu Protokollen abrufen
{: #viewing_logs_account}

Um Informationen zu Protokollen über einen bestimmten Zeitraum für das gesamte {{site.data.keyword.Bluemix_notm}}-Konto abzurufen, verwenden Sie den Befehl `cf logging status` mit der Option **-a**. Sie können außerdem die Optionen **-t** für den Protokolltyp, **-s** für das Startdatum und **-e** für das Enddatum festlegen. 

1. Melden Sie sich unter {{site.data.keyword.Bluemix_notm}} an einer Region, einer Organisation und einem Bereich an. 

    Führen Sie zum Beispiel den folgenden Befehl aus, um sich an der Region 'USA (Süden)' anzumelden: 
	
    ```
    cf login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. Führen Sie den Befehl *status* aus.

    ```
    $ cf logging status -a -s JJJJ-MM-TT -e JJJJ-MM-TT -t *Protokolltyp*
    ```
    {: codeblock}
    
    Dabei gilt:
    
    * *-a* wird zur Angabe von Kontoinformationen verwendet.
    * *-s* wird verwendet, um das Startdatum in Universal Coordinated Time (UTC) festzulegen: *JJJJ-MM-TT*
    * *-e* wird verwendet, um das Enddatum in Universal Coordinated Time (UTC) festzulegen: *JJJJ-MM-TT*
    * *-t* wird verwendet, um den Protokolltyp festzulegen.
    

    Sie können mehrere Protokolltypen angeben, indem Sie die einzelnen Typen durch Kommas trennen. Beispiel: **Protokolltyp_1,Protokolltyp_2,Protokolltyp_3**. 
 
    Beispiel:
    
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














