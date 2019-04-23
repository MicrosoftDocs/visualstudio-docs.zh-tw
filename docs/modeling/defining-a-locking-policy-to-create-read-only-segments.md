---
title: 定義鎖定原則來建立唯讀區段
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b38f81b3269d0a456c077023d23861a55ac06a4c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60117185"
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>定義鎖定原則來建立唯讀區段
Visual Studio Visualization and Modeling SDK 的不變性 API 可讓程式鎖定的特定領域語言 (DSL) 模型的部分或全部，如此可以讀取但不是會變更。 無法使用這個唯讀選項，例如，讓使用者可以要求加上註解，並檢閱 DSL 模型的同事，但可以變更原始禁止。

 此外，身為作者的 DSL，您可以定義*鎖定原則。* 鎖定的原則會定義哪些鎖定是允許、 不允許，或強制。 比方說，當您發行 DSL，您可以建議第三方開發人員擴充新的命令。 不過，您也可以使用 鎖定原則，防止它們改變模型的指定組件的唯讀狀態。

> [!NOTE]
>  可以使用反映來規避鎖定原則。 它適用於第三方開發人員，提供清楚的界限，但並不會提供更強的安全性。

 更多的資訊和範例可在 Visual Studio [Visualization and Modeling SDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)網站。

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="setting-and-getting-locks"></a>設定和取得鎖定
 您可以在存放區、 磁碟分割或個別項目上設定鎖定。 比方說，這個陳述式將會遭到刪除，防止模型項目，並也會造成無法變更其屬性：

```csharp
using Microsoft.VisualStudio.Modeling.Immutability; ...
element.SetLocks(Locks.Delete | Locks.Property);
```

 其他鎖定的值可用來防止變更關聯性、 建立元素時，資料分割和角色中的重新排序連結之間移動資料。

 鎖定會套用到使用者動作及程式碼。 如果程式碼嘗試進行變更時，`InvalidOperationException`就會擲回。 鎖定會忽略在復原或重做作業。

 您可以探索項目是否有任何鎖定指定的集合中使用`IsLocked(Locks)`您可以使用，以取得目前集合的項目上的鎖定和`GetLocks()`。

 您可以設定鎖定，而不使用交易。 鎖定資料庫不是存放區的一部分。 如果您設定鎖定回應值的變更在存放區中，例如在 OnValueChanged，您就應該允許變更屬於的復原作業。

 這些方法是擴充方法中所定義的<xref:Microsoft.VisualStudio.Modeling.Immutability>命名空間。

### <a name="locks-on-partitions-and-stores"></a>鎖定資料分割和存放區
 鎖定也可以套用至資料分割和存放區。 設定磁碟分割的鎖定套用至資料分割中的所有項目。 因此，比方說，下列陳述式會造成資料分割中的所有項目無法被刪除，無論他們自己的鎖定狀態。 不過，其他鎖定這類`Locks.Property`仍然可以在個別的項目上設定：

```csharp
partition.SetLocks(Locks.Delete);
```

 設定存放區的鎖定套用至所有項目，不論該資料分割和項目鎖定的設定。

### <a name="using-locks"></a>使用鎖定
 您可以使用鎖定來實作配置，如下所示：

- 不允許所有的項目和關聯性以外，表示註解的變更。 這可讓使用者加上註解不需要變更它的模型。

- 不允許預設分割區中的變更，但允許在圖表的資料分割的變更。 使用者可以重新排列圖表中，但不能改變基礎的模型。

- 禁止變更除了在個別的資料庫中註冊的使用者群組的存放區。 其他使用者時，圖表和模型是唯讀。

- 不允許為模型的變更，如果圖表的布林值屬性設定為 true。 提供功能表命令，以變更該屬性。 這有助於確保它們不會進行的使用者不小心變更。

- 不允許新增和刪除的項目和關聯性的特定類別，但允許變更屬性。 這會將使用者提供固定的表單開發人員可以在其中填入屬性。

## <a name="lock-values"></a>鎖定值
 鎖定可以設定存放區、 磁碟分割，或個別的 ModelElement。 鎖定是`Flags`列舉型別： 您可以結合使用其值 '&#124;'。

- 鎖定的 ModelElement 永遠會包含其資料分割的鎖定。

- 鎖定資料分割一律會包含存放區的鎖定。

  您無法在磁碟分割上設定鎖定或儲存，並同時停用個別的項目上的鎖定。

|值|這表示如果`IsLocked(Value)`為 true|
|-|-|
|None|沒有限制。|
|屬性|無法變更定義域屬性的項目。 這不適用於關聯性中的網域類別的角色所產生的屬性。|
|新增|在資料分割，則無法建立新的項目和連結，或儲存。<br /><br /> 不適用於`ModelElement`。|
|Move|無法分割區之間移動項目，如果`element.IsLocked(Move)`為 true，或如果`targetPartition.IsLocked(Move)`為 true。|
|刪除|無法刪除項目，如果這個鎖定設定項目本身，或在任何項目要刪除會傳播，例如內嵌的項目和圖形。<br /><br /> 您可以使用`element.CanDelete()`來探索是否可以刪除項目。|
|重新排列|無法變更連結的 roleplayer 的順序。|
|RolePlayer|也就源自於這個項目的連結集，無法變更。 比方說，新的項目不可以內嵌在這個項目。 這不會影響此元素的目標的連結。<br /><br /> 如果這個項目是連結，其來源和目標不會影響。|
|全部|其他值的位元 OR 運算。|

## <a name="locking-policies"></a>鎖定原則
 身為 DSL 的作者，您可以定義*鎖定原則*。 鎖定原則，讓您可以防止特定鎖定設定，或要求，必須設定特定的鎖定會節制主控 SetLocks() 的操作。 一般而言，您可使用鎖定原則可禁止使用者或開發人員不小心在相同的方式，您可以宣告變數 contravening DSL，用途`private`。

 您也可以使用鎖定原則來設定所有項目上的鎖定的項目類型而定。 這是因為`SetLocks(Locks.None)`一律會在第一次建立或從檔案還原序列化的項目時所呼叫。

 不過，您無法使用原則來變更其生命期限內的項目上的鎖定。 若要達成該效果，您應該使用呼叫`SetLocks()`。

 若要定義鎖定原則，您必須：

- 建立會實作 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> 的類別。

- 加入這個類別都是透過您的 DSL 的 DocData 的服務。

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

 進行呼叫時，會呼叫這些方法`SetLocks()`存放區、 磁碟分割，或 ModelElement。 在每個方法中，您會提供建議的一份鎖定。 您可以傳回建議的設定，或者您可以加入和減去鎖定。

 例如: 

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

 若要確定使用者隨時都可以刪除項目，即使其他程式碼會呼叫 `SetLocks(Lock.Delete):`

 `return proposedLocks & (Locks.All ^ Locks.Delete);`

 不允許在每個項目的 MyClass 的所有屬性的變更：

 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`

### <a name="to-make-your-policy-available-as-a-service"></a>若要讓以服務形式供您的原則
 在您`DslPackage`專案中，加入新的檔案，其中包含類似下列範例的程式碼：

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
