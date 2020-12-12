---
title: 規則傳播模型內的變更
description: 瞭解如何建立儲存規則，以在視覺效果和模型 SDK (VMSDK) 中，將變更傳播到另一個元素。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c4ff2273c8c71582c3ef634eeb398b12e29401d0
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363948"
---
# <a name="rules-propagate-changes-within-the-model"></a>規則傳播模型內的變更
您可以建立存放區規則，以視覺效果和模型 SDK (VMSDK) ，將變更傳播到另一個元素。 當存放區中的任何專案發生變更時，系統會排定要執行的規則，通常是在認可最外層的交易時執行。 不同類型的事件有不同類型的規則，例如新增專案或刪除專案。 您可以將規則附加至特定類型的元素、圖形或圖表。 許多內建功能都是由規則所定義：例如，當模型變更時，規則會確保圖表會更新。 您可以新增自己的規則來自訂特定領域語言。

 存放區規則特別適用于傳播儲存區內的變更，也就是模型專案、關聯性、圖形或連接器的變更，以及其定義域屬性。 當使用者叫用復原或重做命令時，不會執行規則。 相反地，交易管理員會確保存放區內容會還原為正確的狀態。 如果您想要將變更傳播到存放區以外的資源，請使用存放區事件。 如需詳細資訊，請參閱 [事件處理常式傳播模型外的變更](../modeling/event-handlers-propagate-changes-outside-the-model.md)。

 例如，假設您想要指定每當使用者 (或您的程式碼) 建立類型 ExampleDomainClass 的新專案時，另一個類型的其他專案會在模型的另一個部分中建立。 您可以撰寫 AddRule，並將它與 ExampleDomainClass 建立關聯。 您會在規則中撰寫程式碼，以建立額外的元素。

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
> 規則的程式碼應該只變更存放區內的元素狀態。也就是說，此規則只會變更模型專案、關聯性、圖形、連接器、圖表或其屬性。 如果您想要將變更傳播到存放區以外的資源，請定義存放區事件。 如需詳細資訊，請參閱 [事件處理常式傳播模型外的變更](../modeling/event-handlers-propagate-changes-outside-the-model.md)。

### <a name="to-define-a-rule"></a>若要定義規則

1. 將規則定義為首碼為屬性的類別 `RuleOn` 。 屬性會將規則與您的其中一個網域類別、關聯性或圖表元素產生關聯。 此規則將會套用至這個類別的每個實例，這可能是抽象的。

2. 將規則加入至 `GetCustomDomainModelTypes()` 您的網域模型類別中所傳回的集合，以註冊規則。

3. 從其中一個抽象規則類別衍生規則類別，然後撰寫執行方法的程式碼。

   下列各節會更詳細地說明這些步驟。

### <a name="to-define-a-rule-on-a-domain-class"></a>若要定義網域類別的規則

- 在自訂程式碼檔案中，定義一個類別，並在其前面加上 <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> 屬性：

    ```csharp
    [RuleOn(typeof(ExampleElement),
         // Usual value - but required, because it is not the default:
         FireTime = TimeToFire.TopLevelCommit)]
    class MyRule ...

    ```

- 第一個參數中的主體類型可以是網域類別、網域關聯性、圖形、連接器或圖表。 通常，您會將規則套用至網域類別和關聯性。

     `FireTime`通常是 `TopLevelCommit` 。 這可確保只有在交易的所有主要變更都已完成之後，才會執行規則。 替代專案是內嵌的，這會在變更後立即執行此規則;和 LocalCommit，它會在目前交易的結尾執行規則 (這可能不是最外層的) 。 您也可以設定規則的優先順序，以影響其在佇列中的順序，但這是達到您所需結果的不可靠方法。

- 您可以將抽象類別指定為主體類型。

- 此規則會套用至主體類別的所有實例。

- 的預設值 `FireTime` 為 TimeToFire. TopLevelCommit。 這會導致在認可最外層交易時執行規則。 替代方法是 TimeToFire。 這會導致規則在觸發事件之後立即執行。

### <a name="to-register-the-rule"></a>註冊規則

- 將您的規則類別新增至 `GetCustomDomainModelTypes` 您的網域模型中所傳回的類型清單：

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

- 如果您不確定網域模型類別的名稱，請在檔案內查看 **Dsl\GeneratedCode\DomainModel.cs**

- 在 DSL 專案的自訂程式碼檔案中撰寫此程式碼。

### <a name="to-write-the-code-of-the-rule"></a>撰寫規則的程式碼

- 從下列其中一個基類衍生規則類別：

  | 基底類別 | 觸發程序 |
  |-|-|
  | <xref:Microsoft.VisualStudio.Modeling.AddRule> | 加入元素、連結或圖形。<br /><br /> 使用此項來偵測新的關聯性，以及新的元素。 |
  | <xref:Microsoft.VisualStudio.Modeling.ChangeRule> | 定義域屬性值已變更。 方法引數會提供舊值和新值。<br /><br /> 若為圖形，當內建 `AbsoluteBounds` 屬性變更時，如果圖形已移動，就會觸發此規則。<br /><br /> 在許多情況下，覆寫 `OnValueChanged` 或 `OnValueChanging` 在屬性處理常式中較為方便。 這些方法會在變更前後立即呼叫。 相反地，規則通常會在交易結束時執行。 如需詳細資訊，請參閱 [網域屬性值變更處理常式](../modeling/domain-property-value-change-handlers.md)。 **注意：**  建立或刪除連結時，不會觸發此規則。 相反地，請 `AddRule` `DeleteRule` 針對網域關聯性撰寫和。 |
  | <xref:Microsoft.VisualStudio.Modeling.DeletingRule> | 即將刪除元素或連結時觸發。 在交易結束之前，屬性 ModelElement 是 true。 |
  | <xref:Microsoft.VisualStudio.Modeling.DeleteRule> | 當元素或連結已刪除時執行。 規則會在執行所有其他規則之後執行，包括 DeletingRules。 ModelElement. IsDeleting 為 false，ModelElement. IsDeleted 為 true。 若要允許後續的復原，元素實際上不會從記憶體中移除，但會從 ElementDirectory 中移除。 |
  | <xref:Microsoft.VisualStudio.Modeling.MoveRule> | 專案會從一個存放區分割區移至另一個。<br /><br />  (請注意，這與圖形的圖形位置無關。 )  |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule> | 此規則只適用于網域關聯性。 如果您明確地將模型專案指派給連結的任一端，則會觸發此程式。 |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule> | 當使用連結上的 MoveBefore 或 MoveToIndex 方法變更元素的連結順序變更時，就會觸發。 |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule> | 在建立交易時執行。 |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule> | 當交易即將認可時執行。 |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule> | 當交易即將回復時執行。 |

- 每個類別都有您覆寫的方法。 輸入 `override` 您的類別以探索它。 這個方法的參數會識別正在變更的元素。

  請注意下列有關規則的要點：

1. 交易中的一組變更可能會觸發許多規則。 通常，在認可最外層的交易時，會執行規則。 它們是以未指定的循序執行。

2. 規則一律會在交易內執行。 因此，您不需要建立新的交易來進行變更。

3. 當交易回復時，或執行復原或重做作業時，不會執行規則。 這些作業會將存放區的所有內容重設為先前的狀態。 因此，如果您的規則變更了存放區以外的任何內容狀態，它可能不會與存放區內容保持 synchronism。 若要更新存放區以外的狀態，最好是使用事件。 如需詳細資訊，請參閱 [事件處理常式傳播模型外的變更](../modeling/event-handlers-propagate-changes-outside-the-model.md)。

4. 從檔案載入模型時，會執行某些規則。 若要判斷載入或儲存是否正在進行中，請使用 `store.TransactionManager.CurrentTransaction.IsSerializing` 。

5. 如果規則的程式碼建立了更多規則引發程式，則會將它們新增至引發清單的結尾，並在交易完成之前執行。 DeletedRules 會在所有其他規則之後執行。 一個規則可以在交易中執行許多次，每次變更一次。

6. 若要在規則之間傳遞資訊，您可以將資訊儲存在中 `TransactionContext` 。 這只是在交易期間維護的字典。 它會在交易結束時處置。 每個規則中的事件引數都提供其存取權。 請記住，規則不會以可預測的循序執行。

7. 考慮其他替代方案之後，請使用規則。 例如，如果您想要在值變更時更新屬性，請考慮使用計算屬性。 如果您想要限制圖形的大小或位置，請使用 `BoundsRule` 。 如果您想要回應屬性值的變更，請將 `OnValueChanged` 處理常式加入至屬性。 如需詳細資訊，請參閱 [回應及傳播變更](../modeling/responding-to-and-propagating-changes.md)。

## <a name="example"></a>範例
 下列範例會在具現化網域關聯性以連結兩個元素時，更新屬性。 當使用者在圖表上建立連結時，以及程式碼建立連結時，將不會觸發此規則。

 若要測試此範例，請使用 [工作流程] 解決方案範本建立 DSL，然後將下列程式碼插入 Dsl 專案的檔案中。 建立並執行方案，然後在調試專案中開啟範例檔案。 在批註圖形和 flow 元素之間繪製批註連結。 批註中的文字會變更，以針對您已與其連接的最新元素進行報告。

 在實務上，您通常會為每個 AddRule 撰寫 DeleteRule。

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