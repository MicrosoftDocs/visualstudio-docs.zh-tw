---
title: IDebugStackFrame2::GetCodeContext |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugStackFrame2::GetCodeContext
helpviewer_keywords:
- IDebugStackFrame2::GetCodeContext
ms.assetid: 93d66159-a41d-49ef-982f-91bb4d073b74
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: c697f56797e456d9b91a1b08809ef42a64e988da
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugstackframe2getcodecontext"></a>IDebugStackFrame2::GetCodeContext
取得此堆疊框架的程式碼內容。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCodeContext (   
   IDebugCodeContext2** ppCodeCxt  
);  
```  
  
```csharp  
int GetCodeContext (   
   out IDebugCodeContext2 ppCodeCxt  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppCodeCxt`  
 [out]傳回[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)物件，代表目前指令指標在此堆疊框架。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)