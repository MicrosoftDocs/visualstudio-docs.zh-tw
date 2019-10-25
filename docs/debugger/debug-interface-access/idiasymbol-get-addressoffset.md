---
title: IDiaSymbol::get_addressOffset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressOffset method
ms.assetid: c15639b0-7f37-46c7-891b-40273b7f6319
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9290173fc9dcfdc07c7c0afbb33c741fe3e53f6c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741082"
---
# <a name="idiasymbolget_addressoffset"></a>IDiaSymbol::get_addressOffset
抓取位址位置的位移部分。 當[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)設定為 `LocIsStatic` 時使用。

## <a name="syntax"></a>語法

```C++
HRESULT get_addressOffset ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回位址位置的位移部分。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回 `S_FALSE` 或錯誤碼。

> [!NOTE]
> @No__t_0 的傳回值表示該屬性不適用於符號。

## <a name="remarks"></a>備註
 對於位於外部 DLL 中的靜態成員，這個方法所傳回的位移可能是0，因為這個方法會依賴取得成員的虛擬位址。 只有在使用指定 DLL 載入位址的非零參數呼叫[IDiaSession](../../debugger/debug-interface-access/idiasession.md)介面中的[IDiaSession：:p ut_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)方法時，虛擬位址才有效。

 若要取得位址的區段部分，請呼叫[IDiaSymbol：： get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)方法。

## <a name="requirements"></a>需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2。h|
|版本:|DIA SDK v7.0|

## <a name="see-also"></a>請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)
- [IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)
- [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)