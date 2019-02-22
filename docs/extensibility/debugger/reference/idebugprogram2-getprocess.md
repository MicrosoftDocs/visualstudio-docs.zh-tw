---
title: IDebugProgram2::GetProcess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1dcfc207a485a3b1eb5ec24930f613692fac69e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54962978"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
取得此程式正在執行中的程序。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetProcess(  
   IDebugProcess2** ppProcess  
);  
```  
  
```csharp  
int GetProcess(  
   out IDebugProcess2 ppProcess  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppProcess`  
 [out]傳回[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)代表程序的介面。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 除非偵錯引擎 (DE) 會實作[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)介面，這個方法 DE 的實作應該一律會傳回`E_NOTIMPL`因為 DE 無法判斷哪個處理序正在執行中，因此無法滿足此方法的實作。  
  
 實作`IDebugEngineLaunch2`介面可讓您表示 DE 必須了解如何建立程序; 因此，DE 實作[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)介面就能知道它正在中執行哪些處理程序。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)