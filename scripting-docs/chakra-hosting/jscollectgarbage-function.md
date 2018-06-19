---
title: JsCollectGarbage 函式 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsCollectGarbage
helpviewer_keywords:
- JsCollectGarbage function
ms.assetid: 995c79a5-6e18-45be-81ff-2a5d3348edb8
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b783e9716d9de1a618d8bb640ce0b507801612d2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24567608"
---
# <a name="jscollectgarbage-function"></a>JsCollectGarbage 函式
執行完整記憶體回收。  
  
## <a name="syntax"></a>語法  
  
```  
STDAPI_(JsErrorCode) JsCollectGarbage(  
   _In_ JsRuntimeHandle runtime  
);  
```  
  
#### <a name="parameters"></a>參數  
 `runtime`  
 將執行記憶體回收的執行階段。  
  
## <a name="return-value"></a>傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** jsrt.h  
  
## <a name="see-also"></a>另請參閱  
 [參考資料 (JavaScript 執行階段)](../chakra-hosting/reference-javascript-runtime.md)