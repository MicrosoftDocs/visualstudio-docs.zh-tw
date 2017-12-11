---
title: JsSerializedScriptLoadSourceCallback Typedef | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9406c488-76ac-49e5-b305-39751f3412ea
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ff3bc206cf3779023a13166f30e8f4f719e7ebe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="jsserializedscriptloadsourcecallback-typedef"></a>JsSerializedScriptLoadSourceCallback Typedef
由執行階段呼叫，以載入序列化指令碼的原始程式碼。     在 `JsSerializedScriptUnloadCallback`之前，呼叫端都必須確保指令碼緩衝區有效。  
  
## <a name="syntax"></a>語法  
  
```  
typedef bool (CALLBACK * JsSerializedScriptLoadSourceCallback)(  
  _In_ JsSourceContextsourceContext,  
  _Outptr_result_z_ const wchar_t** scriptBuffer  
);  
```  
  
#### <a name="parameters"></a>參數  
 `sourceContext`  
 傳遞至 `JsParseSerializedScriptWithCallback` 或 `JsRunSerializedScriptWithCallback`的內容。  
  
 `scriptBuffer`  
 傳回的指令碼。  
  
## <a name="remarks"></a>備註  
  
> [!WARNING]
## <a name="requirements"></a>需求  
 **標頭：** jsrt.h  
  
## <a name="see-also"></a>另請參閱  
 [參考資料 (JavaScript 執行階段)](../chakra-hosting/reference-javascript-runtime.md)