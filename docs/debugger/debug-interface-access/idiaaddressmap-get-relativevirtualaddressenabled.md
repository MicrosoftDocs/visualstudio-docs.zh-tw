---
title: IDiaAddressMap::get_relativeVirtualAddressEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_relativeVirtualAddressEnabled method
ms.assetid: 4c48af81-7148-4d9a-818e-dbe62cbfc638
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 58d7bc241ed2e0fc885ace301b611918d1822dac
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857199"
---
# <a name="idiaaddressmapget_relativevirtualaddressenabled"></a>IDiaAddressMap::get_relativeVirtualAddressEnabled
指出是否已啟用 (RVA) 的相對虛擬位址計算和使用。

## <a name="syntax"></a>語法

```C++
HRESULT get_relativeVirtualAddressEnabled ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>參數
 pRetVal

擴展 `TRUE` 如果已啟用 rva 的計算，則會傳回。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 如果一開始是從 PDB 檔案載入區段，則會啟用 Rva。 藉由呼叫 [IDiaAddressMap：:p ut_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) 方法，可以暫時停用 rva。

 此外，您可以呼叫 [IDiaAddressMap：： set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) 方法來建立新的映射標頭，然後呼叫方法， `put_relativeVirtualAddressEnabled` 以使用新的映射標頭來啟用 rva。

## <a name="see-also"></a>另請參閱
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)
- [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)