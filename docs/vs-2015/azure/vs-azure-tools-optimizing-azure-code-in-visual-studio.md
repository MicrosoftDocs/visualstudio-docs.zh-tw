---
title: 最佳化 Visual Studio 中的 Azure 程式碼 |Microsoft Docs
description: 了解關於如何 Azure 程式碼最佳化工具在 Visual Studio 中的會說明讓您的程式碼，更穩定且更容易執行。
author: ghogen
manager: douge
ms.assetid: ed48ee06-e2d2-4322-af22-07200fb16987
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: ghogen
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: d1d0f5a69015a6c6596e1a2b7ee85b12f4116d6b
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001461"
---
# <a name="optimizing-your-azure-code"></a>最佳化您的 Azure 程式碼
當您在撰寫使用 Microsoft Azure 的應用程式時，有您應該遵循以協助避免應用程式的延展性、 行為和在雲端環境中的效能問題的一些程式碼撰寫做法。 Microsoft 提供 Azure Code Analysis 工具會辨識並找出許多這些常遇到的問題並可協助您解決這些問題。 您可以下載 Visual Studio 中透過 NuGet 中的工具。

## <a name="azure-code-analysis-rules"></a>Azure Code Analysis 規則
Azure Code Analysis 工具會使用下列規則，自動加上旗標的 Azure 程式碼時發現的效能影響的已知的問題。 偵測到問題會顯示為警告或編譯器錯誤。 通常透過燈泡圖示提供程式碼修正或解決警告或錯誤的建議。

## <a name="avoid-using-default-in-process-session-state-mode"></a>請避免使用預設 （同處理序） 工作階段狀態模式
### <a name="id"></a>識別碼
AP0000

### <a name="description"></a>描述
如果您使用預設 （同處理序） 工作階段狀態模式為雲端應用程式時，您可能會遺失工作階段狀態。

請分享您的想法和意見反應，在[Azure Code Analysis 意見反應](http://go.microsoft.com/fwlink/?LinkId=403771)。

### <a name="reason"></a>原因
根據預設，web.config 檔案中指定的工作階段狀態模式會是同處理序。 此外，如果沒有指定組態檔中的項目，工作階段狀態模式會預設為同處理序。 同處理序模式會將工作階段狀態儲存在 web 伺服器上的記憶體。 當重新啟動執行個體或新的執行個體用於負載平衡或容錯移轉支援時，不會儲存在 web 伺服器上的記憶體中儲存的工作階段狀態。 這種情況下，防止應用程式在雲端上進行調整。

ASP.NET 工作階段狀態支援的工作階段狀態資料的數個不同的儲存體選項： InProc、 StateServer、 SQLServer、 自訂和關閉。 建議您自訂模式，將資料裝載上使用外部工作階段狀態存放區，例如[Redis 的 Azure 工作階段狀態提供者](http://go.microsoft.com/fwlink/?LinkId=401521)。

### <a name="solution"></a>方案
一個建議的解決方案是在受管理快取服務儲存工作階段狀態。 了解如何使用[Redis 的 Azure 工作階段狀態提供者](http://go.microsoft.com/fwlink/?LinkId=401521)來儲存工作階段狀態。 您也可以將工作階段狀態儲存在其他地方，以確保您的應用程式在雲端上進行調整。 若要深入了解替代方案，請閱讀[工作階段狀態模式](https://msdn.microsoft.com/library/ms178586)。

## <a name="run-method-should-not-be-async"></a>執行的方法必須同步
### <a name="id"></a>識別碼
AP1000

### <a name="description"></a>描述
建立非同步方法 (例如[await](https://msdn.microsoft.com/library/hh156528.aspx)) 之外[run （)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)方法，然後呼叫非同步方法，從[run （)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)。 宣告[ [run （)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)為非同步方法會導致背景工作角色輸入重新啟動迴圈。

請分享您的想法和意見反應，在[Azure Code Analysis 意見反應](http://go.microsoft.com/fwlink/?LinkId=403771)。

### <a name="reason"></a>原因
呼叫非同步方法內[run （)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)方法會導致雲端服務執行階段回收背景工作角色。 當背景工作角色啟動時，所有的程式執行發生內部[run （)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)方法。 結束[run （)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)方法會導致背景工作角色重新啟動。 當背景工作角色執行階段叫用非同步方法時，它會在非同步方法之後分派所有作業，然後傳回。 這會導致背景工作角色離開[ [ [ [run （)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)方法並重新啟動。 在執行的下一個反覆項目，背景工作角色會再次叫用非同步方法，並重新啟動，導致背景工作角色又再次回收。

### <a name="solution"></a>方案
將外部的所有非同步作業都放[run （)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)方法。 然後，呼叫從非同步方法內[ [run （)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)方法，例如 RunAsync （).wait。 Azure Code Analysis 工具可協助您修正此問題。

下列程式碼片段示範程式碼修正此問題：

```
public override void Run()
{
    RunAsync().Wait();
}

public async Task RunAsync()
{
    //Asynchronous operations code logic
    // This is a sample worker implementation. Replace with your logic.

    Trace.TraceInformation("WorkerRole1 entry point called");

    HttpClient client = new HttpClient();

    Task<string> urlString = client.GetStringAsync("http://msdn.microsoft.com");

    while (true)
    {
        Thread.Sleep(10000);
        Trace.TraceInformation("Working");

        string stream = await urlString;
    }

}
```

## <a name="use-service-bus-shared-access-signature-authentication"></a>使用服務匯流排共用存取簽章驗證
### <a name="id"></a>識別碼
AP2000

### <a name="description"></a>描述
使用共用存取簽章 (SAS) 進行驗證。 存取控制服務 (ACS) 已被取代的服務匯流排驗證。

請分享您的想法和意見反應，在[Azure Code Analysis 意見反應](http://go.microsoft.com/fwlink/?LinkId=403771)。

### <a name="reason"></a>原因
為加強安全性，Azure Active Directory 以 SAS 驗證取代 ACS 驗證。 請參閱[Azure Active Directory 是 ACS 的未來](https://cloudblogs.microsoft.com/enterprisemobility/2013/06/22/azure-active-directory-is-the-future-of-acs/)轉換計畫的資訊。

### <a name="solution"></a>方案
在您的應用程式中使用 SAS 驗證。 下列範例示範如何使用現有的 SAS 權杖來存取服務匯流排命名空間或實體。

```
MessagingFactory listenMF = MessagingFactory.Create(endpoints, new StaticSASTokenProvider(subscriptionToken));
SubscriptionClient sc = listenMF.CreateSubscriptionClient(topicPath, subscriptionName);
BrokeredMessage receivedMessage = sc.Receive();
```

請參閱下列主題中的詳細資訊。

* 如需概觀，請參閱[使用服務匯流排共用存取簽章驗證](https://msdn.microsoft.com/library/dn170477.aspx)
* [如何使用服務匯流排的共用存取簽章驗證](https://msdn.microsoft.com/library/dn205161.aspx)
* 如需範例專案中，請參閱[使用共用存取簽章 (SAS) 驗證，使用服務匯流排訂用帳戶](http://code.msdn.microsoft.com/windowsazure/Using-Shared-Access-e605b37c)

## <a name="consider-using-onmessage-method-to-avoid-receive-loop"></a>請考慮使用 OnMessage 方法來避免 「 接收迴圈 」
### <a name="id"></a>識別碼
AP2002

### <a name="description"></a>描述
若要避免陷入 「 接收迴圈 」 呼叫**OnMessage**方法是更好的解決方案來接收訊息，比呼叫**接收**方法。 不過，如果您必須使用**接收**方法，而且您指定非預設伺服器等待時間，請確定伺服器等待時間超過一分鐘。

請分享您的想法和意見反應，在[Azure Code Analysis 意見反應](http://go.microsoft.com/fwlink/?LinkId=403771)。

### <a name="reason"></a>原因
當呼叫**OnMessage**，用戶端會啟動內部訊息幫浦，持續輪詢佇列或訂用帳戶。 此訊息幫浦包含會發出訊息接收呼叫的無限迴圈。 如果呼叫逾時，就會發出新的呼叫。 值所決定的逾時間隔[OperationTimeout](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.messagingfactorysettings.operationtimeout.aspx)屬性[MessagingFactory](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.messagingfactory.aspx)正在使用。

使用的優點**OnMessage**相較於**接收**是，使用者不必手動輪詢訊息、 處理例外狀況、 處理多個訊息，以平行方式，並完成訊息。

如果您呼叫**接收**而不使用其預設值，請務必*ServerWaitTime*值已超過一分鐘。 設定*ServerWaitTime*超過一分鐘來防止伺服器完全收到訊息之前逾時。

### <a name="solution"></a>方案
請參閱下列的程式碼範例，了解建議用法。 如需詳細資訊，請參閱 < [QueueClient.OnMessage 方法 (Microsoft.ServiceBus.Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.onmessage.aspx)並[QueueClient.Receive 方法 (Microsoft.ServiceBus.Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.receive.aspx)。

若要改善 Azure 傳訊基礎結構的效能，請參閱設計模式[非同步傳訊入門](https://msdn.microsoft.com/library/dn589781.aspx)。

以下是使用的範例**OnMessage**來接收訊息。

```
void ReceiveMessages()
{
    // Initialize message pump options.
    OnMessageOptions options = new OnMessageOptions();
    options.AutoComplete = true; // Indicates if the message-pump should call complete on messages after the callback has completed processing.
    options.MaxConcurrentCalls = 1; // Indicates the maximum number of concurrent calls to the callback the pump should initiate.
    options.ExceptionReceived += LogErrors; // Enables you to get notified of any errors encountered by the message pump.

    // Start receiving messages.
    QueueClient client = QueueClient.Create("myQueue");
    client.OnMessage((receivedMessage) => // Initiates the message pump and callback is invoked for each message that is recieved, calling close on the client will stop the pump.
    {
        // Process the message.
    }, options);
    Console.WriteLine("Press any key to exit.");
    Console.ReadKey();
```

以下是使用的範例**接收**與預設伺服器等待時間。

```
string connectionString =  
CloudConfigurationManager.GetSetting("Microsoft.ServiceBus.ConnectionString");

QueueClient Client =  
    QueueClient.CreateFromConnectionString(connectionString, "TestQueue");

while (true)  
{   
   BrokeredMessage message = Client.Receive();
   if (message != null)
   {
      try  
      {
         Console.WriteLine("Body: " + message.GetBody<string>());
         Console.WriteLine("MessageID: " + message.MessageId);
         Console.WriteLine("Test Property: " +  
            message.Properties["TestProperty"]);

         // Remove message from queue
         message.Complete();
      }

      catch (Exception)
      {
         // Indicate a problem, unlock message in queue
         message.Abandon();
      }
   }
```

以下是使用的範例**接收**與非預設伺服器等待時間。

```
while (true)  
{   
   BrokeredMessage message = Client.Receive(new TimeSpan(0,1,0));

   if (message != null)
   {
      try  
      {
         Console.WriteLine("Body: " + message.GetBody<string>());
         Console.WriteLine("MessageID: " + message.MessageId);
         Console.WriteLine("Test Property: " +  
            message.Properties["TestProperty"]);

         // Remove message from queue
         message.Complete();
      }

      catch (Exception)
      {
         // Indicate a problem, unlock message in queue
         message.Abandon();
      }
   }
}
```
## <a name="consider-using-asynchronous-service-bus-methods"></a>請考慮使用非同步服務匯流排方法
### <a name="id"></a>識別碼
AP2003

### <a name="description"></a>描述
您可以使用服務匯流排的非同步方法來改善代理傳訊的效能。

請分享您的想法和意見反應，在[Azure Code Analysis 意見反應](http://go.microsoft.com/fwlink/?LinkId=403771)。

### <a name="reason"></a>原因
使用非同步方法可讓應用程式並行效果，因為執行每個呼叫不會封鎖主要執行緒。 使用服務匯流排傳訊方法，執行作業時 （傳送、 接收、 刪除、 等等） 的時間。 這個時間包括在處理作業的服務匯流排服務，除了要求和回覆的延遲。 若要增加每次的作業數目，必須同時執行作業。 如需詳細資訊請參閱[效能改善使用服務匯流排代理傳訊的最佳作法](https://msdn.microsoft.com/library/azure/hh528527.aspx)。

### <a name="solution"></a>方案
請參閱[QueueClient 類別 (Microsoft.ServiceBus.Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.aspx)如需如何使用建議的非同步方法的詳細資訊。

若要改善 Azure 傳訊基礎結構的效能，請參閱設計模式[非同步傳訊入門](https://msdn.microsoft.com/library/dn589781.aspx)。

## <a name="consider-partitioning-service-bus-queues-and-topics"></a>請考慮分割服務匯流排佇列和主題
### <a name="id"></a>識別碼
AP2004

### <a name="description"></a>描述
資料分割服務匯流排佇列和主題的更佳的效能與服務匯流排傳訊。

請分享您的想法和意見反應，在[Azure Code Analysis 意見反應](http://go.microsoft.com/fwlink/?LinkId=403771)。

### <a name="reason"></a>原因
資料分割服務匯流排佇列和主題會增加效能輸送量和服務的可用性，因為資料分割的佇列或主題的整體輸送量不會再受到單一訊息代理程式或訊息存放區的效能。 此外，即使訊息存放區暫時中斷不會讓分割的佇列或主題無法使用。 如需詳細資訊，請參閱 <<c0> [ 分割訊息實體](https://msdn.microsoft.com/library/azure/dn520246.aspx)。

### <a name="solution"></a>方案
下列程式碼片段示範如何分割訊息實體。

```
// Create partitioned topic.
NamespaceManager ns = NamespaceManager.CreateFromConnectionString(myConnectionString);
TopicDescription td = new TopicDescription(TopicName);
td.EnablePartitioning = true;
ns.CreateTopic(td);
```

如需詳細資訊，請參閱[分割服務匯流排佇列和主題 |Microsoft Azure 部落格](https://azure.microsoft.com/blog/2013/10/29/partitioned-service-bus-queues-and-topics/)並查看[Microsoft Azure 服務匯流排分割的佇列](https://code.msdn.microsoft.com/windowsazure/Service-Bus-Partitioned-7dfd3f1f)範例。

## <a name="do-not-set-sharedaccessstarttime"></a>不要設定 SharedAccessStartTime
### <a name="id"></a>識別碼
AP3001

### <a name="description"></a>描述
您應該避免使用目前時間的 Sharedaccessstarttime，以立即啟動共用存取原則。 您只需要設定此屬性，如果您想要於稍後啟動的共用存取原則。

請分享您的想法和意見反應，在[Azure Code Analysis 意見反應](http://go.microsoft.com/fwlink/?LinkId=403771)。

### <a name="reason"></a>原因
時鐘同步處理會導致資料中心彼此間產生些微時差。 例如，您會以邏輯方式將設定儲存體 SAS 原則的開始時間為目前時間，使用 DateTime.Now 或類似方法將會使得 SAS 原則立即生效。 不過，資料中心之間的時間稍微差異可能會造成此問題，因為某些資料中心的時間可能稍微晚於開始時間，而有些則比較早。 如此一來，SAS 原則可以很快過期 （甚至是立即） 如果原則的存留期設定太短。

如需 Azure 儲存體上使用共用存取簽章的詳細指引，請參閱[簡介資料表 SAS （共用存取簽章）、 佇列 SAS 以及 Blob sas-Microsoft Azure 儲存體團隊部落格-更新網站首頁-MSDN 部落格](http://blogs.msdn.com/b/windowsazurestorage/archive/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas.aspx)。

### <a name="solution"></a>方案
請移除陳述式，以設定共用的存取原則的開始時間。 Azure Code Analysis 工具提供的修正此問題。 如需有關安全性管理的詳細資訊，請參閱設計模式[Valet 金鑰模式](https://msdn.microsoft.com/library/dn568102.aspx)。

下列程式碼片段示範此問題的程式碼修正。

```
// The shared access policy provides  
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
   SharedAccessExpiryTime = DateTime.UtcNow.AddHours(10),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

## <a name="shared-access-policy-expiry-time-must-be-more-than-five-minutes"></a>共用存取原則到期時間必須超過五分鐘
### <a name="id"></a>識別碼
AP3002

### <a name="description"></a>描述
可以是盡可能因為種狀況稱為 「 時鐘誤差。 」 的不同位置的資料中心之間的差異，五分鐘 為了防止 SAS 原則權杖過期計劃之前設定為 5 分鐘以上的到期時間。

請分享您的想法和意見反應，在[Azure Code Analysis 意見反應](http://go.microsoft.com/fwlink/?LinkId=403771)。

### <a name="reason"></a>原因
以時脈訊號，同步處理世界各地的不同位置的資料中心。 因為需要移動到不同位置的時脈訊號的時間，可能會有不同地理位置的資料中心之間的時間差異雖然應該同步處理的所有項目。 此一時間差可能會影響共用存取原則開始時間和到期間隔。 因此，為了確保共用存取原則會立即生效，請勿指定開始時間。 此外，請確定到期時間超過 5 分鐘，以防止提早逾時。

如需 Azure 儲存體上使用共用存取簽章的詳細資訊，請參閱[簡介資料表 SAS （共用存取簽章）、 佇列 SAS 以及 Blob sas-Microsoft Azure 儲存體團隊部落格-更新網站首頁-MSDN 部落格](http://blogs.msdn.com/b/windowsazurestorage/archive/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas.aspx)。

### <a name="solution"></a>方案
如需有關安全性管理的詳細資訊，請參閱設計模式[Valet 金鑰模式](https://msdn.microsoft.com/library/dn568102.aspx)。

以下是未指定共用存取原則開始時間的範例。

```
// The shared access policy provides  
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
   SharedAccessExpiryTime = DateTime.UtcNow.AddHours(10),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

以下是指定與原則到期期間超過五分鐘的共用存取原則開始時間的範例。

```
// The shared access policy provides  
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
  SharedAccessStartTime = new DateTime(2014,1,20),   
 SharedAccessExpiryTime = new DateTime(2014, 1, 21),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

如需詳細資訊，請參閱 <<c0> [ 建立及使用共用存取簽章](https://msdn.microsoft.com/library/azure/jj721951.aspx)。

## <a name="use-cloudconfigurationmanager"></a>使用 CloudConfigurationManager
### <a name="id"></a>識別碼
AP4000

### <a name="description"></a>描述
使用[ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx)專案的類別，例如 Azure 網站和 Azure 行動服務不會產生執行階段問題。 最佳做法，不過，它是個不錯的主意，若要使用雲端[ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx)以統一的管理所有 Azure 雲端應用程式的組態。

請分享您的想法和意見反應，在[Azure Code Analysis 意見反應](http://go.microsoft.com/fwlink/?LinkId=403771)。

### <a name="reason"></a>原因
CloudConfigurationManager 會讀取適合應用程式環境的組態檔。

[CloudConfigurationManager](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.cloudconfigurationmanager.aspx)

### <a name="solution"></a>方案
重構程式碼而改用[CloudConfigurationManager 類別](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.cloudconfigurationmanager.aspx)。 Azure Code Analysis 工具會提供程式碼修正此問題。

下列程式碼片段示範此問題的程式碼修正。 取代

`var settings = ConfigurationManager.AppSettings["mySettings"];`

取代為

`var settings = CloudConfigurationManager.GetSetting("mySettings");`

以下是如何在 App.config 或 Web.config 檔案中儲存的組態設定的範例。 您可以將設定加入組態檔的 appSettings 區段。 以下是上述的程式碼範例的 Web.config 檔案。

```
<appSettings>
    <add key="webpages:Version" value="3.0.0.0" />
    <add key="webpages:Enabled" value="false" />
    <add key="ClientValidationEnabled" value="true" />
    <add key="UnobtrusiveJavaScriptEnabled" value="true" />
    <add key="mySettings" value="[put_your_setting_here]"/>
  </appSettings>  
```

## <a name="avoid-using-hard-coded-connection-strings"></a>請避免使用硬式編碼的連接字串
### <a name="id"></a>識別碼
AP4001

### <a name="description"></a>描述
如果您使用硬式編碼的連接字串，而您需要加以更新，您必須對原始程式碼進行變更並重新編譯應用程式。 不過，如果您將連接字串儲存在組態檔時，您稍後可以變更它們只要更新組態檔。

請分享您的想法和意見反應，在[Azure Code Analysis 意見反應](http://go.microsoft.com/fwlink/?LinkId=403771)。

### <a name="reason"></a>原因
硬式編碼的連接字串是不良作法，因為當連接字串需要快速變更時，它會導致問題。 此外，如果專案必須簽入原始檔控制，硬式編碼的連接字串引發安全性漏洞，因為在原始程式碼中就能檢視字串。

### <a name="solution"></a>方案
將連接字串儲存在組態檔或 Azure 環境中。

* 對於獨立應用程式，使用 app.config 來儲存連接字串設定。
* 對於 IIS 裝載的 web 應用程式，使用 web.config 來儲存連接字串。
* ASP.NET vNext 應用程式，使用 configuration.json 來儲存連接字串。

如需使用 web.config 或 app.config 等組態檔的資訊，請參閱[ASP.NET Web 組態指導方針](https://msdn.microsoft.com/library/vstudio/ff400235\(v=vs.100\).aspx)。 如需 Azure 環境變數運作方式的詳細資訊，請參閱[Azure 網站： 應用程式字串與連接字串的運作](https://azure.microsoft.com/blog/2013/07/17/windows-azure-web-sites-how-application-strings-and-connection-strings-work/)。 將連接字串儲存在原始檔控制中的資訊，請參閱[避免將機密資訊，例如連接字串放在原始程式碼儲存機制中儲存的檔案](http://www.asp.net/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/source-control)。

## <a name="use-diagnostics-configuration-file"></a>使用診斷組態檔
### <a name="id"></a>識別碼
AP5000

### <a name="description"></a>描述
而不是使用 Microsoft.WindowsAzure.Diagnostics 程式設計 API，例如程式碼中設定診斷設定，您應該在 diagnostics.wadcfg 檔案中設定診斷設定。 （或者，如果您使用 Azure SDK 2.5 的 diagnostics.wadcfgx）。 如此一來，您可以變更診斷設定，而不必重新編譯您的程式碼。

請分享您的想法和意見反應，在[Azure Code Analysis 意見反應](http://go.microsoft.com/fwlink/?LinkId=403771)。

### <a name="reason"></a>原因
之前使用幾種不同的方法，則可以設定 Azure SDK 2.5 (使用 Azure 診斷 1.3）、 Azure 診斷 (WAD): 使用命令式程式碼、 宣告式組態或預設值將它新增至儲存體中的組態 blob組態設定。 不過，若要設定診斷的慣用的方法是使用 XML 組態檔 （diagnostics.wadcfg 或 diagnositcs.wadcfgx SDK 2.5 及更新版本） 應用程式專案中。 這種方法，diagnostics.wadcfg 檔案完全定義的組態和可更新，並在重新部署。 混用 diagnostics.wadcfg 組態檔和組態設定可以使用以程式設計方式[DiagnosticMonitor](https://msdn.microsoft.com/library/microsoft.windowsazure.diagnostics.diagnosticmonitor.aspx)或是[RoleInstanceDiagnosticManager](https://msdn.microsoft.com/library/microsoft.windowsazure.diagnostics.management.roleinstancediagnosticmanager.aspx)類別可以會造成混淆。 請參閱[初始化或變更 Azure 診斷組態](https://msdn.microsoft.com/library/azure/hh411537.aspx)如需詳細資訊。

從 WAD 1.3 （隨附於 Azure SDK 2.5） 開始，它不再可以使用程式碼來設定診斷。 如此一來，您可以只提供時套用，或更新診斷延伸模組的設定。

### <a name="solution"></a>方案
您可以使用診斷組態設計工具來診斷設定移至診斷組態檔 （則是 diagnositcs.wadcfg 或 diagnositcs.wadcfgx SDK 2.5 及更新版本）。 也建議您安裝[Azure SDK 2.5](http://go.microsoft.com/fwlink/?LinkId=513188)並使用最新的診斷功能。

1. 在您想要設定之角色的捷徑功能表，選擇 [內容]，然後選擇 [設定] 索引標籤。
2. 在 **診斷**區段中，請確定**啟用診斷**選取核取方塊。
3. 選擇**設定** 按鈕。

   ![存取啟用診斷選項](./media/vs-azure-tools-optimizing-azure-code-in-visual-studio/IC796660.png)

   請參閱[為 Azure 雲端服務和虛擬機器設定診斷](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md)如需詳細資訊。

## <a name="avoid-declaring-dbcontext-objects-as-static"></a>避免將為靜態 DbContext 物件宣告
### <a name="id"></a>識別碼
AP6000

### <a name="description"></a>描述
若要節省記憶體，請避免宣告為靜態 DBContext 物件。

請分享您的想法和意見反應，在[Azure Code Analysis 意見反應](http://go.microsoft.com/fwlink/?LinkId=403771)。

### <a name="reason"></a>原因
DBContext 物件會保存每個呼叫的查詢結果。 應用程式網域卸載之前，則不會處置靜態 DBContext 物件。 因此，靜態 DBContext 物件可能會耗用大量的記憶體。

### <a name="solution"></a>方案
將 DBContext 宣告為區域變數或非靜態執行個體欄位，對於工作而言，使用它，然後讓它使用後加以處置。

下列範例 MVC 控制器類別示範如何使用 DBContext 物件。

```
public class BlogsController : Controller
    {
        //BloggingContext is a subclass to DbContext        
        private BloggingContext db = new BloggingContext();
        // GET: Blogs
        public ActionResult Index()
        {
            //business logics…
            return View();
        }
        protected override void Dispose(bool disposing)
        {
            if (disposing)
            {
                db.Dispose();
            }
            base.Dispose(disposing);
        }
    }
```

## <a name="next-steps"></a>後續步驟
若要進一步了解最佳化和疑難排解 Azure 應用程式，請參閱[疑難排解 Azure App Service 使用 Visual Studio 中的 web 應用程式](/azure/app-service/web-sites-dotnet-troubleshoot-visual-studio)。
