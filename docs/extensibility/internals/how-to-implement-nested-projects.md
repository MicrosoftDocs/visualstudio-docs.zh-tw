---
title: 如何:實施嵌套專案 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8d9dfe567db0b8788b93b13aeb760d45f4c05b57
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707977"
---
# <a name="how-to-implement-nested-projects"></a>如何:實現嵌so專案

創建嵌套項目類型時,必須實現幾個附加步驟。 父項目承擔與解決方案對其嵌套(子)項目承擔的一些相同職責。 父項目是類似於解決方案的專案容器。 特別是,有幾個事件必須由解決方案和父項目引發,才能生成嵌套專案的層次結構。 這些事件在以下創建嵌套專案的過程中進行了描述。

## <a name="create-nested-projects"></a>建立巢狀專案

1. 集成開發環境 (IDE) 通過<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>呼叫介面載入父專案的專案檔和啟動資訊。 父專案將創建並添加到解決方案中。

    > [!NOTE]
    > 此時,父項目創建嵌套項目的過程還為時過早,因為必須先創建父專案,然後才能創建子專案。 遵循此序列,父專案可以將設置應用於子項目,並且子專案可以根據需要從父專案獲取資訊。 此序列是用戶端(如原始碼控制(SCC) 和**解決方案資源管理員**等需要它。

     父項目必須等待 IDE<xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A>調用該方法,然後才能創建其嵌套(子)專案或專案。

2. IDE`QueryInterface`對的父項目呼<xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>叫 。 如果此調用成功,IDE 將調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A>父項的方法以打開父專案的所有嵌套專案。

3. 父項目調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A>方法以通知偵聽器即將創建嵌套專案。 例如,SCC 正在偵聽這些事件,瞭解解決方案和專案創建過程中的步驟是否按順序進行。 如果步驟順序不正確,則可能無法正確註冊原始程式碼管理。

4. 父項目調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A>方法或其每個<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A>子 專案上的方法。

     傳遞給<xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS>`AddVirtualProject`方法以指示應將虛擬(嵌套)專案添加到專案視窗,從生成中排除,添加到原始程式碼控制項,依如此。 `VSADDVPFLAGS`允許您控制嵌套項目的可見性,並指示與其關聯的功能。

     如果重新載入以前存在的子項目,該專案 GUID 儲存在父項目的項目檔中,則父項目`AddVirtualProjectEx`將呼叫 。 `AddVirtualProject`之間的`AddVirtualProjectEX`唯一區別是,`AddVirtualProjectEX`具有一個參數,使父項目能夠為每個實`guidProjectID`例 指定一個子專案,<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A>以便<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A>啟用 和正常運行。

     如果沒有 GUID 可用(例如,當您添加新嵌套專案時)時,解決方案會在專案添加到父專案時為該專案創建一個。 父專案有責任在其專案檔中保留該專案 GUID。 如果刪除嵌套專案,也可以刪除該專案的 GUID。

5. IDE 調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren>父 專案的每個子專案上的方法。

     如果要嵌套專案,則必須`IVsParentProject`實現父專案。 但是,父專案即使其`QueryInterface``IVsParentProject`下方 有父專案,也從不調用。 解決方案處理對的`IVsParentProject`調用,如果實現,則調用`OpenChildren`以創建嵌套專案。 `AddVirtualProjectEX`從`OpenChildren`呼叫 。 父項目絕不應調用它來保持層次結構創建事件的順序。

6. IDE 調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>子 專案上的方法。

7. 父項目調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A>方法以通知偵聽器父項的子專案已創建。

8. 打開所有子專案<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A>后,IDE 將調用父專案上的方法。

     如果不存在,父項目通過調用`CoCreateGuid`為每個嵌套項目創建 GUID。

    > [!NOTE]
    > `CoCreateGuid`是在創建 GUID 時呼叫的 COM API。 有關詳細資訊,請參閱`CoCreateGuid`MSDN 庫中的 GUID。

     父專案將此 GUID 存儲在其專案檔中,以便下次在 IDE 中打開時將其檢索。 有關調用`AddVirtualProjectEX`檢`guidProjectID`索 子項目的詳細資訊,請參閱步驟 4。

9. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>然後,將調用父 ItemID,通過約定,將該方法委派給嵌套專案。 檢索<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>嵌套要在父級上調用專案時要委派的專案的節點的屬性。

     由於父專案和子專案以程式設計方式實例化,因此此時可以為嵌套專案設置屬性。

    > [!NOTE]
    > 您不僅從嵌套專案中接收上下文資訊,還可以通過檢查__VSHPROPID來詢問父專案是否有任何該項的上下文[。VSHPROPID_UserContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_UserContext>). 通過這種方式,您可以添加特定於單個嵌套項目的額外動態説明屬性和功能表選項。

10. 層次結構是為在**解決方案資源管理器**中顯示而構建的,並調<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>用 該方法。

     通過將層次結構傳遞給環境`GetNestedHierarchy`,以生成要在解決方案資源管理器中顯示的層次結構。 通過這種方式,解決方案知道專案存在,並且可以由生成管理器進行管理以生成,或者允許將專案中的檔置於原始程式碼控制之下。

11. 創建 Project1 的所有嵌套專案後,控制項將傳回解決方案,並重複 Project2 的過程。

     對於具有子項的子專案,將發生相同的創建嵌套項目的過程。 在這種情況下,如果作為 Project1 的子項的 Build Project1 具有子專案,則這些專案將在生成 Project1 之後和 Project2 之前創建。 該過程是遞歸的,層次結構是從自上而下構建的。

     當嵌套項目由於使用者關閉解決方案或特定專案本身而關閉時,將調用`IVsParentProject`<xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>上的另一種方法。 父專案用<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A><xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A><xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A>和 方法將調用換行,以通知偵聽器到解決方案事件,嵌套專案正在關閉。

以下主題涉及實現嵌套專案時要考慮的其他幾個概念:

- [卸載並重新載入嵌套項目的注意事項](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [匯入嵌入專案的精靈支援](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [為嵌入項目執行指令處理](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [篩選嵌套項目的「新增項目」對話框](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)

## <a name="see-also"></a>另請參閱

- [新增項目新增項目新增項目對話框](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [註冊項目和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)
- [檢查表:建立新的項目型態](../../extensibility/internals/checklist-creating-new-project-types.md)
- [內容參數](../../extensibility/internals/context-parameters.md)
- [匯入匯(.vsz) 檔案](../../extensibility/internals/wizard-dot-vsz-file.md)
