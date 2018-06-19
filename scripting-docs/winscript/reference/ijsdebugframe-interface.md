---
title: IJsDebugFrame 介面 |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5af46b18-9d25-4a23-b8d1-fa23bea3efcf
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f09a147375661fb52b88f531aff981897138adff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729608"
---
# <a name="ijsdebugframe-interface"></a>IJsDebugFrame 介面
代表堆疊框架。  
  
## <a name="syntax"></a>語法  
  
```  
IJsDebugFrame : public IUnknown;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[IJsDebugFrame::Evaluate 方法](../../winscript/reference/ijsdebugframe-evaluate-method.md)|評估內容中的運算式，此堆疊框架。|  
|[IJsDebugFrame::GetDebugProperty 方法](../../winscript/reference/ijsdebugframe-getdebugproperty-method.md)|傳回此堆疊框架屬性瀏覽器。|  
|[IJsDebugFrame::GetDocumentPositionWithId 方法](../../winscript/reference/ijsdebugframe-getdocumentpositionwithid-method.md)|傳回此堆疊框架，在使用者層級文件中的目前位置。|  
|[IJsDebugFrame::GetDocumentPositionWithName 方法](../../winscript/reference/ijsdebugframe-getdocumentpositionwithname-method.md)|傳回此堆疊框架，在使用者層級文件中的目前位置。|  
|[IJsDebugFrame::GetName 方法](../../winscript/reference/ijsdebugframe-getname-method.md)|取得堆疊框架的使用者易記名稱。|  
|[IJsDebugFrame::GetReturnAddress 方法](../../winscript/reference/ijsdebugframe-getreturnaddress-method.md)|取得在 'start' 推入的傳回位址 （請參閱 GetStackRange） 的框架。|  
|[IJsDebugFrame::GetStackRange 方法](../../winscript/reference/ijsdebugframe-getstackrange-method.md)|傳回邏輯 JavaScript 堆疊框架的絕對位址範圍。|  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [Windows 指令碼介面參考](../../winscript/reference/windows-script-interfaces-reference.md)