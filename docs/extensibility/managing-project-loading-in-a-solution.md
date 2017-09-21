---
title: "管理方案中的專案載入 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "管理專案載入的方案"
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# 管理方案中的專案載入
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio 方案可以包含大量的專案。 Visual Studio 預設為開啟方案時，同時載入方案中的所有專案且不允許使用者存取的任何專案，直到全部都已完成載入。 當專案載入的程序將持續超過兩分鐘時，進度列會顯示專案載入的數目和專案的總數。 使用者可以在多個專案的方案中工作時卸載專案，但此程序有一些缺點: 已卸載的專案不會建置為重建方案\] 命令的一部分，並且不會顯示 IntelliSense 的說明類型和成員的已關閉的專案。  
  
 開發人員可以減少方案載入時間，並管理專案建立方案負載的管理員來載入行為。 方案負載管理員可以設定不同的專案載入特定專案或專案類型的優先順序，請確定專案會載入之前啟動背景組建、 背景載入其他背景工作完成後之前, 的延遲時間以及執行其他專案負載管理工作。  
  
## 專案載入優先順序  
 Visual Studio 會定義四個不同的專案載入優先順序:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority> \(預設值\): 開啟方案時，會以非同步方式載入專案。 如果已卸載的專案上設定此優先順序，已經開啟方案之後，就會在下一個閒置點載入專案。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: 在背景中，讓使用者能夠存取的專案，而不需要等待已載入的所有專案載入方案開啟時，會都載入專案。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: 在存取時，會載入專案。 當使用者展開專案節點，在 \[方案總管\] 中的，方案就會開啟，因為它是在開啟的文件清單 \(保存在方案使用者選項檔\)，開啟屬於專案的檔案時，存取專案或另一個專案時，載入具有相依性專案。 這種類型的專案不會自動載入之前開始建置程序。方案載入管理員會負責確保會載入所有必要的專案。 開始尋找\/取代檔案中，用於整個方案之前，應該也可載入這些專案。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: 為無法載入，除非使用者明確要求的專案。 明確卸載專案時，這是大小寫。  
  
## 建立方案負載管理員  
 開發人員可以建立方案負載管理員藉由實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> ，並建議 Visual Studio 方案負載管理員使用中。  
  
#### 啟用方案負載管理員  
 Visual Studio 可讓只有一個方案負載管理員在指定的時間，因此當您想要啟動方案負載時，您必須告知 Visual Studio 管理員。 如果稍後啟用第二個方案負載管理員，將會中斷您的方案負載管理員。  
  
 您必須取得 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> 服務和設定 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> 屬性:  
  
```c#  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution; object objLoadMgr = this;   //the class that implements IVsSolutionManager pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
#### 實作 IVsSolutionLoadManager  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A> 開啟方案的程序期間呼叫方法。 若要實作此方法，您使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport> 服務，以設定您想要管理的專案類型的負載優先權。 例如，下列程式碼設定在背景中載入 C\# 專案類型:  
  
```c#  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}"); pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> 關閉 Visual Studio 或不同的封裝已經為使用中的方案負載管理員藉由呼叫時，呼叫方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> 與 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> 屬性。  
  
#### 針對不同種類的方案負載管理員的策略  
 您可以實作解決方案負載管理員不同的方式，根據它們一定會管理解決方案的類型。  
  
 如果方案負載管理員就是要管理的一般載入的方案，則可以實作為 VSPackage 的一部分。 封裝應該設定為自動載入，藉由新增 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> 上值為 VSPackage <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>。 然後可在啟動方案負載管理員 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 方法。  
  
> [!NOTE]
>  如需自動載入封裝的詳細資訊，請參閱 [載入 Vspackage](../extensibility/loading-vspackages.md)。  
  
 Visual Studio 能夠辨識只有最後一個方案負載管理員啟動，因為一般方案負載管理員一律會偵測是否有現有的負載管理員才能啟用本身。 如果方案服務上呼叫 GetProperty\(\) <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> 傳回 `null`, ，沒有使用中的方案負載管理員。 如果它不會傳回 null，請檢查物件是否與您的方案負載管理員相同。  
  
 如果方案負載管理員就是要管理只有幾種類型的解決方案，VSPackage 可以訂閱方案載入事件 \(藉由呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>\)，並使用事件處理常式 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> 啟動方案負載管理員。  
  
 如果方案負載管理員就是要管理特定的解決方案，啟動資訊就會保留做為方案檔的一部分。 若要這樣做，請呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> 方案前一節。  
  
 特定方案負載管理員應該停用自己在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> 事件處理常式，為了避免與其他方案負載管理員的衝突。  
  
 如果您需要方案負載管理員，只保存全域專案載入優先順序 \(比方說，在 \[選項\] 頁面上設定的屬性\)，您可以啟動中的方案載入管理員 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> 保存在方案內容中，設定事件處理常式，然後停用方案負載管理員。  
  
## 處理方案載入事件  
 若要訂閱的方案載入事件，請呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> 啟動您的方案負載管理員。 如果您實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, ，您可以回應不同的專案載入優先順序與相關的事件。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: 這被引發之前開啟方案。 您可以用它來變更專案載入方案中專案的優先順序。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: 解決之道是完全載入，但背景載入的專案開始之前一次之後，就會引發這項目。 比方說，使用者可能存取其負載優先順序是 LoadIfNeeded，專案或方案負載管理員可能已變更專案負載優先權 BackgroundLoad，會啟動該專案的背景載入。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: 這之後就會引發一開始會完全載入方案，以及有解決方案負載管理員。 它也會引發背景載入或視需要載入只要方案已完全載入之後。 在此同時， <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> 就會重新啟動。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: 這是專案 \(或專案\) 載入之前引發。 若要確保在載入專案之前，完成其他背景程序，設定 `pfShouldDelayLoadToNextIdle` 至 **true**。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: 這被引發即將載入專案的批次時。 如果 `fIsBackgroundIdleBatch` 為 true，專案會載入在背景中; 如果 `fIsBackgroundIdleBatch` 為 false，專案要載入同步的使用者要求而，例如使用者如果展開方案總管\] 中的暫止的專案。 您可以實作此執行耗費資源的工作，否則需要進行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterOpenProject%2A>。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: 已載入專案的批次之後，就會引發這項目。  
  
## 偵測及管理方案和專案載入  
 若要偵測專案和方案的載入狀態，請呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> 具有下列值:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` 傳回 `true` 方案及其所有專案是否已載入，否則 `false`。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` 傳回 `true` 如果專案的批次目前正在載入在背景中，否則 `false`。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` 傳回 `true` 如果專案的批次目前正在載入以同步方式導因於使用者命令或其他明確載入，否則 `false`。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` 傳回 `true` 方案目前正在關閉，否則如果 `false`。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` 傳回 `true` 方案目前正在開啟，否則如果 `false`。  
  
 您也可以確保，載入專案和方案 \(無論專案載入優先順序為何\)，藉由呼叫下列方法之一:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: 呼叫這個方法會強制在方法傳回之前載入的方案中的專案。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: 呼叫這個方法會強制在專案 `guidProject` 方法傳回之前載入。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: 呼叫這個方法會強制在專案 `guidProjectID` 方法傳回之前載入。  
  
> [!NOTE]
>  。 根據預設只有專案的需求載入，並載入背景載入優先順序，但如果 <xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS> 旗標會傳遞至方法，所有的專案將會載入標示要明確載入除外。