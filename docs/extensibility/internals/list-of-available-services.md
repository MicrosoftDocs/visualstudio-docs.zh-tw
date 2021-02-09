---
title: 可用的服務清單 |Microsoft Docs
description: 查看 Visual Studio 和 Visual Studio SDK 支援的可用服務清單，包括用來取得每個服務介面的服務 Guid。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, Visual Studio
- Visual Studio, services
ms.assetid: 724eb24b-b87c-4971-a2e7-adee7afc03b2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b00eb3e410c7fd3d10d2aef7fcfbf637ea04e41a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839569"
---
# <a name="list-of-available-services"></a>可用服務清單

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 和 Visual Studio SDK 支援下列服務。 有些套件會提供自己的服務（此處未列出），例如，語言服務沒有單一服務 GUID。 您必須使用語言的名稱，才能在登錄中尋找語言服務的 GUID。

使用此處所列或從其他來源取得的服務 Guid (例如，語言服務) 來取得每個服務所顯示的主要介面或介面。

## <a name="the-services"></a>服務

| 服務 | 介面 | Visual Studio | Visual Studio 2005 | 描述 |
| - | - |---------------|--------------------| - |
| <xref:Microsoft.VisualStudio.OLE.Interop.SBindHost> | <xref:Microsoft.VisualStudio.OLE.Interop.IBindHost> | 是 | 是 | 由 Vspackage 用來 <xref:Microsoft.VisualStudio.OLE.Interop.IBindHost> 從 ActiveX 控制項取得介面，以加速非同步資料傳輸。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SDTE> | <xref:EnvDTE.DTE> | 否 | 是 | 取得用於自動化之 DTE) 物件的設計階段擴充性 (。<br /><br /> C/C + + 識別碼： SID_SDTE |
| <xref:Microsoft.VisualStudio.Shell.Interop.SCodeNavigate> | <xref:Microsoft.VisualStudio.Shell.Interop.ICodeNavigate> | 是 | 是 | 由表單設計工具執行，以顯示控制項的預設事件處理常式。 |
| <xref:Microsoft.VisualStudio.OLE.Interop.SContainerDispatch> | IDispatch | 是 | 是 | 讓 VSPackage 存取另一個 VSPackage 或控制項的自動化介面。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SExtendedTypeLib> | <xref:Microsoft.VisualStudio.Shell.Interop.IExtendedTypeLib> | 是 | 是 | 讓 VSPackage 加入或建立延伸類型程式庫。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SDirList> | <xref:Microsoft.VisualStudio.Shell.Interop.IDirList> | 否 | 是 | 提供容器的名稱清單存取權;例如，如 [**查詢**] 下拉式清單中的 [**尋找和取代**] 對話方塊所示，要搜尋的目錄清單。 <xref:Microsoft.VisualStudio.Shell.Interop.IDirList>可以讀取和寫入物件。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SIVsPackageDynamicToolOwner> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwner> | 是 | 是 | 讓 VSPackage 能夠以動態方式顯示或隱藏自己的工具視窗。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SLicensedClassManager> | <xref:Microsoft.VisualStudio.Shell.Interop.ILicensedClassManager> | 是 | 是 | 藉 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 由指定授權金鑰清單，讓 VSPackage 向其指出所需的類別。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> | <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> | 是 | 是 | 讓 VSPackage 存取登錄區（相對於本機登錄區） [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 |
| <xref:Microsoft.VisualStudio.OLE.Interop.SOleComponentManager> | <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager> | 是 | 是 | 提供元件協調服務，例如訊息迴圈、鍵盤迴圈和事件通知。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> | 是 | 是 | 讓 VSPackage 存取各種使用者介面 (UI) 的元素 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，例如說明、狀態列和 ui 事件。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SOleInPlaceComponent> | <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> | 是 | 是 | 讓 VSPackage 整合其 UI 與的 UI [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SOleInPlaceComponentSite> | <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentSite> | 是 | 是 | 讓 VSPackage 控制工具特有的 UI 變更。 |
| <xref:Microsoft.VisualStudio.OLE.Interop.SOleUndoManager> | <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> | 是 | 是 | 讓 VSPackage 存取容器的復原管理員，以參與該容器的復原堆疊，或存取該容器的復原堆疊。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService> | <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> | 是 | 是 | 讓 VSPackage 能夠提供自己的服務。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SProfferTypeLib> | <xref:Microsoft.VisualStudio.Shell.Interop.IProfferTypeLib> | 是 | 是 | 可讓表單設計工具將類型程式庫設為可供參考。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> | <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> | 是 | 是 | 提供選取專案容器中選取專案的存取權。 由表單設計工具所使用。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SUIHostCommandDispatcher> | <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> | 是 | 是 | 讓 VSPackage 參與命令處理常式鏈，並代表整合式開發環境 (IDE) 或本身來處理命令。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SUIHostLocale> | <xref:Microsoft.VisualStudio.Shell.Interop.IUIHostLocale> | 是 | 是 | 提供對主機的 UI 地區設定資訊的存取。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> | 否 | 是 | 當開啟記錄功能時，可讓 VSPackage 記錄高階訊息。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsAddProjectItemDlg> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg> | 是 | 是 | 提供 [ **加入專案** 專案] 對話方塊的存取權，讓 vspackage 能夠執行自己的 [ **加入專案** ] 功能表選項。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsAddWebReferenceDlg> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg> | 是 | 是 | 顯示 [ **加入參考** ] 對話方塊。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> | 是 | 是 | 讓 VSPackage 判斷是否已為 devenv.exe 指定命令列參數。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsCallBrowser> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsCallBrowser> | 否 | 是 | 讓 VSPackage 建立用於調試的新 **呼叫瀏覽器** 。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsClassView> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsClassView> | 是 | 是 | 讓 VSPackage 同步處理 **類別檢視** 與特定物件。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsCmdNameMapping> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsCmdNameMapping> | 是 | 是 | 提供將命令名稱對應至 Guid 和後端的支援，以及判斷所有可用命令和名稱的名稱。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsCodeDefView> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsCodeDefView> | 否 | 是 | 讓 VSPackage 操作程式 **代碼定義視圖**。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsCodeShareHandler> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsCodeShareHandler> | 是 | 是 | 內部服務。 請勿使用。 |
| <xref:Microsoft.VisualStudio.TextManager.Interop.SVsCodeWindow> | <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> | 是 | 是 | 提供可包含一或多個檔之程式碼視窗的存取權。 |
| <xref:Microsoft.VisualStudio.TextManager.Interop.SVsCodeWindowManager> | <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> | 是 | 是 | 讓 VSPackage 將變更新增至程式碼視窗，例如下拉清單欄。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsCommandWindow> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommandWindow><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommandWindow2> | 是 | 是 | 讓 VSPackage 透過 **命令視窗** 執行命令，並與 **命令視窗** 互動。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsCommandWindowsCollection> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommandWindowsCollection> | 否 | 是 | 讓 VSPackage 操作所維護的 **命令** 視窗清單 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsComplusLibrary> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibraryReferenceManager> | 是 | 是 | 讓 VSPackage 能夠將流覽資訊提供給 **物件瀏覽器**。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsComponentSelectorDlg> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsComponentSelectorDlg> | 否 | 是 | 讓 VSPackage 支援 [ **加入參考** ] 選項，讓使用者選取要加入至專案的外部元件。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsComponentSelectorDlg2> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsComponentSelectorDlg2> | 否 | 是 | 讓 VSPackage 支援 [ **加入參考** ] 選項，讓使用者選取要加入至專案的外部元件。 此版本的對話方塊允許預先填入元件清單，然後才會顯示它。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsConfigurationManagerDlg> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsConfigurationManagerDlg> | 否 | 是 | 顯示 [ **設定管理員** ] 對話方塊。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject> | 否 | 是 | 讓 VSPackage 建立包含其他專案集合的專案。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsDebuggableProtocol> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProtocol> | 是 | 是 | 讓 VSPackage 更新 IDE 用來啟動特定 debug 引擎的可調試通訊協定清單。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsDebugLaunch> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugLaunch> | 是 | 是 | 啟用 VSPackage 以支援啟動偵錯工具。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsDiscoveryService> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsDiscoveryService> | 是 | 是 | 可讓 VSPackage 建立探索會話，以用來探索 Web 服務。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsEnumHierarchyItemsFactory> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumHierarchyItemsFactory> | 是 | 是 | 提供 factory，以建立 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumHierarchyItemsFactory> 用來列舉指定階層 (專案) 的物件。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsErrorList> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsErrorList> | 否 | 是 | 提供其他方法來操作 [ **組建錯誤清單** ] 工作視窗。 具體而言，會將 **組建錯誤清單** 工作視窗帶入 forefront，並強制顯示所有錯誤。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager> | 是 | 是 | 提供對目前方案之 **其他** 檔案專案節點的存取。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChange> | | 是 | 是 | 已過時。 請改用 `SVsFileChangeEx` 服務。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> | 是 | 是 | 可讓 VSPackage 取得 IDE 所觸發的各種檔案變更事件的存取權。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsFilterAddProjectItemDlg> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> | 是 | 是 | 讓 VSPackage 篩選 [ **加入專案** ] 對話方塊中出現的專案。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsFilterKeys> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterKeys> | 是 | 是 | 讓 VSPackage 能夠執行 advanced 鍵盤篩選。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsFontAndColorCacheManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> | 否 | 是 | 提供在中的字型和色彩之快取集的存取權，以重新整理 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 或清除特定快取或所有快取。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsFontAndColorStorage> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities> | 是 | 是 | 讓 VSPackage 操作所維護的字型和色彩設定 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 此外，此服務可讓您存取用於操作字型和色彩資料的公用程式方法集合。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> | 是 | 是 | 提供一般 **輸出視窗** 窗格的存取權，視需要建立。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsHelpService> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsHelpSystem> | 是 | 是 | 提供 Help 系統的存取權。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsHTMLConverter> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsHTMLConverter> | 是 | 是 | [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯工具用來處理 HTML，以格式化其輸出。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsIME> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsIME> | 是 | 是 | 從 VSPackage 中提供輸入方法編輯器 (IME) API 的存取權。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsIntegratedHelp> | <xref:Microsoft.VisualStudio.VSHelp.SVsHelp> | 是 | 是 | 提供存取說明 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 系統以進行關鍵字或 URL 存取，以及透過說明檔進行導覽控制。 只有當 [說明] 已整合至 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE，而不是以外部程式執行時，才能使用此服務。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsIntelliMouseHandler> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntelliMouseHandler> | 是 | 是 | 可讓 VSPackage 存取滑鼠滾輪時的按鍵功能，例如使用滑鼠滾輪以及處理捲軸和平移點陣圖。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsIntellisenseEngine> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseEngine> | 否 | 是 | 啟用專案階層節點以載入或卸載檔案，做為 IntelliSense 作業支援的一部分。 載入和卸載觸發程式事件的程式，可能會影響專案的 IntelliSense 工具提示中顯示的內容。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsIntellisenseProjectHost> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProjectHost> | 否 | 是 | 啟用專案階層節點以提供 (的嵌套 IntelliSense 專案相關資訊，這些專案 <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject> 會執行可在 IntelliSense 工具提示中顯示的介面) 。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsIntellisenseProjectManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProjectManager> | 否 | 是 | 啟用專案階層節點以建議事件的接聽程式，例如參考或設定中的變更，這可能會影響 IntelliSense 工具提示中顯示的內容。 設計為搭配包含的語言使用。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsInvisibleEditorManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> | 是 | 是 | 讓 VSPackage 註冊「隱藏的」編輯器，也就是提供完整編輯功能但使用者看不到的編輯器。 |
| <xref:Microsoft.VisualStudio.TextManager.Interop.SVsLanguageFilter> | <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> | 是 | 是 | 讓 VSPackage 能夠提供文字視圖的其他資訊，例如資料提示和單字的範圍。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsLaunchPad> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsLaunchPad> | 是 | 是 | 讓 VSPackage 執行暫存批次腳本，以執行將輸出傳送至輸出窗格的命令列程式，以及剖析傳送至錯誤視窗的標準警告和錯誤訊息。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsLaunchPadFactory> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsLaunchPadFactory> | 是 | 是 | 提供建立物件的 factory <xref:Microsoft.VisualStudio.Shell.Interop.IVsLaunchPad> 。 |
| <xref:Microsoft.VisualStudio.TextManager.Interop.SVsLinkedUndoTransactionManager> | <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> | 是 | 是 | 提供對連結的復原管理員的存取。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsMenuEditor> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsMenuEditorFactory> | 是 | 是 | 讓表單設計工具存取共用功能表編輯器。 可以查詢 IVsMenuEditorFactory <xref:Microsoft.VisualStudio.Shell.Interop.IVsMenuEditor> 。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext> | 是 | 是 | 讓 VSPackage 建立「內容包」，用來建立特定內容的說明關鍵字。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjBrowser> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjBrowser> | 是 | 是 | 讓 VSPackage 導覽至 **物件瀏覽器** 中的特定物件。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager> | 是 | 是 | 讓 VSPackage 註冊其程式庫管理員，以 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 管理物件，例如命名空間、類別和列舉。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectSearch> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectSearch> | 是 | 是 | 讓 VSPackage 搜尋特定物件。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsOpenProjectOrSolutionDlg> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsOpenProjectOrSolutionDlg> | 否 | 是 | 讓 VSPackage 使用 [標準 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ] 對話方塊來開啟專案或方案。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> | 是 | 是 | 讓 VSPackage 在一般輸出視窗中建立額外的輸出窗格。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsParseCommandLine> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsParseCommandLine> | 是 | 是 | 可讓介面的實作者 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 剖析命令列。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsPathVariableResolver> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsPathVariableResolver> | 否 | 是 | 提供方法來解析特定的變數， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 而這些變數內嵌在路徑中以產生最終的路徑。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsPreviewChangesService> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsPreviewChangesService> | 否 | 是 | 顯示用於重構程式碼的 [ **預覽變更** ] 對話方塊。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsProfileDataManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsProfileDataManager> | 否 | 是 | 提供的 [配置檔案管理員] 存取，可讓您匯 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 入和匯出設定資料，以及顯示目前使用者設定檔設定的 UI。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsProfilesManagerUI> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsProfilesManagerUI> | 否 | 是 | 顯示顯示目前使用者設定檔設定的對話方塊。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsPropertyPageFrame> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPageFrame> | 是 | 是 | 讓 VSPackage 覆寫最初顯示在 [ **屬性** ] 視窗中的屬性頁。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> | 否 | 是 | Vspackage 用來通知原始檔控制提供者檔案即將在記憶體中變更或儲存。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterDebugTargetProvider> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectDebugTargetProvider> | 否 | 是 | 讓 VSPackage 專案以程式設計方式覆寫要在偵錯工具中啟動的目標。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors> | 是 | 是 | 讓 VSPackage 向 IDE 註冊編輯器 factory。 |
| <xref:Microsoft.VisualStudio.TextManager.Interop.SVsRegisterFindScope> | <xref:Microsoft.VisualStudio.TextManager.Interop.IVsRegisterFindScope> | 否 | 是 | 讓 VSPackage 註冊 [檔案 **中尋找** ] 對話方塊中的搜尋範圍。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterPriorityCommandTarget> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget> | 是 | 是 | 讓 VSPackage 將本身註冊為高優先順序的命令處理常式，讓 VSPackage 能夠查看所有命令。 如果有的話，請謹慎使用。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes> | 是 | 是 | 讓 VSPackage 向 IDE 註冊專案類型。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsResourceManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsResourceManager> | 否 | 是 | 讓 VSPackage 從附屬 Dll 載入 managed 和非受控資源。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsResourceView> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsResourceView> | 是 | 是 | 請改用 <xref:Microsoft.VisualStudio.Shell.Interop.SVsClassView> 服務。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> | 是 | 是 | 提供對 IDE 的執行中檔資料表的存取 (RDT 追蹤所有目前開啟之檔的) 。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> | 否 | 是 | 讓 Vspackage 向原始檔控制提供者註冊自己，讓他們可以參與原始檔控制。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccToolsOptions> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions> | 是 | 是 | 讓 VSPackage 取得和設定原始檔控制提供者選項。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSettingsReader> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> | 否 | 是 | 提供使用者設定檔設定的讀取權限。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell> | 是 | 是 | 讓 VSPackage 直接與其他 Vspackage 互動和操作。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger> | 是 | 是 | 提供 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 偵錯工具的存取。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> | 是 | 是 | 讓 VSPackage 存取目前的選取範圍，以及管理命令 UI 內容。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVSMDCodeDomProvider> | IVSMDCodeDomProvider | 否 | 是 | 提供可在機器碼中使用的程式碼檔物件模型 (DOM) 提供者的存取權。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVSMDDesignerService> | IVSMDCodeDomCreator<br /><br /> IVSMDDesignerService | 否 | 是 | 提供對 managed 表單設計工具的 IDE 支援存取。 `IVSMDCodeDomCreator`可以用來建立程式碼 DOM 提供者。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVSMDPropertyBrowser> | IVSMDPropertyBrowser | 否 | 是 | 提供對設計工具屬性 windows 服務的存取。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVSMDTypeResolutionService> | <xref:Microsoft.VisualStudio.Shell.Interop.IVSMDTypeResolutionService> | 否 | 是 | 提供介面的存取權，該介面可以傳回 <xref:System.ComponentModel.Design.ITypeResolutionService> 機器碼中可用的物件。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSmartOpenScope> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSmartOpenScope> | 否 | 是 | 提供方法來開啟元件的範圍，並視需要考慮鎖定。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> | 是 | 是 | 提供目前解決方案的最上層存取權。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager> | 是 | 是 | 讓 VSPackage 與解決方案的組建流程互動。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionObject> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> | 是 | 是 | 請改用 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> 服務。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionPersistence> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> | 是 | 是 | 讓 VSPackage 能夠儲存和取出目前方案 .sln 檔案中的資訊。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSQLCLRReferences> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSQLCLRReferences> | 否 | 是 | 提供在 managed 程式碼元件中新增和更新參考的能力。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsStartPageDownload> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsStartPageDownload> | 否 | 是 | 提供存取 Visual Studio 2017 起始頁面的下載服務，以在背景執行緒上啟動及停止下載服務。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> | 是 | 是 | 提供 IDE 狀態列的存取權。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsStrongNameKeys> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsStrongNameKeys> | 否 | 是 | 提供方法的存取權，以使用用於簽署 managed 程式碼元件的密碼來建立強式金鑰名稱和金鑰檔。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsStructuredFileIO> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsStructuredFileIO> | 是 | 是 | 可讓 VSPackage 支援以多種格式儲存資料。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> | 是 | 是 | 提供 IDE 工作清單視窗的存取。 |
| <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextImageUtilities> | <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextImageUtilities> | 否 | 是 | 提供用於載入和儲存文字檔的公用程式。 |
| <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> | <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> | 是 | 是 | 提供所有文字緩衝區的存取權，以及隱藏的文字會話 (針對 IDE 中可用的隱藏區域) 。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsTextOut> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsTextOut> | 是 | 是 | 提供用來將文字寫入裝置內容的 Win32 函式版本 `TextOut` (需要有 DC 控制碼) 。 |
| <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextSpanSet> | <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextSpanSet> | 是 | 是 | 提供文字影像或緩衝區中文字範圍清單的存取權。 這項服務通常會在檔的容器上執行，並參考目前的檔。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsThreadedWaitDialog> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsThreadedWaitDialog> | 否 | 是 | 讓 VSPackage 顯示一個對話方塊，該對話方塊會等候不同的執行緒 (用來等候背景工作) 。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsThreadPool> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsThreadPool> | 否 | 是 | 讓 VSPackage 起始背景工作，然後由維護 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox> | 是 | 是 | 提供 IDE **工具箱** 的存取權。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolboxActiveXDataProvider> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProvider> | 是 | 是 | 讓 VSPackage 從 **工具箱** 專案中取得資訊。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolboxDataProviderRegistry> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProviderRegistry> | 否 | 是 | 讓 VSPackage 註冊 [工具箱] 資料提供者，而不會產生預先載入整個 **工具箱** 的效能成本。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolsOptions> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolsOptions> | 否 | 是 | 讓 VSPackage 判斷 [ **選項** ] 對話方塊是否已開啟，以及重新整理 [所有選項] 頁面的可見度。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3> | 否 | 是 | 讓 VSPackage 監視專案檔案中的變更，並提供對原始檔控制提供者的批次控制。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> | 是 | 是 | 讓 VSPackage 通知 IDE 對選取專案的變更可能會影響目前選取的專案專案。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelper> | 是 | 是 | 啟用階層 (例如專案 VSPackage) ，以協調剪貼簿與其他階層的使用。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> | 是 | 是 | 提供 IDE UI 元素的存取，例如工具視窗和文件視窗。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellDocumentWindowMgr> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellDocumentWindowMgr> | 是 | 是 | 讓 VSPackage 根據資料流程的內容還原所有視窗的位置，或將所有視窗的位置儲存至資料流程。 很少使用。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> | 是 | 是 | 讓 VSPackage 能夠以許多方式開啟檔，以及判斷誰擁有哪些檔。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> | 否 | 是 | 由介面的實作者用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 來報告錯誤和參考訊息。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsWebBrowsingService> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsWebBrowsingService> | 是 | 是 | 可讓 VSPackage 建立及控制網頁瀏覽會話。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsWebFavorites> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsWebFavorites> | 是 | 是 | 讓 VSPackage 新增至使用者的 [我的最愛 **]** 清單。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsWebPreview> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsWebPreview> | 是 | 是 | 讓 VSPackage 預覽網頁，通常是在子視窗中。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsWebURLMRU> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsWebURLMRU> | 是 | 是 | 讓 VSPackage 將 URL 新增至最近使用的 (MRU) Url 清單，以及取得 MRU 清單中所有 Url 的清單。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsWindowFrame> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> | 是 | 是 | 可讓 VSPackage 取得封裝或部分封裝所在的視窗框架。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsXMLMemberIndexService> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsXMLMemberIndexService> | 是 | 是 | 提供與特定中繼資料檔案相關聯之 XML 格式檔檔案的存取權。 |

## <a name="see-also"></a>另請參閱

- [使用和提供服務](../../extensibility/using-and-providing-services.md)
