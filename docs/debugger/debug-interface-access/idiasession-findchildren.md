---
title: IDiaSession::findChildren | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: cca6778e5697c5f8821322c19d706d733d7f2b9f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742293"
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

在代表父系的[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件。 如果這個父符號是函式、模組或區塊，則會在 `ppResult` 中傳回其詞法子系。 如果父符號為類型，則會傳回其類別子系。 如果此參數為 `NULL`，則 `symtag` 必須設定為 `SymTagExe` 或 `SymTagNull`，以傳回全域範圍（.exe 檔案）。

 `symtag`

在指定要抓取之子系的符號標記。 值取自[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)列舉。 設定為 `SymTagNull` 以取得所有子系。

 `name`

在指定要抓取之子系的名稱。 針對要抓取的所有子系，設定為 `NULL`。

 `compareFlags`

在指定套用至名稱比對的比較選項。 來自[NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)列舉的值可以單獨使用，或搭配使用。

 `ppResult`

脫銷傳回[IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)物件，其中包含所抓取之子符號的清單。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回錯誤碼。

## <a name="example"></a>範例
 下列範例顯示如何尋找符合名稱 `szVarName` 之函式 `pFunc` 的區域變數。

```C++
IDiaEnumSymbols* pEnum;
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );
```

## <a name="see-also"></a>請參閱
- [概觀](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)
- [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)