---
title: "JsGetAndClearException 函式 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsGetAndClearException
helpviewer_keywords:
- JsGetAndClearException function
ms.assetid: 6aec8a88-41ee-47f6-b5f4-32f3cae6bb7b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3e7e4f89bac59aa776762586ab20fa831b5c24bf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="jsgetandclearexception-function"></a>JsGetAndClearException 函式
傳回造成目前內容執行階段處於例外狀況狀態的例外狀況，並重設該執行階段的例外狀況狀態。  
  
## <a name="syntax"></a>語法  
  
```  
STDAPI_(JsErrorCode) JsGetAndClearException(  
   _Out_ JsValueRef *exception  
);  
```  
  
#### <a name="parameters"></a>參數  
 `exception`  
 目前內容的執行階段之例外狀況。  
  
## <a name="return-value"></a>傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## <a name="remarks"></a>備註  
 如果目前內容的執行階段未處於例外狀況狀態，此 API 就會傳回 `JsErrorInvalidArgument`。 如果停用執行階段，這將傳回表示指令碼已被終止的例外狀況，但它將不會清除此例外狀況 (若該執行階段使用 `JsEnableRuntimeExecution` 以重新啟用，則例外狀況將被清除)。  
  
 需要使用中指令碼內容。  
  
## <a name="requirements"></a>需求  
 **標頭：** jsrt.h  
  
## <a name="see-also"></a>另請參閱  
 [參考資料 (JavaScript 執行階段)](../chakra-hosting/reference-javascript-runtime.md)