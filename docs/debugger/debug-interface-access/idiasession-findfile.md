---
description: 依編譯單位和名稱抓取原始程式檔。
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: af547f9e504e9d832968bd18a370cb43e816e786
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159003"
---
# <a name="idiasessionfindfile"></a>IDiaSession::findFile
依編譯單位和名稱抓取原始程式檔。

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

在 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 物件，代表要當做搜尋內容使用的編譯單位。 將此參數設定為， `NULL` 以在所有 compilands 中尋找原始檔。

 `name`

在指定要取出的原始程式檔名稱。 `NULL`針對要取出的所有來源檔案，將此參數設定為。

 `option`

在指定套用至名稱搜尋的比較選項。 [NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)列舉中的值可以單獨使用或合併使用。

 `ppResult`

擴展傳回 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) 物件，其中包含已抓取的原始程式檔清單。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

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
