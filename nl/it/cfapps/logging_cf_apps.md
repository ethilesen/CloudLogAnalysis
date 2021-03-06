---

copyright:
  years: 2017

lastupdated: "2017-07-19"

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}

# Registrazione per le applicazioni Cloud Foundry in Bluemix
{: #logging_bluemix_cf_apps}

In {{site.data.keyword.Bluemix}}, puoi visualizzare, filtrare e analizzare i log Cloud Foundry (CF) attraverso il dashboard {{site.data.keyword.Bluemix_notm}}, Kibana e l'interfaccia riga di comando. Inoltre, puoi trasmettere i record dei log a uno strumento di gestione log esterno. 
{:shortdesc}

{{site.data.keyword.Bluemix_notm}} registra i dati di log generati dalla piattaforma Cloud Foundry e dalle applicazioni Cloud Foundry. Nei log, puoi visualizzare gli errori, le avvertenze e i messaggi informativi che vengono generati per la tua applicazione. 

Quando esegui le tue applicazioni in un PaaS (platform-as-a-service) cloud come Cloud Foundry su {{site.data.keyword.Bluemix_notm}}, non puoi stabilire un tunnel SSH o FTP nell'infrastruttura in cui sono in esecuzione le tue applicazioni per accedere ai log. La piattaforma è controllata dal provider del cloud. Le applicazioni Cloud Foundry in esecuzione su {{site.data.keyword.Bluemix_notm}} utilizzano il componente Loggerator per inoltrare i record di log dall'interno dell'infrastruttura Cloud Foundry. Loggregator raccoglie automaticamente i dati STDOUT e STDERR. Puoi visualizzare e analizzare questi log attraverso il dashboard {{site.data.keyword.Bluemix_notm}}, Kibana e l'interfaccia riga di comando.

La seguente figura mostra una visualizzazione di alto livello della registrazione per {{site.data.keyword.Bluemix_notm}}:

![Panoramica dei componenti di alto livello per le applicazioni CF](images/logging_cf_apps_ov.gif "Panoramica dei componenti di alto livello per le applicazioni CF")
 
La registrazione delle applicazioni Cloud Foundry viene abilitata automaticamente quando utilizzi l'infrastruttura Cloud Foundry per eseguire le tue applicazioni su {{site.data.keyword.Bluemix_notm}}. Per visualizzare i log del runtime Cloud Foundry, devi scrivere i tuoi log in STDOUT e STDERR. Per maggiori informazioni, vedi [Registrazione delle applicazioni di runtime attraverso le applicazioni CF](/docs/services/CloudLogAnalysis/cfapps/logging_writing_to_log_from_cf_app.html#logging_writing_to_log_from_cf_app).

{{site.data.keyword.Bluemix_notm}} conserva una quantità limitata di informazioni di log. Quando si registrano le informazioni, i dati precedenti vengono sostituiti con le informazioni più recenti. Se devi rispettare le politiche organizzative o di settore che richiedono di mantenere una parte o tutte le informazioni di log per scopi di controllo o altro, puoi trasmettere i tuoi log a un host di log esterno, quale un servizio di gestione log di terze parti o un altro host. Per maggiori informazioni, vedi [Configurazione di host log esterno](/docs/services/CloudLogAnalysis/external/logging_external_hosts.html#thirdparty_logging).

## Inserimento log
{: #log_ingestion}

Il servizio {{site.data.keyword.loganalysisshort}} offre diversi piani. Ogni piano definisce se è possibile o meno accedere alla raccolta dei log. Tutti i piani, con l'eccezione del piano *Lite*, includono la capacità di inviare log alla raccolta dei log. Per ulteriori informazioni sui piani, vedi [Piani di servizio](/docs/services/CloudLogAnalysis/log_analysis_ov.html#plans).

Puoi inviare log in {{site.data.keyword.loganalysisshort}} utilizzando il logstash forwarder a più tenant. Per maggiori informazioni, vedi [Invia dati di log utilizzando un logstash forwarder a più tenant (mt-logstash-forwarder)](/docs/services/CloudLogAnalysis/how-to/send-data/send_data_mt.html#send_data_mt).


## Raccolta di log
{: #log_collection}

Per impostazione predefinita, {{site.data.keyword.Bluemix_notm}} archivia i dati dei log nella ricerca log per 3 giorni:   

* Viene archiviato un massimo di 500MB per spazio di dati al giorno. Tutti i log che superano i 500 MB vengono scartati. Le assegnazioni dei limiti vengono
reimpostate ogni giorno alle ore 12:30 UTC.
* Sono ricercabili fino a 1,5 GB di dati per una massimo di 3 giorni. Viene eseguito il rollover (la prima voce inserita è la prima a essere eliminata) dei dati di log quando vengono raggiunti i 1,5 GB di dati o vengono superati i 3 giorni.

Il servizio {{site.data.keyword.loganalysisshort}} fornisce ulteriori piani che ti consentono di archiviare i log nella raccolta dei log per quanto tempo desideri. Per ulteriori informazioni sul prezzo di ogni piano, vedi [Piani di servizio](/docs/services/CloudLogAnalysis/log_analysis_ov.html#plans).

Puoi configurare una politica di conservazione log che puoi utilizzare per definire il numero di giorni in cui desideri conservare i log nella raccolta dei log. Per maggiori informazioni, vedi [Politica di conservazione log](/docs/services/CloudLogAnalysis/log_analysis_ov.html#policies).


## Ricerca log
{: #log_search}

Per impostazione predefinita, puoi utilizzare Kibana per ricercare fino a 500 MB di log al giorno in {{site.data.keyword.Bluemix_notm}}. 

Il servizio {{site.data.keyword.loganalysisshort}} fornisce più piani. Ogni piano ha diverse capacità di ricerca log, ad esempio, il piano *Raccolta di log* ti consente di ricercare fino a 1 GB di dati al giorno. Per ulteriori informazioni sui piani, vedi [Piani di servizio](/docs/services/CloudLogAnalysis/log_analysis_ov.html#plans).


## Metodi per analizzare i log dell'applicazione CF
{: #logging_bluemix_cf_apps_log_methods}

Puoi scegliere uno dei seguenti metodi per analizzare i log della tua applicazione Cloud Foundry:

* Analizza il log in {{site.data.keyword.Bluemix_notm}} per visualizzare l'ultima attività dell'applicazione.
    
    In {{site.data.keyword.Bluemix_notm}}, puoi visualizzare, filtrare e analizzare i log attraverso la scheda **Log** disponibile per ogni applicazione Cloud Foundry. Per maggiori informazioni, vedi [Analisi dei log dell'applicazione CF dal dashboard Bluemix](/docs/services/CloudLogAnalysis/logging_view_dashboard.html#analyzing_logs_bmx_ui).
    
* Analizza i log in Kibana per eseguire attività di analisi avanzate.
    
    In {{site.data.keyword.Bluemix_notm}}, puoi utilizzare Kibana, una piattaforma di analisi e visualizzazione open source, per monitorare, ricercare, analizzare e visualizzare i tuoi dati in una varietà di grafici, ad esempio, diagrammi e tabelle. Per maggiori informazioni, vedi [Analisi dei log in Kibana](/docs/services/CloudLogAnalysis/kibana/analyzing_logs_Kibana.html#analyzing_logs_Kibana).
	
	**Suggerimento:** Per avviare Kibana, vedi [Passaggio a Kibana dal dashboard di un'applicazione CF](/docs/services/CloudLogAnalysis/kibana/launch.html#launch_Kibana_from_cf_app).

* Analizza i log attraverso la CLI per utilizzare i comandi per la gestione dei log a livello di programmazione.
    
    In {{site.data.keyword.Bluemix_notm}}, puoi visualizzare, filtrare e analizzare i log attraverso l'interfaccia della riga di comando utilizzando il comando **cf logs**. Per maggiori informazioni, vedi [Analisi dei log dell'applicazione Cloud Foundry dall'interfaccia riga di comando](/docs/services/CloudLogAnalysis/logging_view_cli.html#analyzing_logs_cli).


## Origini log per le applicazioni CF distribuite a Diego
{: #cf_apps_log_sources_diego}

Per le applicazioni CF (Cloud Foundry) distribuite nell'architettura Cloud Foundry basata su Diego, sono disponibili le seguenti origini log:
    
| Origine log | Nome componente | Descrizione | 
|------------|----------------|-------------|
| LGR | Loggregator | Il componente LGR fornisce informazioni relative al Loggregator Cloud Foundry, che inoltra i log dall'interno di Cloud Foundry. |
| RTR | Router | Il componente RTR fornisce informazioni sulle richieste HTTP a un'applicazione. | 
| STG | In fase di preparazione | Il componente STG fornisce informazioni su come viene preparata o ripreparata un'applicazione. | 
| APP | Applicazione | Il componente APP fornisce i log dall'applicazione. Qui è dove vengono mostrati i stderr e stdout nel tuo codice. | 
| API | API Cloud Foundry | Il componente API fornisce informazioni sulle azioni interne che derivano dalla richiesta di un utente di modificare lo stato di un'applicazione. | 
| CELL | Cella Diego | Il componente CELL fornisce informazioni sull'avvio, l'interruzione o l'arresto anomalo di un'applicazione.|
| SSH | SSH | Il componente SSH fornisce informazioni ogni volta che un utente accede a un'applicazione utilizzando il comando **cf ssh**. |
{: caption="Tabella 1. Origini log per le applicazioni CF distribuite in un'architettura CF basata su Diego" caption-side="top"}

La seguente figura illustra i diversi componenti (origini log) in un'architettura Cloud Foundry basata su Diego: 

![Origini log in un'architettura DEA.](images/cf_apps_diego_F1.png "Componenti (origini log) in un'architettura Cloud Foundry basata su Diego.")
	
## Origini log per le applicazioni CF distribuite a DEA
{: #logging_bluemix_cf_apps_log_sources}

Per le applicazioni CF (Cloud Foundry) distribuite in un'architettura DEA (Droplet Execution Agent), sono disponibili le seguenti origini log:
    
| Origine log | Nome componente | Descrizione | 
|------------|----------------|-------------|
| LGR | Loggregator | Il componente LGR fornisce informazioni relative al Loggregator Cloud Foundry, che inoltra i log dall'interno di Cloud Foundry. |
| RTR | Router | Il componente RTR fornisce informazioni sulle richieste HTTP a un'applicazione. | 
| STG | In fase di preparazione | Il componente STG fornisce informazioni su come viene preparata o ripreparata un'applicazione. | 
| APP | Applicazione | Il componente APP fornisce i log dall'applicazione. Qui è dove vengono mostrati i stderr e stdout nel tuo codice. | 
| API | API Cloud Foundry | Il componente API fornisce informazioni sulle azioni interne che derivano dalla richiesta di un utente di modificare lo stato di un'applicazione. | 
| DEA | Droplet Execution Agent | Il componente DEA fornisce informazioni sull'avvio, l'interruzione o l'arresto anomalo di un'applicazione. <br> Questo componente è disponibile solo se la tua applicazione viene distribuita nell'architettura Cloud Foundry basata su DEA. | 
{: caption="Tabella 2. Origini log per le applicazioni CF distribuite in un'architettura CF basata su DEA" caption-side="top"}

La seguente figura illustra i diversi componenti (origini log) in un'architettura Cloud Foundry basata su DEA: 

![Origini log in un'architettura DEA.](images/cf_apps_dea_F1.png "Componenti (origini log) in un'architettura Cloud Foundry basata su DEA (Droplet Execution Agent).")


