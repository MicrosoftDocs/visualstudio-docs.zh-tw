---
title: "BP_LOCATION_TYPE |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_LOCATION_TYPE
helpviewer_keywords: BP_LOCATION_TYPE structure
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7db6cbd73ba45d05b878648101a7643f21879076
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="bplocationtype"></a>BP_LOCATION_TYPE
指定中斷點要求中斷點的位置類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_BP_LOCATION_TYPE {   
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
  
```csharp  
public enum enum_BP_LOCATION_TYPE {   
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
  
## <a name="members"></a>成員  
 BPLT_NONE  
 不指定任何中斷點的位置。  
  
 BPLT_FILE_LINE  
 指定中斷點的位置類型為的檔案。  
  
 BPLT_FUNC_OFFSET  
 指定中斷點的位置類型當作函式位移。  
  
 BPLT_CONTEXT  
 指定中斷點的位置類型做為內容。  
  
 BPLT_STRING  
 指定中斷點的位置類型為字串。  
  
 BPLT_ADDRESS  
 指定中斷點的位置類型為位址。  
  
 BPLT_RESOLUTION  
 指定中斷點的位置類型做為解析度。  
  
 BPLT_CODE_FILE_LINE  
 指定中斷點的位置類型做為來源的程式碼行。  
  
 BPLT_CODE_FUNC_OFFSET  
 指定中斷點的位置類型做為程式碼的函式位移。  
  
 BPLT_CODE_CONTEXT  
 指定中斷點的位置類型做為程式碼內容。  
  
 BPLT_CODE_STRING  
 指定中斷點的位置類型做為程式碼的字串。  
  
 BPLT_CODE_ADDRESS  
 指定中斷點的位置類型做為程式碼位址。  
  
 BPLT_DATA_STRING  
 指定中斷點的位置類型做為資料字串。  
  
 BPLT_TYPE_MASK  
 位元遮罩，指定的中斷點類型可以擷取從值。  
  
 BPLT_LOCATION_TYPE_MASK  
 位元遮罩，指定的中斷點位置類型可以擷取從值。  
  
## <a name="remarks"></a>備註  
 做為參數來傳遞[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)方法。  
  
 中斷點位置類型是由中斷點類型和位置類型所組成。 這表示中斷點位置類型永遠不會是僅中斷點的型別 (例如， `BPT_CODE`) 或位置類型 (例如， `BPLT_FILE_LINE`)。 這個列舉型別中包含對目前支援的所有中斷點位置類型的預先定義的常數 (`BPLT_CODE_FILE_LINE`透過`BPLT_DATA_STRING`)。  
  
 `BPT_CODE`和`BPT_DATA`屬於[BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)列舉型別。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)   
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)