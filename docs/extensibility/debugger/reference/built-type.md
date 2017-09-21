---
title: "BUILT_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BUILT_TYPE"
helpviewer_keywords: 
  - "BUILT_TYPE 結構"
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# BUILT_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個結構指定來自中繼資料欄位型別相關的資訊。  
  
## 語法  
  
```cpp#  
typedef struct _tagTYPE_BUILT {  
   ULONG32      ulAppDomainID;  
   GUID         guidModule;  
   IDebugField* pUnderlyingField;  
} BUILT_TYPE;  
```  
  
```c#  
public struct BUILT_TYPE {  
   public uint        ulAppDomainID;  
   public Guid        guidModule;  
   public IDebugField pUnderlyingField;  
};  
```  
  
#### 參數  
 ulAppDomainID  
 該符號的來源應用程式的識別碼。  這用來唯一地識別應用程式的執行個體。  
  
 guidModule  
 模組包含此欄位的 GUID。  
  
 pUnderlyingField  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)用來識別這個內建欄位相關聯的基礎欄位的物件。  
  
## 備註  
 這個結構就會出現在 \[聯集的一部分[TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)結構時`dwKind`欄位的`TYPE_INFO`結構設定為 \[ `TYPE_KIND_BUILT` \(介於[dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)列舉型別\)。  
  
## 需求  
 標頭: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)