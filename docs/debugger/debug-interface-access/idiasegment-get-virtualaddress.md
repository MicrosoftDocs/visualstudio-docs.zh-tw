---
title: 'Idiasegment:: Get_virtualaddress |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment::get_virtualAddress method
ms.assetid: 30073dd0-c864-4c4a-8863-80f243419f6c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 70373ef0b2024cc0650d8b8a5b1607bc86b6350d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53819486"
---
# <a name="idiasegmentgetvirtualaddress"></a>IDiaSegment::get_virtualAddress
擷取區段開頭的虛擬位址 (VA)。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_virtualAddress (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回區段開頭的 VA。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 反之則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)