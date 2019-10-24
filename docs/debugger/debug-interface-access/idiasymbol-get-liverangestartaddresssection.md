---
title: IDiaSymbol::get_liveRangeStartAddressSection | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeStartAddressSection
ms.assetid: 892b80ff-5957-4233-b4d7-6144167be289
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a23f0661d8af6417d754fd7a71c66c5dd3ef1135
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739898"
---
# <a name="idiasymbolget_liverangestartaddresssection"></a>IDiaSymbol::get_liveRangeStartAddressSection
傳回區域符號有效範圍之起始位址的區段部分。

## <a name="syntax"></a>語法

```C++
HRESULT get_liveRangeStartAddressSection ( 
   DWORD* section
);
```

#### <a name="parameters"></a>參數
 `section`

脫銷傳回起始位址範圍的區段部分。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回錯誤碼。

> [!NOTE]
> 傳回的錯誤碼表示符號沒有即時範圍資訊。

## <a name="remarks"></a>備註
 區段和位移所形成的位址是符號有效範圍的開頭。

 若要取得位址的位移部分，請使用[IDiaSymbol：： get_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md)。

## <a name="requirements"></a>需求
 標頭： Dia2。h

 程式庫： diaguids

 DLL： msdia100

## <a name="see-also"></a>請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)