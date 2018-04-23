---
title: AD_PROCESS_ID_TYPE |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f8318efdc64adf9792e44ccf2f4ad4aa9f74dd67
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="adprocessidtype"></a>AD_PROCESS_ID_TYPE
指定如何解譯中的處理序識別碼[AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)結構。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
typedef DWORD AD_PROCESS_ID_TYPE;  
```  
  
```csharp  
public enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
```  
  
## <a name="members"></a>成員  
 AD_PROCESS_ID_SYSTEM  
 處理序識別碼是系統識別項。 使用`ProcessId.dwProcessId`欄位[AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)結構。  
  
 AD_PROCESS_ID_GUID  
 處理序識別碼是 GUID。 使用`ProcessId.guidProcessId`欄位`AD_PROCESS_ID`結構。  
  
## <a name="remarks"></a>備註  
 用於`ProcessIdType`隸屬[AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)結構，以識別包含在結構中的處理序識別碼的類型。 決定如何解譯`ProcessId`等位結構中。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)