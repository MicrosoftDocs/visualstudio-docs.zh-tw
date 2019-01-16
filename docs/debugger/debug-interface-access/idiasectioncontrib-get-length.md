---
title: 'Idiasectioncontrib:: Get_length |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_length method
ms.assetid: d0f6b9c7-90fc-4e3c-945a-b8f683a8f006
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 852bf1c4a502c9d76a9f7f460c8fd62c26f73df9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53918693"
---
# <a name="idiasectioncontribgetlength"></a>IDiaSectionContrib::get_length
擷取區段中的位元組的數目。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_length (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]在區段中傳回位元組的數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 反之則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)