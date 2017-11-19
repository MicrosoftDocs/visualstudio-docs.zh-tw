---
title: "IDebugDocumentHelper 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugDocumentHelper interface
ms.assetid: b652a31e-b87b-45f1-b586-94f2b6e822db
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: baadcc1e2dba0b07e132298167b9b711e40cd912
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelper-interface"></a>IDebugDocumentHelper 介面
提供實作許多介面所需的智慧裝載，例如`IDebugDocument`， `IDebugDocumentContext`， `IDebugDocumentProvider`， `IDebugDocumentText`，和`IDebugDocumentTextEvents`介面。  
  
 除了繼承自`IUnknown`、`IDebugDocumentHelper`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|說明|  
|------------|-----------------|  
|[IDebugDocumentHelper::Init](../../winscript/reference/idebugdocumenthelper-init.md)|初始化具有名稱與初始屬性偵錯文件協助程式。|  
|[IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)|將這份文件加入至文件樹狀結構。|  
|[IDebugDocumentHelper::Detach](../../winscript/reference/idebugdocumenthelper-detach.md)|這份文件移除文件樹狀目錄中。|  
|[IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)|會附加結束的 Unicode 字串的這份文件。|  
|[IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)|若要結束的 DBCS 字串將附加的這份文件。|  
|[IDebugDocumentHelper::SetDebugDocumentHost](../../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md)|設定`IDebugDocumentHost`這份文件。|  
|[IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)|指定的文字，但不提供字元會告知協助專家。|  
|[IDebugDocumentHelper::DefineScriptBlock](../../winscript/reference/idebugdocumenthelper-definescriptblock.md)|表示特定範圍的字元是由指定的指令碼引擎所處理的指令碼區塊協助程式。|  
|[IDebugDocumentHelper::SetDefaultTextAttr](../../winscript/reference/idebugdocumenthelper-setdefaulttextattr.md)|設定預設来使用的屬性不是指令碼區塊中的文字。|  
|[IDebugDocumentHelper::SetTextAttributes](../../winscript/reference/idebugdocumenthelper-settextattributes.md)|在某個範圍的文字上設定的屬性。|  
|[IDebugDocumentHelper::SetLongName](../../winscript/reference/idebugdocumenthelper-setlongname.md)|設定文件的完整名稱。|  
|[IDebugDocumentHelper::SetShortName](../../winscript/reference/idebugdocumenthelper-setshortname.md)|設定文件的簡短名稱。|  
|[IDebugDocumentHelper::SetDocumentAttr](../../winscript/reference/idebugdocumenthelper-setdocumentattr.md)|設定這個文件屬性。|  
|[IDebugDocumentHelper::GetDebugApplicationNode](../../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md)|傳回對應到此文件的偵錯應用程式節點。|  
|[IDebugDocumentHelper::GetScriptBlockInfo](../../winscript/reference/idebugdocumenthelper-getscriptblockinfo.md)|擷取的字元和指令碼引擎對應至指令碼區塊的範圍。|  
|[IDebugDocumentHelper::CreateDebugDocumentContext](../../winscript/reference/idebugdocumenthelper-createdebugdocumentcontext.md)|建立新的偵錯文件內容。|  
|[IDebugDocumentHelper::BringDocumentToTop](../../winscript/reference/idebugdocumenthelper-bringdocumenttotop.md)|將這份文件帶到偵錯工具中的第一個使用者介面。|  
|[IDebugDocumentHelper::BringDocumentContextToTop](../../winscript/reference/idebugdocumenthelper-bringdocumentcontexttotop.md)|將本文件的內容傳送到頂端偵錯工具使用者介面中。|