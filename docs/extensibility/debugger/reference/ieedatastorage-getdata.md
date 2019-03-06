---
title: IEEDataStorage::GetData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b6dbf712fc21338f8f5c4699ca2e11d5344dbad
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56693746"
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
從物件擷取指定的位元組數目。

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

#### <a name="parameters"></a>參數
 `dataSize`

 [in]要擷取的位元組數目 (`data`陣列必須具有至少下列數量之位元組為單位)。

 `sizeGotten`

 [out]傳回實際擷取的位元組的數目。

 `data`

 [in、 out]要求的資料填入的陣列。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 建議的使用這個方法是在本機的陣列，擷取資料的所有位元組，因為沒有任何方法可略過的擷取程序中的位元組。 在此情況下，參數`dataSize`應該所傳回的值[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)方法。

## <a name="see-also"></a>另請參閱
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)