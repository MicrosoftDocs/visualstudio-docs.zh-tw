---
title: "IDebugClassField::GetEnclosingClass | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField::GetEnclosingClass"
helpviewer_keywords: 
  - "IDebugClassField::GetEnclosingClass 方法"
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugClassField::GetEnclosingClass
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得圍住此類別的類別。  
  
## 語法  
  
```cpp#  
HRESULT GetEnclosingClass(   
   IDebugClassField** ppClassField  
);  
```  
  
```c#  
int GetEnclosingClass(  
   out IDebugClassField ppClassField  
);  
```  
  
#### 參數  
 `ppClassField`  
 \[\] out傳回[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)物件，代表封入類別。  如果沒有任何封入類別，則傳回 null 值。  
  
## 傳回值  
 如果成功的話，則傳回 S\_OK。 否則，會傳回錯誤碼。  
  
## 備註  
 如果類別由這[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)物件是巢狀的類別，然後在`ppClassField`參數會傳回`IDebugClassField`物件，代表封入類別。  例如，假設此類別定義：  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 呼叫`GetEnclosingClass`上的方法`IDebugClassField`物件代表`NestedClass`類別傳回`IDebugClassField`物件，代表該類別`RootClass`。  
  
## 請參閱  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)