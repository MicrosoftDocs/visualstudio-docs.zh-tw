---
title: JsPromiseContinuationCallback Typedef | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 51a3fd02-9668-4cf7-bb0b-e1fd03b2528f
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 762391cb66e5298bd70beb3238720d3717554ae0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568598"
---
# <a name="jspromisecontinuationcallback-typedef"></a>JsPromiseContinuationCallback Typedef
承諾接續回呼。  
  
## <a name="syntax"></a>語法  
  
```  
typedef void (CALLBACK *JsPromiseContinuationCallback)(  
  _In_ JsValueRef task,  
  _In_opt_ void *callbackState  
);  
```  
  
#### <a name="parameters"></a>參數  
 `task`  
  `callbackState`  
  
## <a name="remarks"></a>備註  
 主機可以在 `JsSetPromiseContinuationCallback`中指定承諾接續回呼。 如果指令碼建立一個要在稍後執行的工作，則會使用該工作呼叫承諾接續回呼，並且應該將該工作放在 FIFO 佇列中，以在目前指令碼完成執行時接著執行。  
  
 只有邊緣模式才支援這個 API。  
  
## <a name="requirements"></a>需求  
 jsrt.h  
  
## <a name="see-also"></a>另請參閱  
 [參考資料 (JavaScript 執行階段)](../chakra-hosting/reference-javascript-runtime.md)