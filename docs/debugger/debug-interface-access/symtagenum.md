---
title: SymTagEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SymTagEnum enumeration
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 806fe878468baa06b52a15879ceaff1b376461e9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738507"
---
# <a name="symtagenum"></a>SymTagEnum
指定符號的類型。

## <a name="syntax"></a>語法

```C++
enum SymTagEnum {
    SymTagNull,
    SymTagExe,
    SymTagCompiland,
    SymTagCompilandDetails,
    SymTagCompilandEnv,
    SymTagFunction,
    SymTagBlock,
    SymTagData,
    SymTagAnnotation,
    SymTagLabel,
    SymTagPublicSymbol,
    SymTagUDT,
    SymTagEnum,
    SymTagFunctionType,
    SymTagPointerType,
    SymTagArrayType,
    SymTagBaseType,
    SymTagTypedef,
    SymTagBaseClass,
    SymTagFriend,
    SymTagFunctionArgType,
    SymTagFuncDebugStart,
    SymTagFuncDebugEnd,
    SymTagUsingNamespace,
    SymTagVTableShape,
    SymTagVTable,
    SymTagCustom,
    SymTagThunk,
    SymTagCustomType,
    SymTagManagedType,
    SymTagDimension,
    SymTagCallSite,
    SymTagInlineSite,
    SymTagBaseInterface,
    SymTagVectorType,
    SymTagMatrixType,
    SymTagHLSLType
};
```

## <a name="elements"></a>項目
`SymTagNull` 表示符號沒有類型。

`SymTagExe` 表示符號是 .exe 檔案。 每個符號存放區只能有一個 `SymTagExe` 符號。 它會當做全域範圍，而且沒有詞法父系。

`SymTagCompiland` 表示符號存放區之每個編譯模組元件的編譯模組符號。 對於原生應用程式，`SymTagCompiland` 符號會對應至連結至影像的物件檔案。 對於某些類型的 Microsoft 中繼語言（MSIL）影像，每個類別都有一個編譯模組。

`SymTagCompilandDetails` 表示符號包含編譯模組的擴充屬性。 抓取這些屬性可能需要載入編譯模組符號。

`SymTagCompilandEnv` 表示符號是針對編譯模組定義的環境字串。

`SymTagFunction` 表示符號為函式。

`SymTagBlock` 表示符號是一個嵌套區塊。

`SymTagData` 表示符號為 [資料]。

`SymTagAnnotation` 指出符號適用于程式碼批註。 這個符號的子系是常數資料字串（`SymTagData`、`LocIsConstant` `DataIsConstant`）。 大部分的用戶端都會忽略此符號。

`SymTagLabel` 表示符號是標籤。

`SymTagPublicSymbol` 表示符號為公用符號。 對於原生應用程式，這個符號是連結影像時遇到的 COFF 外部符號。

`SymTagUDT` 表示符號為使用者定義型別（結構、類別或等位）。

`SymTagEnum` 表示符號是列舉。

`SymTagFunctionType` 表示符號為函式簽章類型。

`SymTagPointerType` 表示符號是指標類型。

`SymTagArrayType` 表示符號為數組類型。

`SymTagBaseType` 表示符號是基底類型。

`SymTagTypedef` 表示符號為 `typedef`，也就是另一個類型的別名。

`SymTagBaseClass` 表示符號是使用者定義類型的基類。

`SymTagFriend` 表示符號為使用者定義類型的 friend。

`SymTagFunctionArgType` 表示符號為函式引數。

`SymTagFuncDebugStart` 表示符號為函式序言碼的結束位置。

`SymTagFuncDebugEnd` 表示符號是函式的結尾程式碼的開始位置。

`SymTagUsingNamespace` 表示符號為命名空間名稱，在目前的範圍中為作用中。

`SymTagVTableShape` 表示符號是虛擬資料表描述。

`SymTagVTable` 表示符號是虛擬資料表指標。

`SymTagCustom` 表示符號為自訂符號，而且 DIA 不會加以解讀。

`SymTagThunk` 表示符號是用來在16和32位程式碼之間共用資料的 Thunk。

`SymTagCustomType` 表示符號為自訂編譯器符號。

`SymTagManagedType` 表示符號在中繼資料中。

`SymTagDimension` 表示符號是一種 FORTRAN 多維陣列。

`SymTagCallSite` 表示符號代表呼叫位置。

`SymTagInlineSite` 表示符號代表內嵌網站。

`SymTagBaseInterface` 表示符號是基底介面。

`SymTagVectorType` 表示符號為向量類型。

`SymTagMatrixType` 表示符號為矩陣類型。

`SymTagHLSLType` 表示符號為高層級的著色器語言類型。

## <a name="remarks"></a>備註
偵錯工具檔案中的所有符號都具有指定符號類型的識別標記。

這個列舉中的值是由呼叫[IDiaSymbol：： get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)方法所傳回。

此列舉中的值會傳遞至下列方法，將搜尋範圍限制為特定符號類型：

- [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)

- [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)

- [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)

- [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)

- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)

- [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)

- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)

- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

## <a name="requirements"></a>需求
標頭： cvconst。h

## <a name="see-also"></a>請參閱
- [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [符號類型的語彙階層架構](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)
- [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)
- [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)
- [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)
- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)
- [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
