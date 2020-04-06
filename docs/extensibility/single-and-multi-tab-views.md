---
title: 單選項卡和多選項卡視圖 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c308b4d6c7b90456255019ef57c6b9d544aefc77
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699982"
---
# <a name="single-and-multi-tab-views"></a>單一和多重索引標籤檢視
編輯器可以創建不同類型的檢視。 一個範例是代碼編輯器視窗,另一個是表單設計器。

 多選項卡檢視是具有多個選項卡的視圖。 例如,HTML 編輯器底部有兩個選項卡:**設計和****源**,每個選項卡都是邏輯檢視。 設計檢視顯示呈現的網頁,而另一個顯示包含網頁的 HTML。

## <a name="accessing-physical-views"></a>存取物理檢視
 物理檢視承載文檔檢視物件,每個物件表示緩衝區中數據視圖,如代碼或窗體。 因此,每個文檔檢視物件都有一個物理視圖(由稱為物理視圖字串串的東西標識),通常只有一個邏輯視圖。

 但是,在某些情況下,物理視圖可以具有兩個或多個邏輯視圖。 一些範例是具有並行檢視的分割視窗的編輯器,或者具有 GUI/設計視圖和代碼後窗體檢視的表單表的表單設計器。

 要使編輯器能夠造訪所有可用的物理檢視,必須為編輯器工廠可以創建的每種類型的文件檢視物件創建唯一的物理檢視字串。 例如,[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]編輯器工廠可以為代碼視窗和窗體設計器視窗創建文檔檢視物件。

## <a name="creating-multi-tabbed-views"></a>建立多選項卡檢視
 儘管文件檢視對象必須透過唯一的物理視圖字串與物理檢視關聯,但您可以在物理檢視中放置多個選項卡,以便以不同的方式查看數據。 在此多選項卡配置中,所有選項卡都與同一物理視圖字串相關聯,但每個選項卡都給定不同的邏輯視圖 GUID。

 要為編輯器建立多選項卡檢視,請實現介面,<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView>然後將不同的邏輯檢視 GUID<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>( ) 與創建的每個選項卡相關聯。

 Visual Studio HTML 編輯器是具有多選項卡檢視的編輯器的範例。 它有**設計和****來源**「選項卡。 為此,不同的邏輯檢視與每個選項卡`LOGICALVIEWID_TextView`**、「設計」** 選項卡和`LOGICALVIEWID_Code`**「源」** 選項卡相關聯。

 通過指定適當的邏輯檢視,VSPackage 可以造訪對應於特定用途的檢視,例如設計窗體、編輯代碼或調試代碼。 但是,其中一個窗口必須由 NULL 字串標識,並且必須對應於主邏輯視圖 ()。`LOGVIEWID_Primary`

 下表列出了可用的邏輯視圖值及其使用。

|紀錄圖代碼|推薦使用|
|--------------------|---------------------|
|`LOGVIEWID_Primary`|編輯器工廠的預設/主視圖。<br /><br /> 所有編輯器工廠都必須支援此值。 此檢視必須使用 NULL 字串作為其物理檢視字串。 必須至少將一個邏輯視圖設置為此值。|
|`LOGVIEWID_Debugging`|調試視圖。 通常,`LOGVIEWID_Debugging`映射到與相同檢視`LOGVIEWID_Code`。|
|`LOGVIEWID_Code`|**查看由「查看代碼」** 命令啟動的檢視。|
|`LOGVIEWID_Designer`|**視圖由「查看窗體」** 命令啟動。|
|`LOGVIEWID_TextView`|文字編輯器檢視。 這是傳<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>回的檢視,可以從中存<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>取 。|
|`LOGVIEWID_UserChooseView`|提示用戶選擇要使用的檢視。|
|`LOGVIEWID_ProjectSpecificEditor`|以 **「開啟使用」** 對話框傳遞到<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> 當用戶選擇「(專案默認編輯器)」條目時。|

 儘管邏輯檢視 GUID 是可擴展的,但只能使用 VSPackage 中定義的邏輯視圖 GUID。

 關閉後,Visual Studio 會保留編輯器工廠的 GUID 以及與文檔視窗關聯的物理檢視字串,以便在重新打開解決方案時使用它重新打開文件視窗。 只有關閉解決方案時打開的視窗才會保留在解決方案 (.suo) 檔中。 這些`VSFPROPID_guidEditorType`值對應於`VSFPROPID_pszPhysicalView``propid`<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>方法中參數中傳遞的 和值。

## <a name="example"></a>範例
 此程式碼段說明瞭如何<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView>使用 對`IVsCodeWindow`象訪問實現的檢視。 在這種情況下,<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>服務用於呼<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A>叫和`LOGVIEWID_TextView`請求 ,獲取指向視窗框的指標。 通過調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>和指定的`VSFPROPID_DocView`值 ,獲得指向文檔視圖物件的指標。 從文件檢視物件中,`QueryInterface`呼叫`IVsCodeWindow`。 在這種情況下,期望返回文本編輯器,因此<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>在方法中返回的文檔檢視對像是一個代碼視窗。

```cpp
HRESULT CFindTool::GotoFileLocation(const WCHAR * szFile, long iLine, long iStart, long iLen)
{
  HRESULT hr;
  if (NULL == szFile || !*szFile)
    return E_INVALIDARG;

  if (iLine == -1L)
    return S_FALSE;

  VSITEMID                  itemid;
  VARIANT                   var;
  RECT                      rc;
  IVsUIShellOpenDocument *  pOpenDoc    = NULL;
  IVsCodeWindow *           pCodeWin    = NULL;
  IVsTextView *             pTextView   = NULL;
  IVsUIHierarchy *          pHierarchy  = NULL;
  IVsWindowFrame *          pFrame      = NULL;
  IUnknown *                pUnk        = NULL;
  IVsHighlight *            pHighlight  = NULL;

  IfFailGo(CGlobalServiceProvider::HrQueryService(SID_SVsUIShellOpenDocument, IID_IVsUIShellOpenDocument, (void **)&pOpenDoc));
  IfFailGo(pOpenDoc->OpenDocumentViaProject(szFile, LOGVIEWID_TextView, NULL, &pHierarchy, &itemid, &pFrame));
  pFrame->Show();
  VariantInit(&var);
  IfFailGo(pFrame->GetProperty(VSFPROPID_DocView, &var));
  if (VT_UNKNOWN != var.vt) { hr = E_FAIL; goto Error; }
  pUnk = V_UNKNOWN(&var);
  if (NULL != pUnk)
  {
    IfFailGo(pUnk->QueryInterface(IID_IVsCodeWindow, (void **)&pCodeWin));
    if (SUCCEEDED(hr = pCodeWin->GetLastActiveView(&pTextView)) ||
        SUCCEEDED(hr = pCodeWin->GetPrimaryView(&pTextView)) )
    {
      pTextView->SetSelection(iLine, iStart, iLine, iStart + iLen);
      // uncover selection
      IfFailGo(pTextView->QueryInterface(IID_IVsHighlight, (void**)&pHighlight));
      IfFailGo(SUCCEEDED(pHighlight->GetHighlightRect(&rc)));
      UncoverSelectionRect(&rc);
    }
  }

Error:
  CLEARINTERFACE(pHighlight);
  CLEARINTERFACE(pTextView);
  CLEARINTERFACE(pCodeWin);
  CLEARINTERFACE(pUnk);
  CLEARINTERFACE(pFrame);
  CLEARINTERFACE(pOpenDoc);
  CLEARINTERFACE(pHierarchy);
  RedrawWindow(m_hwndResults, NULL, NULL, RDW_ERASE|RDW_FRAME|RDW_INVALIDATE|RDW_ALLCHILDREN);
  return hr;
}
```

## <a name="see-also"></a>另請參閱
- [支援多個文件檢視](../extensibility/supporting-multiple-document-views.md)
- [如何︰將檢視附加至文件資料](../extensibility/how-to-attach-views-to-document-data.md)
- [建立自訂編輯器和設計工具](../extensibility/creating-custom-editors-and-designers.md)
