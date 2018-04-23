---
title: MACHINE_INFO |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- MACHINE_INFO
helpviewer_keywords:
- MACHINE_INFO structure
ms.assetid: e7564ff2-00b5-4750-8fd5-dc1029a16912
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4be6ee66149acb970287628289a15574894b8b26
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="machineinfo"></a>MACHINE_INFO
描述特定電腦。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct tagMACHINE_INFO {   
   MACHINE_INFO_FIELDS Fields;  
   BSTR                bstrName;  
   MACHINE_INFO_FLAGS  Flags;  
} MACHINE_INFO;  
```  
  
```csharp  
public struct MACHINE_INFO {   
   public uint   Fields;  
   public string bstrName;  
   public uint   Flags;  
};  
```  
  
## <a name="members"></a>成員  
 `Fields`  
 從旗標的組合[MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)列舉，指定初始化結構的哪些欄位。  
  
 `bstrName`  
 電腦名稱。 相當於呼叫[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)。  
  
 `Flags`  
 從旗標的組合[MACHINE_INFO_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md)描述機器屬性的列舉類型。  
  
## <a name="remarks"></a>備註  
 這個結構由呼叫[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)   
 [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)