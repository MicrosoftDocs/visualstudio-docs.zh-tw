---
title: "EXCEPTION_STATE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EXCEPTION_STATE"
helpviewer_keywords: 
  - "EXCEPTION_STATE 列舉型別"
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# EXCEPTION_STATE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定的例外狀況的狀態。  
  
## 語法  
  
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
  
```c#  
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
  
## Members  
 EXCEPTION\_NONE  
 不會停止在例外狀況。  
  
 EXCEPTION\_STOP\_FIRST\_CHANCE  
 停止在第一個引發的例外狀況。  描述例外狀況事件，當這個旗標會指示要執行的例外狀況事件是第一個出現的例外狀況的事件。  
  
 EXCEPTION\_STOP\_SECOND\_CHANCE  
 停止在第二個引發的例外狀況。  時描述例外狀況事件，表示例外狀況事件是第二個可能的例外狀況的事件。  
  
 EXCEPTION\_STOP\_USER\_FIRST\_CHANCE  
 在使用者模式例外狀況的第一個引發停止。  時描述例外狀況事件，表示例外狀況事件已發生第一個使用者的例外狀況事件。  
  
 EXCEPTION\_STOP\_USER\_UNCAUGHT  
 使用者模式例外狀況未被攔截時，就會停止。  時描述例外狀況事件，表示例外狀況事件是發生無法攔截的使用者模式例外事件。  
  
 EXCEPTION\_STOP\_ALL  
 停止任何例外狀況。  描述例外狀況事件時，無法使用。  
  
 EXCEPTION\_CANNOT\_BE\_CONTINUED  
 描述例外狀況事件，表示例外狀況不能從已繼續。  
  
 EXCEPTION\_CODE\_SUPPORTED  
 指示例外狀況有支援它的程式碼。  用來顯示例外狀況  
  
 EXCEPTION\_CODE\_DISPLAY\_IN\_HEX  
 表示例外狀況的程式碼應該會顯示在 \[十六進位。  用於顯示例外狀況。  
  
 EXCEPTION\_JUST\_MY\_CODE\_SUPPORTED  
 指示例外狀況的程式碼支援 JustMyCode。  用於顯示例外狀況。  
  
 EXCEPTION\_MANAGED\_DEBUG\_ASSISTANT  
 表示 managed 程式碼偵錯工具應該可以處理的例外狀況。  如果沒有設定，預設的偵錯工具處理例外狀況。  這會傳遞至[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)方法並不會用於[EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md)結構。  
  
 EXCEPTION\_STOP\_FIRST\_CHANCE\_USE\_PARENT  
 過時的請不要使用。  
  
 EXCEPTION\_STOP\_SECOND\_CHANCE\_USE\_PARENT  
 過時的請不要使用。  
  
 EXCEPTION\_STOP\_USER\_FIRST\_CHANCE\_USE\_PARENT  
 過時的請不要使用。  
  
 EXCEPTION\_STOP\_USER\_SECOND\_CHANCE\_USE\_PARENT  
 過時的請不要使用。  
  
## 備註  
 用來作為`dwState`成員的[EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md)結構，以指出例外狀況，並有什麼因應對策它的狀態。  
  
 這些值也會傳遞至[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)方法，以設定狀態的所有例外狀況。  
  
 可能與位元的 OR 合併使用這些旗標。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)