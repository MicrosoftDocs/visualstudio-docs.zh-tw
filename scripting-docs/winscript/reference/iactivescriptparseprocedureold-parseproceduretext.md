---
title: IActiveScriptParseProcedureOld::ParseProcedureText |Microsoft Docs
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
ms.openlocfilehash: ec100214a43be6e1faf5e229ce6452432065002b
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093388"
---
# <a name="iactivescriptparseprocedureoldparseproceduretext"></a>IActiveScriptParseProcedureOld::ParseProcedureText
剖析指定的程式碼程序，並將匿名的程序加入至命名空間。  
  
## <a name="syntax"></a>語法  
  
```cpp
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
 [in]此程序的型式參數名稱。 參數名稱都必須以適當的指令碼引擎的分隔符號分隔。 名稱不應該用括號括住。  
  
 `pstrItemName`  
 [in]提供評估程序的內容的具名項目名稱。 如果這個參數是`NULL`，指令碼引擎的全域內容中評估程式碼。  
  
 `punkContext`  
 [in]內容物件。 這個物件被保留用於偵錯環境，其中這類內容可能會提供偵錯工具，來代表使用中的執行階段內容。 如果這個參數是`NULL`，則引擎會使用`pstrItemName`識別內容。  
  
 `pstrDelimiter`  
 [in]結束程序的分隔符號。 當`pstrCode`剖析文字資料流，從主應用程式通常會使用分隔符號，例如兩個單引號 （'），來偵測程序的結尾。 這個參數指定主應用程式使用，允許以提供一些條件式、 指令碼引擎的分隔符號 （例如，單引號 ['] 取代為兩個單引號以做為分隔符號） 的基本前置處理。 究竟要如何 （以及是否） 這項資訊會取決於指令碼引擎的指令碼引擎使用。 將此參數設定為`NULL`如果主機未使用的分隔符號來標示程序的結尾。  
  
 `dwSourceContextCookie`  
 [in]應用程式定義的值，用於偵錯用途。  
  
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
 [out]其中的預設方法是由這個方法剖析的程序傳回的分派包裝函式。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_INVALIDARG`|引數無效。|  
|`E_POINTER`|指定了無效的指標。|  
|`E_NOTIMPL`|不支援這個方法。 指令碼引擎不支援命名空間的程序的執行階段的加入。|  
|`E_UNEXPECTED`|不需要呼叫 （例如，指令碼引擎處於初始化或關閉狀態）。|  
|`OLESCRIPT_E_SYNTAX`|在程序中發生未指定的語法錯誤。|  
|`S_FALSE`|指令碼引擎不支援的分派物件;`ppdisp`參數設為`NULL`。|  
  
## <a name="remarks"></a>備註  
 此呼叫期間不評估任何指令碼相反地，此程序會編譯成方法上`ppdisp`位置呼叫它，可以是由指令碼之後。  
  
 此介面已被取代的益處`IActiveScriptParseProcedure`介面。 `IActiveScriptParseProcedure::ParseProcedureText`方法類似這種方法，但它可讓您指定的程序名稱。 在所有情況下，`IActiveScriptParseProcedure::ParseProcedureText`應該使用。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptParseProcedureOld 介面](../../winscript/reference/iactivescriptparseprocedureold-interface.md)   
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)