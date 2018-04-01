---
title: BPERESI_FIELDS |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 36ac591940acaed2ac8b8f92c701580d9d45f94a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="bperesifields"></a>BPERESI_FIELDS
指定要擷取失敗的解決方式的中斷點相關的資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD BPERESI_FIELDS;  
```  
  
```csharp  
public enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
```  
  
## <a name="members"></a>成員  
 PERESI_BPRESLOCATION  
 初始化/使用`bpResLocation`（中斷點解析位置） 欄位[BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)結構。  
  
 BPERESI_PROGRAM  
 初始化/使用`pProgram`欄位`BP_ERROR_RESOLUTION_INFO`結構。  
  
 BPERESI_THREAD  
 初始化/使用`pThread`欄位`BP_ERROR_RESOLUTION_INFO`結構。  
  
 BPERESI_MESSAGE  
 初始化/使用`bstrMessage`欄位`BP_ERROR_RESOLUTION_INFO`結構。  
  
 BPERESI_TYPE  
 初始化/使用`dwType`（中斷點類型） 欄位`BP_ERROR_RESOLUTION_INFO`結構。  
  
 BPERESI_ALLFIELDS  
 初始化使用的所有欄位`BP_ERROR_RESOLUTION_INFO`結構。  
  
## <a name="remarks"></a>備註  
 做為參數來傳遞[GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)方法，以表示的哪些欄位[BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)結構會進行初始化。  
  
 這些值也可用來表示中的欄位`BP_ERROR_RESOLUTION_INFO`結構時，會使用並有效傳回該結構。  
  
 這些值可能會合併使用位元`OR`。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)