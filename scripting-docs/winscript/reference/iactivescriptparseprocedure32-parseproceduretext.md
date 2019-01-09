---
title: IActiveScriptParseProcedure32::ParseProcedureText |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ede37171-2f1e-4467-a358-17bd4a4f1869
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: e772d8276de5528f0aed25278a03725d09edb180
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090905"
---
# <a name="iactivescriptparseprocedure32parseproceduretext"></a>IActiveScriptParseProcedure32::ParseProcedureText
剖析指定的程式碼程序，並將命名空間中的程序。  
  
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
 [in]若要評估的程序文字的位址。 這個字串的解譯取決於指令碼語言。  
  
 `pstrFormalParams`  
 [in]程序的型式參數名稱的位址。 參數名稱都必須以適當的指令碼引擎的分隔符號分隔。 名稱不應該用括號括住。  
  
 `pstrProcedureName`  
 [in]要剖析的程序名稱的位址。  
  
 `pstrItemName`  
 [in]提供評估程序的內容項目名稱的位址。 如果這個參數是`NULL`，指令碼引擎的全域內容中評估程式碼。  
  
 `punkContext`  
 [in]內容物件的位址。 這個物件被保留用於偵錯環境，其中這類內容可能會提供偵錯工具，來代表使用中的執行階段內容。 如果這個參數是`NULL`，則引擎會使用`pstrItemName`識別內容。  
  
 `pstrDelimiter`  
 [in]程序結束分隔符號的位址。 當`pstrCode`剖析文字資料流，從主應用程式通常會使用分隔符號，例如兩個單引號 （'），來偵測程序的結尾。 這個參數指定主應用程式使用，允許以提供一些條件式的基本前置處理指令碼引擎的分隔符號 （比方說，取代兩個單引號以做為分隔符號使用的單引號 [']）。 究竟要如何 （以及是否） 指令碼的引擎會使用這項資訊會取決於指令碼引擎。 將此參數設定為`NULL`如果主機未使用的分隔符號來標示程序的結尾。  
  
 `dwSourceContextCookie`  
 [in]應用程式定義的值，用於偵錯用途。  
  
 `ulStartingLineNumber`  
 [in]指定剖析將會在開始哪一行的以零為起始值。  
  
 `dwFlags`  
 [in]此程序相關聯的旗標。 可以是下列值的組合：  
  
|值|意義|  
|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|表示中的程式碼`pstrCode`是表示此程序的傳回值的運算式。 根據預設，程式碼可以包含運算式、 陳述式，清單或其他指令碼語言所允許的程序中任何項目。|  
|SCRIPTPROC_IMPLICIT_THIS|表示`this`指標包含在程序的範圍。|  
|SCRIPTPROC_IMPLICIT_PARENTS|表示父系`this`指標包含在程序的範圍內。|  
  
 `ppdisp`  
 [out]包含指令碼的全域方法和屬性的物件的指標位址。 如果指令碼引擎不支援這類物件，`NULL`會傳回。  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引數無效。|  
|`E_POINTER`|指定了無效的指標。|  
|`E_NOTIMPL`|不支援這個方法。 指令碼引擎不支援命名空間的程序的執行階段的加入。|  
|`E_UNEXPECTED`|不需要呼叫 （例如，指令碼引擎處於初始化或關閉狀態）。|  
|`OLESCRIPT_E_SYNTAX`|在程序中發生未指定的語法錯誤。|  
|`S_FALSE`|指令碼引擎不支援的分派物件;`ppdisp`參數設為`NULL`。|  
  
## <a name="remarks"></a>備註  
 此呼叫期間不評估任何指令碼相反地，此程序會編譯成指令碼呼叫的狀態，它可以由指令碼稍後。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptParseProcedure32](../../winscript/reference/iactivescriptparseprocedure32.md)