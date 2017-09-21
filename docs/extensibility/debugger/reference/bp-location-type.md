---
title: "BP_LOCATION_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_LOCATION_TYPE"
helpviewer_keywords: 
  - "BP_LOCATION_TYPE 結構"
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_LOCATION_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定位置的中斷點類型的中斷點要求。  
  
## 語法  
  
```cpp#  
enum enum_BP_LOCATION_TYPE {   
   BPLT_NONE               = 0x00000000,  
   BPLT_FILE_LINE          = 0x00010000,  
   BPLT_FUNC_OFFSET        = 0x00020000,  
   BPLT_CONTEXT            = 0x00030000,  
   BPLT_STRING             = 0x00040000,  
   BPLT_ADDRESS            = 0x00050000,  
   BPLT_RESOLUTION         = 0x00060000,  
   BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,  
   BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,  
   BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,  
   BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,  
   BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,  
   BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,  
   BPLT_TYPE_MASK          = 0x0000FFFF,  
   BPLT_LOCATION_TYPE_MASK = 0xFFFF0000  
};  
typedef DWORD BP_LOCATION_TYPE;  
```  
  
```c#  
public enum enum_BP_LOCATION_TYPE {   
   BPLT_NONE               = 0x00000000,  
   BPLT_FILE_LINE          = 0x00010000,  
   BPLT_FUNC_OFFSET        = 0x00020000,  
   BPLT_CONTEXT            = 0x00030000,  
   BPLT_STRING             = 0x00040000,  
   BPLT_ADDRESS            = 0x00050000,  
   BPLT_RESOLUTION         = 0x00060000,  
   BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,  
   BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,  
   BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,  
   BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,  
   BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,  
   BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,  
   BPLT_TYPE_MASK          = 0x0000FFFF,  
   BPLT_LOCATION_TYPE_MASK = 0xFFFF0000  
};  
```  
  
## Members  
 BPLT\_NONE  
 指定中斷點的位置。  
  
 BPLT\_FILE\_LINE  
 檔案行中指定中斷點位置型的別。  
  
 BPLT\_FUNC\_OFFSET  
 指定的位置類型之中斷點的函式的位移。  
  
 BPLT\_CONTEXT  
 指定位置的中斷點類型，做為內容。  
  
 BPLT\_STRING  
 以字串中指定位置的中斷點類型。  
  
 BPLT\_ADDRESS  
 指定位置的中斷點類型，做為地址。  
  
 BPLT\_RESOLUTION  
 指定位置的中斷點類型，解決問題。  
  
 BPLT\_CODE\_FILE\_LINE  
 原始程式碼行以指定位置的中斷點類型。  
  
 BPLT\_CODE\_FUNC\_OFFSET  
 請指定位置的中斷點類型的程式碼函式的位移。  
  
 BPLT\_CODE\_CONTEXT  
 做為程式碼內容中指定位置的中斷點類型。  
  
 BPLT\_CODE\_STRING  
 以程式碼字串中指定位置的中斷點類型。  
  
 BPLT\_CODE\_ADDRESS  
 指定位置的中斷點類型，做為程式碼的位址。  
  
 BPLT\_DATA\_STRING  
 指定位置的中斷點類型，做為資料字串。  
  
 BPLT\_TYPE\_MASK  
 指定位元遮罩，中斷點類型可擷取的值用完。  
  
 BPLT\_LOCATION\_TYPE\_MASK  
 位元遮罩，指定的中斷點位置類型可擷取的值用完。  
  
## 備註  
 做為參數來傳遞[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)方法。  
  
 中斷點位置類型是由中斷點類型和位置類型所組成。  這表示中斷點位置類型不只是中斷點的型別 \(比方說， `BPT_CODE`\) 或位置的型別 \(例如， `BPLT_FILE_LINE`\)。  這個列舉型別中包含預先定義的常數，對目前支援的所有中斷點位置類型 \(`BPLT_CODE_FILE_LINE`到`BPLT_DATA_STRING`\)。  
  
 `BPT_CODE` 和 `BPT_DATA` 是 [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md) 列舉的成員。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)   
 [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md)