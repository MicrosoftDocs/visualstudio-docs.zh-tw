---
title: "FIELD_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FIELD_INFO"
helpviewer_keywords: 
  - "FIELD_INFO 結構"
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# FIELD_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個結構所描述的區域變數、 參數或另一個欄位。  
  
## 語法  
  
```cpp#  
typedef struct _tagFieldInfo {   
   FIELD_INFO_FIELDS dwFields;  
   BSTR              bstrFullName;  
   BSTR              bstrName;  
   BSTR              bstrType;  
   FIELD_MODIFIERS   dwModifiers;  
} FIELD_INFO;  
```  
  
```c#  
public struct FIELD_INFO {  
   public uint   dwFields;  
   public string bstrFullName;  
   public string bstrName;  
   public string bstrType;  
   public uint   dwModifiers;  
};  
```  
  
## Members  
 dwFields  
 從的旗標組合[FIELD\_INFO\_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)指定哪些成員要填入的列舉型別。  
  
 bstrFullName  
 欄位的完整名稱。  
  
 bstrName  
 欄位的簡短名稱。  
  
 bstrType  
 欄位的型別。  
  
 dwModifiers  
 從的旗標組合[FIELD\_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)列舉型別描述的欄位。  
  
## 備註  
 這個結構會傳遞至[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)填滿其中的方法。  
  
## 需求  
 標頭: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FIELD\_INFO\_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)   
 [FIELD\_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)