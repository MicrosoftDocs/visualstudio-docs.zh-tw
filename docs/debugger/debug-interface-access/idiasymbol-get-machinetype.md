---
title: 'Idiasymbol:: Get_machinetype |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_machineType method
ms.assetid: 30870b10-6f32-45c6-a0d7-020dea707710
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eef0507ccb7036748f5c9d36c9de521a17860a39
ms.sourcegitcommit: 91c7f1b525e0c22d938bc4080ba4ceac2483474f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2019
ms.locfileid: "67032720"
---
# <a name="idiasymbolgetmachinetype"></a>IDiaSymbol::get_machineType
擷取目標 CPU 的類型。

## <a name="syntax"></a>語法

```C++
HRESULT get_machineType ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

[out]傳回值，以從[IMAGE_FILE_MACHINE_ 常數](/windows/desktop/SysInfo/image-file-machine-constants)所指定的目標 CPU 類型。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。

> [!NOTE]
> 傳回值為`S_FALSE`表示此屬性不適用於符號。

## <a name="see-also"></a>另請參閱
- [IMAGE_FILE_MACHINE_ 常數](/windows/desktop/SysInfo/image-file-machine-constants) 
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)