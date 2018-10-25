---
title: EXCEPTION_INFO |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- EXCEPTION_INFO
helpviewer_keywords:
- EXCEPTION_INFO structure
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4bbefc02a05d03dc966c05941ca08c05cce0a5a5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49947908"
---
# <a name="exceptioninfo"></a>EXCEPTION_INFO
描述例外狀況或擲回的正在偵錯之程式的執行階段錯誤。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct tagEXCEPTION_INFO {   
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   BSTR            bstrExceptionName;  
   DWORD           dwCode;  
   EXCEPTION_STATE dwState;  
   GUID            guidType;  
} EXCEPTION_INFO;  
```  
  
```csharp  
public struct EXCEPTION_INFO {   
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public string         bstrExceptionName;  
   public uint           dwCode;  
   public uint           dwState;  
   public Guid           guidType;  
};  
```  
  
## <a name="members"></a>成員  
 pProgram  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)物件，表示的程式發生例外狀況。  
  
 bstrProgramName  
 發生例外狀況的程式名稱。  
  
 bstrExceptionName  
 例外狀況的名稱。  
  
 dwCode  
 例外狀況或執行階段錯誤的識別碼。  
  
 dwState  
 值，以從[EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)列舉型別，定義例外狀況的狀態。  
  
 guidType  
 GUID 的語言識別項、 任一`guidLang`或`guidEng`。  
  
## <a name="remarks"></a>備註  
 此結構會做為參數傳遞[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)並[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)方法。 此結構也會傳遞至[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)来填入的方法。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)   
 [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)