---
title: IDiaFrameData::get_relativeVirtualAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_relativeVirtualAddress method
ms.assetid: de070ef4-6c9d-43ca-911c-5245cbcb8dbe
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 833ef811f6859d7b991ba5931803fc0a3d21745c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56632767"
---
# <a name="idiaframedatagetrelativevirtualaddress"></a>IDiaFrameData::get_relativeVirtualAddress
擷取框架的程式碼的相對虛擬位址 (RVA)。

## <a name="syntax"></a>語法

```C++
HRESULT get_relativeVirtualAddress ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

[out]傳回框架的程式碼的相對虛擬位址。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 否則會傳回錯誤碼。

## <a name="see-also"></a>請參閱
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)