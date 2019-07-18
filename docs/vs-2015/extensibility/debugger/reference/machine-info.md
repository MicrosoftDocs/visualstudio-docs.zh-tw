---
title: MACHINE_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MACHINE_INFO
helpviewer_keywords:
- MACHINE_INFO structure
ms.assetid: e7564ff2-00b5-4750-8fd5-dc1029a16912
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ac571a1e1c7a9d6cff1caaca40f1c6568f99adf1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546774"
---
# <a name="machineinfo"></a>MACHINE_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

描述特定的電腦。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 從旗標的組合[MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)指定結構的哪些欄位會初始化的列舉型別。  
  
 `bstrName`  
 電腦名稱。 相當於呼叫[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)。  
  
 `Flags`  
 從旗標的組合[MACHINE_INFO_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md)說明機器屬性的列舉型別。  
  
## <a name="remarks"></a>備註  
 此結構由呼叫[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)   
 [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
