---
title: IDiaStackFrame::get_allocatesBasePointer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_allocatesBasePointer
ms.assetid: a91e9c8e-c5e3-4887-a60b-f03b5a98f30c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4a747edd3c0140661177438cd9d25e0d1ec811bd
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55029613"
---
# <a name="idiastackframegetallocatesbasepointer"></a>IDiaStackFrame::get_allocatesBasePointer
擷取指出是否要將基底指標配置此位址範圍中的程式碼的旗標。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_allocatesBasePointer (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]會傳回`TRUE`基底的指標會配置程式碼，在此框架中; 否則會傳回`FALSE`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 `S_OK`。 傳回`S_FALSE`不支援的屬性。 否則會傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)