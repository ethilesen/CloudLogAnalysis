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


# 供应 Log Analysis 服务
{: #provision}

可以通过 {{site.data.keyword.Bluemix}} UI 或命令行供应 {{site.data.keyword.loganalysisshort}} 服务。
{:shortdesc}


## 通过 UI 供应
{: #ui}

要在 {{site.data.keyword.Bluemix_notm}} 中供应 {{site.data.keyword.loganalysisshort}} 服务的实例，请完成以下步骤：

1. 登录到 {{site.data.keyword.Bluemix_notm}} 帐户。

    {{site.data.keyword.Bluemix_notm}}“仪表板”位于：[http://bluemix.net![外部链接图标](../../../icons/launch-glyph.svg "外部链接图标")](http://bluemix.net "外部链接图标"){:new_window}。
    
	使用用户标识和密码登录后，{{site.data.keyword.Bluemix_notm}} UI 将打开。

2. 单击**目录**。这将打开 {{site.data.keyword.Bluemix_notm}} 上可用的服务的列表。

3. 选择 **DevOps** 类别以过滤显示的服务列表。

4. 单击 **Log Analysis** 磁贴。

5. 选择服务套餐。缺省情况下，已设置 **Lite** 套餐。


    有关服务套餐的更多信息，请参阅[服务套餐](/docs/services/CloudLogAnalysis/log_analysis_ov.html#plans)。
	
6. 单击**创建**以在您登录到的 {{site.data.keyword.Bluemix_notm}} 空间中供应 {{site.data.keyword.loganalysisshort}} 服务。
  
 

## 通过 CLI 供应
{: #cli}

要通过命令行在 {{site.data.keyword.Bluemix_notm}} 中供应 {{site.data.keyword.loganalysisshort}} 服务的实例，请完成以下步骤：

1. 安装 Cloud Foundry (CF) CLI。如果 CF CLI 已安装，请继续执行下一步。

   有关更多信息，请参阅[安装 CF CLI ![外部链接图标](../../../icons/launch-glyph.svg "外部链接图标")](http://docs.cloudfoundry.org/cf-cli/install-go-cli.html "外部链接图标"){: new_window}。 
    
2. 登录到 {{site.data.keyword.Bluemix_notm}} 区域、组织和空间。 

    例如，要登录到美国南部区域，请运行以下命令：

    ```
    cf login -a https://api.ng.bluemix.net
    ```
    {: codeblock}

    遵循指示信息进行操作。输入您的 {{site.data.keyword.Bluemix_notm}} 凭证，然后选择组织和空间。
	
3. 运行 `cf create-service` 命令以供应实例。

    ```
	cf create-service service_name service_plan service_instance_name
	```
	{: codeblock}
    
    其中
	
	* service_name 是服务的名称，即 **ibmLogAnalysis**。
	* service_plan 是服务套餐名称。有关套餐的列表，请参阅[服务套餐](/docs/services/CloudLogAnalysis/log_analysis_ov.html#plans)。
	* service_instance_name 是要用于所创建的新服务实例的名称。
	有关 cf 命令的更多信息，请参阅 [cf create-service](/docs/cli/reference/cfcommands/index.html#cf_create-service)。

	例如，要使用免费套餐创建 {{site.data.keyword.loganalysisshort}} 服务的实例，请运行以下命令：
	
	```
	cf create-service ibmLogAnalysis lite my_logging_svc
	```
	{: codeblock}
	
4. 验证服务是否已成功创建。运行以下命令：

    ```	
	cf services
	```
	{: codeblock}
    
    运行此命令的输出如下所示：
	
	```
    Getting services in org MyOrg / space MySpace as xxx@yyy.com...
    OK
    
    name                           service                  plan                   bound apps              last operation
    my_logging_svc                ibmLogAnalysis               lite                                        create succeeded
	```
	    {: screen}
	
    



