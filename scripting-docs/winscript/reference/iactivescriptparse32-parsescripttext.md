---
title: IActiveScriptParse32：:P arseScriptText |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: f33e454c-69d8-4cab-9150-d1e7fd04786d
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: e26b5cb1790cab38a6544a04307b7e336a952519
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835364"
---
# <a name="iactivescriptparse32parsescripttext"></a>IActiveScriptParse32::ParseScriptText
剖析指定的程式碼程式碼片段、將宣告新增至命名空間，並適當地評估程式碼。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT ParseScriptText(  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // cookie for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    VARIANT *pvarResult,             // address of buffer for results  
    EXCEPINFO *pexcepinfo            // address of buffer for error data  
);  
```  
  
#### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|`pstrCode`|在要評估之程式碼片段文字的位址。 這個字串的轉譯取決於指令碼語言。|  
|`pstrItemName`|在專案名稱的位址，提供要在其中評估程式碼片段的內容。 如果這個參數是 Null，則會在腳本引擎的全域內容中評估程式碼。|  
|`punkContext`|在內容物件的位址。 這個物件已保留供偵錯工具使用，在此情況下，可能會由偵錯工具提供這類內容來表示作用中的執行時間內容。 如果這個參數是 Null，引擎就會使用 `pstrItemName` 來識別內容。|  
|`pstrDelimiter`|在程式碼片段後端分隔符號的位址。 `pstrCode`從文字的資料流程剖析時，主機通常會使用分隔符號，例如兩個單引號（' '）來偵測程式碼片段的結尾。 這個參數會指定主機所使用的分隔符號，讓腳本引擎提供一些條件式基本前置處理（例如，使用兩個單引號來取代單引號 [']，做為分隔符號）。 腳本引擎利用這項資訊的確切方式，取決於腳本引擎。 `NULL`如果主機未使用分隔符號來標示程式碼片段的結尾，請將此參數設定為。|  
|`dwSourceContextCookie`|在用於進行偵錯工具的 Cookie。|  
|`ulStartingLineNumber`|在以零為起始的值，指定剖析要開始的行。|  
|`dwFlags`|在與程式碼片段相關聯的旗標。 可以是這些值的組合：|  
  
|值|意義|  
|-----------|-------------|  
|SCRIPTTEXT_ISEXPRESSION|如果計算運算式與語句之間的差異很重要，但指令碼語言中的語法不明確，則此旗標會指定要將程式碼片段視為運算式，而不是語句或語句清單。 根據預設，除非您可以從程式碼片段文字的語法判斷正確的選擇，否則會假設語句。|  
|SCRIPTTEXT_ISPERSISTENT|表示如果儲存腳本引擎（例如，透過呼叫 `IPersist*::Save` ），或如果腳本引擎是藉由轉換回到已初始化的狀態重設，則應該儲存此呼叫期間新增的程式碼。|  
|SCRIPTTEXT_ISVISIBLE|表示腳本文字應該是可見的（因此，以名稱呼叫）做為腳本命名空間中的全域方法。|  
  
|||  
|-|-|  
|`pvarResult`|脫銷接收程式碼片段處理結果的緩衝區位址， `NULL` 如果呼叫端不預期結果（也就是未設定 SCRIPTTEXT_ISEXPRESSION 值），則為。|  
|`pexcepinfo`|脫銷接收例外狀況資訊之結構的位址。 如果傳回 DISP_E_EXCEPTION，則會填入此結構 `IActiveScriptParse::ParseScriptText` 。|  
  
## <a name="return-value"></a>傳回值  
 傳回下列其中一值：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`DISP_E_EXCEPTION`|處理程式碼片段時發生例外狀況。 `pexcepinfo`參數包含例外狀況的相關資訊。|  
|`E_INVALIDARG`|引數無效。|  
|`E_POINTER`|指定了不正確指標。|  
|`E_NOTIMPL`|不支援此方法。 腳本引擎不支援運算式或語句的執行時間評估。|  
|`E_UNEXPECTED`|不需要呼叫（例如，腳本引擎處於未初始化或已關閉狀態，或已設定 SCRIPTTEXT_ISEXPRESSION 旗標，且腳本引擎處於初始化狀態）。|  
|`OLESCRIPT_E_SYNTAX`|程式碼片段中發生未指定的語法錯誤。|  
  
## <a name="remarks"></a>備註  
 如果腳本引擎處於已初始化的狀態，則不會在此呼叫期間實際評估任何程式碼。相反地，這類程式碼會在腳本引擎轉換成（或透過）已啟動狀態時，排入佇列並執行。 因為在初始化的狀態中不允許執行，所以在初始化的狀態下，使用 SCRIPTTEXT_ISEXPRESSION 旗標呼叫此方法會發生錯誤。  
  
 程式碼片段可以是運算式、語句清單，或指令碼語言所允許的任何專案。 例如，這個方法是在 HTML 標籤的評估中使用 \<SCRIPT> ，這可讓語句在撰寫 html 網頁時執行，而不只是將它們編譯成腳本狀態。  
  
 傳遞給這個方法的程式碼必須是有效的完整程式碼部分。 例如，在 VBScript 中，使用 Sub 函式（x）來呼叫這個方法一次，然後使用第二次，是不合法的 `End Sub` 。 剖析器不能等候第二個呼叫完成副程式，而是必須產生 parse 錯誤，因為副程式宣告已啟動但未完成。  
  
 如需腳本狀態的詳細資訊，請參閱[Windows 腳本引擎](../../winscript/windows-script-engines.md)的腳本引擎狀態一節。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)