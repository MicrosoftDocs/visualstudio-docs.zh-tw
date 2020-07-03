---
title: IActiveScriptParseProcedure32：:P arseProcedureText |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: ede37171-2f1e-4467-a358-17bd4a4f1869
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 52333d13731b5c31329ee812be403c09cf43d63b
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835728"
---
# <a name="iactivescriptparseprocedure32parseproceduretext"></a>IActiveScriptParseProcedure32::ParseProcedureText
剖析指定的程式碼程式，並將程式新增至命名空間。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT ParseProcedureText(  
    LPCOLESTR pstrCode,              // address of procedure text  
    LPCOLESTR pstrFormalParams,      // address of formal parameter names  
    LPCOLESTR pstrProcedureName,     // address of procedure name  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-procedure delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // procedure flags  
    IDispatch **ppdisp               // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pstrCode`  
 在要評估之程式文字的位址。 這個字串的轉譯取決於指令碼語言。  
  
 `pstrFormalParams`  
 在程式正式參數名稱的位址。 參數名稱必須與腳本引擎的適當分隔符號分隔。 名稱不能以括弧括住。  
  
 `pstrProcedureName`  
 在要剖析之程式名稱的位址。  
  
 `pstrItemName`  
 在提供要評估程式之內容的專案名稱位址。 如果此參數為 `NULL` ，則會在腳本引擎的全域內容中評估程式碼。  
  
 `punkContext`  
 在內容物件的位址。 這個物件已保留供偵錯工具使用，在此情況下，可能會由偵錯工具提供這類內容來表示作用中的執行時間內容。 如果此參數為 `NULL` ，引擎就會使用 `pstrItemName` 來識別內容。  
  
 `pstrDelimiter`  
 在程式結尾分隔符號的位址。 `pstrCode`從文字的資料流程剖析時，主機通常會使用分隔符號，例如兩個單引號（' '）來偵測程式的結尾。 這個參數會指定主機所使用的分隔符號，讓腳本引擎提供一些條件式基本前置處理（例如，使用兩個單引號來取代單引號 [']，做為分隔符號）。 腳本引擎利用這項資訊的確切方式，取決於腳本引擎。 `NULL`如果主機未使用分隔符號來標記程式的結尾，請將此參數設定為。  
  
 `dwSourceContextCookie`  
 在應用程式定義的值，用於進行調試。  
  
 `ulStartingLineNumber`  
 在以零為起始的值，指定剖析要開始的行。  
  
 `dwFlags`  
 在與程式相關聯的旗標。 可以是這些值的組合：  
  
|值|意義|  
|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|表示中的程式碼 `pstrCode` 是代表程式傳回值的運算式。 根據預設，程式碼可以包含運算式、語句清單，或指令碼語言在程式中允許的任何其他專案。|  
|SCRIPTPROC_IMPLICIT_THIS|表示 `this` 指標包含在程式的範圍內。|  
|SCRIPTPROC_IMPLICIT_PARENTS|表示指標的父系 `this` 包含在程式的範圍中。|  
  
 `ppdisp`  
 脫銷物件的指標位址，包含腳本的全域方法和屬性。 如果腳本引擎不支援這類物件， `NULL` 則會傳回。  
  
## <a name="return-value"></a>傳回值  
 傳回下列其中一值：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引數無效。|  
|`E_POINTER`|指定了不正確指標。|  
|`E_NOTIMPL`|不支援此方法。 腳本引擎不支援以執行時間將程式新增至命名空間。|  
|`E_UNEXPECTED`|不需要呼叫（例如，腳本引擎處於未初始化或已關閉狀態）。|  
|`OLESCRIPT_E_SYNTAX`|程式中發生未指定的語法錯誤。|  
|`S_FALSE`|腳本引擎不支援分派物件;`ppdisp`參數設定為 `NULL` 。|  
  
## <a name="remarks"></a>備註  
 此呼叫期間不會評估任何腳本;相反地，此程式會編譯成腳本狀態，稍後腳本可以呼叫它。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptParseProcedure32](../../winscript/reference/iactivescriptparseprocedure32.md)