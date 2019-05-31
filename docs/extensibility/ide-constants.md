---
title: IDE 常數 |Microsoft Docs
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
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d16b758a34eb1b9f48e912f75c4eec144a07ce4a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311321"
---
# <a name="ide-constants"></a>IDE 常數

<xref:Microsoft.VisualStudio.VSConstants>類別提供特定的整合式的開發環境 (IDE) 和先前定義只在標頭檔中的常數。

## <a name="logical-and-physical-views"></a>邏輯與實體的檢視

|值|描述|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` 處理常式應將此值，以傳遞<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法來取得**開啟**對話方塊中，在此情況下可能的程式碼檢視。|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` 處理常式會傳遞此值可<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法來取得**開啟**對話方塊中，在此情況下填入可能<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>偵錯檢視這些項目對應至相同的檢視為<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>。|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` 處理常式會傳遞此值可<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法來取得**開啟**對話方塊中，在此情況下，若要**檢視表單**設計工具檢視。|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` 處理常式會傳遞此值可<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法來取得**開啟**對話方塊中，在此情況下編輯器 factory 的預設/主要資料庫檢視。|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` 處理常式會傳遞此值可<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法來取得**開啟**對話方塊中，在此文件或資料的文字編輯器檢視。|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` 處理常式會傳遞此值以<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>系統會提示使用者選擇要使用哪一個使用者定義檢視的方法。|

## <a name="editor-factory-flags"></a>編輯器 Factory 旗標

|值|描述|
|-----------|-----------------|
|[CEF.CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|過時的旗標位元的第一個參數為結合<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>方法。|
|[CEF.OpenAsNew](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|合併的第一個參數的位元<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>，這方法，表示編輯器 factory 應該執行必要的修正程式。|
|[CEF.OpenFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|合併的第一個參數的位元<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>方法，這個旗標是互斥的[CEF。CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)。|
|[CEF.Silent](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|合併的第一個參數的位元<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>方法，這會指示編輯器 factory 應該建立編輯器，而不顯示使用者介面 (UI)。|

## <a name="visual-studio-errors"></a>Visual Studio 錯誤

|值|描述|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|傳回非同步行為介面的常數時在該物件中已忙碌|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|錯誤是 Visual Studio 的 「 不相容的文件資料 」 特定的 HRESULT。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|錯誤 HRESULT 的特定 Visual Studio，並指出 「 無法載入套件 」。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|錯誤 HRESULT 的特定 Visual Studio，並指出 「 專案已經存在 」。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|錯誤 HRESULT 專屬於 Visual Studio，並指出 「 專案組態失敗。 」|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|錯誤 HRESULT 的特定 Visual Studio，並指出 「 專案未載入。 」|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|錯誤 HRESULT 的特定 Visual Studio，並指出 「 已開啟解決方案。 」|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|錯誤 HRESULT 專屬於 Visual Studio，並指出 「 無法開啟解決方案。 」|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|傳回由參數指定的陣列，從組建介面<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput>介面，但在實作僅適用於方法的所有輸出。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>方法會傳回此值，如果文件的格式，不能在編輯器中開啟。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|HRESULT 值，指出使用者叫用 Visual Studio 精靈中的 [上一頁] 按鈕。|

## <a name="visual-studio-constants"></a>Visual Studio 常數

|值|描述|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|錯誤 HRESULT 的特定 Visual Studio，並指出 「 專案轉送 」。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|常數，它是特定 Visual studio 的 「 工具箱標記 」。|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|廣播透過通知訊息是特定 Visual studio 的常數<xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A>方法表示強制回應性的開頭。|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|廣播透過通知訊息是特定 Visual studio 的常數<xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A>表示強制回應性的結尾的方法。|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|廣播透過通知訊息是特定 Visual studio 的常數<xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A>指出已變更的命令列計量的方法。|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|常數，表示未設定 cookie 的 Visual Studio 特定的。|
|[VSITEMID.Nil](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|代表專案項目不存在的 Visual Studio 項目識別碼。 沒有目前的選取項目時，會使用此值。|
|[VSITEMID.Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|Visual Studio 項目識別項，其代表專案階層的根，並可用來識別整個階層中的，而不是單一項目。|
|[VSITEMID.Selection](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|Visual Studio 項目識別項，表示目前選取的項目或項目，它可以包含階層的根。|

## <a name="ivsselectionevents"></a>IVsSelectionEvents
 描述 IDE 的哪些元件只是已選取，在<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>呼叫，例如。

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

- [IDE 定義的命令，來擴充專案系統](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)