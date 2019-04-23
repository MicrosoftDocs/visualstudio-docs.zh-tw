---
title: 管理方案中的專案載入 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7a383096d164f1b08e2411a7bc808e96f8a6262e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60061303"
---
# <a name="manage-project-loading-in-a-solution"></a>管理方案中的專案載入
Visual Studio 方案可以包含大量的專案。 Visual Studio 預設會在開啟解決方案時，階段中載入方案中的所有專案，而且不允許使用者存取的任何專案，直到它們全部完成載入。 當專案載入的程序會持續超過兩分鐘時，會顯示進度列，顯示載入的專案數目及專案的總數。 使用者可以同時使用多個專案的方案中工作卸載的專案，但此程序有一些缺點： 已卸載的專案並不是建置為重建方案 命令的一部分，並關閉 IntelliSense 描述的型別和成員專案不會顯示。

 開發人員可以減少方案載入時間，並管理由管理員建立的解決方案載入載入行為的專案。 解決方案負載管理員可以確定載入專案時，會先在背景建置、 延遲背景載入其他背景工作必須等到完成後，以及執行其他專案負載的管理工作。

## <a name="create-a-solution-load-manager"></a>建立方案負載管理員
 開發人員可以建立解決方案載入管理員藉由實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager>及建議 Visual Studio 方案負載管理員使用中。

### <a name="activate-a-solution-load-manager"></a>啟用解決方案負載管理員
 Visual Studio 可讓一位方案負載管理員在指定的時間，因此當您想要啟用您的解決方案載入時，您必須告知 Visual Studio 管理員。 如果第二個方案負載管理員啟動之後，將會中斷您的方案負載管理員。

 您必須取得<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>服務，並設定[__VSPROPID4。VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>)屬性：

```csharp
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;
object objLoadMgr = this;   //the class that implements IVsSolutionManager
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);
```

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A>關閉 Visual Studio 或不同的封裝已接管作為使用中的方案負載管理員藉由呼叫時，會呼叫方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A>使用[__VSPROPID4。VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>)屬性。

#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>負載管理員針對不同種類的解決方案的策略。
 您可以實作解決方案負載管理員，以不同的方式，根據它們為了管理的解決方案的類型。

 如果方案負載管理員就是要管理解決方案載入一般情況下，它可以實作 VSPackage 的一部分。 封裝應該設定為自動載入，加上<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>值為 vspackage <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>。 然後可以在中啟用方案負載管理員<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>方法。

> [!NOTE]
>  如需有關自動載入封裝的詳細資訊，請參閱[載入 Vspackage](../extensibility/loading-vspackages.md)。

 Visual Studio 可以辨識只有最後一個方案負載管理員啟動，因為一般解決方案負載管理員應該一律會偵測是否有現有的負載管理員之後再啟動本身。 如果呼叫`GetProperty()`上的方案服務[__VSPROPID4。VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>)傳回`null`，沒有使用中的方案負載管理員。 如果它不會傳回 null，請檢查物件是否與您的方案負載管理員相同。

 如果方案負載管理員就是要管理只有幾種類型的解決方案，VSPackage 可以訂閱方案載入事件 (藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>)，並使用事件處理常式，如<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>啟用方案負載管理員。

 如果方案負載管理員就是要管理特定的解決方案，啟用資訊可以保存方案檔的一部分呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>方案前一節。

 特定解決方案負載管理員應該停用自己在<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A>事件處理常式，以避免衝突與其他解決方案負載管理員。

 如果您需要解決方案負載管理員，來保存全域專案載入屬性 （例如，設定選項 頁面上的屬性），您可以啟用中的方案載入管理員僅<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>事件處理常式，保存在方案內容中，設定然後停用方案負載管理員。

## <a name="handle-solution-load-events"></a>處理方案負載事件
 若要訂閱的方案載入事件，請呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>當您啟用您的方案負載管理員。 如果您實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>，您可以回應不同的專案載入屬性與相關的事件。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>：開啟方案之前，會引發此事件。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>：之後，方案已完全載入，但在背景之前載入的專案重新開始，將引發此事件。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>：有解決方案負載管理員之後一開始會完全載入方案時，, 會引發此事件。 它也會引發之後背景負載或隨選載入解決方案會變得完全載入時。 在此同時，<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid>就會重新啟動。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>：載入專案 （或專案） 之前，會引發此事件。 若要確保載入專案之前，完成其他背景處理程序，將`pfShouldDelayLoadToNextIdle`要 **，則為 true**。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>：即將載入專案的批次時，會引發此事件。 如果`fIsBackgroundIdleBatch`為 true，如果專案是在背景; 載入`fIsBackgroundIdleBatch`為 false，是要載入以同步方式要求的結果使用者，例如使用者如果展開方案總管 中的擱置專案的專案。 您可以處理這個事件來執行耗費資源的工作，否則會需要在<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>：已載入專案的批次後，會引發此事件。

## <a name="detect-and-manage-solution-and-project-loading"></a>偵測及管理方案和專案載入
 若要偵測的專案和方案載入狀態，請呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A>具有下列值：

- [__VSPROPID4。VSPROPID_IsSolutionFullyLoaded](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsSolutionFullyLoaded>):`var`會傳回`true`方案和其所有的專案已載入，否則如果`false`。

- [__VSPROPID4。VSPROPID_IsInBackgroundIdleLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInBackgroundIdleLoadProjectBatch>):`var`會傳回`true`如果批次的專案目前正在載入在背景中，否則`false`。

- [__VSPROPID4。VSPROPID_IsInSyncDemandLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInSyncDemandLoadProjectBatch>):`var`會傳回`true`如果批次的專案目前正在載入以同步方式導因使用者命令或其他明確的負載，否則`false`。

- [__VSPROPID2。VSPROPID_IsSolutionClosing](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2.VSPROPID_IsSolutionClosing>):`var`會傳回`true`解決方案目前正在關閉，否則如果`false`。

- [__VSPROPID。VSPROPID_IsSolutionOpening](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID.VSPROPID_IsSolutionOpening>):`var`會傳回`true`解決方案目前正在開啟，否則如果`false`。

您也可以確保載入專案和方案，藉由呼叫下列方法之一：

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>： 呼叫這個方法會強制在方法傳回之前載入的方案中的專案。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>： 呼叫這個方法會強制在專案`guidProject`載入方法傳回之前。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>： 呼叫這個方法會強制在專案`guidProjectID`載入方法傳回之前。
