---
title: IDiaSession::findAcceleratorInlineesByName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: abd6f8afb7275503fa3de855575e9dcb6dad0fb3
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465843"
---
# <a name="idiasessionfindacceleratorinlineesbyname"></a>IDiaSession::findAcceleratorInlineesByName
針對對應至指定之內嵌函數名稱的內嵌框架，傳回符號的列舉。

## <a name="syntax"></a>語法

```C++
HRESULT findAcceleratorInlineeLinesByName ( 
   LPCOLESTR             name,
   DWORD                 option,
   IDiaEnumSymbols**     ppResult
);
```

#### <a name="parameters"></a>參數
 `name`

在要搜尋的內嵌項函數名稱。

 `option`

在搜尋對應于的內嵌框架時，所要使用的名稱搜尋選項 `name` 。 如需詳細資訊，請參閱[NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)。

 `ppResult`

脫銷以 `IDiaEnumSymbols` 結果初始化之介面指標的指標。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="remarks"></a>備註
 此函式只會在快速鍵 stub 函數中搜尋 inlinees。 它會忽略原生 c + + 程式記錄。

## <a name="see-also"></a>另請參閱
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)