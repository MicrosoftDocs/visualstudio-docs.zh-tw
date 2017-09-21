---
title: "規則傳播模型內的變更 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "程式設計網域模型的定義域專屬語言"
  - "定義域專屬語言規則"
ms.assetid: 1690a38a-c8f5-4bc6-aab9-015771ec6647
caps.latest.revision: 30
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 30
---
# 規則傳播模型內的變更
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以建立存放區的規則，以傳播變更從一個項目到另一個視覺效果和模型 SDK \(VMSDK\)。 存放區中的任何項目變更時，規則被排程執行，通常最外層的交易認可時。 有不同類型的不同類型的事件，例如加入一個項目，或刪除它的規則。 您可以將規則附加到特定類型的項目、 圖形或圖表。 許多內建功能由規則定義︰ 例如，規則可確保模型變更時，會更新圖表。 您可以加入您自己的規則來自訂定義域專屬語言。  
  
 規則存放區是在存放區\-也就是變更傳播變更模型項目、 關聯性、 圖形或連接器和其網域屬性特別有用。 當使用者叫用復原或取消復原命令，不要執行規則。 相反地，交易管理員可確保存放內容會還原到正確的狀態。 如果您想要將變更傳播到外部存放區資源，使用儲存的事件。 如需詳細資訊，請參閱[事件處理常式傳播模型外的變更](../modeling/event-handlers-propagate-changes-outside-the-model.md)。  
  
 例如，假設您想要指定每當使用者 （或您的程式碼） 會建立新的項目型別 ExampleDomainClass，另一種類型的其他項目會在另一個模型的一部分。 您可以撰寫 AddRule，關聯 ExampleDomainClass。 您會撰寫程式碼來建立其他項目的規則中。  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using Microsoft.VisualStudio.Modeling;  
  
namespace ExampleNamespace  
{  
 // Attribute associates the rule with a domain class:  
 [RuleOn(typeof(ExampleDomainClass), FireTime=TimeToFire.TopLevelCommit)]  
 // The rule is a class derived from one of the abstract rules:  
 class MyAddRule : AddRule  
 {  
  // Override the abstract method:  
  public override void ElementAdded(ElementAddedEventArgs e)  
  {  
    base.ElementAdded(e);  
    ExampleDomainClass element = e.ModelElement;  
    Store store = element.Store;  
    // Ignore this call if we're currently loading a model:  
    if (store.TransactionManager.CurrentTransaction.IsSerializing)   
       return;  
  
    // Code here propagates change as required – for example:  
      AnotherDomainClass echo = new AnotherDomainClass(element.Partition);  
      echo.Name = element.Name;  
      echo.Parent = element.Parent;    
    }  
  }  
 // The rule must be registered:  
 public partial class ExampleDomainModel  
 {  
   protected override Type[] GetCustomDomainModelTypes()  
   {  
     List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
     types.Add(typeof(MyAddRule));  
     // If you add more rules, list them here.   
     return types.ToArray();  
   }  
 }  
}  
  
```  
  
> [!NOTE]
>  規則的程式碼應該變更的狀態只有項目存放區。也就是說，規則應該變更只模型項目、 關聯性、 圖形、 連接線、 圖表或其屬性。 如果您想要將變更傳播到外部存放區資源，定義儲存的事件。 如需詳細資訊，請參閱[事件處理常式傳播模型外的變更](../modeling/event-handlers-propagate-changes-outside-the-model.md)。  
  
### 若要定義規則  
  
1.  定義規則，加上類別 `RuleOn` 屬性。 與您的網域類別、 關聯性或圖表項目之一屬性產生關聯的規則。 這個類別，可能是抽象的每個執行個體，將套用的規則。  
  
2.  註冊將其加入至所傳回的集合規則 `GetCustomDomainModelTypes()` 網域模型類別中。  
  
3.  規則從衍生類別的其中一個抽象的規則類別，並撰寫的程式碼的執行方法。  
  
 下列各節說明這些步驟詳細資料。  
  
### 網域類別上定義的規則  
  
-   在自訂程式碼檔案中，定義類別，並在它前面加 <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> 屬性︰  
  
    ```  
    [RuleOn(typeof(ExampleElement),   
         // Usual value – but required, because it is not the default:  
         FireTime = TimeToFire.TopLevelCommit)]   
    class MyRule ...  
  
    ```  
  
-   主體類型中的第一個參數可以是網域類別、 網域關聯性、 圖形、 連接線或圖表。 通常，您將規則套用至網域類別和關聯性。  
  
     `FireTime` 通常是 `TopLevelCommit`。 這可確保交易的所有主要的變更之後，才執行的規則。 替代項目會以內嵌方式，變更; 後立即執行規則和 LocalCommit，它會執行在目前的交易 （這可能不是最外層） 結尾的規則。 您也可以設定會影響在佇列中，其排序規則的優先順序，但這是不可靠的方法，達到您所需要的結果。  
  
-   您可以指定的抽象類別，做為主體類型。  
  
-   規則套用到主體類別的所有執行個體。  
  
-   預設值為 `FireTime` 是 TimeToFire.TopLevelCommit。 這會導致最外層的交易認可時要執行規則。 替代方法是 TimeToFire.Inline。 這會導致觸發的事件後立即執行規則。  
  
### 若要註冊的規則  
  
-   將規則類別加入至所傳回的類型清單 `GetCustomDomainModelTypes` 網域模型中︰  
  
    ```  
    public partial class ExampleDomainModel  
     {  
       protected override Type[] GetCustomDomainModelTypes()  
       {  
         List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
         types.Add(typeof(MyAddRule));  
         // If you add more rules, list them here.   
         return types.ToArray();  
       }  
     }  
  
    ```  
  
-   如果您不確定您的網域模型類別名稱，尋找檔案內的 **Dsl\\GeneratedCode\\DomainModel.cs**  
  
-   在您的 DSL 專案中的自訂程式碼檔案撰寫此程式碼。  
  
### 若要撰寫的程式碼的規則  
  
-   從下列基底類別的其中一個衍生規則類別︰  
  
    |基底類別|觸發程序|  
    |----------|----------|  
    |<xref:Microsoft.VisualStudio.Modeling.AddRule>|加入項目、 連結或圖形。<br /><br /> 使用此選項以偵測新的關聯性，除了新的項目。|  
    |<xref:Microsoft.VisualStudio.Modeling.ChangeRule>|網域屬性值已變更。 方法引數提供舊的和新值。<br /><br /> 此規則會觸發圖形，當內建 `AbsoluteBounds` 屬性變更，如果圖形移動時。<br /><br /> 在許多情況下，會比較方便覆寫 `OnValueChanged` 或 `OnValueChanging` 屬性處理常式中。 變更立即之前和之後，會呼叫這些方法。 相較之下，此規則通常會在交易結束執行。 如需詳細資訊，請參閱[網域屬性值變更處理常式](../modeling/domain-property-value-change-handlers.md)。 **Note:**  建立或刪除連結時，則不會觸發此規則。 相反地，寫入 `AddRule` 和 `DeleteRule` 網域關聯性。|  
    |<xref:Microsoft.VisualStudio.Modeling.DeletingRule>|即將被刪除的項目或連結時，就會觸發。 屬性 ModelElement.IsDeleting 為 true，直到交易結束為止。|  
    |<xref:Microsoft.VisualStudio.Modeling.DeleteRule>|已刪除的項目或連結時執行。 所有其他規則已執行，包括 DeletingRules 之後，會執行規則。 ModelElement.IsDeleting 為 false，而且 ModelElement.IsDeleted 為 true。 若要允許後續復原，此項目實際上不會移除從記憶體中，但從 Store.ElementDirectory 中移除。|  
    |<xref:Microsoft.VisualStudio.Modeling.MoveRule>|項目移到另一個存放區的資料分割。<br /><br /> （請注意，這不與圖形的圖形化的位置）。|  
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule>|此規則只適用於網域關聯性。 如果您明確地指派任一端的連結模型項目，會觸發其項目。|  
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule>|從項目或連結的順序連結上使用 MoveBefore 或 MoveToIndex 方法變更時觸發。|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule>|建立交易時執行。|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule>|認可交易時執行。|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule>|回復交易時執行。|  
  
-   每個類別具有您覆寫的方法。 型別 `override` 才能探索該類別中。 這個方法的參數會識別正在變更的項目。  
  
 請注意下列有關規則的重點︰  
  
1.  在交易中的變更集可能會觸發許多規則。 通常，最外層的交易認可時，會執行規則。 它們會以指定的順序執行。  
  
2.  一律在交易內執行的規則。 因此，您不必建立新的交易，以便進行變更。  
  
3.  交易已回復，或復原或取消復原作業時，不會執行規則。 這些作業重設成先前的狀態存放區的所有內容。 因此，如果您的規則存放區外的任何內容的狀態變更，它可能會將保留在 synchronism 與存放區內容。 若要更新外部存放區的狀態，最好是使用事件。 如需詳細資訊，請參閱[事件處理常式傳播模型外的變更](../modeling/event-handlers-propagate-changes-outside-the-model.md)。  
  
4.  從檔案載入模型時，會執行一些規則。 若要判斷載入或儲存是否正在進行中，使用 `store.TransactionManager.CurrentTransaction.IsSerializing`。  
  
5.  如果您的規則的程式碼會建立多個規則的觸發程序，它們將會新增至清單的結尾引發，並在交易完成之前會先執行。 DeletedRules 之後的所有其他規則執行。 一個規則可以在交易中，每個變更一次執行的次數。  
  
6.  若要傳遞規則的資訊，您可以將資訊儲存於 `TransactionContext`。 這是只會保留在交易期間的字典。 當交易結束時，會處置。 在每個規則的事件引數提供給它的存取。 請記住規則不會執行可預測的順序。  
  
7.  使用其他替代項目後的規則。 例如，如果您想要更新屬性值變更時，請考慮使用計算的屬性。 如果您想要限制的大小或圖形的位置，使用 `BoundsRule`。 如果您想要回應的屬性值變更時，加入 `OnValueChanged` 屬性處理常式。 如需詳細資訊，請參閱[回應及傳播變更](../modeling/responding-to-and-propagating-changes.md)。  
  
## 範例  
 當網域關聯性來連結兩個項目執行個體化時，下列範例會更新屬性。 不只在使用者建立時連結在圖表上，同時也如果程式碼會建立一個連結，將會觸發規則。  
  
 若要測試此範例中，建立 DSL 使用工作流程 」 方案範本，然後插入下列程式碼 Dsl 專案中的檔案。 建置並執行方案，並在偵錯專案中開啟範例檔案。 繪製註解連結之間的註解圖案和資料流程項目。 在註解的文字變更為報表的最新的項目，您已經連接到它。  
  
 在實務上，您通常會針對每個 AddRule 撰寫 DeleteRule。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Microsoft.VisualStudio.Modeling;  
  
namespace Company.TaskRuleExample  
{  
  
  [RuleOn(typeof(CommentReferencesSubjects))]  
  public class RoleRule : AddRule  
  {  
  
    public override void ElementAdded(ElementAddedEventArgs e)  
    {  
      base.ElementAdded(e);  
      CommentReferencesSubjects link = e.ModelElement as CommentReferencesSubjects;  
      Comment comment = link.Comment;  
      FlowElement subject = link.Subject;  
      Transaction current = link.Store.TransactionManager.CurrentTransaction;  
      // Don't want to run when we're just loading from file:  
      if (current.IsSerializing) return;  
      comment.Text = "Flow has " + subject.FlowTo.Count + " outgoing connections";  
    }  
  
  }  
  
  public partial class TaskRuleExampleDomainModel  
  {  
    protected override Type[] GetCustomDomainModelTypes()  
    {  
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
      types.Add(typeof(RoleRule));  
      return types.ToArray();  
    }  
  }  
  
}  
  
```  
  
## 請參閱  
 [事件處理常式傳播模型外的變更](../modeling/event-handlers-propagate-changes-outside-the-model.md)   
 [BoundsRules 限制圖案位置和大小](../modeling/boundsrules-constrain-shape-location-and-size.md)