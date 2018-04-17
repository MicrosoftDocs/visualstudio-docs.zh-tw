---
title: 如何： 使用異動來更新模型 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: ecd9645bfb202d83bf672d03d3c6903a889677f9
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/10/2018
---
# <a name="how-to-use-transactions-to-update-the-model"></a>如何：使用異動更新模型
交易確認至存放區所做的變更會被視為一個群組。 變更群組可加以認可或回復，當做單一單位。  
  
 每當您的程式碼可修改、 新增，或刪除的存放區中的任何項目[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Visualization and Modeling SDK，它必須在交易內執行。 必須有使用中的執行個體<xref:Microsoft.VisualStudio.Modeling.Transaction>時變更相關聯的存放區。 這適用於所有模型項目、 關聯性、 圖形、 圖表和其屬性。  
  
 交易機制可協助您避免不一致的狀態。 如果在交易期間發生錯誤，會回復所有變更。 如果使用者執行復原命令時，每個最近的交易將會被視為單一步驟。 除非您明確地放在個別交易中，使用者無法復原最近的變更的部分。  
  
## <a name="opening-a-transaction"></a>開啟交易  
 管理交易的最方便的方法是使用`using`陳述式括住`try...catch`陳述式：  
  
```  
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
  
 如果例外狀況會防止最終`Commit()`發生變更時，將會重設為先前的狀態存放區。 這可協助您確認該錯誤不會讓模型處於不一致的狀態。  
  
 您可以將任意數目的一筆交易內的變更。 您可以開啟使用中交易內的新交易。 巢狀的交易必須認可或回復包含交易結束之前。 如需詳細資訊，請參閱範例的<xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A>屬性。  
  
 若要進行永久變更，您應該`Commit`交易之前加以處置。 如果未攔截到在交易內發生的例外狀況，存放區將會重設為所做的變更之前的狀態。  
  
## <a name="rolling-back-a-transaction"></a>復原交易  
 若要確定會保留在儲存區，或還原為其交易之前的狀態，您可以使用其中一個這些策略：  
  
1.  引發交易的範圍內未攔截到例外狀況。  
  
2.  回復明確交易：  
  
    ```  
    this.Store.TransactionManager.CurrentTransaction.Rollback();  
    ```  
  
## <a name="transactions-do-not-affect-non-store-objects"></a>交易不會影響非存放區物件  
 交易只能管理存放區的狀態。 它們無法復原至外部的項目，例如檔案、 資料庫或 DSL 定義之外的一般型別與宣告的物件所做的部分變更。  
  
 如果例外狀況可能會保留這類變更與存放區不一致，您應該處理該例外狀況處理常式中的可能性。 確認外部資源保持同步的存放區物件的一個方法是在存放區項目結合每個外部物件，使用事件處理常式。 如需詳細資訊，請參閱[事件處理常式傳播變更外部模型](../modeling/event-handlers-propagate-changes-outside-the-model.md)。  
  
## <a name="rules-fire-at-the-end-of-a-transaction"></a>規則引發交易的結尾  
 在交易結束時，交易已處置之前，不會引發的規則附加到存放區中的項目。 每個規則會套用至模型項目已變更的方法。 比方說，有時其模型項目已變更，更新狀態圖形的 「 修復 」 規則，並將模型項目建立時，這會建立圖形。 沒有任何指定的引發順序。 由規則所做的變更可能會引發另一項規則。  
  
 您可以定義您自己的規則。 如需規則的詳細資訊，請參閱[回應和傳播變更](../modeling/responding-to-and-propagating-changes.md)。  
  
 規則不會復原、 重做或復原命令之後引發。  
  
## <a name="transaction-context"></a>交易內容  
 每筆交易都有的字典，您可以在其中儲存有關的資訊：  
  
 `store.TransactionManager`  
  
 `.CurrentTransaction.TopLevelTransaction`  
  
 `.Context.Add(aKey, aValue);`  
  
 這是特別適用於規則之間傳輸資訊。  
  
## <a name="transaction-state"></a>交易狀態  
 如果變更因為復原或取消復原交易，在某些情況下，您必須避免傳播變更。 此情形，例如，如果您撰寫可以更新存放區中的另一個值的屬性值處理常式。 復原作業會將存放區中的所有值重都設成其先前狀態，因為它不需要計算更新的值。 使用此程式碼：  
  
```  
if (!this.Store.InUndoRedoOrRollback) {...}  
```  
  
 一開始從檔案載入存放區時，可以引發的規則。 若要避免回應這些變更，請使用：  
  
```  
if (!this.Store.InSerializationTransaction) {...}  
  
```