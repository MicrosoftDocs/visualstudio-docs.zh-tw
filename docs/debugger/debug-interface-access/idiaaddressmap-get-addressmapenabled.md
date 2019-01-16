---
title: 'Idiaaddressmap:: Get_addressmapenabled |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_addressMapEnabled method
ms.assetid: 6183dc5e-befa-4e5a-ae5a-f4aa24f3ed9e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc632a0eda039c5f3268d2007f45d7cddd096baa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53896652"
---
# <a name="idiaaddressmapgetaddressmapenabled"></a>IDiaAddressMap::get_addressMapEnabled
指出是否已為特定的工作階段建立對應的位址。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_addressMapEnabled (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 pRetVal  
 [out]傳回`TRUE`如果已啟用的位址對應。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 可執行的後置處理器有時會更新可執行檔。 DIA 包含支援新的版面配置將符號的轉譯機制。  
  
 用戶端應用程式可以藉由取得特定的工作階段中設定對應位址[IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)從介面[IDiaSession](../../debugger/debug-interface-access/idiasession.md)介面及呼叫[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)方法呼叫後面接著[idiaaddressmap:: Put_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)方法。 `get_addressMapEnabled`方法會傳回呼叫的結果`put_addressMapEnabled`方法。  
  
## <a name="see-also"></a>請參閱  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)