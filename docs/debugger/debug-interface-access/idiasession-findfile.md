---
title: IDiaSession::findFile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFile method
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d9751127007b4e7823cf6d2ae35ed2fe80cb83b8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742285"
---
# <a name="idiasessionfindfile"></a>IDiaSession::findFile
依編譯模組和名稱來抓取原始程式檔。

## <a name="syntax"></a>語法

```C++
HRESULT findFile ( 
   IDiaSymbol*           pCompiland,
   LPCOLESTR             name,
   DWORD                 option,
   IDiaEnumSourceFiles** ppResult
);
```

#### <a name="parameters"></a>參數
 `pCompiland`

在[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件，代表要做為搜尋內容使用的編譯模組。 將此參數設定為 `NULL`，以在所有 compilands 中尋找原始檔。

 `name`

在指定要抓取之來源檔案的名稱。 將此參數設定為所有要抓取之來源檔案的 `NULL`。

 `option`

在指定套用至名稱搜尋的比較選項。 來自[NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)列舉的值可以單獨使用，或搭配使用。

 `ppResult`

脫銷傳回[IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)物件，其中包含所抓取之來源檔案的清單。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回錯誤碼。

## <a name="example"></a>範例

```C++
IDiaEnumSourceFiles* pEnum;
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );
```

## <a name="see-also"></a>請參閱
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)