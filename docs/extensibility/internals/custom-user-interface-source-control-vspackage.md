---
title: 自訂使用者介面 (來源控制 VS 套件) |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6ef807cef17a6ca3cddfee05ba57ace27e34a9e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708935"
---
# <a name="custom-user-interface-source-control-vspackage"></a>自訂使用者介面 (原始碼管理 VS 套件)
VSPackage 通過 Visual Studio 命令表 *(.vsct*) 檔聲明其功能表項及其預設狀態。 整合[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]式開發環境 (IDE) 以預設狀態顯示選單項,直到載入 VSPackage。 隨後,調用<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>該方法以啟用或禁用功能表項。

 VSPackage 可以設置註冊表項,以便 VSPackage 可以根據命令使用者介面 (UI) 上下文自動載入,儘管通常原始程式碼管理 VSPackage 應按需載入,而不是僅切換到特定的 UI 上下文。 有關**自動載入套件**註冊表項的詳細資訊,請參閱[管理 VS 套件](../../extensibility/managing-vspackages.md)。

## <a name="vspackage-ui"></a>VSPackage UI
 原始碼管理套件作為 VSPackage 實現,不使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]中的任何 UI。 每個原始程式碼管理 VSPackage 必須指定其自己的 UI 元素,如選單項、選單組、工具視窗、工具列和任何所需的 UI 來設置特定於原始碼管理 VSPackage 的選項。 這些 UI 元素可以靜態或動態啟用。 靜態 UI 元素在 *.vsct*檔中定義,無論是否載入 VS 套件,都顯示。 動態 UI 元素可能可見,具體取決於特定命令 UI<xref:EnvDTE.Constants.vsContextNoSolution>上下文(<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>如 )或由於對方法調用的結果。 動態 UI 元素的可見性符合延遲載入 VS 套件的策略。

## <a name="ui-constraints-on-source-control-vspackages"></a>原始碼管理 VSPackages 的 UI 規範
 由於源控件 VSPackage 在載入後無法從 IDE 中刪除,因此 VSPackage 必須能夠進入非活動狀態。 當 VS 包收到其不再處於活動狀態的通知時,VS 包將禁用其 UI 並忽略任何外部 IDE 交互。 當 VSPackage 不處於活動<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>狀態時 ,VSPackage 的方法的實現應隱藏命令。

 每個原始程式碼管理 VSPackage`IVsSccProvider`都必須 實現介面。 介面上的兩種方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A><xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>和 必須由 VSPackage 實現。

 原始碼管理 VSPackage 可能已訂閱了各種 IDE 事件<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>,<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>這些事件由、 等實現。 此外,VSPackage 可能已實現啟用註冊表的回調介面<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>, 例如 。 這些介面都必須在非活動時被忽略。

 下面的清單顯示受原始碼管理 VSPackage 的活動狀態影響的介面:

- 跟蹤項目文件事件。

- 解決方案事件。

- 解決方案持久性介面。 當處於非活動狀態時,包不應寫入 *.sln*和 *.suo*檔。

- 屬性擴展器。

  當原始碼<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>管理<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>VSPackage 處於非活動狀態時,不會呼叫所需的 和以及與原始程式碼管理關聯的任何可選介面。

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]當 IDE[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]啟動 時,將指令 UI 上下文設定為目前預設源控制項 VSPackage ID 的 ID。 這將導致活動源控件 VSPackage 的靜態 UI 顯示在 IDE 中,而無需實際載入 VSPackage。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]暫停 VSPackage 在對 VSPackage 進行[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]任何呼<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>叫之前 透過註冊 。

  下表描述了有關[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE如何隱藏不同UI項的具體詳細資訊。

| UI 項 | 描述 |
| - | - |
| 功能表與工具列 | 原始碼管理套件必須在 *.vsct*檔案的[可見性約束](../../extensibility/visibilityconstraints-element.md)部分中將初始選單和工具列可見性狀態設置為原始碼管理包 ID。 這使[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 能夠適當地設置功能表項的狀態,而無需載入 VSPackage<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>並調用 方法的實現。 |
| 工具視窗 | 原始碼管理 VSPackage 隱藏它位於非活動狀態時擁有的任何工具視窗。 |
| 原始碼管理 VSPackage 特定選項頁 | 註冊表項**HKLM_SOFTWARE_Microsoft_VisualStudio_X.Y_ToolsOptionsPages_可見性CmdUIContexts**允許 VSPackage 設置它需要顯示其選項頁的上下文。 必須使用此密鑰下的註冊表項使用原始程式碼管理服務的服務ID (SID)併為其分配DWORD值1。 每當在註冊源代碼管理 VSPackage 的上下文中發生 UI 事件時,如果 VSPackage 處於活動狀態,則將調用它。 |

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>
- <xref:EnvDTE.Constants.vsContextNoSolution>
- [管理 VSPackages](../../extensibility/managing-vspackages.md)
