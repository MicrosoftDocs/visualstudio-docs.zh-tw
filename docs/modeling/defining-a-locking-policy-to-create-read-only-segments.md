---
title: "定義要建立唯讀區段的鎖定原則 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa549c71-2bf6-4b08-b7b2-7756dd6f1dc8
caps.latest.revision: "12"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 93e4393a7b6731a10a00dc309353dba5870c269f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>定義鎖定原則來建立唯讀區段
不變性 API [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Visualization and Modeling SDK 可讓程式鎖定部分或全部的特定領域語言 (DSL) 模型，讓它可以讀取但不是會變更。 無法使用此唯讀選項，例如，讓使用者可以要求加上註解，並檢閱 DSL 模型的同事，但可以變更原始禁止。  
  
 此外，做為 DSL 的作者，您可以定義*鎖定原則。* 鎖定會允許，不允許，或強制的鎖定原則定義。 比方說，當您發行 DSL，您可以鼓勵協力廠商開發人員擴充，以新命令。 不過，您也可以使用鎖定原則，防止它們改變模型的指定組件的唯讀狀態。  
  
> [!NOTE]
>  可以使用反映來規避鎖定原則。 它適用於協力廠商開發人員，提供清楚的界限，但不提供增強式安全性。  
  
 詳細資訊和範例可用在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkId=186128)網站。  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
  
## <a name="setting-and-getting-locks"></a>設定和取得鎖定  
 在存放區、 資料分割，或個別的項目，您可以設定鎖定。 例如，這個陳述式會防止將模型項目遭到刪除，並將也會阻止其屬性變更：  
  
```  
using Microsoft.VisualStudio.Modeling.Immutability; ...  
element.SetLocks(Locks.Delete | Locks.Property);  
```  
  
 其他鎖定值可以用來防止在關聯性、 項目建立、 移動資料分割，在角色中的重新排序連結之間的變更。  
  
 鎖定套用使用者動作和程式碼。 如果程式碼嘗試進行變更，`InvalidOperationException`就會擲回。 在復原或重做作業的鎖定會遭到忽略。  
  
 您可以探索項目是否有任何鎖定在指定集合中使用`IsLocked(Locks)`，您可以使用來取得目前的資料集的項目上的鎖定`GetLocks()`。  
  
 您可以設定鎖定，而不使用交易。 鎖定資料庫不是存放區的一部分。 如果您設定鎖定回應值的變更在存放區中，例如在 OnValueChanged，您就應該允許變更屬於的復原作業。  
  
 這些方法是擴充方法中所定義的<xref:Microsoft.VisualStudio.Modeling.Immutability>命名空間。  
  
### <a name="locks-on-partitions-and-stores"></a>鎖定資料分割和儲存區  
 鎖定也可以套用至資料分割和存放區。 設定磁碟分割的鎖定套用至資料分割中的所有項目。 因此，比方說，下列陳述式會使資料分割中的所有項目無法刪除，不論其自己的鎖定狀態。 不過，其他鎖定例如`Locks.Property`仍無法設定個別項目上：  
  
```  
partition.SetLocks(Locks.Delete);  
```  
  
 設定存放區的鎖定套用至所有項目，而不論該鎖定資料分割與項目上的設定為何。  
  
### <a name="using-locks"></a>使用鎖定  
 您無法使用鎖定來實作結構描述，如下列範例：  
  
-   不允許所有項目和關聯性以外代表註解的變更。 這可讓使用者加上註解不需要變更它的模型。  
  
-   不允許變更預設資料分割中，但允許變更圖表的資料分割中。 使用者可以重新排列圖表中，但無法變更基礎模型。  
  
-   不允許變更除了會在個別的資料庫中註冊的使用者群組的存放區。 其他使用者，圖表和模型都是唯讀狀態。  
  
-   不允許變更模型，如果圖表的布林屬性設定為 true。 提供功能表命令來變更該屬性。 這有助於確保它們不會進行使用者不小心變更。  
  
-   不允許新增和刪除的項目和關聯性的特定類別，但允許屬性變更。 這可以讓使用者有固定的表單，可以在其中填入屬性。  
  
## <a name="lock-values"></a>鎖定值  
 可以儲存、 資料分割或個別 ModelElement 上設定鎖定。 鎖定是`Flags`列舉型別： 您可以結合使用其值 ' &#124;'。  
  
-   鎖定的 ModelElement 一定要包含其資料分割的鎖定。  
  
-   鎖定資料分割一律會包含存放區的鎖定。  
  
 您無法在資料分割上設定鎖定，或儲存並同時停用個別的項目上的鎖定。  
  
|值|這表示如果`IsLocked(Value)`為 true|  
|-----------|------------------------------------------|  
|無|沒有限制。|  
|屬性|無法變更定義域屬性的項目。 這不適用於網域中的類別關聯性的角色所產生的屬性。|  
|新增|在資料分割，則無法建立新的項目和連結或儲存。<br /><br /> 不適用於`ModelElement`。|  
|Move|無法分割區之間移動項目，如果`element.IsLocked(Move)`為 true，或如果`targetPartition.IsLocked(Move)`為 true。|  
|刪除|無法刪除項目，如果這個鎖定設定項目本身，或在任何項目要刪除會傳播，例如內嵌的項目和圖形。<br /><br /> 您可以使用`element.CanDelete()`來探索項目是否可以刪除。|  
|重新排列|無法變更連結 roleplayer 時的順序。|  
|RolePlayer|無法變更連結的來源是在這個項目集。 例如，新項目不可以內嵌在這個項目。 這不會影響這個項目是目標的連結。<br /><br /> 如果這個項目是連結，其來源和目標不會影響。|  
|全部|其他值的位元 OR 運算。|  
  
## <a name="locking-policies"></a>鎖定原則  
 做為 DSL 的作者，您可以定義*鎖定原則*。 鎖定原則，讓您可以防止特定鎖定設定，或強制，必須將特定的鎖定會節制主控 SetLocks() 的操作。 一般而言，您可使用鎖定原則，防止使用者或開發人員不小心 contravening DSL 的用途，您可以將變數宣告的方式相同`private`。  
  
 您也可以使用鎖定原則設定的項目類型相依的所有項目上鎖定。 這是因為`SetLocks(Locks.None)`一律會先建立或從檔案還原序列化項目時呼叫。  
  
 不過，您無法使用原則來變更其生命期限內的項目上的鎖定。 若要達成這個效果，您應該使用呼叫`SetLocks()`。  
  
 若要定義鎖定原則，您必須：  
  
-   建立會實作 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> 的類別。  
  
-   將這個類別加入到為服務，可透過 DSL 的 DocData。  
  
### <a name="to-define-a-locking-policy"></a>若要定義鎖定原則  
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>具有下列定義：  
  
```  
public interface ILockingPolicy  
{  
  Locks RefineLocks(ModelElement element, Locks proposedLocks);  
  Locks RefineLocks(Partition partition, Locks proposedLocks);  
  Locks RefineLocks(Store store, Locks proposedLocks);  
}  
```  
  
 進行呼叫時，會呼叫這些方法`SetLocks()`存放區、 磁碟分割，或 ModelElement。 在每個方法，為您提供建議的鎖定集。 您可以傳回建議的設定，或您可以加入和減去鎖定。  
  
 例如:   
  
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
  
 請確定使用者隨時都可以刪除元素，即使其他程式碼會呼叫`SetLocks(Lock.Delete):`  
  
 `return proposedLocks & (Locks.All ^ Locks.Delete);`  
  
 不允許在 MyClass 中的所有元素的所有屬性的變更：  
  
 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`  
  
### <a name="to-make-your-policy-available-as-a-service"></a>若要以服務形式提供您的原則  
 在您`DslPackage`專案中，加入新的檔案，其中包含與下列範例類似的程式碼：  
  
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
