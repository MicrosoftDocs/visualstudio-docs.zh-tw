---
title: IEEData儲存:獲取數據 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62a1295aeb2a6afad51dee0f1015e3ab01d13fbb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718205"
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
從物件檢索指定數量的位元組。

## <a name="syntax"></a>語法

```cpp
HRESULT GetData(
   ULONG  dataSize,
   ULONG* sizeGotten,
   BYTE*  data
);
```

```csharp
int GetData(
   uint     dataSize,
   out uint sizeGotten,
   byte[]   data
);
```

## <a name="parameters"></a>參數
`dataSize`\
[在]要檢查的位元組數(`data`陣列必須至少保留此位元) 。

`sizeGotten`\
[出]返回實際檢索的位元組數。

`data`\
[進出]要用請求的數據填充的陣列。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 此方法的建議用途是檢索到本地陣列中的所有數據位元組,因為在檢索過程中無法跳過位元組。 在這種情況下,參數`dataSize`應該是[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)方法返回的值。

## <a name="see-also"></a>另請參閱
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)
