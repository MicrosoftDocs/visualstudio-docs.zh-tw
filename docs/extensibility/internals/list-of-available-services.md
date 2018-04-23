---
title: 可用服務清單 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, Visual Studio
- Visual Studio, services
ms.assetid: 724eb24b-b87c-4971-a2e7-adee7afc03b2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6f2caeaee433fc0c47d8332c4443d104e26a7ee7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="list-of-available-services"></a>可用服務清單
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 和 Visual Studio SDK 支援下列服務。 有些封裝提供它們自己這裡未列出的服務 — 例如，語言服務並沒有單一的服務 GUID。 若要在登錄中尋找語言服務的 GUID，您必須使用的語言名稱。  
  
 若要取得的主要介面或介面顯示與每個服務使用此處所列，或來自其他來源 （例如，語言服務） 所取得的服務 Guid。  
  
## <a name="the-services"></a>服務  
  
|服務|介面|Visual Studio|Visual Studio 2005|描述|  
|-------------|---------------|-------------------|------------------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.SBindHost>|<xref:Microsoft.VisualStudio.OLE.Interop.IBindHost>|[是]|[是]|用來取得 Vspackage<xref:Microsoft.VisualStudio.OLE.Interop.IBindHost>自 ActiveX 控制項以便非同步資料傳輸的介面。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SDTE>|<xref:EnvDTE.DTE>|否|[是]|取得用來自動化的設計階段擴充性 (DTE) 物件。<br /><br /> C/C + + 識別碼： SID_SDTE|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SCodeNavigate>|<xref:Microsoft.VisualStudio.Shell.Interop.ICodeNavigate>|[是]|[是]|若要顯示控制項的預設事件處理常式的表單設計工具所實作。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.SContainerDispatch>|IDispatch|[是]|[是]|可讓 VSPackage 也可以存取另一個 VSPackage 或控制項的 automation 介面。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SExtendedTypeLib>|<xref:Microsoft.VisualStudio.Shell.Interop.IExtendedTypeLib>|[是]|[是]|可讓 VSPackage 也可以加入或建立擴充的型別程式庫。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SDirList>|<xref:Microsoft.VisualStudio.Shell.Interop.IDirList>|否|[是]|提供容器的存取權的名稱清單的清單。例如，搜尋中所示的目錄清單**尋找和取代** 對話方塊中的**查詢**下拉式清單。 <xref:Microsoft.VisualStudio.Shell.Interop.IDirList>物件可以是從讀取以及寫入。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SIVsPackageDynamicToolOwner>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwner>|[是]|[是]|可讓 VSPackage 也可以有自己的工具視窗上以動態方式顯示或隱藏。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SLicensedClassManager>|<xref:Microsoft.VisualStudio.Shell.Interop.ILicensedClassManager>|[是]|[是]|可讓 VSPackage 也可以指示[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]它需要藉由指定一份授權金鑰的類別。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry>|<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2>|[是]|[是]|可讓 VSPackage 也可以存取相對於本機登錄[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]登錄區。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.SOleComponentManager>|<xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager>|[是]|[是]|提供元件協調服務，例如訊息迴圈、 鍵盤迴圈和事件通知。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager>|[是]|[是]|可讓 VSPackage 也可以存取的各種使用者介面 (UI) 項目[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，例如說明、 狀態列，與使用者事件。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SOleInPlaceComponent>|<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>|[是]|[是]|可讓 VSPackage 也可以整合其 UI 的 ui [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SOleInPlaceComponentSite>|<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentSite>|[是]|[是]|可讓 VSPackage 也可以控制所特有工具 UI 變更。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.SOleUndoManager>|<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>|[是]|[是]|可讓 VSPackage 也可以存取容器的復原管理員可以參與該容器復原堆疊，或存取該容器復原堆疊。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SProfferService>|<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>|[是]|[是]|可讓 VSPackage 也可以提供自己的服務。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SProfferTypeLib>|<xref:Microsoft.VisualStudio.Shell.Interop.IProfferTypeLib>|[是]|[是]|可讓表單設計工具，讓型別程式庫可供參考。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>|<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>|[是]|[是]|提供存取權的選擇中選取範圍容器。 使用表單設計工具。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SUIHostCommandDispatcher>|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|[是]|[是]|可讓 VSPackage 也可以參與命令處理常式鏈結和處理代表整合式的開發環境 (IDE)，或其本身的命令。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SUIHostLocale>|<xref:Microsoft.VisualStudio.Shell.Interop.IUIHostLocale>|[是]|[是]|存取主應用程式的 UI 地區設定資訊。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>|否|[是]|可讓 VSPackage 也可以開啟記錄時記錄高層級的訊息。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsAddProjectItemDlg>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg>|[是]|[是]|提供存取**加入專案項目**對話方塊，可讓 Vspackage 實作自己**加入項目**功能表選項。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsAddWebReferenceDlg>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg>|[是]|[是]|顯示**加入參考** 對話方塊。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>|[是]|[是]|可讓 VSPackage 也可以判斷是否 devenv.exe 指定命令列參數。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCallBrowser>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCallBrowser>|否|[是]|可讓 VSPackage 也可以建立新**呼叫瀏覽器**用於偵錯。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsClassView>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsClassView>|[是]|[是]|可讓 VSPackage 也可以同步處理**類別檢視**特定的物件。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCmdNameMapping>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCmdNameMapping>|[是]|[是]|支援的命令名稱對應至 Guid，以及判斷所有可用的命令和名稱的名稱。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCodeDefView>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCodeDefView>|否|[是]|可讓 VSPackage 也可以管理**程式碼定義檢視**。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCodeShareHandler>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCodeShareHandler>|[是]|[是]|內部的服務。 請勿使用。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.SVsCodeWindow>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|[是]|[是]|提供存取權可以包含一或多個文件的程式碼視窗。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.SVsCodeWindowManager>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|[是]|[是]|可讓 VSPackage 也可以將變更加入到下拉式清單列例如程式碼視窗。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCommandWindow>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCommandWindow><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommandWindow2>|[是]|[是]|可讓 VSPackage 也可以執行命令**命令視窗**並與其互動否則**命令視窗**。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCommandWindowsCollection>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCommandWindowsCollection>|否|[是]|可讓 VSPackage 也可以操作的清單**命令**windows 維護[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsComplusLibrary>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsLibraryReferenceManager>|[是]|[是]|可讓 VSPackage 提供瀏覽資訊給**物件瀏覽器**。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsComponentSelectorDlg>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsComponentSelectorDlg>|否|[是]|可讓 VSPackage 也可以支援**加入參考**選項，可讓使用者選取要新增至專案的外部元件。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsComponentSelectorDlg2>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsComponentSelectorDlg2>|否|[是]|可讓 VSPackage 也可以支援**加入參考**選項，可讓使用者選取要新增至專案的外部元件。 這一版的對話方塊可讓預先填入的元件清單，顯示之前。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsConfigurationManagerDlg>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsConfigurationManagerDlg>|否|[是]|顯示**Configuration Manager**  對話方塊。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject>|否|[是]|可讓 VSPackage 也可以建立包含的其他專案集合的專案。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsDebuggableProtocol>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProtocol>|[是]|[是]|可讓 VSPackage 也可以更新由 IDE 所用來啟動特定的偵錯引擎可偵錯的通訊協定清單。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsDebugLaunch>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugLaunch>|[是]|[是]|可讓 VSPackage 也可以支援啟動偵錯工具。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsDiscoveryService>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDiscoveryService>|[是]|[是]|可讓 VSPackage 也可以建立用來探索 Web 服務探索工作階段。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsEnumHierarchyItemsFactory>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumHierarchyItemsFactory>|[是]|[是]|提供要建立 factory<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumHierarchyItemsFactory>物件可用來列舉指定階層 （專案）。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsErrorList>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsErrorList>|否|[是]|提供其他方法來操作**組建錯誤清單**工作 視窗。 具體來說，使**組建錯誤清單**forefront 以 [工作] 視窗，並強制顯示所有錯誤。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager>|[是]|[是]|提供存取**其他檔案**目前方案的專案節點。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChange>||[是]|[是]|已過時。 使用`SVsFileChangeEx`改為服務。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx>|[是]|[是]|可讓 VSPackage 也可以存取由 IDE 所觸發的各種檔案變更事件。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFilterAddProjectItemDlg>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>|[是]|[是]|可讓 VSPackage 也可以篩選的項目會出現在**加入項目** 對話方塊。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFilterKeys>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterKeys>|[是]|[是]|可讓 VSPackage 也可以執行進階的鍵盤的篩選。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFontAndColorCacheManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>|否|[是]|提供存取資料集的快取的字型和色彩[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]以重新整理或清除特定快取或所有快取。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFontAndColorStorage>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>|[是]|[是]|可讓 VSPackage 也可以管理所維護的字型和色彩設定[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 此外，此服務會提供操作字型和色彩資料的公用程式方法的集合的存取。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane>|[是]|[是]|提供一般存取**輸出 視窗** 窗格中，依需要建立它。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsHelpService>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHelpSystem>|[是]|[是]|提供說明系統的存取權。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsHTMLConverter>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHTMLConverter>|[是]|[是]|使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯工具來處理 HTML 格式的輸出。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsIME>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsIME>|[是]|[是]|若要輸入法 (IME) API 內 VSPackage 提供的存取。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsIntegratedHelp>|<xref:Microsoft.VisualStudio.VSHelp.SVsHelp>|[是]|[是]|提供存取[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]說明系統的關鍵字或 URL 存取導覽控制項以及到說明檔。 此服務才會提供說明整合到[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE，並不以執行外部程式。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsIntelliMouseHandler>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsIntelliMouseHandler>|[是]|[是]|可讓 VSPackage 也可以存取 intellimouse 滑鼠功能，例如使用滑鼠滾輪，以及處理 scroll 和取景位置調整點陣圖，在按下滑鼠滾輪時。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsIntellisenseEngine>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseEngine>|否|[是]|可讓專案階層節點載入或卸載的 IntelliSense 作業支援一部分的檔案。 載入和卸載可能會影響 IntelliSense 的專案的工具提示中顯示的內容的觸發程序事件的程序。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsIntellisenseProjectHost>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProjectHost>|否|[是]|可讓專案階層節點提供巢狀 IntelliSense 專案的相關資訊 (可實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>介面)，可以顯示 IntelliSense 工具提示中。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsIntellisenseProjectManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProjectManager>|否|[是]|可讓要通知的事件，例如參考或組態中，這可能會影響 IntelliSense 的工具提示中顯示的內容中的變更接聽程式的專案階層節點。 為了能與包含的語言。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsInvisibleEditorManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager>|[是]|[是]|可讓 VSPackage 註冊 「 隱藏 」 編輯器中，也就是提供完整的編輯功能，但不會對使用者顯示的編輯器。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.SVsLanguageFilter>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|[是]|[是]|可讓 VSPackage 也可以提供其他資訊，以文字檢視，例如資料提示的文字範圍。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsLaunchPad>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsLaunchPad>|[是]|[是]|可讓 VSPackage 也可以執行暫存批次指令碼，執行其輸出傳送至 [輸出] 窗格，命令列程式和剖析標準的警告和錯誤訊息傳送至視窗時發生錯誤。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsLaunchPadFactory>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsLaunchPadFactory>|[是]|[是]|提供 factory 建立<xref:Microsoft.VisualStudio.Shell.Interop.IVsLaunchPad>物件。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.SVsLinkedUndoTransactionManager>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager>|[是]|[是]|已連結的復原管理員提供存取。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsMenuEditor>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMenuEditorFactory>|[是]|[是]|可讓表單設計工具來存取共用的功能表編輯器。 可以查詢 IVsMenuEditorFactory <xref:Microsoft.VisualStudio.Shell.Interop.IVsMenuEditor>。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext>|[是]|[是]|可讓 VSPackage 也可以建立的 「 內容包 」，用來建立關聯的特定內容的 Help 關鍵字。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsObjBrowser>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjBrowser>|[是]|[是]|可讓 VSPackage 也可以瀏覽至中的特定物件**物件瀏覽器**。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager>|[是]|[是]|可讓 VSPackage 也可以註冊其程式庫管理員[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]管理物件，例如命名空間、 類別和列舉型別。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectSearch>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectSearch>|[是]|[是]|可讓 VSPackage 也可以搜尋特定的物件。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsOpenProjectOrSolutionDlg>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOpenProjectOrSolutionDlg>|否|[是]|可讓 VSPackage 也可以使用標準[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]對話方塊，即可開啟專案或方案。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>|[是]|[是]|可讓 VSPackage 也可以在一般的 [輸出] 視窗中建立其他輸出窗格。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsParseCommandLine>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsParseCommandLine>|[是]|[是]|可讓實作者的<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>剖析命令列介面。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsPathVariableResolver>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPathVariableResolver>|否|[是]|提供方法來解決特定的變數[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]和內嵌於產生的最後一個路徑的路徑。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsPreviewChangesService>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPreviewChangesService>|否|[是]|顯示**預覽變更**用於重構程式碼的對話方塊。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsProfileDataManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProfileDataManager>|否|[是]|提供存取的設定檔管理員[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]讓匯入和匯出設定資料，以及顯示目前的使用者設定檔設定的 UI。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsProfilesManagerUI>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProfilesManagerUI>|否|[是]|顯示對話方塊，顯示目前的使用者設定檔設定。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsPropertyPageFrame>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPageFrame>|[是]|[是]|可讓 VSPackage 也可以覆寫的屬性頁中最先顯示**屬性**視窗。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|否|[是]|用來通知原始檔控制提供者檔案即將在記憶體中變更或儲存 Vspackage。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterDebugTargetProvider>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectDebugTargetProvider>|否|[是]|可讓 VSPackage 專案，以程式設計方式覆寫要啟動偵錯工具中的目標。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors>|[是]|[是]|可讓 VSPackage 也可以登錄 editor factory 與 IDE。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.SVsRegisterFindScope>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsRegisterFindScope>|否|[是]|可讓 VSPackage 也可以註冊的搜尋範圍**檔案中尋找** 對話方塊。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterPriorityCommandTarget>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>|[是]|[是]|可讓 VSPackage 登錄它自己做為高優先順序命令處理常式，可讓 VSPackage 也可以查看所有命令。 如果有的話，請謹慎地，使用。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>|[是]|[是]|可讓 VSPackage 也可以向 IDE 中的專案類型。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsResourceManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsResourceManager>|否|[是]|可讓 VSPackage 也可以從附屬 Dll 載入 managed 和 unmanaged 資源。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsResourceView>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsResourceView>|[是]|[是]|使用<xref:Microsoft.VisualStudio.Shell.Interop.SVsClassView>改為服務。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>|[是]|[是]|提供存取至 IDE 執行文件資料表 (RDT)，以追蹤所有目前開啟的文件。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|否|[是]|可讓 Vspackage 自我登錄與原始檔控制提供者，讓他們可以參與原始檔控制中。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccToolsOptions>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions>|[是]|[是]|可讓 VSPackage 取得和設定原始檔控制提供者選項。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSettingsReader>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader>|否|[是]|提供讀取存取權的使用者設定檔設定。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsShell>|[是]|[是]|可讓 VSPackage 也可以直接互動，及管理其他 Vspackage。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger>|[是]|[是]|提供存取[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯工具。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|[是]|[是]|可讓 VSPackage 也可以存取目前的選取範圍和管理命令 UI 內容。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVSMDCodeDomProvider>|IVSMDCodeDomProvider|否|[是]|提供存取權的程式碼文件物件模型 (DOM) 提供者可用於原生程式碼。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVSMDDesignerService>|IVSMDCodeDomCreator<br /><br /> IVSMDDesignerService|否|[是]|受管理的表單設計工具提供的存取權的 IDE 支援。 `IVSMDCodeDomCreator`可用來建立程式碼 DOM 提供者。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVSMDPropertyBrowser>|IVSMDPropertyBrowser|否|[是]|提供設計工具屬性的 windows 服務的存取權。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVSMDTypeResolutionService>|<xref:Microsoft.VisualStudio.Shell.Interop.IVSMDTypeResolutionService>|否|[是]|提供可傳回的介面存取<xref:System.ComponentModel.Design.ITypeResolutionService>原生程式碼中使用的物件。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSmartOpenScope>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSmartOpenScope>|否|[是]|提供開啟組件，列入考量所需的鎖定上之範圍的方法。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution>|[是]|[是]|提供最上層存取目前的方案。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager>|[是]|[是]|可讓 VSPackage 也可以與方案的建置程序互動。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionObject>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution>|[是]|[是]|使用<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>改為服務。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionPersistence>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>|[是]|[是]|可讓 VSPackage 也可以儲存和擷取目前方案的.sln 檔案中的資訊。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSQLCLRReferences>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSQLCLRReferences>|否|[是]|可讓您新增及更新參考 managed 程式碼組件中的。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStartPageDownload>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStartPageDownload>|否|[是]|提供啟動的頁面下載服務啟動及停止在背景執行緒上下載服務的存取權。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar>|[是]|[是]|提供 IDE 的 [狀態] 列的存取。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStrongNameKeys>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStrongNameKeys>|否|[是]|提供方法來建立強式金鑰名稱和金鑰的檔案具有用於簽署 managed 程式碼組件的密碼存取。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStructuredFileIO>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStructuredFileIO>|[是]|[是]|可讓 VSPackage 也可以提供以多種格式儲存資料的支援。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList>|[是]|[是]|提供存取 IDE 的 [工作清單] 視窗。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextImageUtilities>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextImageUtilities>|否|[是]|提供公用程式載入及儲存文字檔案。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>|[是]|[是]|提供存取所有文字緩衝區，以及在 IDE 中可用的 （如隱藏區域） 的隱藏的文字工作階段。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTextOut>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTextOut>|[是]|[是]|提供 Win32 版本`TextOut`函式，用於將文字寫入至裝置內容 （需要 DC 控制代碼）。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextSpanSet>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextSpanSet>|[是]|[是]|提供一份文字影像或緩衝區中的文字範圍的存取。 這個服務通常在文件的容器上實作，並會參考目前的文件。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsThreadedWaitDialog>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsThreadedWaitDialog>|否|[是]|可讓 VSPackage 也可以顯示不同的執行緒 （用來等待背景工作） 等待對話方塊。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsThreadPool>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsThreadPool>|否|[是]|可讓 VSPackage 也可以啟動背景工作，然後由維護[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox>|[是]|[是]|可讓您存取 IDE**工具箱**。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsToolboxActiveXDataProvider>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProvider>|[是]|[是]|可讓 VSPackage 也可以取得資訊從**工具箱**項目。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsToolboxDataProviderRegistry>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProviderRegistry>|否|[是]|可讓 VSPackage 也可以註冊的工具箱資料提供者，而不會產生效能成本預先載入整個**工具箱**。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsToolsOptions>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolsOptions>|否|[是]|可讓 VSPackage 也可以判斷如果**選項**對話方塊為開啟，以及重新整理所有的 [選項] 頁面的可見性。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3>|否|[是]|可讓 VSPackage 監視專案檔中的變更，並提供批次控制原始檔控制提供者。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|[是]|[是]|可讓 VSPackage 也可以通知 IDE 的變更可能會影響目前選取的專案項目選取項目。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelper>|[是]|[是]|協調其他階層剪貼簿中的使用可讓階層 （例如 VSPackage 專案）。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>|[是]|[是]|提供 IDE 的 UI 項目，例如工具視窗與文件視窗存取。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellDocumentWindowMgr>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellDocumentWindowMgr>|[是]|[是]|可讓 VSPackage 還原資料的資料流的內容為基礎的所有視窗的位置，或將所有視窗的位置儲存至資料流。 很少使用。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>|[是]|[是]|可讓 VSPackage 中透過許多方式開啟文件，並決定哪些文件擁有者是誰。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger>|否|[是]|使用的實作器<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>介面，以報告錯誤和參考用訊息。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsWebBrowsingService>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWebBrowsingService>|[是]|[是]|可讓 VSPackage 也可以建立和控制網頁瀏覽工作階段。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsWebFavorites>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWebFavorites>|[是]|[是]|可讓 VSPackage 也可以為該使用者新增**我的最愛**清單。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsWebPreview>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWebPreview>|[是]|[是]|可讓 VSPackage 也可以預覽網頁上，通常是在子視窗。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsWebURLMRU>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWebURLMRU>|[是]|[是]|可讓 VSPackage 將 URL 新增至 Url 的最近使用的 (MRU) 清單，以及取得 MRU 清單中的所有 Url 的清單。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsWindowFrame>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>|[是]|[是]|可讓 VSPackage 也可以取得視窗框架中的封裝的一部分可能平均分攤工作量。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsXMLMemberIndexService>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsXMLMemberIndexService>|[是]|[是]|提供特定的中繼資料檔案與相關聯的 XML 格式的文件檔案的存取權。|  
  
## <a name="see-also"></a>另請參閱  
 [COM 和受管理的服務](http://msdn.microsoft.com/en-us/6c5808b4-ad87-48d7-ae06-33a81e7052af)   
 [使用和提供服務](../../extensibility/using-and-providing-services.md)