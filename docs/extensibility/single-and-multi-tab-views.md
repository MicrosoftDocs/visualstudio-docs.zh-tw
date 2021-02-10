---
title: 單一和多重索引標籤的視圖 |Microsoft Docs
description: 瞭解如何在編輯器（例如程式碼編輯器視窗和表單設計工具）中執行多個索引標籤的查看。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6cea04557fb0bf3075461b22979cac2168af322
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942980"
---
# <a name="single-and-multi-tab-views"></a>單一和多重索引標籤檢視
編輯器可以建立不同類型的視圖。 其中一個範例是 [程式碼編輯器] 視窗，另一個則是表單設計工具。

 多索引標籤式的視圖是具有多個索引標籤的視圖。 例如，HTML 編輯器在底部有兩個索引標籤： [ **設計** ] 和 [ **來源**]，每一個都是邏輯視圖。 設計檢視會顯示呈現的網頁，而另一個則會顯示包含網頁的 HTML。

## <a name="accessing-physical-views"></a>存取實體視圖
 實體視圖會裝載文檔視圖物件，每個物件都代表緩衝區中的資料檢視，例如程式碼或表單。 因此，每個檔視圖物件都有實體視圖 (由稱為實體 view 字串) 識別，通常是單一邏輯視圖。

 不過，在某些情況下，實體視圖可以有兩個以上的邏輯視圖。 某些範例是具有分割視窗和並排顯示的編輯器，或是具有 GUI/設計檢視和程式碼後置於表單設計檢視的表單設計工具。

 若要讓您的編輯器可以存取所有可用的實體視圖，您必須為編輯器 factory 可建立的每個檔視圖物件類型建立唯一的實體視圖字串。 例如， [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 編輯器 factory 可以建立程式碼視窗和表單設計工具視窗的檔視圖物件。

## <a name="creating-multi-tabbed-views"></a>建立多個索引標籤式的視圖
 雖然檔視圖物件必須透過唯一的實體視圖字串與實體視圖相關聯，您可以在實體視圖內放置多個索引標籤，以不同的方式來啟用資料的查看。 在這個多索引標籤式設定中，所有索引標籤都與相同的實體視圖字串相關聯，但每個索引標籤都有不同的邏輯視圖 GUID。

 若要為編輯器建立多個索引標籤式的視圖，請執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> 介面，然後將不同的邏輯視圖 GUID (<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>) 與您建立的每個索引標籤建立關聯。

 Visual Studio HTML 編輯器是具有多個索引標籤視圖的編輯器範例。 它有 [ **設計** ] 和 [ **來源** ] 索引標籤。 若要啟用此功能，您可以 `LOGICALVIEWID_TextView` 在 [ **設計** ] 索引標籤和 `LOGICALVIEWID_Code` [ **來源** ] 索引標籤上，將不同的邏輯視圖與每個索引標籤

 藉由指定適當的邏輯視圖，VSPackage 可以存取對應至特定用途的視圖，例如設計表單、編輯程式碼或偵錯工具代碼。 但是，其中一個視窗必須以 Null 字串來識別，且必須對應至主要邏輯視圖 (`LOGVIEWID_Primary`) 。

 下表列出可用的邏輯視圖值及其用法。

|LOGVIEWID GUID|建議使用|
|--------------------|---------------------|
|`LOGVIEWID_Primary`|編輯器 factory 的預設/主要視圖。<br /><br /> 所有編輯器 factory 都必須支援這個值。 此視圖必須使用 Null 字串作為其實體視圖字串。 至少必須將一個邏輯視圖設定為此值。|
|`LOGVIEWID_Debugging`|調試的觀點。 一般而言，會 `LOGVIEWID_Debugging` 對應至與相同的視圖 `LOGVIEWID_Code` 。|
|`LOGVIEWID_Code`|View **Code** 命令啟動。|
|`LOGVIEWID_Designer`|View **Form** 命令啟動。|
|`LOGVIEWID_TextView`|文字編輯器視圖。 這是傳回的視圖 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> ，您可以從中存取 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 。|
|`LOGVIEWID_UserChooseView`|提示使用者選擇要使用的視圖。|
|`LOGVIEWID_ProjectSpecificEditor`|由 [ **開啟方式** ] 對話方塊傳遞至<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> 當使用者選擇 [ (專案預設編輯器) ] 專案時。|

 雖然邏輯視圖 Guid 是可擴充的，但您只能使用 VSPackage 中所定義的邏輯視圖 Guid。

 在關機時，Visual Studio 會保留編輯器 factory 的 GUID 以及與文件視窗相關聯的實體視圖字串，以便在重新開啟方案時，用它來重新開啟文件視窗。 只有在關閉方案時開啟的視窗，會保存在解決方案 () 檔案中。 這些值會對應至 `VSFPROPID_guidEditorType` `VSFPROPID_pszPhysicalView` 方法中的參數所傳入的和值 `propid` <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 。

## <a name="example"></a>範例
 此程式碼片段說明如何 <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> 使用物件來存取可執行檔視圖 `IVsCodeWindow` 。 在此情況下， <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> 服務會用來呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> 和要求 `LOGVIEWID_TextView` ，以取得視窗框架的指標。 您可以呼叫並指定的值，以取得檔視圖物件的指標 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> `VSFPROPID_DocView` 。 在檔視圖物件中， `QueryInterface` 會呼叫 `IVsCodeWindow` 。 在此情況下，預期會傳回文字編輯器，因此在此方法中傳回的檔視圖物件 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 就是程式碼視窗。

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
