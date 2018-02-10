---
title: "規則將在模型中的變更傳播 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: af086275f641e3237f8d22308c960ad30240b647
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="rules-propagate-changes-within-the-model"></a>規則傳播模型內的變更
您可以建立將變更傳播會在項目到另一個 Visualization and Modeling SDK (VMSDK) 中的存放區規則。 存放區中的任何項目變更時，規則排程時所要執行，通常就會認可最外層的交易。 有不同類型的不同類型的事件，例如加入新項目，或刪除它的規則。 您可以將規則附加到特定類型的項目、 圖形或圖表。 許多內建功能由規則定義： 例如，規則可確保模型變更時，會更新圖表。 您可以自訂特定領域語言，加入您自己的規則。  
  
 規則存放區是將內部存放區-也就是變更傳播變更至模型項目、 關聯性、 圖形或連接器，以及其網域屬性特別有用。 當使用者叫用復原或取消復原命令時，不會執行規則。 相反地，交易管理員可確保存放內容會還原到正確的狀態。 如果您想要將變更傳播到外部存放區資源，使用儲存的事件。 如需詳細資訊，請參閱[事件處理常式傳播變更外部模型](../modeling/event-handlers-propagate-changes-outside-the-model.md)。  
  
 例如，假設您想要指定每當使用者 （或您的程式碼） 建立新項目型別 ExampleDomainClass，模型的另一個組件中建立另一種類型的其他項目。 您無法撰寫 AddRule，並將它與 ExampleDomainClass 關聯。 您會撰寫程式碼中建立其他項目的規則。  
  
```csharp  
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
  
    // Code here propagates change as required - for example:  
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
>  規則的程式碼應該變更只有在存放區; 內的項目狀態也就是說，規則應該變更只模型項目、 關聯性、 圖形、 連接器、 圖表或其屬性。 如果您想要將變更傳播到外部存放區資源，定義儲存的事件。 如需詳細資訊，請參閱[事件處理常式傳播變更外部模型](../modeling/event-handlers-propagate-changes-outside-the-model.md)  
  
### <a name="to-define-a-rule"></a>若要定義規則  
  
1.  定義規則，如前面會加上類別`RuleOn`屬性。 與您的網域類別、 關聯性或圖表元素的其中一個屬性產生關聯的規則。 規則將套用至這個類別，可能是抽象的每個執行個體。  
  
2.  註冊規則加入至所傳回之集`GetCustomDomainModelTypes()`在您的網域模型類別。  
  
3.  規則從衍生類別的其中一個抽象的規則類別，並撰寫程式碼的執行方法。  
  
 下列章節將詳述這些步驟。  
  
### <a name="to-define-a-rule-on-a-domain-class"></a>若要在網域類別上定義的規則  
  
-   在自訂程式碼檔案中，將類別定義，並在它前面加<xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute>屬性：  
  
    ```  
    [RuleOn(typeof(ExampleElement),   
         // Usual value - but required, because it is not the default:  
         FireTime = TimeToFire.TopLevelCommit)]   
    class MyRule ...  
  
    ```  
  
-   主體類型的第一個參數可以是領域類別、 網域關聯性、 形狀、 連接器或圖表。 通常，您將規則套用至網域類別和關聯性。  
  
     `FireTime`通常是`TopLevelCommit`。 這可確保會執行規則，只在進行交易的所有主要的變更之後。 替代會以內嵌方式，變更; 之後，即會執行規則和 LocalCommit，它會執行目前的交易 （這可能不是最外層） 結尾的規則。 您也可以設定會影響在佇列中，其排序規則的優先順序，但這是不可靠的方法達到您所需要的結果。  
  
-   您可以指定的抽象類別，做為主體類型。  
  
-   將規則套用到主體類別的所有執行個體。  
  
-   預設值為`FireTime`是 TimeToFire.TopLevelCommit。 這會導致最外層的交易認可時要執行規則。 替代方式是 TimeToFire.Inline。 這會導致執行觸發的事件之後，即規則。  
  
### <a name="to-register-the-rule"></a>註冊規則  
  
-   將規則類別加入至所傳回的類型清單`GetCustomDomainModelTypes`網域模型中：  
  
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
  
-   如果您不確定您的網域模型類別的名稱，尋找檔案內**Dsl\GeneratedCode\DomainModel.cs**  
  
-   DSL 專案中的自訂程式碼檔案中撰寫此程式碼。  
  
### <a name="to-write-the-code-of-the-rule"></a>撰寫程式碼的規則  
  
-   從下列基底類別的其中一個衍生規則類別：  
  
    |基底類別|觸發程序|  
    |----------------|-------------|  
    |<xref:Microsoft.VisualStudio.Modeling.AddRule>|加入項目、 連結或圖形。<br /><br /> 使用此偵測新的關聯性，除了新的項目。|  
    |<xref:Microsoft.VisualStudio.Modeling.ChangeRule>|網域屬性值已變更。 方法引數提供的舊的和新值。<br /><br /> 形狀，就會觸發這個規則時內建`AbsoluteBounds`屬性變更，如果圖形移動時。<br /><br /> 在許多情況下，會比較方便覆寫`OnValueChanged`或`OnValueChanging`屬性處理常式中。 變更立即之前和之後，會呼叫這些方法。 相反地，規則通常會在交易結束執行。 如需詳細資訊，請參閱[網域屬性值變更處理常式](../modeling/domain-property-value-change-handlers.md)。 **注意：**建立或刪除連結時，不會觸發這個規則。 相反地，寫入`AddRule`和`DeleteRule`網域關聯性。|  
    |<xref:Microsoft.VisualStudio.Modeling.DeletingRule>|即將刪除的項目或連結時，就會觸發。 屬性 ModelElement.IsDeleting 成立直到交易結束為止。|  
    |<xref:Microsoft.VisualStudio.Modeling.DeleteRule>|已刪除的項目或連結時執行。 所有其他規則已執行，包括 DeletingRules 之後，會執行規則。 ModelElement.IsDeleting 為 false，而且 ModelElement.IsDeleted 為 true。 若要允許進行後續的復原，項目實際上不會移除從記憶體中，但會從 Store.ElementDirectory 移除。|  
    |<xref:Microsoft.VisualStudio.Modeling.MoveRule>|項目移至另一個存放區的磁碟分割。<br /><br /> （請注意，這不與圖形化圖案的位置）。|  
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule>|此規則只適用於網域關聯性。 如果您必須明確地將模型項目指派給連結的兩端，觸發。|  
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule>|從項目或連結的順序在連結上使用的 MoveBefore 或 MoveToIndex 方法變更時觸發。|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule>|在建立的交易時執行。|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule>|不會認可交易時執行。|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule>|回復交易時執行。|  
  
-   每個類別具有您覆寫的方法。 型別`override`才能探索該類別中。 這個方法的參數識別正在變更的項目。  
  
 請注意下列有關規則的重點：  
  
1.  在交易中的變更集可能會觸發許多規則。 通常，當最外層的交易認可時，會執行規則。 未指定的順序執行它們。  
  
2.  在交易內，則一律執行規則。 因此，您不必建立新的交易進行變更。  
  
3.  回復交易，或復原或取消復原作業時，不會執行規則。 這些作業重設其先前狀態存放區的所有內容。 因此，如果您的規則存放區外的任何內容的狀態變更，它可能會保留 synchronism 與存放區中內容。 若要更新外部存放區的狀態，最好是使用事件。 如需詳細資訊，請參閱[事件處理常式傳播變更外部模型](../modeling/event-handlers-propagate-changes-outside-the-model.md)。  
  
4.  從檔案載入模型時，會執行一些規則。 若要判斷載入或儲存是否正在進行中，使用`store.TransactionManager.CurrentTransaction.IsSerializing`。  
  
5.  如果您的規則的程式碼會建立更多的規則觸發程序，它們將會引發清單結尾，加入並在異動完成之前會先執行。 所有其他規則後，會執行 DeletedRules。 一項規則可以執行許多次，在交易中，每個變更一次。  
  
6.  若要通過規則的資訊，您可以儲存中的資訊`TransactionContext`。 這是只在交易期間維護的字典。 當交易結束時，會處置。 每個規則中的事件引數提供給它的存取。 請記住可預測的順序不會執行規則。  
  
7.  使用規則之後考慮其他替代方案。 例如，如果您想要更新屬性值變更時，請考慮使用計算的屬性。 如果您想要限制的大小或圖形的位置，使用`BoundsRule`。 如果您想要回應的屬性值變更時，新增`OnValueChanged`屬性處理常式。 如需詳細資訊，請參閱[回應和傳播變更](../modeling/responding-to-and-propagating-changes.md)。  
  
## <a name="example"></a>範例  
 領域關聯具現化連結兩個項目時，下列範例會更新屬性。 不只當使用者建立的連結在圖表上，但也如果程式碼會建立一個連結，將會觸發此規則。  
  
 若要測試此範例中，建立 DSL 使用工作流程解決方案範本，並將下列程式碼插入 Dsl 專案中的檔案。 建置並執行方案，以及開啟偵錯專案中的範例檔案。 繪製註解連結之間的註解圖案和資料流程項目。 註解變更的最新的項目，您已經連接到報表中的文字。  
  
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
  
## <a name="see-also"></a>請參閱  
 [事件處理常式將模型之外的變更傳播](../modeling/event-handlers-propagate-changes-outside-the-model.md)   
 [BoundsRules 限制圖案位置和大小](../modeling/boundsrules-constrain-shape-location-and-size.md)