---
title: CONTEXT_INFO |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fb634f59a3a7eb3b37e70dd87f48b22a07251d0e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="contextinfo"></a>CONTEXT_INFO
此結構描述的記憶體內容或程式碼內容。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _tagCONTEXT_INFO {   
   CONTEXT_INFO_FIELDS dwFields;  
   BSTR                bstrModuleUrl;  
   BSTR                bstrFunction;  
   TEXT_POSITION       posFunctionOffset;  
   BSTR                bstrAddress;  
   BSTR                bstrAddressOffset;  
   BSTR                bstrAddressAbsolute;  
} CONTEXT_INFO;  
```  
  
```csharp  
public struct CONTEXT_INFO {  
   public uint          dwFields;  
   public string        bstrModuleUrl;  
   public string        bstrFunction;  
   public TEXT_POSITION posFunctionOffset;  
   public string        bstrAddress;  
   public string        bstrAddressOffset;  
   public string        bstrAddressAbsolute;  
};  
```  
  
## <a name="members"></a>成員  
 dwFields  
 從他的旗標的組合[CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)列舉，指定哪些欄位都已填寫**。**  
  
 bstrModuleUrl  
 內容所在位置之模組的名稱。  
  
 bstrFunction  
 內容所在的函式名稱。  
  
 posFunctionOffset  
 A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)識別相關聯的程式碼內容的函式的行和資料行位移的結構。  
  
 bstrAddress  
 指定的內容所在的程式碼中的位址。  
  
 bstrAddressOffset  
 指定的內容所在的程式碼中的位址位移。  
  
 bstrAddressAbsolute  
 指定的內容所在位置的記憶體中的絕對位址。  
  
## <a name="remarks"></a>備註  
 此結構會從呼叫傳回[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)方法。  
  
 此結構的典型用法就是支援**記憶體**偵錯視窗。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)   
 [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)