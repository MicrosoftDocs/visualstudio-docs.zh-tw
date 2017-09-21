---
title: "DEBUG_ADDRESS_UNION | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEBUG_ADDRESS_UNION"
helpviewer_keywords: 
  - "DEBUG_ADDRESS_UNION 等位"
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# DEBUG_ADDRESS_UNION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

說明不同類型的地址。  
  
## 語法  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS_UNION {  
   ADDRESS_KIND dwKind;  
   union {  
      NATIVE_ADDRESS                  addrNative;  
      UNMANAGED_ADDRESS_THIS_RELATIVE addrThisRel;  
      UNMANAGED_ADDRESS_PHYSICAL      addrUPhysical;  
      METADATA_ADDRESS_METHOD         addrMethod;  
      METADATA_ADDRESS_FIELD          addrField;  
      METADATA_ADDRESS_LOCAL          addrLocal;  
      METADATA_ADDRESS_PARAM          addrParam;  
      METADATA_ADDRESS_ARRAYELEM      addrArrayElem;  
      METADATA_ADDRESS_RETVAL         addrRetVal;  
      DWORD                           unused;  
   } addr;  
} DEBUG_ADDRESS_UNION;  
```  
  
```c#  
public struct DEBUG_ADDRESS_UNION {  
   public ADDRESS_KIND dwKind;  
   public IntPtr       unionmember;  
}  
```  
  
## 詞彙  
 dwKind  
 介於[ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)列舉型別，指定如何解譯聯集。  
  
 addr.addrNative  
 \[只有 c \+ \+\]包含[NATIVE\_ADDRESS](../../../extensibility/debugger/reference/native-address.md)結構，如果`dwKind` \= ADDRESS\_KIND\_NATIVE。  
  
 addr.addrThisRel  
 \[只有 c \+ \+\]包含[UNMANAGED\_ADDRESS\_THIS\_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)結構，如果`dwKind` \= ADDRESS\_KIND\_UNMANAGED\_THIS\_RELATIVE。  
  
 addr.addUPhysical  
 \[只有 c \+ \+\]包含[UNMANAGED\_ADDRESS\_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)結構，如果`dwKind` \= ADDRESS\_KIND\_UNMANAGED\_PHYSICAL。  
  
 addr.addrMethod  
 \[只有 c \+ \+\]包含[METADATA\_ADDRESS\_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)結構，如果`dwKind` \= ADDRESS\_KIND\_METHOD。  
  
 addr.addrField  
 \[只有 c \+ \+\]包含[METADATA\_ADDRESS\_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)結構，如果`dwKind` \= ADDRESS\_KIND\_FIELD。  
  
 addr.addrLocal  
 \[只有 c \+ \+\]包含[METADATA\_ADDRESS\_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)結構，如果`dwKind` \= ADDRESS\_KIND\_LOCAL。  
  
 addr.addrParam  
 \[只有 c \+ \+\]包含[METADATA\_ADDRESS\_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)結構，如果`dwKind` \= ADDRESS\_KIND\_PARAM。  
  
 addr.addrArrayElem  
 \[只有 c \+ \+\]包含[METADATA\_ADDRESS\_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)結構，如果`dwKind` \= ADDRESS\_KIND\_ARRAYELEM。  
  
 addr.addrRetVal  
 \[只有 c \+ \+\]包含[METADATA\_ADDRESS\_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)結構，如果`dwKind` \= ADDRESS\_KIND\_RETVAL。  
  
 addr.unused  
 \[只有 c \+ \+\] 與邊框距離。  
  
 地址  
 \[只有 c \+ \+\]聯集的名稱。  
  
 unionmember  
 \[C\# 只\]這個值必須為基礎的適當的結構類型來封送處理`dwKind`。  如之間的關聯，請參閱 「 備註 」 `dwKind`和轉譯的聯集。  
  
## 備註  
 在這種結構屬於[DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)架構，表示其中一個為數種不同類型的地址 \( `DEBUG_ADDRESS`結構會填入由呼叫[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)方法\)。  
  
 \[C\# 只\]下表顯示如何解譯`unionmember`每一類型的地址的成員。  此範例顯示如何這麼做是一種地址。  
  
|`dwKind`|`unionmember`解譯為|  
|--------------|----------------------|  
|`ADDRESS_KIND_NATIVE`|[NATIVE\_ADDRESS](../../../extensibility/debugger/reference/native-address.md)|  
|`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`|[UNMANAGED\_ADDRESS\_THIS\_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)|  
|`ADDRESS_KIND_UNMANAGED_PHYSICAL`|[UNMANAGED\_ADDRESS\_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)|  
|`ADDRESS_KIND_METHOD`|[METADATA\_ADDRESS\_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)|  
|`ADDRESS_KIND_FIELD`|[METADATA\_ADDRESS\_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)|  
|`ADDRESS_KIND_LOCAL`|[METADATA\_ADDRESS\_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)|  
|`ADDRESS_KIND_PARAM`|[METADATA\_ADDRESS\_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)|  
|`ADDRESS_KIND_ARRAYELEM`|[METADATA\_ADDRESS\_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)|  
|`ADDRESS_KIND_RETVAL`|[METADATA\_ADDRESS\_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)|  
  
## 範例  
 這個範例會示範如何解譯其中一種地址 \(`METADATA_ADDRESS_ARRAYELEM`\) 的`DEBUG_ADDRESS_UNION` C\# 中的結構。  其餘的項目可以解譯方式完全相同。  
  
```c#  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(DEBUG_ADDRESS_UNION dau)  
        {  
            if (dau.dwKind == (uint)enum_ADDRESS_KIND.ADDRESS_KIND_METADATA_ARRAYELEM)  
            {  
                 METADATA_ADDRESS_ARRAYELEM arrayElem =  
                     (METADATA_ADDRESS_ARRAYELEM)Marshal.PtrToStructure(dau.unionmember,  
                                 typeof(METADATA_ADDRESS_ARRAYELEM));  
            }  
        }  
    }  
}  
```  
  
## 需求  
 標頭: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)