---
title: 'Idiainjectedsource:: Get_filename |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_filename method
ms.assetid: 20f4fc68-335a-4971-b3a6-76501f0e8b19
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 41d9cfbc2619f3701567f594b6d7db7400003212
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53911113"
---
# <a name="idiainjectedsourcegetfilename"></a>IDiaInjectedSource::get_filename
擷取來源檔案名稱。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_filename (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 pRetVal  
 [out]傳回來源的檔案名稱。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 反之則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)