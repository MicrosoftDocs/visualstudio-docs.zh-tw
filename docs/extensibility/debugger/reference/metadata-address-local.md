---
title: "METADATA_ADDRESS_LOCAL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "METADATA_ADDRESS_LOCAL"
helpviewer_keywords: 
  - "METADATA_ADDRESS_LOCAL 結構"
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# METADATA_ADDRESS_LOCAL
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個結構是表示 \(通常是函式或方法\) 的範圍內的區域變數的位址。  
  
## 語法  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_LOCAL {  
   _mdToken  tokMethod;  
   IUnknown* pLocal;  
   DWORD     dwIndex;  
} METADATA_ADDRESS_LOCAL;  
```  
  
```c#  
public struct METADATA_ADDRESS_LOCAL {  
   public int    tokMethod;  
   public object pLocal;  
   public uint   dwIndex;  
}  
```  
  
## 詞彙  
 tokMethod  
 方法或函式的 ID 區域變數是部份。  
  
 \[C\+\+\]`_mdToken` is a `typedef` for a 32\-bit `int`.  
  
 pLocal  
 這個結構是表示其地址之語彙基元。  
  
 dwIndex  
 可以是這個區域變數之方法或函式，或其他值 \(特定語言\) 的索引。  
  
## 備註  
 這個結構屬於等位中的[DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)結構時`dwKind`欄位的`DEBUG_ADDRESS_UNION`結構設定為 \[ `ADDRESS_KIND_LOCAL` \(介於[ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)列舉型別\)。  
  
 `Warning:` \[只有 c \+ \+\]如果`pLocal`不是 null，則您必須呼叫`Release`語彙基元的指標 \(`addr`是一個欄位，在[DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)結構\)：  
  
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
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)