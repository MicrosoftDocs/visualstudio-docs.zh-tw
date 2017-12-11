---
title: "JsIdle 函式 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsIdle
helpviewer_keywords: JsIdle function
ms.assetid: 372d1c62-8e19-4886-aa33-364cabc09bba
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ddffd4f37c0e10985a2dbca26558d8a94b21b2f7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="jsidle-function"></a>JsIdle 函式
告知執行階段執行任何必要的閒置處理。  
  
## <a name="syntax"></a>語法  
  
```  
STDAPI_(JsErrorCode) JsIdle(  
   _Out_opt_ unsigned int *nextIdleTick  
);  
```  
  
#### <a name="parameters"></a>參數  
 `nextIdleTick`  
 當需要執行更多閒置作業時，下個系統會繼續進行滴答。 可以是 null。 如果沒有近期的閒置工作需要執行，則傳回滴答的最大數目。  
  
## <a name="return-value"></a>傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## <a name="remarks"></a>備註  
 如果已為目前的執行階段啟用閒置處理，則呼叫 `JsIdle` 會通知目前的執行階段主機處於閒置狀態，並通知執行階段可以執行記憶體清除工作。  
  
 直到執行階段有更多閒置工作需執行之前，`JsIdle` 也可以傳回系統滴答次數。 在滴答次數傳遞之前呼叫的 `JsIdle` 將無法執行。  
  
 需要使用中指令碼內容。  
  
## <a name="requirements"></a>需求  
 **標頭：** jsrt.h  
  
## <a name="see-also"></a>另請參閱  
 [參考資料 (JavaScript 執行階段)](../chakra-hosting/reference-javascript-runtime.md)