---
title: 規則傳播模型內的變更
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74d64b4fe0c0aa5293e11daad13f632c4a487736
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747424"
---
# <a name="rules-propagate-changes-within-the-model"></a>規則傳播模型內的變更
您可以在視覺效果和模型化 SDK （VMSDK）中建立存放區規則，將變更從某個元素傳播到另一個專案。 當存放區中的任何元素髮生變更時，會排定執行的規則，通常是在最外層的交易認可時。 不同種類的事件有不同類型的規則，例如新增專案或刪除專案。 您可以將規則附加至特定類型的元素、圖形或圖表。 許多內建功能都是由規則所定義：例如，當模型變更時，規則會確保圖表會更新。 您可以藉由新增自己的規則來自訂您的特定領域語言。

 存放區規則特別適合用來傳播存放區內的變更，也就是模型專案、關聯性、圖形或連接器的變更，以及其網域屬性。 當使用者叫用 [復原] 或 [重做] 命令時，不會執行規則。 相反地，交易管理員會確保存放區內容還原至正確的狀態。 如果您想要將變更傳播至存放區外的資源，請使用 Store 事件。 如需詳細資訊，請參閱[事件處理常式傳播模型外的變更](../modeling/event-handlers-propagate-changes-outside-the-model.md)。

 例如，假設您想要指定每當使用者（或您的程式碼）建立 ExampleDomainClass 類型的新專案時，就會在模型的另一個部分中建立另一個類型的其他元素。 您可以撰寫 AddRule，並將它與 ExampleDomainClass 建立關聯。 您會在規則中撰寫程式碼，以建立額外的元素。

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
> 規則的程式碼應該只變更存放區內元素的狀態;也就是說，此規則應該只會變更模型專案、關聯性、圖形、連接器、圖表或其屬性。 如果您想要將變更傳播至存放區外的資源，請定義存放區事件。 如需詳細資訊，請參閱[事件處理常式傳播模型外的變更](../modeling/event-handlers-propagate-changes-outside-the-model.md)。

### <a name="to-define-a-rule"></a>若要定義規則

1. 將規則定義為前面加上 `RuleOn` 屬性的類別。 屬性會將規則與您的其中一個網域類別、關聯性或圖表元素產生關聯。 此規則會套用到此類別的每個實例，這可能是抽象的。

2. 將規則新增至您的網域模型類別中 `GetCustomDomainModelTypes()` 所傳回的集合，藉此註冊。

3. 從其中一個抽象規則類別衍生規則類別，並撰寫執行方法的程式碼。

   下列各節會更詳細地描述這些步驟。

### <a name="to-define-a-rule-on-a-domain-class"></a>在網域類別上定義規則

- 在自訂程式碼檔案中，定義類別並在其前面加上 <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> 屬性：

    ```csharp
    [RuleOn(typeof(ExampleElement),
         // Usual value - but required, because it is not the default:
         FireTime = TimeToFire.TopLevelCommit)]
    class MyRule ...

    ```

- 第一個參數中的主體類型可以是網域類別、網域關聯性、圖形、連接器或圖表。 通常，您會將規則套用至網域類別和關聯性。

     @No__t_0 通常 `TopLevelCommit`。 這可確保只有在交易的所有主要變更完成之後，才會執行規則。 替代方案是內嵌的，這會在變更後立即執行規則;和 LocalCommit，它會在目前交易的結尾執行規則（這可能不是最外層的）。 您也可以設定規則的優先順序，以影響其在佇列中的順序，但這是不可靠的方法，無法達成您所需的結果。

- 您可以指定抽象類別做為主體類型。

- 此規則會套用至 subject 類別的所有實例。

- @No__t_0 的預設值是 TimeToFire. TopLevelCommit。 這會導致在認可最外層交易時執行規則。 替代方案是 TimeToFire。 這會導致規則在觸發事件之後立即執行。

### <a name="to-register-the-rule"></a>註冊規則

- 將您的規則類別加入網域模型中 `GetCustomDomainModelTypes` 所傳回的類型清單中：

    ```csharp
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

- 如果您不確定網域模型類別的名稱，請在檔案**Dsl\GeneratedCode\DomainModel.cs**中查看

- 請在 DSL 專案的自訂程式碼檔案中撰寫此程式碼。

### <a name="to-write-the-code-of-the-rule"></a>若要撰寫規則的程式碼

- 從下列其中一個基類衍生規則類別：

  | 基底類別 | 觸發程序 |
  |-|-|
  | <xref:Microsoft.VisualStudio.Modeling.AddRule> | 加入元素、連結或圖形。<br /><br /> 使用此專案來偵測新的關聯性，以及新的元素。 |
  | <xref:Microsoft.VisualStudio.Modeling.ChangeRule> | 定義域屬性值已變更。 方法引數會提供新舊值。<br /><br /> 針對圖形，當內建的 `AbsoluteBounds` 屬性變更時，如果圖形已移動，就會觸發此規則。<br /><br /> 在許多情況下，覆寫屬性處理常式中 `OnValueChanged` 或 `OnValueChanging` 會比較方便。 這些方法會在變更前後立即呼叫。 相反地，此規則通常會在交易結束時執行。 如需詳細資訊，請參閱[網域屬性值變更處理常式](../modeling/domain-property-value-change-handlers.md)。 **注意：** 建立或刪除連結時，不會觸發此規則。 相反地，請撰寫網域關聯性的 `AddRule` 和 `DeleteRule`。 |
  | <xref:Microsoft.VisualStudio.Modeling.DeletingRule> | 即將刪除元素或連結時觸發。 屬性 ModelElement. IsDeleting 是 true，直到交易結束為止。 |
  | <xref:Microsoft.VisualStudio.Modeling.DeleteRule> | 已刪除元素或連結時執行。 規則會在所有其他規則都執行之後執行，包括 DeletingRules。 ModelElement. IsDeleting 是 false，而 ModelElement. IsDeleted 為 true。 為了允許進行後續的復原，專案實際上不會從記憶體中移除，但會從 ElementDirectory 中移除。 |
  | <xref:Microsoft.VisualStudio.Modeling.MoveRule> | 元素會從某個存放區資料分割移到另一個。<br /><br /> （請注意，這與形狀的圖形位置無關）。 |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule> | 此規則僅適用于網域關聯性。 如果您明確地將模型元素指派給任一連結的結尾，就會觸發此專案。 |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule> | 當專案的連結順序在連結上使用 MoveBefore 或 MoveToIndex 方法變更時，就會觸發。 |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule> | 在建立交易時執行。 |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule> | 在即將認可交易時執行。 |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule> | 當交易即將回復時執行。 |

- 每個類別都有一個您覆寫的方法。 在類別中輸入 `override` 以探索它。 這個方法的參數會識別正在變更的元素。

  請注意下列關於規則的要點：

1. 交易中的一組變更可能會觸發許多規則。 通常，當最外層的交易認可時，就會執行規則。 它們會以未指定的循序執行。

2. 規則一律會在交易內執行。 因此，您不需要建立新的交易來進行變更。

3. 當交易回復時，或執行復原或重做作業時，不會執行規則。 這些作業會將存放區的所有內容重設為先前的狀態。 因此，如果您的規則變更了存放區外部任何專案的狀態，它可能不會與存放區內容保持 synchronism。 若要更新存放區外的狀態，最好是使用事件。 如需詳細資訊，請參閱[事件處理常式傳播模型外的變更](../modeling/event-handlers-propagate-changes-outside-the-model.md)。

4. 從檔案載入模型時，會執行某些規則。 若要判斷載入或儲存是否正在進行中，請使用 `store.TransactionManager.CurrentTransaction.IsSerializing`。

5. 如果規則的程式碼會建立更多規則引發程式，則會將它們新增到引發清單的結尾，並會在交易完成之前執行。 DeletedRules 會在所有其他規則之後執行。 一個規則可以在交易中執行多次，每個變更一次。

6. 若要在規則之間傳遞資訊，您可以將資訊儲存在 `TransactionContext` 中。 這只是在交易期間維護的字典。 當交易結束時，就會處置它。 每個規則中的事件引數都提供對它的存取。 請記住，規則不會以可預測的循序執行。

7. 考慮其他替代方案之後，請使用規則。 例如，如果您想要在值變更時更新屬性，請考慮使用計算的屬性。 如果您想要限制圖形的大小或位置，請使用 `BoundsRule`。 如果您想要回應屬性值的變更，請將 `OnValueChanged` 處理常式新增至屬性。 如需詳細資訊，請參閱[回應和傳播變更](../modeling/responding-to-and-propagating-changes.md)。

## <a name="example"></a>範例
 下列範例會在將網域關聯性具現化以連結兩個元素時，更新屬性。 此規則不只會在使用者于圖表上建立連結時觸發，而且程式碼也會建立連結。

 若要測試此範例，請使用 [工作流程] 方案範本建立 DSL，然後將下列程式碼插入 Dsl 專案的檔案中。 建立並執行方案，並在調試專案中開啟範例檔案。 在批註圖形與 flow 元素之間繪製批註連結。 批註中的文字會變更，以報告您已連接的最近元素。

 在實務上，您通常會針對每個 AddRule 撰寫 DeleteRule。

```csharp
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

- [事件處理常式傳播模型外的變更](../modeling/event-handlers-propagate-changes-outside-the-model.md)