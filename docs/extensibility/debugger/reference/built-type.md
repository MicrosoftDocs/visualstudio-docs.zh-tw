---
title: BUILT_TYPE |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BUILT_TYPE
helpviewer_keywords:
- BUILT_TYPE structure
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
caps.latest.revision: 7
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 34a426853952325f2d1911b7fca55a8f94a6d40f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="builttype"></a>BUILT_TYPE
此結構會指定從中繼資料的欄位類型的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _tagTYPE_BUILT {  
   ULONG32      ulAppDomainID;  
   GUID         guidModule;  
   IDebugField* pUnderlyingField;  
} BUILT_TYPE;  
```  
  
```csharp  
public struct BUILT_TYPE {  
   public uint        ulAppDomainID;  
   public Guid        guidModule;  
   public IDebugField pUnderlyingField;  
};  
```  
  
#### <a name="parameters"></a>參數  
 ulAppDomainID  
 應用程式的來源符號的識別碼。 這用來唯一識別應用程式的執行個體。  
  
 guidModule  
 包含此欄位之模組的 GUID。  
  
 pUnderlyingField  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件，可識別此內建欄位相關聯的基礎欄位。  
  
## <a name="remarks"></a>備註  
 此結構會顯示過程中的等位[TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)結構時`dwKind`欄位`TYPE_INFO`結構設為`TYPE_KIND_BUILT`(介於[dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)列舉型別）。  
  
## <a name="requirements"></a>需求  
 標頭： sh.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)