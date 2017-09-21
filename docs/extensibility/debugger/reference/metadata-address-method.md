---
title: "METADATA_ADDRESS_METHOD | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "METADATA_ADDRESS_METHOD"
helpviewer_keywords: 
  - "METADATA_ADDRESS_METHOD 結構"
ms.assetid: fc0e5370-1b4f-4867-837f-0d63c4b9dd09
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# METADATA_ADDRESS_METHOD
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個結構是表示類別的方法的位址。  
  
## 語法  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_METHOD {  
   _mdToken tokMethod;  
   DWORD    dwOffset;  
   DWORD    dwVersion;  
} METADATA_ADDRESS_METHOD;  
```  
  
```c#  
public struct METADATA_ADDRESS_METHOD {  
   public int  tokMethod;  
   public uint dwOffset;  
   public uint dwVersion;  
}  
```  
  
## 詞彙  
 tokMethod  
 方法的識別碼。  
  
 \[C\+\+\]`_mdToken` is a `typedef` for a 32\-bit `int`.  
  
 dwOffset  
 \(可以 vtable 中表示的位移\) 這個方法從類別開始的位移。  
  
 dwVersion  
 \(這個值是唯一的符號提供者\) 的方法版本。  
  
## 備註  
 這個結構屬於等位中的[DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)結構時`dwKind`欄位的`DEBUG_ADDRESS_UNION`結構設定為 \[ `ADDRESS_KIND_METHOD` \(介於[ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)列舉型別\)。  
  
## 需求  
 標頭: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)