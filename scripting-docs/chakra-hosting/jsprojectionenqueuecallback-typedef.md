---
title: JsProjectionEnqueueCallback Typedef | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 19c1cefb-a7be-4196-b780-9fe6adf35ba5
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bda4a3a80edac38ab2c3885c2256cdf9d03eb8c1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568308"
---
# <a name="jsprojectionenqueuecallback-typedef"></a>JsProjectionEnqueueCallback Typedef
當預估 API 在不同於原始執行緒的執行緒上完成時，JsRT 所呼叫的應用程式回呼。  
  
## <a name="syntax"></a>語法  
  
```  
typedef void (CALLBACK *JsProjectionEnqueueCallback)(  
  _In_ JsProjectionCallback jsCallback,  
  _In_ JsProjectionCallbackContext jsContext,  
  _In_opt_ void *callbackState  
);  
```  
  
#### <a name="parameters"></a>參數  
 `jsCallback`  
 要在原始執行緒上叫用的回呼。  
  
 `jsContext`  
 應用程式內容。  
  
 `callbackState`  
 必須傳入 `jsCallback`的 JsRT 內容。  
  
## <a name="remarks"></a>備註  
 需要呼叫 JsSetProjectionEnqueueCallback 接收回呼。  
  
 只有邊緣模式才支援這個 API。  
  
## <a name="requirements"></a>需求  
 jsrt.h  
  
## <a name="see-also"></a>另請參閱  
 [參考資料 (JavaScript 執行階段)](../chakra-hosting/reference-javascript-runtime.md)