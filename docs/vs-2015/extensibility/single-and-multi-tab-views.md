---
title: 單一和多重索引標籤的檢視 |Microsoft Docs
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
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8231581761199be4df9c368494fb27bdc7926c51
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51748986"
---
# <a name="single-and-multi-tab-views"></a>單一和多重索引標籤檢視
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

編輯器可以建立不同類型的檢視。 其中一個範例的程式碼編輯器 視窗，另一個是表單設計工具。  
  
 多個索引標籤的檢視是具有多個索引標籤的檢視。 例如，HTML 編輯器有兩個索引標籤底部：**設計**並**來源**，每個邏輯檢視。 [設計] 檢視會顯示呈現的網頁，而另一個則顯示包含網頁的 HTML。  
  
## <a name="accessing-physical-views"></a>存取實體的檢視  
 實體的檢視裝載的文件檢視物件，每個都代表一個緩衝區，例如程式碼或表單中的資料檢視。 因此，每個文件檢視物件有一個實體檢視 （又稱為實體檢視字串所識別），以及通常是單一的邏輯檢視。  
  
 不過，在某些情況下，實體的檢視可以有兩個或多個邏輯檢視。 已分隔視窗並排顯示檢視的編輯器] 或 [表單設計工具有 GUI/設計檢視與程式碼後置--格式檢視的一些範例。  
  
 若要讓您存取所有可用的實體檢視的編輯器，您必須建立每種類型的編輯器 factory 可以建立的文件檢視物件的唯一實體檢視字串。 比方說，[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]編輯器 factory 可以建立文件的程式碼視窗和表單設計工具視窗的檢視物件。  
  
## <a name="creating-multi-tabbed-views"></a>建立多個索引標籤檢視  
 雖然文件檢視物件必須是唯一的實體檢視字串的實體檢視相關聯，您可以將不同的方式啟用檢視的資料實體的檢視中的多個索引標籤。 在這個多索引標籤 」 組態中，所有索引標籤會與相同的實體檢視字串中，相關聯，但每個索引標籤會提供不同的邏輯檢視 GUID。  
  
 若要建立多個索引標籤檢視編輯器，實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView>介面，並將關聯不同的邏輯檢視 GUID (<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>) 在您建立與每個索引標籤。  
  
 Visual Studio HTML 編輯器是具有多重索引標籤檢視編輯器的範例。 它有**設計**並**來源**索引標籤。 若要這麼做，不同的邏輯檢視是每個索引標籤中，相關聯`LOGICALVIEWID_TextView`for**設計** 索引標籤和`LOGICALVIEWID_Code`for**來源** 索引標籤。  
  
 藉由指定適當的邏輯檢視，VSPackage 可以存取對應至特定的用途，例如設計表單、 編輯程式碼，或偵錯程式碼檢視。 不過，其中一個視窗必須以 NULL 字串識別，而且這必須對應到主要的邏輯檢視 (`LOGVIEWID_Primary`)。  
  
 下表列出可用的邏輯檢視值和其用法。  
  
|LOGVIEWID GUID|建議的使用|  
|--------------------|---------------------|  
|`LOGVIEWID_Primary`|編輯器 factory 的預設/主要資料庫檢視。<br /><br /> 所有編輯器 factory 必須都支援此值。 此檢視必須使用 NULL 字串作為其實體檢視字串。 此值必須設定至少一個邏輯檢視。|  
|`LOGVIEWID_Debugging`|偵錯 檢視。 通常`LOGVIEWID_Debugging`對應至相同的檢視為`LOGVIEWID_Code`。|  
|`LOGVIEWID_Code`|檢視啟動**檢視程式碼**命令。|  
|`LOGVIEWID_Designer`|檢視啟動**檢視表單**命令。|  
|`LOGVIEWID_TextView`|文字編輯器檢視。 這是傳回的檢視<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>，從您可以存取<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。|  
|`LOGVIEWID_UserChooseView`|會提示使用者選擇要使用何種檢視。|  
|`LOGVIEWID_ProjectSpecificEditor`|藉由傳遞**開啟**對話方塊<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> 當使用者選擇 [（專案預設編輯器）] 項目。|  
  
 雖然邏輯檢視 Guid 是可擴充的您可以使用只有在 VSPackage 中定義的邏輯檢視 Guid。  
  
 關閉時，Visual Studio 會保留，讓它可用來重新開啟解決方案時，重新開啟文件視窗與文件視窗相關聯的實體檢視字串編輯器 factory 的 GUID。 方案已關閉時開啟的視窗都保存於方案 (.suo) 檔案。 這些值對應至`VSFPROPID_guidEditorType`並`VSFPROPID_pszPhysicalView`傳入值`propid`中的參數<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>方法。  
  
## <a name="example"></a>範例  
 此程式碼片段說明如何<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView>物件用來存取檢視可實作`IVsCodeWindow`。 在此情況下，<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>服務用來呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A>和 要求`LOGVIEWID_TextView`，取得視窗框架的指標。 藉由呼叫取得文件檢視物件的指標<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>和指定的值為`VSFPROPID_DocView`。 文件檢視物件中，從`QueryInterface`稱為`IVsCodeWindow`。 預期在此情況下會傳回文字編輯器，，和文件檢視物件中傳回的因此<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>方法是程式碼視窗。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [支援多個文件檢視](../extensibility/supporting-multiple-document-views.md)   
 [如何： 將檢視附加至文件資料](../extensibility/how-to-attach-views-to-document-data.md)   
 [建立自訂編輯器和設計工具](../extensibility/creating-custom-editors-and-designers.md)

