---
title: IJsDebugFrame 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5af46b18-9d25-4a23-b8d1-fa23bea3efcf
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 91fe8cdf91b0c2121f4a1a7f111794b0fbe36669
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575110"
---
# <a name="ijsdebugframe-interface"></a>IJsDebugFrame 介面
代表堆疊框架。  
  
## <a name="syntax"></a>語法  
  
```cpp
IJsDebugFrame : public IUnknown;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|[屬性]|描述|  
|----------|-----------------|  
|[IJsDebugFrame::Evaluate 方法](../../winscript/reference/ijsdebugframe-evaluate-method.md)|評估此堆疊框架內容中的運算式。|  
|[IJsDebugFrame::GetDebugProperty 方法](../../winscript/reference/ijsdebugframe-getdebugproperty-method.md)|傳回此堆疊框架的屬性瀏覽器。|  
|[IJsDebugFrame::GetDocumentPositionWithId 方法](../../winscript/reference/ijsdebugframe-getdocumentpositionwithid-method.md)|傳回此堆疊框架在使用者層級檔中的目前位置。|  
|[IJsDebugFrame::GetDocumentPositionWithName 方法](../../winscript/reference/ijsdebugframe-getdocumentpositionwithname-method.md)|傳回此堆疊框架在使用者層級檔中的目前位置。|  
|[IJsDebugFrame::GetName 方法](../../winscript/reference/ijsdebugframe-getname-method.md)|取得堆疊框架的使用者易記名稱。|  
|[IJsDebugFrame::GetReturnAddress 方法](../../winscript/reference/ijsdebugframe-getreturnaddress-method.md)|取得在框架的 ' start ' （請參閱 GetStackRange）中推送的傳回位址。|  
|[IJsDebugFrame::GetStackRange 方法](../../winscript/reference/ijsdebugframe-getstackrange-method.md)|傳回邏輯 JavaScript 堆疊框架的絕對位址範圍。|  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag。h  
  
## <a name="see-also"></a>請參閱  
 [Windows 指令碼介面參考](../../winscript/reference/windows-script-interfaces-reference.md)