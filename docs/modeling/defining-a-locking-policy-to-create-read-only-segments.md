---
title: 定義鎖定原則來建立唯讀區段
description: 瞭解如何為程式定義原則，以鎖定部分或所有特定領域語言 (DSL) 模型，讓它可以讀取但不能變更。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6bb8e05ffc030716f32ab7e79233ca9e02ef2e11
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385782"
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>定義鎖定原則來建立唯讀區段
Visual Studio 視覺效果和模型 SDK 的永久性 API 可讓程式鎖定部分或所有特定領域語言 (DSL) 模型，讓它可以讀取但不會變更。 例如，您可以使用這個唯讀選項，讓使用者可以要求同事標注和審核 DSL 模型，但不允許他們變更原始模型。

 此外，作為 DSL 的作者，您可以定義 *鎖定原則。* 鎖定原則會定義允許、不允許或強制的鎖定。 例如，當您發佈 DSL 時，可以鼓勵協力廠商開發人員以新的命令延伸。 但是，您也可以使用鎖定原則來防止它們變更模型指定部分的唯讀狀態。

> [!NOTE]
> 您可以使用反映來規避鎖定原則。 它為協力廠商開發人員提供明確的界限，但不提供強大的安全性。

 如需詳細資訊和範例，請參閱 Visual Studio [視覺效果和模型 SDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db) 網站。

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="setting-and-getting-locks"></a>設定和取得鎖定
 您可以在存放區、分割區或個別元素上設定鎖定。 例如，此語句可防止刪除模型專案，也會防止變更其屬性：

```csharp
using Microsoft.VisualStudio.Modeling.Immutability; ...
element.SetLocks(Locks.Delete | Locks.Property);
```

 您可以使用其他鎖定值來防止關聯性、元素建立、資料分割之間的移動，以及重新排序角色中的連結。

 鎖定適用于使用者動作和程式碼。 如果程式碼嘗試進行變更， `InvalidOperationException` 將會擲回。 復原或重做作業會忽略鎖定。

 您可以使用來探索某個專案是否有指定之集合中的任何鎖定 `IsLocked(Locks)` ，而且您可以使用來取得專案目前的鎖定集 `GetLocks()` 。

 您可以設定不使用交易的鎖定。 鎖定資料庫不是存放區的一部分。 如果您設定鎖定以回應存放區中的值變更，例如在 OnValueChanged 中，您應該允許屬於復原作業一部分的變更。

 這些方法是在命名空間中定義的擴充方法 <xref:Microsoft.VisualStudio.Modeling.Immutability> 。

### <a name="locks-on-partitions-and-stores"></a>分割區和存放區的鎖定
 鎖定也可以套用至分割區和存放區。 在分割區上設定的鎖定會套用至資料分割中的所有元素。 因此，下列語句將會防止刪除分割區中的所有元素，而不考慮它們本身的鎖定狀態。 不過，其他鎖定（例如） `Locks.Property` 仍然可以在個別元素上設定：

```csharp
partition.SetLocks(Locks.Delete);
```

 在存放區上設定的鎖定會套用至其所有專案，不論資料分割上的鎖定設定和元素。

### <a name="using-locks"></a>使用鎖定
 您可以使用鎖定來執行配置，例如下列範例：

- 除了表示批註的專案和關聯性之外，不允許對所有元素和關聯性進行變更。 這可讓使用者在不變更模型的情況下對其加上批註。

- 不允許變更預設分割區，但允許圖表分割區中的變更。 使用者可以重新排列圖表，但無法改變基礎模型。

- 除了在個別資料庫中註冊的使用者群組以外，不允許變更存放區。 若為其他使用者，則圖表和模型是唯讀的。

- 如果圖表的 [布林值] 屬性設定為 true，則不允許對模型進行變更。 提供功能表命令來變更該屬性。 這有助於確保使用者不會不小心進行變更。

- 不允許新增和刪除特定類別的元素和關聯性，但允許屬性變更。 這會為使用者提供固定的表單，讓他們可以填滿屬性。

## <a name="lock-values"></a>鎖定值
 您可以在存放區、資料分割或個別的 ModelElement 上設定鎖定。 鎖定是 `Flags` 列舉：您可以使用 ' &#124; ' 將其值結合。

- ModelElement 的鎖定一律會包含其分割區的鎖定。

- 分割區的鎖定一律會包含存放區的鎖定。

  您無法在分割區或存放區上設定鎖定，同時停用個別元素的鎖定。

|值|表示 if `IsLocked(Value)` 為 true|
|-|-|
|無|無限制。|
|屬性|無法變更元素的網域屬性。 這並不適用于關聯性中網域類別角色所產生的屬性。|
|加|無法在分割區或存放區中建立新的元素和連結。<br /><br /> 不適用於 `ModelElement` 。|
|移動|如果 `element.IsLocked(Move)` 是 true，或是如果為 true，則無法在分割區之間移動元素 `targetPartition.IsLocked(Move)` 。|
|刪除|如果這個鎖定是在元素本身上設定，或在刪除所要傳播的任何專案（例如內嵌的元素和圖形）上設定，則無法刪除元素。<br /><br /> 您可以使用 `element.CanDelete()` 來探索是否可刪除元素。|
|排序|無法變更 roleplayer 的連結順序。|
|RolePlayer|無法變更以此專案為來源的連結集合。 例如，新的元素不能內嵌在此專案底下。 這不會影響此元素為目標的連結。<br /><br /> 如果這個元素是連結，則不會影響其來源和目標。|
|全部|其他值的位 OR。|

## <a name="locking-policies"></a>鎖定原則
 作為 DSL 的作者，您可以定義 *鎖定原則*。 鎖定原則會審核 SetLocks () 的作業，讓您可以防止設定特定鎖定或強制設定特定鎖定。 一般而言，您會使用鎖定原則來防止使用者或開發人員不慎 contravening 預期的 DSL 使用方式，就像您可以宣告變數一樣 `private` 。

 您也可以使用鎖定原則來設定相依于專案類型之所有專案的鎖定。 這是因為 `SetLocks(Locks.None)` 當第一次從檔案建立或還原序列化專案時，一律會呼叫。

 不過，您無法使用原則來改變其生命週期內的鎖定。 若要達成這個效果，您應該使用的呼叫 `SetLocks()` 。

 若要定義鎖定原則，您必須：

- 建立會實作 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> 的類別。

- 將這個類別新增至可透過 DSL DocData 使用的服務。

### <a name="to-define-a-locking-policy"></a>若要定義鎖定原則
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> 具有下列定義：

```csharp
public interface ILockingPolicy
{
  Locks RefineLocks(ModelElement element, Locks proposedLocks);
  Locks RefineLocks(Partition partition, Locks proposedLocks);
  Locks RefineLocks(Store store, Locks proposedLocks);
}
```

 當對 `SetLocks()` 存放區、分割區或 ModelElement 進行呼叫時，會呼叫這些方法。 在每個方法中，您都會提供一組建議的鎖定。 您可以傳回建議的集合，也可以加入和減少鎖定。

 例如：

```csharp
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

 若要確定使用者一律可以刪除元素，即使其他程式碼呼叫 `SetLocks(Lock.Delete):`

 `return proposedLocks & (Locks.All ^ Locks.Delete);`

 若不允許在 MyClass 的每個元素的所有屬性中變更：

 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`

### <a name="to-make-your-policy-available-as-a-service"></a>讓您的原則可作為服務使用
 在您的 `DslPackage` 專案中加入新檔案，其中包含類似下列範例的程式碼：

```csharp
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
