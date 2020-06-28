---
title: IDiaSymbol：： get_relativeVirtualAddress |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_relativeVirtualAddress method
ms.assetid: e37219e3-c021-4057-9ec8-4f7cf3c13a15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3e7ff0b8a9227cd05086f84e5db1a569fb2ffb2f
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85462452"
---
# <a name="idiasymbolget_relativevirtualaddress"></a>IDiaSymbol::get_relativeVirtualAddress
抓取位置的相對虛擬位址（RVA）。 當[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)設定為時，請使用 `LocIsStatic` 。

## <a name="syntax"></a>語法

```C++
HRESULT get_relativeVirtualAddress ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回位置的相對虛擬位址。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示此屬性無法用於符號。

## <a name="example"></a>範例

```C++
IDiaSymbol* pSymbol;
DWORD       rva;
pSymbol->get_relativeVirtualAddress( &rva );
```

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)