---
description: 指出是否已為特定會話建立位址對應。
title: IDiaAddressMap::get_addressMapEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_addressMapEnabled method
ms.assetid: 6183dc5e-befa-4e5a-ae5a-f4aa24f3ed9e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6a55ff89e97d1898ec2ced2b62f7cdfa5a0df817
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149106"
---
# <a name="idiaaddressmapget_addressmapenabled"></a>IDiaAddressMap::get_addressMapEnabled
指出是否已為特定會話建立位址對應。

## <a name="syntax"></a>語法

```C++
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
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)
