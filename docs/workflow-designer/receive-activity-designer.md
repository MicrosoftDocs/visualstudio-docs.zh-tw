---
title: "Receive 活動設計工具 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.ServiceModel.Activities.Receive.UI
ms.assetid: f58d3c70-944d-4bb4-90a7-e68c103caddc
caps.latest.revision: "8"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 68d198675f5b0b91320e9c21d497caf225798cc7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="receive-activity-designer"></a>Receive 活動設計工具
**接收**活動設計工具用來建立及設定<xref:System.ServiceModel.Activities.Receive>活動。 <xref:System.ServiceModel.Activities.Receive> 活動是接收訊息的活動，該訊息可能是內建的型別 (例如 <xref:System.ServiceModel.Channels.Message>、<xref:System.IO.Stream> 或 <xref:System.Xml.Linq.XElement>)，或是應用程式定義的資料合約、訊息合約或可序列化的 XML 類別。  
  
## <a name="the-receive-activity"></a>Receive 活動  
 <xref:System.ServiceModel.Activities.Receive> 活動可以接收單一項目或多個項目，視所使用的接收內容型別而定。 <xref:System.ServiceModel.Activities.SendReply> 活動可以繫結至 <xref:System.ServiceModel.Activities.Receive> 活動，而後者會接收服務上做為要求/回應訊息交換模式的一部分之訊息。  
  
### <a name="using-the-receive-activity-designer"></a>使用 Receive 活動設計工具  
 **接收**活動設計工具位於**傳訊**分類**工具箱**，即可存取的哪一個**工具箱**索引標籤上[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)](或者，選取**工具列**從**檢視**功能表或 CTRL + ALT + X。)  
  
 **接收**活動設計工具可以從拖曳**工具箱**，置放到上[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]介面任一處活動通常放置。 這會建立一個 <xref:System.ServiceModel.Activities.Receive> 活動，具有 Receive 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 <xref:System.Activities.Activity.DisplayName%2A>可編輯的標頭中**接收**活動設計工具或在**DisplayName**屬性方格的方塊。  
  
 若要建立<xref:System.ServiceModel.Activities.SendReply>活動並將它繫結至所選<xref:System.ServiceModel.Activities.Receive>活動，以滑鼠右鍵按一下**接收**活動設計工具，然後按一下**建立 SendReply**內容功能表中的項目，**SendReplyToReceive**設計工具隨即出現下面**接收**設計工具。 <xref:System.ServiceModel.Activities.SendReply> 活動會傳送回覆訊息，而這屬於服務上要求/回應訊息交換模式的一部分。 可以使用設定**SendReplyToReceive**設計工具。  
  
 或者， **ReceiveAndSendReply**範本設計工具中的**傳訊**分類**工具箱**可用來建立一對預先設定<xref:System.ServiceModel.Activities.Receive>和<xref:System.ServiceModel.Activities.SendReply>活動。 [!INCLUDE[crabout](../test/includes/crabout_md.md)]使用**ReceiveAndSendReply**和**SendReplyToReceive**範本，請參閱[ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)主題。  
  
### <a name="the-receive-activity-properties"></a>Receive 活動屬性  
 下表顯示 <xref:System.ServiceModel.Activities.Receive> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中或在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上編輯。 唯一必要的屬性是 <xref:System.ServiceModel.Activities.Receive.OperationName%2A> 屬性。  
  
|屬性名稱|必要項|使用方式|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.ServiceModel.Activities.Receive> 活動的易記名稱。 預設值是 Receive。<br /><br /> 雖然不是必須使用非預設值做為易記 <xref:System.Activities.Activity.DisplayName%2A>，但建議您盡量使用這類型的值。|  
|<xref:System.ServiceModel.Activities.Receive.OperationName%2A>|True|指定這個 <xref:System.ServiceModel.Activities.Receive> 活動實作之服務作業的名稱。 這個屬性用來建構的預設值為**動作**屬性如果**動作**未明確設定屬性。|  
|<xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>|False|指定服務合約的名稱。 這個屬性會用於將服務作業群組為個別的服務合約。 具有相同 <xref:System.ServiceModel.Activities.Receive> 的所有 <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> 活動，都會分組歸類到同一個服務合約 (WSDL 連接埠類型)。 預設值是最上層 (根) 活動的完整 CLR 名稱。|  
|<xref:System.ServiceModel.Activities.Receive.Content%2A>|False|指定要接收的訊息或參數內容。 這可以是 <xref:System.ServiceModel.Activities.ReceiveMessageContent> 活動或 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 活動。 編輯這個屬性旁邊的橢圓形按鈕，即可**內容**在屬性方格，或按一下欄位**定義...**按鈕**內容**上加上標籤**接收**活動設計工具介面。 兩者都顯示**內容定義**對話方塊。 [!INCLUDE[crabout](../test/includes/crabout_md.md)]如何使用此方塊，請參閱[內容定義對話方塊](../workflow-designer/content-definition-dialog-box.md)主題。|  
|<xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>|False|指定某個具有 <xref:System.ServiceModel.Activities.Receive> 物件之工作流程的服務作業中，不同 <xref:System.ServiceModel.MessageQuerySet> 活動之間的相互關聯。 按一下省略符號按鈕旁的 [<xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>屬性以開啟 [屬性] 方格中的**CorrelatesOn 定義**] 對話方塊。 [!INCLUDE[crabout](../test/includes/crabout_md.md)]使用此對話方塊，請參閱[內容定義對話方塊](../workflow-designer/content-definition-dialog-box.md)主題。|  
|<xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A>|False|指定用來路由訊息到適當工作流程執行個體的 <xref:System.ServiceModel.Activities.CorrelationHandle>。<br /><br /> 按一下省略符號按鈕旁的 [<xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A>屬性以開啟 [屬性] 方格中的**運算式編輯器**] 對話方塊。 [!INCLUDE[crabout](../test/includes/crabout_md.md)]使用此對話方塊，請參閱[How to： 使用運算式編輯器](../workflow-designer/how-to-use-the-expression-editor.md)主題。|  
|<xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A>|False|指定 <xref:System.ServiceModel.Activities.CorrelationInitializer> 物件的集合，這些物件會初始化多個 <xref:System.ServiceModel.Activities.CorrelationHandle> 物件，用來設定工作流程內的這個 <xref:System.ServiceModel.Activities.Receive> 活動。 按一下省略符號按鈕旁的 [<xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A>屬性以開啟 [屬性] 方格中的**加入相互關聯初始設定式**] 對話方塊。 [!INCLUDE[crabout](../test/includes/crabout_md.md)]使用此方塊中，請參閱[加入 CorrelationInitializers 對話方塊](../workflow-designer/add-correlationinitializers-dialog-box.md)主題。|  
|<xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A>|False|指定值，這個值會判斷如果訊息與現有的工作流程執行個體之間不具有相互關聯，是否要建立新的工作流程執行個體來處理該訊息。 如果值設定為**true**，來處理訊息時未與現有的工作流程執行個體相互關聯訊息建立新的工作流程執行個體。|  
|<xref:System.ServiceModel.Activities.Receive.KnownTypes%2A>|False|指定這個 <xref:System.ServiceModel.Activities.Receive> 活動實作服務作業之已知型別的集合。 這個屬性應該搭配 <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> 屬性 (設定為 <xref:System.Runtime.Serialization.DataContractSerializer>) 使用。 如果使用 <xref:System.Xml.Serialization.XmlSerializer>，則會忽略此項。<br /><br /> 按一下旁邊的橢圓形按鈕**KnownTypes**欄位在屬性方格中顯示**型別集合編輯器**對話方塊中，您可以加入相關型別。 [!INCLUDE[crabout](../test/includes/crabout_md.md)]使用此方塊中，請參閱[型別集合編輯器對話方塊](../workflow-designer/type-collection-editor-dialog-box.md)主題。|  
|<xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A>|False|指定訊息的 <xref:System.Net.Security.ProtectionLevel>。<br /><br /> 1。<xref:System.Net.Security.ProtectionLevel>表示僅有驗證。<br />2。<xref:System.Net.Security.ProtectionLevel>表示簽署資料以協助確保傳輸之資料的完整性。<br />3。<xref:System.Net.Security.ProtectionLevel>表示加密並簽署資料以協助確保傳輸資料的完整性與機密性。|  
|<xref:System.ServiceModel.Activities.Receive.SerializerOption%2A>|False|指定 <xref:System.ServiceModel.Activities.Receive> 活動實作服務作業之序列化程式的型別。 預設值是 <xref:System.Runtime.Serialization.DataContractSerializer>，這會使用提供的資料合約，將型別的執行個體序列化及還原序列化，成為 XML 資料流或文件。 如果 XML 需要更多控制，也可以使用 <xref:System.Xml.Serialization.XmlSerializer>。|  
|<xref:System.ServiceModel.Activities.Receive.Action%2A>|False|指定訊息的動作標頭。 如果它未明確設定，其值會預設為： https://tempuri.org/ {服務合約命名空間} / {服務合約名稱} / {作業名稱}。|  
  
## <a name="see-also"></a>另請參閱  
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [傳送](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)