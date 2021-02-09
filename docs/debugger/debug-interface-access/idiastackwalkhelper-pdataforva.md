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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d150e777f657fcf63dc66dbe3e686c1b445dd473
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863806"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
傳回與虛擬位址相關聯的 .PDATA 資料區塊。

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

在要取得之資料的大小（以位元組為單位）。

 `pcbData`

擴展傳回取得的實際資料大小（以位元組為單位）。

 `pbData`

[in，out]填入所要求資料的緩衝區。 不可以是 `NULL`。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果指定的位址沒有 .pdata，則會傳回。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 .PDATA (名為 ". .pdata" 的區段 ) 的編譯單位包含函式例外狀況處理的相關資訊。

 呼叫端知道要傳回多少資料，讓呼叫端不需要要求有多少資料可供使用。 因此，如果參數為，則此方法的執行可接受傳回錯誤 `pbData` `NULL` 。

## <a name="see-also"></a>另請參閱
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)