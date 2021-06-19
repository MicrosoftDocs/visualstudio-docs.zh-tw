---
title: 如何：使用異動更新模型
description: 瞭解交易可確保對存放區所做的變更會視為群組，以及如何使用交易來更新模型。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e91e569573076d1614a9fa946b67f3bda01e6fba
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390538"
---
# <a name="how-to-use-transactions-to-update-the-model"></a>如何：使用異動更新模型
交易可確保對存放區所做的變更會視為群組。 您可以使用單一單位來認可或回復已分組的變更。

 每當您的程式碼在 Visual Studio 視覺效果和模型 SDK 中修改、新增或刪除存放區中的任何專案時，都必須在交易內進行。 <xref:Microsoft.VisualStudio.Modeling.Transaction>發生變更時，必須有與存放區相關聯的使用中實例。 這適用于所有模型專案、關聯性、圖形、圖表和其屬性。

 交易機制可協助您避免不一致的狀態。 如果在交易期間發生錯誤，則會回復所有變更。 如果使用者執行復原命令，則會將每個最近的交易視為單一步驟。 除非您明確地將專案放在不同的交易中，否則使用者無法復原最近變更的部分。

## <a name="opening-a-transaction"></a>開啟交易
 管理交易最方便的方法，就是 `using` 在語句中包含語句 `try...catch` ：

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

 如果防止在 `Commit()` 變更期間發生最後的例外狀況，則會將存放區重設為先前的狀態。 這可協助您確保錯誤不會讓模型處於不一致的狀態。

 您可以在一個交易內進行任何數量的變更。 您可以在使用中交易內開啟新交易。 嵌套交易必須在包含的交易結束之前認可或回復。 如需詳細資訊，請參閱屬性的範例 <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A> 。

 若要永久變更您的變更，您應該在 `Commit` 交易處置之前先進行交易。 如果發生不在交易內的例外狀況，則存放區會在變更前重設為其狀態。

## <a name="rolling-back-a-transaction"></a>復原交易
 若要確保存放區在交易之前保持不變或還原為其狀態，您可以使用下列其中一種策略：

1. 引發在交易範圍內未攔截到的例外狀況。

2. 明確回復交易：

    ```csharp
    this.Store.TransactionManager.CurrentTransaction.Rollback();
    ```

## <a name="transactions-do-not-affect-non-store-objects"></a>交易不會影響非存放區物件
 交易只會管理存放區的狀態。 它們無法復原對外部專案所做的部分變更，例如，在 DSL 定義以外使用一般類型宣告的檔案、資料庫或物件。

 如果例外狀況可能使這類變更與存放區不一致，您應該在例外狀況處理常式中處理這種可能性。 確定外部資源與存放區物件保持同步的其中一種方式，是使用事件處理常式，將每個外部物件結合到內建元素。 如需詳細資訊，請參閱 [事件處理常式傳播模型外的變更](../modeling/event-handlers-propagate-changes-outside-the-model.md)。

## <a name="rules-fire-at-the-end-of-a-transaction"></a>在交易結束時引發規則
 在交易結束時，在處置交易之前，會引發附加至存放區中元素的規則。 每個規則都是套用至已變更之模型專案的方法。 例如，有「修正」規則，可在模型專案變更時，更新圖形的狀態，並在建立模型專案時建立圖形。 沒有指定的引發順序。 規則所做的變更可能會引發另一項規則。

 您可以定義自己的規則。 如需規則的詳細資訊，請參閱 [回應和傳播變更](../modeling/responding-to-and-propagating-changes.md)。

 在復原、重做或復原命令之後，不會引發規則。

## <a name="transaction-context"></a>交易內容
 每個交易都有一個字典，您可以在其中儲存任何您想要的資訊：

 `store.TransactionManager`

 `.CurrentTransaction.TopLevelTransaction`

 `.Context.Add(aKey, aValue);`

 這特別適用于在規則之間傳輸資訊。

## <a name="transaction-state"></a>交易狀態
 在某些情況下，如果變更是由復原或重做交易所造成，則您需要避免傳播變更。 例如，如果您撰寫的屬性值處理常式可更新存放區中的其他值，就會發生這種情況。 因為復原作業會將存放區中的所有值重設為先前的狀態，所以不需要計算更新的值。 使用此程式碼：

```csharp
if (!this.Store.InUndoRedoOrRollback) {...}
```

 從檔案開始載入存放區時，可以引發規則。 若要避免回應這些變更，請使用：

```csharp
if (!this.Store.InSerializationTransaction) {...}
```
