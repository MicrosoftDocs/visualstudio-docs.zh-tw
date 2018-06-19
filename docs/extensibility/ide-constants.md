---
title: IDE 常數 |Microsoft 文件
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
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
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e9c7e870b02dbe5a903ca8195954ffd5a8f63549
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133095"
---
# <a name="ide-constants"></a>IDE 常數

<xref:Microsoft.VisualStudio.VSConstants>類別會提供的常數特有的整合式的開發環境 (IDE) 和先前定義只能在標頭檔中。

## <a name="logical-and-physical-views"></a>邏輯與實體的檢視

|值|描述|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` 處理常式應該此值傳遞至<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法來取得**開啟**對話方塊中，在此情況下，在可能的程式碼檢視。|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` 處理常式此值傳遞至<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法來取得**開啟**對話方塊中，在此情況下填入可能<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>偵錯檢視對應到相同的檢視為<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>。|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` 處理常式此值傳遞至<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法來取得**開啟**對話方塊中的，在這種情況下**檢視表單**設計工具檢視。|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` 處理常式此值傳遞至<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法來取得**開啟**對話方塊中，在此情況下編輯器 factory 的預設/主要資料庫檢視。|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` 處理常式此值傳遞至<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法來取得**開啟**對話方塊中，在此文件或資料的文字編輯器檢視。|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` 處理常式此值傳遞至<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>以提示使用者選擇要使用哪一個使用者定義檢視的方法。|

## <a name="editor-factory-flags"></a>編輯器 Factory 旗標

|值|描述|
|-----------|-----------------|
|[CEF.CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|過時的旗標做為第一個參數的位元結合<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>方法。|
|[CEF.OpenAsNew](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|組合的位元的第一個參數為<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>，此方法，指出編輯器 factory 應該執行必要的修正程式。|
|[CEF.OpenFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|組合的位元的第一個參數為<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>方法，這個旗標都是互相 exclusive [CEF。CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)。|
|[CEF.Silent](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|組合的位元的第一個參數為<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>方法，這會指示編輯器 factory 應該建立編輯器，而不會顯示使用者介面 (UI)。|

## <a name="visual-studio-errors"></a>Visual Studio 錯誤

|值|描述|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|介面返回非同步行為常數時在該物件中已忙碌|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|特定的 HRESULT 錯誤[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]的 「 不相容的文件資料 」。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|特定的 HRESULT 錯誤[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]和，指出 「 無法載入封裝 」。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|特定的 HRESULT 錯誤[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，表示 「 專案已經存在 」。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|特定的 HRESULT 錯誤[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]和，指出 「 專案組態失敗。 」|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|特定的 HRESULT 錯誤[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]和，指出 「 無法載入專案 」。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|特定的 HRESULT 錯誤[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]和，指出 「 解決方案已經開啟。 」|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|特定的 HRESULT 錯誤[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]和，指出 「 解決方案未開啟。 」|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|傳回由參數指定的陣列，從組建介面<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput>介面，但實作可以只將方法套用到所有輸出。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>方法會傳回此值，如果文件的格式，無法在編輯器中開啟。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|HRESULT 值，指出使用者叫用中的上一頁按鈕[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]精靈。|

## <a name="visual-studio-constants"></a>Visual Studio 常數

|值|描述|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|特定的 HRESULT 錯誤[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]和，指出 「 轉送專案 」。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|常數的特定[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]"工具箱標記 」。|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|常數的特定[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]廣播透過通知訊息<xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A>方法表示的樣式開頭。|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|常數的特定[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]廣播透過通知訊息<xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A>方法，表示樣式的結尾。|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|常數的特定[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]廣播通知訊息透過<xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A>指出已變更的命令列度量資訊的方法。|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|常數的特定[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，表示尚未設定 cookie。|
|[VSITEMID.Nil](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|A[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]表示專案項目不存在的項目識別項。 沒有目前的選取項目時，會使用此值。|
|[VSITEMID.Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|A[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]代表專案階層架構的根，用來識別整個階層，而不是單一項目項目識別項。|
|[VSITEMID.Selection](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|A [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，代表目前選取的項目或項目，可以包含階層的根項目識別項。|

## <a name="ivsselectionevents"></a>IVsSelectionEvents
 描述 IDE 的哪個元件只選取了，在<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>呼叫，例如。

|常數|值|
|--------------|-----------|
|[SelectionElement.DocumentFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[SelectionElement.PropertyBrowserSID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[SelectionElement.StartupProject](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[SelectionElement.UndoManager](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[SelectionElement.UserContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5|
|[SelectionElement.WindowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1|

## <a name="vsselelemid"></a>VSSELELEMID
 用來指出新的選取狀態的常數。

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