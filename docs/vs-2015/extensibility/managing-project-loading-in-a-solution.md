---
title: 管理方案中的專案載入 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0ce2f80aa50c3222797d925a888e5c004b21512d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58941230"
---
# <a name="managing-project-loading-in-a-solution"></a>管理方案中的專案載入
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 方案可以包含大量的專案。 Visual Studio 預設會在開啟解決方案時，階段中載入方案中的所有專案，而且不允許使用者存取的任何專案，直到它們全部完成載入。 當專案載入的程序會持續超過兩分鐘時，會顯示進度列，顯示載入的專案數目及專案的總數。 使用者可以同時使用多個專案的方案中工作卸載的專案，但此程序有一些缺點： 已卸載的專案並不是建置為重建方案 命令的一部分，並關閉 IntelliSense 描述的型別和成員專案不會顯示。  
  
 開發人員可以減少方案載入時間，並管理由管理員建立的解決方案載入載入行為的專案。 解決方案負載管理員可以設定不同的專案載入特定專案或專案類型的優先順序、 確定載入專案時，會開始在背景建置之前，延遲背景載入其他背景工作必須等到完成後，和執行其他專案負載的管理工作。  
  
## <a name="project-loading-priorities"></a>專案載入優先順序  
 Visual Studio 會定義四個不同的專案載入優先順序：  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority> （預設值）： 開啟解決方案時，會以非同步方式載入專案。 如果已開啟方案之後卸載的專案上設定此優先順序，會載入專案，在下一步 的閒置時間點。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>： 在背景中，讓使用者能夠存取的專案，而不需要等候，直到已載入所有專案載入方案開啟時，會都載入專案。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>： 在存取時，會載入專案。 當使用者展開專案節點，在 [方案總管] 中的，當檔案屬於專案開啟時的方案就會開啟，因為它是在開啟的文件清單中 （保存在方案的使用者選項檔），或存取專案的另一個專案也就是載入的專案上具有相依性。 開始建置程序; 前不會自動載入這種類型的專案解決方案負載管理員會負責確保會載入所有必要的專案。 開始尋找/取代檔案中，在整個解決方案之前，應該也可載入這些專案。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>： 會為除非使用者明確要求，否則無法載入的專案。 明確卸載專案時，這會是大小寫。  
  
## <a name="creating-a-solution-load-manager"></a>管理員建立的解決方案載入  
 開發人員可以建立解決方案載入管理員藉由實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager>及建議 Visual Studio 方案負載管理員使用中。  
  
#### <a name="activating-a-solution-load-manager"></a>啟用解決方案負載管理員  
 Visual Studio 可讓一位方案負載管理員在指定的時間，因此當您想要啟用您的解決方案載入時，您必須告知 Visual Studio 管理員。 如果第二個方案負載管理員啟動之後，將會中斷您的方案負載管理員。  
  
 您必須取得<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>服務，並設定<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>屬性：  
  
```csharp  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;  
object objLoadMgr = this;   //the class that implements IVsSolutionManager  
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
#### <a name="implementing-ivssolutionloadmanager"></a>實作 IVsSolutionLoadManager  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A>開啟解決方案的程序期間呼叫方法。 若要實作這個方法，您使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport>服務來設定您想要管理的專案類型的負載優先順序。 例如，下列程式碼會設定在背景中載入 C# 專案類型：  
  
```csharp  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}");  
pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A>關閉 Visual Studio 或不同的封裝已接管作為使用中的方案負載管理員藉由呼叫時，會呼叫方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A>與<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>屬性。  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>負載管理員針對不同種類的解決方案的策略。  
 您可以實作解決方案負載管理員，以不同的方式，根據它們為了管理的解決方案的類型。  
  
 如果方案負載管理員就是要管理解決方案載入一般情況下，它可以實作 VSPackage 的一部分。 封裝應該設定為自動載入，加上<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>值為 vspackage <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>。 然後可以在中啟用方案負載管理員<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>方法。  
  
> [!NOTE]
>  如需有關自動載入封裝的詳細資訊，請參閱[載入 Vspackage](../extensibility/loading-vspackages.md)。  
  
 Visual Studio 可以辨識只有最後一個方案負載管理員啟動，因為一般解決方案負載管理員應該一律會偵測是否有現有的負載管理員之後再啟動本身。 如果方案服務之呼叫 GetProperty()<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>傳回`null`，沒有使用中的方案負載管理員。 如果它不會傳回 null，請檢查物件是否與您的方案負載管理員相同。  
  
 如果方案負載管理員就是要管理只有幾種類型的解決方案，VSPackage 可以訂閱方案載入事件 (藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>)，並使用事件處理常式，如<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>啟用方案負載管理員。  
  
 如果方案負載管理員就是要管理特定的解決方案，可保存啟用資訊做為方案檔的一部分。 若要這樣做，請呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>方案前一節。  
  
 特定解決方案負載管理員應該停用自己在<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A>事件處理常式，以避免衝突與其他解決方案負載管理員。  
  
 如果您需要解決方案負載管理員，來保存全域專案載入優先順序 （比方說，在 [選項] 頁面上設定的屬性），您可以啟用中的方案載入管理員僅<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents2.OnAfterOpenProject%2A>事件處理常式，保存在方案內容中，設定然後停用方案負載管理員。  
  
## <a name="handling-solution-load-events"></a>事件處理解決方案載入  
 若要訂閱的方案載入事件，請呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>當您啟用您的方案負載管理員。 如果您實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>，您可以回應不同的專案載入優先順序與相關的事件。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>：開啟方案之前，會引發這項目。 您可以使用它來變更專案載入方案中專案的優先順序。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>：解決方法是完全載入，但是背景之前載入的專案重新開始之後，就會引發這項目。 例如，使用者可能已存取負載優先順序是 LoadIfNeeded，專案或方案負載管理員可能已變更的專案載入優先順序為 BackgroundLoad，則會開始該專案的背景載入。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>：這之後就會引發一開始會完全載入方案時，有解決方案負載管理員。 它也會引發之後背景負載或隨選載入解決方案會變得完全載入時。 在此同時，<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid>就會重新啟動。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>：這會引發之前載入的專案 （或專案）。 若要確保載入專案之前，完成其他背景處理程序，將`pfShouldDelayLoadToNextIdle`要 **，則為 true**。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>：這會在即將載入專案的批次時引發。 如果`fIsBackgroundIdleBatch`為 true，如果專案是在背景; 載入`fIsBackgroundIdleBatch`為 false，是要載入以同步方式要求的結果使用者，例如使用者如果展開方案總管 中的擱置專案的專案。 您也可以將此選項以執行耗費資源的工作，否則會需要在實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>：已載入專案的批次之後，就會引發這項目。  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>偵測及管理方案和專案載入  
 若要偵測的專案和方案載入狀態，請呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A>具有下列值：  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>:`var`會傳回`true`方案和其所有的專案已載入，否則如果`false`。  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>:`var`會傳回`true`如果批次的專案目前正在載入在背景中，否則`false`。  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>:`var`會傳回`true`如果批次的專案目前正在載入以同步方式導因使用者命令或其他明確的負載，否則`false`。  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>:`var`會傳回`true`解決方案目前正在關閉，否則如果`false`。  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>:`var`會傳回`true`解決方案目前正在開啟，否則如果`false`。  
  
  您也可以確保專案和方案載入 （不論專案載入優先順序為何），藉由呼叫下列方法之一：  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>： 呼叫這個方法會強制在方法傳回之前載入的方案中的專案。  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>： 呼叫這個方法會強制在專案`guidProject`載入方法傳回之前。  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>： 呼叫這個方法會強制在專案`guidProjectID`載入方法傳回之前。  
  
> [!NOTE]
>  。 根據預設只需要在專案載入，並會載入背景負載優先順序，但如果<xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS>旗標會傳遞至方法中，將會載入所有專案，但標示要明確載入的項目除外。
