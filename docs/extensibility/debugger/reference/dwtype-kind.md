---
title: dwTYPE_KIND |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5eaa1b9edc128b5e13641bb5b38296fd96740ab4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109639"
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
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)