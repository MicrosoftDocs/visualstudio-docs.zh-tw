---
description: 傳回此物件中包含的位元組數目。
title: IEEDataStorage：： GetSize |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetSize
helpviewer_keywords:
- IEEDataStorage::GetSize
ms.assetid: 33d232c4-1239-4abc-922b-e1bc5b908169
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 46051ae73859213b3206e27fb83d40c0561d0c0b
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222922"
---
# <a name="ieedatastoragegetsize"></a>IEEDataStorage::GetSize
傳回此物件中包含的位元組數目。

## <a name="syntax"></a>語法

```cpp
HRESULT GetSize(
   ULONG* size
);
```

```csharp
int GetSize(
   out uint size
);
```

## <a name="parameters"></a>參數
`size`\
擴展此物件中包含的位元組數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 您可以 [使用 [已](../../../extensibility/debugger/reference/ieedatastorage-getdata.md) 執行] 方法來取出實際的資料位元組。

## <a name="see-also"></a>另請參閱
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)
