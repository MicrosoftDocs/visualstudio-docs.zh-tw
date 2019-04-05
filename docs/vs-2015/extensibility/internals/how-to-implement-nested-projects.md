---
title: HOW TO：實作巢狀的專案 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5100fb42cba7c993861ef5b9fa0682400b0cfa4a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58944480"
---
# <a name="how-to-implement-nested-projects"></a>HOW TO：實作巢狀專案
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

當您建立巢狀的專案類型，有幾個額外步驟必須實作。 父專案會採用一些相同的方案具有及其巢狀 （子系） 專案的責任。 父專案是類似於方案的專案的容器。 特別是，有數個必須在解決方案，以及若要建立巢狀專案的階層的父專案所引發的事件。 這些事件是以建立巢狀的專案的下列程序所述。  
  
### <a name="to-create-nested-projects"></a>若要建立巢狀的專案  
  
1. 整合式的開發環境 (IDE) 載入父專案的專案檔案和啟動資訊，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>介面。 父專案建立並加入至方案。  
  
   > [!NOTE]
   >  到目前為止，則還太早父專案來建立巢狀的專案，因為必須先建立父專案，可以建立子專案的程序。 依照這個順序中，父專案可以將設定套用至子專案，並視子專案能夠取得父專案中的資訊。 此序列是需要在原始程式碼控制 (SCC) 等方案總管 中的用戶端。  
  
    父專案必須等候<xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A>專案，它可以建立巢狀 （子） 之前，IDE 所要呼叫的方法。  
  
2. IDE 呼叫`QueryInterface`上的父專案<xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>。 如果這個呼叫會成功，IDE 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A>開啟父專案的巢狀專案的所有父代的方法。  
  
3. 父專案呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A>是即將建立的方法來通知巢狀專案的接聽程式。 SCC，比方說，接聽這些事件才能知道是否方案和專案建立程序中的步驟所發生的順序。 如果步驟發生故障，解決方案可能不會與原始程式碼控制正確登錄。  
  
4. 父專案呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A>方法或<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A>及其子專案的每個上的方法。  
  
    您傳遞<xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS>至`AddVirtualProject`方法，指出虛擬 （巢狀） 的專案應該加入 [專案] 視窗中，從組建排除加入原始程式碼控制項中，依此類推。 `VSADDVPFLAGS` 可讓您控制巢狀專案的可見性，並指出哪些功能是與它相關聯。  
  
    如果您重新載入先前已存在的子專案的專案儲存在父專案的專案檔案中的父專案呼叫的 GUID `AddVirtualProjectEx`。 唯一的差別`AddVirtualProject`和`AddVirtualProjectEX`在於`AddVirtualProjectEX`有參數，以啟用父專案，以指定每個執行個體`guidProjectID`的子專案，以啟用<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A>函式正確。  
  
    如果沒有 GUID，例如當您加入新的巢狀的專案時，解決方案會建立一個專案時，它會新增至父代。 它負責父專案來保存該專案在其專案檔中的 GUID。 如果您刪除巢狀的專案時，也可以刪除該專案的 GUID。  
  
5. IDE 呼叫`M:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren`父專案的每一個子專案上的方法。  
  
    父專案必須實作`IVsParentProject`如果您想要建立巢狀專案。 但是專案永遠不會呼叫父`QueryInterface`針對`IVsParentProject`即使它有它的父專案。 解決方案會處理對`IVsParentProject`，如果實作時，會呼叫`OpenChildren`建立巢狀的專案。 `AddVirtualProjectEX` 一律會從呼叫`OpenChildren`。 它應該永遠不會由父專案在順序中保留階層建立事件呼叫。  
  
6. IDE 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>子專案上的方法。  
  
7. 父專案呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A>方法來通知接聽程式已建立的父代的子專案。  
  
8. IDE 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A>父專案之後已經開啟所有的子專案的方法。  
  
    如果已經存在，則父專案會建立每個巢狀專案的 GUID 藉由呼叫`CoCreateGuid`。  
  
   > [!NOTE]
   >  `CoCreateGuid` COM API 呼叫時要建立的 GUID。 如需詳細資訊，請參閱`CoCreateGuid`和 MSDN Library 中的 Guid。  
  
    父專案會儲存此 GUID 要擷取下一次，它會在 IDE 中開啟其專案檔中。 請參閱步驟 4 與呼叫相關的詳細資訊`AddVirtualProjectEX`擷取`guidProjectID`子專案。  
  
9. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>父項目識別碼，然後呼叫方法，依照慣例您委派中巢狀的專案。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>擷取巢狀處理您想要在父系上呼叫時，委派中的專案節點的屬性。  
  
     因為父和子專案具現化以程式設計的方式，您可以在此時設定巢狀專案的屬性。  
  
    > [!NOTE]
    >  不只執行您會看到從巢狀專案中，執行的內容資訊，但您也可以要求父專案是否已藉由檢查該項目的任何內容<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>。 如此一來，您可以加入額外的動態說明屬性及功能表選項，指定個別的巢狀專案。  
  
10. 階層是顯示在 [方案總管] 藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>方法。  
  
     透過在環境中將階層`GetNestedHierarchy`建置在方案總管 中顯示階層架構。 在這種方式，解決方案會知道專案存在並可將建置的組建管理員 中，或可以允許將受原始程式碼控制專案中的檔案。  
  
11. Project1 巢狀的所有專案建立後，控制權會傳遞回方案和程序會重複 Project2。  
  
     有子系的子專案，就會發生同樣的程序來建立巢狀的專案。 在此情況下，如果 BuildProject1，也就是子系 Project1，有子專案，就會建立它們之後 BuildProject1 和 Project2 之前。 此程序是遞迴和階層是從頂端向下。  
  
     巢狀的專案關閉時使用者關閉方案或特定專案本身，另一種方法，因為`IVsParentProject`， <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>，會呼叫。 父專案將呼叫包裝<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A>方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A>而<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A>來通知解決方案的事件接聽程式，關閉巢狀的專案的方法。  
  
    下列主題處理實作巢狀的專案時要考量的幾個其他概念：  
  
    [卸載並重新載入巢狀專案的考量](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)  
  
    [巢狀專案的精靈支援](../../extensibility/internals/wizard-support-for-nested-projects.md)  
  
    [實作巢狀專案的命令處理](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)  
  
    [篩選巢狀專案的 AddItem 對話方塊](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)  
  
## <a name="see-also"></a>另請參閱  
 [新增項目加入新項目對話方塊](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [註冊專案和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)   
 [檢查清單：建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [內容參數](../../extensibility/internals/context-parameters.md)   
 [精靈檔 (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
