---
description: 指定符號的類型。
title: SymTagEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- SymTagEnum enumeration
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 72d07b0609fd9d66507c898854810043f2911e0c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161603"
---
# <a name="symtagenum"></a>SymTagEnum
指定符號的類型。

## <a name="syntax"></a>Syntax

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

## <a name="elements"></a>元素
`SymTagNull` 指出符號沒有類型。

`SymTagExe` 指出符號是 .exe 檔案。 `SymTagExe`每個符號存放區只有一個符號。 它可做為全域範圍，且沒有詞法父代。

`SymTagCompiland` 表示符號存放區之每個編譯單位元件的編譯單位符號。 若為原生應用程式， `SymTagCompiland` 符號會對應至連結至影像的物件檔案。 針對某些類型的 Microsoft 中繼語言 (MSIL) 的影像，每個類別都有一個編譯單位。

`SymTagCompilandDetails` 指出符號包含編譯單位的擴充屬性。 抓取這些屬性可能需要載入編譯單位符號。

`SymTagCompilandEnv` 指出此符號是為編譯單位定義的環境字串。

`SymTagFunction` 指出符號為函式。

`SymTagBlock` 指出符號是嵌套區塊。

`SymTagData` 指出符號為數據。

`SymTagAnnotation` 指出符號適用于程式碼注釋。 此符號的子系是常數資料字串 `SymTagData` ， (、 `LocIsConstant` `DataIsConstant`) 。 大部分的用戶端會忽略此符號。

`SymTagLabel` 指出符號是標籤。

`SymTagPublicSymbol` 指出符號為公用符號。 若為原生應用程式，此符號是連結影像時所遇到的 COFF 外部符號。

`SymTagUDT` 指出符號是使用者定義型別 (結構、類別或等位) 。

`SymTagEnum` 指出符號為列舉。

`SymTagFunctionType` 指出符號為函式簽章類型。

`SymTagPointerType` 指出符號是指標類型。

`SymTagArrayType` 指出符號為數組類型。

`SymTagBaseType` 指出符號是基底類型。

`SymTagTypedef` 指出符號為 `typedef` ，也就是另一種類型的別名。

`SymTagBaseClass` 指出符號是使用者定義型別的基類。

`SymTagFriend` 指出符號是使用者定義型別的 friend。

`SymTagFunctionArgType` 指出符號為函式引數。

`SymTagFuncDebugStart` 指出符號是函式序言碼的結束位置。

`SymTagFuncDebugEnd` 指出符號為函式結尾程式碼的開始位置。

`SymTagUsingNamespace` 指出符號是命名空間名稱，在目前的範圍中為作用中。

`SymTagVTableShape` 指出此符號為虛擬資料表描述。

`SymTagVTable` 指出此符號為虛擬資料表指標。

`SymTagCustom` 指出符號是自訂符號，而且不是由 DIA 所解讀。

`SymTagThunk` 指出符號是可用於在16和32位程式碼之間共用資料的 Thunk。

`SymTagCustomType` 指出符號是自訂編譯器符號。

`SymTagManagedType` 指出符號在中繼資料中。

`SymTagDimension` 指出符號為 FORTRAN 多維陣列。

`SymTagCallSite` 表示符號代表呼叫位置。

`SymTagInlineSite` 表示符號代表內嵌網站。

`SymTagBaseInterface` 指出符號是基底介面。

`SymTagVectorType` 指出符號是向量類型。

`SymTagMatrixType` 指出符號是矩陣類型。

`SymTagHLSLType` 指出符號為高階著色器語言類型。

## <a name="remarks"></a>備註
偵錯工具檔中的所有符號都有指定符號類型的識別標記。

呼叫 [IDiaSymbol：： get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) 方法時，會傳回此列舉中的值。

此列舉中的值會傳遞至下列方法，以將搜尋範圍限制為特定符號類型：

- [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)

- [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)

- [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)

- [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)

- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)

- [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)

- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)

- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

## <a name="requirements"></a>規格需求
標頭： cvconst。h

## <a name="see-also"></a>另請參閱
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
