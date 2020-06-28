---
title: IDiaSegment::get_relativeVirtualAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment::get_relativeVirtualAddress method
ms.assetid: b6a573a1-3671-4c1c-a5c2-2ab8f07fd510
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b01b0acfae5c08c8e638e403634fae1f68e2086
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465948"
---
# <a name="idiasegmentget_relativevirtualaddress"></a>IDiaSegment::get_relativeVirtualAddress
抓取區段開頭的相對虛擬位址（RVA）。

## <a name="syntax"></a>語法

```C++
HRESULT get_relativeVirtualAddress ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回區段開頭的 RVA。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援此屬性，則傳回。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)