---
title: 如何：執行嵌套專案 |Microsoft Docs
description: 瞭解如何藉由從方案和父專案引發事件以建立專案階層，在 Visual Studio 中執行嵌套專案。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 85a5c14196211a638cd830ac6df39570288aa831
ms.sourcegitcommit: 2f964946d7044cc7d49b3fc10b413ca06cb2d11b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2020
ms.locfileid: "96761333"
---
# <a name="how-to-implement-nested-projects"></a>如何：執行嵌套專案

當您建立嵌套專案類型時，必須執行幾個額外的步驟。 父專案會採用解決方案針對其嵌套 (子) 專案所擁有的相同責任。 父專案是類似于方案的專案容器。 尤其是，方案和父專案必須引發數個事件，以建立嵌套專案的階層架構。 這些事件將在下列程式中描述，以建立嵌套專案。

## <a name="create-nested-projects"></a>建立嵌套專案

1. 整合式開發環境 (IDE) 透過呼叫介面載入父專案的專案檔案和啟動資訊 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> 。 父專案已建立並加入至方案。

    > [!NOTE]
    > 到目前為止，因為必須先建立父專案，才能建立子專案，所以父專案建立嵌套專案的程式太早太早。 依照這個順序，父專案可以將設定套用至子專案，而子專案可以視需要從父專案取得資訊。 此順序是用戶端所需的順序，例如原始程式碼控制 (SCC) 和 **方案總管**。

     父專案必須等待 <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> IDE 呼叫方法，才能建立其嵌套 (子) 專案或專案。

2. IDE 會 `QueryInterface` 在的父專案上呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject> 。 如果這個呼叫成功，IDE 就會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> 父系的方法，以開啟父專案的所有嵌套專案。

3. 父專案 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> 會呼叫方法，以通知接聽程式即將建立的嵌套專案。 例如，SCC 會接聽這些事件，以瞭解解決方案和專案建立程式中的步驟是否按照順序發生。 如果步驟未依順序發生，則可能無法正確地向原始程式碼控制註冊方案。

4. 父專案會 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> 在其每個子專案上呼叫方法或方法。

     您會傳遞 <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> 至 `AddVirtualProject` 方法，以指出應該將虛擬 (嵌套) 專案加入至專案視窗、從組建中排除、加入至原始程式碼控制等。 `VSADDVPFLAGS` 可讓您控制嵌套專案的可見度，並指出與其相關聯的功能。

     如果您重載先前現有的子專案，而該專案的專案 GUID 儲存在父專案的專案檔中，則父專案會呼叫 `AddVirtualProjectEx` 。 和之間的唯一差異在於 `AddVirtualProject` `AddVirtualProjectEX` `AddVirtualProjectEX` 具有參數，可讓父專案指定每個實例的 `guidProjectID` 子專案，以使其能夠 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> 正常運作。

     如果沒有可用的 GUID，例如當您加入新的嵌套專案時，方案會在新增至父系時，為專案建立一個 GUID。 父專案必須負責在其專案檔中保存該專案 GUID。 如果您刪除了嵌套專案，也可以刪除該專案的 GUID。

5. IDE 會 <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren> 在父專案的每個子專案上呼叫此方法。

     如果您想要嵌套專案，則必須執行父專案 `IVsParentProject` 。 但是，即使父專案的 `QueryInterface` `IVsParentProject` 父專案位於其底下，也永遠不會呼叫。 解決方案會處理對的呼叫 `IVsParentProject` ，並在執行時呼叫 `OpenChildren` 以建立嵌套專案。 `AddVirtualProjectEX` 一律會從呼叫 `OpenChildren` 。 父專案絕不會呼叫它，以依序保留階層建立事件。

6. IDE 會 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> 在子專案上呼叫方法。

7. 父專案 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> 會呼叫方法，以通知接聽程式已建立父系的子專案。

8. IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> 會在開啟所有子專案之後，呼叫父專案上的方法。

     如果它不存在，則父專案會藉由呼叫來建立每個嵌套專案的 GUID `CoCreateGuid` 。

    > [!NOTE]
    > `CoCreateGuid` 是在建立 GUID 時呼叫的 COM API。 如需詳細資訊，請參閱 `CoCreateGuid` MSDN Library 中的和 guid。

     父專案會將此 GUID 儲存在其專案檔中，以便下一次在 IDE 中開啟時加以取出。 請參閱步驟4，以取得與的呼叫相關的詳細資訊，以 `AddVirtualProjectEX` 取得 `guidProjectID` 子專案的。

9. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>然後，系統會針對父 ItemID 呼叫方法，依照慣例，您會將委派給嵌套專案。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>會在父代上呼叫您要委派的專案時，抓取該節點的屬性。

     因為父系和子專案是以程式設計方式具現化，所以您可以在這個位置設定嵌套專案的屬性。

    > [!NOTE]
    > 您不僅會從嵌套專案接收內容資訊，還可以藉由檢查 __VSHPROPID，來詢問父專案是否有該專案的任何內容 [。VSHPROPID_UserCoNtext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_UserContext>)。 如此一來，您就可以針對個別的嵌套專案加入額外的動態說明屬性和功能表選項。

10. 階層的建立是為了在 **方案總管** 中，透過呼叫方法來顯示 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> 。

     您可以透過將階層傳遞至環境， `GetNestedHierarchy` 以建立要在方案總管中顯示的階層。 如此一來，解決方案就知道專案存在，而且可以由組建管理員來管理，或允許專案中的檔案放在原始程式碼控制之下。

11. 當 Project1 的所有嵌套專案都已建立時，控制權會傳回給方案，並針對 Project2 重複處理常式。

     針對具有子系的子專案，則會發生建立嵌套專案的相同程式。 在此情況下，如果 BuildProject1 （即 Project1 的子系）有子專案，則會在 BuildProject1 之後和 Project2 之前建立。 此程式是遞迴的，且階層是由上而下建立的。

     當因為使用者關閉方案或特定專案本身而關閉嵌套專案時，會呼叫上的另一個方法 `IVsParentProject` <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A> 。 父專案 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> 會使用和方法來包裝對方法的呼叫， <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> 以通知接聽程式要關閉的解決方案事件。

下列主題將討論當您執行嵌套專案時要考慮的其他幾個概念：

- [卸載和重載嵌套專案的考慮](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [針對嵌套專案的 Wizard 支援](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [執行嵌套專案的命令處理](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [篩選嵌套專案的 AddItem 對話方塊](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)

## <a name="see-also"></a>另請參閱

- [在 [加入新專案] 對話方塊中加入專案](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [註冊專案和專案範本](../../extensibility/internals/registering-project-and-item-templates.md)
- [檢查清單：建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)
- [內容參數](../../extensibility/internals/context-parameters.md)
- [Wizard ( .vsz) 檔](../../extensibility/internals/wizard-dot-vsz-file.md)
