---
title: MACHINE_INFO_FIELDS |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- MACHINE_INFO_FIELDS
helpviewer_keywords:
- MACHINE_INFO_FIELDS enumeration
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 631ef4bbb23d4b0cedbf86d7eedb019580cf7e5b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942500"
---
# <a name="machineinfofields"></a>MACHINE_INFO_FIELDS
指定要擷取特定電腦的資訊種類。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_MACHINE_INFO_FIELDS {   
   MCIF_NAME  = 0x00000001,  
   MCIF_FLAGS = 0x00000002,  
   MCIF_ALL   = 0x00000003  
};  
typedef DWORD MACHINE_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_MACHINE_INFO_FIELDS {   
   MCIF_NAME  = 0x00000001,  
   MCIF_FLAGS = 0x00000002,  
   MCIF_ALL   = 0x00000003  
};  
```  
  
## <a name="members"></a>成員  
 MCIF_NAME  
 初始化/使用`bstrName`欄位在結構中。  
  
 MCIF_FLAGS  
 初始化/使用`Flags`欄位在結構中。  
  
 MIF_ALL  
 初始化/使用的所有欄位在結構中。  
  
## <a name="remarks"></a>備註  
 這些值會傳遞給[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)方法，以表示哪些成員[MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)結構會進行初始化。  
  
 也用於`Fields`隸屬`MACHINE_INFO`表示哪些欄位已使用且有效的結構。  
  
 這些旗標可能會結合的位元`OR`。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)   
 [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)