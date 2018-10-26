---
title: IDebugEngine2::RemoveSetException |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::RemoveSetException
helpviewer_keywords:
- IDebugEngine2::RemoveSetException
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4880bfc80f27c362deb056b176492eb62ec6f975
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49941542"
---
# <a name="idebugengine2removesetexception"></a>IDebugEngine2::RemoveSetException
移除指定的例外狀況，讓它不再由偵錯引擎。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT RemoveSetException(   
   EXCEPTION_INFO* pException  
);  
```  
  
```csharp  
int RemoveSetException(   
   EXCEPTION_INFO[] pException  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pException`  
 [in][EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)結構，描述要移除的例外狀況。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 要移除的例外狀況必須先前已設定的先前呼叫[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)方法。  
  
 若要一次移除所有設定例外狀況，請呼叫[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)