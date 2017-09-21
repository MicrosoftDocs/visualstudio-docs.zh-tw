---
title: "METADATA_ADDRESS_FIELD | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "METADATA_ADDRESS_FIELD"
helpviewer_keywords: 
  - "METADATA_ADDRESS_FIELD 結構"
ms.assetid: 15ab45fe-6b3b-4e09-880b-31b34f523607
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# METADATA_ADDRESS_FIELD
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個結構是表示類別或結構的欄位的位址。  
  
## 語法  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_FIELD {  
   _mdToken tokField;  
} METADATA_ADDRESS_FIELD  
```  
  
```c#  
public struct METADATA_ADDRESS_FIELD {  
   public int tokField;  
}  
```  
  
## 詞彙  
 tokField  
 欄位語彙基元的識別碼。  
  
 \[C\+\+\]`_mdToken` is a `typedef` for a 32\-bit `int`.  
  
## 備註  
 這個結構屬於等位中的[DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)結構時`dwKind`欄位的`DEBUG_ADDRESS_UNION`結構設定為 \[ `ADDRESS_KIND_FIELD` \(介於[ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)列舉型別\)。  
  
## 需求  
 標頭: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)