---
title: IDebugStackFrame2::GetDebugProperty |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame2::GetDebugProperty
helpviewer_keywords:
- IDebugStackFrame2::GetDebugProperty
ms.assetid: 02c2fa04-1424-4bca-9936-feaecd2afab6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3f1a8153326fbb88a569680c84376b8c7c911622
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49883307"
---
# <a name="idebugstackframe2getdebugproperty"></a>IDebugStackFrame2::GetDebugProperty
取得堆疊框架的屬性的描述。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetDebugProperty (   
   IDebugProperty2** ppDebugProp  
);  
```  
  
```csharp  
int GetDebugProperty (   
   out IDebugProperty2 ppDebugProp  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppDebugProp`  
 [out]傳回[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)物件，描述此堆疊框架的內容。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 呼叫[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)本機變數、 方法參數、 暫存器和堆疊框架相關聯的 「 this 」 指標，可以擷取與適當的篩選器的方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)