---
description: 捕獲總和檢查碼位元組。
title: IDiaSourceFile::get_checksum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8aac5b35c98b8bb5b11bc623a274949ee32d9229
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147594"
---
# <a name="idiasourcefileget_checksum"></a>IDiaSourceFile::get_checksum
捕獲總和檢查碼位元組。

## <a name="syntax"></a>語法

```C++
HRESULT get_checksum ( 
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>參數
 `cbData`

在資料緩衝區的大小（以位元組為單位）。

 `pcbData`

擴展傳回總和檢查碼位元組數目。 這個參數不可以是 `NULL`。

 `data`

[in，out]填滿總和檢查碼位元組的緩衝區。 如果這個參數是 `NULL` ，則會傳回 `pcbData` 所需的位元組數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 若要判斷用來產生總和檢查碼位元組的總和檢查碼演算法類型，請呼叫 [IDiaSourceFile：： get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) 方法。

 總和檢查碼通常是從原始程式檔的影像產生，因此原始程式檔中的變更會反映在總和檢查碼位元組的變更中。 如果總和檢查碼位元組不符合從載入的檔案影像產生的總和檢查碼，則應該將檔案視為損毀或遭篡改。

 一般總和檢查碼的大小絕對不會超過32個位元組，但不會假設這是總和檢查碼的大小上限。 將 `data` 參數設定為， `NULL` 以取得取出總和檢查碼所需的位元組數目。 然後，配置適當大小的緩衝區，然後再使用新的緩衝區呼叫這個方法一次。

## <a name="see-also"></a>另請參閱
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)
