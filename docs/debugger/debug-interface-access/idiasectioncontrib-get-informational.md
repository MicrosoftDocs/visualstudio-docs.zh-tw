---
title: 'Idiasectioncontrib:: Get_informational |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_informational method
ms.assetid: 5351e89f-7db1-4f8e-9e57-2dd1c74002e0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e582849fe392a77b48a8c83664c98fedb8037f5f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53987624"
---
# <a name="idiasectioncontribgetinformational"></a>IDiaSectionContrib::get_informational
擷取旗標，指出區段是否包含註解或類似的資訊。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_informational(  
   BOOL* pRetVal  
};  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]會傳回`TRUE`如果區段包含註解或其他資訊中; 否則會傳回`FALSE`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 `S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 通常.directive 區段包含的資訊。  
  
## <a name="see-also"></a>請參閱  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)