---
title: "IDebugMethodField::EnumAllLocals | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::EnumAllLocals"
helpviewer_keywords: 
  - "IDebugMethodField::EnumAllLocals 方法"
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugMethodField::EnumAllLocals
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

建立方法，包括在內部編譯器產生的所有區域變數的列舉值。  
  
## 語法  
  
```cpp#  
HRESULT EnumAllLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```c#  
int EnumAllLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### 參數  
 `pAddress`  
 \[in\][IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)物件，表示在方法中，指向特定的範圍 」 或 「 內容是偵錯地址。  
  
 `ppLocals`  
 \[\] out傳回[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)物件，代表在指定的範圍 ； 所有區域變數的清單 否則，會傳回 null 值，表示沒有區域變數。  
  
## 傳回值  
 如果成功的話，會傳回 S\_OK，或傳回 S\_FALSE，如果不有任何區域變數。  否則，會傳回錯誤碼。  
  
## 備註  
 只有包含特定的偵錯的地址區塊中所定義的變數，才會列舉。  這個方法會包含任何編譯器所產生的區域變數。  如果所需要的全部都在原始檔，這項呼叫中明確定義的區域變數[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)方法。  
  
 一種方法可以包含多個範圍的內容或區塊。  
  
## 請參閱  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)