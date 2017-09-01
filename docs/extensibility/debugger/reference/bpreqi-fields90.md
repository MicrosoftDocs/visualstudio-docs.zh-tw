---
title: BPREQI_FIELDS90 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BPREQI_FIELDS90 enumeration
ms.assetid: bf6f7efc-39f2-46a2-906d-c3647bf89995
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 2de27fc0c3ea470e63c82c8116e34e450eb08bb2
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="bpreqifields90"></a>BPREQI_FIELDS90
Enumerates the valid values that specify the information to be retrieved about a breakpoint request. This enumeration extends the [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) enumeration.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_BPREQI_FIELDS90  
{  
   // VS 8.0 values  
   BPREQI90_BPLOCATION                = 0x0001,  
   BPREQI90_LANGUAGE                  = 0x0002,  
   BPREQI90_PROGRAM                   = 0x0004,  
   BPREQI90_PROGRAMNAME               = 0x0008,  
   BPREQI90_THREAD                    = 0x0010,  
   BPREQI90_THREADNAME                = 0x0020,  
   BPREQI90_PASSCOUNT                 = 0x0040,  
   BPREQI90_CONDITION                 = 0x0080,  
   BPREQI90_FLAGS                     = 0x0100,  
   BPREQI90_ALLOLDFIELDS              = 0x01ff,  
   BPREQI90_VENDOR                    = 0x0200,  
   BPREQI90_CONSTRAINT                = 0x0400,  
   BPREQI90_TRACEPOINT                = 0x0800,  
  
   // Values added in VS 9.0  
   BPREQI90_MACROTRACEPOINT           = 0x1000,  
  
   BPREQI90_ALLFIELDS                 = 0xffff  
};  
typedef DWORD BPREQI_FIELDS90;  
```  
  
```csharp  
public enum enum_BPREQI_FIELDS90  
{  
    // VS 8.0 values  
    BPREQI90_BPLOCATION                = 0x0001,  
    BPREQI90_LANGUAGE                  = 0x0002,  
    BPREQI90_PROGRAM                   = 0x0004,  
    BPREQI90_PROGRAMNAME               = 0x0008,  
    BPREQI90_THREAD                    = 0x0010,  
    BPREQI90_THREADNAME                = 0x0020,  
    BPREQI90_PASSCOUNT                 = 0x0040,  
    BPREQI90_CONDITION                 = 0x0080,  
    BPREQI90_FLAGS                     = 0x0100,  
    BPREQI90_ALLOLDFIELDS              = 0x01ff,  
    BPREQI90_VENDOR                    = 0x0200,  
    BPREQI90_CONSTRAINT                = 0x0400,  
    BPREQI90_TRACEPOINT                = 0x0800,  
  
    // Values added in VS 9.0  
    BPREQI90_MACROTRACEPOINT           = 0x1000,  
  
    BPREQI90_ALLFIELDS                 = 0xffff  
};  
```  
  
#### <a name="parameters"></a>Parameters  
 BPREQI90_BPLOCATION  
 Initialize or use the `bpLocation` (breakpoint location) field of the [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) or [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) structure.  
  
 BPREQI90_LANGUAGE  
 Initialize or use the `guidLanguage` field of the `BP_REQUEST_INFO` or `BP_REQUEST_INFO2` structure.  
  
 BPREQI90_PROGRAM  
 Initialize or use the `pProgram` field of the `BP_REQUEST_INFO` or `BP_REQUEST_INFO2` structure.  
  
 BPREQI90_PROGRAMNAME  
 Initialize or use the `bstrProgramName` field of the `BP_REQUEST_INFO` or `BP_REQUEST_INFO2` structure.  
  
 BPREQI90_THREAD  
 Initialize or use the `pThread` field of the `BP_REQUEST_INFO` or `BP_REQUEST_INFO2` structure.  
  
 BPREQI90_THREADNAME  
 Initialize or use the `bstrThreadName` field of the `BP_REQUEST_INFO` or `BP_REQUEST_INFO2` structure.  
  
 BPREQI90_PASSCOUNT  
 Initialize or use the `bpPassCount` field of the `BP_REQUEST_INFO` or `BP_REQUEST_INFO2` structure.  
  
 BPREQI90_CONDITION  
 Initialize or use the `bpCondition` (breakpoint condition) field of the `BP_REQUEST_INFO` or `BP_REQUEST_INFO2` structure.  
  
 BPREQI90_FLAGS  
 Initialize or use the `dwFlags` field of the `BP_REQUEST_INFO` or `BP_REQUEST_INFO2` structure.  
  
 BPREQI90_ALLOLDFIELDS  
 Initialize or use all fields for the of the `BP_REQUEST_INFO` structure.  
  
 BPREQI90_VENDOR  
 Initialize or use the `guidVendor` field of `BP_REQUEST_INFO2` structure.  
  
 BPREQI90_CONSTRAINT  
 Initialize or use the `bstrConstraint` field of `BP_REQUEST_INFO2` structure.  
  
 BPREQI90_TRACEPOINT  
 Initialize or use the `bstrTracepoint` field of `BP_REQUEST_INFO2` structure.  
  
 BPREQI90_MACROTRACEPOINT  
 Initialize or use the `bstrMacroTracepoint` field of `BP_REQUEST_INFO2` structure. BPREQI_ALLFIELDS does not include this field.  
  
 BPREQI90_ALLFIELDS  
 Specifies all fields for the `BP_REQUEST_INFO2` structure.  
  
## <a name="requirements"></a>Requirements  
 Header: Msdbg90.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>See Also  
 [Enumerations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
