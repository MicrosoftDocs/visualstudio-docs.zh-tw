---
title: IDiaStackWalkFrame：： readMemory |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ffd85fd1a6878fd378931901098d90f2a24c8ccc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99854798"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
從映射讀取記憶體。

## <a name="syntax"></a>語法

```C++
HRESULT readMemory ( 
   MemoryTypeEnum type,
   ULONGLONG va,
   DWORD     cbData,
   DWORD*    pcbData,
   BYTE      data[]
);
```

#### <a name="parameters"></a>參數
 `type`

在其中一個 [MemoryTypeEnum 列舉](../../debugger/debug-interface-access/memorytypeenum.md) 列舉值，這個值會指定要存取的記憶體種類。

 `va`

在映射中要開始讀取的虛擬位址位置。

 `cbData`

在資料緩衝區的大小（以位元組為單位）。

 `pcbData`

擴展傳回傳回的位元組數目。 如果 `data` 為 `NULL` ，則 `pcbData` 包含可用的資料位元組總數。

 `data`

擴展要以指定位置中的資料填入的緩衝區。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)