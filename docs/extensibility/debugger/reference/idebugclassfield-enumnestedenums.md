---
title: "IDebugClassField::EnumNestedEnums | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField::EnumNestedEnums"
helpviewer_keywords: 
  - "IDebugClassField::EnumNestedEnums 方法"
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugClassField::EnumNestedEnums
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

建立巢狀列舉值，這個類別的列舉值。  
  
## 語法  
  
```cpp#  
HRESULT EnumNestedEnums(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int EnumNestedEnums(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### 參數  
 `ppEnum`  
 \[\] out傳回[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)物件，表示巢狀列舉型別的清單。  如果不有任何巢狀列舉型別，則傳回 null 值。  
  
## 傳回值  
 如果成功的話，會傳回 S\_OK，或傳回 S\_FALSE，如果不有任何巢狀列舉值。  否則，會傳回錯誤碼。  
  
## 備註  
 列舉型別的每個元素都是[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)物件，描述的巢狀列舉型別。  
  
 在類別內宣告列舉型別會被視為巢狀列舉型別。  例如，指定下列程式碼：  
  
```  
class RootClass {  
   enum NestedEnum { EnumValue = 0 }  
};  
```  
  
 `EnumNestedEnums`方法會傳回[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)物件，其中包含一個[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)物件，代表`NestedEnum`列舉型別。  
  
## 請參閱  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)