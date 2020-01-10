---
title: 如何：使用異動更新模型
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33d6c249845c72e25b7201bed5e640ff523c5d81
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594600"
---
# <a name="how-to-use-transactions-to-update-the-model"></a>如何：使用異動更新模型
交易可確保對存放區所做的變更會被視為群組。 群組的變更可以做為單一單位來認可或復原。

 每當程式碼修改、加入或刪除 Visual Studio 視覺效果和模型化 SDK 中存放區中的任何專案時，就必須在交易內執行此動作。 當變更發生時，必須有使用中的 <xref:Microsoft.VisualStudio.Modeling.Transaction> 實例與存放區相關聯。 這適用于所有模型元素、關聯性、圖形、圖表和其屬性。

 交易機制可協助您避免不一致的狀態。 如果在交易期間發生錯誤，則會復原所有變更。 如果使用者執行復原命令，則會將每個最近的交易視為單一步驟。 使用者無法復原最近變更的部分，除非您明確地將它們放在不同的交易中。

## <a name="opening-a-transaction"></a>開啟交易
 管理交易最方便的方法，是使用包含在 `try...catch` 語句中的 `using` 語句：

```csharp
Store store; ...
try
{
  using (Transaction transaction =
    store.TransactionManager.BeginTransaction("update model"))
    // Outermost transaction must always have a name.
  {
    // Make several changes in Store:
    Person p = new Person(store);
    p.FamilyTreeModel = familyTree;
    p.Name = "Edward VI";
    // end of changes to Store

    transaction.Commit(); // Don't forget this!
  } // transaction disposed here
}
catch (Exception ex)
{
  // If an exception occurs, the Store will be
  // rolled back to its previous state.
}
```

 如果發生變更時，無法執行最後 `Commit()` 的例外狀況，則會將存放區重設為先前的狀態。 這可協助您確保錯誤不會讓模型處於不一致的狀態。

 您可以在單一交易內進行任意數目的變更。 您可以在使用中交易內開啟新交易。 在包含的交易結束之前，必須認可或回復嵌套的交易。 如需詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A> 屬性的範例。

 若要讓變更成為永久的，您應該在處置交易之前，先將其 `Commit`。 如果發生未在交易內攔截到的例外狀況，存放區將會重設為其在變更之前的狀態。

## <a name="rolling-back-a-transaction"></a>復原交易
 若要確保存放區會在交易之前保留或還原為其狀態，您可以使用下列其中一個策略：

1. 引發不會在交易範圍內攔截到的例外狀況。

2. 明確回復交易：

    ```csharp
    this.Store.TransactionManager.CurrentTransaction.Rollback();
    ```

## <a name="transactions-do-not-affect-non-store-objects"></a>交易不會影響非存放區物件
 交易只會管理存放區的狀態。 它們無法復原對外部專案所做的部分變更，例如檔案、資料庫或您在 DSL 定義外部以一般類型宣告的物件。

 如果例外狀況可能會使這項變更與存放區不一致，您應該在例外狀況處理常式中處理這種可能性。 若要確保外部資源與存放區物件保持同步，其中一種方法是使用事件處理常式，將每個外部物件分別儲存至同一個存放區元素。 如需詳細資訊，請參閱[事件處理常式傳播模型外的變更](../modeling/event-handlers-propagate-changes-outside-the-model.md)。

## <a name="rules-fire-at-the-end-of-a-transaction"></a>在交易結束時引發規則
 在交易結束時，處置交易之前，會引發附加至存放區中元素的規則。 每個規則都是套用至已變更之模型專案的方法。 例如，在模型專案已變更時，會更新圖形狀態的「修正」規則，並在建立模型專案時建立圖形。 沒有指定的引發順序。 規則所做的變更可能會引發另一個規則。

 您可以定義自己的規則。 如需規則的詳細資訊，請參閱[回應和傳播變更](../modeling/responding-to-and-propagating-changes.md)。

 在復原、重做或 rollback 命令之後，不會引發規則。

## <a name="transaction-context"></a>交易內容
 每筆交易都有一個字典，您可以在其中儲存所需的任何資訊：

 `store.TransactionManager`

 `.CurrentTransaction.TopLevelTransaction`

 `.Context.Add(aKey, aValue);`

 這在規則之間傳送資訊時特別有用。

## <a name="transaction-state"></a>交易狀態
 在某些情況下，如果是藉由復原或重做交易所造成的變更，您就必須避免傳播變更。 例如，如果您撰寫的屬性值處理常式可更新存放區中的另一個值，則可能會發生這種情況。 因為「復原」作業會將存放區中的所有值重設為先前的狀態，所以不需要計算更新的值。 使用此程式碼：

```csharp
if (!this.Store.InUndoRedoOrRollback) {...}
```

 當首次從檔案載入存放區時，規則就會引發。 若要避免回應這些變更，請使用：

```csharp
if (!this.Store.InSerializationTransaction) {...}
```
