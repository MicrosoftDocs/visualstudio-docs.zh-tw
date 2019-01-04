---
title: HOW TO：使用異動更新模型
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: f42c7a384b4f46864e4c79d386cd82ca39949a61
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53938338"
---
# <a name="how-to-use-transactions-to-update-the-model"></a>HOW TO：使用異動更新模型
交易確認至存放區所做的變更會被視為一個群組。 分組的變更可以認可或回復，當做單一單位。

 每當您的程式碼會修改、 新增，或刪除 Visual Studio Visualization and Modeling SDK 中的存放區中的任何項目，它必須在交易內進行。 必須有使用中的執行個體<xref:Microsoft.VisualStudio.Modeling.Transaction>變更發生時，以存放區相關聯。 這適用於所有模型項目、 關聯性、 圖形、 圖表和其屬性。

 交易的機制，可協助您避免不一致的狀態。 如果在交易期間發生錯誤，會回復所有變更。 如果使用者執行復原 命令，每個新的交易將會被視為單一步驟。 使用者無法復原最近的變更，部份，除非您將它們明確放在個別交易中。

## <a name="opening-a-transaction"></a>開啟交易
 管理交易的最方便的方法是使用`using`陳述式括住`try...catch`陳述式：

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

 如果例外狀況，以防止最終`Commit()`，就會發生在變更時，將會重設為先前的狀態。 這可協助您確保錯誤不會在不一致的狀態讓模型。

 您可以讓任意數目的一筆交易內的變更。 您可以開啟新的交易內使用中交易。 巢狀的交易必須認可或回復包含交易結束之前。 如需詳細資訊，請參閱範例<xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A>屬性。

 若要進行永久變更，您應該`Commit`交易之前處置它。 如果發生例外狀況不會攔截在交易內，所做的變更之前的狀態將會重設的存放區。

## <a name="rolling-back-a-transaction"></a>復原交易
 若要確保會保留在存放區，或會還原為其交易前的狀態，您可以使用其中一個策略：

1.  引發交易的範圍內沒有攔截到例外狀況。

2.  回復明確交易：

    ```csharp
    this.Store.TransactionManager.CurrentTransaction.Rollback();
    ```

## <a name="transactions-do-not-affect-non-store-objects"></a>交易不會影響非存放區物件
 交易只能管理存放區的狀態。 它們無法復原部分外部的項目，例如檔案、 資料庫或您已經使用一般類型的 DSL 定義之外宣告的物件所做的變更。

 如果例外狀況，可能會導致這類變更不一致的存放區，您應該處理這個例外狀況處理常式中的可能性。 請確定外部資源保持同步的存放區物件的方法之一是在存放區項目結合每個外部物件，使用事件處理常式。 如需詳細資訊，請參閱 <<c0> [ 事件處理常式傳播變更外部模型](../modeling/event-handlers-propagate-changes-outside-the-model.md)。

## <a name="rules-fire-at-the-end-of-a-transaction"></a>規則引發交易的結尾
 在交易結束時，會處置交易之前，就會引發附加至項目存放區中的規則。 每個規則是套用至模型項目已變更的方法。 比方說，有其模型項目已變更時，更新狀態的圖形的 「 修正 」 規則，並建立模型項目時，這會建立一個圖形。 沒有任何指定的引發順序。 規則所做的變更可以引發另一項規則。

 您可以定義自己的規則。 如需規則的詳細資訊，請參閱 <<c0> [ 回應及傳播變更](../modeling/responding-to-and-propagating-changes.md)。

 規則不會復原、 重做或復原命令之後引發。

## <a name="transaction-context"></a>交易內容
 每筆交易都可以在其中儲存您想要的任何資訊的字典：

 `store.TransactionManager`

 `.CurrentTransaction.TopLevelTransaction`

 `.Context.Add(aKey, aValue);`

 這是特別適用於傳輸規則之間的資訊。

## <a name="transaction-state"></a>交易狀態
 在某些情況下，您必須避免傳播變更，如果變更因為復原或重做交易。 這種情形，例如，如果您要撰寫可以更新存放區中的另一個值的屬性值處理常式。 復原作業會將存放區中的所有值重都設成其先前狀態，因為它不需要計算更新的值。 使用下列程式碼：

```csharp
if (!this.Store.InUndoRedoOrRollback) {...}
```

 一開始從檔案載入存放區時，可以引發的規則。 若要避免回應這些變更，請使用：

```csharp
if (!this.Store.InSerializationTransaction) {...}
```