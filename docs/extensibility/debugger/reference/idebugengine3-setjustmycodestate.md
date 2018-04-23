---
title: IDebugEngine3::SetJustMyCodeState |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fda672cc9d6861520b9da3a894b94d51f4100683
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
這個方法的 JustMyCode 狀態資訊告知偵錯引擎。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL           fUpdate,  
   DWORD          dwModules,  
   JMC_CODE_SPEC* rgJMCSpec  
);  
```  
  
```csharp  
int SetJustMyCodeState(  
   int             fUpdate,   
   uint            dwModules,   
   JMC_CODE_SPEC[] rgJMCSpec  
);  
```  
  
#### <a name="parameters"></a>參數  
 `fUpdate`  
 [in]非零 (`TRUE`) 若要更新目前的資訊，零 (`FALSE`) 重設 （略過任何先前設定） 的所有資訊。  
  
 `dwModules`  
 [in]中的資訊結構數目 `rgJMCSpec.`  
  
 `rgJMCSpec`  
 [in]陣列[JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)来使用的結構。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`，否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 JustMyCode 是偵錯只屬於使用者程式碼，並忽略系統程式碼等所有中繼程式碼的概念，即使原始程式碼是適用於該系統程式碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)