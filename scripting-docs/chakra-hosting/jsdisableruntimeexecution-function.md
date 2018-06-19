---
title: JsDisableRuntimeExecution 函式 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsDisableRuntimeExecution
helpviewer_keywords:
- JsDisableRuntimeExecution function
ms.assetid: 4bd4670a-a9da-4f8c-b3fd-1fd366d915c3
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f44545f7c81344a2d22f0083087f77ac8074278c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568268"
---
# <a name="jsdisableruntimeexecution-function"></a>JsDisableRuntimeExecution 函式
暫停指令碼執行，並在執行階段中終止任何執行中的指令碼。  
  
## <a name="syntax"></a>語法  
  
```  
STDAPI_(JsErrorCode) JsDisableRuntimeExecution(  
   _In_ JsRuntimeHandle runtime  
);  
```  
  
#### <a name="parameters"></a>參數  
 `runtime`  
 要暫停的執行階段。  
  
## <a name="return-value"></a>傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## <a name="remarks"></a>備註  
 已暫停的執行階段之呼叫將會失敗，除非 `JsEnableRuntimeExecution` 被呼叫。  
  
 在執行階段為作用中的執行緒上未必需要呼叫這個應用程式開發介面。 雖然執行階段將設定為暫停狀態，但執行中的指令碼可能不會立即遭到暫停；將會盡快以不可攔截的例外狀況終止執行中的指令碼。  
  
 在早已暫停之執行階段的暫停中執行會沒有任何作業。  
  
## <a name="requirements"></a>需求  
 **標頭：** jsrt.h  
  
## <a name="see-also"></a>另請參閱  
 [參考資料 (JavaScript 執行階段)](../chakra-hosting/reference-javascript-runtime.md)