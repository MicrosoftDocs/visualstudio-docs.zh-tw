---
title: JsErrorCode 列舉 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsErrorCode
helpviewer_keywords:
- JsErrorCode enumeration
ms.assetid: 4902f3f3-47a5-4e74-9c29-f96eeecbcda9
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b09babd38505c5619f414d2e349cd52b3596ceac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569088"
---
# <a name="jserrorcode-enumeration"></a>JsErrorCode 列舉
從 Chakra 裝載 API 傳回的錯誤碼。  
  
## <a name="syntax"></a>語法  
  
```  
enum JsErrorCode : unsigned int;  
```  
  
## <a name="members"></a>Members  
  
### <a name="values"></a>值  
  
|名稱|描述|  
|----------|-----------------|  
|`JsErrorAlreadyDebuggingContext`|由於內容已處於偵錯狀態，因此無法再將它設為偵錯狀態。|  
|`JsErrorAlreadyProfilingContext`|由於內容已經在進行分析，因此無法啟動分析。|  
|`JsErrorArgumentNotObject`|呼叫處理物件值的裝載 API 時內含非物件值。|  
|`JsErrorBadSerializedScript`|使用了序列化不正確的指令碼，或是序列化的指令碼是使用不同版本的 Chakra 引擎進行序列化。|  
|`JsErrorCannotDisableExecution`|執行階段未支援可靠的指令碼中斷。|  
|`JsErrorCannotSerializeDebugScript`|指令碼無法在偵錯內容中序列化。|  
|`JsErrorCategoryEngine`|與引擎本身內發生的錯誤相關的錯誤分類。|  
|`JsErrorCategoryFatal`|表示嚴重並指出引擎失敗的錯誤分類。|  
|`JsErrorCategoryScript`|與指令碼中的錯誤相關的錯誤分類。|  
|`JsErrorCategoryUsage`|與 API 本身使用方式不正確相關的錯誤分類。|  
|`JsErrorFatal`|引擎發生嚴重錯誤。|  
|`JsErrorHeapEnumInProgress`|堆積列舉目前正在指令碼內容中執行。|  
|`JsErrorIdleNotEnabled`|主機未啟用閒置處理時發出閒置通知。|  
|`JsErrorInDisabledState`|執行階段處於停用狀態。|  
|`JsErrorInExceptionState`|引擎處於例外狀況狀態，而且在清除例外狀況之前無法呼叫 API。|  
|`JsErrorInObjectBeforeCollectCallback`|在收集回呼之前的物件中不支援此作業。<br /><br /> 只有邊緣模式會支援這個列舉值。|  
|`JsErrorInProfileCallback`|指令碼內容正在進行設定檔回呼。|  
|`JsErrorInThreadServiceCallback`|執行緒服務回呼目前正在執行。|  
|`JsErrorInvalidArgument`|裝載 API 的引數無效。|  
|`JsErrorNoCurrentContext`|裝載 API 需要目前內容，但是沒有目前內容。|  
|`JsErrorNotImplemented`|裝載 API 尚未實作。|  
|`JsErrorNullArgument`|在不允許 null 的內容中，裝載 API 的引數為 null。|  
|`JsErrorObjectNotInspectable`|不能將物件解除包裝成 `IInspectable` 指標。<br /><br /> 只有邊緣模式會支援這個列舉值。|  
|`JsErrorOutOfMemory`|Chakra 引擎記憶體不足。|  
|`JsErrorPropertyNotSymbol`|在符號屬性 ID 上運作的裝載 API ，但以非符號屬性 ID 被呼叫。如果以非符號屬性 ID 呼叫此函式，則 `JsGetSymbolFromPropertyId` 會傳回錯誤碼。<br /><br /> 只有邊緣模式會支援這個列舉值。|  
|`JsErrorPropertyNotString`|在字串屬性 ID 上運作的裝載 API ，但以非字串屬性 ID 被呼叫。如果以非字串屬性 ID 呼叫此函式，則現有的 `JsGetPropertyNamefromId` 會傳回錯誤碼。<br /><br /> 只有邊緣模式會支援這個列舉值。|  
|`JsErrorRuntimeInUse`|無法處置仍在使用的執行階段。|  
|`JsErrorScriptCompile`|無法編譯 JavaScript。|  
|`JsErrorScriptEvalDisabled`|指令碼已終止，因為它嘗試使用 `eval` 或 `function` ，而且 eval 已停用。|  
|`JsErrorScriptException`|執行指令碼時發生 JavaScript 例外狀況。|  
|`JsErrorScriptTerminated`|指令碼因暫停執行階段的要求而終止。|  
|`JsErrorWrongRuntime`|使用在不同 JavaScript 執行階段中建立的物件呼叫裝載 API。|  
|`JsErrorWrongThread`|在錯誤的執行緒上呼叫裝載 API。|  
|`JsNoError`|成功錯誤碼。|  
  
## <a name="requirements"></a>需求  
 **標頭：** jsrt.h  
  
## <a name="see-also"></a>另請參閱  
 [參考資料 (JavaScript 執行階段)](../chakra-hosting/reference-javascript-runtime.md)