---
title: IDebugEngine3：： SetJustMyCodeState |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ebaf697bfdfff435c12eee1002ff93f4eba7ed65
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195858"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個方法會告訴 debug engine 有關 JustMyCode 狀態資訊的資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL           fUpdate,  
   DWORD          dwModules,  
   JMC_CODE_SPEC* rgJMCSpec  
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
 在非零 (`TRUE`) 更新目前的資訊，零 (`FALSE`) 重設所有資訊 (忽略先前設定) 的任何資訊。  
  
 `dwModules`  
 在中的資訊結構數目 `rgJMCSpec.`  
  
 `rgJMCSpec`  
 在要使用 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) 結構的陣列。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 JustMyCode 是僅針對屬於使用者的程式碼，以及忽略所有中繼程式碼（例如系統程式碼）的概念，即使原始程式碼可供該系統程式碼使用也是一樣。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)
