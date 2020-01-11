---
title: 定義鎖定原則來建立唯讀區段 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: fa549c71-2bf6-4b08-b7b2-7756dd6f1dc8
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0d9887e3c7cf283bff453e458502400a7ade1a41
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849561"
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>定義鎖定原則來建立唯讀區段
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 視覺效果和模型化 SDK 的不變 API，可讓程式鎖定部分或所有的特定領域語言（DSL）模型，使其可以讀取但不會變更。 例如，可以使用此唯讀選項，讓使用者可以要求同事標注和檢查 DSL 模型，但不允許它們變更原始的。

 此外，身為 DSL 的作者，您可以定義*鎖定原則。* 鎖定原則會定義允許、不允許或強制的鎖定。 例如，當您發行 DSL 時，您可以鼓勵協力廠商開發人員使用新的命令來擴充它。 但是您也可以使用鎖定原則，防止它們改變模型指定部分的唯讀狀態。

> [!NOTE]
> 藉由使用反映，可以規避鎖定原則。 它為協力廠商開發人員提供清楚的界限，但不提供強大的安全性。

 如需詳細資訊和範例，請 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)][視覺效果和模型化 SDK](https://docs.microsoft.com/samples/browse/?redirectedfrom=MSDN-samples)網站。

## <a name="setting-and-getting-locks"></a>設定和取得鎖定
 您可以在存放區、資料分割或個別元素上設定鎖定。 例如，此語句會防止刪除模型專案，而且也會防止其屬性遭到變更：

```
using Microsoft.VisualStudio.Modeling.Immutability; ...
element.SetLocks(Locks.Delete | Locks.Property);
```

 其他鎖定值可以用來防止關聯性、專案建立、在資料分割之間移動，以及重新排序角色中的連結。

 鎖定適用于使用者動作和程式碼。 如果程式碼嘗試進行變更，則會擲回 `InvalidOperationException`。 復原或重做作業會忽略鎖定。

 您可以使用 `IsLocked(Locks)`，探索某個專案是否具有指定集合中的任何鎖定，而且您可以使用 `GetLocks()`取得專案的目前鎖定集。

 您可以在不使用交易的情況下設定鎖定。 鎖定資料庫不是存放區的一部分。 如果您設定鎖定以回應存放區中某個值的變更（例如在 OnValueChanged 中），您應該允許復原作業中的變更。

 這些方法是在 <xref:Microsoft.VisualStudio.Modeling.Immutability> 命名空間中定義的擴充方法。

### <a name="locks-on-partitions-and-stores"></a>磁碟分割和存放區的鎖定
 您也可以將鎖定套用至資料分割和存放區。 分割區上設定的鎖定會套用至資料分割中的所有元素。 因此，例如，下列語句會防止資料分割中的所有元素被刪除，而不論其本身的鎖定狀態。 儘管如此，其他的鎖定（例如 `Locks.Property`）仍然可以在個別元素上設定：

```
partition.SetLocks(Locks.Delete);
```

 在存放區上設定的鎖定會套用至其所有元素，而不論資料分割和元素上的鎖定設定。

### <a name="using-locks"></a>使用鎖定
 您可以使用鎖定來執行配置，如下列範例所示：

- 不允許變更所有專案和關聯性，但代表批註的專案和關係除外。 這可讓使用者在不變更模型的情況下加上附注。

- 不允許預設分割區中的變更，但允許圖表分割區中的變更。 使用者可以重新排列圖表，但是無法改變基礎模型。

- 不允許變更存放區，但在個別資料庫中註冊的使用者群組除外。 針對其他使用者，圖表和模型都是唯讀的。

- 如果圖表的布林值屬性設定為 true，則不允許對模型進行變更。 提供功能表命令來變更該屬性。 這有助於確保使用者不會意外地進行變更。

- 不允許新增和刪除特定類別的元素和關聯性，但允許屬性變更。 這會為使用者提供固定的表單，讓他們可以在其中填入屬性。

## <a name="lock-values"></a>鎖定值
 您可以在存放區、資料分割或個別的 ModelElement 上設定鎖定。 鎖定是 `Flags` 列舉：您可以使用 '&#124;' 結合其值。

- ModelElement 的鎖定一律包含其分割區的鎖定。

- 資料分割的鎖定一律包含存放區的鎖定。

  您無法在資料分割或儲存區上設定鎖定，同時停用個別元素的鎖定。

|{2&gt;值&lt;2}|如果 `IsLocked(Value)` 為 true 則為意義|
|-----------|------------------------------------------|
|None|無限制。|
|屬性|無法變更元素的網域屬性。 這不適用於關聯性中網域類別的角色所產生的屬性。|
|Add|無法在資料分割或存放區中建立新的元素和連結。<br /><br /> 不適用於 `ModelElement`。|
|Move|如果 `element.IsLocked(Move)` 為 true，或 `targetPartition.IsLocked(Move)` 為 true，則無法在分割區之間移動元素。|
|刪除|如果已在專案本身上設定此鎖定，或在任何要傳播刪除的專案上（例如內嵌專案和圖形），則無法刪除元素。<br /><br /> 您可以使用 `element.CanDelete()` 來探索是否可以刪除元素。|
|重新排序|無法變更 roleplayer 的連結順序。|
|RolePlayer|無法變更來源為此元素的連結集合。 例如，新的專案無法內嵌在此元素底下。 這不會影響此元素為目標的連結。<br /><br /> 如果這個元素是連結，其來源和目標不會受到影響。|
|全部|其他值的位 OR。|

## <a name="locking-policies"></a>鎖定原則
 身為 DSL 的作者，您可以定義*鎖定原則*。 鎖定原則會審核 SetLocks （）的作業，因此您可以防止設定特定鎖定或強制設定特定鎖定。 一般來說，您會使用鎖定原則來防止使用者或開發人員不小心 contravening 使用的 DSL，如同您可以 `private`宣告變數的方式一樣。

 您也可以使用鎖定原則，針對相依于元素類型的所有專案設定鎖定。 這是因為在第一次建立專案或從檔案還原序列化元素時，一律會呼叫 `SetLocks(Locks.None)`。

 不過，您無法使用原則來改變元素在其生命週期內的鎖定。 若要達成這個效果，您應該使用 `SetLocks()`的呼叫。

 若要定義鎖定原則，您必須：

- 建立會實作 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> 的類別。

- 將此類別新增至可透過 DSL DocData 取得的服務。

### <a name="to-define-a-locking-policy"></a>定義鎖定原則
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> 具有下列定義：

```
public interface ILockingPolicy
{
  Locks RefineLocks(ModelElement element, Locks proposedLocks);
  Locks RefineLocks(Partition partition, Locks proposedLocks);
  Locks RefineLocks(Store store, Locks proposedLocks);
}
```

 呼叫以在存放區、資料分割或 ModelElement 上進行 `SetLocks()` 時，會呼叫這些方法。 在每個方法中，會提供一組建議的鎖定。 您可以傳回建議的集合，也可以加入和減去鎖定。

 例如：

```
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Immutability;
namespace Company.YourDsl.DslPackage // Change
{
  public class MyLockingPolicy : ILockingPolicy
  {
    /// <summary>
    /// Moderate SetLocks(this ModelElement target, Locks locks)
    /// </summary>
    /// <param name="element">target</param>
    /// <param name="proposedLocks">locks</param>
    /// <returns></returns>
    public Locks RefineLocks(ModelElement element, Locks proposedLocks)
    {
      // In my policy, users can never delete an element,
      // and other developers cannot easily change that:
      return proposedLocks | Locks.Delete);
    }
    public Locks RefineLocks(Store store, Locks proposedLocks)
    {
      // Only one user can change this model:
      return Environment.UserName == "aUser"
           ? proposedLocks : Locks.All;
    }

```

 若要確保使用者永遠可以刪除元素，即使其他程式碼呼叫 `SetLocks(Lock.Delete):`

 `return proposedLocks & (Locks.All ^ Locks.Delete);`

 若不允許變更 MyClass 的每個元素的所有屬性：

 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`

### <a name="to-make-your-policy-available-as-a-service"></a>將您的原則當做服務提供
 在您的 `DslPackage` 專案中，加入包含類似下列範例之程式碼的新檔案：

```
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Immutability;
namespace Company.YourDsl.DslPackage // Change
{
  // Override the DocData GetService() for this DSL.
  internal partial class YourDslDocData // Change
  {
    /// <summary>
    /// Custom locking policy cache.
    /// </summary>
    private ILockingPolicy myLockingPolicy = null;

    /// <summary>
    /// Called when a service is requested.
    /// </summary>
    /// <param name="serviceType">Service requested</param>
    /// <returns>Service implementation</returns>
    public override object GetService(System.Type serviceType)
    {
      if (serviceType == typeof(SLockingPolicy)
       || serviceType == typeof(ILockingPolicy))
      {
        if (myLockingPolicy == null)
        {
          myLockingPolicy = new MyLockingPolicy();
        }
        return myLockingPolicy;
      }
      // Request is for some other service.
      return base.GetService(serviceType);
    }
}
```
