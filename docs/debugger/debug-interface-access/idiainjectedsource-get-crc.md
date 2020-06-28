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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b67072fe2928556d355aac2e65cf5d011873edd9
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467124"
---
# <a name="idiainjectedsourceget_crc"></a>IDiaInjectedSource::get_crc
從原始程式碼的位元組，抓取計算的迴圈冗余檢查（CRC）。

## <a name="syntax"></a>語法

```C++
HRESULT get_crc ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回從原始程式碼的位元組計算出來的 CRC。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援此屬性，則傳回。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)