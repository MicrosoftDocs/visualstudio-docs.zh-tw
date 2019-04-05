---
title: 定義工作項目連結處理常式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: d52e0bbf-0166-4bb4-a2e3-cefed6188875
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7bc151e69206e37f88eac04ac8bbb2f4d9dbf1ad
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58940826"
---
# <a name="define-a-work-item-link-handler"></a>定義工作項目連結處理常式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以建立 Visual Studio 整合擴充功能，當使用者建立或刪除 UML 模型項目和工作項目之間的連結時做出回應。 例如，當使用者選擇將新的工作項目連結至模型項目，您的程式碼可以從模型中的值初始化工作項目的欄位。  
  
## <a name="set-up-a-uml-extension-solution"></a>設定 UML 擴充功能方案  
 這會讓您開發處理常式，然後將它們分散給其他使用者。 您必須設定兩個 Visual Studio 專案：  
  
-   包含連結處理常式程式碼的類別庫專案。  
  
-   VSIX 專案，做為安裝命令的容器。 如果您想要，可以在相同的 VSIX 中包含其他元件。  
  
#### <a name="to-set-up-the-visual-studio-solution"></a>設定 Visual Studio 方案  
  
1.  建立類別庫專案，將它加入現有的 VSIX 方案，或是建立新的方案。  
  
    1.  在 [檔案]  功能表上，依序選擇 [新增] 和 [專案] 。  
  
    2.  底下**已安裝的範本**，展開**Visual C#** 或是**Visual Basic**，然後在中間的資料行中按一下**類別庫**。  
  
    3.  設定 [方案]  以表示您是要建立新的方案，還是將元件加入已經開啟的 VSIX 方案。  
  
    4.  設定專案名稱和位置，然後按一下 [確定]。  
  
2.  除非您的方案已經包含 VSIX 專案，否則請建立一個。  
  
    1.  在 [方案總管] 中，在方案的捷徑功能表上，選擇 [新增] 和 [新增專案] 。  
  
    2.  在 [已安裝的範本] 下，依序展開 [Visual C#]  或 [Visual Basic] ，然後選取 [擴充性] 。 在中間的資料行中，選擇 [VSIX 專案] 。  
  
3.  將 VSIX 專案設定為方案的啟始專案。  
  
    -   在方案總管中，在 VSIX 專案的捷徑功能表上，選擇 [設定為啟始專案] 。  
  
4.  在  **source.extension.vsixmanifest**下方**內容**，新增類別庫專案做為 MEF 元件。  
  
    1.  在 [中繼資料]  索引標籤上，設定 VSIX 的名稱。  
  
    2.  在 [安裝目標]  索引標籤上，設定 Visual Studio 版本做為目標。  
  
    3.  在 [資產]  索引標籤上，選擇 [新增] ，然後在對話方塊中設定：  
  
          =   
  
          =   
  
          =   
  
## <a name="defining-the-work-item-link-handler"></a>定義工作項目連結處理常式  
 在類別庫專案中執行下列所有工作。  
  
### <a name="project-references"></a>專案參考  
 將下列 [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] 組件加入您的專案參考：  
  
 `Microsoft.TeamFoundation.WorkItemTracking.Client.dll`  
  
 `Microsoft.VisualStudio.TeamFoundation.WorkItemTracking.dll Microsoft.VisualStudio.Modeling.Sdk.[version]`  
  
 `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml`  
  
 `Microsoft.VisualStudio.Uml.Interfaces`  
  
 `System.ComponentModel.Composition`  
  
 `System.Drawing` -由範例程式碼  
  
 如果您找不到上述其中一個參考下 **.Net**索引標籤**加入參考**對話方塊中，使用 [瀏覽] 索引標籤來尋找在 \Program Files\Microsoft Visual Studio [版本] \Common7\IDE\在 PrivateAssemblies\\。  
  
### <a name="import-the-work-item-namespace"></a>匯入工作項目命名空間  
 在您[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]專案**參考**，加入下列組件的參考：  
  
- Microsoft.TeamFoundation.WorkItemTracking.Client.dll  
  
- Microsoft.VisualStudio.TeamFoundation.WorkItemTracking.dll  
  
  在您的程式碼中，匯入下列命名空間：  
  
```  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.Uml.Classes;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.TeamFoundation.WorkItemTracking;  
using System.Linq;  
```  
  
### <a name="define-the-linked-work-item-event-handler"></a>定義連結的工作項目事件處理常式  
 將類別檔案加入類別庫專案，並設定其內容，如下所示。 將命名空間和類別名稱變更為您偏好的任何內容。  
  
```  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.Uml.Classes;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.TeamFoundation.WorkItemTracking;  
using System.Linq;  
  
namespace WorkItems  
{  
  [Export(typeof(ILinkedWorkItemExtension))]  
  public class MyWorkItemExtension : ILinkedWorkItemExtension  
  {  
    // Called before a new work item is edited by the user.  
    // Use this to initialize work item fields from the model element.  
    public void OnWorkItemCreated(System.Collections.Generic.IEnumerable<IElement> elementsToBeLinked, IWorkItemDocument workItemDocument)  
    {  
      INamedElement namedElement =  
            elementsToBeLinked.First() as INamedElement;  
      if (namedElement != null)  
        workItemDocument.Item.Title = namedElement.Name;  
  
    }  
  
    // Called when any work item is linked to a model element.  
    public void OnWorkItemLinked(System.Collections.Generic.IEnumerable<IElement> elements, string serverUri, int workItemId)  
    {  
      foreach (IElement element in elements)  
        foreach (IShape shape in element.Shapes())  
          shape.Color = System.Drawing.Color.Red;  
    }  
  
    // Called when a work item is unlinked from a model element.  
    public void OnWorkItemRemoved(IElement element, string serverUri, int workItemId)  
    {  
      foreach (IShape shape in element.Shapes())  
        shape.Color = System.Drawing.Color.White;  
    }  
  }  
}  
```  
  
## <a name="testing-the-link-handler"></a>測試連結處理常式  
 基於測試目的，請在偵錯模式中執行連結處理常式。  
  
> [!WARNING]
>  您必須先連接 TFS 原始程式碼控制 (SCC) 才能建立或連結工作項目。 若您嘗試開啟連接至不同的 TFS SCC，Visual Studio 會自動關閉目前方案。 請先確認您已連接至適當的 SCC，再嘗試建立或連結至工作項目。 在更新版本的 Visual Studio 中，如果沒有連接至 SCC 即無法使用功能表命令。  
  
#### <a name="to-test-the-link-handler"></a>測試連結處理常式  
  
1.  按 **F5**，或在 [偵錯]  功能表上，選擇 [開始偵錯] 。  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的實驗執行個體隨即啟動。  
  
     **疑難排解**:如果新[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]不會啟動，請確定 VSIX 專案已設定為啟始專案的方案。  
  
2.  在實驗性 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]中，開啟或建立模型專案，並開啟或建立模型圖表。  
  
3.  建立模型項目，例如 UML 類別，並設定其名稱。  
  
4.  以滑鼠右鍵按一下項目，然後按一下**建立工作項目**。  
  
    -   如果子功能表顯示**開啟 Team Foundation Server 連接**，您必須關閉專案、 連接至適當的 TFS，並重新啟動此程序。  
  
    -   如果子功能表顯示工作項目類型的清單，請按一下其中一個。  
  
         新的工作項目表單隨即開啟。  
  
5.  如果您已經在上一節中使用範例程式碼，請確認工作項目的標題與模型項目相同。 這表示 `OnWorkItemCreated()` 已生效。  
  
6.  完成表單、儲存並關閉工作項目。  
  
7.  請確認工作項目現在是以紅色顯示。 這示範了範例程式碼的 `OnWorkItemLinked()`。  
  
     **疑難排解**:如果尚未執行的處理常式方法，確認：  
  
    -   類別庫專案會列為 MEF 元件**內容**列入**source.extensions.manifest**在 VSIX 專案。  
  
    -   正確的 `Export` 屬性會附加至處理常式類別，且該類別會實作 `ILinkedWorkItemExtension`。  
  
    -   所有 `Import` 和 `Export` 屬性的參數都有效。  
  
## <a name="about-the-work-item-handler-code"></a>關於工作項目處理常式程式碼  
  
### <a name="listening-for-new-work-items"></a>接聽新的工作項目  
 當使用者選擇要建立新的工作項目，以連結至模型項目時，會呼叫 `OnWorkItemCreated`。 您的程式碼可以初始化工作項目欄位。 接著工作項目會呈現給使用者，使用者可以更新欄位並儲存工作項目。 在成功儲存工作項目之前，不會建立模型項目的連結。  
  
```  
public void OnWorkItemCreated(  
    IEnumerable<IElement> elementsToBeLinked,  
    IWorkItemDocument workItem)  
{  
  INamedElement namedElement =   
         elementsToBeLinked.First() as INamedElement;  
  if (namedElement != null)  
      workItem.Item.Title = namedElement.Name;  
}  
```  
  
### <a name="listening-for-link-creation"></a>接聽連結建立作業  
 建立連結之後，會呼叫 `OnWorkItemLinked`。 不論連結是指向新的工作項目還是現有的項目，都會呼叫它。 針對每個工作項目會呼叫一次。  
  
```  
public void OnWorkItemLinked  
        (IEnumerable<IElement> elements,   
         string serverUri, // TFS server  
         int workItemId)  
{  
  foreach (IElement element in elements)  
    foreach (IShape shape in element.Shapes())  
         shape.Color = System.Drawing.Color.Red;  
}  
```  
  
> [!NOTE]
>  若要讓此範例運作，您必須在 `System.Drawing.dll` 加入專案參考，並匯入命名空間 `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation`。 不過，`OnWorkItemLinked` 的其他實作並不需要這些加入作業。  
  
### <a name="listening-for-link-removal"></a>接聽連結移除作業  
 在每個刪除的工作項目連結之前，會呼叫一次 `OnWorkItemRemoved`。 如果刪除模型項目，將會移除其所有連結。  
  
```  
public void OnWorkItemRemoved  
         (IElement element, string serverUri, int workItemId)  
{...}  
```  
  
## <a name="updating-a-work-item"></a>更新工作項目  
 您可以使用 Team Foundation 命名空間，來管理工作項目。  
  
 若要使用下列範例，請在您的專案參考加入這些 .NET 組件：  
  
-   Microsoft.TeamFoundation.Client.dll  
  
-   Microsoft.TeamFoundation.WorkItemTracking.Client.dll  
  
```  
  
using Microsoft.TeamFoundation.Client;  
using Microsoft.TeamFoundation.WorkItemTracking.Client;  
...  
public void OnWorkItemLinked  
        (IEnumerable<IElement> elements,   
         string serverUri, // TFS server  
         int workItemId)  
{  
  TfsTeamProjectCollection tfs =  
        TfsTeamProjectCollectionFactory  
            .GetTeamProjectCollection(new Uri(serverUri));  
  WorkItemStore workItemStore = new WorkItemStore(tfs);  
  WorkItem item = workItemStore.GetWorkItem(workItemId);  
  item.Open();  
  item.Title = "something";  
  item.Save();  
}   
```  
  
## <a name="accessing-the-work-item-reference-links"></a>存取工作項目參考連結  
 您可以如下所示存取連結：  
  
```  
//Get:  
string linkString = element.GetReference(ReferenceConstants.WorkItem);  
// Set:  
element.AddReference(ReferenceConstants.WorkItem, linkString, true);  
  
```  
  
 `linkString` 的格式為：  
  
 `string.Format(@"%{0}\{1}#{1}${2}", tfServer, projectCollection, RepositoryGuid, workItem.Id);`  
  
 其中：  
  
- 您的伺服器 URI 是：  
  
   `http://tfServer:8080/tfs/projectCollection`  
  
   大小寫在 `projectCollection` 中很重要。  
  
- 您可以從 TFS 連接取得 `RepositoryGuid`：  
  
  ```csharp  
  TfsTeamProjectCollection tpc = TfsTeamProjectCollectionFactory...;  
  RepositoryGuid= tpc.InstanceId;  
  
  ```  
  
  如需參考的詳細資訊，請參閱[將參考字串附加至 UML 模型項目](../modeling/attach-reference-strings-to-uml-model-elements.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.TeamFoundation.WorkItemTracking.Client.WorkItemStore?displayProperty=fullName>   
 [連結模型項目和工作項目](../modeling/link-model-elements-and-work-items.md)   
 [將參考字串附加至 UML 模型項目](../modeling/attach-reference-strings-to-uml-model-elements.md)   
 [定義與安裝模型擴充功能](../modeling/define-and-install-a-modeling-extension.md)   
 [使用 UML API 進行程式設計](../modeling/programming-with-the-uml-api.md)
