---
title: JsObjectBeforeCollectCallback Typedef | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: f21a064a-579f-44cb-9d21-76b62e8c18f5
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7d11de01c44792d3e41cc2721a404f2ed906f02e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568438"
---
# <a name="jsobjectbeforecollectcallback-typedef"></a>JsObjectBeforeCollectCallback Typedef
收集物件前呼叫的回呼。  
  
## <a name="syntax"></a>語法  
  
```  
typedef void (CALLBACK *JsObjectBeforeCollectCallback)(  
  _In_ JsRef ref,  
  _In_opt_ void *callbackState  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ref`  
 要收集的物件。  
  
 `callbackState`  
 傳遞給 `JsSetObjectBeforeCollectCallback`的狀態。  
  
## <a name="remarks"></a>備註  
 只有邊緣模式才支援這個 API。  
  
## <a name="requirements"></a>需求  
 jsrt.h  
  
## <a name="see-also"></a>另請參閱  
 [參考資料 (JavaScript 執行階段)](../chakra-hosting/reference-javascript-runtime.md)