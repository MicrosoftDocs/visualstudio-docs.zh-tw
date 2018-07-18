---
title: JsSetRuntimeMemoryLimit 函式 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsSetRuntimeMemoryLimit
helpviewer_keywords:
- JsSetRuntimeMemoryLimit function
ms.assetid: 74feb31f-19f6-43e3-b117-0694c59ac593
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 587eb369e6971c7527177624ccf5baf839246cf9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568968"
---
# <a name="jssetruntimememorylimit-function"></a>JsSetRuntimeMemoryLimit 函式
設定執行階段目前的記憶體限制。  
  
## <a name="syntax"></a>語法  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeMemoryLimit(  
   _In_ JsRuntimeHandle runtime,  
   _In_ size_t memoryLimit  
);  
```  
  
#### <a name="parameters"></a>參數  
 `runtime`  
 要設定其記憶體限制的執行階段。  
  
 `memoryLimit`  
 新執行階段記憶體限制，以位元組為單位；或為 -1，代表沒有記憶體限制。  
  
## <a name="return-value"></a>傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## <a name="remarks"></a>備註  
 記憶體限制將導致任何因超過此限制的作業失敗，並傳回「記憶體不足」錯誤訊息。 設定執行階段的記憶體限制為 -1 表示此執行階段沒有任何的記憶體限制。 新的執行階段預設為沒有記憶體限制。 如果新的記憶體限制超過目前使用量，則呼叫會成功，且在此執行階段內的所有未來配置將會失敗，除非此執行階段的記憶體使用量降低至限制之下。  
  
 無論此執行階段是否在另一個執行緒上作用，永遠可以設定執行階段的記憶體限制。  
  
## <a name="requirements"></a>需求  
 **標頭：** jsrt.h  
  
## <a name="see-also"></a>另請參閱  
 [參考資料 (JavaScript 執行階段)](../chakra-hosting/reference-javascript-runtime.md)