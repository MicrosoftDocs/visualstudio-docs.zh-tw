---
title: 工作流程設計工具-Send 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Send.UI
ms.assetid: b514f2e4-767c-4b94-ac61-dd3a54d4b96d
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 86eab31b2d268475f4ae6c9fe91c9ee5b6a4e4bc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649979"
---
# <a name="send-activity-designer"></a>Send 活動設計工具

[ **Send** ] 活動設計工具會用來建立和設定 <xref:System.ServiceModel.Activities.Send> 活動。

## <a name="the-send-activity"></a>Send 活動

 <xref:System.ServiceModel.Activities.Send> 活動會用來傳送訊息至服務。 <xref:System.ServiceModel.Activities.ReceiveReply> 活動可以繫結程序至 <xref:System.ServiceModel.Activities.Send> 活動，而後者會接收用戶端上做為要求/回應訊息交換模式的一部分之訊息。

### <a name="using-the-send-activity-designer"></a>使用 Send 活動設計工具

在 [工具箱] 的 [**訊息**] 分類中，存取 [ **Send** ] 活動設計**工具**。 [ **Send** ] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到工作流程設計工具介面上通常用來放置活動的任一處。 這會建立一個 <xref:System.ServiceModel.Activities.Send> 活動，具有 Send 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 @No__t_0 可以在 [ **Send** ] 活動設計工具的標頭中編輯，或是在屬性方格的 [ **DisplayName** ] 方塊中編輯。

若要建立 <xref:System.ServiceModel.Activities.ReceiveReply> 活動，並將它系結至選取的 <xref:System.ServiceModel.Activities.Send> 活動，請以滑鼠右鍵按一下 [ **Send** ] 活動設計工具，按一下內容功能表中的 [**建立 ReceiveReply** ] 專案， **ReceiveReplyForSend**設計工具會出現**在傳送**設計工具。 <xref:System.ServiceModel.Activities.ReceiveReply> 活動會接收用戶端上做為要求/回應訊息交換模式的一部分之訊息。 您可以使用**ReceiveReplyForSend**設計工具來設定它。

或者，工具箱 的 **訊息** 分類中的  **sendandreceivereply**  範本設計**工具**可以用來建立一對預先設定的 <xref:System.ServiceModel.Activities.Send> 和 <xref:System.ServiceModel.Activities.ReceiveReply> 活動。 如需有關使用**sendandreceivereply**和**ReceiveReplyForSend**範本的詳細資訊，請參閱[sendandreceivereply](../workflow-designer/sendandreceivereply-template-designer.md)主題。

### <a name="the-send-activity-properties"></a>Send 活動屬性

下表顯示 <xref:System.ServiceModel.Activities.Send> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中或在工作流程設計工具介面上編輯。

| 屬性名稱 | 必要項 | 使用量 |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | <xref:System.ServiceModel.Activities.Send> 活動的易記名稱。 預設為 Send。 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。 |
| <xref:System.ServiceModel.Activities.Send.OperationName%2A> | True | 這個 <xref:System.ServiceModel.Activities.Send> 活動呼叫之服務作業的名稱。 如果未明確設定**action**屬性，則會使用這個屬性來建立**action**屬性的預設值。 |
| <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> | True | 要呼叫之服務所實作的服務合約名稱。 |
| <xref:System.ServiceModel.Activities.Send.Content%2A> | False | 指定要接收的訊息或參數內容。 這可以是 <xref:System.ServiceModel.Activities.ReceiveMessageContent> 活動或 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 活動。 編輯此屬性，方法是選取屬性方格中 **[內容**] 欄位旁邊的省略號按鈕，或按一下 [ **Receive** ] 活動設計工具介面上 [**內容**] 標籤旁的 [**定義**] 按鈕。 兩者都會顯示 [**內容定義**] 對話方塊。 如需如何使用此方塊的詳細資訊，請參閱[內容定義對話方塊](../workflow-designer/content-definition-dialog-box.md)主題。 |
| <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> | False | 指定用來路由訊息到適當工作流程執行個體的 <xref:System.ServiceModel.Activities.CorrelationHandle>。<br /><br /> 按一下 [屬性] 方格中 [<xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A>] 屬性旁的省略號按鈕，以開啟 [**運算式編輯器**] 對話方塊。 如需有關使用此對話方塊的詳細資訊，請參閱[如何：使用運算式編輯器](../workflow-designer/how-to-use-the-expression-editor.md)主題。 |
| <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> | False | 指定 <xref:System.ServiceModel.Activities.CorrelationInitializer> 物件的集合，這些物件會初始化多個 <xref:System.ServiceModel.Activities.CorrelationHandle> 物件，用來設定工作流程內的這個 <xref:System.ServiceModel.Activities.Send> 活動。 按一下 [屬性] 方格中 [<xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A>] 屬性旁的省略號按鈕，以開啟 [**加入相互關聯初始化運算式**] 對話方塊。 如需使用此方塊的詳細資訊，請參閱[新增 CorrelationInitializers 對話方塊](../workflow-designer/add-correlationinitializers-dialog-box.md)主題。 |
| <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> | False | 這個 <xref:System.ServiceModel.Activities.Send> 活動要呼叫之服務作業之已知型別的集合。 這個屬性應該搭配 <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> 屬性 (設定為 <xref:System.Runtime.Serialization.DataContractSerializer>) 使用。 如果使用 <xref:System.Xml.Serialization.XmlSerializer>，則會忽略此項。<br /><br /> 選取屬性方格中 [ **KnownTypes** ] 欄位旁邊的省略號按鈕，以顯示 [**類型集合編輯器**] 對話方塊，您可以在其中加入相關的類型。<br /><br /> 選取屬性方格中 [ **KnownTypes** ] 欄位旁邊的省略號按鈕，以顯示 [**類型集合編輯器**] 對話方塊，您可以在其中加入相關的類型。 如需使用此方塊的詳細資訊，請參閱[型別集合編輯器對話方塊](../workflow-designer/type-collection-editor-dialog-box.md)主題。 |
| <xref:System.ServiceModel.Activities.Send.ProtectionLevel%2A> | True | 指定訊息的 <xref:System.Net.Security.ProtectionLevel>。<br /><br /> 1. <xref:System.Net.Security.ProtectionLevel> 表示僅驗證。<br />2. <xref:System.Net.Security.ProtectionLevel> 表示簽署資料，以協助確保傳輸資料的完整性。<br />3. <xref:System.Net.Security.ProtectionLevel> 表示加密和簽署資料，以協助確保傳輸資料的機密性和完整性。 |
| <xref:System.ServiceModel.Activities.Send.SerializerOption%2A> | True | <xref:System.ServiceModel.Activities.Send> 活動要呼叫之服務作業所要使用的序列化程式。 預設值是 <xref:System.Runtime.Serialization.DataContractSerializer>，這會使用提供的資料合約，將型別的執行個體序列化及還原序列化，成為 XML 資料流或文件。 |
| <xref:System.ServiceModel.Activities.Send.Action%2A> | False | 指定訊息的動作標頭。 如果未明確設定，其值會預設為： https://tempuri.org/{service 合約命名空間}/合約名稱}/{作業名稱}。 如果在 <xref:System.ServiceModel.Activities.Send> 活動上指定，則接收訊息的 <xref:System.ServiceModel.Activities.Receive> 活動必須與要正確傳遞的訊息具有相同的值。 |
| <xref:System.ServiceModel.Activities.Send.TokenImpersonationLevel%2A> | | 訊息的接收者允許的 <xref:System.Security.Principal.TokenImpersonationLevel>。 它會定義安全性模擬等級，以控制伺服器進程可代表用戶端進程採取的程度。<xref:System.Security.Principal.TokenImpersonationLevel> 表示未指派模擬層級。 <xref:System.Security.Principal.TokenImpersonationLevel> 表示伺服器處理序無法取得用戶端的識別資訊，也無法模擬用戶端。 <xref:System.Security.Principal.TokenImpersonationLevel> 表示伺服器處理序可以取得關於用戶端的資訊，例如安全識別項和權限，但無法模擬用戶端。 對於匯出其自己的物件之伺服器 (例如匯出資料表和檢視表的資料庫產品) 而言，這將會很有用。 藉由使用所擷取的用戶端安全性資訊，伺服器便可做出存取驗證決策，而不用具備使用其他服務的能力，這些服務使用用戶端的安全性內容。 <xref:System.Security.Principal.TokenImpersonationLevel> 表示伺服器處理序可在其本機系統上模擬用戶端的安全性內容。 伺服器無法在遠端系統上模擬用戶端。 <xref:System.Security.Principal.TokenImpersonationLevel> 表示伺服器處理序可在遠端系統上模擬用戶端的安全性內容。 |
| <xref:System.ServiceModel.Activities.Send.Endpoint%2A> | | <xref:System.ServiceModel.Endpoint> 活動傳送訊息的目標 <xref:System.ServiceModel.Activities.Send>。 如果設定此屬性，<xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> 屬性應該是**null**。 |
| <xref:System.ServiceModel.Activities.Send.EndpointAddress%2A> | | 訊息傳送至的 <xref:System.ServiceModel.EndpointAddress>。 |
| <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> | | 端點組態的名稱。 這個屬性會在您設定組態檔中的端點時設定。 這個屬性應該設定為設定檔中的 **\<endpoint >** 元素所指定的名稱。 如果已設定這個屬性，<xref:System.ServiceModel.Activities.Send.Endpoint%2A> 屬性應該是**null**。 |

## <a name="see-also"></a>請參閱

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)