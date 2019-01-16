---
title: 'Idiasectioncontrib:: Get_comdat |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_comdat method
ms.assetid: 8bd9be8d-59ee-4698-b055-daba354b8dcc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09ba0e015ae4383a0d8bb215d565635570f04daa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53951442"
---
# <a name="idiasectioncontribgetcomdat"></a>IDiaSectionContrib::get_comdat
擷取指出區段是否為 COMDAT 記錄旗標。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_comdat (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]會傳回`TRUE`區段，則 COMDAT 記錄; 否則會傳回`FALSE`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 `S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 COMDAT 記錄是可封裝函式讓看到連結器的通用物件檔案格式 (COFF) 記錄。  
  
## <a name="see-also"></a>請參閱  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)