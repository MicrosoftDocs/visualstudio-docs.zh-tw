---
title: 網域屬性值變更處理常式
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, overriding event handlers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9fcad439c7f0633f75d2a7364e2d0d3bfb142f89
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62994636"
---
# <a name="domain-property-value-change-handlers"></a>網域屬性值變更處理常式

在 Visual Studio 網域特定語言中，當網域屬性的值變更時，`OnValueChanging()`和`OnValueChanged()`網域屬性處理常式中叫用方法。 若要回應變更，您可以覆寫這些方法。

## <a name="override-the-property-handler-methods"></a>覆寫屬性處理常式方法

網域指定的語言的每個網域屬性會由巢狀於父網域類別內的類別來處理。 其名稱遵循下列格式*PropertyName*PropertyHandler。 您可以檢查這個檔案中的屬性處理常式類別**Dsl\Generated Code\DomainClasses.cs**。 在這個類別中，會在值變更前立即呼叫 `OnValueChanging()`，並在值變更後立即呼叫 `OnValueChanged()`。

例如，假設您有一個名為的網域類別`Comment`具有字串網域屬性，名為`Text`和名為整數屬性`TextLengthCount`。 會造成`TextLengthCount`一定要包含的長度`Text`字串，您可以在 Dsl 專案中的個別檔案中撰寫下列程式碼：

```csharp
// Domain Class "Comment":
public partial class Comment
{
  // Domain Property "Text":
  partial class TextPropertyHandler
  {
    protected override void OnValueChanging(CommentBase element, string oldValue, string newValue)
    {
      base.OnValueChanging(element, oldValue, newValue);

      // To update values outside the Store, write code here.

      // Let the transaction manager handle undo:
      Store store = element.Store;
      if (store.InUndoRedoOrRollback || store.InSerializationTransaction) return;

      // Update values in the Store:
      this.TextLengthCount = newValue.Length;
    }
  }
}
```

請注意有關屬性處理常式的下列重點：

- 當使用者變更網域屬性時，以及當程式碼指派不同的值給屬性時，都會呼叫屬性處理常式方法。

- 只有在值實際變更時，才會呼叫方法。 如果程式碼指派的值與目前的值相同，則不會叫用處理常式。

- 計算和自訂儲存網域屬性沒有 OnValueChanged 和 OnValueChanging 方法。

- 您無法使用變更處理常式來修改新值。 如果您要這樣做 (例如將值限制在特定範圍內)，請定義 `ChangeRule`。

- 您無法將變更處理常式加入至代表關聯性角色的屬性。 請改為定義關聯性類別上的 `AddRule` 和 `DeleteRule`。 建立或變更連結時，即會觸發這些規則。 如需詳細資訊，請參閱 <<c0> [ 規則傳播變更內模型](../modeling/rules-propagate-changes-within-the-model.md)。

### <a name="changes-in-and-out-of-the-store"></a>存放區內外的變更

屬性處理常式方法會在啟始變更的異動內呼叫。 因此，您可以在存放區中進行更多變更，而不需要開啟新異動。 您的變更可能會產生更多處理常式呼叫。

當異動正在復原、正在取消復原或已復原時，便不應該在存放區中進行變更，包括對模型項目、關聯性、圖形、連接線、圖表或其屬性所做的變更。

此外，從檔案載入模型時，通常不會更新值。

因此，對模型所做的變更應該受到類似如下的測試所保護：

```csharp
if (!store.InUndoRedoOrRollback && !store. InSerializationTransaction)
{
   this.TextLength = ...; // in-store changes
}
```

相對地，如果您的屬性處理常式將變更傳播到存放區外 (例如傳播至檔案、資料庫或非存放區變數)，則應該一律進行這些變更，以在使用者叫用復原或取消復原時，更新外部值。

### <a name="cancel-a-change"></a>取消變更

如果您要避免變更，可以復原目前的異動。 例如，您可能想確保某個屬性保持在特定範圍內。

```csharp
if (newValue > 10)
{
   store.TransactionManager.CurrentTransaction.Rollback();
   System.Windows.Forms.MessageBox.Show("Value must be less than 10");
}
```

### <a name="alternative-technique-calculated-properties"></a>替代方法：導出的屬性

先前的範例示範如何使用 OnValueChanged() 將某個網域屬性的值傳播至另一個網域屬性。 每個屬性都有自己的儲存值。

相反地，您可以考慮將衍生屬性定義為計算屬性。 在此情況下，屬性不會有自己的儲存值，因此每當需要屬性值時，都會評估定義的函式。 如需詳細資訊，請參閱 <<c0> [ 計算和儲存體的自訂屬性](../modeling/calculated-and-custom-storage-properties.md)。

而不是上述範例中，您可以設定**種類**欄位`TextLengthCount`要**導出**DSL 定義中。 您可以提供您自己**取得**此網域屬性的方法。 **取得**方法會傳回目前的長度`Text`字串。

不過，計算屬性的潛在缺點是每次使用值都會評估運算式，因此可能呈現效能問題。 此外，計算屬性沒有 OnValueChanging() 和 OnValueChanged()。

### <a name="alternative-technique-change-rules"></a>替代方法：變更規則

如果您定義了 ChangeRule，則會將其執行的交易，在其中變更屬性值的結尾。  如需詳細資訊，請參閱 <<c0> [ 規則傳播變更內模型](../modeling/rules-propagate-changes-within-the-model.md)。

如果在一個異動中進行數項變更，ChangeRule 會在所有變更完成時執行。 相較之下，則會執行 OnValue...方法執行時的一些變更尚未執行。 視您要達成的目標而定，ChangeRule 可能更適用。

您也可以使用 ChangeRule 調整屬性的新值，將指定的範圍內。

> [!WARNING]
> 如果某項規則變更了存放區內容，可能會觸發其他規則和屬性處理常式。 如果某項規則變更了已觸發的屬性，則會再次呼叫此規則。 您必須確定規則定義不會無限地造成觸發。

```csharp
using Microsoft.VisualStudio.Modeling;
...
// Change rule on the domain class Comment:
[RuleOn(typeof(Comment), FireTime = TimeToFire.TopLevelCommit)]
class MyCommentTrimRule : ChangeRule
{
  public override void
    ElementPropertyChanged(ElementPropertyChangedEventArgs e)
  {
    base.ElementPropertyChanged(e);
    Comment comment = e.ModelElement as Comment;

    if (comment.Text.StartsWith(" ") || comment.Text.EndsWith(" "))
      comment.Text = comment.Text.Trim();
    // If changed, rule will trigger again.
  }
}

// Register the rule:
public partial class MyDomainModel
{
 protected override Type[] GetCustomDomainModelTypes()
 { return new Type[] { typeof(MyCommentTrimRule) };
 }
}
```

## <a name="example"></a>範例

### <a name="description"></a>描述

下列範例覆寫網域屬性的屬性處理常式，並在 `ExampleElement` 網域類別的屬性變更時通知使用者。

### <a name="code"></a>程式碼

```csharp
using DslModeling = global::Microsoft.VisualStudio.Modeling;
using DslDesign = global::Microsoft.VisualStudio.Modeling.Design;

namespace msft.FieldChangeSample
{
  public partial class ExampleElement
  {
    internal sealed partial class NamePropertyHandler
    {
      protected override void OnValueChanged(ExampleElement element,
         string oldValue, string newValue)
      {
        if (!this.Store.InUndoRedoOrRollback)
        {
           // make in-store changes here...
        }
        // This part is called even in undo:
        System.Windows.Forms.MessageBox.Show("Value Has Changed");
        base.OnValueChanged(element, oldValue, newValue);
      }
    }
  }
}
```