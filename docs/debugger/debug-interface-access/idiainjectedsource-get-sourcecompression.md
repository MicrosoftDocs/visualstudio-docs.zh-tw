---
title: IDiaInjectedSource：： get_sourceCompression |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_sourceCompression method
ms.assetid: 854b142f-23a9-466c-bf7f-98e581d5abcd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 480a0949cd1d42c60b05c5efc89f42c3457ab602
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855778"
---
# <a name="idiainjectedsourceget_sourcecompression"></a>IDiaInjectedSource::get_sourceCompression
抓取所使用的來源壓縮指標。

## <a name="syntax"></a>語法

```C++
HRESULT get_sourceCompression ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展傳回使用的來源壓縮指標。 值為零表示未使用任何來源壓縮。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援這個屬性，則傳回。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法所傳回的值是所使用之編譯器的特定值。 例如，編譯器可能會使用 Run-Length 編碼或 Huffman 樣式壓縮。

## <a name="see-also"></a>另請參閱
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)