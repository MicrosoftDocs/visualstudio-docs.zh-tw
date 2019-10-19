---
title: IActiveScriptParse：： AddScriptlet |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: c1b4ac460afea1efd538c64224d84afef49d1a67
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573529"
---
# <a name="iactivescriptparseaddscriptlet"></a>IActiveScriptParse::AddScriptlet
將程式碼程式碼片段加入至腳本。 這個方法是在腳本的持續狀態與主機檔一起密不可分的環境中使用，而主機負責還原腳本，而不是透過 `IPersist*` 介面。 主要範例是 HTML 指令碼語言，可讓 HTML 檔案中內嵌的程式碼程式碼片段附加至內部事件（例如，ONCLICK = "button1. text = ' Exit '"）。  
  
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
 在要與程式碼片段建立關聯的預設名稱位址。 如果程式碼片段不包含命名資訊（如上述的 ONCLICK 範例所示），則會使用這個名稱來識別程式碼片段。 如果這個參數是 `NULL`，腳本引擎會在必要時製造一個唯一的名稱。  
  
 `pstrCode`  
 在要加入之程式碼片段文字的位址。 這個字串的轉譯取決於指令碼語言。  
  
 `pstrItemName`  
 在包含與此程式碼片段相關聯之專案名稱的緩衝區位址。 除了 `pstrSubItemName` 以外，這個參數會識別程式碼片段為事件處理常式的物件。  
  
 `pstrSubItemName`  
 在緩衝區的位址，其中包含與此程式碼片段相關聯之命名專案的 `subobject` 名稱;這個名稱必須在命名專案的類型資訊中找到。 如果程式碼片段要與指定的專案產生關聯，而不是 `subitem`，則此參數為 Null。 除了 `pstrItemName` 以外，這個參數會識別程式碼片段為事件處理常式的特定物件。  
  
 `pstrEventName`  
 在緩衝區的位址，其中包含程式碼片段為事件處理常式之事件的名稱。  
  
 `pstrDelimiter`  
 在程式碼片段後端分隔符號的位址。 從文字的資料流程剖析 `pstrCode` 參數時，主機通常會使用分隔符號，例如兩個單引號（' '）來偵測程式碼片段的結尾。 這個參數會指定主機所使用的分隔符號，讓腳本引擎提供一些條件式基本前置處理（例如，使用兩個單引號來取代單引號 [']，做為分隔符號）。 腳本引擎利用這項資訊的確切方式，取決於腳本引擎。 如果主機未使用分隔符號來標示程式碼片段的結尾，請將此參數設為 Null。  
  
 `dwSourceContextCookie`  
 在應用程式定義的值，用於進行調試。  
  
 `ulStartingLineNumber`  
 在以零為起始的值，指定剖析要開始的行。  
  
 `dwFlags`  
 在與程式碼片段相關聯的旗標。 可以是下列值的組合：  
  
|傳回值|意義|  
|------------------|-------------|  
|SCRIPTTEXT_ISVISIBLE|表示腳本文字應該是可見的（因此，以名稱呼叫）做為腳本命名空間中的全域方法。|  
|SCRIPTTEXT_ISPERSISTENT|表示如果儲存腳本引擎（例如，透過呼叫 `IPersist*::Save`），或如果腳本引擎是藉由轉換回到已初始化的狀態重設，則應該儲存此呼叫期間新增的程式碼。 如需此狀態的詳細資訊，請參閱腳本引擎狀態。|  
  
 `pbstrName` ,  
 脫銷用來識別程式碼片段的實際名稱。 這是依照喜好設定的順序：在程式碼片段文字中明確指定的名稱、`pstrDefaultName` 中提供的預設名稱，或腳本引擎合成的唯一名稱。  
  
 `pexcepinfo` ,  
 脫銷包含例外狀況資訊之結構的位址。 如果傳回 DISP_E_EXCEPTION，則應該填入此結構。  
  
## <a name="return-value"></a>傳回值  
 傳回下列其中一個值：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`DISP_E_EXCEPTION`|剖析程式碼片段時發生例外狀況。 @No__t_0 參數包含例外狀況的相關資訊。|  
|`E_INVALIDARG`|引數無效。|  
|`E_NOTIMPL`|不支援這個方法;腳本引擎不支援新增事件接收程式碼片段。|  
|`E_POINTER`|指定了不正確指標。|  
|`E_UNEXPECTED`|不需要呼叫（例如，腳本引擎尚未載入或初始化），因此失敗。|  
|`OLESCRIPT_E_INVALIDNAME`|提供的預設名稱在此指令碼語言中無效。|  
|`OLESCRIPT_E_SYNTAX`|程式碼片段中發生未指定的語法錯誤。|  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)