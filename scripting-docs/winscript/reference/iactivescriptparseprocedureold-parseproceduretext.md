---
title: IActiveScriptParseProcedureOld：:P arseProcedureText |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 116cbc7fac0d53b55c9766945d56ecebd27b6785
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577441"
---
# <a name="iactivescriptparseprocedureoldparseproceduretext"></a>IActiveScriptParseProcedureOld::ParseProcedureText
剖析指定的程式碼程式，並將匿名程式新增至命名空間。  
  
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
 在要評估的程式文字。 這個字串的轉譯取決於指令碼語言。  
  
 `pstrFormalParams`  
 在程式的正式參數名稱。 參數名稱必須與腳本引擎的適當分隔符號分隔。 名稱不能以括弧括住。  
  
 `pstrItemName`  
 在命名專案的名稱，可提供要在其中評估程式的內容。 如果 `NULL` 此參數，則會在腳本引擎的全域內容中評估程式碼。  
  
 `punkContext`  
 在內容物件。 這個物件已保留供偵錯工具使用，在此情況下，可能會由偵錯工具提供這類內容來表示作用中的執行時間內容。 如果 `NULL` 這個參數，引擎就會使用 `pstrItemName` 來識別內容。  
  
 `pstrDelimiter`  
 在程式結尾的分隔符號。 從文字的資料流程剖析 `pstrCode` 時，主機通常會使用分隔符號，例如兩個單引號（' '）來偵測程式的結尾。 這個參數會指定主機使用的分隔符號，讓腳本引擎提供一些條件式的基本前置處理（例如，以兩個單引號取代單引號 ['] 做為分隔符號使用）。 腳本引擎使用此資訊的確切方式，取決於腳本引擎。 如果主機未使用分隔符號來標記程式的結尾，請將此參數設定為 `NULL`。  
  
 `dwSourceContextCookie`  
 在應用程式定義的值，用於進行調試。  
  
 `ulStartingLineNumber`  
 在以零為起始的值，指定要開始剖析的那一行。  
  
 `dwFlags`  
 在與程式相關聯的旗標。 可以是這些值的組合。  
  
|常數|值|意義|  
|--------------|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|0x00000020|表示 `pstrCode` 中的程式碼是代表此程式傳回值的運算式。|  
|SCRIPTPROC_IMPLICIT_THIS|0x00000100|表示 `this` 指標包含在程式的範圍內。|  
|SCRIPTPROC_IMPLICIT_PARENTS|0x00000200|表示 `this` 指標的父系包含在程式的範圍內。|  
  
 `ppdisp`  
 脫銷傳回分派包裝函式，其中的預設方法是由這個方法剖析的程式。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_INVALIDARG`|引數無效。|  
|`E_POINTER`|指定了不正確指標。|  
|`E_NOTIMPL`|不支援這個方法。 腳本引擎不支援以執行時間將程式新增至命名空間。|  
|`E_UNEXPECTED`|不需要呼叫（例如，腳本引擎處於未初始化或已關閉狀態）。|  
|`OLESCRIPT_E_SYNTAX`|程式中發生未指定的語法錯誤。|  
|`S_FALSE`|腳本引擎不支援分派物件;`ppdisp`parameter 設定為 `NULL`。|  
  
## <a name="remarks"></a>備註  
 此呼叫期間不會評估任何腳本;相反地，此程式會編譯成 `ppdisp` 的方法，稍後腳本可以呼叫它。  
  
 這個介面已被取代，而改用 `IActiveScriptParseProcedure` 介面。 @No__t_0 方法與這個方法類似，但它允許指定程式名稱。 在所有情況下，都應該使用 `IActiveScriptParseProcedure::ParseProcedureText`。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptParseProcedureOld 介面](../../winscript/reference/iactivescriptparseprocedureold-interface.md)   
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)