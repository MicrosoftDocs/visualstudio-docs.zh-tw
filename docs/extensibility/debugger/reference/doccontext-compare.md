---
title: "DOCCONTEXT_COMPARE |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 77c810bb6e4791fbc0c3cf787f340a8d996ce037
ms.contentlocale: zh-tw
ms.lasthandoff: 09/26/2017

---
# <a name="doccontextcompare"></a>DOCCONTEXT_COMPARE
指定的準則來比較兩個文件內容。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
typedef DWORD DOCCONTEXT_COMPARE;  
```  
  
```csharp  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
```  
  
## <a name="members"></a>成員  
 DOCCONTEXT_EQUAL  
 等於目標文件內容的清單中找到的第一個文件內容。  
  
 DOCCONTEXT_LESS_THAN  
 小於目標文件內容的清單中找到的第一個文件內容。  
  
 DOCCONTEXT_GREATER_THAN  
 大於目標文件內容的清單中找到的第一個文件內容。  
  
 DOCCONTEXT_SAME_DOCUMENT  
 在相同的文件為目標的文件內容中的清單中找到的第一個文件內容。  
  
## <a name="remarks"></a>備註  
 做為引數傳遞[比較](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)方法。  
  
 這些值可用來指定在清單中尋找第一個文件內容比較準則。 文件內容有一份文件內容來比較本身針對透過`IDebugDocumentContext2::Compare`方法。 比較運算子的清單中的第一個文件內容`true`再傳回。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)
