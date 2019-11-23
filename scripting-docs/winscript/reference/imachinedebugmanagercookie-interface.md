---
title: IMachineDebugManagerCookie 介面 |Microsoft Docs
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
ms.openlocfilehash: 6b39c286f389c99187b0f3250fc68af92ff5dcc8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573891"
---
# <a name="imachinedebugmanagercookie-interface"></a>IMachineDebugManagerCookie 介面
類似于 `IMachineDebugManager` 介面，`IMachineDebugManagerCookie` 介面支援 debug cookie。  
  
 這個介面（以及 `IDebugCookie` 介面）允許腳本在腳本偵錯工具進程中執行，而不需要偵錯工具追蹤這些腳本。  
  
 腳本偵錯工具會在進程 Debug Manager （PDM）上呼叫 `IDebugCookie::SetDebugCookie` 方法。 然後，PDM 會連同任何要求一起傳送此 cookie，以使用 `IMachineDebugManagerCookie` 介面的方法，在電腦 Debug Manager （MDM）中新增或移除腳本應用程式。 然後，MDM 會通知每個變更的偵錯工具，但具有該 cookie 的每一項。  
  
 除了繼承自 `IUnknown`的方法之外，`IMachineDebugManagerCookie` 介面也會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|將應用程式新增至執行中的應用程式清單。|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|傳回目前正在執行之應用程式清單的列舉值。|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|從執行中的應用程式清單中移除應用程式。|  
  
## <a name="see-also"></a>另請參閱  
 [IMachineDebugManager 介面](../../winscript/reference/imachinedebugmanager-interface.md)   
 [IDebugCookie 介面](../../winscript/reference/idebugcookie-interface.md)