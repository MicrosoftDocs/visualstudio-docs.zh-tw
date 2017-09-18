---
title: "DEBUG_ADDRESS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEBUG_ADDRESS"
helpviewer_keywords: 
  - "DEBUG_ADDRESS 結構"
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# DEBUG_ADDRESS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此結構代表地址。  
  
## 語法  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS {  
   ULONG32             ulAppDomainID;  
   GUID                guidModule;  
   _mdToken            tokClass;  
   DEBUG_ADDRESS_UNION addr;  
} DEBUG_ADDRESS;  
```  
  
```c#  
public struct DEBUG_ADDRESS {  
   public uint                ulAppDomainID;  
   public Guid                guidModule;  
   public int                 tokClass;  
   public DEBUG_ADDRESS_UNION addr;  
}  
```  
  
## 詞彙  
 ulAppDomainID  
 處理序 id。  
  
 guidModule  
 模組含有此位址的 GUID。  
  
 tokClass  
 語彙基元，用來識別這個地址類型的類別。  
  
> [!NOTE]
>  這個值會是專用符號的提供者，因此並不是做為類別型別識別項的一般意義。  
  
 地址  
 A [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)結構，其中包含結構描述的個別地址類型的聯集。  值`addr`。`dwKind`來自[ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)列舉型別，而這正說明如何解譯聯集。  
  
## 備註  
 這個結構會傳遞至[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)方法，會自動填入。  
  
 **警告 \[只有 c \+ \+\]**  
  
 如果`addr.dwKind`是`ADDRESS_KIND_METADATA_LOCAL`則為由右`addr.addr.addrLocal.pLocal`不是 null 值，則您必須呼叫`Release`語彙基元的指標：  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## 需求  
 標頭: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)