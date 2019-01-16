---
title: 'Idiasectioncontrib:: Get_addresssection |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_addressSection method
ms.assetid: 13fe7e0b-c978-4a1d-bb57-64c8583b5e14
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c03a3955bbb3e247d2f2a2324f2715c960fd6fab
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53917640"
---
# <a name="idiasectioncontribgetaddresssection"></a>IDiaSectionContrib::get_addressSection
擷取所佔比重的地址中區段的一部分。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_addressSection (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回所佔比重的地址中區段的一部分。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 反之則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)