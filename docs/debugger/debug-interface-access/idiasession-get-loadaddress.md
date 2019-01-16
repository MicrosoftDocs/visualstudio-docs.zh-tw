---
title: 'Idiasession:: Get_loadaddress |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::get_loadAddress method
ms.assetid: 5162ae1a-38e3-4571-8995-4ed9be1dec3e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bd52a6cba05c4757eaefcc1518d4e659c4c89643
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53951257"
---
# <a name="idiasessiongetloadaddress"></a>IDiaSession::get_loadAddress
擷取對應至這個符號存放區中的符號的可執行檔載入位址。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_loadAddress (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回虛擬位址 (VA) 載入.exe 檔或.dll 檔案的位置。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 傳回的載入位址也永遠是零除非特別使用來設定[idiasession:: Put_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)方法。  
  
## <a name="see-also"></a>請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)