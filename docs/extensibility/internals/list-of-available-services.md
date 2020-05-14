---
title: 可用服務清單 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, Visual Studio
- Visual Studio, services
ms.assetid: 724eb24b-b87c-4971-a2e7-adee7afc03b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 302d4bcff647a74acc973c47e0b62e66c86e5859
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707349"
---
# <a name="list-of-available-services"></a>可用服務清單

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Visual Studio SDK 支援以下服務。 某些包提供此處未列出的服務,例如,語言服務沒有單個服務 GUID。 您必須使用語言的名稱才能在註冊表中找到語言服務的 GUID。

使用此處列出的服務 GUID 或從其他來源(例如語言服務)獲取與每個服務顯示的主介面或介面。

## <a name="the-services"></a>服務

| 服務 | 介面 | Visual Studio | Visual Studio 2005 | 描述 |
| - | - |---------------|--------------------| - |
| <xref:Microsoft.VisualStudio.OLE.Interop.SBindHost> | <xref:Microsoft.VisualStudio.OLE.Interop.IBindHost> | 是 | 是 | VSPackages 用於從 ActiveX<xref:Microsoft.VisualStudio.OLE.Interop.IBindHost>控制項獲取介面,以方便非同步資料傳輸。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SDTE> | <xref:EnvDTE.DTE> | 否 | 是 | 獲取用於自動化的設計時間擴展 (DTE) 物件。<br /><br /> C/C++ ID:SID_SDTE |
| <xref:Microsoft.VisualStudio.Shell.Interop.SCodeNavigate> | <xref:Microsoft.VisualStudio.Shell.Interop.ICodeNavigate> | 是 | 是 | 由表單設計器實現,以顯示控制項的預設事件處理程式。 |
| <xref:Microsoft.VisualStudio.OLE.Interop.SContainerDispatch> | IDispatch | 是 | 是 | 使 VSPackage 能夠造訪另一個 VSPackage 或控制項的自動化介面。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SExtendedTypeLib> | <xref:Microsoft.VisualStudio.Shell.Interop.IExtendedTypeLib> | 是 | 是 | 使 VSPackage 能夠添加或創建擴充類型庫。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SDirList> | <xref:Microsoft.VisualStudio.Shell.Interop.IDirList> | 否 | 是 | 提供對容器命名清單的訪問;例如,要搜索的目錄清單,如「**尋找」和取代**「下拉清單中的」**尋找**「對話框中所示。 物件<xref:Microsoft.VisualStudio.Shell.Interop.IDirList>可以從讀取並寫入物件。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SIVsPackageDynamicToolOwner> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwner> | 是 | 是 | 使 VSPackage 能夠動態顯示或隱藏自己的工具視窗。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SLicensedClassManager> | <xref:Microsoft.VisualStudio.Shell.Interop.ILicensedClassManager> | 是 | 是 | 通過指定許可證金鑰清單,使[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackage 能夠向所需的類指示它所需的類型。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> | <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> | 是 | 是 | 使 VSPackage 能夠存取[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]相對於本地 註冊表配置單元的註冊表。 |
| <xref:Microsoft.VisualStudio.OLE.Interop.SOleComponentManager> | <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager> | 是 | 是 | 提供元件協調服務,如消息迴圈、鍵盤迴圈和事件通知。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> | 是 | 是 | 使 VSPackage[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]能夠存取的各種使用者介面 (UI) 元素,如説明、狀態列和 UI 事件。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SOleInPlaceComponent> | <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> | 是 | 是 | 使 VS 包將其[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]UI 與的 UI 整合。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SOleInPlaceComponentSite> | <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentSite> | 是 | 是 | 使 VS 套件能夠控制特定於工具的 UI 更改。 |
| <xref:Microsoft.VisualStudio.OLE.Interop.SOleUndoManager> | <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> | 是 | 是 | 使 VSPackage 能夠存取容器的復原管理員,以參與該容器的復原堆疊或存取該容器的復原堆疊。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService> | <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> | 是 | 是 | 使 VSPackage 能夠提供自己的服務。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SProfferTypeLib> | <xref:Microsoft.VisualStudio.Shell.Interop.IProfferTypeLib> | 是 | 是 | 使表單設計器使類型庫可供參考。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> | <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> | 是 | 是 | 提供對選擇容器中選擇項的訪問許可權。 由表單設計器使用。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SUIHostCommandDispatcher> | <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> | 是 | 是 | 使 VSPackage 能夠參與命令處理程式鏈,並代表集成開發環境 (IDE) 或本身處理命令。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SUIHostLocale> | <xref:Microsoft.VisualStudio.Shell.Interop.IUIHostLocale> | 是 | 是 | 提供對主機的 UI 區域設置資訊的訪問。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> | 否 | 是 | 啟用 VSPackage 可在啟用紀錄記錄時記錄進階訊息。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsAddProjectItemDlg> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg> | 是 | 是 | 提供對 **「添加項目項目 」** 對話框的訪問,允許 VS 包實現其自己的 **「添加專案」** 選單選項。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsAddWebReferenceDlg> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg> | 是 | 是 | 顯示「**添加參考」** 對話方塊。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> | 是 | 是 | 啟用 VSPackage 以確定是否將命令列開關提供給 devenv.exe。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsCallBrowser> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsCallBrowser> | 否 | 是 | 使 VSPackage 能夠建立新的**調用瀏覽器**,用於除錯。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsClassView> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsClassView> | 是 | 是 | 使 VS 包能夠將**類視圖**同步到特定物件。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsCmdNameMapping> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsCmdNameMapping> | 是 | 是 | 支援將命令名稱映射到 GUID 並返回並確定所有可用命令和名稱的名稱。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsCodeDefView> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsCodeDefView> | 否 | 是 | 使 VS 套件能夠操作**程式碼定義檢視**。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsCodeShareHandler> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsCodeShareHandler> | 是 | 是 | 內部服務。 請勿使用。 |
| <xref:Microsoft.VisualStudio.TextManager.Interop.SVsCodeWindow> | <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> | 是 | 是 | 提供對可以包含一個或多個文件的代碼窗口的訪問。 |
| <xref:Microsoft.VisualStudio.TextManager.Interop.SVsCodeWindowManager> | <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> | 是 | 是 | 使 VSPackage 向代碼視窗(如下拉欄)添加更改。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsCommandWindow> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommandWindow><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommandWindow2> | 是 | 是 | 使 VSPackage 通過**命令視窗**執行命令,然後以其他方式與**命令視窗**進行互動。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsCommandWindowsCollection> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommandWindowsCollection> | 否 | 是 | 使 VSPackage 能夠**Command**[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]操作 由維護的命令視窗的清單。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsComplusLibrary> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibraryReferenceManager> | 是 | 是 | 使 VS 包向**物件瀏覽器**提供瀏覽資訊。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsComponentSelectorDlg> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsComponentSelectorDlg> | 否 | 是 | 使 VSPackage 支援**新增參考**選項,該選項允許使用者選擇要添加到專案的外部元件。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsComponentSelectorDlg2> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsComponentSelectorDlg2> | 否 | 是 | 使 VSPackage 支援**新增參考**選項,該選項允許使用者選擇要添加到專案的外部元件。 此版本的對話框允許在顯示元件清單之前預填充元件清單。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsConfigurationManagerDlg> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsConfigurationManagerDlg> | 否 | 是 | 顯示 **「設定管理員**」 對話方塊。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject> | 否 | 是 | 使 VSPackage 能夠建立包含其他專案集合的專案。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsDebuggableProtocol> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProtocol> | 是 | 是 | 使 VSPackage 能夠更新 IDE 用於啟動特定調試引擎的可調試協定清單。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsDebugLaunch> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugLaunch> | 是 | 是 | 使 VS 包支援啟動除錯器。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsDiscoveryService> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsDiscoveryService> | 是 | 是 | 使 VSPackage 創建用於發現 Web 服務的發現工作階段。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsEnumHierarchyItemsFactory> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumHierarchyItemsFactory> | 是 | 是 | 提供用於創建<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumHierarchyItemsFactory>用於枚舉指定層次結構(專案)的物件的工廠。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsErrorList> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsErrorList> | 否 | 是 | 提供了用於操作**生成錯誤清單**任務視窗的其他方法。 具體而言,將**生成錯誤清單**任務視窗置於最前沿,並強制顯示所有錯誤。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager> | 是 | 是 | 提供對當前解決方案**的雜項檔**專案節點的訪問。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChange> | | 是 | 是 | 已過時。 而是`SVsFileChangeEx`使用服務。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> | 是 | 是 | 使 VSPackage 能夠造訪由 IDE 觸發的各種檔更改事件。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsFilterAddProjectItemDlg> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> | 是 | 是 | 使 VSPackage 能夠篩選「**新增項目**」 對話框中顯示的專案。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsFilterKeys> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterKeys> | 是 | 是 | 使 VSPackage 能夠執行進階鍵盤篩選。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsFontAndColorCacheManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> | 否 | 是 | 提供對字體[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]和顏色的緩存集的訪問,以刷新或清除特定緩存或所有快取。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsFontAndColorStorage> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities> | 是 | 是 | 使 VSPackage 能夠操作[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]維護的 字體和顏色設置。 此外,此服務還提供對用於操作字體和顏色數據的實用程式方法集合的訪問。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> | 是 | 是 | 提供對常規**輸出視窗**窗格的訪問,根據需要創建它。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsHelpService> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsHelpSystem> | 是 | 是 | 提供對幫助系統的訪問。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsHTMLConverter> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsHTMLConverter> | 是 | 是 | [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]除錯器用於處理 HTML 以格式化其輸出。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsIME> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsIME> | 是 | 是 | 從 VS 套件中提供對輸入方法編輯器 (IME) API 的訪問。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsIntegratedHelp> | <xref:Microsoft.VisualStudio.VSHelp.SVsHelp> | 是 | 是 | 提供對[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]關鍵字或網址訪問的幫助系統的存取,以及透過幫助文件的導航控制。 僅當説明整合到 IDE 而不是作為外部[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]程式執行 時,此服務才可用。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsIntelliMouseHandler> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntelliMouseHandler> | 是 | 是 | 使 VSPackage 能夠造訪 IntelliMouse 功能,例如使用滑鼠滾輪,並在按一下滑鼠滾輪時處理滾動和平移位圖。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsIntellisenseEngine> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseEngine> | 否 | 是 | 使專案層次結構節點能夠載入或卸載檔,作為支援 IntelliSense 操作的一部分。 載入和卸載過程觸發可能影響 IntelliSense 工具提示中顯示的事件。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsIntellisenseProjectHost> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProjectHost> | 否 | 是 | 使專案層次結構節點能夠提供有關嵌套 IntelliSense 專案<xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>(實現介面)的資訊,這些專案可以顯示在 IntelliSense 工具提示中。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsIntellisenseProjectManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProjectManager> | 否 | 是 | 使專案層次結構節點能夠通知偵聽器事件,例如引用或配置的更改,這可能會影響 IntelliSense 工具提示中顯示的內容。 設計用於包含語言。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsInvisibleEditorManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> | 是 | 是 | 使 VSPackage 能夠註冊「不可見」編輯器,即提供完全編輯功能但使用者不可見的編輯器。 |
| <xref:Microsoft.VisualStudio.TextManager.Interop.SVsLanguageFilter> | <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> | 是 | 是 | 使 VSPackage 能夠向文字檢視提供其他資訊,如數據提示和單詞範圍。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsLaunchPad> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsLaunchPad> | 是 | 是 | 使 VSPackage 能夠執行臨時批次處理文稿,執行其輸出發送到輸出窗格的命令列程式,並分析發送到錯誤視窗的標準警告和錯誤訊息。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsLaunchPadFactory> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsLaunchPadFactory> | 是 | 是 | 提供用於創建<xref:Microsoft.VisualStudio.Shell.Interop.IVsLaunchPad>物件的工廠。 |
| <xref:Microsoft.VisualStudio.TextManager.Interop.SVsLinkedUndoTransactionManager> | <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> | 是 | 是 | 提供對連結撤銷管理器的訪問。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsMenuEditor> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsMenuEditorFactory> | 是 | 是 | 使表單表單編輯器可以存取共享選單編輯器。 可以查詢 IVMenu 編輯<xref:Microsoft.VisualStudio.Shell.Interop.IVsMenuEditor>器工廠 。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext> | 是 | 是 | 使 VSPackage 能夠建立「上下文包」,用於關聯特定上下文的幫助關鍵字。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjBrowser> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjBrowser> | 是 | 是 | 使 VS 包導航到**物件瀏覽器**中的特定物件。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager> | 是 | 是 | 使 VSPackage 將其庫管理器[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]註冊用於 管理命名空間、類和枚舉等物件。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectSearch> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectSearch> | 是 | 是 | 使 VS 包能夠搜索特定物件。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsOpenProjectOrSolutionDlg> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsOpenProjectOrSolutionDlg> | 否 | 是 | 使 VSPackage 能夠[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]使用標準 對話框打開專案或解決方案。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> | 是 | 是 | 使 VSPackage 能夠在常規輸出視窗中創建其他輸出窗格。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsParseCommandLine> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsParseCommandLine> | 是 | 是 | 使介面的<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>實現者能夠解析命令行。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsPathVariableResolver> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsPathVariableResolver> | 否 | 是 | 提供了一種解決特定於[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]的變數的方法,這些變數嵌入到路徑中以生成最終路徑。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsPreviewChangesService> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsPreviewChangesService> | 否 | 是 | 顯示重構代碼中使用的 **「預覽更改」** 對話方塊。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsProfileDataManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsProfileDataManager> | 否 | 是 | 提供對設定檔[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]管理員的訪問,該管理員允許導入和匯出設置資料,以及顯示當前使用者的設定檔設置的 UI。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsProfilesManagerUI> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsProfilesManagerUI> | 否 | 是 | 顯示顯示當前使用者的配置檔設置的對話方塊。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsPropertyPageFrame> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPageFrame> | 是 | 是 | 使 VSPackage 能夠覆蓋屬性頁最初顯示在 **「屬性」** 視窗中。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> | 否 | 是 | VSPackages 用於通知原始程式碼管理提供程式檔即將在記憶體中更改或保存。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterDebugTargetProvider> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectDebugTargetProvider> | 否 | 是 | 使 VSPackage 專案能夠以程式設計方式覆蓋目標,以在除錯器中啟動。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors> | 是 | 是 | 使 VSPackage 向 IDE 註冊編輯器工廠。 |
| <xref:Microsoft.VisualStudio.TextManager.Interop.SVsRegisterFindScope> | <xref:Microsoft.VisualStudio.TextManager.Interop.IVsRegisterFindScope> | 否 | 是 | 使 VSPackage 註冊「**在檔案中搜尋**」對話框的搜尋範圍。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterPriorityCommandTarget> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget> | 是 | 是 | 使 VSPackage 能夠將自己註冊為高優先順序命令處理程式,這允許 VSPackage 查看所有命令。 請謹慎使用(如果有的話)。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes> | 是 | 是 | 使 VS 包能夠向 IDE 註冊項目類型。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsResourceManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsResourceManager> | 否 | 是 | 使 VSPackage 能夠從附屬 DLL 載入託管和非託管資源。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsResourceView> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsResourceView> | 是 | 是 | 而是<xref:Microsoft.VisualStudio.Shell.Interop.SVsClassView>使用服務。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> | 是 | 是 | 提供對 IDE 正在執行的文件表 (RDT) 的訪問,該表可追蹤所有當前打開的文檔。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> | 否 | 是 | 使 VSPackages 能夠向原始碼管理提供程式註冊,以便它們能夠參與原始碼管理。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccToolsOptions> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions> | 是 | 是 | 使 VSPackage 獲取和設定原始碼管理提供程式選項。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSettingsReader> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> | 否 | 是 | 提供對使用者的配置檔設置的讀取存取許可權。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell> | 是 | 是 | 使 VS 包能夠直接與其他 VS 包交互和操作。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger> | 是 | 是 | 提供對調試器[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]的訪問。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> | 是 | 是 | 使 VSPackage 可以造取目前選擇並管理命令 UI 上下文。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVSMDCodeDomProvider> | IVSMD 代碼提供者 | 否 | 是 | 提供對代碼文件物件模型 (DOM) 提供程式的訪問,該提供程式可在本機代碼中使用。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVSMDDesignerService> | IVSMD 代碼創造者<br /><br /> IVSMD設計服務 | 否 | 是 | 提供對託管表單設計器的 IDE 支援的訪問。 `IVSMDCodeDomCreator`可用於創建代碼 DOM 提供程式。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVSMDPropertyBrowser> | IVSMD 屬性瀏覽器 | 否 | 是 | 提供對設計器屬性視窗服務的訪問。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVSMDTypeResolutionService> | <xref:Microsoft.VisualStudio.Shell.Interop.IVSMDTypeResolutionService> | 否 | 是 | 提供對可以返回本機代碼中可使用<xref:System.ComponentModel.Design.ITypeResolutionService>的物件的介面的訪問。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSmartOpenScope> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSmartOpenScope> | 否 | 是 | 提供了一種在程式集上打開作用域的方法,並考慮根據需要鎖定。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> | 是 | 是 | 提供對當前解決方案的頂級訪問。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager> | 是 | 是 | 使 VSPackage 能夠與解決方案的生成過程進行互動。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionObject> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> | 是 | 是 | 改用<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>服務。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionPersistence> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> | 是 | 是 | 使 VSPackage 能夠儲存和檢索當前解決方案的 .sln 檔案中的資訊。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSQLCLRReferences> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSQLCLRReferences> | 否 | 是 | 提供在託管代碼程式集中添加和更新引用的能力。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsStartPageDownload> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsStartPageDownload> | 否 | 是 | 提供對 Visual Studio 2017 起始頁的下載服務的訪問,以便啟動和停止後台線程上的下載服務。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> | 是 | 是 | 提供對 IDE 狀態列的訪問。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsStrongNameKeys> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsStrongNameKeys> | 否 | 是 | 提供對使用用於對託管代碼程式集進行簽名的密碼創建強密鑰名稱和密鑰檔的方法的訪問。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsStructuredFileIO> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsStructuredFileIO> | 是 | 是 | 使 VSPackage 能夠支援以多種格式保存數據。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> | 是 | 是 | 提供存取 IDE 的任務列表視窗。 |
| <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextImageUtilities> | <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextImageUtilities> | 否 | 是 | 提供用於載入和保存文本檔的實用程式。 |
| <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> | <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> | 是 | 是 | 提供對所有文本緩衝區以及 IDE 中可用的隱藏文本會話(對於隱藏區域)的訪問。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsTextOut> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsTextOut> | 是 | 是 | 提供 Win32`TextOut`函數的版本,用於將文本寫入設備上下文(需要 DC 句柄)。 |
| <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextSpanSet> | <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextSpanSet> | 是 | 是 | 提供對文本圖像或緩衝區中文本範圍列表的訪問。 此服務通常在文檔容器上實現,並引用當前文檔。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsThreadedWaitDialog> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsThreadedWaitDialog> | 否 | 是 | 使 VSPackage 顯示在另一個線程上等待的對話框(用於等待後台任務)。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsThreadPool> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsThreadPool> | 否 | 是 | 使 VS 包啟動後台任務,[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]然後由維護。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox> | 是 | 是 | 提供對 IDE**工具箱**的訪問。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolboxActiveXDataProvider> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProvider> | 是 | 是 | 使 VSPackage 能夠從**工具箱**專案獲取資訊。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolboxDataProviderRegistry> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProviderRegistry> | 否 | 是 | 使 VSPackage 能夠註冊工具箱數據提供者,而不會產生預載入整個**工具箱**的效能成本。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolsOptions> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolsOptions> | 否 | 是 | 啟用 VSPackage 以確定 **「選項」** 對話框是否處於打開狀態,並刷新所有選項頁的可見性。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3> | 否 | 是 | 使 VSPackage 能夠監視專案檔中的更改,並提供對原始程式碼管理提供程式的批次處理控制。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> | 是 | 是 | 使 VSPackage 能夠通知 IDE 對選區的更改,這些更改可能會影響當前選定的專案項。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelper> | 是 | 是 | 使層次結構(如專案 VSPackage)能夠協調剪貼簿與其他層次結構的使用。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> | 是 | 是 | 提供對 IDE 的 UI 元素(如工具視窗和文檔視窗)的訪問。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellDocumentWindowMgr> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellDocumentWindowMgr> | 是 | 是 | 使 VSPackage 能夠根據資料流的內容還原所有視窗的位置,或將所有視窗的位置保存到流中。 很少使用。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> | 是 | 是 | 使 VSPackage 能夠以多種方式打開文檔,並確定誰擁有哪些文檔。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> | 否 | 是 | 由<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>介面的實現者用於報告錯誤和資訊消息。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsWebBrowsingService> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsWebBrowsingService> | 是 | 是 | 使 VS 套件能夠建立和控制 Web 瀏覽作業階段。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsWebFavorites> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsWebFavorites> | 是 | 是 | 使 VS 套件新增到使用者的**收藏夾**清單中。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsWebPreview> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsWebPreview> | 是 | 是 | 使 VSPackage 能夠預覽網頁,通常在子視窗中。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsWebURLMRU> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsWebURLMRU> | 是 | 是 | 使 VSPackage 能夠將 URL 加入最近使用的網址 清單中,並取得 MRU 清單中所有網址的清單。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsWindowFrame> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> | 是 | 是 | 使 VSPackage 能夠獲取包或包的一部分可能所在的視窗框架。 |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsXMLMemberIndexService> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsXMLMemberIndexService> | 是 | 是 | 提供對與特定元資料檔關聯的 XML 格式文件文件的訪問。 |

## <a name="see-also"></a>另請參閱

- [使用和提供服務](../../extensibility/using-and-providing-services.md)
