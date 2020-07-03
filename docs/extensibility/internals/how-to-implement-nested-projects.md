---
title: 如何：執行嵌套的專案 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3b1ac3c147962b943499172435c3f601115d36a9
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905351"
---
# <a name="how-to-implement-nested-projects"></a>如何：執行嵌套的專案

當您建立嵌套的專案類型時，必須執行幾個額外的步驟。 父專案會採用解決方案針對其嵌套（子系）專案所擁有的相同責任。 父專案是類似于方案的專案容器。 特別的是，方案和父專案必須引發數個事件，以建立嵌套專案的階層架構。 這些事件會在建立嵌套專案的下列進程中加以說明。

## <a name="create-nested-projects"></a>建立嵌套專案

1. 整合式開發環境（IDE）會藉由呼叫介面來載入父專案的專案檔和啟動資訊 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> 。 隨即建立父專案，並將其新增至方案。

    > [!NOTE]
    > 此時，父專案建立嵌套專案的程式太早過了，因為必須先建立父專案，才能建立子專案。 遵循此順序，父專案可以將設定套用至子專案，而子專案可以視需要從父專案取得資訊。 此順序是因為用戶端需要它，例如原始程式碼控制（SCC）和**方案總管**。

     父專案必須等候 <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> IDE 呼叫方法，才能建立其嵌套（子）專案或專案。

2. IDE 會 `QueryInterface` 在的父專案上呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject> 。 如果這個呼叫成功，IDE 會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> 父系的方法，以開啟父專案的所有嵌套專案。

3. 父專案 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> 會呼叫方法，以通知接聽程式將要建立的嵌套專案。 例如，SCC 會接聽這些事件，以瞭解解決方案和專案建立程式中的步驟是否依序發生。 如果步驟未按照順序發生，解決方案可能不會正確地向原始程式碼控制註冊。

4. 父專案會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> 其每個子專案的方法或方法。

     您會將傳遞 <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> 至 `AddVirtualProject` 方法，以指出應該將虛擬（nested）專案加入至專案視窗、從組建中排除、加入至原始程式碼控制項等等。 `VSADDVPFLAGS`可讓您控制嵌套專案的可見度，並指出與它相關聯的功能。

     如果您重載先前已存在的子專案，且專案 GUID 儲存在父專案的專案檔中，則父專案會呼叫 `AddVirtualProjectEx` 。 和之間的唯一差異在於 `AddVirtualProject` `AddVirtualProjectEX` ， `AddVirtualProjectEX` 有一個參數可讓父專案指定子專案的每個實例， `guidProjectID` 以便讓 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> 正常運作。

     如果沒有可用的 GUID （例如當您加入新的嵌套專案時），方案會在將其加入至父系時為專案建立一個。 父專案會負責將該專案 GUID 保存在其專案檔中。 如果您刪除的是嵌套專案，則也可以刪除該專案的 GUID。

5. IDE 會 <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren> 在父專案的每個子專案上呼叫方法。

     如果您想要嵌套專案，則父專案必須執行 `IVsParentProject` 。 但父專案永遠不會呼叫 `QueryInterface` ， `IVsParentProject` 即使它的父專案位於其底下也一樣。 解決方案會處理對的呼叫 `IVsParentProject` ，如果已執行，則會呼叫 `OpenChildren` 來建立嵌套專案。 `AddVirtualProjectEX`一律從呼叫 `OpenChildren` 。 父專案永遠不應呼叫它，以依序保留階層建立事件。

6. IDE 會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> 子專案上的方法。

7. 父專案 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> 會呼叫方法，以通知接聽程式已建立父代的子專案。

8. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A>當所有子專案都開啟之後，IDE 會在父專案上呼叫方法。

     如果尚未存在，父專案會藉由呼叫，為每個嵌套的專案建立 GUID `CoCreateGuid` 。

    > [!NOTE]
    > `CoCreateGuid`是在建立 GUID 時呼叫的 COM API。 如需詳細資訊，請參閱 `CoCreateGuid` MSDN library 中的和 guid。

     父專案會將此 GUID 儲存在它的專案檔中，以便下一次在 IDE 中開啟它。 如需的詳細資訊，請參閱步驟4，取得 `AddVirtualProjectEX` `guidProjectID` 子專案的呼叫。

9. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>然後會針對父系 ItemID 呼叫方法，依照慣例，您會將委派至嵌套專案。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>會抓取節點的屬性，在父代上呼叫您要委派的專案。

     由於父代和子專案是以程式設計方式具現化，因此您可以在此時設定嵌套專案的屬性。

    > [!NOTE]
    > 您不僅會從已嵌套的專案接收內容資訊，還可以藉由檢查 __VSHPROPID，詢問父專案是否有該專案的任何內容[。VSHPROPID_UserCoNtext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_UserContext>)。 如此一來，您就可以針對個別的嵌套專案加入額外的動態 [說明] 屬性和功能表選項。

10. 階層是針對在呼叫方法的**方案總管**中顯示而建立的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> 。

     您可以透過將階層傳遞至環境， `GetNestedHierarchy` 以建立要在方案總管中顯示的階層。 如此一來，解決方案就知道專案存在，而且可以由組建管理員進行管理，或允許專案中的檔案放在原始程式碼控制之下。

11. 建立 Project1 的所有嵌套專案之後，控制權會傳回給方案，並針對 Project2 重複處理。

     針對具有子系的子專案，會發生這個相同的程式來建立嵌套專案。 在此情況下，如果 BuildProject1 （也就是 Project1 的子系）有子專案，則會在 BuildProject1 之後和 Project2 之前建立。 此程式是遞迴的，並由上而下建立階層。

     當嵌套的專案因為使用者關閉方案或特定專案本身而關閉時， `IVsParentProject` 會呼叫、上的另一個方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A> 。 父專案 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> 會使用和方法來包裝對方法的呼叫， <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> 以通知接聽程式已關閉嵌套專案的解決方案事件。

下列主題會處理您在執行嵌套專案時要考慮的其他幾個概念：

- [卸載和重載嵌套專案的考慮](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [支援嵌套專案的 Wizard](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [執行嵌套專案的命令處理](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [篩選嵌套專案的 [AddItem] 對話方塊](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)

## <a name="see-also"></a>另請參閱

- [將專案加入至 [加入新專案] 對話方塊](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [註冊專案和專案範本](../../extensibility/internals/registering-project-and-item-templates.md)
- [檢查清單：建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)
- [內容參數](../../extensibility/internals/context-parameters.md)
- [Wizard （.vsz）檔案](../../extensibility/internals/wizard-dot-vsz-file.md)
