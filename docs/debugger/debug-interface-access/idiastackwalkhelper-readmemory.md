---
title: IDiaStackWalkHelper：： readMemory |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bc768db3f42f610a8efd30cea567e721929cb291
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464692"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
從記憶體中可執行檔的影像讀取資料區塊。

## <a name="syntax"></a>語法

```C++
HRESULT readMemory( 
   enum MemoryTypeEnum type,
   ULONGLONG           va,
   DWORD               cbData,
   DWORD*              pcbData,
   BYTE*               pbData
);
```

#### <a name="parameters"></a>參數
 `type`

在[MemoryTypeEnum 列舉](../../debugger/debug-interface-access/memorytypeenum.md)列舉中的值，指定要讀取的記憶體類型。

 va

在影像中要開始讀取的虛擬位址。

 `cbData`

在資料緩衝區的大小（以位元組為單位）。

 `pcbData`

脫銷傳回實際讀取的位元組數目。 如果 `pbData` 為 `NULL` ，則這是可用的資料位元組總數。

 `pbData`

[in、out]填入記憶體讀取的緩衝區。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [MemoryTypeEnum 列舉](../../debugger/debug-interface-access/memorytypeenum.md)