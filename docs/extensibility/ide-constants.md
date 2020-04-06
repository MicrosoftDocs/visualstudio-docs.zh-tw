---
title: IDE 常量 |微軟文件
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc2eddac1cc7d7e616deb197752adf41a4d68d15
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710507"
---
# <a name="ide-constants"></a>IDE 常量

類<xref:Microsoft.VisualStudio.VSConstants>提供特定於整合式開發環境 (IDE) 且以前僅在標頭檔中定義的常量。

## <a name="logical-and-physical-views"></a>邏輯檢視與物理檢視

|值|描述|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`處理程式應將此值傳遞給<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法,以獲得 **「打開使用」** 對話方塊,在這種情況下,請處理可能的程式碼檢視。|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`處理程式將此值傳遞給<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法,以獲得 **「打開使用」** 對話方塊,在這種情況下,<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>填充了可能映射到的<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>相同檢視的調試檢視。|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`處理程式將此值傳遞給<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法以獲取 **「打開使用」** 對話框,在這種情況下,用於**查看窗體**設計器檢視。|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`處理程式將此值傳遞給<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法以獲取 **「打開使用」** 對話方塊,在這種情況下,編輯器工廠的預設/主視圖。|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`處理程式將此值傳遞給<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法,以獲得文件或資料文字編輯器檢視中的 **「打開」** 對話框。|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`處理程式將此值傳遞給方法,<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>該方法提示用戶選擇要使用的使用者定義的檢視。|

## <a name="editor-factory-flags"></a>編輯器工廠標誌

|值|描述|
|-----------|-----------------|
|[Cef。克隆檔案](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|過時的標誌按位方式組合為<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>方法的第一個參數。|
|[Cef。開放AsNew](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|按位方式組合為<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>方法的第一個參數,這表明編輯器工廠應執行必要的修復。|
|[Cef。開啟檔案](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|這個旗標<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>作為方法的第一個參數按位組合,是 CEF 的互斥[。複製檔案](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)。|
|[Cef。沉默](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|按位方式組合為<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>方法的第一個參數,這表明編輯器工廠應創建編輯器而不顯示使用者介面 (UI)。|

## <a name="visual-studio-errors"></a>視覺工作室錯誤

|值|描述|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|當有問題的物件在已經忙時,介面返回到異步行為的常量|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|特定於 Visual Studio 的「不相容文件資料」的錯誤 HRESULT。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|特定於 Visual Studio 並指示"未載入套件"的錯誤 HRESULT。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|特定於 Visual Studio 並指示「專案已存在」的錯誤 HRESULT。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|特定於 Visual Studio 並指示「專案設定失敗」的錯誤 HRESULT。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|特定於 Visual Studio 並指示「專案未載入」的錯誤 HRESULT。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|特定於 Visual Studio 並指示"解決方案已打開"的錯誤 HRESULT。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|特定於 Visual Studio 並指示"解決方案未打開"的錯誤 HRESULT。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|由具有用於從<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput>介面指定陣列的參數的生成介面返回,但實現只能將該方法應用於所有輸出。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|如果<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>文件的格式無法在編輯器中打開,則該方法將返回此值。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|HRESULT 值,指示用戶點擊可視化工作室嚮導中的後退按鈕。|

## <a name="visual-studio-constants"></a>視覺化工作室常數

|值|描述|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|特定於 Visual Studio 並指示「項目轉發」的錯誤 HRESULT。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|特定於「工具箱標記」的可視化工作室的常量。|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|特定於 Visual Studio 的常量,用於透過<xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A>指示模式開始的方法廣播通知訊息。|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|特定於 Visual Studio 的常量,用於透過<xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A>指示模式結束的方法廣播通知訊息。|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|特定於 Visual Studio 的常量,用於透過<xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A>指示命令列指標已更改的方法廣播通知訊息。|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|特定於 Visual Studio 的常量,指示尚未設置 Cookie。|
|[VSITEMID。零](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|表示缺少專案項的可視化工作室項標識符。 當沒有當前選擇時,將使用此值。|
|[VSITEMID。根](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|表示專案層次結構的根目錄的 Visual Studio 項識別碼,用於標識整個層次結構,而不是單個項。|
|[VSITEMID。選擇](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|表示當前選定的項或項的 Visual Studio 項識別碼,可以包括層次結構的根目錄。|

## <a name="ivsselectionevents"></a>IV 選擇事件
 例如,在<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>調用中描述剛剛選擇的 IDE 的哪些元件。

|持續性|值|
|--------------|-----------|
|[選擇元素.文件架構](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[選擇元素.屬性瀏覽器SID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[選擇元素.啟動項目](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[選擇元素.復原管理員](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[選擇元素.使用者上下文](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0 x 5|
|[選擇元素.視窗框架](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1|

## <a name="vsselelemid"></a>VSSELELEMID
 用於指示新選擇狀態的常量。

|持續性|值|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|2|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|7|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|4|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|6|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|3|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|0|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|5|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|1|

## <a name="component-selector-dialog-constants"></a>元件選擇器對話框常量

|持續性|值|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELCHANGED>|WM_USER = 1280|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELDBLCLICK>|WM_USER = 1281|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_CLEARSELECTION>|WM_USER = 1290|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_GETSELECTION>|WM_USER = 1287|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZELIST>|WM_USER = 1285|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZETAB>|WM_USER = 1288|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_QUERYCANSELECT>|WM_USER = 1286|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_SETMULTISELECT>|WM_USER = 1289|

## <a name="see-also"></a>另請參閱

- [擴充項目系統的 IDE 定義指令](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
