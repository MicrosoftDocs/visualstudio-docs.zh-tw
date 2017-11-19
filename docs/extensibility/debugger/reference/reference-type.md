---
title: "REFERENCE_TYPE |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: REFERENCE_TYPE
helpviewer_keywords: REFERENCE_TYPE enumeration
ms.assetid: b1ffba10-eb9d-48ba-bf48-6d8b71d6f270
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7c5616cea578339f1527a73d03e9d6cb208ec6ad
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="referencetype"></a>REFERENCE_TYPE
指定的參考類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_REFERENCE_TYPE {   
   REF_TYPE_WEAK   = 0x0001,  
   REF_TYPE_STRONG = 0x0002  
};  
typedef DWORD REFERENCE_TYPE;  
```  
  
```csharp  
public enum enum_REFERENCE_TYPE {   
   REF_TYPE_WEAK   = 0x0001,  
   REF_TYPE_STRONG = 0x0002  
};  
```  
  
## <a name="members"></a>成員  
 REF_TYPE_WEAK  
 指定的弱式參考。 無法結合`REF_TYPE_STRONG`。  
  
 REF_TYPE_STRONG  
 指定強式參考。 無法結合`REF_TYPE_WEAK`。  
  
## <a name="remarks"></a>備註  
 做為`dwRefType`隸屬[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)結構。  
  
 做為參數來傳遞[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)