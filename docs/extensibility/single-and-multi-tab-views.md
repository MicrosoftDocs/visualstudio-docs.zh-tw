---
title: "單一和多重索引標籤檢視 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f20e5d251d8d6ef31289fb1b9ee8b9420ff9146a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="single-and-multi-tab-views"></a>單一和多重索引標籤檢視
編輯器可以建立不同類型的檢視。 其中一個範例的程式碼編輯器 視窗，另一個是表單設計工具。  
  
 多個索引標籤檢視是有多個索引標籤的檢視。 例如，HTML 編輯器中會有兩個索引標籤底部：**設計**和**來源**，每個邏輯檢視。 [設計] 檢視會顯示轉譯的網頁上，其他則會顯示包含網頁的 HTML。  
  
## <a name="accessing-physical-views"></a>存取實體的檢視  
 實體檢視裝載文件檢視物件，每個都代表資料緩衝區，程式碼或表單中的檢視。 因此，每個文件檢視物件具有實體檢視 （稱為實體檢視字串的項目所識別），和通常單一邏輯檢視。  
  
 不過，在某些情況下，實體檢視可以有兩個或多個邏輯檢視。 具有分隔視窗具有由並排檢視的編輯器或具有 GUI/設計檢視和程式碼後置--格式檢視的表單設計工具的一些範例。  
  
 若要啟用您的編輯器，來存取所有可用的實體檢視，您必須建立每種類型的編輯器 factory 可以建立的文件檢視物件的唯一實體檢視字串。 例如，[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]編輯器 factory 可以建立文件檢視物件的程式碼視窗和表單的設計工具視窗。  
  
## <a name="creating-multi-tabbed-views"></a>建立多個索引標籤的檢視  
 雖然文件檢視物件必須是透過唯一的實體檢視字串的實體檢視相關聯，您可以將實體的檢視，若要啟用不同的方式檢視的資料內的多個索引標籤。 上述多個索引標籤的設定，所有索引標籤與相關聯的實體檢視相同的字串，但每個索引標籤會指定不同的邏輯檢視 GUID。  
  
 若要建立多個索引標籤檢視編輯器中，實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView>介面，並將產生關聯的不同的邏輯檢視 GUID (<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>) 在您建立的每個索引標籤。  
  
 Visual Studio HTML 編輯器是具有多個索引標籤檢視編輯器的範例。 它有**設計**和**來源**索引標籤。 若要啟用此功能，不同的邏輯檢視為每個索引標籤上，與相關聯`LOGICALVIEWID_TextView`如**設計** 索引標籤和`LOGICALVIEWID_Code`的**來源** 索引標籤。  
  
 藉由指定適當的邏輯檢視，VSPackage 可以存取對應至某特定用途，例如設計表單、 編輯程式碼，或偵錯程式碼的檢視。 不過，其中一個視窗必須以 NULL 字串識別，且這必須與主要的邏輯檢視 (`LOGVIEWID_Primary`)。  
  
 下表列出可用的邏輯檢視值以及其用法。  
  
|LOGVIEWID GUID|建議的使用|  
|--------------------|---------------------|  
|`LOGVIEWID_Primary`|編輯器 factory 的預設/主要資料庫檢視。<br /><br /> 所有編輯器 factory 必須都支援此值。 此檢視必須使用其實體檢視字串 NULL 字串。 至少一個邏輯檢視，必須設定為這個值。|  
|`LOGVIEWID_Debugging`|偵錯檢視。 一般而言，`LOGVIEWID_Debugging`對應至相同的檢視為`LOGVIEWID_Code`。|  
|`LOGVIEWID_Code`|檢視由啟動**檢視程式碼**命令。|  
|`LOGVIEWID_Designer`|檢視由啟動**檢視表單**命令。|  
|`LOGVIEWID_TextView`|文字編輯器檢視。 這是傳回檢視<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>，從您可以存取<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。|  
|`LOGVIEWID_UserChooseView`|會提示使用者選擇要使用的檢視。|  
|`LOGVIEWID_ProjectSpecificEditor`|傳**開啟** 對話方塊<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> 當使用者選擇 」 （專案預設編輯器） 」 項目。|  
  
 雖然可延伸邏輯檢視的 Guid，但是您可以使用只有在 VSPackage 中定義的邏輯檢視 Guid。  
  
 在關閉時，Visual Studio 會保留，使它可以用來重新開啟方案時，重新開啟文件視窗與文件視窗相關聯的實體檢視字串編輯器 factory 的 GUID。 關閉方案時開啟的視窗會保存在方案 (.suo) 檔案。 這些值對應至`VSFPROPID_guidEditorType`和`VSFPROPID_pszPhysicalView`傳入值`propid`中的參數<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>方法。  
  
## <a name="example"></a>範例  
 這個程式碼片段將說明如何<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView>物件用來存取檢視可實作`IVsCodeWindow`。 在此情況下，<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>服務用來呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A>和要求`LOGVIEWID_TextView`，從中取得視窗框架的指標。 文件檢視物件的指標透過呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>和指定的值是`VSFPROPID_DocView`。 文件檢視物件中，從`QueryInterface`稱為`IVsCodeWindow`。 預期的情況下在此情況下會傳回文字編輯器，，和文件檢視物件中傳回的因此<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>方法是在程式碼視窗。  
  
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
  
## <a name="see-also"></a>請參閱  
 [支援多個文件檢視](../extensibility/supporting-multiple-document-views.md)   
 [如何： 將附加至文件資料的檢視](../extensibility/how-to-attach-views-to-document-data.md)   
 [建立自訂編輯器和設計工具](../extensibility/creating-custom-editors-and-designers.md)