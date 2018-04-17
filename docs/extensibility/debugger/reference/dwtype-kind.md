---
title: dwTYPE_KIND |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
caps.latest.revision: 8
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 97136c781fa0ba6b3eb79250a4ecbe0bd2e4e694
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="dwtypekind"></a>dwTYPE_KIND
指定如何解譯的型別[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
  
typedef DWORD dwTYPE_KIND;  
```  
  
```csharp  
public enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
```  
  
#### <a name="parameters"></a>參數  
 TYPE_KIND_METADATA  
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)聯集應該解譯為[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)結構。  
  
 TYPE_KIND_PDB  
 `TYPE_INFO`聯集應該解譯為[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)結構。  
  
 TYPE_KIND_BUILT  
 `TYPE_INFO`聯集應該解譯為[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)結構。  
  
## <a name="remarks"></a>備註  
 這個列舉值會出現在`dwKind`欄位[TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)架構，用來決定如何解譯`type`等位成員。 `TYPE_INFO`結構由呼叫[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： sh.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)