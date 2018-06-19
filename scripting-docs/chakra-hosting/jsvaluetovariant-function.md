---
title: JsValueToVariant 函式 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsValueToVariant
helpviewer_keywords:
- JsValueToVariant function
ms.assetid: 070244be-a69d-4b78-971b-69c0579c03cf
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2beb0a72a8e19d38d80ab8bf29ce0478ba7f481f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568898"
---
# <a name="jsvaluetovariant-function"></a>JsValueToVariant 函式
初始化傳入的 `VARIANT`，做為 JavaScript 值的投影。  
  
## <a name="syntax"></a>語法  
  
```  
STDAPI_(JsErrorCode) JsValueToVariant(  
   _In_ JsValueRef object,  
   _Out_ VARIANT *variant  
);  
```  
  
#### <a name="parameters"></a>參數  
 `object`  
 要投影為 `VARIANT` 的 JavaScript 值。  
  
 `variant`  
 要初始化為投影的 `VARIANT` 結構之指標。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 COM Automation 用戶端可以使用 `VARIANT` 投影呼叫投影的 JavaScript 物件。  
  
 需要使用中指令碼內容。  
  
## <a name="requirements"></a>需求  
 **標頭：** jsrt.h  
  
## <a name="see-also"></a>另請參閱  
 [參考資料 (JavaScript 執行階段)](../chakra-hosting/reference-javascript-runtime.md)