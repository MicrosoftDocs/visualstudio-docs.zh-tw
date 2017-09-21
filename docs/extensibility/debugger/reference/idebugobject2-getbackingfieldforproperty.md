---
title: "IDebugObject2::GetBackingFieldForProperty | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject2::GetBackingFieldForProperty"
helpviewer_keywords: 
  - "IDebugObject2::GetBackingFieldForProperty 方法"
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugObject2::GetBackingFieldForProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得變數的欄位 \(如果有的話\)，可能會支援這個物件所表示的屬性。  
  
## 語法  
  
```cpp  
HRESULT GetBackingFieldForProperty(  
   IDebugObject2** ppObject  
);  
```  
  
```c#  
int GetBackingFieldForProperty(  
   out IDebugObject2 ppObject  
);  
```  
  
#### 參數  
 `ppObject`  
 \[\] out[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)物件，描述支援的欄位。  
  
## 傳回值  
 如果成功的話，則傳回 S\_OK。 否則，會傳回錯誤碼。  
  
## 備註  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)物件代表一個 managed 程式碼類別屬性，也就是使用 get 方法和 \(或\) set 存取子。  這類屬性通常會需要變數來包含操作屬性的值。  這個變數就是所謂的支援欄位。  如果物件不支援欄位，請務必傳回 null 值： 某些呼叫端可能不會注意到傳回的值，但會看起來中已傳回了 null 值，請參閱`ppObject`。  
  
## 請參閱  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)