---
title: IActiveScriptParse::ParseScriptText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParse.ParseScriptText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_ParseScriptText
ms.assetid: 2d237d6c-cc65-415b-8808-72791304a136
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3396aee8c044ee9b84d7d6256c6ad69a99965170
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62954881"
---
# <a name="iactivescriptparseparsescripttext"></a>IActiveScriptParse::ParseScriptText
剖析指定的程式碼程式碼片段，加入宣告至命名空間，並評估為適當的程式碼。  
  
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
|`pstrCode`|[in]若要評估的 scriptlet 文字的位址。 這個字串的解譯取決於指令碼語言。|  
|`pstrItemName`|[in]提供評估 scriptlet 的內容項目名稱的位址。 如果此參數為 NULL，就會在指令碼引擎的全域內容中評估程式碼。|  
|`punkContext`|[in]內容物件的位址。 這個物件被保留用於偵錯環境，其中這類內容可能會提供偵錯工具，來代表使用中的執行階段內容。 如果此參數為 NULL，則引擎會使用`pstrItemName`識別內容。|  
|`pstrDelimiter`|[in]結束的程式碼片段分隔符號的位址。 當`pstrCode`剖析文字資料流，從主應用程式通常會使用分隔符號，例如兩個單引號 （'），偵測 scriptlet 結尾。 這個參數指定主應用程式使用，允許以提供一些條件式的基本前置處理指令碼引擎的分隔符號 （比方說，取代兩個單引號以做為分隔符號使用的單引號 [']）。 究竟要如何 （以及是否） 指令碼的引擎會使用這項資訊會取決於指令碼引擎。 將此參數設定為`NULL`如果主機未使用的分隔符號來標示 scriptlet 結尾。|  
|`dwSourceContextCookie`|[in]用來進行偵錯 cookie。|  
|`ulStartingLineNumber`|[in]指定剖析將會在開始哪一行的以零為起始值。|  
|`dwFlags`|[in]與 scriptlet 相關的旗標。 可以是下列值的組合：|  
  
|值|意義|  
|-----------|-------------|  
|SCRIPTTEXT_ISEXPRESSION|如果計算的運算式和陳述式之間的差別是很重要，但在指令碼語言中語法上模稜兩可，這個旗標會指定程式碼片段是可解譯為運算式，而不是陳述式或陳述式的清單。 根據預設，除非可以從 scriptlet 文字的語法判斷正確的選擇，會假設陳述式。|  
|SCRIPTTEXT_ISPERSISTENT|表示是否指令碼引擎已儲存，是否應該儲存此呼叫期間加入的程式碼 (例如，透過呼叫`IPersist*::Save`)，或如果指令碼引擎透過轉換為初始化的狀態重設。|  
|SCRIPTTEXT_ISVISIBLE|指出應該顯示的指令碼文字 (因此，可依據名稱呼叫) 做為指令碼的命名空間中的全域方法。|  
  
|||  
|-|-|  
|`pvarResult`|[out]接收 scriptlet 處理序的結果的緩衝區位址或`NULL`如果呼叫端不預期結果 （也就是未設定 SCRIPTTEXT_ISEXPRESSION 值）。|  
|`pexcepinfo`|[out]接收到的例外狀況資訊結構的位址。 如果會填入這個結構`IActiveScriptParse::ParseScriptText`傳回 DISP_E_EXCEPTION。|  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`DISP_E_EXCEPTION`|處理 scriptlet 中發生例外狀況。 `pexcepinfo`參數包含例外狀況的相關資訊。|  
|`E_INVALIDARG`|引數無效。|  
|`E_POINTER`|指定了無效的指標。|  
|`E_NOTIMPL`|不支援這個方法。 指令碼引擎不支援執行階段評估的運算式或陳述式。|  
|`E_UNEXPECTED`|不需要呼叫 （例如，指令碼引擎處於初始化或關閉狀態，或 SCRIPTTEXT_ISEXPRESSION 旗標已設定和指令碼引擎處於初始化狀態）。|  
|`OLESCRIPT_E_SYNTAX`|Scriptlet 中發生未指定的語法錯誤。|  
  
## <a name="remarks"></a>備註  
 如果指令碼引擎處於初始化狀態，程式碼不會實際評估此呼叫; 期間相反地，這類程式碼會排入佇列時就執行指令碼引擎轉換為 （或是經過） 啟動的狀態。 初始化狀態中不允許執行，因為它會是錯誤呼叫這個方法以 SCRIPTTEXT_ISEXPRESSION 旗標，在初始化狀態中。  
  
 程式碼片段可以是運算式、 陳述式，清單或允許的指令碼語言的任何項目。 比方說，這個方法用於評估 HTML\<指令碼 > 標記，以允許要建構的 HTML 網頁，而不是只將它們編譯成指令碼狀態執行的陳述式。  
  
 傳遞至這個方法的程式碼必須是有效完整部分的程式碼。 例如，在 VBScript 中是不合法呼叫這個方法一次使用 Sub function，然後第二次使用`End Sub`。 剖析器必須等到第二個呼叫完成副程式，但是而是必須產生剖析錯誤由於副程式宣告已啟動但未完成。  
  
 如需指令碼狀態的詳細資訊，請參閱指令碼引擎狀態一節[Windows 指令碼引擎](../../winscript/windows-script-engines.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)