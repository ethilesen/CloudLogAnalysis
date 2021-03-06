---

copyright:
  years: 2017
lastupdated: "2017-07-14"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Protokollierung für virtuelle Maschinen
{: #logging_vm_ov}

Die Protokollfunktionen werden für virtuelle Maschinen (VMs) nicht automatisch aktiviert. Sie können Ihre VM jedoch so konfigurieren, dass sie Protokolle an 'Log Collection' sendet. Zum Erfassen und Senden von Protokolldaten von einer VM an den {{site.data.keyword.loganalysisshort}}-Service müssen Sie einen Multi-Tenant Logstash Forwarder (mt-logstash-forwarder) konfigurieren. Anschließend können Sie Protokolle in Kibana anzeigen, filtern und analysieren.
{:shortdesc}


## Einpflegen von Protokollen (Log Ingestion)
{: #log_ingestion}

Der {{site.data.keyword.loganalysisshort}}-Service bietet verschiedene Pläne. Jeder Plan definiert, ob Sie Protokolle an 'Log Collection' senden können. Alle Pläne - mit Ausnahme des *Lite*-Plans - beinhalten die Möglichkeit, Protokolle an 'Log Collection' zu senden. Weitere Informationen zu den Plänen finden Sie unter [Servicepläne](/docs/services/CloudLogAnalysis/log_analysis_ov.html#plans).

Sie können Protokolle über den Multi-Tenant Logstash Forwarder (mt-logstash-forwarder) an {site.data.keyword.loganalysisshort}} senden. Weitere Informationen finden Sie unter [Protokolldaten mit Multi-Tenant Logstash Forwarder (mt-logstash-forwarder) senden](/docs/services/CloudLogAnalysis/how-to/send-data/send_data_mt.html#send_data_mt). 


## Erfassen von Protokollen (Log Collection)
{: #log_collection}

Standardmäßig speichert {{site.data.keyword.Bluemix_notm}} Protokolldaten für bis zu drei Tage:   

* Maximal werden 500 MB pro Datenbereich und Tag gespeichert. Alle Protokolle oberhalb der Kapazitätsgrenze von 500 MB werden nicht berücksichtigt. Die Kapazitätsgrenze wird täglich um 12:30 AM (UTC) zurückgesetzt.
* Bis zu 1,5 GB Daten können für einen Zeitraum von maximal 3 Tagen durchsucht werden. Das Rollover der Protokolldaten (First In, First Out) erfolgt bei 1,5 GB an Daten oder nach drei Tagen.

Der {{site.data.keyword.loganalysisshort}}-Service bietet zusätzliche Pläne, mit denen Sie Protokolle in 'Log Collection' so lange wie erforderlich speichern können. Weitere Informationen zu den Preisen der einzelnen Pläne finden Sie unter [Servicepläne](/docs/services/CloudLogAnalysis/log_analysis_ov.html#plans).

Sie können eine Protokollaufbewahrungsrichtlinie konfigurieren, die die Anzahl Tage definiert, für die Protokolle in 'Log Collection' aufbewahrt werden. Weitere Informationen finden Sie unter [Protokollaufbewahrungsrichtlinie](/docs/services/CloudLogAnalysis/log_analysis_ov.html#policies).


## Durchsuchen von Protokollen (Log Search)
{: #log_search}

Standardmäßig können Sie Kibana verwenden, um 500 MB Protokolle pro Tag in {{site.data.keyword.Bluemix_notm}} zu durchsuchen. 

Der {{site.data.keyword.loganalysisshort}}-Service bietet mehrere Pläne. Für jeden Plan gibt es unterschiedliche Protokollsuchfunktionen. Z. B. können Sie beim *Log Collection*-Plan bis zu 1 GB an Daten pro Tag durchsuchen. Weitere Informationen zu den Plänen finden Sie unter [Servicepläne](/docs/services/CloudLogAnalysis/log_analysis_ov.html#plans).


## Analysieren von Protokollen (Log Analysis)
{: #log_analysis}

Zum Analysieren von Protokolldaten verwenden Sie Kibana, um erweiterte Analysetasks auszuführen. Sie können Kibana, eine quelloffene Analyse- und Visualisierungsplattform, dazu verwenden, Ihre Daten in einer Reihe von Darstellungsarten, wie zum Beispiel Diagrammen und Tabellen, zu überwachen, zu durchsuchen, zu analysieren und zu visualisieren. Weitere Informationen finden Sie unter [Protokolle in Kibana analysieren](/docs/services/CloudLogAnalysis/kibana/analyzing_logs_Kibana.html#analyzing_logs_Kibana).
