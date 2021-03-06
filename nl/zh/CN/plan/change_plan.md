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


# 更改套餐
{: #change_plan}

可以在 {{site.data.keyword.Bluemix_notm}} 的服务“仪表板”中或通过运行 `cf update-service` 命令来更改 {{site.data.keyword.loganalysisshort}} 服务套餐。您可以随时升级或降级套餐。
{:shortdesc}

## 通过 UI 更改服务套餐
{: #change_plan_ui}

要在 {{site.data.keyword.Bluemix_notm}} 的服务“仪表板”中更改服务套餐，请完成以下步骤：

1. 登录到 {{site.data.keyword.Bluemix_notm}}，然后在 {{site.data.keyword.Bluemix_notm}} 仪表板中单击 {{site.data.keyword.loganalysisshort}} 服务。 
    
2. 在 {{site.data.keyword.Bluemix_notm}} UI 中选择**套餐**选项卡。

    这将显示有关当前套餐的信息。
	
3. 选择新套餐以升级或降级现有套餐。 

4. 单击**保存**。



## 通过 CLI 更改服务套餐
{: #change_plan_cli}

要在 Bluemix 中通过 CLI 更改服务套餐，请完成以下步骤：

1. 登录到 {{site.data.keyword.Bluemix_notm}} 区域、组织和空间。 

    例如，要登录到美国南部区域，请运行以下命令：
	
	```
    cf login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
	
2. 运行 `cf services` 命令以检查当前套餐，并从空间中可用的服务的列表中获取 {{site.data.keyword.loganalysisshort}} 服务名称。 

    **name** 字段的值是必须用于更改套餐的名称。 

    例如：
	
	```
	$ cf services
    Getting services in org MyOrg / space dev as xxx@yyy.com...
    OK
    
    name              service          plan      bound apps   last operation
    Log Analysis-a4   ibmLogAnalysis   premium                create succeeded
    ```
	{: screen}
    
3. 升级或降级套餐。运行 `cf update-service` 命令。
    
	```
	cf update-service service_name [-p new_plan]
	```
	{: codeblock}
	
	其中 
	
	* *service_name* 是服务的名称。可以运行 `cf services` 命令来获取此值。
	* *new_plan* 是套餐的名称。
	
	下表列出了不同的套餐及其支持的值：
	
	<table>
	  <caption>表 1. 套餐列表。</caption>
	  <tr>
	    <th>套餐</th>
	    <th>名称</th>
	  </tr>
	  <tr>
	    <td>Lite</td>
	    <td>lite</td>
	  </tr>
	  <tr>
	    <td>日志收集</td>
	    <td>premium</td>
	  </tr>
	  <tr>
	    <td>日志收集，每天搜索 2 GB</td>
	    <td>premiumsearch2</td>
	  </tr>
	  <tr>
	    <td>日志收集，每天搜索 5 GB</td>
	    <td>premiumsearch5</td>
	  </tr>
	  <tr>
	    <td>日志收集，每天搜索 10 GB</td>
	    <td>premiumsearch10</td>
	  </tr>
	</table>
	
	例如，要将套餐降级到 *Lite* 套餐，请运行以下命令：
	
	```
	cf update-service "Log Analysis-a4" -p lite
    Updating service instance Log Analysis-a4 as xxx@yyy.com...
    OK
	```
	{: screen}

4. 验证是否已更改为新套餐。运行 `cf services` 命令。

    ```
	cf services
    Getting services in org MyOrg / space dev as xxx@yyy.com...
    OK

    name              service          plan   bound apps   last operation
    Log Analysis-a4   ibmLogAnalysis   lite                update succeeded
	```
	{: screen}






