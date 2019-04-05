---
title: EXCEPTION_STATE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4e30d9cc9df592cc6feb97c14449dbc6a122ec63
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58943161"
---
# <a name="exceptionstate"></a>EXCEPTION_STATE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

指定的例外狀況狀態。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
enum enum_EXCEPTION_STATE {   
   EXCEPTION_NONE                          = 0x0000,  
   EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,  
   EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,  
   EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,  
   EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,  
   EXCEPTION_STOP_ALL                      = 0x00FF,  
   EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,  
  
   // These are for exception types only  
   EXCEPTION_CODE_SUPPORTED                = 0x1000,  
   EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,  
   EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,  
   EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,  
  
   // These are no longer used  
   EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,  
   EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,  
   EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,  
   EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,  
};  
typedef DWORD EXCEPTION_STATE;  
```  
  
```csharp  
public enum enum_EXCEPTION_STATE {   
   EXCEPTION_NONE                          = 0x0000,  
   EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,  
   EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,  
   EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,  
   EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,  
   EXCEPTION_STOP_ALL                      = 0x00FF,  
   EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,  
  
   // These are for exception types only  
   EXCEPTION_CODE_SUPPORTED                = 0x1000,  
   EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,  
   EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,  
   EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,  
  
   // These are no longer used  
   EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,  
   EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,  
   EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,  
   EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,  
};  
```  
  
## <a name="members"></a>成員  
 EXCEPTION_NONE  
 不會停止在例外狀況。  
  
 EXCEPTION_STOP_FIRST_CHANCE  
 停止在第一個引發的例外狀況。 描述例外狀況事件，當此旗標會指出例外狀況事件是第一個可能發生的例外狀況的事件。  
  
 EXCEPTION_STOP_SECOND_CHANCE  
 停止在第二個引發的例外狀況。 當描述例外狀況事件，表示例外狀況事件的第二個可能發生例外狀況事件。  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE  
 在使用者模式例外狀況的第一次引發處停止。 當描述例外狀況事件，表示例外狀況事件的第一個可能發生使用者例外狀況事件。  
  
 EXCEPTION_STOP_USER_UNCAUGHT  
 當未攔截到的使用者模式例外狀況時停止。 當描述例外狀況事件，表示例外狀況事件無法攔截的使用者模式例外狀況事件。  
  
 EXCEPTION_STOP_ALL  
 停止的任何例外狀況。 描述例外狀況事件時，無法使用。  
  
 EXCEPTION_CANNOT_BE_CONTINUED  
 描述例外狀況事件，表示例外狀況，無法繼續從。  
  
 EXCEPTION_CODE_SUPPORTED  
 表示例外狀況有支援它的程式碼。 用來顯示例外狀況  
  
 EXCEPTION_CODE_DISPLAY_IN_HEX  
 表示以十六進位方式，應該會顯示例外狀況代碼。 用來顯示例外狀況。  
  
 EXCEPTION_JUST_MY_CODE_SUPPORTED  
 表示例外狀況的程式碼支援 JustMyCode。 用來顯示例外狀況。  
  
 EXCEPTION_MANAGED_DEBUG_ASSISTANT  
 表示 managed 程式碼偵錯工具應該處理的例外狀況。 如果沒有設定，預設偵錯工具處理的例外狀況。 這會傳遞至[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)方法並不會用於[EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)結構。  
  
 EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT  
 已淘汰，請勿使用。  
  
 EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT  
 已淘汰，請勿使用。  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT  
 已淘汰，請勿使用。  
  
 EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT  
 已淘汰，請勿使用。  
  
## <a name="remarks"></a>備註  
 做`dwState`隸屬[EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)結構來表示的狀態，以及例外狀況有關它可以做什麼。  
  
 這些值也會傳遞給[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)方法來設定所有的例外狀況的狀態。  
  
 這些旗標可能會與位元 OR 運算結合。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)
