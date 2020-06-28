---
title: IDiaAddressMap：： set_imageHeaders |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ded09d64a071c12e14de1597c21aad3872cacf4
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468543"
---
# <a name="idiaaddressmapset_imageheaders"></a>IDiaAddressMap::set_imageHeaders
設定影像標頭以啟用相對虛擬位址轉譯。

## <a name="syntax"></a>語法

```C++
HRESULT set_imageHeaders ( 
   DWORD cbData,
   BYTE  data[],
   BOOL  originalHeaders
);
```

#### <a name="parameters"></a>參數
 cbData

在標頭資料的位元組數目。 必須是 `n*sizeof(IMAGE_SECTION_HEADER)` `n` 可執行檔的區段標頭數目。

 data[]

在`IMAGE_SECTION_HEADER`要當做影像標頭使用的結構陣列。

 originalHeaders

在如果 `FALSE` 影像標頭來自新影像，則設定為， `TRUE` 如果它們在升級前反映原始影像則為。 通常，這會設定為 `TRUE` 僅與[IDiaAddressMap：： set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)方法的呼叫結合。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="remarks"></a>備註
 `IMAGE_SECTION_HEADER`結構會在 Winnt. h 中宣告，並代表可執行檔的影像區段標頭格式。

 相對虛擬位址計算須視值而定 `IMAGE_SECTION_HEADER` 。 通常，DIA 會從程式資料庫（.pdb）檔案中抓取這些檔案。 如果遺漏這些值，DIA 就無法計算相對虛擬位址，而[IDiaAddressMap：： get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)方法會傳回 `FALSE` 。 接著，用戶端必須呼叫[IDiaAddressMap：:p ut_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)方法，以便在從影像本身提供遺漏的影像標頭之後，啟用相對虛擬位址計算。

## <a name="see-also"></a>另請參閱
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)
- [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)