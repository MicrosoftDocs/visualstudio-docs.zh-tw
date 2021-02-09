---
title: 自訂消費者介面 (原始檔控制 VSPackage) |Microsoft Docs
description: 瞭解如何使用原始檔控制 VSPackage 指定 UI 專案，在 Visual Studio 中建立自訂使用者介面 (UI) 。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 97c82254516c78a3aff9884e91e44adc45b95981
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902986"
---
# <a name="custom-user-interface-source-control-vspackage"></a>自訂使用者介面 (原始檔控制 VSPackage) 
VSPackage 會透過 Visual Studio 的命令資料表 (*. .vsct*) 檔來宣告其功能表項目和其預設狀態。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式開發環境 (IDE) 會顯示預設狀態下的功能表項目，直到載入 VSPackage 為止。 接著 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 會呼叫方法來啟用或停用功能表項目。

 VSPackage 可以設定登錄機碼，以便根據命令使用者介面 (UI) 內容來自動載入 VSPackage，不過通常原始檔控制 VSPackage 應該視需要載入，而不只是切換至特定的 UI 內容。 如需 **AutoLoadPackages** 登錄機碼的詳細資訊，請參閱 [管理 vspackage](../../extensibility/managing-vspackages.md)。

## <a name="vspackage-ui"></a>VSPackage UI
 原始檔控制封裝會實作為 VSPackage，而且不會使用中的任何 UI [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 每個原始檔控制 VSPackage 都必須指定自己的 UI 元素，例如功能表項目、功能表群組、工具視窗、工具列，以及設定原始檔控制 VSPackage 特定選項的任何必要 UI。 這些 UI 元素可以靜態或動態方式啟用。 靜態 UI 元素是在 *.vsct* 檔案中定義，而且會顯示 VSPackage 是否已載入。 根據特定的命令 UI 內容（例如 <xref:EnvDTE.Constants.vsContextNoSolution> ）或呼叫方法的結果，可能會顯示動態 UI 元素 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 。 動態 UI 元素的可見度符合延遲載入 Vspackage 的策略。

## <a name="ui-constraints-on-source-control-vspackages"></a>原始檔控制 Vspackage 上的 UI 條件約束
 因為原始檔控制 VSPackage 在載入後無法從 IDE 中移除，所以 VSPackage 必須能夠進入非使用中狀態。 當 VSPackage 收到不再使用的通知時，VSPackage 會停用其 UI，並忽略任何外部 IDE 互動。 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>當 VSPackage 非使用中時，VSPackage 的方法的執行應該會隱藏命令。

 每個原始檔控制 VSPackage 都必須執行 `IVsSccProvider` 介面。 介面上的兩個方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A> 都必須由 VSPackage 執行。

 原始檔控制 VSPackage 可能已訂閱各種 IDE 事件，這些事件是由 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> 、等等所執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> 。 此外，VSPackage 可能已執行啟用登錄的回呼介面，例如 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> 。 這些介面必須在非使用中時全部忽略。

 下列清單顯示受原始檔控制 VSPackage 之作用中狀態影響的介面：

- 追蹤專案檔案事件。

- 解決方案事件。

- 解決方案持續性介面。 非使用中時，套件不應寫入 *.sln* 和 *.suo* 檔案中。

- 屬性擴充項。

  <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> 當原始檔控制 VSPackage 為非使用中時，不會呼叫所需的和以及與原始檔控制相關聯的任何選用介面。

  當 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 啟動時，會 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 將命令 UI 內容設定為目前預設原始檔控制 VSPackage 識別碼的識別碼。 這會導致作用中原始檔控制 VSPackage 的靜態 UI 出現在 IDE 中，而不會實際載入 VSPackage。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 在對 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> VSPackage 進行任何呼叫之前，暫停 VSPackage 透過進行註冊。

  下表說明 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 如何隱藏不同的 UI 專案的特定詳細資料。

| UI 專案 | Description |
| - | - |
| 功能表與工具列 | 原始檔控制封裝必須在 *.vsct* 檔案的 [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md)區段中，將初始功能表和工具列可見度狀態設定為原始檔控制封裝識別碼。 這可讓 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 適當地設定功能表項目的狀態，而不需要載入 VSPackage 和呼叫方法的執行 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 。 |
| 工具視窗 | 當它變成非使用中時，原始檔控制 VSPackage 會隱藏它所擁有的任何工具視窗。 |
| 原始檔控制 VSPackage 特定的選項頁面 | 登錄機碼 **HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUICoNtexts** 可讓 VSPackage 設定需要顯示其 [選項] 頁面的內容。 您必須使用原始檔控制服務的服務識別碼 (SID) 來建立此機碼底下的登錄專案，並為其指派 DWORD 值1。 每當 UI 事件發生在與原始檔控制 VSPackage 的內容中時，就會呼叫 VSPackage （如果它是使用中）。 |

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>
- <xref:EnvDTE.Constants.vsContextNoSolution>
- [管理 VSPackages](../../extensibility/managing-vspackages.md)
