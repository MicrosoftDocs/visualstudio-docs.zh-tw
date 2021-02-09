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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8ed505938636c9cccb69a927cdafbcb9589b35bc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863799"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
從記憶體中的可執行檔映射讀取資料區塊。

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

在 [MemoryTypeEnum 列舉](../../debugger/debug-interface-access/memorytypeenum.md) 列舉中的值，指定要讀取的記憶體類型。

 va

在映射中要開始讀取的虛擬位址。

 `cbData`

在資料緩衝區的大小（以位元組為單位）。

 `pcbData`

擴展傳回實際讀取的位元組數目。 如果 `pbData` 為 `NULL` ，則表示可用的資料位元組總數。

 `pbData`

[in，out]填入記憶體讀取的緩衝區。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [MemoryTypeEnum 列舉](../../debugger/debug-interface-access/memorytypeenum.md)