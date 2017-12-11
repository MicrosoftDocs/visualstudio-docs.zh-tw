---
title: JsProjectionCallbackContext Typedef | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 50c705c5-664f-4a1a-92f6-4882fc718ab1
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7548dc14ab4b3dddc1633a1ba948aba564d8438a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="jsprojectioncallbackcontext-typedef"></a>JsProjectionCallbackContext Typedef
從 JsRT 傳入應用程式回呼 JsProjectionEnqueueCallback，然後再以正確執行緒上的應用程式所提供的回呼 `JsProjectionCallback` 傳回 JsRT 的內容。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef void *JsProjectionCallbackContext;  
```  
  
## <a name="remarks"></a>備註  
 需要呼叫 `JsSetProjectionEnqueueCallback` 接收回呼。  
  
 只有邊緣模式才支援這個 API。  
  
## <a name="requirements"></a>需求  
 jsrt.h  
  
## <a name="see-also"></a>另請參閱  
 [參考資料 (JavaScript 執行階段)](../chakra-hosting/reference-javascript-runtime.md)