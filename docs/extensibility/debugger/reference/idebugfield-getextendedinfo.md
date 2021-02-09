---
title: IDebugField：： GetExtendedInfo |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 911556cb615e373d620b496fb31e5d6093b7cc37
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869930"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
這個方法會取得有關欄位的延伸資訊。

## <a name="syntax"></a>語法

```cpp
HRESULT GetExtendedInfo( 
   REFGUID guidExtendedInfo,
   BYTE**  prgBuffer,
   DWORD*  pdwLen
);
```

```csharp
int GetExtendedInfo(
   ref Guid guidExtendedInfo,
   IntPtr[] prgBuffer,
   ref uint pdwLen
);
```

## <a name="parameters"></a>參數
`guidExtendedInfo`\
在選取要傳回的資訊。 有效值為：

|值|描述|
|-----------|-----------------|
|`guidConstantValue`|值，表示為位元組序列。|
|`guidConstantType`|類型簽章的類型。|

`prgBuffer`\
擴展傳回擴充的資訊。

`pdwLen`\
[in，out]傳回擴充資訊的大小（以位元組為單位）。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 目前，這個方法只會傳回常數的型別或值。 呼叫端必須釋放中傳回的緩衝區， `prgBuffer` 方法是呼叫 COM 的函式 `CoTaskMemFree` (c + +) 或 <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (c # ) 。

## <a name="see-also"></a>另請參閱
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
