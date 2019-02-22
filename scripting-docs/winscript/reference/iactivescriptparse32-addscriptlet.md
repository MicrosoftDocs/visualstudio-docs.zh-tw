---
title: IActiveScriptParse32::AddScriptlet |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fcf11eb2-8e71-4cca-afda-a91791c243ff
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: b5a680eea5f5695d3a7253b9cf722af6ebf537c6
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089540"
---
# <a name="iactivescriptparse32addscriptlet"></a>IActiveScriptParse32::AddScriptlet
將指令碼中的程式碼的程式碼片段。 這個方法會在環境中與主應用程式文件提及永續性狀態的指令碼主機會負責還原指令碼，而非透過`IPersist*`介面。 主要範例是允許的程式碼內嵌在 HTML 文件附加至內建事件的程式碼片段的 HTML 指令碼語言 (例如，ONCLICK="button1.text='Exit' 」)。  
  
## <a name="syntax"></a>語法  
  
```cpp
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
 [in]與 scriptlet 相關聯的預設名稱的位址。 如果程式碼片段不會包含命名資訊 （如上述的 ONCLICK 範例），這個名稱會用來識別程式碼片段中。 如果這個參數是`NULL`，指令碼引擎會製造一個唯一的名稱，如有必要。  
  
 `pstrCode`  
 [in]要加入的程式碼片段文字的位址。 這個字串的解譯取決於指令碼語言。  
  
 `pstrItemName`  
 [in]包含與此程式碼片段相關聯的項目名稱的緩衝區位址。 這個參數，除了`pstrSubItemName`，可識別程式碼片段的事件處理常式的物件。  
  
 `pstrSubItemName`  
 [in]包含名稱的緩衝區位址`subobject`與此程式碼片段會產生關聯，此名稱必須找到具名項目型別資訊中的具名項目。 這個參數是 NULL，如果程式碼片段是具名的項目，而不是與相關聯`subitem`。 這個參數，除了`pstrItemName`，識別特定的程式碼片段的事件處理常式的物件。  
  
 `pstrEventName`  
 [in]包含的事件的事件處理常式程式碼片段的名稱之緩衝區的位址。  
  
 `pstrDelimiter`  
 [in]結束的程式碼片段分隔符號的位址。 當`pstrCode`參數從文字資料流剖析，主應用程式通常會使用分隔符號，例如兩個單引號 （'），偵測 scriptlet 結尾。 這個參數指定主應用程式使用，允許以提供一些條件式的基本前置處理指令碼引擎的分隔符號 （比方說，取代兩個單引號以做為分隔符號使用的單引號 [']）。 究竟要如何 （以及是否） 指令碼的引擎會使用這項資訊會取決於指令碼引擎。 如果主機未使用分隔符號來標示程式碼片段的結尾，請設定此參數為 NULL。  
  
 `dwSourceContextCookie`  
 [in]應用程式定義的值，用於偵錯用途。  
  
 `ulStartingLineNumber`  
 [in]指定剖析將會在開始哪一行的以零為起始值。  
  
 `dwFlags`  
 [in]與 scriptlet 相關的旗標。 可以是下列值的組合：  
  
|傳回值|意義|  
|------------------|-------------|  
|SCRIPTTEXT_ISVISIBLE|指出應該顯示的指令碼文字 (因此，可依據名稱呼叫) 做為指令碼的命名空間中的全域方法。|  
|SCRIPTTEXT_ISPERSISTENT|表示是否指令碼引擎已儲存，是否應該儲存此呼叫期間加入的程式碼 (例如，透過呼叫`IPersist*::Save`)，或如果指令碼引擎透過轉換為初始化的狀態重設。 如需有關此狀態的詳細資訊，請參閱指令碼引擎狀態。|  
  
 `pbstrName` ,  
 [out]用來識別程式碼片段的實際名稱。 這是偏好的順序： 程式碼片段文字中明確指定的名稱，在中提供的預設名稱`pstrDefaultName`，或指令碼引擎合成的唯一名稱。  
  
 `pexcepinfo` ,  
 [out]包含例外狀況資訊結構的位址。 如果傳回 DISP_E_EXCEPTION，應該會自動填入這個結構。  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`DISP_E_EXCEPTION`|剖析的程式碼片段中，發生例外狀況。 `pexcepinfo`參數包含例外狀況的相關資訊。|  
|`E_INVALIDARG`|引數無效。|  
|`E_NOTIMPL`|不支援這個方法;指令碼引擎不支援新增事件接收的程式碼片段。|  
|`E_POINTER`|指定了無效的指標。|  
|`E_UNEXPECTED`|不需要呼叫 （例如，指令碼引擎有尚未載入或初始化），因此失敗。|  
|`OLESCRIPT_E_INVALIDNAME`|在此指令碼語言中提供的預設名稱無效。|  
|`OLESCRIPT_E_SYNTAX`|Scriptlet 中發生未指定的語法錯誤。|  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)