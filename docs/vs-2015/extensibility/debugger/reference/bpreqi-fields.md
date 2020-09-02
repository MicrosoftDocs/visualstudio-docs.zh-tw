---
title: BPREQI_FIELDS |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BPREQI_FIELDS
helpviewer_keywords:
- BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a8ad9e4b6d83ebc05c78a8b84c0c06e00d7563bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153219"
---
# <a name="bpreqi_fields"></a>BPREQI_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

指定要抓取之中斷點要求的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
typedef DWORD BPREQI_FIELDS;  
```  
  
```csharp  
public enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
```  
  
## <a name="members"></a>成員  
 BPREQI_BPLOCATION  
 初始化/使用 `bpLocation` [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 或 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 結構的 (中斷點位置) 欄位。  
  
 BPREQI_LANGUAGE  
 初始化/使用 `guidLanguage` 或結構的欄位 `BP_REQUEST_INFO` `BP_REQUEST_INFO2` 。  
  
 BPREQI_PROGRAM  
 初始化/使用 `pProgram` 或結構的欄位 `BP_REQUEST_INFO` `BP_REQUEST_INFO2` 。  
  
 BPREQI_PROGRAMNAME  
 初始化/使用 `bstrProgramName` 或結構的欄位 `BP_REQUEST_INFO` `BP_REQUEST_INFO2` 。  
  
 BPREQI_THREAD  
 初始化/使用 `pThread` 或結構的欄位 `BP_REQUEST_INFO` `BP_REQUEST_INFO2` 。  
  
 BPREQI_THREADNAME  
 初始化/使用 `bstrThreadName` 或結構的欄位 `BP_REQUEST_INFO` `BP_REQUEST_INFO2` 。  
  
 BPREQI_PASSCOUNT  
 初始化/使用 `bpPassCount` 或結構的欄位 `BP_REQUEST_INFO` `BP_REQUEST_INFO2` 。  
  
 BPREQI_CONDITION  
 初始化/使用 `bpCondition` 或結構的 (中斷點條件) 欄位 `BP_REQUEST_INFO` `BP_REQUEST_INFO2` 。  
  
 BPREQI_FLAGS  
 初始化/使用 `dwFlags` 或結構的欄位 `BP_REQUEST_INFO` `BP_REQUEST_INFO2` 。  
  
 BPREQI_ALLOLDFIELDS  
 初始化/使用結構之的所有欄位 `BP_REQUEST_INFO` 。  
  
 BPREQI_VENDOR  
 初始化/使用 `guidVendor` 結構的欄位 `BP_REQUEST_INFO2` 。  
  
 BPREQI_CONSTRAINT  
 初始化/使用 `bstrConstraint` 結構的欄位 `BP_REQUEST_INFO2` 。  
  
 BPREQI_TRACEPOINT  
 初始化/使用 `bstrTracepoint` 結構的欄位 `BP_REQUEST_INFO2` 。  
  
 BPREQI_ALLFIELDS  
 指定結構的所有欄位 `BP_REQUEST_INFO2` 。  
  
## <a name="remarks"></a>備註  
 以引數形式傳遞至 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) 和 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 方法，以指定要初始化 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 和 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 結構的哪些欄位。  
  
 這些旗標也可用來指出傳回的和結構的哪些欄位 `BP_REQUEST_INFO` `BP_REQUEST_INFO2` ，以及傳回每個結構時的有效欄位。  
  
 這些值可能會與位結合 `OR` 。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [枚舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
