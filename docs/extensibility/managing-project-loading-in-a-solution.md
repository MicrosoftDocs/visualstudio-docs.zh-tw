---
title: 管理方案中的專案載入 |Microsoft Docs
description: 瞭解開發人員如何藉由建立解決方案負載管理員來減少解決方案載入時間，以及管理專案載入行為。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 425f610e8a473460cb7d9170138521e2e7bee08a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073088"
---
# <a name="manage-project-loading-in-a-solution"></a>管理方案中的專案載入
Visual Studio 的解決方案可以包含大量專案。 預設的 Visual Studio 行為是在方案開啟時載入方案中的所有專案，而不允許使用者存取任何專案，直到全部載入完成為止。 當專案載入的程式持續兩分鐘以上時，會顯示進度列，其中顯示已載入的專案數和專案總數。 使用者可以在具有多個專案的方案中工作時卸載專案，但此程式有一些缺點：卸載的專案不會建立為重建方案命令的一部分，且不會顯示已關閉專案之類型和成員的 IntelliSense 描述。

 開發人員可以藉由建立解決方案載入管理員來減少方案載入時間，以及管理專案載入行為。 解決方案載入管理員可以確保先載入專案，再啟動背景組建、延遲背景載入，直到其他背景工作完成，並執行其他專案負載管理工作為止。

## <a name="create-a-solution-load-manager"></a>建立解決方案負載管理員
 開發人員可以藉由執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> 和建議解決方案載入管理員處於作用中狀態的 Visual Studio，來建立解決方案負載管理員。

### <a name="activate-a-solution-load-manager"></a>啟動解決方案負載管理員
 Visual Studio 在指定的時間僅允許一個解決方案載入管理員，因此當您想要啟用方案載入管理員時，必須建議 Visual Studio。 如果稍後已啟用第二個解決方案載入管理員，您的解決方案載入管理員將會中斷連線。

 您必須取得 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> 服務並設定 [__VSPROPID4。VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) 屬性：

```csharp
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;
object objLoadMgr = this;   //the class that implements IVsSolutionManager
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);
```

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A>當 Visual Studio 關閉時，或透過呼叫 __VSPROPID4 來將不同的封裝視為使用中的方案負載管理員時，就會呼叫方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> [。VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>)屬性。

#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>不同類型方案負載管理員的策略
 您可以根據所要管理的解決方案類型，以不同的方式來執行解決方案載入管理員。

 如果解決方案負載管理員通常是用來管理解決方案載入，則可作為 VSPackage 的一部分來執行。 封裝應該設定為自動載入，方法是 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> 在 VSPackage 上加入值為的 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid> 。 然後可以在方法中啟動解決方案載入管理員 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 。

> [!NOTE]
> 如需自動載入功能套件的詳細資訊，請參閱 [載入 vspackage](../extensibility/loading-vspackages.md)。

 由於 Visual Studio 只會辨識要啟動的最後一個解決方案載入管理員，因此一般解決方案負載管理員應該一律偵測是否有現有的負載管理員，然後再啟用本身。 如果 `GetProperty()` __VSPROPID4 的解決方案服務上呼叫 [。VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) 傳回 `null` 時，沒有使用中的方案負載管理員。 如果它不會傳回 null，請檢查物件是否與您的方案負載管理員相同。

 如果方案載入管理員僅管理幾種類型的解決方案，VSPackage 可以藉由呼叫) 來訂閱者案載入事件 (， <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> 並使用的事件處理常式 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> 來啟動方案載入管理員。

 如果解決方案負載管理員只是為了管理特定的解決方案，則可以藉由呼叫預先方案區段的方式，將啟用資訊保存為方案檔的一部分 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> 。

 特定的解決方案負載管理員應該在事件處理常式中停用本身 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> ，而不會與其他解決方案負載管理員發生衝突。

 如果您只需要方案載入管理員來保存全域專案載入屬性 (例如，在 [選項] 頁面上設定的屬性) ，您可以在事件處理常式中啟用 [方案載入管理員] <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> ，在 [方案屬性] 中保存設定，然後停用方案載入管理員。

## <a name="handle-solution-load-events"></a>處理解決方案載入事件
 若要訂閱者案載入事件，請 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> 在啟用方案載入管理員時呼叫。 如果您執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents> ，您可以回應與不同專案載入屬性相關的事件。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>：在開啟方案之前，會引發此事件。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>：此事件會在解決方案完全載入之後，但在背景專案載入重新開始之前引發。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>：當方案一開始完全載入時，無論是否有解決方案負載管理員，都會引發此事件。 當解決方案完全載入時，它也會在背景載入或要求載入之後引發。 同時， <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> 也會重新開機。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>：此事件會在專案 (或專案的載入) 之前引發。 為了確保在載入專案之前，會先完成其他背景進程，請將設定 `pfShouldDelayLoadToNextIdle` 為 **true**。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>：當即將載入專案批次時，就會引發此事件。 若 `fIsBackgroundIdleBatch` 為 true，則會在背景載入專案; 如果 `fIsBackgroundIdleBatch` 為 false，則會以同步方式將專案載入，以做為使用者要求的結果，例如，如果使用者在方案總管中展開暫止專案。 您可以處理這個事件來執行昂貴的工作，否則必須在中完成 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> 。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>：載入專案批次之後，就會引發此事件。

## <a name="detect-and-manage-solution-and-project-loading"></a>偵測和管理方案和專案載入
 若要偵測專案和方案的載入狀態，請 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> 使用下列值來呼叫：

- [__VSPROPID4。VSPROPID_IsSolutionFullyLoaded](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsSolutionFullyLoaded>)： `var` `true` 如果方案及其所有專案都已載入，則會傳回，否則會傳回 `false` 。

- [__VSPROPID4。VSPROPID_IsInBackgroundIdleLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInBackgroundIdleLoadProjectBatch>)： `var` `true` 如果目前正在背景載入專案批次，則會傳回，否則會傳回 `false` 。

- [__VSPROPID4。VSPROPID_IsInSyncDemandLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInSyncDemandLoadProjectBatch>)： `var` `true` 如果專案的批次因為使用者命令或其他明確的載入而同步載入，則會傳回，否則會傳回 `false` 。

- [__VSPROPID2。VSPROPID_IsSolutionClosing](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2.VSPROPID_IsSolutionClosing>)： `var` `true` 如果方案目前正在關閉，則傳回，否則傳回 `false` 。

- [__VSPROPID。VSPROPID_IsSolutionOpening](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID.VSPROPID_IsSolutionOpening>)： `var` `true` 如果目前正在開啟方案，則會傳回，否則會傳回 `false` 。

您也可以藉由呼叫下列其中一種方法，來確定專案和方案已載入：

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>：呼叫這個方法會強制方案中的專案在方法傳回之前載入。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>：呼叫這個方法會強制載入在 `guidProject` 方法傳回之前載入的專案。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>：呼叫這個方法會強制載入在 `guidProjectID` 方法傳回之前載入的專案。
