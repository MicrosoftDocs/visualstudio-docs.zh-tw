---
title: IDebugCookie 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugCookie interface
ms.assetid: 0dbc75d9-6f33-400f-a5bf-9122cf534082
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47b48b917ee3376c417beffd9972d76a444513ef
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573201"
---
# <a name="idebugcookie-interface"></a>IDebugCookie 介面
允許設定 debug cookie，以與 `IMachineDebugManagerCookie` 介面搭配使用。 如需詳細資訊，請參閱[IMachineDebugManagerCookie 介面](../../winscript/reference/imachinedebugmanagercookie-interface.md)。 這個介面是由進程 Debug Manager （PDM）所執行，並由腳本偵錯工具所使用。  
  
## <a name="methods"></a>方法  
 除了繼承自 `IUnknown` 的方法之外，`IDebugCookie` 介面也會公開下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugCookie::SetDebugCookie](../../winscript/reference/idebugcookie-setdebugcookie.md)|設定偵錯工具 cookie。|  
  
## <a name="see-also"></a>請參閱  
 [IMachineDebugManagerCookie 介面](../../winscript/reference/imachinedebugmanagercookie-interface.md)