---
title: IDE 常數 |Microsoft Docs
description: VSConstants 類別提供 IDE 特有的常數，而且先前只定義在標頭檔中。
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- IDE, errors
- logical views
- errors [Visual Studio], IDE
- UI context constants
- constants, Visual Studio IDE
- IDE, constants
- physical views
ms.assetid: 5030e70a-241d-474a-ba8c-e3b1cf947ff0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c3a6e3c7460beb95ad410cead8bd644c37489e16
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883229"
---
# <a name="ide-constants"></a>IDE 常數

<xref:Microsoft.VisualStudio.VSConstants>類別會提供整合式開發環境 (IDE) 所特有的常數，以及之前只在標頭檔中定義的常數。

## <a name="logical-and-physical-views"></a>邏輯與實體的觀點

|值|描述|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`處理常式應該將此值傳遞給 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 方法，以取得 [**開啟方式**] 對話方塊，在此案例中可能是程式碼視圖。|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`處理常式會將此值傳遞給 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 方法，以取得 [**開啟方式**] 對話方塊，在此案例中，會使用 <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> 對應至相同視圖的可能偵錯工具視圖來填入 <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid> 。|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`處理常式會將此值傳遞給 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 方法，以取得 [**開啟方式**] 對話方塊，在此案例中是用來 **查看表單** 設計工具的視圖。|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`處理常式會將此值傳遞給 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 方法，以取得 [**開啟方式**] 對話方塊，在此案例中為編輯器 factory 的預設/主要視圖。|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`處理常式會將此值傳遞給 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 方法，以取得 [**開啟方式**] 對話方塊，在此為 [檔] 或 [資料文字編輯器] 視圖。|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`處理常式會將此值傳遞給方法，以 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 提示使用者選擇要使用的使用者定義視圖。|

## <a name="editor-factory-flags"></a>編輯器 Factory 旗標

|值|描述|
|-----------|-----------------|
|[Cef。CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|已淘汰的旗標，以位為方法的第一個參數 <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> 。|
|[Cef。OpenAsNew](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|將位結合為，方法的第一個參數 <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> ，表示編輯器 factory 應該執行必要的修正。|
|[Cef。OpenFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|將位結合為方法的第一個參數 <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> ，此旗標與 CEF 互斥 [。CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)。|
|[Cef。沉默](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|將位結合為方法的第一個參數 <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> ，這表示編輯器 factory 應該在不顯示使用者介面 (UI) 的情況下建立編輯器。|

## <a name="visual-studio-errors"></a>Visual Studio 錯誤

|值|描述|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|當有問題的物件已忙碌時，介面會傳回非同步行為的常數|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|「不相容的檔資料」 Visual Studio 特定的錯誤 HRESULT。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Visual Studio 的特定錯誤 HRESULT，指出「未載入封裝」。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Visual Studio 特定的錯誤 HRESULT，指出「專案已經存在」。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Visual Studio 特定的錯誤 HRESULT，指出「專案設定失敗」。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Visual Studio 的特定錯誤 HRESULT，指出「未載入專案」。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Visual Studio 所特有的錯誤 HRESULT，表示「解決方案已經開啟」。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Visual Studio 特定的錯誤 HRESULT，指出「未開啟方案」。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|由具有參數可從介面指定陣列的組建介面傳回 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> ，但實作為只能將方法套用至所有輸出。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>如果檔的格式無法在編輯器中開啟，則此方法會傳回這個值。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|HRESULT 值，指出使用者按 Visual Studio wizard 中的 [上一頁] 按鈕。|

## <a name="visual-studio-constants"></a>Visual Studio 常數

|值|描述|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Visual Studio 所特有的錯誤 HRESULT，表示「專案轉寄」。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|「工具箱標記」 Visual Studio 的特定常數。|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Visual Studio 特定的常數，可透過表示樣式開頭的方法廣播通知訊息 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> 。|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Visual Studio 特定的常數，可透過指出樣式結束的方法廣播通知訊息 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> 。|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Visual Studio 的常數，可透過方法來廣播通知訊息 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> ，指出命令列計量已變更。|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Visual Studio 的特定常數，表示尚未設定 cookie。|
|[VSITEMID.零](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|代表不存在專案專案的 Visual Studio 專案識別碼。 當目前沒有選取專案時，就會使用這個值。|
|[VSITEMID.根](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|代表專案階層之根的 Visual Studio 專案識別碼，用來識別整個階層，而不是單一專案。|
|[VSITEMID.選擇](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|Visual Studio 專案識別碼，代表目前選取的專案或專案，可以包含階層的根。|

## <a name="ivsselectionevents"></a>IVsSelectionEvents
 描述剛在呼叫中選取的 IDE 元件（ <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> 例如）。

|常數|值|
|--------------|-----------|
|[SelectionElement.DocumentFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[SelectionElement.PropertyBrowserSID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[SelectionElement. 啟始專案](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[SelectionElement. UndoManager](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[SelectionElement. UserCoNtext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5|
|[SelectionElement.WindowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1|

## <a name="vsselelemid"></a>VSSELELEMID
 用來表示新選取狀態的常數。

|常數|值|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|2|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|7|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|4|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|6|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|3|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|0|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|5|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|1|

## <a name="component-selector-dialog-constants"></a>元件選取器對話方塊常數

|常數|值|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELCHANGED>|WM_USER + 1280|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELDBLCLICK>|WM_USER + 1281|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_CLEARSELECTION>|WM_USER + 1290|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_GETSELECTION>|WM_USER + 1287|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZELIST>|WM_USER + 1285|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZETAB>|WM_USER + 1288|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_QUERYCANSELECT>|WM_USER + 1286|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_SETMULTISELECT>|WM_USER + 1289|

## <a name="see-also"></a>另請參閱

- [用來擴充專案系統的 IDE 定義的命令](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
