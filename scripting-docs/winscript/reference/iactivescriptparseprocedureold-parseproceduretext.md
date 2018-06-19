---
title: IActiveScriptParseProcedureOld::ParseProcedureText |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedureOld.ParseProcedureText
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptParseProcedureOld::ParseProcedureText
ms.assetid: 21a21313-35ce-432d-b9a6-7999065f19ac
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cab546deb390535fa8ff71e116a0ad42d33cc104
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724998"
---
# <a name="iactivescriptparseprocedureoldparseproceduretext"></a>IActiveScriptParseProcedureOld::ParseProcedureText
剖析指定的程式碼的程序，並將匿名的程序加入至命名空間。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ParseProcedureText(  
   LPCOLESTR    pstrCode,  
   LPCOLESTR    pstrFormalParams,  
   LPCOLESTR    pstrItemName,  
   IUnknown*    punkContext,  
   LPCOLESTR    pstrDelimiter,  
   DWORD_PTR    dwSourceContextCookie,  
   ULONG        ulStartingLineNumber,  
   DWORD        dwFlags,  
   IDispatch**  ppdisp  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pstrCode`  
 [in]要評估的程序文字。 這個字串的解譯取決於指令碼語言。  
  
 `pstrFormalParams`  
 [in]此程序的型式參數名稱。 參數名稱必須以適當的指令碼引擎的分隔符號分隔。 名稱不應該包含在括號中。  
  
 `pstrItemName`  
 [in]提供要評估的程序的內容之具名項目的名稱。 如果這個參數是`NULL`，指令碼引擎的全域內容中評估程式碼。  
  
 `punkContext`  
 [in]將內容物件。 此物件被保留供在偵錯環境，其中這類內容可能會提供偵錯工具，來代表作用中的執行階段內容中使用。 如果這個參數是`NULL`，引擎會使用`pstrItemName`來識別內容。  
  
 `pstrDelimiter`  
 [in]程序結束的分隔符號。 當`pstrCode`剖析文字資料流，從主應用程式通常會使用分隔符號，例如兩個單引號 （'），來偵測程序的結尾。 此參數指定的分隔符號使用的主機，讓指令碼引擎提供一些條件，基本前置處理 （例如，單引號 ['] 取代成兩個單引號做為分隔符號使用）。 方式 （和 if） 這項資訊取決於指令碼引擎的指令碼引擎使用。 這個參數設定為`NULL`若主機未使用分隔符號來標示程序的結尾。  
  
 `dwSourceContextCookie`  
 [in]應用程式定義的值，用於偵錯之用。  
  
 `ulStartingLineNumber`  
 [in]指定哪一行剖析開始的以零為起始值。  
  
 `dwFlags`  
 [in]此程序相關聯的旗標。 可以是下列值的組合。  
  
|常數|值|意義|  
|--------------|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|0x00000020|表示中的程式碼`pstrCode`是表示此程序的傳回值的運算式。|  
|SCRIPTPROC_IMPLICIT_THIS|0x00000100|表示`this`指標包含在程序的範圍。|  
|SCRIPTPROC_IMPLICIT_PARENTS|0x00000200|表示父系`this`指標包含在程序的範圍內。|  
  
 `ppdisp`  
 [out]其中的預設方法是由這個方法所剖析的程序傳回的分派包裝函式。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_INVALIDARG`|引數無效。|  
|`E_POINTER`|指定了無效的指標。|  
|`E_NOTIMPL`|不支援這個方法。 指令碼引擎不支援命名空間的程序的執行階段的加入。|  
|`E_UNEXPECTED`|不應該呼叫 （例如，指令碼引擎是在未初始化或已關閉狀態）。|  
|`OLESCRIPT_E_SYNTAX`|程序中發生未指定的語法錯誤。|  
|`S_FALSE`|指令碼引擎不支援分派物件。`ppdisp`參數設定為`NULL`。|  
  
## <a name="remarks"></a>備註  
 此呼叫; 期間會不評估任何指令碼而是程序編譯成方法上`ppdisp`其中它可由呼叫指令碼之後。  
  
 此介面已被取代之喜好`IActiveScriptParseProcedure`介面。 `IActiveScriptParseProcedure::ParseProcedureText`方法類似於這個方法，但它可讓指定的程序名稱。 在所有情況下，`IActiveScriptParseProcedure::ParseProcedureText`應使用。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptParseProcedureOld 介面](../../winscript/reference/iactivescriptparseprocedureold-interface.md)   
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)