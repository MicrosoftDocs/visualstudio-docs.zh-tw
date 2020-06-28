---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1ff6b04322bca213d5eeddfbc0f7ea4b01bb9226
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465304"
---
# <a name="idiasourcefileget_checksum"></a>IDiaSourceFile::get_checksum
抓取總和檢查碼位元組。

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

脫銷傳回總和檢查碼位元組數。 這個參數不可以是 `NULL`。

 `data`

[in、out]填入總和檢查碼位元組的緩衝區。 如果此參數為 `NULL` ，則會傳回 `pcbData` 所需的位元組數目。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="remarks"></a>備註
 若要判斷用來產生總和檢查碼位元組的總和檢查碼演算法類型，請呼叫[IDiaSourceFile：： get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)方法。

 總和檢查碼通常是從來源檔案的影像產生，因此來源檔案中的變更會反映在總和檢查碼位元組的變更中。 如果總和檢查碼位元組與從檔案載入的影像產生的總和檢查碼不符，則應該將檔案視為已損毀或遭到篡改。

 一般總和檢查碼的大小絕不會超過32個位元組，但不會假設為總和檢查碼的大小上限。 將 `data` 參數設定為 `NULL` ，以取得抓取總和檢查碼所需的位元組數目。 然後配置適當大小的緩衝區，並使用新的緩衝區多次呼叫此方法。

## <a name="see-also"></a>另請參閱
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)