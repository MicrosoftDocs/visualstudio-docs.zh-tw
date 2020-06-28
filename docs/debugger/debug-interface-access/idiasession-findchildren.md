---
title: IDiaSession::findChildren | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findChildren method
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dcc62ed0b4a1f0a9ddd43ef692f748db4d9b6f10
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465836"
---
# <a name="idiasessionfindchildren"></a>IDiaSession::findChildren
抓取符合名稱和符號類型之指定父系識別碼的所有子系。

## <a name="syntax"></a>語法

```C++
HRESULT findChildren ( 
   IDiaSymbol*       parent,
   SymTagEnum        symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>參數
 `parent`

在代表父系的[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件。 如果這個父符號是函式、模組或區塊，則會在中傳回其詞法子系 `ppResult` 。 如果父符號為類型，則會傳回其類別子系。 如果此參數為 `NULL` ，則 `symtag` 必須將設定為 `SymTagExe` 或 `SymTagNull` ，這會傳回全域範圍（.exe 檔案）。

 `symtag`

在指定要抓取之子系的符號標記。 值取自[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)列舉。 將設定為 `SymTagNull` 以取出所有子系。

 `name`

在指定要抓取之子系的名稱。 `NULL`針對要抓取的所有子系，將設為。

 `compareFlags`

在指定套用至名稱比對的比較選項。 來自[NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)列舉的值可以單獨使用，或搭配使用。

 `ppResult`

脫銷傳回[IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)物件，其中包含所抓取之子符號的清單。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="example"></a>範例
 下列範例顯示如何尋找符合名稱之函式的區域變數 `pFunc` `szVarName` 。

```C++
IDiaEnumSymbols* pEnum;
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );
```

## <a name="see-also"></a>另請參閱
- [概觀](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)
- [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)