---
description: 允許用戶端啟用或停用相對虛擬位址 (RVA) 的計算和使用。
title: IDiaAddressMap：:p ut_relativeVirtualAddressEnabled |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_relativeVirtualAddressEnabled method
ms.assetid: 767c078e-8ad7-4940-9e00-cae7704aadee
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7c3aab1379a39ee6abfd977350743e36c9792efb
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158319"
---
# <a name="idiaaddressmapput_relativevirtualaddressenabled"></a>IDiaAddressMap::put_relativeVirtualAddressEnabled
允許用戶端啟用或停用相對虛擬位址 (RVA) 的計算和使用。

## <a name="syntax"></a>語法

```C++
HRESULT put_relativeVirtualAddressEnabled ( 
   BOOL NewVal
);
```

#### <a name="parameters"></a>參數
 NewVal

在將設定為 `TRUE` ，以啟用或 `FALSE` 停用。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 DIA 介面所描述的 debug 物件位址，以及可執行檔的映射基底，可以抓取為相對虛擬位址。

 從 PDB 檔案開始載入區段時，會啟用使用 Rva。 若要取得使用 Rva 的目前狀態，請呼叫 [IDiaAddressMap：： get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) 方法。

 在 `put_relativeVirtualAddress` 成功呼叫 [IDiaAddressMap：： set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) 方法之後，必須呼叫方法來啟用 rva，以建立新的映射標頭。

## <a name="see-also"></a>另請參閱
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)
