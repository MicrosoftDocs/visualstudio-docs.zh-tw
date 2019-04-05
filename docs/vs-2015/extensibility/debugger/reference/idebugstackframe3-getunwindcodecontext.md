---
title: IDebugStackFrame3::GetUnwindCodeContext | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::GetUnwindCodeContext
helpviewer_keywords:
- IDebugStackFrame3::GetUnwindCodeContext method
ms.assetid: b25f7e7d-2b24-48e4-93b3-829e61d73ebf
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c5a3fdaf9ca21841a43041f0ad5c1dc7b1507085
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58941277"
---
# <a name="idebugstackframe3getunwindcodecontext"></a>IDebugStackFrame3::GetUnwindCodeContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

傳回代表位置，如果堆疊回溯作業的程式碼內容時發生。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetUnwindCodeContext(  
   IDebugCodeContext2 **ppCodeContext  
);  
```  
  
```csharp  
int GetUnwindCodeContext(  
   out IDebugCodeContext2 ppCodeContext  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppCodeContext`  
 [out]傳回[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)物件，表示程式碼的內容位置，如果發生堆疊回溯。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 即使這個方法可能會傳回位置的程式碼內容之後的堆疊回溯,，它不一定表示堆疊回溯可以實際發生在目前的堆疊框架。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
