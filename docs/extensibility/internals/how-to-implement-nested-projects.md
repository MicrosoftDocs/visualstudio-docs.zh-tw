---
title: "如何： 實作巢狀的專案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 26456122d8b2cb0e89cfcda929cf68306959a31e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-implement-nested-projects"></a>如何： 實作巢狀的專案
當您建立的巢狀的專案類型都必須實作數個額外的步驟。 父專案會在某些相同方案中有針對其巢狀 （子系） 專案的責任。 父專案是類似於方案的專案的容器。 特別是，有數個解決方案和所要建立的巢狀專案階層的父專案必須引發的事件。 這些事件是以建立巢狀的專案的下列程序所述。  
  
### <a name="to-create-nested-projects"></a>若要建立巢狀的專案  
  
1.  整合式的開發環境 (IDE) 藉由呼叫載入父專案的專案檔和啟動資訊<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>介面。 父專案建立並加入至方案。  
  
    > [!NOTE]
    >  此時，它是父專案來建立巢狀的專案，因為必須建立父專案，才能建立子專案的程序還太早。 遵循此順序，父專案可以將設定套用至子專案而視子專案可取得父專案中的資訊。 此順序是如果需要在原始程式碼控制 (SCC) 等方案總管 中的用戶端。  
  
     父專案必須等候<xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A>專案，它才能建立其巢狀 （子） IDE 所呼叫方法。  
  
2.  IDE 呼叫`QueryInterface`上父專案<xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>。 如果這個呼叫會成功，IDE 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A>開啟父專案的巢狀專案的所有父系的方法。  
  
3.  父專案呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A>方法來通知接聽程式巢狀專案即將被建立。 SCC，比方說，接聽知道如果方案和專案建立程序中的步驟會在順序中進行這些事件。 順序的步驟時，方案可能不會與原始程式碼控制正確登錄。  
  
4.  父專案呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A>方法或<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A>及其子專案的每個上的方法。  
  
     您傳遞<xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS>至`AddVirtualProject`方法，指出虛擬 （巢狀） 專案，應該加入 [專案] 視窗中，從組建排除加入原始程式碼控制，依此類推。 `VSADDVPFLAGS`可讓您控制可見性的巢狀專案，並指出哪些功能可與它相關聯。  
  
     如果您重新載入先前已存在的子專案的專案儲存在父專案的專案檔，父專案呼叫的 GUID `AddVirtualProjectEx`。 唯一的差別`AddVirtualProject`和`AddVirtualProjectEX`在於`AddVirtualProjectEX`有參數，讓父專案，以指定每個執行個體`guidProjectID`的子專案，以啟用<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A>函式正確。  
  
     如果沒有 GUID 可用，例如當您新增新的巢狀的專案時，方案會建立一個專案時加入至父代。 它負責父專案來保存該專案其專案檔中的 GUID。 如果您刪除巢狀的專案，也可以刪除該專案的 GUID。  
  
5.  IDE 呼叫`M:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren`父專案的每一個子專案上的方法。  
  
     父專案必須實作`IVsParentProject`如果您想要建立巢狀專案。 但是專案永遠不會呼叫父`QueryInterface`如`IVsParentProject`即使它有父專案底下。 方案會處理呼叫`IVsParentProject`和實作時，如果呼叫`OpenChildren`建立巢狀的專案。 `AddVirtualProjectEX`一律會從呼叫`OpenChildren`。 它應該永遠不會由父專案，將階層建立事件保留在順序呼叫。  
  
6.  IDE 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>子專案上的方法。  
  
7.  父專案呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A>方法來通知接聽程式已建立的父代的子專案。  
  
8.  IDE 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A>父專案之後，已經開啟所有的子專案上的方法。  
  
     如果已經存在，則父專案會建立每個巢狀專案的 GUID 藉由呼叫`CoCreateGuid`。  
  
    > [!NOTE]
    >  `CoCreateGuid`COM API 呼叫時要建立的 GUID。 如需詳細資訊，請參閱`CoCreateGuid`和 MSDN Library 中的 Guid。  
  
     父專案會在要擷取 IDE 中開啟，下次其專案檔中儲存此 GUID。 請參閱步驟 4，如需詳細資訊與相關的呼叫`AddVirtualProjectEX`擷取`guidProjectID`子專案。  
  
9. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>為父項目識別碼，然後呼叫方法依慣例您將委派中加入巢狀專案。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>擷取會建立您想要在父代上呼叫時，委派中的專案節點的屬性。  
  
     因為父和子專案中具現化以程式設計的方式，您可以在此時設定巢狀專案的屬性。  
  
    > [!NOTE]
    >  不只進行巢狀專案，從接收的內容資訊，但您也可以要求父專案是否已藉由檢查該項目的任何內容<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>。 如此一來，您可以加入額外的動態說明的屬性及功能表選項，指定個別的巢狀專案。  
  
10. 階層是顯示在 [方案總管] 藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>方法。  
  
     您將階層傳遞至透過環境`GetNestedHierarchy`若要建立以便在方案總管 中顯示階層。 在這種方式，方案會知道專案存在並可受建置的組建管理員，或可以允許將原始程式碼控制之下專案中的檔案。  
  
11. Project1 的所有巢狀的專案建立後，控制權會回到方案和程序會重複用於 Project2。  
  
     具有子元素的子專案，就會發生同樣的程序來建立巢狀的專案。 在此情況下，如果 BuildProject1，也就是 Project1 的子系，在子專案，則會建立之後 BuildProject1、 Project2 之前。 程序遞迴而且階層從頂端向下建置。  
  
     巢狀的專案當關閉，因為使用者關閉方案或特定專案本身，另一個方法上`IVsParentProject`， <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>，稱為。 父專案包裝呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A>方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A>通知，關閉巢狀的專案方案的事件接聽程式的方法。  
  
 下列主題處理實作巢狀的專案時要考量的幾個其他概念：  
  
 [卸載並重新載入巢狀專案的考量](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)  
  
 [巢狀專案的精靈支援](../../extensibility/internals/wizard-support-for-nested-projects.md)  
  
 [實作巢狀專案的命令處理](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)  
  
 [篩選巢狀專案的 AddItem 對話方塊](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)  
  
## <a name="see-also"></a>另請參閱  
 [加入項目來加入新項目對話方塊](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [註冊專案和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)   
 [檢查清單： 建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [內容參數](../../extensibility/internals/context-parameters.md)   
 [精靈檔 (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)