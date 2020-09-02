---
title: IDiaAddressMap::get_addressMapEnabled | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_addressMapEnabled method
ms.assetid: 6183dc5e-befa-4e5a-ae5a-f4aa24f3ed9e
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0cf874590d6bcf7f259d7a59eee1b81b79ffe1a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178250"
---
# <a name="idiaaddressmapget_addressmapenabled"></a>IDiaAddressMap::get_addressMapEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

指出是否已為特定會話建立位址對應。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_addressMapEnabled (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 pRetVal  
 擴展 `TRUE` 如果已啟用位址對應，則會傳回。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 可執行檔後端可能會更新可執行檔。 DIA 包含一種機制，可支援將符號轉譯成新的版面配置。  
  
 用戶端應用程式可以從[IDiaSession](../../debugger/debug-interface-access/idiasession.md)介面取得[IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)介面，然後呼叫[IDiaAddressMap：： Set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)方法，然後呼叫[IDiaAddressMap：:p ut_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)方法，來設定特定會話的位址對應。 方法會傳回 `get_addressMapEnabled` 呼叫方法的結果 `put_addressMapEnabled` 。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaAddressMap：： set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)
