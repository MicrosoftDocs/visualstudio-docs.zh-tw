---
title: BP_RES_DATA_FLAGS |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_RES_DATA_FLAGS
helpviewer_keywords:
- BP_RES_DATA_FLAGS enumeration
ms.assetid: d97611e2-def6-45a9-ad7d-eedf2ad4c82b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 08890a0be03329bd2c2c3469cc20c330223fb8a0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="bpresdataflags"></a>BP_RES_DATA_FLAGS
指定是否正在模擬資料中斷點，或實作中的硬體。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_BP_RES_DATA_FLAGS {   
   BP_RES_DATA_EMULATED = 0x0001  
};  
typedef DWORD BP_RES_DATA_FLAGS;  
```  
  
```csharp  
public enum enum_BP_RES_DATA_FLAGS {   
   BP_RES_DATA_EMULATED = 0x0001  
};  
```  
  
## <a name="members"></a>成員  
 BP_RES_DATA_EMULATED  
 指定模擬的資料中斷點。  
  
## <a name="remarks"></a>備註  
 用於`dwFlags`隸屬[BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)結構。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)