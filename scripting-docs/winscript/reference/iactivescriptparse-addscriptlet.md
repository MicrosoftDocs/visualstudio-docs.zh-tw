---
title: IActiveScriptParse::AddScriptlet |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParse.AddScriptlet
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_AddScriptlet
ms.assetid: 824929f4-4dd3-473a-92d9-0b96acea2f14
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e854ac71dc36263d805160f9336e049856076ce5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724648"
---
# <a name="iactivescriptparseaddscriptlet"></a>IActiveScriptParse::AddScriptlet
將程式碼的程式碼片段加入至指令碼。 這個方法使用與主應用程式的文件密不可分永續性狀態的指令碼，且主應用程式會負責將還原指令碼中，環境中而非透過`IPersist*`介面。 主要的範例包括允許的內嵌於 HTML 文件附加至內建事件的程式碼的程式碼片段的 HTML 指令碼語言 (例如，ONCLICK="button1.text='Exit'")。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT AddScriptlet(  
    LPCOLESTR pstrDefaultName,       // address of default name of scriptlet  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    LPCOLESTR pstrSubItemName,       // address of subitem name  
    LPCOLESTR pstrEventName,         // address of event name  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    BSTR *pbstrName,                 // address of actual name of scriptlet  
    EXCEPINFO *pexcepinfo            // address of exception information  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pstrDefaultName`  
 [in]預設名稱與程式碼片段的位址。 如果程式碼片段未包含名稱的資訊 （如同 ONCLICK 上述範例中），此名稱將用於識別程式碼片段。 如果這個參數是`NULL`，必要時，指令碼引擎製造唯一的名稱。  
  
 `pstrCode`  
 [in]要加入的程式碼片段文字的位址。 這個字串的解譯取決於指令碼語言。  
  
 `pstrItemName`  
 [in]包含與這個程式碼片段相關聯的項目名稱的緩衝區位址。 這個參數，除了`pstrSubItemName`，識別程式碼片段的事件處理常式的物件。  
  
 `pstrSubItemName`  
 [in]包含名稱之緩衝區的位址`subobject`與此程式碼片段是相關聯; 此名稱必須找到具名項目的型別資訊中的具名項目。 這個參數是 NULL，而不是具名的項目相關聯的程式碼片段是否`subitem`。 這個參數，除了`pstrItemName`，識別特定的事件處理常式程式碼片段的物件。  
  
 `pstrEventName`  
 [in]包含的事件的事件處理常式程式碼片段的名稱之緩衝區的位址。  
  
 `pstrDelimiter`  
 [in]結尾的程式碼片段分隔符號的位址。 當`pstrCode`參數會從文字資料流剖析，主應用程式通常會使用分隔符號，例如兩個單引號 （'），來偵測程式碼片段的結尾。 這個參數會指定使用主機，允許以提供一些條件的基本前置處理指令碼引擎的分隔符號 （例如，取代單引號 ['] 具有兩個單引號做為分隔符號使用）。 方式 （和 if） 指令碼的引擎會使用這項資訊取決於指令碼引擎。 如果主機未使用的分隔符號來標示程式碼片段的結尾，請設定此參數為 NULL。  
  
 `dwSourceContextCookie`  
 [in]應用程式定義的值，用於偵錯之用。  
  
 `ulStartingLineNumber`  
 [in]以零為起始的值，指定會在開始剖析那一行。  
  
 `dwFlags`  
 [in]程式碼片段相關聯的旗標。 可以是下列值的組合：  
  
|傳回值|意義|  
|------------------|-------------|  
|SCRIPTTEXT_ISVISIBLE|指出應該顯示指令碼文字 (，因此，可依名稱) 做為指令碼的命名空間中的全域方法。|  
|SCRIPTTEXT_ISPERSISTENT|表示是否儲存指令碼引擎時，會儲存此通話期間加入的程式碼 (例如，透過呼叫`IPersist*::Save`)，或如果指令碼引擎會重設透過初始化的狀態轉換。 如需有關此狀態的詳細資訊，請參閱指令碼引擎的狀態。|  
  
 `pbstrName` ,  
 [out]用來識別程式碼片段的實際名稱。 這是要依喜好設定順序： 程式碼片段文字中明確指定名稱，提供中的預設名稱`pstrDefaultName`，或指令碼引擎合成的唯一名稱。  
  
 `pexcepinfo` ,  
 [out]此結構包含例外狀況資訊的位址。 如果傳回 DISP_E_EXCEPTION，應該會自動填入這個結構。  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`DISP_E_EXCEPTION`|剖析的程式碼片段時，發生例外狀況。 `pexcepinfo`參數包含例外狀況的相關資訊。|  
|`E_INVALIDARG`|引數無效。|  
|`E_NOTIMPL`|不支援這個方法。指令碼引擎不支援新增事件接收的程式碼片段。|  
|`E_POINTER`|指定了無效的指標。|  
|`E_UNEXPECTED`|不應該呼叫 （例如，指令碼引擎有尚未載入或初始化），因此失敗。|  
|`OLESCRIPT_E_INVALIDNAME`|此指令碼語言中提供的預設名稱無效。|  
|`OLESCRIPT_E_SYNTAX`|在程式碼片段中發生未指定的語法錯誤。|  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)