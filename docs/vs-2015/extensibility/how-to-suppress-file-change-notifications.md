---
title: 如何：隱藏檔案變更通知 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - suppress file change notification
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3f045175eae165b75a887ada2716b19f34fc228b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204084"
---
# <a name="how-to-suppress-file-change-notifications"></a>如何：隱藏檔案變更通知
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當表示文字緩衝區的實體檔案已變更時，會顯示一個對話方塊，顯示 **您要將變更儲存至下列專案的訊息嗎？** 這就是所謂的檔案變更通知。 但是，如果檔案中有許多變更，這個對話方塊就會再度出現，而且可能很快就會變成討厭。  
  
 您可以使用下列程式，以程式設計方式隱藏此對話方塊。 如此一來，您就可以立即重載檔案，而不需要每次都提示使用者儲存變更。  
  
### <a name="to-suppress-file-change-notification"></a>隱藏檔案變更通知  
  
1. 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> 方法來判斷哪個文字緩衝區物件與開啟的檔案相關聯。  
  
2. 將 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 記憶體中的物件導向至記憶體中的物件，藉由 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> 從 (的檔 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 資料) 物件取得介面，然後執行方法並將 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> `fIgnore` 參數設定為， `true` 以忽略監視檔案變更。  
  
3. 在和介面上呼叫方法， <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 以更新記憶體中的 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 物件與檔案 (例如，將欄位新增至您的元件) 。  
  
4. 使用變更來更新磁片上的檔案，而不考慮使用者可能進行的任何暫止編輯。  
  
     如此一來，當您指示 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 物件繼續監視檔案變更通知時，記憶體中的文字緩衝區會反映您所產生的變更，以及所有其他暫止的編輯。 磁片上的檔案會反映您所產生的最新程式碼，以及使用者在使用者編輯的程式碼中任何先前儲存的變更。  
  
5. 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> 方法，藉 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 由將參數設定為，以通知物件繼續監視檔案變更通知 `fIgnore` `false` 。  
  
6. 如果您想要對檔案進行數個變更，例如原始程式碼控制 (SCC) ，您必須告訴全域檔案變更服務暫時暫停檔案變更通知。  
  
     例如，如果您重寫檔案，然後變更時間戳記，則必須暫停檔案變更通知，因為重寫和 timestample 作業每個都會計為個別的檔案變更事件。 若要啟用全域檔案變更通知，您應該改為呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A> 方法。  
  
## <a name="example"></a>範例  
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
  
## <a name="robust-programming"></a>穩固程式設計  
 如果您的案例牽涉到對檔案進行多項變更，就像 SCC 一樣，在警示檔資料以繼續監視檔案變更之前，請務必先繼續全域檔案變更通知。
