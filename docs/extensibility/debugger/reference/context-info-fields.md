---
title: CONTEXT_INFO_FIELDS |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- CONTEXT_INFO_FIELDS
helpviewer_keywords:
- CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a6833e93e7947ee5013a8879c6a5fc949de9fb20
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49929461"
---
# <a name="contextinfofields"></a>CONTEXT_INFO_FIELDS
指定要擷取記憶體內容的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_CONTEXT_INFO_FIELDS {   
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
typedef DWORD CONTEXT_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_CONTEXT_INFO_FIELDS {  
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
```  
  
## <a name="members"></a>成員  
 CIF_MODULEURL  
 初始化/使用`bstrModuleUrl`欄位[CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)結構。  
  
 CIF_FUNCTION  
 初始化/使用`bstrFunction`欄位`CONTEXT_INFO`結構。  
  
 CIF_FUNCTIONOFFSET  
 初始化/使用`posFunctionOffset`欄位`CONTEXT_INFO`結構。  
  
 CIF_ADDRESS  
 初始化/使用`bstrAddress`欄位`CONTEXT_INFO`結構。  
  
 CIF_ADDRESSOFFSET  
 初始化/使用`bstrAddressOffset`欄位`CONTEXT_INFO`結構。  
  
 CIF_ALLFIELDS  
 初始化/使用的所有欄位`CONTEXT_INFO`結構。  
  
## <a name="remarks"></a>備註  
 這些值會傳遞的參數[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)方法，以表示哪些欄位[CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)結構會進行初始化。  
  
 這些旗標也可用來表示欄位`CONTEXT_INFO`結構會使用和有效時，會傳回這個結構。  
  
 這些值可能會與位元 OR 運算結合。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)