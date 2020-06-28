---
title: IDiaFrameData::get_relativeVirtualAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_relativeVirtualAddress method
ms.assetid: de070ef4-6c9d-43ca-911c-5245cbcb8dbe
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2f78fdb1769cf9ea4cbc9c22792fed890601b2fe
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467208"
---
# <a name="idiaframedataget_relativevirtualaddress"></a>IDiaFrameData::get_relativeVirtualAddress
抓取框架之程式碼的相對虛擬位址（RVA）。

## <a name="syntax"></a>語法

```C++
HRESULT get_relativeVirtualAddress ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回框架之程式碼的相對虛擬位址。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援此屬性，則傳回。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)