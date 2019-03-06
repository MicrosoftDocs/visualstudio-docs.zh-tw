---
title: DEBUG_REFERENCE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REFERENCE_INFO
helpviewer_keywords:
- DEBUG_REFERENCE_INFO structure
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c82e1d3894b9fa3ffbdffb5ab69c134ff73e0df7
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56720285"
---
# <a name="debugreferenceinfo"></a>DEBUG_REFERENCE_INFO
描述的參考。

## <a name="syntax"></a>語法

```cpp
typedef struct tagDEBUG_REFERENCE_INFO {
    DEBUGREF_INFO_FLAGS dwFields;
    BSTR                bstrName;
    BSTR                bstrType;
    BSTR                bstrValue;
    DBG_ATTRIB_FLAGS    dwAttrib;
    REFERENCE_TYPE.     dwRefType;
    IDebugReference2*   m_pReference;
} DEBUG_REFERENCE_INFO;
```

```csharp
public struct DEBUG_REFERENCE_INFO {
    public uint             dwFields;
    public string           bstrName;
    public string           bstrType;
    public string           bstrValue;
    public ulong            dwAttrib;
    public uint.            dwRefType;
    public IDebugReference2 m_pReference;
};
```

## <a name="members"></a>成員
dwFields A 中的旗標的組合[DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)列舉，指定哪些欄位都已填寫。

名稱的使用者指定 bstrName [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)物件。

以格式化的字串方式輸入 bstrType 參考。

bstrValue 格式化字串的參考值

dwAttrib A 中的旗標的組合[DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)指定偵錯屬性的屬性旗標的列舉型別。

dwRefType 的值從[REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)列舉，指定參考型別是否為強式或弱式。

m_pReference [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)物件，指定的參考資訊。

## <a name="remarks"></a>備註
此結構會傳遞至呼叫[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)来填入的方法。 此結構也會傳回從清單的一部分[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)介面，反而會從呼叫傳回[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)方法。

## <a name="requirements"></a>需求
標頭： msdbg.h

命名空間：Microsoft.VisualStudio.Debugger.Interop

組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
