---
title: 'Idialinenumber:: Get_columnnumber |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_columnNumber method
ms.assetid: e317f29a-6525-46a7-8421-33985392f8fd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 64b5b79a7f5342a240a16506f97322d915228949
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53893389"
---
# <a name="idialinenumbergetcolumnnumber"></a>IDiaLineNumber::get_columnNumber
擷取運算式或陳述式的開始處的資料行編號。  
  
## <a name="syntax"></a>語法  
  
```  
[C++]  
HRESULT get_columnNumber (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回的資料行編號的運算式或陳述式的開始位置。 如果值為零，則不存在的資料行資訊。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法所傳回的資料行值會列在列中的陳述式的第一個字元的位元組位移。  
  
## <a name="see-also"></a>請參閱  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)