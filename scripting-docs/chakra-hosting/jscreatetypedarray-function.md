---
title: JsCreateTypedArray 函式 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 937a2a91-6f5f-4aaa-a018-d3089702bf36
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1df33d0e1aadec9d7ed5aebf743e2c2f840e51fd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568358"
---
# <a name="jscreatetypedarray-function"></a>JsCreateTypedArray 函式
建立 JavaScript 具類型陣列物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
STDAPI_(JsErrorCode) JsCreateTypedArray(  
   _In_ JsTypedArrayType arrayType,  
   _In_ JsValueRef baseArray,  
   _In_ unsigned int byteOffset,  
   _In_ unsigned int elementLength,  
   _Out_ JsValueRef *result  
);  
```  
  
#### <a name="parameters"></a>參數  
 `arrayType`  
 要建立之陣列的類型。  
  
 `baseArray`  
 新陣列的基底陣列。 如果沒有基底陣列，則使用 `JS_INVALID_REFERENCE`。  
  
 `byteOffset`  
 結果具類型陣列所要參考之 `baseArray` (`ArrayBuffer`) 開頭的位移 (以位元組為單位)。 只有在 `baseArray` 是 `ArrayBuffer` 物件時才適用。 否則必須為 0。  
  
 `elementLength`  
 陣列中的項目數。 只有在建立不具有 `baseArray` 的新具類型陣列 (`baseArray` 是 `JS_INVALID_REFERENCE`)，或 `baseArray` 是 `ArrayBuffer` 物件時才適用。 否則必須為 0。  
  
 `result`  
 新的具類型陣列物件。  
  
## <a name="return-value"></a>傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## <a name="remarks"></a>備註  
 `baseArray` 可以是 `ArrayBuffer`、其他類型的陣列或 JavaScript `Array`。 如果傳回的具類型陣列是 `ArrayBuffer`，則會使用 `baseArray`；否則會建立並使用基礎來源陣列的複本。  
  
 需要使用中指令碼內容。  
  
 只有邊緣模式才支援這個 API。  
  
## <a name="requirements"></a>需求  
 **標頭：** jsrt.h  
  
## <a name="see-also"></a>另請參閱  
 [參考資料 (JavaScript 執行階段)](../chakra-hosting/reference-javascript-runtime.md)