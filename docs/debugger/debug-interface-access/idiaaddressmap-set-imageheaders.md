---
title: IDiaAddressMap：： set_imageHeaders |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: ef17e1073c67ede75d075b18773129c287349c0d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745019"
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

在標頭資料的位元組數目。 必須是 `n*sizeof(IMAGE_SECTION_HEADER)`，其中 `n` 是可執行檔中的區段標頭數目。

 data[]

在要當做影像標頭使用之 `IMAGE_SECTION_HEADER` 結構的陣列。

 originalHeaders

在如果影像標頭來自新影像，請將設定為 `FALSE`，`TRUE` 在升級之前是否反映原始影像。 通常，這會設定為僅與[IDiaAddressMap：： set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)方法的呼叫組合在一起 `TRUE`。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 @No__t_0 結構會在 Winnt. h 中宣告，並代表可執行檔的影像區段標頭格式。

 相對虛擬位址計算取決於 `IMAGE_SECTION_HEADER` 值。 通常，DIA 會從程式資料庫（.pdb）檔案中抓取這些檔案。 如果遺漏這些值，DIA 就無法計算相對虛擬位址，而[IDiaAddressMap：： get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)方法會傳回 `FALSE`。 接著，用戶端必須呼叫[IDiaAddressMap：:P ut_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)方法，以便在從影像本身提供遺漏的影像標頭之後，啟用相對虛擬位址計算。

## <a name="see-also"></a>請參閱
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)
- [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)