---
title: 規則傳播模型內的變更 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
ms.assetid: 1690a38a-c8f5-4bc6-aab9-015771ec6647
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: ab05923a02176f4c0d8aa30ac9d26b0e41868396
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49222712"
---
# <a name="rules-propagate-changes-within-the-model"></a>規則傳播模型內的變更
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以建立存放區的規則，以將變更傳播從一個項目到另一個在 Visualization and Modeling SDK (VMSDK)。 存放區中的任何項目變更時發生，來執行，只有認可的最外層的交易時，通常被排定規則。 有不同類型的不同類型的事件，例如加入項目，或刪除它的規則。 您可以將規則附加至特定類型的項目、 圖形或圖表。 許多內建功能由規則定義： 例如，規則可確保當模型變更時，會更新圖表。 您可以自訂特定領域語言，藉由新增您自己的規則。  
  
 規則存放區會特別有用，如內存放區 – 也就是變更傳播變更至模型項目、 關聯性、 圖形或連接器和其網域屬性。 當使用者叫用復原或取消復原命令時，不會執行規則。 相反地，交易管理員可確保存放內容會還原到正確的狀態。 如果您想要將變更傳播到外部存放區的資源，使用儲存的事件。 如需詳細資訊，請參閱 <<c0> [ 事件處理常式傳播變更外部模型](../modeling/event-handlers-propagate-changes-outside-the-model.md)。  
  
 例如，假設您想要指定每當使用者 （或您的程式碼） 會建立新的項目型別的 ExampleDomainClass，另一種類型的其他項目會在另一個模型的一部分。 您可以撰寫 AddRule，並將它關聯 ExampleDomainClass。 您需要撰寫程式碼中的規則，以建立其他的項目。  
  
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
>  規則的程式碼應變更市集; 內的項目只有狀態也就是說，規則應該變更只有模型項目、 關聯性、 圖形、 連接器、 圖表或其屬性。 如果您想要將變更傳播到外部存放區的資源，定義儲存的事件。 如需詳細資訊，請參閱[事件處理常式傳播變更外部模型](../modeling/event-handlers-propagate-changes-outside-the-model.md)  
  
### <a name="to-define-a-rule"></a>若要定義規則  
  
1.  定義規則，如前面會加上類別`RuleOn`屬性。 屬性會將規則與其中一個網域類別、 關聯性或圖表項目產生關聯。 此規則將套用至每個執行個體，這個類別，它可能是抽象。  
  
2.  註冊規則，方法是將它新增至所傳回之集`GetCustomDomainModelTypes()`網域模型類別中。  
  
3.  從其中一個抽象的規則類別，衍生規則類別，並撰寫程式碼的執行方法。  
  
 下列各節會說明這些步驟，在更多詳細資料。  
  
### <a name="to-define-a-rule-on-a-domain-class"></a>若要在網域類別上定義的規則  
  
-   在自訂程式碼檔案中，定義的類別，並在它前面加<xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute>屬性：  
  
    ```  
    [RuleOn(typeof(ExampleElement),   
         // Usual value – but required, because it is not the default:  
         FireTime = TimeToFire.TopLevelCommit)]   
    class MyRule ...  
  
    ```  
  
-   主體類型的第一個參數可以是網域類別、 網域關聯性、 圖形、 連接器或圖表。 通常，您將規則套用至網域類別和關聯性。  
  
     `FireTime`通常是`TopLevelCommit`。 這可確保只有在已進行交易的所有主要的變更之後，才便執行該項規則。 替代項目會以內嵌方式，它會執行規則，隨後變更;和 LocalCommit，它會執行目前的交易 （這可能不是最外層） 結尾的規則。 您也可以設定會影響在佇列中，其排序規則的優先順序，但這是不可靠的方法，達成您所需要的結果。  
  
-   您可以指定的抽象類別，做為主體類型。  
  
-   將規則套用到主體類別的所有執行個體。  
  
-   預設值為`FireTime`是 TimeToFire.TopLevelCommit。 這會導致最外層的交易認可時要執行規則。 替代方法是 TimeToFire.Inline。 這會導致觸發的事件後立即執行規則。  
  
### <a name="to-register-the-rule"></a>若要註冊規則  
  
-   將您的規則類別新增至所傳回的類型清單`GetCustomDomainModelTypes`領域模型中：  
  
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
  
-   如果您不確定您的領域模型類別的名稱，尋找檔案內**Dsl\GeneratedCode\DomainModel.cs**  
  
-   這段程式碼檔案中撰寫自訂程式碼在您的 DSL 專案中。  
  
### <a name="to-write-the-code-of-the-rule"></a>若要撰寫的程式碼的規則  
  
-   從下列基底類別的其中一個衍生規則類別：  
  
    |基底類別|觸發程序|  
    |----------------|-------------|  
    |<xref:Microsoft.VisualStudio.Modeling.AddRule>|新增項目、 連結或圖形。<br /><br /> 使用此選項來偵測新的關聯性，除了新的項目。|  
    |<xref:Microsoft.VisualStudio.Modeling.ChangeRule>|網域屬性值已變更。 方法引數提供的舊和新值。<br /><br /> 如圖形，就會觸發這個規則時內建`AbsoluteBounds`屬性變更，如果圖形移動時。<br /><br /> 在許多情況下，會更方便地覆寫`OnValueChanged`或`OnValueChanging`屬性處理常式中。 變更立即之前和之後，會呼叫這些方法。 相反地，規則通常會在交易結束執行。 如需詳細資訊，請參閱 <<c0> [ 網域屬性值變更處理常式](../modeling/domain-property-value-change-handlers.md)。 **注意：** 建立或刪除連結時，不會觸發此規則。 相反地，撰寫`AddRule`和`DeleteRule`網域關聯性。|  
    |<xref:Microsoft.VisualStudio.Modeling.DeletingRule>|即將刪除的項目或連結時觸發。 屬性 ModelElement.IsDeleting 成立直到交易結束為止。|  
    |<xref:Microsoft.VisualStudio.Modeling.DeleteRule>|已刪除的項目或連結時執行。 所有其他規則已執行，包括 DeletingRules 之後，會執行規則。 ModelElement.IsDeleting 為 false，而且 ModelElement.IsDeleted 為 true。 若要供後續的復原，項目實際上不會移除從記憶體中，但它會從 Store.ElementDirectory 移除。|  
    |<xref:Microsoft.VisualStudio.Modeling.MoveRule>|項目移到另一個存放區的資料分割。<br /><br /> （請注意，這不相關，圖形化圖案的位置）。|  
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule>|此規則只適用於網域關聯性。 如果您明確地將模型項目指派給連結的任一端，就會觸發這項目。|  
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule>|或從項目連結的順序連結使用的 MoveBefore 或 MoveToIndex 方法變更時觸發。|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule>|會建立的交易時，就會執行。|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule>|執行會認可交易時。|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule>|執行回復交易時。|  
  
-   每個類別會具有您覆寫的方法。 型別`override`在您的類別，以進行探索。 此方法的參數會識別正在變更的項目。  
  
 請注意下列有關規則的重點：  
  
1.  一組在交易中的變更可能會觸發許多規則。 通常，最外層的交易認可時，會執行規則。 它們會在未指定的順序執行。  
  
2.  規則一律會在交易內執行。 因此，您不必建立新的交易進行變更。  
  
3.  當交易已回復，或執行復原或重做作業時，不會執行規則。 這些作業會重設其先前狀態的存放區的所有內容。 因此，如果您的規則變更的外部存放區的任何項目狀態時，它可能不請 synchronism 存放區內容。 若要更新外部存放區的狀態，最好是使用事件。 如需詳細資訊，請參閱 <<c0> [ 事件處理常式傳播變更外部模型](../modeling/event-handlers-propagate-changes-outside-the-model.md)。  
  
4.  從檔案載入模型時，會執行一些規則。 若要判斷載入或儲存是否正在進行中，使用`store.TransactionManager.CurrentTransaction.IsSerializing`。  
  
5.  如果您的規則的程式碼會建立多個規則的觸發程序，它們會新增至清單的結尾引發，並在異動完成之前會先執行。 DeletedRules 執行之後的所有其他規則。 一項規則可以執行許多次，在交易中，每個變更一次。  
  
6.  若要傳遞規則的資訊，您可以儲存中的資訊`TransactionContext`。 這是只會保留在交易期間的字典。 當交易結束時，會處置它。 每個規則中的事件引數提供給它的存取。 請記住規則不會執行可預測的順序。  
  
7.  除了考慮其他替代方案的使用規則。 例如，如果您想要更新屬性值變更時，請考慮使用計算的屬性。 如果您想要限制的大小或形狀的位置，使用`BoundsRule`。 如果您想要回應的屬性值變更時，新增`OnValueChanged`給屬性的處理常式。 如需詳細資訊，請參閱 <<c0> [ 回應及傳播變更](../modeling/responding-to-and-propagating-changes.md)。  
  
## <a name="example"></a>範例  
 若要將兩個項目連結的網域關聯性具現化時，下列範例會更新屬性。 不只在使用者建立時連結在圖表中，但也如果程式碼會建立連結，就會觸發此規則。  
  
 若要測試此範例中，建立 DSL 使用工作流程 」 方案範本，並在 Dsl 專案中的檔案中插入下列程式碼。 建置和執行方案，並開啟偵錯專案中的範例檔案。 繪製註解連結之間的註解圖形和資料流程項目。 中的最新的項目，您已經連接到報表的註解變更的文字。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [事件處理常式傳播模型外的變更](../modeling/event-handlers-propagate-changes-outside-the-model.md)   
 [BoundsRules 限制圖案位置和大小](../modeling/boundsrules-constrain-shape-location-and-size.md)



