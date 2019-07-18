---
title: 'Idiasymbol:: Get_objectpointertype |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_objectPointerType method
ms.assetid: bce193b9-67b0-4c35-96e5-6a664937322e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 69dac79a040a8eff68c36c82b9a85935d969b5ec
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "64808911"
---
# <a name="idiasymbolgetobjectpointertype"></a>IDiaSymbol::get_objectPointerType
擷取類別方法的物件指標的類型。

## <a name="syntax"></a>語法

```C++
HRESULT get_objectPointerType ( 
   IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

[out]傳回[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件，表示類別方法的物件指標。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。

> [!NOTE]
> 傳回值為`S_FALSE`表示此屬性不適用於符號。

## <a name="remarks"></a>備註
 這個屬性只適用於具有符號[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)種`SymTagFunctionType`。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)