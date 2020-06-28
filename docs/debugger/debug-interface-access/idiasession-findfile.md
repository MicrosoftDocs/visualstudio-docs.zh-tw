---
title: IDiaSession::findFile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 2ba8422ed2be8f06ac64fb9c7fa81c5b1b3c3f3c
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465822"
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

在[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件，代表要做為搜尋內容使用的編譯模組。 將此參數設定為 `NULL` ，即可在所有 compilands 中尋找原始檔。

 `name`

在指定要抓取之來源檔案的名稱。 將此參數設定為，以 `NULL` 取得所有原始程式檔的抓取。

 `option`

在指定套用至名稱搜尋的比較選項。 來自[NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)列舉的值可以單獨使用，或搭配使用。

 `ppResult`

脫銷傳回[IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)物件，其中包含所抓取之來源檔案的清單。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="example"></a>範例

```C++
IDiaEnumSourceFiles* pEnum;
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );
```

## <a name="see-also"></a>另請參閱
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)