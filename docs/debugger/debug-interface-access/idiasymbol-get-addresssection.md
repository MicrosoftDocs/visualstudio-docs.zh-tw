---
title: IDiaSymbol::get_addressSection | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressSection method
ms.assetid: fe80d479-3bb5-4f55-9b62-1bd58d0a60ce
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2d5f06658cb6d2faad13112813731208075460cb
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464356"
---
# <a name="idiasymbolget_addresssection"></a>IDiaSymbol::get_addressSection
抓取位址位置的區段部分。 當[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)設定為時，請使用 `LocIsStatic` 。

## <a name="syntax"></a>語法

```C++
HRESULT get_addressSection ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回位址位置的區段部分。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該屬性不適用於符號。

## <a name="remarks"></a>備註
 對於位於外部 DLL 中的靜態成員，這個方法所傳回的區段可能是0，因為這個方法會依賴取得成員的虛擬位址。 只有在使用指定 DLL 載入位址的非零參數呼叫[IDiaSession](../../debugger/debug-interface-access/idiasession.md)介面中的[IDiaSession：:p ut_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)方法時，虛擬位址才有效。

 若要取得位址的位移部分，請呼叫[IDiaSymbol：： get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)方法。

## <a name="requirements"></a>需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2。h|
|版本：|DIA SDK v7.0|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)