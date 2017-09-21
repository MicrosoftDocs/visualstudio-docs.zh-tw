---
title: "IDebugClassField::EnumNestedClasses | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField::EnumNestedClasses"
helpviewer_keywords: 
  - "IDebugClassField::EnumNestedClasses 方法"
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugClassField::EnumNestedClasses
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

建立這個類別中巢狀類別列舉值。  
  
## 語法  
  
```cpp#  
HRESULT EnumNestedClasses(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int EnumNestedClasses(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### 參數  
 `ppEnum`  
 \[\] out傳回[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)物件，表示巢狀類別的清單。  如果沒有巢狀的類別，則傳回 null 值。  
  
## 傳回值  
 如果成功的話，傳回 S\_OK 則會傳回 S\_FALSE，如果沒有巢狀的類別。  否則，會傳回錯誤碼。  
  
## 備註  
 列舉型別的每個元素都是[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)物件，描述巢狀的類別。  
  
 巢狀的類別是在另一個類別內定義的類別。  例如：  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)列舉型別會包含另一個物件代表`NestedClass`類別。  
  
## 請參閱  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)