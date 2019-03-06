---
title: 'Idiasymbol:: Findchildren |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildren method
ms.assetid: 5fe7573a-e48b-428d-9c17-7421b7209246
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5199be7307fdaa607f5aa6a5f554d9fcc82f452d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56623147"
---
# <a name="idiasymbolfindchildren"></a>IDiaSymbol::findChildren
擷取之符號的子系。

## <a name="syntax"></a>語法

```C++
HRESULT findChildren ( 
   enum SymTagEnum   symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>參數
 `symtag`

[in]指定要擷取的子系的符號標記中定義[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)。 若要設定`SymTagNull`要擷取的所有子系。

 `name`

[in]指定要擷取的子系的名稱。 若要設定`NULL`要擷取的所有子系。

 `compareFlags`

[in]指定比較選項套用至對應的名稱。 從數值[NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)單獨或合併，就可以使用列舉型別。

 `ppResult`

[out]傳回[IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)擷取物件，其中包含一份子符號。

## <a name="return-value"></a>傳回值
 會傳回`S_OK`如果找不到，至少一個子系的符號，或是傳回`S_FALSE`如果找不到任何子系; 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法相當於呼叫[idiasession:: Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)完成這個符號的第一個參數的方法。

## <a name="see-also"></a>請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)