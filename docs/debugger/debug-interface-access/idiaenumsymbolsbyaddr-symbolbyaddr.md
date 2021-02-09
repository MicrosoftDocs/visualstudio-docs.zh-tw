---
title: IDiaEnumSymbolsByAddr::symbolByAddr | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::symbolByAddr method
ms.assetid: 0b6f5a68-8402-4f29-8219-20576fda8166
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9453cb9cd703fd22d9dcff0f1606449dd0fe2cac
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856059"
---
# <a name="idiaenumsymbolsbyaddrsymbolbyaddr"></a>IDiaEnumSymbolsByAddr::symbolByAddr
藉由依影像區段號和位移來執行查閱，以放置列舉值。

## <a name="syntax"></a>語法

```C++
HRESULT symbolByAddr ( 
   DWORD**      isect,
   DWORD**      offsect,
   IDiaSymbol** ppsymbol
);
```

#### <a name="parameters"></a>參數
 isect

在影像區段編號。

 offsect

在區段中的位移。

 ppsymbol

擴展傳回 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 物件，代表找到的符號。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果找不到符號，則會傳回。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)