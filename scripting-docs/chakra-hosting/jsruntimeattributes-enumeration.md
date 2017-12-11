---
title: "JsRuntimeAttributes 列舉 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsRuntimeAttributes
helpviewer_keywords: JsRuntimeAttributes enumeration
ms.assetid: f76d82e9-a695-4d6a-96c1-b3a4d27fed68
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a7917ad5468b8d2924526f953ae444c5d8381eb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="jsruntimeattributes-enumeration"></a>JsRuntimeAttributes 列舉
執行階段的屬性。  
  
## <a name="syntax"></a>語法  
  
```  
enum JsRuntimeAttributes;  
```  
  
## <a name="members"></a>Members  
  
### <a name="values"></a>值  
  
|名稱|描述|  
|----------|-----------------|  
|`JsRuntimeAttributeAllowScriptInterrupt`|執行階段應該支援可靠的指令碼中斷。 這樣會增加執行階段檢查指令碼中斷要求的位置數，但是會稍微降低執行階段的效能。|  
|`JsRuntimeAttributeDisableBackgroundWork`|執行階段將不會在背景執行緒上執行任何作業 (例如，記憶體回收)。|  
|`JsRuntimeAttributeDisableEval`|使用 `eval` 或 `function` 建構函式將會擲回例外狀況。|  
|`JsRuntimeAttributeDisableNativeCodeGeneration`|執行階段不會產生機器碼。|  
|`JsRuntimeAttributeEnableExperimentalFeatures`|執行階段會啟用所有實驗性功能。|  
|`JsRuntimeAttributeEnableIdleProcessing`|主機將會呼叫 `JsIdle`，因此，請啟用閒置處理。 否則執行階段將會稍微積極地管理記憶體。|  
|`JsRuntimeAttributeDispatchSetExceptionsToDebugger`|呼叫 `JsSetException` 也會將例外狀況分派至指令碼偵錯工具 (如果有)，讓偵錯工具有機會中斷例外狀況。|  
|`JsRuntimeAttributeNone`|沒有特殊屬性。|  
  
## <a name="requirements"></a>需求  
 **標頭：** jsrt.h  
  
## <a name="see-also"></a>另請參閱  
 [參考資料 (JavaScript 執行階段)](../chakra-hosting/reference-javascript-runtime.md)