---
title: JsNumberToInt 函式 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 8b9256d6-76ac-4c74-a97c-fbb16c13f5f5
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f24acb837fdf46694aa2370e2ccf1fe3c926ce19
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568428"
---
# <a name="jsnumbertoint-function"></a>JsNumberToInt 函式
擷取數值的`int` 值。  
  
## <a name="syntax"></a>語法  
  
```  
STDAPI_(JsErrorCode) JsNumberToInt(  
      _In_ JsValueRef value,  
      _Out_ int *intValue  
);  
```  
  
#### <a name="parameters"></a>參數  
 `value`  
 要轉換成 `int` 值的數值。  
  
 `intValue`  
 `int` 值。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 這個函式會擷取數值的值，並轉換成 `int` 值。 如果值的類型不是數字，它將會失敗並傳回 `JsErrorInvalidArgument`。  
  
 需要使用中指令碼內容。  
  
 只有邊緣模式才支援這個 API。  
  
## <a name="requirements"></a>需求  
 **標頭：** jsrt.h  
  
## <a name="see-also"></a>另請參閱  
 [參考資料 (JavaScript 執行階段)](../chakra-hosting/reference-javascript-runtime.md)