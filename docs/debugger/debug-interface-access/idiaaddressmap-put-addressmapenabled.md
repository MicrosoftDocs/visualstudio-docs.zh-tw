---
description: 指定是否應該使用位址對應來轉譯符號位址。
title: IDiaAddressMap::put_addressMapEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 84878e83db15cfa5a9c68dccfec78536035cb70f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159511"
---
# <a name="idiaaddressmapput_addressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
指定是否應該使用位址對應來轉譯符號位址。

## <a name="syntax"></a>語法

```C++
HRESULT put_addressMapEnabled ( 
   BOOL NewVal
);
```

#### <a name="parameters"></a>參數
 NewVal

在設定為 `TRUE` 以啟用符號轉譯或 `FALSE` 停用。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 可執行檔後端可能會更新可執行檔。 DIA 包含一種機制，可支援將符號轉譯成新的版面配置。

 載入 PDB 檔案時，會啟用儲存在檔案中的位址對應。 不過，在某些情況下，用戶端應用程式可能需要呼叫 [IDiaAddressMap：： set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) 方法來提供自己的位址對應。 如果 `set_addressMap` 方法成功，用戶端應用程式必須使用的 `put_addressMapEnabled` 參數來呼叫方法， `NewVal` `TRUE` 以啟用該位址對應。

 您可以呼叫 [IDiaAddressMap：： get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) 方法，以抓取正在啟用之位址對應的目前狀態。

## <a name="see-also"></a>另請參閱
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)
