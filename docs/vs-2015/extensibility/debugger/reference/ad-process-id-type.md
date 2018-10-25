---
title: AD_PROCESS_ID_TYPE |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ff8645bcca588f6c186d96f43bdda491bf07c7f5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49907660"
---
# <a name="adprocessidtype"></a>AD_PROCESS_ID_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

指定如何解譯中的處理序識別碼[AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)結構。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 系統識別項處理序 ID。 使用`ProcessId.dwProcessId`欄位[AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)結構。  
  
 AD_PROCESS_ID_GUID  
 處理序識別碼是 GUID。 使用`ProcessId.guidProcessId`欄位`AD_PROCESS_ID`結構。  
  
## <a name="remarks"></a>備註  
 用於`ProcessIdType`隸屬[AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)結構，以識別包含在結構中的處理序識別碼的類型。 決定如何解譯`ProcessId`聯集結構中。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)

