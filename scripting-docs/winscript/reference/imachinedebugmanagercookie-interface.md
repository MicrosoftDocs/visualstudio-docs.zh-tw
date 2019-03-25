---
title: IMachineDebugManagerCookie Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IMachineDebugManagerCookie interface
ms.assetid: 04770935-3ccf-41e9-b0c1-c78376ab1e3c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fdc02498360f2e3900012166474c5d1e35abd6ee
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58151046"
---
# <a name="imachinedebugmanagercookie-interface"></a>IMachineDebugManagerCookie 介面
類似於`IMachineDebugManager`介面，`IMachineDebugManagerCookie`介面支援偵錯 cookie。  
  
 這個介面 (連同`IDebugCookie`介面) 允許執行指令碼偵錯工具處理序中，不需要偵錯工具，追蹤的這些指令碼的指令碼。  
  
 指令碼偵錯工具呼叫`IDebugCookie::SetDebugCookie`方法程序進行偵錯管理員 (PDM)。 接著，PDM 會傳送任何要求，以新增或移除指令碼的應用程式或從機器偵錯 Manager (MDM)，以及此 cookie 使用的方法`IMachineDebugManagerCookie`介面。 MDM 然後通知此變更，除了包含該 cookie 的每個偵錯工具。  
  
 除了繼承自方法`IUnknown`，則`IMachineDebugManagerCookie`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|新增應用程式執行的應用程式清單。|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|傳回目前執行中應用程式清單的列舉值。|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|移除應用程式從執行的應用程式清單。|  
  
## <a name="see-also"></a>另請參閱  
 [IMachineDebugManager 介面](../../winscript/reference/imachinedebugmanager-interface.md)   
 [IDebugCookie 介面](../../winscript/reference/idebugcookie-interface.md)