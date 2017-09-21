---
title: "如何: 隱藏檔案變更告知 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，舊版的隱藏檔案變更通知"
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# 如何: 隱藏檔案變更告知
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

代表文字緩衝區的實體檔案已被變更時，對話方塊會顯示與訊息一起**是否要將變更儲存到下列項目?** 這就是所謂的檔案變更通知。  如果許多的變更將會為檔案，不過，不斷地顯示此對話方塊很快就令人厭煩。  
  
 以程式設計的方式，您可以隱藏此對話方塊，使用下列程序。  如此一來，您可以重新載入檔案立即而不需提示使用者每次儲存所做的變更。  
  
### 若要隱藏的檔案變更通知  
  
1.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>方法，以判斷哪一個文字緩衝區物件是開啟的檔案相關聯。  
  
2.  直接<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>要略過的記憶體中監視檔案變更所取得的物件<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>介面從<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> \(文件的資料\) 的物件，然後再實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A>方法以`fIgnore`參數設為`true`。  
  
3.  呼叫物件方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>介面，以更新記憶體中<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> \(例如，當的欄位會加入至您的元件\) 的檔案變更的物件。  
  
4.  不考慮任何暫止編輯的使用者可能正在進行的變更更新磁碟上的檔案。  
  
     如此一來，當您讓<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>物件，若要繼續監視檔案變更通知、 文字緩衝區在記憶體中的就會反映您所產生，以及所有其他暫止的編輯變更。  磁碟上的檔案會反映您所產生的最新的程式碼和任何先前儲存的使用者所做的變更在使用者編輯的程式碼中。  
  
5.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A>方法來通知關於<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>物件以繼續監視檔案變更通知，藉由設定`fIgnore`參數，以`false`。  
  
6.  如果您打算進行多次變更該檔案，請在 \[大小寫的原始程式碼控制 \(SCC\)，您就必須通知通用檔案變更服務，暫時檔案變更通知。  
  
     比方說，如果您重寫該檔案，然後變更 \[時間戳記時，您必須暫止檔案的變更通知，如的重新寫入與 timestample 作業每個計算為個別的檔案變更事件。  若要啟用的通用檔案變更通知，您應該呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A>方法。  
  
## 範例  
 以下示範如何隱藏檔案變更通知。  
  
```cpp#  
//Misc. helper classes  
  
CSuspendFileChanges::CSuspendFileChanges(  
    /* [in] */ const CString& strMkDocument,   
    /* [in] */ BOOL fSuspendNow /* = TRUE */)   
:  
    m_strMkDocument(strMkDocument),  
    m_fFileChangeSuspended(FALSE)  
{  
    if(fSuspendNow)  
        Suspend();  
}  
CSuspendFileChanges::~CSuspendFileChanges()  
{  
    Resume();  
}  
void CSuspendFileChanges::Suspend()  
{  
    USES_CONVERSION;  
  
    // Prevent suspend from suspending more than once.  
    if(m_fFileChangeSuspended)  
        return;  
  
    IVsRunningDocumentTable* pRDT =   
      _VxModule.GetIVsRunningDocumentTable();  
    ASSERT(pRDT);  
    if (!pRDT)  
        return;  
  
    CComPtr<IUnknown> srpDocData;  
    VSCOOKIE vscookie = VSCOOKIE_NIL;  
    pRDT->FindAndLockDocument(RDT_NoLock, T2COLE(m_strMkDocument),    
      NULL, NULL, &srpDocData, &vscookie);  
    if ( (vscookie == VSCOOKIE_NIL) || !srpDocData)  
        return;  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
    {  
        m_fFileChangeSuspended = TRUE;  
        srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, TRUE);   
        srpDocData->QueryInterface(IID_IVsDocDataFileChangeControl,   
          (void**)&m_srpIVsDocDataFileChangeControl);  
        if(m_srpIVsDocDataFileChangeControl)  
            m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(TRUE);  
    }  
}  
void CSuspendFileChanges::Resume()  
{  
    if(!m_fFileChangeSuspended)  
        return;  
  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
  
    srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, FALSE);   
    if(m_srpIVsDocDataFileChangeControl)  
        m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(FALSE);  
    m_fFileChangeSuspended = FALSE;  
    m_srpIVsDocDataFileChangeControl.Release();  
}  
// Misc. helper classes  
```  
  
## 穩固程式設計  
 如果您的情況涉及多項變更至檔案中，如 SCC，大小寫則一定要恢復警示文件資料，以繼續監視檔案變更前的通用檔案變更通知。