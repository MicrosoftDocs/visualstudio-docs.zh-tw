---
title: "IActiveScriptParse32::ParseScriptText |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f33e454c-69d8-4cab-9150-d1e7fd04786d
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: af1e3b6723b402263359719695aa1f57432c76e2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparse32parsescripttext"></a>IActiveScriptParse32::ParseScriptText
剖析指定的程式碼程式碼片段，新增到命名空間宣告，並評估為適當的程式碼。  
  
## <a name="syntax"></a>語法  
  
```  
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
|`pstrCode`|[in]要評估的程式碼片段文字的位址。 這個字串的解譯取決於指令碼語言。|  
|`pstrItemName`|[in]提供要評估程式碼片段的內容項目名稱的位址。 如果這個參數是 NULL，就會在指令碼引擎的全域內容中評估程式碼。|  
|`punkContext`|[in]內容物件的位址。 此物件被保留供在偵錯環境，其中這類內容可能會提供偵錯工具，來代表作用中的執行階段內容中使用。 如果這個參數是 NULL，引擎會使用`pstrItemName`來識別內容。|  
|`pstrDelimiter`|[in]結尾的程式碼片段分隔符號的位址。 當`pstrCode`剖析文字資料流，從主應用程式通常會使用分隔符號，例如兩個單引號 （'），來偵測程式碼片段的結尾。 這個參數會指定使用主機，允許以提供一些條件的基本前置處理指令碼引擎的分隔符號 （例如，取代單引號 ['] 具有兩個單引號做為分隔符號使用）。 方式 （和 if） 指令碼的引擎會使用這項資訊取決於指令碼引擎。 這個參數設定為`NULL`若主機未使用分隔符號來標示程式碼片段的結尾。|  
|`dwSourceContextCookie`|[in]Cookie 用於偵錯之用。|  
|`ulStartingLineNumber`|[in]以零為起始的值，指定會在開始剖析那一行。|  
|`dwFlags`|[in]程式碼片段相關聯的旗標。 可以是下列值的組合：|  
  
|值|意義|  
|-----------|-------------|  
|SCRIPTTEXT_ISEXPRESSION|如果計算的運算式和陳述式之間的差別是很重要，但語法模稜兩可的指令碼語言中，此旗標會指定程式碼片段會被解譯為運算式，而不是陳述式或陳述式的清單。 根據預設，除非您可以從程式碼片段文字的語法判斷正確的選擇，會假設陳述式。|  
|SCRIPTTEXT_ISPERSISTENT|表示是否儲存指令碼引擎時，會儲存此通話期間加入的程式碼 (例如，透過呼叫`IPersist*::Save`)，或如果指令碼引擎會重設透過初始化的狀態轉換。|  
|SCRIPTTEXT_ISVISIBLE|指出應該顯示指令碼文字 (，因此，可依名稱) 做為指令碼的命名空間中的全域方法。|  
  
|||  
|-|-|  
|`pvarResult`|[out]接收的程式碼片段處理結果的緩衝區位址或`NULL`如果呼叫端必須確保沒有結果 （也就是未設定 SCRIPTTEXT_ISEXPRESSION 值）。|  
|`pexcepinfo`|[out]接收到的例外狀況資訊結構的位址。 此結構會填滿，如果`IActiveScriptParse::ParseScriptText`傳回 DISP_E_EXCEPTION。|  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`DISP_E_EXCEPTION`|在程式碼片段的處理時發生例外狀況。 `pexcepinfo`參數包含例外狀況的相關資訊。|  
|`E_INVALIDARG`|引數無效。|  
|`E_POINTER`|指定了無效的指標。|  
|`E_NOTIMPL`|不支援這個方法。 指令碼引擎不支援執行階段評估的運算式或陳述式。|  
|`E_UNEXPECTED`|不應該呼叫 （例如，指令碼引擎會處於未初始化或已關閉狀態，或 SCRIPTTEXT_ISEXPRESSION 旗標已設定和指令碼引擎正在初始化的狀態）。|  
|`OLESCRIPT_E_SYNTAX`|在程式碼片段中發生未指定的語法錯誤。|  
  
## <a name="remarks"></a>備註  
 如果指令碼引擎在初始化的狀態，將實際在這個呼叫; 期間評估沒有程式碼這類程式碼會排入佇列而執行指令碼引擎轉換至 （或透過） 時啟動的狀態。 因為初始化的狀態不允許執行時，會呼叫這個方法與 SCRIPTTEXT_ISEXPRESSION 中的旗標時初始化的狀態錯誤。  
  
 程式碼片段可以是運算式、 陳述式，清單或指令碼語言所允許的任何項目。 例如，這個方法用於評估的 HTML\<指令碼 > 標記，允許執行，因為正在建構的 HTML 網頁，而不是只將其編譯至指令碼狀態的陳述式。  
  
 傳遞至此方法的程式碼必須是有效而完整的一部分的程式碼。 例如，在 VBScript 中不合法呼叫這個方法一次使用 Sub Function(x)，然後第二次使用`End Sub`。 剖析器必須等候完成的副程式，第二個呼叫，但而是必須產生剖析錯誤，因為副程式宣告已啟動，但未完成。  
  
 如需指令碼狀態的詳細資訊，請參閱 > 一節指令碼引擎狀態[Windows 指令碼引擎](../../winscript/windows-script-engines.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)