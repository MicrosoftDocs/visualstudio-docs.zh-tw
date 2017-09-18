---
title: "BP_RESOLUTION_LOCATION | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_RESOLUTION_LOCATION"
helpviewer_keywords: 
  - "BP_RESOLUTION_LOCATION 結構"
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_RESOLUTION_LOCATION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定中斷點的解析度位置的結構。  
  
## 語法  
  
```cpp#  
struct _BP_RESOLUTION_LOCATION {  
   BP_TYPE bpType;  
   union {  
      BP_RESOLUTION_CODE bpresCode;  
      BP_RESOLUTION_DATA bpresData;  
      int                unused;  
   } bpResLocation;  
} BP_RESOLUTION_LOCATION;  
```  
  
```c#  
public struct BP_RESOLUTION_LOCATION {  
   public uint bpType;  
   public IntPtr unionmember1;  
   public IntPtr unionmember2;  
   public IntPtr unionmember3;  
   public uint   unionmember4;  
};  
```  
  
## Members  
 `bpType`  
 介於[BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md)列舉型別，指定如何解譯`bpResLocation`等位或`unionmemberX`成員。  
  
 `bpResLocation.bpresCode`  
 \[只有 c \+ \+\]Contains the [BP\_RESOLUTION\_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) structure if `bpType` \= `BPT_CODE`.  
  
 `bpResLocation.bpresData`  
 \[只有 c \+ \+\]Contains the [BP\_RESOLUTION\_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) structure if `bpType` \= `BPT_DATA`.  
  
 `bpResLocation.unused`  
 \[只有 c \+ \+\]版面配置區。  
  
 `unionmember1`  
 \[C\# 只\]請參閱有關如何解譯的註解。  
  
 `unionmember2`  
 \[C\# 只\]請參閱有關如何解譯的註解。  
  
 `unionmember3`  
 \[C\# 只\]請參閱有關如何解譯的註解。  
  
 `unionmember4`  
 \[C\# 只\]請參閱有關如何解譯的註解。  
  
## 備註  
 這個結構屬於[BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)和[BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)結構。  
  
 \[C\# 只\]`unionmemberX`成員會被解譯如下表。  向畫面左邊欄位的下瀏覽`bpType`的值然後橫向來判斷每一`unionmemberX`成員表示呼叫和封送處理`unionmemberX`據以。  請參閱的方式來解譯此結構在 C\# 中的範例。  
  
|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|  
|----------------------|--------------------|--------------------|--------------------|--------------------|  
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|\-|\-|\-|  
|`BPT_DATA`|`string`\(資料的運算式\)|`string`\(函式名稱\)|`string`\(影像名稱\)|`enum_BP_RES_DATA_FLAGS`|  
  
## 範例  
 這個範例會示範如何解譯`BP_RESOLUTION_LOCATION` C\# 中的結構。  
  
```c#  
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
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md)   
 [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP\_RESOLUTION\_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)   
 [BP\_RESOLUTION\_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)   
 [BP\_RES\_DATA\_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)