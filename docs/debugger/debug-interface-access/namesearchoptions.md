---
description: 指定符號和檔案名的搜尋選項。
title: NameSearchOptions |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bd074de0c44803a06d5399f2bd4dc1e3c43618a1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155345"
---
# <a name="namesearchoptions"></a>NameSearchOptions
指定符號和檔案名的搜尋選項。

## <a name="syntax"></a>Syntax

```C++
enum NameSearchOptions {
    nsNone,
    nsfCaseSensitive     = 0x1,
    nsfCaseInsensitive   = 0x2,
    nsfFNameExt          = 0x4,
    nsfRegularExpression = 0x8,
    nsfUndecoratedName   = 0x10,

// For backward compatibility:
    nsCaseSensitive           = nsfCaseSensitive,
    nsCaseInsensitive         = nsfCaseInsensitive,
    nsFNameExt                = nsfCaseInsensitive | nsfFNameExt,
    nsRegularExpression       = nsfRegularExpression | nsfCaseSensitive,
    nsCaseInRegularExpression = nsfRegularExpression | nsfCaseInsensitive
};
```

## <a name="elements"></a>元素
`nsNone`未指定任何選項。

`nsfCaseSensitive` 適用區分大小寫的名稱比對。

`nsfCaseInsensitive` 套用不區分大小寫的名稱比對。

`nsfFNameExt` 將名稱視為路徑，並套用副檔名名稱。

`nsfRegularExpression` 使用星號 ( * ) 和問號 (？ ) 為萬用字元，套用區分大小寫的名稱比對。 不支援 (其他常見的正則運算式字元。 ) 

`nsfUndecoratedName` 只適用于同時具有未修飾和裝飾名稱的符號。

## <a name="remarks"></a>備註
此列舉的值會傳遞至下列方法：

- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)

- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)

- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

## <a name="requirements"></a>規格需求
標頭： dia2。h

## <a name="see-also"></a>另請參閱
- [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
