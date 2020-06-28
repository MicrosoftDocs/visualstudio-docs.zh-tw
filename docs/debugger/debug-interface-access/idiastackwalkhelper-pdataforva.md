---
title: IDiaStackWalkHelper::pdataForVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d6e9b3e812311ef3d9555584d72ebb966098232a
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464706"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
傳回與虛擬位址相關聯的 PDATA 資料區塊。

## <a name="syntax"></a>語法

```C++
HRESULT pdataForVA( 
   ULONGLONG  va,
   DWORD      cbData,
   DWORD*     pcbData,
   BYTE*      pbData
);
```

#### <a name="parameters"></a>參數
 `va`

在指定要取得之資料的虛擬位址。

 `cbData`

在要取得的資料大小（以位元組為單位）。

 `pcbData`

脫銷傳回取得的實際資料大小（以位元組為單位）。

 `pbData`

[in、out]以要求的資料填入的緩衝區。 不可以是 `NULL`。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 如果指定的位址沒有 PDATA，則傳回 `S_FALSE` 。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 編譯模組的 PDATA （名為 ". PDATA" 的區段）包含函式例外狀況處理的相關資訊。

 呼叫者知道要傳回多少資料，讓呼叫端不需要詢問有多少資料可用。 因此，如果參數為，則可接受此方法的實作為傳回錯誤 `pbData` `NULL` 。

## <a name="see-also"></a>另請參閱
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)