---
title: 'Idiaframedata:: Get_lengthprolog |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_lengthProlog method
ms.assetid: 5f042ff1-e74e-430a-be34-d2cf1b18eff2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7ab2331c5138e11921c33fdbfacf54bc4d9d7ce2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53838316"
---
# <a name="idiaframedatagetlengthprolog"></a>IDiaFrameData::get_lengthProlog
擷取的初構程式碼區塊中的位元組數目。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_lengthProlog (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回的初構程式碼的位元組數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 初構程式碼是一連串的指示，會保留暫存器、 設定 CPU 狀態，以及建立函式的堆疊。  
  
## <a name="see-also"></a>請參閱  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)