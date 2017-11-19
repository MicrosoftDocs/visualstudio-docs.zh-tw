---
title: "IActiveScriptParseProcedure::ParseProcedureText |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptParseProcedure.ParseProcedureText
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptParseProcedure_ParseProcedureText
ms.assetid: 345a74ae-b4e8-42b2-abd8-633a370e8e7f
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c2a877f6ebc692f9f54d69597e06db501f642802
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparseprocedureparseproceduretext"></a>IActiveScriptParseProcedure::ParseProcedureText
剖析指定的程式碼的程序，並將程式新增到命名空間。  
  
## <a name="syntax"></a>語法  
  
```  
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
 [in]要評估的程序文字的位址。 這個字串的解譯取決於指令碼語言。  
  
 `pstrFormalParams`  
 [in]程序的型式參數名稱的位址。 參數名稱必須以適當的指令碼引擎的分隔符號分隔。 名稱不應該包含在括號中。  
  
 `pstrProcedureName`  
 [in]要剖析的程序名稱的位址。  
  
 `pstrItemName`  
 [in]提供要評估的程序的內容項目名稱的位址。 如果這個參數是`NULL`，指令碼引擎的全域內容中評估程式碼。  
  
 `punkContext`  
 [in]內容物件的位址。 此物件被保留供在偵錯環境，其中這類內容可能會提供偵錯工具，來代表作用中的執行階段內容中使用。 如果這個參數是`NULL`，引擎會使用`pstrItemName`來識別內容。  
  
 `pstrDelimiter`  
 [in]程序結束的分隔字元的位址。 當`pstrCode`剖析文字資料流，從主應用程式通常會使用分隔符號，例如兩個單引號 （'），來偵測程序的結尾。 這個參數會指定使用主機，允許以提供一些條件的基本前置處理指令碼引擎的分隔符號 （例如，取代單引號 ['] 具有兩個單引號做為分隔符號使用）。 方式 （和 if） 指令碼的引擎會使用這項資訊取決於指令碼引擎。 這個參數設定為`NULL`若主機未使用分隔符號來標示程序的結尾。  
  
 `dwSourceContextCookie`  
 [in]應用程式定義的值，用於偵錯之用。  
  
 `ulStartingLineNumber`  
 [in]以零為起始的值，指定會在開始剖析那一行。  
  
 `dwFlags`  
 [in]此程序相關聯的旗標。 可以是下列值的組合：  
  
|值|意義|  
|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|表示中的程式碼`pstrCode`是表示此程序的傳回值的運算式。 根據預設，程式碼可以包含運算式、 陳述式，清單或任何其他程序中允許的指令碼語言。|  
|SCRIPTPROC_IMPLICIT_THIS|表示`this`指標包含在程序的範圍。|  
|SCRIPTPROC_IMPLICIT_PARENTS|表示父系`this`指標包含在程序的範圍內。|  
  
 `ppdisp`  
 [out]包含指令碼的全域方法和屬性的物件的指標位址。 如果指令碼引擎不支援這類物件，`NULL`傳回。  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引數無效。|  
|`E_POINTER`|指定了無效的指標。|  
|`E_NOTIMPL`|不支援這個方法。 指令碼引擎不支援命名空間的程序的執行階段的加入。|  
|`E_UNEXPECTED`|不應該呼叫 （例如，指令碼引擎是在未初始化或已關閉狀態）。|  
|`OLESCRIPT_E_SYNTAX`|程序中發生未指定的語法錯誤。|  
|`S_FALSE`|指令碼引擎不支援分派物件。`ppdisp`參數設定為`NULL`。|  
  
## <a name="remarks"></a>備註  
 此呼叫; 期間會不評估任何指令碼相反地，此程序會編譯到指令碼呼叫的狀態，它可以指令碼更新版本。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)