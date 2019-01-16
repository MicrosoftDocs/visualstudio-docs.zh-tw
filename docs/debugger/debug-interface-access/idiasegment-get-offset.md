---
title: 'Idiasegment:: Get_offset |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment::get_offset method
ms.assetid: 97415ac6-b072-4e3c-9dd3-73087ae605fc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1f78969d128443393c72f374c9ed63dd9ba0d1d1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53832761"
---
# <a name="idiasegmentgetoffset"></a>IDiaSegment::get_offset
擷取位移，區段，區段開始的位置。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_offset (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]會傳回位移，區段，區段開始的位置。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 反之則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)