---
title: BPRESI_FIELDS |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BPRESI_FIELDS
helpviewer_keywords:
- BPRESI_FIELDS enumeration
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 560080231de78d60e3d7c1e56c5b1c46bbfe6155
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="bpresifields"></a>BPRESI_FIELDS
指定要擷取有關中斷點的成功解決方式的資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
typedef DWORD BPRESI_FIELDS;  
```  
  
```csharp  
public enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
```  
  
## <a name="members"></a>成員  
 BPRESI_BPRESLOCATION  
 初始化/使用`bpResLocation`（中斷點解析位置） 欄位[BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)結構。  
  
 BPRESI_PROGRAM  
 初始化/使用`pProgram`欄位`BP_RESOLUTION_INFO`結構。  
  
 BPRESI_THREAD  
 初始化/使用`pThread`欄位`BP_RESOLUTION_INFO`結構。  
  
 BPRESI_ALLFIELDS  
 指定所有欄位。  
  
## <a name="remarks"></a>備註  
 傳遞至[GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)方法，以表示的哪些欄位[BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)結構會進行初始化。  
  
 這些旗標也可用來表示的哪些欄位`BP_RESOLUTION_INFO`結構時，會使用並有效傳回該結構。  
  
 這些值可能會合併使用位元`OR`。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)