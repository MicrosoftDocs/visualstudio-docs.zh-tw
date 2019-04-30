---
title: IDiaTable::get__NewEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::get__NewEnum method
ms.assetid: ee89bba8-5d5c-4a0b-aa0d-1aad56baa380
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c749b87b525ea52593cdfec301fda6987f361c4f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62834112"
---
# <a name="idiatablegetnewenum"></a>IDiaTable::get__NewEnum
擷取<xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT>這個列舉值的版本。

## <a name="syntax"></a>語法

```C++
HRESULT get__NewEnum ( 
   IUnknown** pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

[out]傳回`IUnknown`介面，表示<xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT>這個列舉值的版本。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)