---
title: IDiaStackWalkFrame：： readMemory |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae1201fca1fc25cce19b40b47d6435d02d80e1b4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741471"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
從影像讀取記憶體。

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

在其中一個[MemoryTypeEnum 列舉](../../debugger/debug-interface-access/memorytypeenum.md)列舉值，指定要存取的記憶體類型。

 `va`

在映射中要開始讀取的虛擬位址位置。

 `cbData`

在資料緩衝區的大小（以位元組為單位）。

 `pcbData`

脫銷傳回傳回的位元組數目。 如果 `NULL` `data`，則 `pcbData` 包含可用的資料位元組總數。

 `data`

脫銷要填入指定位置之資料的緩衝區。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回錯誤碼。

## <a name="see-also"></a>請參閱
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)