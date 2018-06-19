---
title: IDebugDocumentHost 介面 |Microsoft 文件
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
ms.openlocfilehash: adaeb98f18a052106036a91885696dd4b4760dea
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726988"
---
# <a name="idebugdocumenthost-interface"></a>IDebugDocumentHost 介面
會公開主應用程式專屬功能，例如語法著色、 偵錯工具。 `IDebugDocumentHelper::SetDebugDocumentHost`方法會採用這個介面做為引數。  
  
 除了繼承自`IUnknown`、`IDebugDocumentHost`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|說明|  
|------------|-----------------|  
|[IDebugDocumentHost::GetDeferredText](../../winscript/reference/idebugdocumenthost-getdeferredtext.md)|傳回已加入使用的字元範圍`IDebugDocumentHelper::AddDeferredText`，原始的主機文件中。|  
|[IDebugDocumentHost::GetScriptTextAttributes](../../winscript/reference/idebugdocumenthost-getscripttextattributes.md)|傳回的文件的文字區塊的文字屬性。|  
|[IDebugDocumentHost::OnCreateDocumentContext](../../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md)|通知主機，新的文件內容建立，並可讓主應用程式選擇性地傳回的物件可控制的新內容。|  
|[IDebugDocumentHost::GetPathName](../../winscript/reference/idebugdocumenthost-getpathname.md)|傳回文件的原始程式檔的完整路徑 （包括檔案名稱）。|  
|[IDebugDocumentHost::GetFileName](../../winscript/reference/idebugdocumenthost-getfilename.md)|傳回文件沒有路徑資訊的名稱。|  
|[IDebugDocumentHost::NotifyChanged](../../winscript/reference/idebugdocumenthost-notifychanged.md)|已儲存文件的原始程式檔和它的內容應該重新整理通知主機。|