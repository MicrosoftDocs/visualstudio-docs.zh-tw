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
ms.openlocfilehash: 8ee129526113a1c8af8f918de81c1f286d5cb703
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154461"
---
# <a name="idebugcookie-interface"></a>IDebugCookie 介面
可讓偵錯 cookie 設定，以搭配`IMachineDebugManagerCookie`介面。 如需詳細資訊，請參閱 < [IMachineDebugManagerCookie 介面](../../winscript/reference/imachinedebugmanagercookie-interface.md)。 此介面是實作處理程序進行偵錯管理員 (PDM)，並由指令碼偵錯工具。  
  
## <a name="methods"></a>方法  
 除了繼承自方法`IUnknown`，則`IDebugCookie`介面會公開下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugCookie::SetDebugCookie](../../winscript/reference/idebugcookie-setdebugcookie.md)|設定偵錯應用程式的 cookie。|  
  
## <a name="see-also"></a>另請參閱  
 [IMachineDebugManagerCookie 介面](../../winscript/reference/imachinedebugmanagercookie-interface.md)