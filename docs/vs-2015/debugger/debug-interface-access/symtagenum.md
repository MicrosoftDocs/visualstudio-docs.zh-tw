---
title: SymTagEnum |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- SymTagEnum enumeration
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 09462ee9d9223c79b4ee0dcf4e8a5efa37b4c796
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783295"
---
# <a name="symtagenum"></a>SymTagEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

指定符號的類型。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
enum SymTagEnum {   
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
 `SymTagNull`  
 表示符號己沒有型別。  
  
 `SymTagExe`  
 表示符號是.exe 檔。 只有一個`SymTagExe`每個符號存放區的符號。 它可做為全域範圍，並沒有語彙的父代。  
  
 `SymTagCompiland`  
 表示符號存放區的每個編譯模組元件的編譯模組符號。 原生應用程式，`SymTagCompiland`符號都會對應至連結到映像物件檔案。 某些類型的 Microsoft Intermediate Language (MSIL) 映像，還有每個類別的一個編譯模組。  
  
 `SymTagCompilandDetails`  
 表示符號包含擴充的屬性的編譯模組。 擷取這些屬性可能會要求載入編譯模組符號。  
  
 `SymTagCompilandEnv`  
 表示符號的編譯模組中定義的環境字串。  
  
 `SymTagFunction`  
 表示符號是函式。  
  
 `SymTagBlock`  
 表示符號是巢狀的區塊。  
  
 `SymTagData`  
 表示符號的資料。  
  
 `SymTagAnnotation`  
 表示程式碼註解符號。 這個符號的子系是常數資料字串 (`SymTagData`， `LocIsConstant`， `DataIsConstant`)。 大部分的用戶端會忽略這個符號。  
  
 `SymTagLabel`  
 表示符號的標籤。  
  
 `SymTagPublicSymbol`  
 表示符號為公用符號。 原生應用程式，這個符號會是連結的映像時，遇到 COFF 外部符號。  
  
 `SymTagUDT`  
 表示符號為使用者定義的類型 （結構、 類別或等位）。  
  
 `SymTagEnum`  
 表示符號的列舉型別。  
  
 `SymTagFunctionType`  
 表示符號的函式簽章類型。  
  
 `SymTagPointerType`  
 表示符號是指標類型。  
  
 `SymTagArrayType`  
 表示符號的陣列型別。  
  
 `SymTagBaseType`  
 表示符號的基底類型。  
  
 `SymTagTypedef`  
 表示符號`typedef`，也就是另一種類型的別名。  
  
 `SymTagBaseClass`  
 表示符號的使用者定義類型的基底類別。  
  
 `SymTagFriend`  
 表示符號的使用者定義型別。  
  
 `SymTagFunctionArgType`  
 表示符號是函式的引數。  
  
 `SymTagFuncDebugStart`  
 表示符號函式的初構程式碼的結束位置。  
  
 `SymTagFuncDebugEnd`  
 表示符號的函式的結尾程式碼的開頭位置。  
  
 `SymTagUsingNamespace`  
 表示符號的命名空間的名稱，為目前範圍中作用中。  
  
 `SymTagVTableShape`  
 表示符號的虛擬資料表的描述。  
  
 `SymTagVTable`  
 表示符號的虛擬資料表指標。  
  
 `SymTagCustom`  
 表示符號是自訂的符號，而且無法解譯 dia 時發生  
  
 `SymTagThunk`  
 表示符號的 thunk，用來共用 16 和 32 位元程式碼之間的資料。  
  
 `SymTagCustomType`  
 表示符號是自訂的編譯器符號。  
  
 `SymTagManagedType`  
 表示中繼資料中的符號。  
  
 `SymTagDimension`  
 表示符號的 FORTRAN 多維陣列。  
  
 `SymTagCallSite`  
 表示符號代表呼叫位置。  
  
 `SymTagInlineSite`  
 表示符號代表內嵌網站。  
  
 `SymTagBaseInterface`  
 表示符號的基底介面。  
  
 `SymTagVectorType`  
 表示符號的向量型別。  
  
 `SymTagMatrixType`  
 表示符號的 matrix 類型。  
  
 `SymTagHLSLType`  
 表示符號為高的層級著色器語言型別。  
  
## <a name="remarks"></a>備註  
 偵錯檔案內的所有符號都有指定的符號類型的識別標記。  
  
 這個列舉型別中的值會傳回呼叫[idiasymbol:: Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)方法。  
  
 這個列舉型別中的值會傳遞至下列方法來限制搜尋特定的符號類型的範圍：  
  
-   [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
-   [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)  
  
-   [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
-   [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
-   [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)  
  
-   [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>需求  
 標頭： cvconst.h  
  
## <a name="see-also"></a>另請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [符號類型的語彙階層架構](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Idiasession:: Findsymbolbyaddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)   
 [Idiasession:: Findsymbolbyrva](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)   
 [Idiasession:: Findsymbolbyrvaex](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)   
 [Idiasession:: Findsymbolbytoken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)   
 [Idiasession:: Findsymbolbyva](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)   
 [Idiasession:: Findsymbolbyvaex](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)   
 [Idiasession:: Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)



