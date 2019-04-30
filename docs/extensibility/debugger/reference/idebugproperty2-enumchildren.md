---
title: IDebugProperty2::EnumChildren | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::EnumChildren
helpviewer_keywords:
- IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1cfbce26a84254158f088e8744c14154aef7f61a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62869512"
---
# <a name="idebugproperty2enumchildren"></a>IDebugProperty2::EnumChildren
擷取屬性的子系清單。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumChildren ( 
   DEBUGPROP_INFO_FLAGS      dwFields,
   DWORD                     dwRadix,
   REFGUID                   guidFilter,
   DBG_ATTRIB_FLAGS          dwAttribFilter,
   LPCOLESTR                 pszNameFilter,
   DWORD                     dwTimeout,
   IEnumDebugPropertyInfo2** ppEnum
);
```

```csharp
int EnumChildren ( 
   enum_DEBUGPROP_INFO_FLAGS   dwFields,
   uint                        dwRadix,
   ref Guid                    guidFilter,
   uint                        dwAttribFilter,
   string                      pszNameFilter,
   uint                        dwTimeout,
   out IEnumDebugPropertyInfo2 ppEnum
);
```

#### <a name="parameters"></a>參數
 `dwFields`

 [in]從旗標的組合[DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)列舉，指定哪些欄位中列舉[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)結構要進行填寫。

 `dwRadix`

 [in]指定要用於格式化數字的任何資訊的基數。

 `guidFilter`

 [in]篩選器搭配使用的 GUID`dwAttribFilter`並`pszNameFilter`參數來選取哪一個`DEBUG_PROPERTY_INFO`子系是要列舉。 比方說，`guidFilterLocals`篩選條件的本機變數。

 `dwAttribFilter`

 [in]從旗標的組合[DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)列舉，指定要列舉，例如物件的類型`DBG_ATTRIB_METHOD`可能是這個屬性的子系的所有方法。 用於搭配`guidFilter`和`pszNameFilter`參數。

 `pszNameFilter`

 [in]搭配使用的篩選器名稱`guidFilter`並`dwAttribFilter`參數來選取哪一個`DEBUG_PROPERTY_INFO`子系是要列舉。 比方說，此參數設定為"MyX 」 篩選條件具有名稱"MyX。 」 的所有子系

 `dwTimeout`

 [in]指定的時間上限，以毫秒為單位，從這個方法返回之前等候。 使用`INFINITE`無限期等候。

 `ppEnum`

 [out]傳回[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)物件，其中包含的子屬性的清單。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)