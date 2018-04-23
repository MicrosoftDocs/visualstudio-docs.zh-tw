---
title: IDebugEngine2::SetException |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::SetException
helpviewer_keywords:
- IDebugEngine2::SetException
ms.assetid: e6f5ec48-09e8-4b9b-9dc9-55f8d883f1b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 371a5c45e7df725babab96587e5064e5290d80ac
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugengine2setexception"></a>IDebugEngine2::SetException
指定偵錯引擎 (DE) 應該如何處理指定的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetException(   
   EXCEPTION_INFO* pException  
);  
```  
  
```csharp  
int SetException(   
   EXCEPTION_INFO[] pException  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pException`  
 [in][EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)描述例外狀況，以及如何偵錯時的結構。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 若要停止產生第一個可能發生的例外狀況的程式，第二個機會，可指示 DE 或完全無法執行。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)