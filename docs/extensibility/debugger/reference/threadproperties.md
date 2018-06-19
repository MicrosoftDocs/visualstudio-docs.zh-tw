---
title: THREADPROPERTIES |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e4079c688358f3e7deedd28b5eb05e556192bfe6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31125749"
---
# <a name="threadproperties"></a>THREADPROPERTIES
描述執行緒屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _tagTHREADPROPERTIES {   
   THREADPROPERTY_FIELDS dwFields;  
   DWORD                 dwThreadId;  
   DWORD                 dwSuspendCount;  
   DWORD                 dwThreadState;  
   BSTR                  bstrPriority;  
   BSTR                  bstrName;  
   BSTR                  bstrLocation;  
} THREADPROPERTIES;  
```  
  
```csharp  
public struct THREADPROPERTIES {   
   public uint   dwFields;  
   public uint   dwThreadId;  
   public uint   dwSuspendCount;  
   public uint   dwThreadState;  
   public string bstrPriority;  
   public string bstrName;  
   public string bstrLocation;  
};  
```  
  
## <a name="members"></a>成員  
 dwFields  
 從旗標的組合[THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)描述在此結構中的哪些欄位有效的列舉。  
  
 dwThreadId  
 執行緒識別碼。  
  
 dwSuspendCount  
 執行緒暫停計數。  
  
 dwThreadState  
 中的值[THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)列舉，指出作業系統執行緒的狀態。  
  
 bstrPriority  
 字串，指定的執行緒優先權。例如，"上方 Normal"、"Normal"或者 「 時間重大 」。  
  
 bstName  
 執行緒名稱。  
  
 bstrLocation  
 執行緒位置 （通常是最上層的堆疊框架），通常表示為目前停止執行方法的名稱。  
  
## <a name="remarks"></a>備註  
 此結構會填入呼叫[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)方法。 因此傳回的資訊通常用於填入**執行緒**視窗。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)   
 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)