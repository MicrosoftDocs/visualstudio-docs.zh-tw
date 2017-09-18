---
title: "PDB_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PDB_TYPE"
helpviewer_keywords: 
  - "PDB_TYPE 結構"
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# PDB_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個結構指定取自 PDB 符號的欄位型別相關的資訊。  
  
## 語法  
  
```cpp#  
typedef struct _tagTYPE_PDB {  
   ULONG32 ulAppDomainID;  
   GUID    guidModule;  
   DWORD   symid;  
} PDB_TYPE;  
```  
  
```c#  
public struct PDB_TYPE {  
   public uint ulAppDomainID;  
   public Guid guidModule;  
   public uint symid;  
};  
```  
  
#### 參數  
 ulAppDomainID  
 該符號的來源應用程式的識別碼。  這用來唯一地識別應用程式的執行個體。  
  
 guidModule  
 模組包含此欄位的 GUID。  
  
 symid  
 符號這個欄位的對應的識別碼。  
  
## 備註  
 這個結構就會出現在 \[聯集的一部分[TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)結構時`dwKind`欄位的`TYPE_INFO`結構設定為 \[ `TYPE_KIND_PDB` \(介於[dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)列舉型別\)。  
  
## 需求  
 標頭: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)