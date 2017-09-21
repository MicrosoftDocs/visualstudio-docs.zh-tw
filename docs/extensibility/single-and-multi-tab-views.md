---
title: "單一和多重] 索引標籤檢視 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，自訂-單一和多重] 索引標籤檢視"
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# 單一和多重] 索引標籤檢視
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

編輯器可建立不同類型的檢視。  例如，程式碼編輯器\] 視窗，另一個是表單設計工具。  
  
 多個索引標籤檢視是一種檢視，有多個索引標籤。  例如，HTML 編輯器有兩個索引標籤下方： **設計** 和 **來源**，每個邏輯檢視。  \[設計\] 檢視會顯示呈現的 web 網頁，而另一個則顯示包含在 web 網頁的 HTML。  
  
## 存取實體檢視  
 實體檢視主控文件檢視物件，每個都代表一個緩衝區，例如程式碼或表單中的資料檢視。  因此，每個文件檢視物件所具有的實體檢視 \(由稱為實體檢視字串的項目\)，而且通常是單一的邏輯檢視。  
  
 不過，在某些情況下，實體的檢視可以有兩個以上的邏輯檢視。  已分割視窗並排顯示的檢視編輯器\] 或 \[表單設計工具的 GUI\/設計檢視\] 和 \[程式碼後置\-\-形狀的檢視，是一些範例。  
  
 若要讓您存取所有可用的實體檢視的編輯器，您必須建立唯一的實體檢視字串，每一種編輯器工廠可以建立的文件檢視物件。  例如， [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]編輯器工廠可以建立文件程式碼\] 視窗和表單的設計工具視窗的檢視物件。  
  
## 建立多個索引標籤中的資料檢視表  
 雖然文件檢視物件必須是唯一的實體檢視字串透過實體檢視相關聯，您可以將實體的檢視表，以便以不同的方式檢視的資料中的多個索引標籤。  在此多個索引標籤的設定，所有索引標籤會以相同的實體檢視字串相關聯，但每個索引標籤會提供不同的邏輯檢視 GUID。  
  
 若要建立多個索引標籤檢視的編輯器，請實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView>介面，並將產生關聯的不同的邏輯檢視 GUID \(<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>\) 在您建立的每個索引標籤。  
  
 Visual Studio 的 HTML 編輯器是使用 multi\-tab 檢視編輯器的範例。  它有**設計** 和 **來源**索引標籤。  若要啟用這種情況，不同的邏輯檢視已經有每個索引標籤中， `LOGICALVIEWID_TextView`的**設計** \] 索引標籤和`LOGICALVIEWID_Code`的**來源** \] 索引標籤。  
  
 藉由指定適當的邏輯檢視，VSPackage 可以存取檢視對應於某特定用途，例如設計表單\]、 \[編輯程式碼，或 \[偵錯程式碼。  不過，其中一個視窗必須由 NULL 字串，且這必須對應到主要的邏輯檢視 \(`LOGVIEWID_Primary`\)。  
  
 下表列出可用的邏輯檢視值以及其用法。  
  
|LOGVIEWID 的 GUID|建議的使用|  
|----------------------|-----------|  
|`LOGVIEWID_Primary`|編輯器原廠預設值\/主檢視。<br /><br /> 所有編輯器工廠必須都支援此值。  此檢視作為它的實體檢視字串，必須使用 NULL 字串。  必須設定一個以上的邏輯檢視，此值。|  
|`LOGVIEWID_Debugging`|偵錯的檢視。  一般而言， `LOGVIEWID_Debugging`會對應到相同的檢視，做為`LOGVIEWID_Code`。|  
|`LOGVIEWID_Code`|檢視由啟動**檢視程式碼**指令。|  
|`LOGVIEWID_Designer`|檢視由啟動**檢視表單**指令。|  
|`LOGVIEWID_TextView`|文字編輯器檢視。  這是檢視，會傳回<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>，您可以存取從<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。|  
|`LOGVIEWID_UserChooseView`|會提示使用者選擇使用何種檢視。|  
|`LOGVIEWID_ProjectSpecificEditor`|傳址方式傳遞**開啟** \] 對話方塊<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> 當使用者選擇"\(專案預設編輯器\) 」 項目。|  
  
 雖然邏輯檢視 Guid 是可擴充的您可以使用 \[只在您的 VSPackage 中定義的邏輯檢視 Guid。  
  
 在關機時，Visual Studio 會保留編輯器工廠和實體檢視字串，讓它可以用來重新開啟文件視窗，當方案被重新開啟時，與文件視窗相關聯的 GUID。  方案關閉時開啟的視窗會保存方案 \(.suo\) 檔案中。  這些值會對應至`VSFPROPID_guidEditorType`和`VSFPROPID_pszPhysicalView`傳入的值`propid`中的參數<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>方法。  
  
## 範例  
 此程式碼片段將說明如何<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView>物件用來檢視存取實作`IVsCodeWindow`。  如此一來， <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>服務用來呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> ，也會要求`LOGVIEWID_TextView`，它會取得視窗框架的指標。  文件的檢視物件的指標藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> ，並指定值為`VSFPROPID_DocView`。  文件的檢視物件，從`QueryInterface`會針對呼叫`IVsCodeWindow`。  在預期的情況，在這個案例是傳回文字編輯器，且因此文件檢視傳回的物件在<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>方法是程式碼\] 視窗。  
  
```cpp#  
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
  
## 請參閱  
 [支援多個文件檢視](../extensibility/supporting-multiple-document-views.md)   
 [如何︰ 附加至文件資料的檢視](../extensibility/how-to-attach-views-to-document-data.md)   
 [建立自訂編輯器和設計工具](../extensibility/creating-custom-editors-and-designers.md)