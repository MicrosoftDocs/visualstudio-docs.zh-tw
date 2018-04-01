---
title: BP_LOCATION |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BP_LOCATION
helpviewer_keywords:
- BP_LOCATION union
ms.assetid: ed1e874c-f289-4c31-8b6c-04dde03ad0f5
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 6e268d809442b0101d5d520ca7bdd5f5c37fb62b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="bplocation"></a>BP_LOCATION
指定用來描述中斷點的位置的結構類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _BP_LOCATION {  
   BP_LOCATION_TYPE bpLocationType;  
   union {  
      BP_LOCATION_CODE_FILE_LINE   bplocCodeFileLine;  
      BP_LOCATION_CODE_FUNC_OFFSET bplocCodeFuncOffset;  
      BP_LOCATION_CODE_CONTEXT     bplocCodeContext;  
      BP_LOCATION_CODE_STRING      bplocCodeString;  
      BP_LOCATION_CODE_ADDRESS     bplocCodeAddress;  
      BP_LOCATION_DATA_STRING      bplocDataString;  
      BP_LOCATION_RESOLUTION       bplocResolution;  
      DWORD                        unused;  
   } bpLocation;  
} BP_LOCATION;  
```  
  
```csharp  
public struct BP_LOCATION {  
   public uint   bpLocationType;  
   public IntPtr unionmember1;  
   public IntPtr unionmember2;  
   public IntPtr unionmember3;  
   public IntPtr unionmember4;  
};  
```  
  
## <a name="members"></a>成員  
 `bpLocationType`  
 中的值[BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md)列舉用來解譯`bpLocation`union 或`unionmemberX`成員。  
  
 `bpLocation`.`bplocCodeFileLine`  
 [只有 c + +]包含[BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)結構如果`bpLocationType`  =  `BPLT_CODE_FILE_LINE`。  
  
 `bpLocation.bplocCodeFuncOffset`  
 [只有 c + +]包含[BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)結構如果`bpLocationType`  =  `BPLT_CODE_FUNC_OFFSET`。  
  
 `bpLocation.bplocCodeContext`  
 [只有 c + +]包含[BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)結構如果`bpLocationType`  =  `BPLT_CODE_CONTEXT`。  
  
 `bpLocation.bplocCodeString`  
 [只有 c + +]包含[BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)結構如果`bpLocationType`  =  `BPLT_CODE_STRING`。  
  
 `bpLocation.bplocCodeAddress`  
 [只有 c + +]包含[BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)結構如果`bpLocationType`  =  `BPLT_CODE_ADDRESS`。  
  
 `bpLocation.bplocDataString`  
 [只有 c + +]包含[BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)結構如果`bpLocationType`  =  `BPLT_DATA_STRING`。  
  
 `bpLocation.bplocResolution`  
 [只有 c + +]包含[BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)結構如果`bpLocationType`  =  `BPLT_RESOLUTION`。  
  
 `unionmember1`  
 [僅限 C#]請參閱 < 備註 >，有關如何解譯。  
  
 `unionmember2`  
 [僅限 C#]請參閱 < 備註 >，有關如何解譯。  
  
 `unionmember3`  
 [僅限 C#]請參閱 < 備註 >，有關如何解譯。  
  
 `unionmember4`  
 [僅限 C#]請參閱 < 備註 >，有關如何解譯。  
  
## <a name="remarks"></a>備註  
 這個結構是屬於[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)和[BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)結構。  
  
 [僅限 C#]`unionmemberX`成員會根據下表來解譯。 尋找左側資料行的`bpLocationType`值，然後尋找其他資料行來判斷每個跨`unionmemberX`成員代表和封送處理`unionmemberX`據此。 請參閱範例的方法來解譯此結構在 C# 中的一部分。  
  
|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|  
|----------------------|--------------------|--------------------|--------------------|--------------------|  
|`BPLT_CODE_FILE_LINE`|`string`（內容）|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|-|-|  
|`BPLT_CODE_FUNC_OFFSET`|`string`（內容）|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|-|-|  
|`BPLT_CODE_CONTEXT`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|  
|`BPLT_CODE_STRING`|`string`（內容）|`string`（條件式運算式）|-|-|  
|`BPLT_CODE_ADDRESS`|`string`（內容）|`string`(模組 URL)|`string`（函式名稱）|`string`（位址）|  
|`BPLT_DATA_STRING`|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|`string`（內容）|`string`（資料運算式）|`uint`（項目數目）|  
|`BPLT_RESOLUTION`|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|-|-|-|  
  
## <a name="example"></a>範例  
 這個範例示範如何解譯`BP_LOCATION`結構中的 C#`BPLT_DATA_STRING`型別。 這個特定的類型會顯示如何解譯這四種`unionmemberX`所有可能的格式 （物件、 字串和數字） 中的成員。  
  
```csharp  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(BP_LOCATION bp)  
        {  
            if (bp.bpLocationType == (uint)enum_BP_LOCATION_TYPE.BPLT_DATA_STRING)  
            {  
                 IDebugThread2 pThread = (IDebugThread2)Marshal.GetObjectForIUnknown(bp.unionmember1);  
                 string context = Marshal.PtrToStringBSTR(bp.unionmember2);  
                 string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);  
                 uint numElements = (uint)Marshal.ReadInt32(bp.unionmember4);  
            }  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)   
 [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)   
 [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)   
 [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)   
 [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)   
 [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)   
 [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)