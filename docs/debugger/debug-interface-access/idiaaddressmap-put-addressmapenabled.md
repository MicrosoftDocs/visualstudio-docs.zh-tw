---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9b671150463060f11dc62ea49d3a21cd388c6000
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468571"
---
# <a name="idiaaddressmapput_addressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
指定是否應使用位址對應來轉譯符號位址。

## <a name="syntax"></a>語法

```C++
HRESULT put_addressMapEnabled ( 
   BOOL NewVal
);
```

#### <a name="parameters"></a>參數
 NewVal

在設定為 `TRUE` 以啟用符號的轉譯，或設為 `FALSE` 停用。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="remarks"></a>備註
 可執行檔後置處理常式有時會更新可執行檔。 DIA 包含一種機制，可支援將符號轉譯為新的版面配置。

 載入 PDB 檔案時，會啟用儲存在檔案中的位址對應。 不過，有時候用戶端應用程式可能需要藉由呼叫[IDiaAddressMap：： set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)方法來提供自己的位址對應。 如果 `set_addressMap` 方法成功，用戶端應用程式必須 `put_addressMapEnabled` 使用的參數呼叫方法， `NewVal` `TRUE` 以啟用該位址對應。

 您可以呼叫[IDiaAddressMap：： get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)方法來抓取要啟用的位址對應的目前狀態。

## <a name="see-also"></a>另請參閱
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)