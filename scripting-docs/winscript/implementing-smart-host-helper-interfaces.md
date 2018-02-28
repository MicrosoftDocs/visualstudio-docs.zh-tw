---
title: "實作智慧主機協助程式介面 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Smart Host Helper Interfaces, implementing
ms.assetid: b9c44246-4d4d-469e-91be-00c8f5796fa5
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba571f6ad66855c44902e06467889e2cae5b4555
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="implementing-smart-host-helper-interfaces"></a>實作智慧主機協助程式介面
[IDebugDocumentHelper 介面](../winscript/reference/idebugdocumenthelper-interface.md)介面可大幅簡化建立智慧主機以進行主動式偵錯的工作，因為它提供智慧裝載所需的許多介面的實作。  
  
 若要使用 `IDebugDocumentHelper` 成為智慧主機，則主應用程式只能執行三件事：  
  
1.  `CoCreate` 處理序偵錯管理員，並使用 [IProcessDebugManager 介面](../winscript/reference/iprocessdebugmanager-interface.md)介面將應用程式新增至可偵錯應用程式清單。  
  
2.  使用 [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md) 方法，以建立每個指令碼物件的偵錯文件協助程式。 請確定已定義文件名稱、父代文件、文字和指令碼區塊。  
  
3.  對物件實作 [IActiveScriptSiteDebug 介面](../winscript/reference/iactivescriptsitedebug-interface.md)介面，而此介面可實作 [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) 介面 (動態指令碼處理的必要項目)。 `IActiveScriptSiteDebug` 介面上的唯一重要方法只會委派給協助程式。  
  
 如果主機需要語法色彩、文件內容建立和其他擴充功能的額外控制，則主機可以選擇性地實作 [IDebugDocumentHost 介面](../winscript/reference/idebugdocumenthost-interface.md)介面。  
  
 智慧主機協助程式的主要限制是它只能處理文件，而文件在新增之後，其內容會變更或縮小 (雖然可以展開文件)。 不過，對於許多智慧主機而言，它提供的功能完全就是需要的功能。  
  
 下列各節會詳述每個步驟。  
  
## <a name="create-an-application-object"></a>建立應用程式物件  
 需要先建立 [IDebugApplication 介面](../winscript/reference/idebugapplication-interface.md)物件在偵錯工具中代表您的應用程式，才能使用智慧主機協助程式。  
  
#### <a name="to-create-an-application-object"></a>建立應用程式物件  
  
1.  使用 `CoCreateInstance`，建立處理序偵錯管理員的執行個體。  
  
2.  呼叫 [IProcessDebugManager::CreateApplication](../winscript/reference/iprocessdebugmanager-createapplication.md)。  
  
3.  使用 [IDebugApplication::SetName](../winscript/reference/idebugapplication-setname.md)，設定應用程式上的名稱。  
  
4.  使用 [IProcessDebugManager::AddApplication](../winscript/reference/iprocessdebugmanager-addapplication.md)，以將應用程式物件新增至可偵錯應用程式清單。  
  
     下列程式碼會概述此處理序，但未包含錯誤檢查或其他強固的程式設計技術。  
  
    ```  
    CoCreateInstance(CLSID_ProcessDebugManager, NULL,  
          CLSCTX_INPROC_SERVER | CLSCTX_INPROC_HANDLER  
          | CLSCTX_LOCAL_SERVER,  
    IID_IProcessDebugManager, (void **)&g_ppdm);  
    g_ppdm->CreateApplication(&g_pda);  
    g_pda->SetName(L"My cool application");  
    g_ppdm->AddApplication(g_pda, &g_dwAppCookie);  
    ```  
  
## <a name="using-idebugdocumenthelper"></a>使用 IDebugDocumentHelper  
  
#### <a name="to-use-the-helper-minimal-sequence-of-steps"></a>使用協助程式 (最小序列的步驟)  
  
1.  針對每個主機文件，使用 [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md) 建立協助程式。  
  
2.  對協助程式呼叫 [IDebugDocumentHelper::Init](../winscript/reference/idebugdocumenthelper-init.md)，並提供名稱、文件屬性等等。  
  
3.  使用文件的父代協助程式呼叫 [IDebugDocumentHelper::Attach](../winscript/reference/idebugdocumenthelper-attach.md) (如果文件是根文件，則為 NULL)，以定義樹狀結構中文件的位置，並向偵錯工具顯示它。  
  
4.  呼叫 [IDebugDocumentHelper::AddDBCSText](../winscript/reference/idebugdocumenthelper-adddbcstext.md) 或 [IDebugDocumentHelper::AddUnicodeText](../winscript/reference/idebugdocumenthelper-addunicodetext.md)，以定義文件的文字  (在瀏覽器中，如果以累加方式下載文件，則可以多次呼叫這些項目)。  
  
5.  呼叫 [IDebugDocumentHelper::DefineScriptBlock](../winscript/reference/idebugdocumenthelper-definescriptblock.md) 以定義每個指令碼區塊和相關聯指令碼引擎的範圍。  
  
## <a name="implementing-iactivescriptsitedebug"></a>實作 IActiveScriptSiteDebug  
 若要實作 [IActiveScriptSiteDebug::GetDocumentContextFromPosition](../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md)，請取得對應至所指定網站的協助程式，然後取得所指定來源內容的起始文件位移，如下所示：  
  
```  
pddh->GetScriptBlockInfo(dwSourceContext, NULL, &ulStartPos, NULL);  
```  
  
 接下來，使用協助程式來建立指定字元位移的新文件內容：  
  
```  
pddh->CreateDebugDocumentContext(ulStartPos + uCharacterOffset, cChars, &pddcNew);  
```  
  
 若要實作 [IActiveScriptSiteDebug::GetRootApplicationNode](../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md)，只需要呼叫 `IDebugApplication::GetRootNode` (繼承自 [IRemoteDebugApplication::GetRootNode](../winscript/reference/iremotedebugapplication-getrootnode.md))。  
  
 若要實作 [IDebugDocumentHelper::GetDebugApplicationNode](../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md)，只會傳回您一開始使用處理序偵錯管理員所建立的 `IDebugApplication`。  
  
## <a name="the-optional-idebugdocumenthost-interface"></a>選擇性 IDebugDocumentHost 介面  
 主機可以使用 [IDebugDocumentHelper::SetDebugDocumentHost](../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md) 額外控制協助程式，以提供 [IDebugDocumentHost 介面](../winscript/reference/idebugdocumenthost-interface.md)的實作。 以下是主機介面可讓您執行的一些重要事項：  
  
-   使用 [IDebugDocumentHelper::AddDeferredText](../winscript/reference/idebugdocumenthelper-adddeferredtext.md) 新增文字；因此，主機不需要立即提供實際字元。 真正需要這些字元時，協助程式會在主機上呼叫 [IDebugDocumentHost::GetDeferredText](../winscript/reference/idebugdocumenthost-getdeferredtext.md)。  
  
-   覆寫協助程式所提供的預設語法著色。 協助程式會呼叫 [IDebugDocumentHost::GetScriptTextAttributes](../winscript/reference/idebugdocumenthost-getscripttextattributes.md) 來判斷某範圍字元的著色，並在主機傳回 `E_NOTIMPL` 時回復為其預設實作。  
  
-   實作 [IDebugDocumentHost::OnCreateDocumentContext](../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md)，以提供協助程式所建立之文件內容的控制未知。 這可讓主機覆寫預設文件內容實作的功能。  
  
-   提供檔案系統中文件的路徑名稱。 有些偵錯 UI 會使用這個選項允許使用者編輯和儲存文件變更。 呼叫 [IDebugDocumentHost::NotifyChanged](../winscript/reference/idebugdocumenthost-notifychanged.md)，以在儲存文件之後通知主機。  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼偵錯概觀](../winscript/active-script-debugging-overview.md)