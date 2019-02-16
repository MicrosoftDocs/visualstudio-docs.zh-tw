---
title: BUILT_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BUILT_TYPE
helpviewer_keywords:
- BUILT_TYPE structure
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 692391379c3f2581e535a9e5c885f776565fb93d
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315479"
---
# <a name="builttype"></a>BUILT_TYPE
此結構會指定取自中繼資料的欄位類型的相關資訊。

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
符號所來自的應用程式的識別碼。 這用來唯一識別應用程式的執行個體。

guidModule  
模組包含此欄位的 GUID。

pUnderlyingField  
[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件，可識別此內建欄位相關聯的基礎欄位。

## <a name="remarks"></a>備註
此結構會顯示為中的等位的一部分[TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)結構時`dwKind`欄位`TYPE_INFO`結構設定為`TYPE_KIND_BUILT`(值[dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)列舉型別）。

## <a name="requirements"></a>需求
標頭： sh.h

命名空間：Microsoft.VisualStudio.Debugger.Interop

組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
[結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)  
[TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)  
[dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)  
[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
