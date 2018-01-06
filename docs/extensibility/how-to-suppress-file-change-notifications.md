---
title: "如何： 隱藏檔案變更通知 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - suppress file change notification
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 209006129bcb2cfaaf88233768df1d9597cd09a5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-suppress-file-change-notifications"></a>如何： 隱藏檔案變更告知
當實體代表文字緩衝的檔案已變更時，對話方塊會顯示與訊息**您要將變更儲存到下列項目嗎？** 這稱為檔案變更通知。 如果檔案要有多少變更，不過，一再重複顯示這個對話方塊可以快速成為造成困擾。  
  
 您可以透過程式設計方式隱藏這個對話方塊方塊中，使用下列程序。 如此一來，您可以重新載入檔案立即而不需要提示使用者每次儲存變更。  
  
### <a name="to-suppress-file-change-notification"></a>若要隱藏檔案變更通知  
  
1.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>方法，以判斷哪一個文字緩衝區物件都與開啟的檔案。  
  
2.  直接<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>記憶體中要忽略監視檔案變更所取得的物件<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>介面從<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>（文件資料） 物件，然後實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A>方法`fIgnore`參數設定為`true`。  
  
3.  呼叫物件方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>更新記憶體中的介面<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>物件 （例如，當欄位加入至您的元件） 的檔案變更。  
  
4.  更新與變更的磁碟上的檔案，而不考慮任何暫止的編輯使用者可能必須在進行中。  
  
     如此一來，當您直接<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>繼續監視檔案的物件變更通知，在記憶體中的文字緩衝區會產生，以及所有其他暫止的編輯作業的變更。 磁碟上的檔案反映您所產生的最新的程式碼，且任何先前儲存的使用者所做的變更在使用者編輯的程式碼中。  
  
5.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A>方法來通知<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>繼續監視檔案變更通知設定的物件`fIgnore`參數`false`。  
  
6.  如果您計劃變更數個檔案，如同在原始程式碼控制 (SCC)，您必須告訴通用檔案變更服務暫時檔案變更告知。  
  
     比方說，如果在重寫該檔案，然後變更時間戳記必須暫停了檔案的變更通知，因為在重寫及 timestample 作業每個計算為個別的檔案變更事件。 若要啟用全域檔案變更通知，您應該改為呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A>方法。  
  
## <a name="example"></a>範例  
 以下示範如何隱藏檔案變更通知。  
  
```cpp  
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
  
## <a name="robust-programming"></a>穩固程式設計  
 如果您的案例牽涉到多個變更檔案，如所示的 SCC，大小寫則重要警示繼續監視檔案變更的文件資料之前繼續通用檔案變更通知。