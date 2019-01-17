---
title: IDebugDocumentHost 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentHost interface
ms.assetid: 2fed4220-b6a2-47c6-bf28-daad7dd5c42d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46684bf2264813a8daaa466b98119496ba85d4b9
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346536"
---
# <a name="idebugdocumenthost-interface"></a>IDebugDocumentHost 介面
會公開主應用程式特有的功能，例如語法著色、 偵錯工具。 `IDebugDocumentHelper::SetDebugDocumentHost`方法會採用此介面做為引數。  
  
 除了繼承自方法`IUnknown`，則`IDebugDocumentHost`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugDocumentHost::GetDeferredText](../../winscript/reference/idebugdocumenthost-getdeferredtext.md)|傳回已加入使用的字元範圍`IDebugDocumentHelper::AddDeferredText`，原始的主機文件中。|  
|[IDebugDocumentHost::GetScriptTextAttributes](../../winscript/reference/idebugdocumenthost-getscripttextattributes.md)|傳回的文件的文字區塊的文字屬性。|  
|[IDebugDocumentHost::OnCreateDocumentContext](../../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md)|主應用程式建立時，新的文件內容，並可讓主機 （選擇性） 傳回的物件可控制新的內容。|  
|[IDebugDocumentHost::GetPathName](../../winscript/reference/idebugdocumenthost-getpathname.md)|傳回文件的原始程式檔的完整路徑 （包括檔案名稱）。|  
|[IDebugDocumentHost::GetFileName](../../winscript/reference/idebugdocumenthost-getfilename.md)|傳回文件，但不含路徑資訊的名稱。|  
|[IDebugDocumentHost::NotifyChanged](../../winscript/reference/idebugdocumenthost-notifychanged.md)|已儲存文件的原始程式檔和其內容應該重新整理，請通知主機。|