---
title: 在解決方案中管理項目載入 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 21cd5e7e557e795db49aea7a14e8e4cc7caa0422
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702724"
---
# <a name="manage-project-loading-in-a-solution"></a>在解決方案中管理項目載入
可視化工作室解決方案可以包含大量專案。 預設 Visual Studio 行為是在打開解決方案時載入解決方案中的所有專案,並且不允許使用者存取任何專案,直到這些專案都載入完。 當專案載入過程將持續兩分鐘以上時,將顯示一個進度條,顯示載入的項目數和專案總數。 用戶可以在具有多個專案的解決方案中卸載專案,但此過程有一些缺點:卸載的專案不是作為重建解決方案命令的一部分構建的,並且不會顯示已關閉專案的類型和成員的 IntelliSense 描述。

 開發人員可以透過創建解決方案載入管理器來縮短解決方案載入時間並管理專案載入行為。 解決方案載入管理器可以在啟動後台生成之前確保載入專案,將後台載入延遲到其他後台任務完成,並執行其他專案載入管理任務。

## <a name="create-a-solution-load-manager"></a>建立解決方案負載管理員
 開發人員可以通過<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager>實現 並通知 Visual Studio 解決方案負載管理器處於活動狀態來創建解決方案負載管理器。

### <a name="activate-a-solution-load-manager"></a>啟動解決方案負載管理員
 Visual Studio 在給定時間只允許一個解決方案載入管理員,因此當您要啟動解決方案載入管理員時,您必須建議 Visual Studio。 如果稍後啟動第二個解決方案負載管理器,則解決方案負載管理器將斷開連接。

 您必須獲得服務<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>並設置[__VSPROPID4。VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>)屬性:

```csharp
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;
object objLoadMgr = this;   //the class that implements IVsSolutionManager
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);
```

 當<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A>Visual Studio 關閉時,或者當其他包透過呼叫__VSPROPID4接管為活動解決方案負載管理員時,<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A>將呼叫該方法[。VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>)屬性。

#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>不同類型的解決方案負載管理員的原則
 您可以以不同的方式實施解決方案負載管理器,具體取決於它們要管理的解決方案類型。

 如果解決方案負載管理器用於管理解決方案載入,則可以將其作為 VSPackage 的一部分實現。 應透過 VSPackage<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>上的 設定為自動載入,其<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>值為 。 然後可以在<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>方法中激活解決方案負載管理器。

> [!NOTE]
> 有關自動載入套件的詳細資訊,請參閱載[入 VS 套件](../extensibility/loading-vspackages.md)。

 由於 Visual Studio 只識別要啟動的最後一個解決方案負載管理器,因此一般解決方案負載管理器在啟動自身之前應始終檢測是否存在現有負載管理器。 如果調用`GetProperty()`解決方案服務[__VSPROPID4。VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>)返回`null`,沒有活動的解決方案負載管理器。 如果未返回 null,請檢查物件是否與解決方案負載管理器相同。

 如果解決方案載入管理器僅用於管理幾種類型的解決方案,則 VS 套件可以訂閱解決方案載入事件(透過<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>呼叫),並使用事件<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>處理程式 來啟動解決方案載入管理器。

 如果解決方案負載管理器僅用於管理特定解決方案,則啟動資訊可以通過調<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>用 解決方案前部分作為解決方案檔的一部分進行保留。

 特定解決方案負載管理器應在<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A>事件處理程式中停用自身,以免與其他解決方案負載管理器發生衝突。

 如果只需要一個解決方案載入管理器來保留全域專案載入屬性(例如,在 Options 頁上設置的屬性),則<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>可以在事件處理程式中啟動解決方案載入管理器,在解決方案屬性中保留設置,然後停用解決方案載入管理器。

## <a name="handle-solution-load-events"></a>處理解決方案載入事件
 要訂閱解決方案載入事件,請啟動<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>解決方案載入管理器時調用。 如果實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>,則可以回應與不同專案載入屬性相關的事件。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>:在打開解決方案之前將觸發此事件。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>:此事件在解決方案完全載入後觸發,但在後台專案載入重新開始之前。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: 無論是否有解決方案負載管理器,此事件是在最初完全載入解決方案後觸發的。 每當解決方案完全載入時,也會在後台載入或需求載入後觸發它。 同時,<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid>重新啟動。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>:此事件在載入專案(或專案)之前觸發。 為了確保在載入專案之前完成其他後台行程,將設置為`pfShouldDelayLoadToNextIdle` **true**。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>:當一批項目即將載入時,將觸發此事件。 如果`fIsBackgroundIdleBatch`為 true,則專案將在後台載入;如果`fIsBackgroundIdleBatch`為 false,則專案將由於使用者請求而同步載入,例如,如果使用者在解決方案資源管理器中展開掛起的專案。 您可以處理此事件,以執行昂貴的工作,否則需要在中<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>完成。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>:載入一批專案後,將觸發此事件。

## <a name="detect-and-manage-solution-and-project-loading"></a>偵測及管理解決方案和專案載入
 為了偵測項目和解決方案的負載狀態,使用以下值呼<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A>叫 :

- [__VSPROPID4VSPROPID_IsSolutionFullyLoaded](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsSolutionFullyLoaded>) `var` `true`: 如果載入解決方案及其所有專案,則傳`false`回,否則將傳回 。

- [__VSPROPID4VSPROPID_IsInBackgroundIdleLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInBackgroundIdleLoadProjectBatch>) `var` `true`: 如果目前在後台載入一批專案,則傳回`false`,否則傳回 。

- [__VSPROPID4VSPROPID_IsInSyncDemandLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInSyncDemandLoadProjectBatch>) `var` `true`: 如果一批項目當前由於使用者命令或其他顯式載入而同步載入,則返回`false`,否則將返回。

- [__VSPROPID2。VSPROPID_IsSolutionClosing](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2.VSPROPID_IsSolutionClosing>) `var` `true`: 如果解決方案目前正在關閉,則`false`傳回, 否則將傳回 。

- [__VSPROPIDVSPROPID_IsSolutionOpening](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID.VSPROPID_IsSolutionOpening>) `var` `true`: 如果目前正在開啟解決方案,則`false`傳回, 否則會傳回 。

還可以透過調用以下方法之一來確保載入專案和解決方案:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>調用此方法強制解決方案中的專案在方法返回之前載入。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>:調用此方法強制 中的專案`guidProject`在 方法返回之前載入。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>:調用此方法強制專案在`guidProjectID`方法返回之前載入。
