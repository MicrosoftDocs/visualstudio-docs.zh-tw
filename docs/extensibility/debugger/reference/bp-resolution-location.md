---
title: BP_RESOLUTION_LOCATION |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BP_RESOLUTION_LOCATION
helpviewer_keywords:
- BP_RESOLUTION_LOCATION structure
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a85c6c097867aea17be4b4aeca1431a05c74903a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="bpresolutionlocation"></a>BP_RESOLUTION_LOCATION
指定中斷點解析位置的結構。  
  
## <a name="syntax"></a>語法  
  
```cpp  
struct _BP_RESOLUTION_LOCATION {  
   BP_TYPE bpType;  
   union {  
      BP_RESOLUTION_CODE bpresCode;  
      BP_RESOLUTION_DATA bpresData;  
      int                unused;  
   } bpResLocation;  
} BP_RESOLUTION_LOCATION;  
```  
  
```csharp  
public struct BP_RESOLUTION_LOCATION {  
   public uint bpType;  
   public IntPtr unionmember1;  
   public IntPtr unionmember2;  
   public IntPtr unionmember3;  
   public uint   unionmember4;  
};  
```  
  
## <a name="members"></a>成員  
 `bpType`  
 中的值[BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)列舉，指定如何解譯`bpResLocation`union 或`unionmemberX`成員。  
  
 `bpResLocation.bpresCode`  
 [只有 c + +]包含[BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)結構如果`bpType`  =  `BPT_CODE`。  
  
 `bpResLocation.bpresData`  
 [只有 c + +]包含[BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)結構如果`bpType`  =  `BPT_DATA`。  
  
 `bpResLocation.unused`  
 [只有 c + +]預留位置。  
  
 `unionmember1`  
 [僅限 C#]請參閱 < 備註 >，有關如何解譯。  
  
 `unionmember2`  
 [僅限 C#]請參閱 < 備註 >，有關如何解譯。  
  
 `unionmember3`  
 [僅限 C#]請參閱 < 備註 >，有關如何解譯。  
  
 `unionmember4`  
 [僅限 C#]請參閱 < 備註 >，有關如何解譯。  
  
## <a name="remarks"></a>備註  
 這個結構是屬於[BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)和[BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)結構。  
  
 [僅限 C#]`unionmemberX`成員會根據下表來解譯。 尋找左側資料行的`bpType`來判斷每個值然後透過`unionmemberX`成員代表和封送處理`unionmemberX`據此。 請參閱 < 如何解譯此結構在 C# 中的範例。  
  
|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|  
|----------------------|--------------------|--------------------|--------------------|--------------------|  
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|  
|`BPT_DATA`|`string`（資料運算式）|`string`（函式名稱）|`string`（映像名稱）|`enum_BP_RES_DATA_FLAGS`|  
  
## <a name="example"></a>範例  
 這個範例示範如何解譯`BP_RESOLUTION_LOCATION`C# 中的結構。  
  
```csharp  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(BP_RESOLUTION_LOCATION bprl)  
        {  
            if (bprl.bpType == (uint)enum_BP_TYPE.BPT_CODE)  
            {  
                 IDebugCodeContext2 pContext = (IDebugCodeContext2)Marshal.GetObjectForIUnknown(bp.unionmember1);  
            }  
            else if (bprl.bpType == (uint)enum_BP_TYPE.BPT_DATA)  
            {  
                 string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);  
                 string functionName = Marshal.PtrToStringBSTR(bp.unionmember2);  
                 string imageName = Marshal.PtrToStringBSTR(bp.unionmember3);  
                 enum_BP_RES_DATA_FLAGS numElements = (enum_BP_RES_DATA_FLAGS)bp.unionmember4;  
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
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)   
 [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)   
 [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)