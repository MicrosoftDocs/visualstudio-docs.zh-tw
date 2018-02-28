---
title: "IMachineDebugManagerCookie 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IMachineDebugManagerCookie interface
ms.assetid: 04770935-3ccf-41e9-b0c1-c78376ab1e3c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a03b959a7eb09f3b85530bbba07d1d2dc7f8948a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="imachinedebugmanagercookie-interface"></a>IMachineDebugManagerCookie 介面
類似於`IMachineDebugManager`介面，`IMachineDebugManagerCookie`介面支援偵錯 cookie。  
  
 這個介面 (連同`IDebugCookie`介面) 允許執行指令碼偵錯工具處理序中，不需要偵錯工具，追蹤的那些指令碼的指令碼。  
  
 指令碼偵錯工具呼叫`IDebugCookie::SetDebugCookie`方法處理程序進行偵錯管理員 (PDM)。 然後，PDM 會傳送此 cookie，以及新增或移除指令碼應用程式或從電腦進行偵錯管理員 (MDM)，任何要求的方法`IMachineDebugManagerCookie`介面。 MDM 然後通知變更，除了具有該 cookie 的每個偵錯的工具。  
  
 除了繼承自`IUnknown`、`IMachineDebugManagerCookie`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|說明|  
|------------|-----------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|新增應用程式來執行應用程式清單。|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|傳回目前執行的應用程式清單的列舉值。|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|移除應用程式從執行的應用程式清單。|  
  
## <a name="see-also"></a>另請參閱  
 [IMachineDebugManager 介面](../../winscript/reference/imachinedebugmanager-interface.md)   
 [IDebugCookie 介面](../../winscript/reference/idebugcookie-interface.md)