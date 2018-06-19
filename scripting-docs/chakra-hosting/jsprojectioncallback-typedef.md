---
title: JsProjectionCallback Typedef | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 32f22d37-e57e-4196-b6cd-a3fc75bd0632
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 80d1c64f04f44a8560c25935fba2a48905a73260
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568248"
---
# <a name="jsprojectioncallback-typedef"></a>JsProjectionCallback Typedef
應該使用傳遞給正確執行緒上 `JsProjectionEnqueueCallback` 之內容呼叫的 JsRT 回呼。  
  
## <a name="syntax"></a>語法  
  
```  
typedef void (CALLBACK *JsProjectionCallback)(  
  _In_ JsProjectionCallbackContext jsContext  
);  
```  
  
#### <a name="parameters"></a>參數  
 `jsContext`  
 需要呼叫 `JsSetProjectionEnqueueCallback` 接收回呼。  
  
## <a name="remarks"></a>備註  
 只有邊緣模式才支援這個 API。  
  
## <a name="requirements"></a>需求  
 jsrt.h  
  
## <a name="see-also"></a>另請參閱  
 [參考資料 (JavaScript 執行階段)](../chakra-hosting/reference-javascript-runtime.md)