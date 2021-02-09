---
title: IDiaInjectedSource::get_crc | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_crc method
ms.assetid: 2ecdda93-950e-40d6-b79b-4ae3c55b6cfc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e346352d802404beca57054ab649366035baa908
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864835"
---
# <a name="idiainjectedsourceget_crc"></a>IDiaInjectedSource::get_crc
抓取迴圈冗余檢查 (CRC) 從原始程式碼的位元組計算。

## <a name="syntax"></a>語法

```C++
HRESULT get_crc ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展傳回從原始程式碼位元組算出的 CRC。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援這個屬性，則傳回。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)