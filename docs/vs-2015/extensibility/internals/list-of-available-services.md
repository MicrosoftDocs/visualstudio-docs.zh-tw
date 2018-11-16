---
title: 可用服務清單 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, Visual Studio
- Visual Studio, services
ms.assetid: 724eb24b-b87c-4971-a2e7-adee7afc03b2
caps.latest.revision: 50
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0363aba508ff1a00fcca34f4b0b7a857aa15fc4f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51730699"
---
# <a name="list-of-available-services"></a>可用服務清單
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 和 Visual Studio SDK 支援下列服務。 某些套件提供自己此處未列出的服務 — 例如，語言服務並沒有單一服務的 GUID。 若要在登錄中尋找語言服務的 GUID，您必須使用的語言名稱。  
  
 若要取得的主要介面或介面顯示與每個服務使用此處所列，或從其他來源 （例如，語言服務） 取得的服務 Guid。  
  
## <a name="the-services"></a>服務  
  
|服務|介面|Visual Studio|Visual Studio 2005|描述|  
|-------------|---------------|-------------------|------------------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.SBindHost>|<xref:Microsoft.VisualStudio.OLE.Interop.IBindHost>|是|是|用來取得 Vspackage<xref:Microsoft.VisualStudio.OLE.Interop.IBindHost>從 ActiveX 控制項來加速非同步資料傳輸的介面。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SDTE>|<xref:EnvDTE.DTE>|否|是|取得用來自動化的設計階段擴充性 (DTE) 物件。<br /><br /> C/C + + 識別碼： SID_SDTE|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SCodeNavigate>|<xref:Microsoft.VisualStudio.Shell.Interop.ICodeNavigate>|是|是|若要顯示控制項的預設事件處理常式的表單設計工具來實作。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.SContainerDispatch>|IDispatch|是|是|可讓 VSPackage 也可以存取另一個 VSPackage 或控制項的自動化介面。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SExtendedTypeLib>|<xref:Microsoft.VisualStudio.Shell.Interop.IExtendedTypeLib>|是|是|可讓 VSPackage 也可以加入或建立擴充的型別程式庫。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SDirList>|<xref:Microsoft.VisualStudio.Shell.Interop.IDirList>|否|是|提供容器的權限的名稱清單的清單;比方說，若要搜尋中所示的目錄清單**尋找及取代** 對話方塊中的**查詢**下拉式清單。 <xref:Microsoft.VisualStudio.Shell.Interop.IDirList>物件可以是讀取以及寫入。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SIVsPackageDynamicToolOwner>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwner>|是|是|可讓 VSPackage 也可以有它自己的工具視窗以動態方式顯示或隱藏。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SLicensedClassManager>|<xref:Microsoft.VisualStudio.Shell.Interop.ILicensedClassManager>|是|是|可讓 VSPackage 也可以向[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]它需要藉由指定一份授權金鑰的類別。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry>|<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2>|是|是|可讓 VSPackage 也可以存取相對於本機登錄[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]登錄 hive。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.SOleComponentManager>|<xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager>|是|是|提供元件協調服務，例如訊息迴圈、 鍵盤迴圈和事件通知。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager>|是|是|可讓 VSPackage 也可以存取的各種使用者介面 (UI) 項目[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]、 說明、 狀態列等使用者介面事件。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SOleInPlaceComponent>|<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>|是|是|可讓 VSPackage 也可以整合其 UI 的 ui [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SOleInPlaceComponentSite>|<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentSite>|是|是|可讓 VSPackage 也可以控制特定工具的 UI 變更。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.SOleUndoManager>|<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>|是|是|可讓 VSPackage 也可以存取容器的復原管理員可以參與該容器的復原堆疊，或存取該容器的復原堆疊。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SProfferService>|<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>|是|是|可讓 VSPackage 也可以提供自己的服務。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SProfferTypeLib>|<xref:Microsoft.VisualStudio.Shell.Interop.IProfferTypeLib>|是|是|可讓表單設計工具可以讓型別程式庫可供參考。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>|<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>|是|是|提供存取權的選項中選取項目容器。 使用表單設計工具。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SUIHostCommandDispatcher>|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|是|是|可讓 VSPackage 也可以參與命令處理常式鏈結和處理代表整合式的開發環境 (IDE) 或其本身的命令。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SUIHostLocale>|<xref:Microsoft.VisualStudio.Shell.Interop.IUIHostLocale>|是|是|提供存取主應用程式的 UI 地區設定資訊。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>|否|是|可讓 VSPackage 來記錄記錄已開啟時的高層級的訊息。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsAddProjectItemDlg>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg>|是|是|提供存取權**加入專案項目**對話方塊，可讓 Vspackage 實作自己**加入項目**功能表選項。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsAddWebReferenceDlg>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg>|是|是|顯示**加入參考** 對話方塊。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>|是|是|可讓 VSPackage 也可以判斷是否命令列參數指定給 devenv.exe。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCallBrowser>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCallBrowser>|否|是|可讓 VSPackage 也可以建立新**呼叫瀏覽器**用於偵錯。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsClassView>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsClassView>|是|是|可讓 VSPackage 也可以同步處理**類別檢視**特定的物件。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCmdNameMapping>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCmdNameMapping>|是|是|支援將命令名稱對應至 Guid 和上一步，並判斷所有可用的命令和名稱的名稱。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCodeDefView>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCodeDefView>|否|是|可讓 VSPackage 來操作**程式碼定義檢視**。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCodeShareHandler>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCodeShareHandler>|是|是|內部的服務。 請勿使用。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.SVsCodeWindow>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|是|是|提供存取權可以包含一或多個文件的程式碼視窗。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.SVsCodeWindowManager>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|是|是|可讓 VSPackage 也可以將變更新增至程式碼 視窗，例如下拉式清單列。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCommandWindow>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCommandWindow><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommandWindow2>|是|是|可讓 VSPackage 也可以執行命令**命令視窗**，否則互動**命令視窗**。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCommandWindowsCollection>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCommandWindowsCollection>|否|是|可讓 VSPackage 也可以操作的清單**命令**windows 維護[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsComplusLibrary>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsLibraryReferenceManager>|是|是|可讓 VSPackage 來提供以瀏覽資訊**物件瀏覽器**。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsComponentSelectorDlg>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsComponentSelectorDlg>|否|是|可讓以支援 VSPackage**加入參考**選項，可讓使用者選取要新增至專案的外部元件。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsComponentSelectorDlg2>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsComponentSelectorDlg2>|否|是|可讓以支援 VSPackage**加入參考**選項，可讓使用者選取要新增至專案的外部元件。 在顯示之前，這個版本的對話方塊可讓預先填入的元件清單。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsConfigurationManagerDlg>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsConfigurationManagerDlg>|否|是|顯示**Configuration Manager**  對話方塊。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject>|否|是|可讓 VSPackage 也可以建立包含的其他專案集合的專案。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsDebuggableProtocol>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProtocol>|是|是|可讓 VSPackage 也可以更新可偵錯的 IDE 啟動特定的偵錯引擎使用的通訊協定的清單。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsDebugLaunch>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugLaunch>|是|是|可讓 VSPackage 也可以支援偵錯工具啟動。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsDiscoveryService>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDiscoveryService>|是|是|可讓 VSPackage 也可以建立用來探索 Web 服務探索工作階段。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsEnumHierarchyItemsFactory>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumHierarchyItemsFactory>|是|是|提供要建立 factory<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumHierarchyItemsFactory>物件可用來列舉指定的階層 （專案）。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsErrorList>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsErrorList>|否|是|提供其他方法來操作**組建錯誤清單**工作 視窗。 具體來說，帶來**組建錯誤清單**放到 [工作] 視窗，並強制要顯示的所有錯誤。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager>|是|是|提供存取權**其他檔案**目前方案的專案節點。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChange>||是|是|已過時。 使用`SVsFileChangeEx`改為服務。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx>|是|是|可讓 VSPackage 也可以存取由 IDE 所觸發的各種檔案變更事件。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFilterAddProjectItemDlg>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>|是|是|可讓 VSPackage 也可以篩選出現在項目**加入項目** 對話方塊。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFilterKeys>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterKeys>|是|是|可讓 VSPackage 也可以執行進階的鍵盤的篩選。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFontAndColorCacheManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>|否|是|字型提供存取快取組，並中色彩[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]以重新整理或清除特定快取或所有的快取。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFontAndColorStorage>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>|是|是|可讓 VSPackage 也可以操作所維護的字型和色彩設定[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。 此外，此服務提供存取的公用程式方法，以操作字型和色彩資料的集合。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane>|是|是|可讓您存取一般**輸出視窗** 窗格中，依需要建立它。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsHelpService>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHelpSystem>|是|是|提供說明系統的存取權。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsHTMLConverter>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHTMLConverter>|是|是|使用[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]偵錯工具來處理其輸出格式的 HTML。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsIME>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsIME>|是|是|若要輸入法 (IME) API 內 VSPackage 提供的存取。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsIntegratedHelp>|<xref:Microsoft.VisualStudio.VSHelp.SVsHelp>|是|是|提供存取[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]說明關鍵字或 URL 的系統存取以及瀏覽控制項到說明檔。 此服務才會提供說明整合到[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]IDE 並不以外部程式執行。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsIntelliMouseHandler>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsIntelliMouseHandler>|是|是|可讓 VSPackage 也可以存取 IntelliMouse 功能，例如使用滑鼠滾輪，以及處理 scroll 和取景位置調整的點陣圖，按下滑鼠滾輪時。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsIntellisenseEngine>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseEngine>|否|是|可讓載入或卸載檔案的 IntelliSense 作業支援一部分的專案階層節點。 載入和卸載作業可能會影響專案的 IntelliSense 工具提示中顯示的內容的觸發程序事件的處理程序。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsIntellisenseProjectHost>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProjectHost>|否|是|可讓專案階層節點提供巢狀的 IntelliSense 專案的相關資訊 (實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>介面)，可以顯示 IntelliSense 工具提示中。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsIntellisenseProjectManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProjectManager>|否|是|可讓通知的事件，例如參考或組態中，這可能會影響 IntelliSense 工具提示中顯示的內容中的變更的接聽程式的專案階層節點。 設計來與所包含的語言。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsInvisibleEditorManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager>|是|是|可讓 VSPackage 註冊 「 不可見的 」 編輯器中，也就是編輯器提供完整的編輯功能，但看不到使用者。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.SVsLanguageFilter>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|是|是|可讓 VSPackage 來提供額外的資訊，以文字檢視，例如資料提示的文字範圍。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsLaunchPad>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsLaunchPad>|是|是|可讓 VSPackage 也可以執行 [暫存批次指令碼，來執行命令列程式，其輸出會傳送到輸出] 窗格中，和剖析標準的警告和錯誤訊息傳送至視窗時發生錯誤。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsLaunchPadFactory>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsLaunchPadFactory>|是|是|提供 factory 建立<xref:Microsoft.VisualStudio.Shell.Interop.IVsLaunchPad>物件。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.SVsLinkedUndoTransactionManager>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager>|是|是|連結的復原管理員提供存取。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsMenuEditor>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMenuEditorFactory>|是|是|可讓表單設計工具來存取共用的功能表編輯器。 可以查詢 IVsMenuEditorFactory <xref:Microsoft.VisualStudio.Shell.Interop.IVsMenuEditor>。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext>|是|是|可讓 VSPackage 也可以建立的 「 內容包 」，用來將特定內容的 Help 關鍵字。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsObjBrowser>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjBrowser>|是|是|可讓瀏覽至特定的物件，在 VSPackage**物件瀏覽器**。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager>|是|是|可讓 VSPackage 也可以註冊使用其程式庫管理員[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]管理物件，例如命名空間、 類別和列舉型別。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectSearch>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectSearch>|是|是|可讓 VSPackage 也可以搜尋特定的物件。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsOpenProjectOrSolutionDlg>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOpenProjectOrSolutionDlg>|否|是|可讓 VSPackage 也可以使用標準[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]對話方塊來開啟專案或方案。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>|是|是|可讓 VSPackage 也可以建立一般的 [輸出] 視窗中的其他輸出窗格。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsParseCommandLine>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsParseCommandLine>|是|是|可讓實作者的<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>剖析命令列介面。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsPathVariableResolver>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPathVariableResolver>|否|是|可用來解決特定的變數[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]和內嵌於以產生最終的路徑的路徑。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsPreviewChangesService>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPreviewChangesService>|否|是|顯示**預覽變更**中重構程式碼使用的對話方塊。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsProfileDataManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProfileDataManager>|否|是|提供存取權的設定檔管理員[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]這可讓您匯入和匯出設定資料，以及顯示目前的使用者設定檔設定的 UI。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsProfilesManagerUI>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProfilesManagerUI>|否|是|顯示對話方塊，其中顯示目前的使用者設定檔設定。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsPropertyPageFrame>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPageFrame>|是|是|可讓 VSPackage 也可以覆寫的屬性頁 一開始所示**屬性**視窗。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|否|是|用來通知檔案是在記憶體中變更或儲存原始檔控制提供者 Vspackage。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterDebugTargetProvider>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectDebugTargetProvider>|否|是|可讓 VSPackage 專案，以程式設計方式覆寫要偵錯工具中啟動的目標。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors>|是|是|可讓 VSPackage 也可以在 IDE 中向編輯器 factory。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.SVsRegisterFindScope>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsRegisterFindScope>|否|是|可讓註冊的搜尋範圍 VSPackage**檔案中尋找** 對話方塊。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterPriorityCommandTarget>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>|是|是|可讓 VSPackage 也可以自行註冊為高優先順序命令處理常式，可讓 VSPackage，若要查看所有的命令。 如果有的話，請使用盡量節制。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>|是|是|可讓 VSPackage 也可以向在 IDE 中的專案類型。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsResourceManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsResourceManager>|否|是|可讓 VSPackage 也可以從附屬 Dll 載入 managed 和 unmanaged 資源。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsResourceView>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsResourceView>|是|是|使用<xref:Microsoft.VisualStudio.Shell.Interop.SVsClassView>改為服務。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>|是|是|提供存取至 IDE 的執行文件資料表 (RDT) 會追蹤所有目前開啟的文件。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|否|是|可讓 Vspackage 自行註冊與原始檔控制提供者，讓他們可以參與原始檔控制中。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccToolsOptions>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions>|是|是|可讓 VSPackage 也可以取得和設定原始檔控制提供者選項。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSettingsReader>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader>|否|是|提供使用者的設定檔設定的讀取權限。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsShell>|是|是|可讓 VSPackage 也可以直接互動和操作其他 Vspackage。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger>|是|是|提供存取[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]偵錯工具。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|是|是|可讓 VSPackage 也可以存取目前的選取範圍和管理命令 UI 內容。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVSMDCodeDomProvider>|IVSMDCodeDomProvider|否|是|提供存取權的程式碼文件物件模型 (DOM) 提供者可以使用原生程式碼。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVSMDDesignerService>|IVSMDCodeDomCreator<br /><br /> IVSMDDesignerService|否|是|提供 managed 的表單設計工具中的 IDE 支援的存取權。 `IVSMDCodeDomCreator`可用來建立程式碼 DOM 提供者。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVSMDPropertyBrowser>|IVSMDPropertyBrowser|否|是|提供設計工具屬性的 windows 服務的存取權。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVSMDTypeResolutionService>|<xref:Microsoft.VisualStudio.Shell.Interop.IVSMDTypeResolutionService>|否|是|提供存取權的介面，可傳回<xref:System.ComponentModel.Design.ITypeResolutionService>使用原生程式碼的物件。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSmartOpenScope>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSmartOpenScope>|否|是|可用來開啟組件中，納入鎖定所需的帳戶中的領域。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution>|是|是|提供最上層存取目前的方案。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager>|是|是|可讓 VSPackage 也可以與解決方案的建置程序互動。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionObject>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution>|是|是|使用<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>改為服務。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionPersistence>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>|是|是|可讓 VSPackage 也可以儲存和擷取從目前方案的.sln 檔案的資訊。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSQLCLRReferences>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSQLCLRReferences>|否|是|可讓您加入和更新的 managed 程式碼組件中的參考。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStartPageDownload>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStartPageDownload>|否|是|提供啟動和停止下載服務在背景執行緒上的 [入門] 頁面的下載服務存取權。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar>|是|是|提供 IDE 的 [狀態] 列的存取。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStrongNameKeys>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStrongNameKeys>|否|是|提供方法來建立強式金鑰名稱和金鑰檔案，以用於簽署 managed 程式碼組件的密碼的存取。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStructuredFileIO>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStructuredFileIO>|是|是|可讓 VSPackage 來提供支援以多種格式儲存資料。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList>|是|是|提供存取 IDE 的 [工作清單] 視窗。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextImageUtilities>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextImageUtilities>|否|是|提供公用程式載入及儲存文字檔。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>|是|是|提供存取所有的文字緩衝區，以及在 IDE 中可用的 （適用於隱藏的區域） 的隱藏的文字工作階段。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTextOut>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTextOut>|是|是|提供 Win32 版本`TextOut`函式將文字寫入至 裝置內容 （需要 DC 控點）。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextSpanSet>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextSpanSet>|是|是|提供一份文字影像或緩衝區中的文字範圍的存取。 此服務通常會實作在文件的容器，並會參考目前文件。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsThreadedWaitDialog>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsThreadedWaitDialog>|否|是|可讓 VSPackage 也可以顯示不同的執行緒 （用來等待背景工作） 等候對話方塊。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsThreadPool>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsThreadPool>|否|是|可讓 VSPackage 也可以起始背景工作，然後由維護[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox>|是|是|可讓您存取 IDE**工具箱**。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsToolboxActiveXDataProvider>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProvider>|是|是|可讓以取得資訊從 VSPackage**工具箱**項目。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsToolboxDataProviderRegistry>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProviderRegistry>|否|是|可讓註冊的工具箱資料提供者，而不會產生效能成本預先載入整個 VSPackage**工具箱**。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsToolsOptions>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolsOptions>|否|是|可讓 VSPackage 也可以判斷是否**選項**對話方塊開啟時，以及重新整理所有的 [選項] 頁面的可見性。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3>|否|是|可讓 VSPackage 來監視在專案檔中的變更，並提供批次控制原始檔控制提供者。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|是|是|可讓 VSPackage 也可以通知 IDE 的變更可能會影響目前選取的專案項目選取項目。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelper>|是|是|協調其他階層剪貼簿中的使用，可讓階層 （例如 VSPackage 專案）。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>|是|是|提供 IDE 的 UI 項目，例如工具視窗和文件視窗存取。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellDocumentWindowMgr>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellDocumentWindowMgr>|是|是|可讓 VSPackage 來還原資料的資料流的內容為基礎的所有視窗的位置，或將所有視窗的位置儲存到資料流。 很少使用。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>|是|是|可讓 VSPackage 透過數種方式開啟文件，並判斷哪些文件擁有者是誰。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger>|否|是|使用的實作器<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>介面來報告錯誤和參考用訊息。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsWebBrowsingService>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWebBrowsingService>|是|是|可讓 VSPackage 也可以建立和控制網頁瀏覽工作階段。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsWebFavorites>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWebFavorites>|是|是|可讓將新增至使用者的 VSPackage**我的最愛**清單。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsWebPreview>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWebPreview>|是|是|可讓 VSPackage 也可以預覽網頁，通常是在子視窗。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsWebURLMRU>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWebURLMRU>|是|是|可讓 VSPackage 將 URL 新增至最近使用的 (MRU) 清單的 Url，並取得一份 MRU 清單中的所有 Url。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsWindowFrame>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>|是|是|可讓 VSPackage 來取得在其中封裝的一部分可能平均分攤工作量的視窗框架。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsXMLMemberIndexService>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsXMLMemberIndexService>|是|是|提供特定的中繼資料檔案與相關聯的 XML 格式的文件檔案的存取權。|  
  
## <a name="see-also"></a>另請參閱  
 [COM 和受管理的服務](http://msdn.microsoft.com/en-us/6c5808b4-ad87-48d7-ae06-33a81e7052af)   
 [使用和提供服務](../../extensibility/using-and-providing-services.md)

